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
