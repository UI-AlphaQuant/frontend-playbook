## 📌 Real-World Production Improvements

| Feature             | Why                       | Standard Example                               |
| ------------------- | ------------------------- | ---------------------------------------------- |
| Retry Logic         | Handle temporary failures | Retry API 2-3 times for network/500 errors     |
| Request Timeout     | Prevent infinite waiting  | Abort request after 5s using `AbortController` |
| Debounce Search API | Reduce API calls          | Wait 300ms before search request               |
| Pagination          | Large data handling       | `?page=1&limit=10`                             |
| Caching             | Better performance        | Store API data in memory/localStorage          |
| AbortController     | Cancel old requests       | Cancel previous search request on typing       |
| Refresh Token       | Auto re-login             | Generate new access token automatically        |
| Environment Config  | Multiple servers          | DEV/STAGING/PROD base URLs                     |

- Real Production API URLs

| Module         | Example Endpoint                |
| -------------- | ------------------------------- |
| Login          | `/api/auth/login`               |
| Refresh Token  | `/api/auth/refresh-token`       |
| Products       | `/api/products`                 |
| Product Search | `/api/products/search?q=iphone` |
| Users          | `/api/users?page=1&limit=10`    |
| Orders         | `/api/orders`                   |
| Payment Verify | `/api/payments/verify`          |

- Enterprise-Level Best Practices

| Best Practice        | Why                           |
| -------------------- | ----------------------------- |
| Central API Client   | Reusable fetch logic          |
| Separate API Files   | Better scalability            |
| Retry Only Safe APIs | Avoid duplicate payment/order |
| Abort Old Searches   | Better UX/performance         |
| Debounce Search      | Reduce server load            |
| Cache Static Data    | Faster app                    |
| Use Refresh Token    | Seamless login                |
| Timeout APIs         | Prevent frozen UI             |
| Use Env Config       | Easy deployments              |

- APIs Usually NOT Retried

| API            | Why                      |
| -------------- | ------------------------ |
| Payment API    | Avoid double payment     |
| Order Creation | Avoid duplicate orders   |
| Delete APIs    | Prevent duplicate delete |

- APIs Commonly Cached

| API               | Reason         |
| ----------------- | -------------- |
| Profile           | Rarely changes |
| Settings          | Static         |
| Categories        | Mostly static  |
| Dashboard Summary | Performance    |

- APIs Commonly Debounced

| API       | Reason                |
| --------- | --------------------- |
| Search    | High frequency typing |
| Filter    | Rapid UI changes      |
| Auto Save | Reduce writes         |

### Retry Logic

```js
// Frontend retries automatically before showing failure. Payment verification API
async function verifyPayment(paymentId, retries = 3) {
  try {
    const response = await fetch(`/api/payments/${paymentId}/verify`);
    if (!response.ok) {
      throw new Error("Verification Failed");
    }
    return await response.json();
  } catch (error) {
    if (retries === 0) {
      throw error;
    }
    console.log(`Retrying... (${retries})`);
    return verifyPayment(paymentId, retries - 1);
  }
}
```

### Request Timeout

```js
// Large products API taking too long, Prevent UI hanging forever.
async function getProducts() {
  const controller = new AbortController();
  const timeout = setTimeout(() => {
    controller.abort();
  }, 5000);

  try {
    const response = await fetch("/api/products", {
      signal: controller.signal,
    });

    return await response.json();
  } catch (error) {
    if (error.name === "AbortError") {
      console.log("Request Timeout");
    }
    throw error;
  } finally {
    clearTimeout(timeout);
  }
}
```

### Debounce Search API

```js
// E-commerce live product search
let debounceTimer;
searchInput.addEventListener("input", (e) => {
  clearTimeout(debounceTimer);

  debounceTimer = setTimeout(() => {
    searchProducts(e.target.value);
  }, 400);
});

async function searchProducts(keyword) {
  const response = await fetch(`/api/products/search?q=${keyword}`);
  const data = await response.json();

  renderProducts(data);
}
```

### Pagination

```js
// Admin dashboard users table
// Instead of 50,000 users at once, load only 10 users per page
async function getUsers(page = 1) {
  const response = await fetch(`/api/users?page=${page}&limit=10`);

  return response.json();
}
```

```json
// API Response
{
  "data": [],
  "page": 1,
  "totalPages": 50,
  "totalUsers": 500
}
```

### Caching

```js
// Dashboard profile/settings data, Avoid fetching same data repeatedly.

async function getProfile() {
  const cachedData = localStorage.getItem("profile");
  if (cachedData) {
    return JSON.parse(cachedData);
  }
  const response = await fetch("/api/profile");
  const data = await response.json();
  localStorage.setItem("profile", JSON.stringify(data));

  return data;
}
```

### Abort Controller

```js
// Search suggestions while typing
// Cancel previous API request to prevent: Old results overriding new results

let controller;
async function searchProducts(keyword) {
  if (controller) {
    controller.abort();
  }
  controller = new AbortController();

  try {
    const response = await fetch(`/api/products/search?q=${keyword}`, {
      signal: controller.signal,
    });
    const data = await response.json();
    renderProducts(data);
  } catch (error) {
    if (error.name !== "AbortError") {
      console.error(error);
    }
  }
}
```

### Refresh Token

```js
// JWT token expired after 15 minutes
// Instead of logging out immediately: Refresh token generates new access token

async function refreshAccessToken() {
  const refreshToken = localStorage.getItem("refreshToken");
  const response = await fetch("/api/auth/refresh-token", {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
    },
    body: JSON.stringify({
      refreshToken,
    }),
  });
  const data = await response.json();
  localStorage.setItem("accessToken", data.accessToken);

  return data.accessToken;
}
```

### Auto Retry Original API

```js
if (response.status === 401) {
  const newToken = await refreshAccessToken();

  return apiClient(endpoint, {
    ...options,
    headers: {
      Authorization: `Bearer ${newToken}`,
    },
  });
}
```

### Environment Config

- Different servers for:

| Environment | Server                  |
| ----------- | ----------------------- |
| Local Dev   | localhost               |
| Testing     | staging-api.company.com |
| Production  | api.company.com         |

```js
// config/env.js
const ENV = "development";
const CONFIG = {
  development: {
    API_URL: "http://localhost:3000",
  },

  staging: {
    API_URL: "https://staging-api.company.com",
  },

  production: {
    API_URL: "https://api.company.com",
  },
};

export default CONFIG[ENV];
```

```js
// Usage
import ENV from "./config/env.js";

fetch(`${ENV.API_URL}/products`);
```

---

## 📌 API HTML vs React

- In Vanilla JS: You manually update UI
- In React: State updates UI automatically

| Feature             | Normal HTML App     | React App                     |
| ------------------- | ------------------- | ----------------------------- |
| UI Update           | Manual DOM update   | State-based re-render         |
| Event Handling      | `addEventListener`  | JSX events (`onClick`)        |
| State Management    | Variables/manual    | `useState`                    |
| Lifecycle           | Manual handling     | `useEffect`                   |
| API Calls           | Anywhere            | Usually inside hooks/services |
| Cleanup             | Manual              | `useEffect` cleanup           |
| Loading/Error State | Manual DOM changes  | React state                   |
| Caching             | Custom/localStorage | React Query/SWR commonly      |
| Reusability         | Utility functions   | Hooks + components            |
| Global State        | Difficult           | Context/Zustand/Redux         |
| Search Debounce     | Manual              | `useEffect` + hooks           |
| Request Cancel      | Manual              | Cleanup in `useEffect`        |

```js
// Normal HTML
document.querySelector("#title").innerText = data.title;
```

```jsx
// React
// React automatically updates UI.
setProducts(data);
```

### React API Folder Structure

```txt
src/
│
├── api/
│   ├── apiClient.ts
│   ├── authApi.ts
│   └── productApi.ts
│
├── hooks/
│   ├── useDebounce.ts
│   ├── useProducts.ts
│   └── useAuth.ts
│
├── services/
│   └── storageService.ts
│
├── pages/
├── components/
├── context/
├── store/
├── utils/
└── config/
```

### Common React API Libraries

| Library         | Usage            |
| --------------- | ---------------- |
| Axios           | HTTP client      |
| React Query     | API caching      |
| SWR             | Fetch/cache      |
| Zustand         | Global state     |
| Redux Toolkit   | Enterprise state |
| React Hook Form | Form handling    |
| Zod/Yup         | Validation       |

```txt
UI Components
      ↓
Custom Hooks
      ↓
API Layer
      ↓
HTTP Client
      ↓
Backend
```

| App Size   | Recommended                         |
| ---------- | ----------------------------------- |
| Small      | fetch + custom hooks                |
| Medium     | Axios + React Query                 |
| Enterprise | Axios + React Query + Zustand/Redux |

### Environment Config in React

- React Uses `.env`

```env
VITE_API_URL=https://api.company.com
```

```tsx
// Usage
fetch(`${import.meta.env.VITE_API_URL}/products`);
```

### Important Rule

1. Vite Requires `VITE_`

✅ Correct

```env
VITE_API_URL=https://api.com
```

❌ Wrong

```env
API_URL=https://api.com
```

2. NEVER hardcode URLs

❌ Bad

```ts
fetch("https://api.mycompany.com/products");
```

✅ Good

```ts
fetch(`${ENV.API_URL}/products`);
```

### Real-World Environment Variables

| Variable              | Purpose                   | Real Usage Example                        |
| --------------------- | ------------------------- | ----------------------------------------- |
| `VITE_API_URL`        | Backend URL               | `https://api.company.com`                 |
| `VITE_APP_NAME`       | Browser Tab Title         | `Admin Dashboard`                         |
| `VITE_ENABLE_LOGS`    | Console Enable debug logs | Enable logs in dev, disable in production |
| `VITE_STRIPE_KEY`     | Payment public key        | Stripe checkout/payment integration       |
| `VITE_SOCKET_URL`     | WebSocket server          | Real-time chat/notifications              |
| `VITE_GOOGLE_MAP_KEY` | Maps integration          | Google Maps/address autocomplete          |

```ts
// VITE_API_URL
fetch(`${import.meta.env.VITE_API_URL}/products`);

// VITE_APP_NAME
document.title = import.meta.env.VITE_APP_NAME;

// VITE_ENABLE_LOGS
if (import.meta.env.VITE_ENABLE_LOGS === "true") {
  console.log("API Response:", data);
}

// VITE_STRIPE_KEY
import { loadStripe } from "@stripe/stripe-js";
const stripe = await loadStripe(import.meta.env.VITE_STRIPE_KEY);

// VITE_SOCKET_URL
const socket = new WebSocket(import.meta.env.VITE_SOCKET_URL);

// VITE_GOOGLE_MAP_KEY
const mapKey = import.meta.env.VITE_GOOGLE_MAP_KEY;
```

- Important Security Note
  Public API URL
  Stripe public key
  Google Maps public key

```env
DATABASE_PASSWORD=123456
JWT_SECRET=secret
STRIPE_SECRET_KEY=sk_live_xxx
```
