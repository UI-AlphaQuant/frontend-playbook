# 👉 React Vite TS Production API Foundation

## 📌 Recommended Structure

```txt
src/
│
├── api/
│   ├── apiClient.ts
│   ├── retryRequest.ts
│   ├── tokenManager.ts
│   ├── cacheManager.ts
│   ├── requestTimeout.ts
│   └── abortManager.ts
│
├── hooks/
│   ├── useDebounce.ts
│   └── usePagination.ts
│
├── config/
│   └── env.ts
│
├── types/
│   └── api.types.ts
│
├── utils/
│   └── sleep.ts
│
└── features/
```

- Step-by-Step Flow

```txt
Component
   ↓
Feature API
   ↓
apiClient
   ↓
Retry / Timeout / Refresh Token
   ↓
Fetch API
   ↓
Backend
```

- `.env.development`

```env
VITE_API_URL=http://localhost:3000/api
```

- `.env.production`

```env
VITE_API_URL=https://api.company.com/api
```

### `config/env.ts`

```ts
// Centralized Config
export const ENV = {
  API_URL: import.meta.env.VITE_API_URL,
};
```

### `types/api.types.ts`

```ts
// Shared API Types
export type ApiError = {
  message: string;
  status?: number;
};

export type PaginationParams = {
  page?: number;
  limit?: number;
};

export type ApiResponse<T> = {
  data: T;
  message?: string;
};
```

### `utils/sleep.ts`

```ts
// Shared Delay Utility
export function sleep(ms: number) {
  return new Promise((resolve) => setTimeout(resolve, ms));
}
```

### `api/tokenManager.ts`

```ts
// Token Handling
const ACCESS_TOKEN_KEY = "access_token";
const REFRESH_TOKEN_KEY = "refresh_token";

export const tokenManager = {
  getAccessToken() {
    return localStorage.getItem(ACCESS_TOKEN_KEY);
  },

  setAccessToken(token: string) {
    localStorage.setItem(ACCESS_TOKEN_KEY, token);
  },

  getRefreshToken() {
    return localStorage.getItem(REFRESH_TOKEN_KEY);
  },

  setRefreshToken(token: string) {
    localStorage.setItem(REFRESH_TOKEN_KEY, token);
  },

  clearTokens() {
    localStorage.removeItem(ACCESS_TOKEN_KEY);
    localStorage.removeItem(REFRESH_TOKEN_KEY);
  },
};
```

### `api/cacheManager.ts`

```ts
// Shared Memory Cache
const cache = new Map();

export const cacheManager = {
  get(key: string) {
    return cache.get(key);
  },

  set(key: string, value: unknown) {
    cache.set(key, value);
  },

  remove(key: string) {
    cache.delete(key);
  },

  clear() {
    cache.clear();
  },
};
```

### `api/retryRequest.ts`

```ts
// Reusable Retry Logic
import { sleep } from "../utils/sleep";

export async function retryRequest<T>(
  callback: () => Promise<T>,
  retries = 3,
  delay = 1000,
): Promise<T> {
  try {
    return await callback();
  } catch (error) {
    if (retries <= 0) {
      throw error;
    }
    await sleep(delay);
    return retryRequest(callback, retries - 1, delay);
  }
}
```

### `api/requestTimeout.ts`

```ts
// Shared Timeout Utility
export function createTimeoutSignal(timeout = 5000) {
  const controller = new AbortController();
  const timeoutId = setTimeout(() => {
    controller.abort();
  }, timeout);

  return {
    signal: controller.signal,
    clear: () => clearTimeout(timeoutId),
  };
}
```

### `api/abortManager.ts`

```ts
// Shared AbortController Manager
const controllers = new Map<string, AbortController>();

export const abortManager = {
  create(key: string) {
    this.abort(key);
    const controller = new AbortController();
    controllers.set(key, controller);

    return controller;
  },

  abort(key: string) {
    const controller = controllers.get(key);

    if (controller) {
      controller.abort();
      controllers.delete(key);
    }
  },
};
```

### `hooks/useDebounce.ts`

```ts
// Shared Debounce Hook
import { useEffect, useState } from "react";

export function useDebounce<T>(value: T, delay = 400) {
  const [debouncedValue, setDebouncedValue] = useState(value);

  useEffect(() => {
    const timer = setTimeout(() => {
      setDebouncedValue(value);
    }, delay);

    return () => {
      clearTimeout(timer);
    };
  }, [value, delay]);

  return debouncedValue;
}
```

### `hooks/usePagination.ts`

```ts
// Shared Pagination Hook
import { useState } from "react";

export function usePagination(initialPage = 1) {
  const [page, setPage] = useState(initialPage);
  const nextPage = () => {
    setPage((prev) => prev + 1);
  };
  const previousPage = () => {
    setPage((prev) => Math.max(prev - 1, 1));
  };

  return {
    page,
    setPage,
    nextPage,
    previousPage,
  };
}
```

### `api/apiClient.ts`

- Main Reusable Enterprise API Client

```ts id="lxlm5i"
import { ENV } from "../config/env";
import { retryRequest } from "./retryRequest";
import { tokenManager } from "./tokenManager";
import { createTimeoutSignal } from "./requestTimeout";

type ApiClientOptions = RequestInit & {
  retry?: boolean;
  timeout?: number;
  cacheKey?: string;
};

export async function apiClient<T>(
  endpoint: string,
  options: ApiClientOptions = {},
): Promise<T> {
  const { retry = false, timeout = 5000, ...fetchOptions } = options;
  const request = async () => {
    const { signal, clear } = createTimeoutSignal(timeout);

    try {
      const response = await fetch(`${ENV.API_URL}${endpoint}`, {
        ...fetchOptions,
        signal,

        headers: {
          "Content-Type": "application/json",
          Authorization: `Bearer ${tokenManager.getAccessToken()}`,
          ...fetchOptions.headers,
        },
      });

      if (response.status === 401) {
        throw new Error("Unauthorized");
      }
      if (!response.ok) {
        throw new Error(`API Error: ${response.status}`);
      }
      return response.json();
    } finally {
      clear();
    }
  };

  if (retry) {
    return retryRequest(request);
  }

  return request();
}
```

| File Handles        | Responsibility          |
| ------------------- | ----------------------- |
| `env.ts`            | Environment variables   |
| `apiClient.ts`      | Main reusable API layer |
| `retryRequest.ts`   | Retry failed requests   |
| `requestTimeout.ts` | Abort slow requests     |
| `abortManager.ts`   | Cancel old requests     |
| `cacheManager.ts`   | Shared caching          |
| `tokenManager.ts`   | Auth token handling     |
| `useDebounce.ts`    | Debounced values        |
| `usePagination.ts`  | Pagination state        |

| Feature             | Included |
| ------------------- | -------- |
| Reusable API Client | ✅       |
| Environment Config  | ✅       |
| Retry Logic         | ✅       |
| Request Timeout     | ✅       |
| AbortController     | ✅       |
| Token Support       | ✅       |
| Shared Cache        | ✅       |
| Debounce Hook       | ✅       |
| Pagination Hook     | ✅       |
| TypeScript Support  | ✅       |

---

## 📌 Real World Usage

### 📄 Retry Logic

- Payment Verification API
  User paid successfully BUT bank/payment gateway verification API temporarily fails

#### `features/payments/payment.types.ts`

```ts
// Shared Payment Types
export type PaymentStatusResponse = {
  success: boolean;
  paymentId: string;
  orderId: string;
  paymentStatus: "Pending" | "Paid" | "Failed";
  transactionId: string;
};
```

#### `features/payments/paymentApi.ts`

```ts
// Payment APIs
import { apiClient } from "../../api/apiClient";
import { retryRequest } from "../../api/retryRequest";
import { PaymentStatusResponse } from "./payment.types";

export function verifyPayment(paymentId: string) {
  return retryRequest(
    () =>
      apiClient<PaymentStatusResponse>(`/payments/${paymentId}/verify`, {
        method: "GET",
        retry: false,
      }),
    3,
    1500,
  );
}
```

#### `features/payments/PaymentStatus.tsx`

```tsx
// Real UI Component
import { useEffect, useState } from "react";
import { verifyPayment } from "./paymentApi";
import { PaymentStatusResponse } from "./payment.types";

export default function PaymentStatus() {
  const [payment, setPayment] = useState<PaymentStatusResponse | null>(null);
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState("");

  useEffect(() => {
    checkPaymentStatus();
  }, []);

  async function checkPaymentStatus() {
    try {
      setLoading(true);
      setError("");
      const response = await verifyPayment("pay_123456");
      setPayment(response);
    } catch (error) {
      setError("Unable to verify payment");
      console.error(error);
    } finally {
      setLoading(false);
    }
  }

  if (loading) {
    return <p>Verifying payment...</p>;
  }
  if (error) {
    return <p>{error}</p>;
  }
  if (!payment) {
    return null;
  }

  return (
    <div>
      <h2>
        Payment Status:
        {payment.paymentStatus}
      </h2>

      <p>
        Transaction ID:
        {payment.transactionId}
      </p>

      <p>
        Order ID:
        {payment.orderId}
      </p>
    </div>
  );
}
```

### 📄 Request Timeout

- Prevent UI from waiting forever.

#### `features/products/product.types.ts`

```ts
export type Product = {
  id: number;
  title: string;
  price: number;
  thumbnail: string;
};

export type ProductsResponse = {
  products: Product[];
};
```

#### `features/products/productApi.ts`

```ts
// Timeout-Specific API Usage
import { apiClient } from "../../api/apiClient";
import { ProductsResponse } from "./product.types";

export function getProducts() {
  return apiClient<ProductsResponse>("/products", {
    method: "GET",

    timeout: 5000,
  });
}
```

#### `features/products/ProductList.tsx`

```tsx
// Production Component
import { useEffect, useState } from "react";
import { getProducts } from "./productApi";
import { Product } from "./product.types";

export default function ProductList() {
  const [products, setProducts] = useState<Product[]>([]);
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState("");

  useEffect(() => {
    fetchProducts();
  }, []);

  async function fetchProducts() {
    try {
      setLoading(true);
      setError("");
      const response = await getProducts();
      setProducts(response.products);
    } catch (error) {
      if (error instanceof DOMException && error.name === "AbortError") {
        setError("Request timeout. Please try again.");

        return;
      }

      setError("Failed to load products.");
    } finally {
      setLoading(false);
    }
  }
  if (loading) {
    return <p>Loading products...</p>;
  }
  if (error) {
    return <p>{error}</p>;
  }

  return (
    <div>
      {products.map((product) => (
        <div key={product.id}>
          <img src={product.thumbnail} alt={product.title} width={100} />
          <h3>{product.title}</h3>
          <p>${product.price}</p>
        </div>
      ))}
    </div>
  );
}
```

#### Real API

Request: http GET /products
Response:

```json
{
  "products": [
    {
      "id": 1,
      "title": "iPhone 15",
      "price": 999,
      "thumbnail": "/iphone.jpg"
    }
  ]
}
```

### 📄 Debounce Search API

- 5 API requests Without Debounce, With only 1 API requests

#### `features/products/search.types.ts`

```ts
export type Product = {
  id: number;
  title: string;
  price: number;
};

export type SearchProductsResponse = {
  products: Product[];
};
```

#### `features/products/searchApi.ts`

```ts
import { apiClient } from "../../api/apiClient";
import { SearchProductsResponse } from "./search.types";

export function searchProducts(query: string) {
  return apiClient<SearchProductsResponse>(
    `/products/search?q=${encodeURIComponent(query)}`,
    {
      method: "GET",
      timeout: 3000,
    },
  );
}
```

#### `features/products/ProductSearch.tsx`

```tsx
import { useEffect, useState } from "react";
import { useDebounce } from "../../hooks/useDebounce";
import { searchProducts } from "./searchApi";
import { Product } from "./search.types";

export default function ProductSearch() {
  const [search, setSearch] = useState("");
  const [products, setProducts] = useState<Product[]>([]);
  const [loading, setLoading] = useState(false);
  const debouncedSearch = useDebounce(search, 400);

  useEffect(() => {
    if (!debouncedSearch.trim()) {
      setProducts([]);
      return;
    }

    fetchProducts();
  }, [debouncedSearch]);

  async function fetchProducts() {
    try {
      setLoading(true);
      const response = await searchProducts(debouncedSearch);
      setProducts(response.products);
    } finally {
      setLoading(false);
    }
  }

  return (
    <>
      <input
        type="text"
        placeholder="Search products..."
        value={search}
        onChange={(e) => setSearch(e.target.value)}
      />

      {loading && <p>Searching...</p>}

      {products.map((product) => (
        <div key={product.id}>{product.title}</div>
      ))}
    </>
  );
}
```

### 📄 Pagination

#### `features/users/user.types.ts`

```ts
export type User = {
  id: number;
  name: string;
  email: string;
};

export type UsersResponse = {
  users: User[];
  page: number;
  totalPages: number;
  totalItems: number;
};
```

#### `features/users/userApi.ts`

```ts
import { apiClient } from "../../api/apiClient";
import { UsersResponse } from "./user.types";

type GetUsersParams = {
  page: number;
  limit: number;
};

export function getUsers({ page, limit }: GetUsersParams) {
  return apiClient<UsersResponse>(`/users?page=${page}&limit=${limit}`, {
    method: "GET",
    timeout: 5000,
  });
}
```

#### `features/users/UserList.tsx`

```tsx
import { useEffect, useState } from "react";
import { usePagination } from "../../hooks/usePagination";
import { getUsers } from "./userApi";
import { User } from "./user.types";

export default function UserList() {
  const { page, nextPage, previousPage } = usePagination();
  const [users, setUsers] = useState<User[]>([]);
  const [totalPages, setTotalPages] = useState(1);
  const [loading, setLoading] = useState(false);

  useEffect(() => {
    fetchUsers();
  }, [page]);

  async function fetchUsers() {
    try {
      setLoading(true);
      const response = await getUsers({
        page,
        limit: 20,
      });
      setUsers(response.users);
      setTotalPages(response.totalPages);
    } finally {
      setLoading(false);
    }
  }

  return (
    <>
      {loading && <p>Loading...</p>}

      <table>
        <tbody>
          {users.map((user) => (
            <tr key={user.id}>
              <td>{user.name}</td>

              <td>{user.email}</td>
            </tr>
          ))}
        </tbody>
      </table>

      <button disabled={page === 1} onClick={previousPage}>
        Previous
      </button>

      <span>
        Page {page} of {totalPages}
      </span>

      <button disabled={page >= totalPages} onClick={nextPage}>
        Next
      </button>
    </>
  );
}
```

### 📄 Caching

```text
First API call
      ↓
Store in cache
      ↓
Reuse everywhere
```

#### `features/profile/profile.constants.ts`

```ts
export const PROFILE_CACHE_KEY = "profile";
```

#### `features/profile/profile.types.ts`

```ts
export type Profile = {
  id: number;
  name: string;
  email: string;
  role: string;
  avatar: string;
};
```

#### `features/profile/profileApi.ts`

```ts
import { apiClient } from "@/api/apiClient";
import { cacheManager } from "@/api/cacheManager";
import { Profile } from "./profile.types";
import { PROFILE_CACHE_KEY } from "./profile.constants";

const CACHE_TTL = 1000 * 60 * 5;

type CacheEntry<T> = {
  data: T;
  expiresAt: number;
};

export async function getProfile(forceRefresh = false) {
  const cached = cacheManager.get(
    PROFILE_CACHE_KEY,
  ) as CacheEntry<Profile> | null;

  const isValidCache = cached && cached.expiresAt > Date.now();

  if (!forceRefresh && isValidCache) {
    return cached.data;
  }

  const profile = await apiClient<Profile>("/profile");

  cacheManager.set(PROFILE_CACHE_KEY, {
    data: profile,
    expiresAt: Date.now() + CACHE_TTL,
  });

  return profile;
}

export function clearProfileCache() {
  cacheManager.remove(PROFILE_CACHE_KEY);
}
```

#### `features/profile/ProfileCard.tsx`

```tsx
import { useEffect, useState } from "react";
import { getProfile } from "./profileApi";
import { Profile } from "./profile.types";

export default function ProfileCard() {
  const [profile, setProfile] = useState<Profile | null>(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    loadProfile();
  }, []);

  async function loadProfile() {
    try {
      const data = await getProfile();
      setProfile(data);
    } finally {
      setLoading(false);
    }
  }

  if (loading) {
    return <p>Loading...</p>;
  }

  if (!profile) {
    return null;
  }

  return (
    <div>
      <h3>{profile.name}</h3>
      <p>{profile.email}</p>
      <p>{profile.role}</p>
    </div>
  );
}
```

#### `src/features/profile/ProfileUpdate.tsx`

```tsx
import { clearProfileCache } from "./profileApi";

async function handleUpdateProfile(payload: UpdateProfilePayload) {
  await updateProfile(payload);
  clearProfileCache();
}
```

### 📄 Abort Controller

- Cancel old requests and keep only latest request active.

#### `src/features/products/search.types.ts`

```ts
export type Product = {
  id: number;
  title: string;
  price: number;
};

export type SearchProductsResponse = {
  products: Product[];
};
```

#### `src/features/products/searchApi.ts`

```ts
import { apiClient } from "@/api/apiClient";
import { abortManager } from "@/api/abortManager";
import { SearchProductsResponse } from "./search.types";

const SEARCH_REQUEST_KEY = "product-search";

export async function searchProducts(query: string) {
  const controller = abortManager.create(SEARCH_REQUEST_KEY);

  return apiClient<SearchProductsResponse>(
    `/products/search?q=${encodeURIComponent(query)}`,
    {
      method: "GET",
      signal: controller.signal,
    },
  );
}
```

#### `src/features/products/ProductSearch.tsx`

```tsx
import { useEffect, useState } from "react";
import { useDebounce } from "@/hooks/useDebounce";
import { searchProducts } from "./searchApi";
import { Product } from "./search.types";

export default function ProductSearch() {
  const [search, setSearch] = useState("");
  const [products, setProducts] = useState<Product[]>([]);
  const [loading, setLoading] = useState(false);
  const debouncedSearch = useDebounce(search, 400);

  useEffect(() => {
    if (debouncedSearch.trim().length < 2) {
      setProducts([]);
      return;
    }

    fetchProducts();
  }, [debouncedSearch]);

  async function fetchProducts() {
    try {
      setLoading(true);
      const response = await searchProducts(debouncedSearch);

      setProducts(response.products);
    } catch (error) {
      if (error instanceof DOMException && error.name === "AbortError") {
        return;
      }

      console.error(error);
    } finally {
      setLoading(false);
    }
  }

  return (
    <>
      <input
        value={search}
        placeholder="Search products..."
        onChange={(e) => setSearch(e.target.value)}
      />

      {loading && <p>Searching...</p>}

      {products.map((product) => (
        <div key={product.id}>{product.title}</div>
      ))}
    </>
  );
}
```

- search/autocomplete/filter APIs
  Debounce + AbortController
- Responsibilities
  Debounce > Reduces API calls
  AbortController > Cancels outdated requests

```text
// Real Senario
User Types:
i
ip
iph
ipho
iphone

Debounce
↓
Only 1 API request sent

User changes to:
iphone 15

AbortController
↓
Cancel previous request
↓
Start new request
↓
Show latest results only
```

### 📄 Refresh Token

```txt
User logged in at 9:00 AM
Access Token > Expires after 15 minutes

User continues using application >
API returns 401 >
Refresh Token API called >
New Access Token generated >
Original API retried >
User remains logged in
```

#### `src/features/auth/auth.types.ts`

```ts
export type RefreshTokenResponse = {
  accessToken: string;
};
```

#### `src/features/auth/authApi.ts`

```ts
import { ENV } from "@/config/env";
import { tokenManager } from "@/api/tokenManager";
import { RefreshTokenResponse } from "./auth.types";

export async function refreshAccessToken() {
  const refreshToken = tokenManager.getRefreshToken();
  const response = await fetch(`${ENV.API_URL}/auth/refresh-token`, {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
    },
    body: JSON.stringify({
      refreshToken,
    }),
  });

  if (!response.ok) {
    throw new Error("Refresh token failed");
  }

  const data = (await response.json()) as RefreshTokenResponse;
  tokenManager.setAccessToken(data.accessToken);
  return data.accessToken;
}
```

#### `src/api/apiClient.ts`

```ts
import { ENV } from "@/config/env";
import { tokenManager } from "./tokenManager";
import { refreshAccessToken } from "@/features/auth/authApi";

export async function apiClient<T>(
  endpoint: string,
  options: RequestInit = {},
): Promise<T> {
  const executeRequest = async () => {
    return fetch(`${ENV.API_URL}${endpoint}`, {
      ...options,
      headers: {
        "Content-Type": "application/json",
        Authorization: `Bearer ${tokenManager.getAccessToken()}`,
        ...options.headers,
      },
    });
  };

  let response = await executeRequest();

  if (response.status === 401) {
    const newToken = await refreshAccessToken();

    response = await fetch(`${ENV.API_URL}${endpoint}`, {
      ...options,

      headers: {
        "Content-Type": "application/json",
        Authorization: `Bearer ${newToken}`,
        ...options.headers,
      },
    });
  }

  if (!response.ok) {
    throw new Error(`API Error: ${response.status}`);
  }

  return response.json();
}
```

#### `src/features/profile/profileApi.ts`

```ts
import { apiClient } from "@/api/apiClient";
import { Profile } from "./profile.types";

export function getProfile() {
  return apiClient<Profile>("/profile");
}
```

#### `src/features/profile/ProfileCard.tsx`

```tsx
import { useEffect, useState } from "react";
import { getProfile } from "./profileApi";
import { Profile } from "./profile.types";

export default function ProfileCard() {
  const [profile, setProfile] = useState<Profile | null>(null);
  useEffect(() => {
    loadProfile();
  }, []);

  async function loadProfile() {
    const data = await getProfile();
    setProfile(data);
  }

  if (!profile) {
    return <p>Loading...</p>;
  }

  return (
    <div>
      <h3>{profile.name}</h3>
    </div>
  );
}
```

### 📄 Users Entry/View

```txt
User Profile Form

User enters:
- Name
- Email
- Phone

Click Save >
POST API >
Response received >
Display updated info on same page
```

#### `src/features/profile/profile.types.ts`

```ts
export type Profile = {
  id: number;
  name: string;
  email: string;
  phone: string;
};

export type SaveProfilePayload = {
  name: string;
  email: string;
  phone: string;
};
```

#### `src/features/profile/profileApi.ts`

```ts
import { apiClient } from "@/api/apiClient";
import { Profile, SaveProfilePayload } from "./profile.types";

export function saveProfile(payload: SaveProfilePayload) {
  return apiClient<Profile>("/profile", {
    method: "POST",
    body: JSON.stringify(payload),
  });
}
```

#### `src/features/profile/ProfilePage.tsx`

```tsx
import { useState } from "react";
import { saveProfile } from "./profileApi";
import { Profile, SaveProfilePayload } from "./profile.types";

export default function ProfilePage() {
  const [form, setForm] = useState<SaveProfilePayload>({
    name: "",
    email: "",
    phone: "",
  });
  const [profile, setProfile] = useState<Profile | null>(null);
  const [loading, setLoading] = useState(false);

  async function handleSubmit(e: React.FormEvent) {
    e.preventDefault();

    try {
      setLoading(true);
      const response = await saveProfile(form);

      setProfile(response);
    } finally {
      setLoading(false);
    }
  }

  function handleChange(e: React.ChangeEvent<HTMLInputElement>) {
    setForm((prev) => ({
      ...prev,
      [e.target.name]: e.target.value,
    }));
  }

  return (
    <div>
      <form onSubmit={handleSubmit}>
        <input
          name="name"
          value={form.name}
          onChange={handleChange}
          placeholder="Name"
        />

        <input
          name="email"
          value={form.email}
          onChange={handleChange}
          placeholder="Email"
        />

        <input
          name="phone"
          value={form.phone}
          onChange={handleChange}
          placeholder="Phone"
        />

        <button type="submit" disabled={loading}>
          {loading ? "Saving..." : "Save"}
        </button>
      </form>

      {profile && (
        <div>
          <h3>Saved Profile</h3>
          <p>{profile.name}</p>
          <p>{profile.email}</p>
          <p>{profile.phone}</p>
        </div>
      )}
    </div>
  );
}
```

---

## 📌 More Examples

### 📄 CRUD (Create / Read / Update / Delete)

#### `src/features/users/user.types.ts`

```ts
export type User = {
  id: number;
  name: string;
  email: string;
};

export type CreateUserPayload = {
  name: string;
  email: string;
};

export type UpdateUserPayload = CreateUserPayload;
```

#### `src/features/users/userApi.ts`

```ts
import { apiClient } from "@/api/apiClient";
import { User, CreateUserPayload, UpdateUserPayload } from "./user.types";

export function getUsers() {
  return apiClient<User[]>("/users");
}

export function createUser(payload: CreateUserPayload) {
  return apiClient<User>("/users", {
    method: "POST",
    body: JSON.stringify(payload),
  });
}

export function updateUser(userId: number, payload: UpdateUserPayload) {
  return apiClient<User>(`/users/${userId}`, {
    method: "PUT",
    body: JSON.stringify(payload),
  });
}

export function deleteUser(userId: number) {
  return apiClient<void>(`/users/${userId}`, {
    method: "DELETE",
  });
}
```

#### `src/features/users/UserList.tsx`

```tsx
// READ
import { useEffect, useState } from "react";
import { getUsers } from "./userApi";
import { User } from "./user.types";

export default function UserList() {
  const [users, setUsers] = useState<User[]>([]);

  useEffect(() => {
    loadUsers();
  }, []);

  async function loadUsers() {
    const data = await getUsers();

    setUsers(data);
  }

  return (
    <div>
      {users.map((user) => (
        <div key={user.id}>{user.name}</div>
      ))}
    </div>
  );
}
```

#### `src/features/users/UserForm.tsx`

```tsx
// CREATE-UPDATE
import { useState } from "react";
import { createUser, updateUser } from "./userApi";
import { User } from "./user.types";

type Props = {
  initialValues?: User;
};

export default function UserForm({ initialValues }: Props) {
  // determine create vs update mode
  const isEditMode = Boolean(initialValues?.id);
  const [name, setName] = useState(initialValues?.name ?? "");
  const [email, setEmail] = useState(initialValues?.email ?? "");

  // handle create/update submit
  async function handleSubmit(e: React.FormEvent) {
    e.preventDefault();

    const payload = {
      name,
      email,
    };

    // update existing user
    if (isEditMode && initialValues) {
      await updateUser(initialValues.id, payload);
      return;
    }

    // create new user
    await createUser(payload);

    // reset form after create
    setName("");
    setEmail("");
  }

  return (
    <form onSubmit={handleSubmit}>
      <input
        value={name}
        onChange={(e) => setName(e.target.value)}
        placeholder="Name"
      />

      <input
        value={email}
        onChange={(e) => setEmail(e.target.value)}
        placeholder="Email"
      />

      <button type="submit">
        {isEditMode ? "Update User" : "Create User"}
      </button>
    </form>
  );
}
```

#### `src/features/users/DeleteUserButton.tsx`

```tsx
// DELETE
import { deleteUser } from "./userApi";

type Props = {
  userId: number;
};

export default function DeleteUserButton({ userId }: Props) {
  async function handleDelete() {
    await deleteUser(userId);
  }

  return <button onClick={handleDelete}>Delete</button>;
}
```

#### Partial Update (PATCH)

```tsx
export function updateUser(
  userId: number,
  payload: Partial<UpdateUserPayload>,
) {
  return apiClient<User>(`/users/${userId}`, {
    method: "PATCH",
    body: JSON.stringify(payload),
  });
}
```

### 📄 File Upload

#### `src/features/profile/profile.types.ts`

```ts
export type UploadImageResponse = {
  imageUrl: string;
};
```

#### `src/features/profile/profileApi.ts`

```ts
import { apiClient } from "@/api/apiClient";
import { UploadImageResponse } from "./profile.types";

export async function uploadProfileImage(file: File) {
  const formData = new FormData();
  formData.append("image", file);

  return apiClient<UploadImageResponse>("/uploads/profile-image", {
    method: "POST",
    body: formData,
    headers: {},
  });
}
```

#### `src/features/profile/ProfileImageUpload.tsx`

```tsx
import { useState } from "react";
import { uploadProfileImage } from "./profileApi";

export default function ProfileImageUpload() {
  const [imageUrl, setImageUrl] = useState("");
  const [loading, setLoading] = useState(false);

  async function handleChange(e: React.ChangeEvent<HTMLInputElement>) {
    const file = e.target.files?.[0];

    if (!file) {
      return;
    }

    try {
      setLoading(true);
      const response = await uploadProfileImage(file);
      setImageUrl(response.imageUrl);
    } finally {
      setLoading(false);
    }
  }

  return (
    <>
      <input type="file" accept="image/*" onChange={handleChange} />
      {loading && <p>Uploading...</p>}
      {imageUrl && <img src={imageUrl} alt="Profile" width={150} />}
    </>
  );
}
```

#### `src/api/apiClient.ts`

```ts
const isFormData =
  options.body instanceof FormData;

headers: {
  ...(isFormData
    ? {}
    : {
        "Content-Type":
          "application/json",
      }),

  ...options.headers,
}
```

### 📄 Infinite Scroll

#### `src/features/products/product.types.ts`

```ts
export type Product = {
  id: number;
  title: string;
  price: number;
};

export type ProductsResponse = {
  data: Product[];
  page: number;
  totalPages: number;
};
```

#### `src/features/products/productApi.ts`

```ts
import { apiClient } from "@/api/apiClient";
import { ProductsResponse } from "./product.types";

export function getProducts(page: number) {
  return apiClient<ProductsResponse>(`/products?page=${page}&limit=20`);
}
```

#### `src/features/products/ProductList.tsx`

```tsx
import { useEffect, useRef, useState } from "react";
import { getProducts } from "./productApi";
import { Product } from "./product.types";

export default function ProductList() {
  const [products, setProducts] = useState<Product[]>([]);
  const [page, setPage] = useState(1);
  const [hasMore, setHasMore] = useState(true);
  const observerRef = useRef<HTMLDivElement>(null);

  useEffect(() => {
    loadProducts();
  }, [page]);

  async function loadProducts() {
    const response = await getProducts(page);

    setProducts((prev) => [...prev, ...response.data]);
    setHasMore(page < response.totalPages);
  }

  useEffect(() => {
    const observer = new IntersectionObserver(([entry]) => {
      if (entry.isIntersecting && hasMore) {
        setPage((prev) => prev + 1);
      }
    });

    if (observerRef.current) {
      observer.observe(observerRef.current);
    }

    return () => observer.disconnect();
  }, [hasMore]);

  return (
    <>
      {products.map((product) => (
        <div key={product.id}>{product.title}</div>
      ))}
      <div ref={observerRef} />
    </>
  );
}
```

### 📄 Server-Side Filtering

#### `src/features/users/user.types.ts`

```ts
export type User = {
  id: number;
  name: string;
  email: string;
  status: "active" | "inactive";
  role: string;
};

export type UsersResponse = {
  data: User[];
};
```

#### `src/features/users/userApi.ts`

```ts
import { apiClient } from "@/api/apiClient";
import { UsersResponse } from "./user.types";

type GetUsersParams = {
  status?: string;
  role?: string;
};

export function getUsers(params: GetUsersParams) {
  const searchParams = new URLSearchParams();

  if (params.status) {
    searchParams.append("status", params.status);
  }

  if (params.role) {
    searchParams.append("role", params.role);
  }

  return apiClient<UsersResponse>(`/users?${searchParams.toString()}`);
}
```

#### `src/features/users/UserList.tsx`

```tsx
import { useEffect, useState } from "react";
import { getUsers } from "./userApi";
import { User } from "./user.types";

export default function UserList() {
  const [users, setUsers] = useState<User[]>([]);
  const [status, setStatus] = useState("");

  useEffect(() => {
    loadUsers();
  }, [status]);

  async function loadUsers() {
    const response = await getUsers({
      status,
    });

    setUsers(response.data);
  }

  return (
    <>
      <select value={status} onChange={(e) => setStatus(e.target.value)}>
        <option value="">All</option>
        <option value="active">Active</option>
        <option value="inactive">Inactive</option>
      </select>

      {users.map((user) => (
        <div key={user.id}>{user.name}</div>
      ))}
    </>
  );
}
```

### 📄 Server-Side Sorting

#### `src/features/users/user.types.ts`

```ts
export type User = {
  id: number;
  name: string;
  email: string;
  createdAt: string;
};

export type UsersResponse = {
  data: User[];
};
```

#### `src/features/users/userApi.ts`

```ts
import { apiClient } from "@/api/apiClient";
import { UsersResponse } from "./user.types";

type GetUsersParams = {
  sort?: string;
  order?: "asc" | "desc";
};

export function getUsers(params: GetUsersParams) {
  const searchParams = new URLSearchParams();

  if (params.sort) {
    searchParams.append("sort", params.sort);
  }

  if (params.order) {
    searchParams.append("order", params.order);
  }

  return apiClient<UsersResponse>(`/users?${searchParams.toString()}`);
}
```

#### `src/features/users/UserList.tsx`

```tsx
import { useEffect, useState } from "react";
import { getUsers } from "./userApi";
import { User } from "./user.types";

export default function UserList() {
  const [users, setUsers] = useState<User[]>([]);
  const [sort, setSort] = useState("createdAt");
  const [order, setOrder] = useState<"asc" | "desc">("desc");

  useEffect(() => {
    loadUsers();
  }, [sort, order]);

  async function loadUsers() {
    const response = await getUsers({
      sort,
      order,
    });

    setUsers(response.data);
  }

  return (
    <>
      <select value={sort} onChange={(e) => setSort(e.target.value)}>
        <option value="name">Name</option>
        <option value="createdAt">Created Date</option>
      </select>

      <select
        value={order}
        onChange={(e) => setOrder(e.target.value as "asc" | "desc")}
      >
        <option value="asc">Ascending</option>
        <option value="desc">Descending</option>
      </select>

      {users.map((user) => (
        <div key={user.id}>{user.name}</div>
      ))}
    </>
  );
}
```

### 📄 Search + Filter + Sort + Pagination

#### `src/features/users/user.types.ts`

```ts
export type User = {
  id: number;
  name: string;
  email: string;
  status: "active" | "inactive";
  createdAt: string;
};

export type UsersResponse = {
  data: User[];
  page: number;
  totalPages: number;
  totalItems: number;
};
```

#### `src/features/users/userApi.ts`

```ts
import { apiClient } from "@/api/apiClient";
import { UsersResponse } from "./user.types";

type GetUsersParams = {
  page: number;
  limit: number;
  search?: string;
  status?: string;
  sort?: string;
  order?: "asc" | "desc";
};

export function getUsers(params: GetUsersParams) {
  const searchParams = new URLSearchParams();

  searchParams.append("page", String(params.page));
  searchParams.append("limit", String(params.limit));

  if (params.search) {
    searchParams.append("search", params.search);
  }
  if (params.status) {
    searchParams.append("status", params.status);
  }
  if (params.sort) {
    searchParams.append("sort", params.sort);
  }
  if (params.order) {
    searchParams.append("order", params.order);
  }

  return apiClient<UsersResponse>(`/users?${searchParams.toString()}`);
}
```

#### `src/features/users/UserList.tsx`

```tsx
import { useEffect, useState } from "react";
import { useDebounce } from "@/hooks/useDebounce";
import { getUsers } from "./userApi";
import { User } from "./user.types";

const PAGE_SIZE = 20;

export default function UserList() {
  const [users, setUsers] = useState<User[]>([]);
  const [page, setPage] = useState(1);
  const [totalPages, setTotalPages] = useState(1);
  const [search, setSearch] = useState("");
  const [status, setStatus] = useState("");
  const [sort, setSort] = useState("createdAt");
  const [order, setOrder] = useState<"asc" | "desc">("desc");
  const debouncedSearch = useDebounce(search, 400);

  useEffect(() => {
    loadUsers();
  }, [page, debouncedSearch, status, sort, order]);

  async function loadUsers() {
    const response = await getUsers({
      page,
      limit: PAGE_SIZE,
      search: debouncedSearch,
      status,
      sort,
      order,
    });

    setUsers(response.data);
    setTotalPages(response.totalPages);
  }

  function handleSearch(value: string) {
    setPage(1);
    setSearch(value);
  }

  function handleStatusChange(value: string) {
    setPage(1);
    setStatus(value);
  }

  return (
    <>
      <input
        placeholder="Search users..."
        value={search}
        onChange={(e) => handleSearch(e.target.value)}
      />

      <select
        value={status}
        onChange={(e) => handleStatusChange(e.target.value)}
      >
        <option value="">All</option>

        <option value="active">Active</option>

        <option value="inactive">Inactive</option>
      </select>

      <select value={sort} onChange={(e) => setSort(e.target.value)}>
        <option value="createdAt">Created Date</option>

        <option value="name">Name</option>
      </select>

      <select
        value={order}
        onChange={(e) => setOrder(e.target.value as "asc" | "desc")}
      >
        <option value="desc">Desc</option>

        <option value="asc">Asc</option>
      </select>

      {users.map((user) => (
        <div key={user.id}>{user.name}</div>
      ))}

      <button disabled={page === 1} onClick={() => setPage((prev) => prev - 1)}>
        Previous
      </button>

      <span>
        {page} / {totalPages}
      </span>

      <button
        disabled={page >= totalPages}
        onClick={() => setPage((prev) => prev + 1)}
      >
        Next
      </button>
    </>
  );
}
```

#### API Request

```http
GET /users
?page=1
&limit=20
&search=john
&status=active
&sort=createdAt
&order=desc
```

#### API Response

```json
{
  "data": [
    {
      "id": 1,
      "name": "John Doe",
      "email": "john@test.com",
      "status": "active",
      "createdAt": "2026-01-10"
    }
  ],
  "page": 1,
  "totalPages": 25,
  "totalItems": 500
}
```

### 📄 Optimistic Updates

- Small UI state changes
- Wishlist, Like Post, Bookmark Article

#### `src/features/products/product.types.ts`

```ts
export type Product = {
  id: number;
  title: string;
  isWishlisted: boolean;
};
```

#### `src/features/products/productApi.ts`

```ts
import { apiClient } from "@/api/apiClient";

export function toggleWishlist(productId: number) {
  return apiClient<void>(`/products/${productId}/wishlist`, {
    method: "POST",
  });
}
```

#### `src/features/products/ProductCard.tsx`

```tsx
import { useState } from "react";
import { toggleWishlist } from "./productApi";
import { Product } from "./product.types";

type Props = {
  product: Product;
};

export default function ProductCard({ product }: Props) {
  const [isWishlisted, setIsWishlisted] = useState(product.isWishlisted);

  async function handleWishlist() {
    const previousState = isWishlisted;

    // optimistic update
    setIsWishlisted(!previousState);

    try {
      await toggleWishlist(product.id);
    } catch {
      // rollback on failure
      setIsWishlisted(previousState);
    }
  }

  return <button onClick={handleWishlist}>{isWishlisted ? "❤️" : "🤍"}</button>;
}
```

### 📄 Batch APIs

- Delete Multiple Users
- Activate Selected Users

#### `src/features/users/user.types.ts`

```ts
export type User = {
  id: number;
  name: string;
  email: string;
};

export type BulkDeleteUsersPayload = {
  ids: number[];
};
```

#### `src/features/users/userApi.ts`

```ts
import { apiClient } from "@/api/apiClient";
import { BulkDeleteUsersPayload } from "./user.types";

export function bulkDeleteUsers(payload: BulkDeleteUsersPayload) {
  return apiClient<void>("/users/bulk-delete", {
    method: "POST",
    body: JSON.stringify(payload),
  });
}
```

#### `src/features/users/UserList.tsx`

```tsx
import { useState } from "react";
import { bulkDeleteUsers } from "./userApi";
import { User } from "./user.types";

type Props = {
  initialUsers: User[];
};

export default function UserList({ initialUsers }: Props) {
  const [users, setUsers] = useState(initialUsers);
  const [selectedIds, setSelectedIds] = useState<number[]>([]);

  function toggleSelection(userId: number) {
    setSelectedIds((prev) =>
      prev.includes(userId)
        ? prev.filter((id) => id !== userId)
        : [...prev, userId],
    );
  }

  async function handleBulkDelete() {
    if (!selectedIds.length) {
      return;
    }

    await bulkDeleteUsers({
      ids: selectedIds,
    });

    setUsers((prev) => prev.filter((user) => !selectedIds.includes(user.id)));
    setSelectedIds([]);
  }

  return (
    <>
      <button disabled={!selectedIds.length} onClick={handleBulkDelete}>
        Delete Selected
      </button>

      {users.map((user) => (
        <div key={user.id}>
          <input
            type="checkbox"
            checked={selectedIds.includes(user.id)}
            onChange={() => toggleSelection(user.id)}
          />

          {user.name}
        </div>
      ))}
    </>
  );
}
```

```http
POST /users/bulk-delete
```

```json
{
  "ids": [1, 2, 3]
}
```

### 📄 Export APIs

- Admin Users Page > Filters Applied > Export CSV

#### `src/features/users/userApi.ts`

```ts
import { ENV } from "@/config/env";

export async function exportUsers(params: {
  search?: string;
  status?: string;
}) {
  const searchParams = new URLSearchParams();

  if (params.search) {
    searchParams.append("search", params.search);
  }

  if (params.status) {
    searchParams.append("status", params.status);
  }

  const response = await fetch(
    `${ENV.API_URL}/users/export?${searchParams.toString()}`,
  );

  if (!response.ok) {
    throw new Error("Export failed");
  }

  return response.blob();
}
```

#### `src/features/users/UserList.tsx`

```tsx
import { exportUsers } from "./userApi";

async function handleExport() {
  const file = await exportUsers({
    status: "active",
  });

  const url = window.URL.createObjectURL(file);
  const link = document.createElement("a");

  link.href = url;
  link.download = "users.csv";
  link.click();

  window.URL.revokeObjectURL(url);
}
```

```tsx
<button onClick={handleExport}>Export CSV</button>
```

### 📄 Dashboard Aggregation APIs

- Because dashboards usually need data from multiple tables/services.
- Users Card, Orders Card, Revenue Card, Pending Orders Card (Frontend waits for 4 API calls.)
- Usually backend creates a dedicated dashboard endpoint.

#### `src/features/dashboard/dashboard.types.ts`

```ts
export type DashboardSummary = {
  totalUsers: number;
  totalOrders: number;
  totalRevenue: number;
  pendingOrders: number;
  activeUsers: number;
};
```

#### `src/features/dashboard/dashboardApi.ts`

```ts
import { apiClient } from "@/api/apiClient";
import { DashboardSummary } from "./dashboard.types";

export function getDashboardSummary() {
  return apiClient<DashboardSummary>("/dashboard");
}
```

#### `src/features/dashboard/Dashboard.tsx`

```tsx
import { useEffect, useState } from "react";
import { getDashboardSummary } from "./dashboardApi";
import { DashboardSummary } from "./dashboard.types";

export default function Dashboard() {
  const [summary, setSummary] = useState<DashboardSummary | null>(null);

  useEffect(() => {
    loadDashboard();
  }, []);

  async function loadDashboard() {
    const data = await getDashboardSummary();
    setSummary(data);
  }

  if (!summary) {
    return <p>Loading...</p>;
  }

  return (
    <>
      <div>
        Users:
        {summary.totalUsers}
      </div>

      <div>
        Orders:
        {summary.totalOrders}
      </div>

      <div>Revenue: ₹{summary.totalRevenue}</div>

      <div>
        Pending:
        {summary.pendingOrders}
      </div>
    </>
  );
}
```

### 📄 Dependent Dropdown APIs

#### `src/features/location/location.types.ts`

```ts
export type Country = {
  id: number;
  name: string;
};

export type State = {
  id: number;
  name: string;
};

export type City = {
  id: number;
  name: string;
};
```

#### `src/features/location/locationApi.ts`

```ts
import { apiClient } from "@/api/apiClient";
import { Country, State, City } from "./location.types";

export function getCountries() {
  return apiClient<Country[]>("/countries");
}

export function getStates(countryId: number) {
  return apiClient<State[]>(`/states?countryId=${countryId}`);
}

export function getCities(stateId: number) {
  return apiClient<City[]>(`/cities?stateId=${stateId}`);
}
```

#### `src/features/location/LocationForm.tsx`

```tsx
import { useEffect, useState } from "react";
import { getCountries, getStates, getCities } from "./locationApi";
import { Country, State, City } from "./location.types";

export default function LocationForm() {
  const [countries, setCountries] = useState<Country[]>([]);
  const [states, setStates] = useState<State[]>([]);
  const [cities, setCities] = useState<City[]>([]);
  const [countryId, setCountryId] = useState("");
  const [stateId, setStateId] = useState("");

  useEffect(() => {
    loadCountries();
  }, []);

  useEffect(() => {
    if (!countryId) {
      return;
    }

    loadStates(Number(countryId));

    setStateId("");
    setCities([]);
  }, [countryId]);

  useEffect(() => {
    if (!stateId) {
      return;
    }

    loadCities(Number(stateId));
  }, [stateId]);

  async function loadCountries() {
    const data = await getCountries();
    setCountries(data);
  }

  async function loadStates(countryId: number) {
    const data = await getStates(countryId);
    setStates(data);
  }

  async function loadCities(stateId: number) {
    const data = await getCities(stateId);
    setCities(data);
  }

  return (
    <>
      <select value={countryId} onChange={(e) => setCountryId(e.target.value)}>
        <option value="">Select Country</option>

        {countries.map((country) => (
          <option key={country.id} value={country.id}>
            {country.name}
          </option>
        ))}
      </select>

      <select
        value={stateId}
        onChange={(e) => setStateId(e.target.value)}
        disabled={!countryId}
      >
        <option value="">Select State</option>

        {states.map((state) => (
          <option key={state.id} value={state.id}>
            {state.name}
          </option>
        ))}
      </select>

      <select disabled={!stateId}>
        <option value="">Select City</option>

        {cities.map((city) => (
          <option key={city.id} value={city.id}>
            {city.name}
          </option>
        ))}
      </select>
    </>
  );
}
```

```txt
- Frontend:
Handle dropdown changes
Call APIs
Populate options

- Backend:
Return filtered records
based on selected parent value
```

### 📄 Feature Flags

```txt
New Dashboard UI

Some users: ✓ See New Dashboard
Other users: ✓ See Old Dashboard

Without redeploying frontend.
```

#### `src/features/featureFlags/featureFlag.types.ts`

```ts
export type FeatureFlags = {
  enableNewDashboard: boolean;
  enableChatSupport: boolean;
  enableAiAssistant: boolean;
};
```

#### `src/features/featureFlags/featureFlagApi.ts`

```ts
import { apiClient } from "@/api/apiClient";
import { FeatureFlags } from "./featureFlag.types";

export function getFeatureFlags() {
  return apiClient<FeatureFlags>("/feature-flags");
}
```

#### `src/features/featureFlags/FeatureFlagProvider.tsx`

```tsx
import { createContext, useContext, useEffect, useState } from "react";
import { getFeatureFlags } from "./featureFlagApi";
import { FeatureFlags } from "./featureFlag.types";

const FeatureFlagContext = createContext<FeatureFlags | null>(null);

export function FeatureFlagProvider({ children }: React.PropsWithChildren) {
  const [flags, setFlags] = useState<FeatureFlags | null>(null);

  useEffect(() => {
    loadFlags();
  }, []);

  async function loadFlags() {
    const data = await getFeatureFlags();
    setFlags(data);
  }

  if (!flags) {
    return null;
  }

  return (
    <FeatureFlagContext.Provider value={flags}>
      {children}
    </FeatureFlagContext.Provider>
  );
}

export function useFeatureFlags() {
  const flags = useContext(FeatureFlagContext);

  if (!flags) {
    throw new Error("Feature flags not loaded");
  }

  return flags;
}
```

#### `src/App.tsx`

```tsx
import { FeatureFlagProvider } from "@/features/featureFlags/FeatureFlagProvider";

export default function App() {
  return (
    <FeatureFlagProvider>
      <Dashboard />
    </FeatureFlagProvider>
  );
}
```

#### `src/features/dashboard/Dashboard.tsx`

```tsx
import { useFeatureFlags } from "@/features/featureFlags/FeatureFlagProvider";

export default function Dashboard() {
  const flags = useFeatureFlags();

  return flags.enableNewDashboard ? <NewDashboard /> : <OldDashboard />;
}
```

### 📄 Notifications

```txt
Scenarios: New Order, New Message, Payment Received, Ticket Assigned, Lead Assigned, System Alert
Page Load > Fetch Notifications
Every 30 Seconds > Fetch Notifications
Frontend: Display Notifications, Mark Read, Unread Count
```

#### `src/features/notifications/notification.types.ts`

```ts
export type Notification = {
  id: number;
  title: string;
  message: string;
  isRead: boolean;
  createdAt: string;
};

export type NotificationsResponse = {
  data: Notification[];
  unreadCount: number;
};
```

#### `src/features/notifications/notificationApi.ts`

```ts
import { apiClient } from "@/api/apiClient";
import { NotificationsResponse } from "./notification.types";

export function getNotifications() {
  return apiClient<NotificationsResponse>("/notifications");
}

export function markNotificationRead(notificationId: number) {
  return apiClient<void>(`/notifications/${notificationId}/read`, {
    method: "PATCH",
  });
}
```

#### `src/features/notifications/NotificationBell.tsx`

```tsx
import { useEffect, useState } from "react";
import { getNotifications, markNotificationRead } from "./notificationApi";
import { Notification } from "./notification.types";

export default function NotificationBell() {
  const [notifications, setNotifications] = useState<Notification[]>([]);
  const [unreadCount, setUnreadCount] = useState(0);

  useEffect(() => {
    loadNotifications();
  }, []);

  async function loadNotifications() {
    const response = await getNotifications();
    setNotifications(response.data);
    setUnreadCount(response.unreadCount);
  }

  async function handleRead(notificationId: number) {
    await markNotificationRead(notificationId);

    setNotifications((prev) =>
      prev.map((item) =>
        item.id === notificationId
          ? {
              ...item,
              isRead: true,
            }
          : item,
      ),
    );

    setUnreadCount((prev) => Math.max(prev - 1, 0));
  }

  return (
    <>
      <button>🔔 ({unreadCount})</button>

      {notifications.map((notification) => (
        <div key={notification.id}>
          <p>{notification.title}</p>

          {!notification.isRead && (
            <button onClick={() => handleRead(notification.id)}>
              Mark Read
            </button>
          )}
        </div>
      ))}
    </>
  );
}
```

### 📄 WebSocket APIs

- Real-time two-way communication between client and server

```txt
Scenarios: Chat Messages, Trading Apps, Live Scores, Notifications, Order Tracking, Collaborative Editing
Connection: Client Connects > WebSocket Open > Server Pushes Updates > UI Updates Instantly
Common Events: message, notification, order-updated, stock-price-updated, user-online

Popular Libraries: Native WebSocket, Socket.IO
Examples: WhatsApp, Zerodha Kite, Google Docs, Slack, Teams, Live Sports Apps
```

#### `src/features/chat/chat.types.ts`

```ts
export type ChatMessage = {
  id: string;
  userId: string;
  text: string;
  createdAt: string;
};
```

#### `src/features/chat/chatSocket.ts`

```ts
const socket = new WebSocket("wss://api.company.com/chat");

export function connectChat() {
  return socket;
}

export function sendMessage(message: string) {
  socket.send(
    JSON.stringify({
      type: "message",
      text: message,
    }),
  );
}
```

#### `src/features/chat/ChatPage.tsx`

```tsx
import { useEffect, useState } from "react";
import { connectChat, sendMessage } from "./chatSocket";
import { ChatMessage } from "./chat.types";

export default function ChatPage() {
  const [messages, setMessages] = useState<ChatMessage[]>([]);
  const [text, setText] = useState("");

  useEffect(() => {
    const socket = connectChat();

    socket.onmessage = (event) => {
      const message = JSON.parse(event.data);
      setMessages((prev) => [...prev, message]);
    };

    return () => {
      socket.close();
    };
  }, []);

  function handleSend() {
    if (!text.trim()) {
      return;
    }
    sendMessage(text);
    setText("");
  }

  return (
    <>
      {messages.map((message) => (
        <div key={message.id}>{message.text}</div>
      ))}
      <input value={text} onChange={(e) => setText(e.target.value)} />

      <button onClick={handleSend}>Send</button>
    </>
  );
}
```

---

## 📌 Axios

- Axios is a Promise-based HTTP client that simplifies API communication by providing automatic JSON parsing, interceptors, request configuration, and better error handling than fetch().

| Item        | Description                   |
| ----------- | ----------------------------- |
| Purpose     | HTTP Client For APIs          |
| Works In    | Browser + Node.js             |
| Supports    | GET, POST, PUT, PATCH, DELETE |
| Returns     | Promise                       |
| Alternative | Native `fetch()`              |

```bash
npm install axios
```

```js
// Import
import axios from "axios";
```

| Common Methods   | Purpose                |
| ---------------- | ---------------------- |
| `axios.get()`    | Read Data              |
| `axios.post()`   | Create Data            |
| `axios.put()`    | Update Entire Resource |
| `axios.patch()`  | Partial Update         |
| `axios.delete()` | Delete Resource        |

### Examples

```js
// GET Request
const res = await axios.get("/users");
console.log(res.data);

// POST Request
await axios.post("/users", {
  name: "John",
});

// PUT Request
await axios.put("/users/1", {
  name: "John",
});

// PATCH Request
await axios.patch("/users/1", {
  name: "John",
});

// DELETE Request
await axios.delete("/users/1");
```

- Query Params

```js
axios.get("/users", {
  params: {
    page: 1,
    limit: 10,
  },
});

// Generated URL: /users?page=1&limit=10
```

- Headers

```js
axios.get("/users", {
  headers: {
    Authorization: `Bearer ${token}`,
  },
});
```

- Create API Instance

```js
const api = axios.create({
  baseURL: "https://api.com",
});

// Usage:
api.get("/users");
api.post("/users");
```

- Interceptors (JWT Tokens, Logging, Error Handling)

```js
api.interceptors.request.use((config) => {
  config.headers.Authorization = `Bearer ${token}`;

  return config;
});
```

- Typical Project Structure

```txt
src
├─ api
│  └─ axios.js
├─ services
│  └─ userService.js
├─ pages
└─ components
```

### Response Object

| Property  | Purpose                 | Example                       |
| --------- | ----------------------- | ----------------------------- |
| `data`    | API Data                | `res.data.users`              |
| `status`  | HTTP Status Code        | `200`, `404`, `500`           |
| `headers` | Response Headers        | `res.headers["content-type"]` |
| `config`  | Original Request Config | `res.config.url`              |

```js
const res = await axios.get("/users");
console.log(res.data); // API data
console.log(res.status); // 200
console.log(res.headers["content-type"]); // application/json
console.log(res.config.url); // /users
```

### Axios vs Fetch

| Feature            | Axios        | Fetch           |
| ------------------ | ------------ | --------------- |
| Built Into Browser | ❌           | ✅              |
| JSON Parsing       | ✅ Automatic | ❌ `res.json()` |
| Request Timeout    | ✅           | ❌              |
| Interceptors       | ✅           | ❌              |
| Error Handling     | Better       | Basic           |
| File Uploads       | ✅           | ✅              |

---
