# 👉 React Tools

## 📌 States

### Zustand - `useState` - Redux

| Feature          | `useState`           | Zustand                  | Redux Toolkit            |
| ---------------- | -------------------- | ------------------------ | ------------------------ |
| Type             | React Hook           | External Library         | External Library         |
| State Scope      | Local component      | Global state             | Global state             |
| Setup Complexity | Very simple          | Simple                   | Medium                   |
| Boilerplate      | Minimal              | Minimal                  | More structure           |
| Performance      | Good for local state | Optimized global updates | Optimized scalable state |
| Learning Curve   | Easy                 | Easy                     | Medium                   |
| DevTools Support | Basic                | Yes                      | Advanced                 |
| Async Handling   | Manual               | Manual                   | Built-in patterns        |
| Best For         | Small/local state    | Medium apps              | Large enterprise apps    |

| Tool          | Common Usage                 |
| ------------- | ---------------------------- |
| `useState`    | Form inputs, toggles, modals |
| Zustand       | Cart, theme, auth            |
| Redux Toolkit | Enterprise dashboards        |

```jsx
// useState
const [count, setCount] = useState(0);
```

```jsx
// Zustand
const useStore = create((set) => ({
  count: 0,
}));
```

```jsx
// Redux Toolkit
const counterSlice = createSlice({
  name: "counter",
});
```

```txt
useState
→ Local component storage

Zustand
→ Simple global shared storage

Redux Toolkit
→ Structured enterprise-level global state system
```

---

## 📌 Redux Toolkit

Redux Toolkit is a global state management library used for sharing and managing application state across React components.

| Concept         | Purpose                 | Example                    | Real-World Usage    |
| --------------- | ----------------------- | -------------------------- | ------------------- |
| Store           | Global state container  | `configureStore()`         | App-wide data       |
| Slice           | State section + logic   | `createSlice()`            | Auth/cart           |
| State           | Shared application data | `count: 0`                 | Dashboard data      |
| Reducer         | Updates state           | `increment()`              | Add/remove item     |
| Action          | Trigger state update    | `dispatch(increment())`    | UI interactions     |
| `useSelector()` | Read store data         | `state.counter.count`      | Show shared data    |
| `useDispatch()` | Send action             | `dispatch(action)`         | Update global state |
| Provider        | Share store globally    | `<Provider store={store}>` | Entire React app    |

| Redux Part      | Simple Meaning                   | Example                   |
| --------------- | -------------------------------- | ------------------------- |
| Store           | Global storage box               | Entire app data           |
| Slice           | One section of global state      | Cart slice, auth slice    |
| State           | Stored data                      | `count: 0`                |
| Reducer         | Function updating state          | Increase/decrease counter |
| Action          | Instruction to update state      | `increment()`             |
| `useSelector()` | Read state from store            | Get cart count            |
| `useDispatch()` | Send update request              | Add/remove product        |
| Provider        | Makes store available everywhere | Wrap React app            |

```bash
npm install @reduxjs/toolkit react-redux
```

```jsx
// store.js
import { configureStore, createSlice } from "@reduxjs/toolkit";

const counterSlice = createSlice({
  name: "counter",
  initialState: {
    count: 0,
  },
  reducers: {
    increment: (state) => {
      state.count += 1;
    },
    decrement: (state) => {
      state.count -= 1;
    },
  },
});

export const { increment, decrement } = counterSlice.actions;
export const store = configureStore({
  reducer: {
    counter: counterSlice.reducer,
  },
});
```

```jsx
// main.jsx
import ReactDOM from "react-dom/client";
import { Provider } from "react-redux";

import App from "./App";
import { store } from "./store";

ReactDOM.createRoot(document.getElementById("root")).render(
  <Provider store={store}>
    <App />
  </Provider>,
);
```

```jsx
// App.jsx
import { useDispatch, useSelector } from "react-redux";
import { increment, decrement } from "./store";

export default function App() {
  const count = useSelector((state) => state.counter.count);
  const dispatch = useDispatch();

  return (
    <div>
      <h1>{count}</h1>
      <button onClick={() => dispatch(increment())}>+</button>
      <button onClick={() => dispatch(decrement())}>-</button>
    </div>
  );
}
```

### Redux Flow

```txt
User Action
     ↓
Dispatch Action
     ↓
Reducer Updates State
     ↓
Store Updates
     ↓
UI Re-renders
```

| Best Practice                | Notes                        |
| ---------------------------- | ---------------------------- |
| Use slices by feature        | Better scalability           |
| Keep state minimal           | Avoid unnecessary complexity |
| Separate API logic           | Cleaner architecture         |
| Use Redux Toolkit            | Less boilerplate             |
| Avoid storing local UI state | Use `useState` when possible |

| Real-World Usage | Example                |
| ---------------- | ---------------------- |
| Shopping Cart    | Shared cart state      |
| Authentication   | User login state       |
| SaaS Dashboard   | Global analytics state |
| Notifications    | Shared alert system    |

---
