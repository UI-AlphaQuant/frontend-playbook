## 📌 Redux

| Item       | Description                      |
| ---------- | -------------------------------- |
| Purpose    | Global State Management          |
| Pattern    | Flux Architecture                |
| Data Flow  | Unidirectional                   |
| Store      | Single Source Of Truth           |
| Common Use | Auth, Cart, User Data, App State |

### Redux Toolkit (RTK)

- Redux Toolkit is the modern, recommended way to use Redux, providing simplified state management with less boilerplate through createSlice, configureStore, and createAsyncThunk.

| Item              | Description            |
| ----------------- | ---------------------- |
| Purpose           | Official Redux Wrapper |
| Created By        | Redux Team             |
| Boilerplate       | Much Less              |
| Recommended       | ✅ Yes                 |
| Industry Standard | ⭐⭐⭐⭐⭐             |

| Core Redux Concepts | Purpose                |
| ------------------- | ---------------------- |
| Store               | Global State Container |
| State               | Application Data       |
| Action              | What Happened          |
| Reducer             | Updates State          |
| Dispatch            | Sends Action           |
| Selector            | Reads State            |

- Data Flow

```txt
Component
    ↓
dispatch(action)
    ↓
Reducer
    ↓
Store Updated
    ↓
useSelector()
    ↓
Component Re-Renders
```

- Redux Toolkit

```js
// createSlice → createSlice(config)
const counterSlice = createSlice({
  name: "counter",
  initialState: {
    count: 0,
  },
  reducers: {
    increment: (state) => {
      state.count++;
    },
  },
});
```

```js
// Generated Action
counterSlice.actions.increment();
```

### Common APIs

```js
// configureStore → configureStore(config)
configureStore({});

// createSlice → createSlice(config)
createSlice({});

// createAsyncThunk → createAsyncThunk(type, callback)
createAsyncThunk();

// useSelector → useSelector(selector)
useSelector();

// useDispatch → useDispatch()
useDispatch();
```

- React Usage

```js
// useSelector → useSelector(selector)
const count = useSelector((state) => state.counter.count); // 0
// useDispatch → useDispatch()
const dispatch = useDispatch();

dispatch(increment());
```

- Async API Calls

```js
// createAsyncThunk → createAsyncThunk(type, callback)
export const fetchUsers = createAsyncThunk("users/fetch", async () => {
  const res = await fetch("/api/users");
  return res.json();
});
```

- Folder Structure

```txt
src/
├─ app/
│  └─ store.ts
├─ features/
│  ├─ auth/
│  ├─ users/
│  └─ cart/
└─ components/
```

- **Common Production Slices:** authSlice, userSlice, cartSlice, themeSlice, notificationSlice, productSlice

- Modern Redux Stack

```txt
Redux Toolkit
├─ configureStore
├─ createSlice
├─ createAsyncThunk
├─ useSelector
└─ useDispatch
```

### Redux Persist

```bash
npm install redux-persist
```

- Persist Redux state in storage so data survives page refreshes and browser reloads.
  - Useful for large applications.
    - Authentication
    - User Preferences
    - Theme Settings
    - Cart Data
    - App Settings

```txt
Redux Store
      ↓
Redux Persist
      ↓
localStorage / sessionStorage
      ↓
Page Refresh
      ↓
State Restored
```

- Before Persist: Login > Refresh Page > State Lost
- After Persist: Login > Refresh Page > State Restored

### persistConfig.ts

```ts
// Persist Entire Store
import storage from "redux-persist/lib/storage";
export const persistConfig = {
  key: "root",
  storage,
};

// Persist Specific Reducers
export const persistConfig = {
  key: "root",
  storage,
  whitelist: ["auth", "settings"],
};

// Exclude Reducers
const persistConfig = {
  key: "root",
  storage,
  blacklist: ["products"],
};

// Clear Persisted Data
persistor.purge(); // Logout / Reset App / Clear Cache

// Nested Persist
const authPersistConfig = {
  key: "auth",
  storage,
};
const authReducerPersisted = persistReducer(authPersistConfig, authReducer);

// Transform Data Before Saving (Encryption, Filtering, Data Formatting)
import { createTransform } from "redux-persist";
const transform = createTransform(
  (inboundState) => inboundState,
  (outboundState) => outboundState,
);
```

- Storage Options
  - localStorage (Default)
  - sessionStorage

```ts
import storage from "redux-persist/lib/storage";
import sessionStorage from "redux-persist/lib/storage/session";
```

### Configure Store

```ts
import { configureStore } from "@reduxjs/toolkit";
import { persistStore, persistReducer } from "redux-persist";
import authReducer from "./authSlice";
import { persistConfig } from "./persistConfig";

const persistedReducer = persistReducer(persistConfig, authReducer);
export const store = configureStore({
  reducer: {
    auth: persistedReducer,
  },
});
export const persistor = persistStore(store);
```

### main.tsx

```tsx
import ReactDOM from "react-dom/client";
import { Provider } from "react-redux";
import { PersistGate } from "redux-persist/integration/react";

import { store, persistor } from "./store";

ReactDOM.createRoot(document.getElementById("root")!).render(
  <Provider store={store}>
    <PersistGate loading={null} persistor={persistor}>
      <App />
    </PersistGate>
  </Provider>,
);
```

### Example Slice

```ts
import { createSlice } from "@reduxjs/toolkit";

const initialState = {
  user: null,
  token: null,
};
const authSlice = createSlice({
  name: "auth",
  initialState,
  reducers: {
    loginSuccess(state, action) {
      state.user = action.payload.user;
      state.token = action.payload.token;
    },

    logout(state) {
      state.user = null;
      state.token = null;
    },
  },
});

export const { loginSuccess, logout } = authSlice.actions;
export default authSlice.reducer;
```

---
