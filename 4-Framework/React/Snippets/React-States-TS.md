### AuthSlice

```tsx
// store/authSlice.ts
import { createSlice, PayloadAction } from "@reduxjs/toolkit";

type User = {
  id: number;
  name: string;
  email: string;
};

type AuthState = {
  user: User | null;
  token: string | null;
  isLoggedIn: boolean;
};

const initialState: AuthState = {
  user: null,
  token: null,
  isLoggedIn: false,
};

const authSlice = createSlice({
  name: "auth",

  initialState,

  reducers: {
    login: (
      state,
      action: PayloadAction<{
        user: User;
        token: string;
      }>,
    ) => {
      state.user = action.payload.user;
      state.token = action.payload.token;
      state.isLoggedIn = true;
    },

    logout: (state) => {
      state.user = null;
      state.token = null;
      state.isLoggedIn = false;
    },
  },
});

export const { login, logout } = authSlice.actions;
export default authSlice.reducer;
```

### Store

```tsx
// store/store.ts
import { configureStore } from "@reduxjs/toolkit";
import authReducer from "./authSlice";

export const store = configureStore({
  reducer: {
    auth: authReducer,
  },
});

export type RootState = ReturnType<typeof store.getState>;
export type AppDispatch = typeof store.dispatch;
```

### Main

```tsx
// main.tsx
import ReactDOM from "react-dom/client";
import { Provider } from "react-redux";
import App from "./App";
import { store } from "./store/store";

ReactDOM.createRoot(document.getElementById("root")!).render(
  <Provider store={store}>
    <App />
  </Provider>,
);
```

### App

```tsx
// App.tsx
import { useDispatch, useSelector } from "react-redux";
import type { RootState, AppDispatch } from "./store/store";
import { login, logout } from "./store/authSlice";

export default function App() {
  const dispatch = useDispatch<AppDispatch>();
  const { user, isLoggedIn } = useSelector((state: RootState) => state.auth);

  const handleLogin = () => {
    dispatch(
      login({
        user: {
          id: 1,
          name: "john",
          email: "john@example.com",
        },

        token: "jwt-token",
      }),
    );
  };

  return (
    <div>
      <h1>{isLoggedIn ? `Welcome ${user?.name}` : "Please Login"}</h1>

      {!isLoggedIn ? (
        <button onClick={handleLogin}>Login</button>
      ) : (
        <button onClick={() => dispatch(logout())}>Logout</button>
      )}
    </div>
  );
}
```

| Auth State   | Purpose              |
| ------------ | -------------------- |
| `user`       | Logged-in user data  |
| `token`      | Authentication token |
| `isLoggedIn` | Login status         |
| `login()`    | Store auth data      |
| `logout()`   | Clear auth state     |

```txt
Login System
Protected Routes
Role-based Access
User Profile
JWT Authentication
Persistent Sessions
```

---

## 📌 Redux

- Generic Reusable Slice Factory

| File            | Required  |
| --------------- | --------- |
| store.ts        | ✅        |
| hooks.ts        | ✅        |
| authSlice.ts    | ✅        |
| userSlice.ts    | ✅        |
| productSlice.ts | ✅        |
| selectors.ts    | ⚠️ Common |
| thunks.ts       | ⚠️ Common |
| middleware.ts   | Rare      |
| listeners.ts    | Rare      |

```txt
app/
├─ store.ts
├─ hooks.ts

features/
├─ auth/
│  ├─ authSlice.ts
│  ├─ authSelectors.ts
│  └─ authThunks.ts
│
├─ users/
│  ├─ userSlice.ts
│  ├─ userSelectors.ts
│  └─ userThunks.ts
│
├─ products/
│  ├─ productSlice.ts
│  ├─ productSelectors.ts
│  └─ productThunks.ts
│
└─ cart/
   └─ cartSlice.ts
```

- **Usage:**
  - store.ts → Creates Store
  - hooks.ts → Typed Redux Hooks
  - authSlice.ts → State + Reducers + Actions
  - authSelectors.ts → Read State
  - authThunks.ts → Async Logic + API Calls

### store.tsx

- configureStore() / reducers / RootState / AppDispatch

```ts
import { configureStore } from "@reduxjs/toolkit";

import authReducer from "../features/auth/authSlice";
import userReducer from "../features/users/userSlice";
import productReducer from "../features/products/productSlice";
import cartReducer from "../features/cart/cartSlice";

export const store = configureStore({
  reducer: {
    auth: authReducer,
    users: userReducer,
    products: productReducer,
    cart: cartReducer,
  },
});

export type RootState = ReturnType<typeof store.getState>;
export type AppDispatch = typeof store.dispatch;
```

### authSlice.tsx

```tsx
import { createSlice, PayloadAction } from "@reduxjs/toolkit";

type User = {
  id: number;
  name: string;
};

type AuthState = {
  user: User | null;
};

const initialState: AuthState = {
  user: null,
};

const authSlice = createSlice({
  name: "auth",
  initialState,
  reducers: {
    login: (state, action: PayloadAction<User>) => {
      state.user = action.payload;
    },
    logout: (state) => {
      state.user = null;
    },
  },
});

export const { login, logout } = authSlice.actions;
export default authSlice.reducer;
```

### hooks.tsx

- Typed Redux Hooks, Avoid Repeating Types, Provides Type Safety
- useAppDispatch() / useAppSelector()

```ts
import { TypedUseSelectorHook, useDispatch, useSelector } from "react-redux";
import type { RootState, AppDispatch } from "./store";
export const useAppDispatch = () => useDispatch<AppDispatch>();
export const useAppSelector: TypedUseSelectorHook<RootState> = useSelector;
```

### authSlice.ts

- initialState / createSlice() / reducers login() logout() / actions / reducer

```ts
import { createSlice, PayloadAction } from "@reduxjs/toolkit";

type User = {
  id: number;
  name: string;
  email: string;
};

type AuthState = {
  user: User | null;
  token: string | null;
  isAuthenticated: boolean;
};

const initialState: AuthState = {
  user: null,
  token: null,
  isAuthenticated: false,
};

const authSlice = createSlice({
  name: "auth",
  initialState,
  reducers: {
    login: (
      state,
      action: PayloadAction<{
        user: User;
        token: string;
      }>,
    ) => {
      state.user = action.payload.user;
      state.token = action.payload.token;
      state.isAuthenticated = true;
    },

    logout: (state) => {
      state.user = null;
      state.token = null;
      state.isAuthenticated = false;
    },
  },
});

export const { login, logout } = authSlice.actions;
export default authSlice.reducer;
```

### authSelectors.ts

- Reusable State Readers, Centralized Selectors, Avoid Repeating state.auth.xxx

```ts
import type { RootState } from "../../app/store";
export const selectUser = (state: RootState) => state.auth.user;
export const selectToken = (state: RootState) => state.auth.token;
export const selectIsAuthenticated = (state: RootState) =>
  state.auth.isAuthenticated;
```

### authThunks.ts

- Async Redux Actions, API Calls, Business Logic, Side Effects
- createAsyncThunk() / API Call / pending / fulfilled / rejected

```ts
import { createAsyncThunk } from "@reduxjs/toolkit";

type LoginPayload = {
  email: string;
  password: string;
};

export const loginUser = createAsyncThunk(
  "auth/loginUser",
  async (payload: LoginPayload) => {
    const response = await fetch("/api/login", {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify(payload),
    });

    return response.json();
  },
);
```

---
