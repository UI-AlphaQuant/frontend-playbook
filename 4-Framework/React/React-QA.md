# React – Interview Q&A

## � BASIC

**Q:** What is React?
**A:** JavaScript library for building reusable, dynamic user interfaces. Uses component-based architecture and Virtual DOM for efficient rendering.

**Q:** What is JSX?
**A:** JavaScript XML. Syntax extension allowing you to write HTML-like code in JavaScript. Gets compiled to `React.createElement()` calls. Makes UI code more readable.

**Q:** Difference between JSX and TSX?
**A:** JSX is JavaScript with XML syntax. TSX is the same but with TypeScript. TSX provides type safety for props, state, and events.

**Q:** What are components in React?
**A:** Reusable pieces of UI. Functional components are JavaScript functions returning JSX. Class components are ES6 classes with render method.

**Q:** Functional vs Class components?
**A:** Functional components are simpler, use hooks for state/effects. Class components use `this` and lifecycle methods. Modern React prefers functional components.

**Q:** What are props?
**A:** Short for properties. Data passed from parent to child component. Props are immutable (read-only). Enables component reusability with different data.

**Q:** What is state?
**A:** Data managed within component using `useState` hook. Mutable and local to component. When state changes, component re-renders. Don't pass state as props directly.

**Q:** Props vs State?
**A:** Props are external data (parent to child), immutable. State is internal data, mutable. Props are passed in, state is defined inside component.

**Q:** What is Virtual DOM?
**A:** In-memory representation of real DOM. React updates Virtual DOM first, then compares with actual DOM. Only updates changed elements (diffing). Improves performance.

**Q:** Virtual DOM vs Real DOM?
**A:** Virtual DOM is JavaScript object (faster to manipulate). Real DOM is browser's actual DOM (slow to update). React batches Virtual DOM updates, applies to real DOM in one operation.

**Q:** What is conditional rendering?
**A:** Rendering different UI based on conditions. Use ternary operator, logical AND, or if-else. Example: `{condition ? <Component1 /> : <Component2 />}`.

**Q:** What are keys in React lists?
**A:** Unique identifier for items in list. Helps React identify which items have changed. Without keys, React re-renders all items when list changes.

**Q:** Why should keys be unique?
**A:** React uses keys to match elements between renders. Non-unique keys cause component state to get mixed up. Performance degrades with index-based keys.

**Q:** What is event handling in React?
**A:** Attaching functions to DOM events like click, change, submit. Use camelCase syntax: `onClick`, `onChange`. Pass function reference, not function call. Event object automatically passed.

**Q:** Controlled vs uncontrolled components?
**A:** Controlled: form input value managed by React state. Uncontrolled: form input manages its own state via refs. Prefer controlled for form handling.

**Q:** What are React hooks?
**A:** Functions allowing functional components to use state and lifecycle features. Built-in hooks: `useState`, `useEffect`, `useContext`, `useReducer`, `useRef`, `useCallback`, `useMemo`.

**Q:** What is `useState` hook?
**A:** Hook for adding state to functional components. Returns `[state, setState]` pair. Calling setState triggers component re-render.

**Q:** What is `useEffect` hook?
**A:** Hook for side effects (API calls, subscriptions, DOM updates). Runs after component renders. Takes callback and dependency array. Replaces lifecycle methods.

**Q:** What is dependency array in `useEffect`?
**A:** Array of dependencies. Effect runs when dependencies change. Empty array `[]` = runs once on mount. No array = runs on every render.

**Q:** What causes infinite loops in `useEffect`?
**A:** Missing or incorrect dependency array. Effect updates state that's in dependency array, causing effect to run again. Fix: add state to dependencies or move outside effect.

**Q:** What is cleanup function in `useEffect`?
**A:** Function returned from effect that runs before component unmounts or before effect runs again. Used to cleanup subscriptions, timers, event listeners. Prevents memory leaks.

**Q:** What is `useRef` hook?
**A:** Hook for accessing DOM elements or storing mutable values. Doesn't cause re-render when updated. Returns same object reference on every render.

**Q:** `useRef` vs `useState`?
**A:** `useRef` doesn't cause re-render, persists across renders. `useState` causes re-render when updated. Use `useRef` for DOM access, `useState` for UI updates.

---

## � INTERMEDIATE

**Q:** What is Context API?
**A:** Mechanism for sharing data between components without prop drilling. Create context with `createContext()`, provide with `<Provider>`, consume with `useContext()`.

**Q:** What are custom hooks?
**A:** Reusable function that uses other hooks internally. Starts with "use" prefix. Encapsulates component logic. Share stateful logic between components.

**Q:** What is React Router?
**A:** Library for client-side routing in React SPAs. Enables navigation without full page reload. Components: `BrowserRouter`, `Routes`, `Route`, `Link`, `useNavigate`.

**Q:** What is CSR (Client-Side Rendering)?
**A:** Rendering happens in browser. JavaScript loads, React renders components. Fast interactions after initial load. Slower initial load, worse SEO.

**Q:** What is SSR (Server-Side Rendering)?
**A:** Rendering happens on server. HTML sent to browser ready to display. Fast initial load, better SEO. Requires server resources, slower time-to-interactive.

**Q:** What is SSG (Static Site Generation)?
**A:** HTML generated at build time. Pre-built pages served to users. Fastest performance, excellent SEO. Used for blogs, docs, landing pages.

**Q:** CSR vs SSR vs SSG?
**A:** CSR: fast after load, poor SEO. SSR: fast initial, good SEO, server load. SSG: fastest, best SEO, no dynamic content. Choose based on content type.

**Q:** How do you handle API calls in React?
**A:** Use `useEffect` for fetching. Add error and loading states. Implement proper error handling. Use try-catch with async/await. Clean up subscriptions in cleanup function.

**Q:** Fetch vs Axios?
**A:** `fetch()` is built-in browser API. Axios is library. Axios has better error handling, timeout, interceptors. Fetch is lighter, requires more manual setup.

**Q:** How do you handle forms in React?
**A:** Use controlled components with `useState`. Track each input in state. Validate on change/submit. Prevent default form submission. Use libraries like Formik for complex forms.

**Q:** What is form validation?
**A:** Checking user input correctness before submission. Validate on input change (real-time feedback) and on submit. Show error messages. Server-side validation also required.

**Q:** Local state vs global state?
**A:** Local state: component's own state. Global state: shared across components (Context, Redux). Use local for component-specific data. Global for app-wide data (user, theme, auth).

**Q:** What is props drilling?
**A:** Passing props through many intermediate components that don't need them. Creates maintenance burden. Solution: Context API, state management libraries (Redux, Zustand).

**Q:** What is immutable update?
**A:** Never directly modify state. Create new objects/arrays instead. Example: `setState([...arr, newItem])` not `arr.push(newItem)`. Ensures proper re-rendering, prevents bugs.

**Q:** What are portals?
**A:** React feature to render components outside parent DOM hierarchy. Use `ReactDOM.createPortal()`. Common for modals, tooltips, dropdowns to avoid CSS stacking context issues.

**Q:** What are Error Boundaries?
**A:** Class components catching JavaScript errors anywhere in child tree. Prevent entire app from crashing. Show fallback UI. Log errors to service.

**Q:** What is accessibility in React?
**A:** Making React apps usable for everyone including disabled users. Use semantic HTML, ARIA attributes, keyboard navigation, proper labels, color contrast, screen reader testing.

**Q:** What are ARIA attributes?
**A:** Accessibility Rich Internet Applications. HTML attributes providing additional semantics to assistive technologies. Examples: `aria-label`, `aria-hidden`, `aria-live`, `role`.

**Q:** How do you deploy React apps?
**A:** Build production version (`npm run build`). Deploy to hosting (Vercel, Netlify, AWS). Configure environment variables. Set up CI/CD pipeline. Monitor performance.

**Q:** What is CI/CD?
**A:** Continuous Integration: automated testing on commits. Continuous Deployment: automated deployment to production. Catches bugs early, faster release cycle, improved code quality.

**Q:** What is production build?
**A:** Optimized version of app for deployment. Minified code, optimized assets, removed debugging info. Much smaller bundle size. Use `npm run build` to create.

**Q:** What are environment variables?
**A:** Configuration values like API URLs, API keys. Use `.env` files. Prefix with `REACT_APP_` to expose to frontend. Keep secrets server-side.

**Q:** How do you debug React apps?
**A:** Use React DevTools browser extension. Console logs and breakpoints. Browser DevTools. Network tab for API calls. Check component tree, props, hooks state.

**Q:** Real-life (Indian e-commerce context): Handle payment form securely?
**A:** Never store card details in React. Use Razorpay/PayU integration via API gateway. Store only payment reference. Validate on backend. Implement CSRF protection. Use HTTPS.

**Q:** Real-life: Optimize form with 100 input fields?
**A:** Use `useReducer` instead of `useState` for each field. Implement field-level validation. Lazy-load sections. Use form library like Formik or React Hook Form. Debounce validation.

**Q:** Calculation: If component renders 100 times per second unnecessarily, what's performance impact?
**A:** At 60fps browser expects 16ms per frame. Unnecessary renders = expensive calculations waste CPU. For 1000 components: 100 renders/sec × 1000 = 100,000 renders/sec = major lag. Fix with `useMemo`, `useCallback`, `React.memo`.

---

## � ADVANCED

**Q:** What is reconciliation?
**A:** Process of updating Virtual DOM to match component state. React compares new Virtual DOM with previous one. Identifies what changed. Updates real DOM selectively.

**Q:** What is diffing algorithm?
**A:** Algorithm React uses comparing two Virtual DOM trees. Assumes different tree types produce different trees. Keys help identify same elements. Two-pass algorithm: depth-first traversal.

**Q:** How does React rendering work internally?
**A:** Component function called, returns JSX. JSX compiled to `React.createElement()` calls. Creates Virtual DOM tree. Compares with previous tree. Updates real DOM. Browser repaints.

**Q:** What is concurrent rendering?
**A:** New React feature allowing rendering to be interrupted. Work split into units. Can pause, abandon, or reuse work. Improves responsiveness for slow devices. Used with Suspense.

**Q:** What is Suspense?
**A:** React component for handling async operations in declarative way. Shows fallback while loading. Used with lazy-loaded components and data fetching (experimental).

**Q:** What is lazy loading in React?
**A:** `React.lazy()` and dynamic imports loading components on demand. Reduces initial bundle size. Components downloaded when route accessed. Combined with Suspense for fallback.

**Q:** What is code splitting?
**A:** Dividing app into smaller chunks loaded on demand. Improves initial load time. Webpack handles this automatically with dynamic imports. Combine with lazy loading.

**Q:** What is hydration?
**A:** Process of attaching React to server-rendered HTML. React renders components in browser, compares with server HTML, attaches event listeners. Makes static HTML interactive.

**Q:** What is `useMemo` hook?
**A:** Memoizes computed value. Reruns only when dependencies change. Prevents expensive recalculations on every render. Use for heavy computations, derived data.

**Q:** What is `useCallback` hook?
**A:** Memoizes function reference. Returns same function unless dependencies change. Passes to child components preventing unnecessary re-renders. Essential with `React.memo()`.

**Q:** What is `React.memo`?
**A:** Higher-order component preventing re-render if props haven't changed. Shallow comparison by default. Custom comparison available. Use for expensive components.

**Q:** What is `useReducer` hook?
**A:** Advanced state management. Similar to Redux. Takes reducer function and initial state. Returns `[state, dispatch]`. Better for complex state logic with multiple sub-values.

**Q:** Context API vs Redux?
**A:** Context is built-in, simpler for small apps. Redux is library, better for large apps with complex state. Redux has middleware, time-travel debugging. Context causes all consumers to re-render on update.

**Q:** What is React Fiber?
**A:** New reconciliation engine in React 16+. Enables incremental rendering. Can pause, resume, abort rendering. Improves responsiveness. Works in browser requestIdleCallback.

**Q:** What is hydration mismatch?
**A:** Server-rendered HTML differs from client-rendered HTML. Causes console warnings. Usually from random values, browser-specific APIs, timezone differences. Fix: match server/client rendering.

**Q:** What are deprecated React patterns?
**A:** String refs, `getChildContext`, legacy Context API, some lifecycle methods. Use modern hooks, `useRef`, new Context API instead. Avoid in new code.

**Q:** What are compound components?
**A:** Pattern where multiple components work together. Example: `<Select>` `<Option>`. Share implicit state via Context. Flexible, composable API. Common in UI libraries.

**Q:** What are HOCs (Higher-Order Components)?
**A:** Function taking component and returning enhanced component. Used for props manipulation, state abstraction, authentication. Being replaced by hooks in modern React.

**Q:** What are render props?
**A:** Pattern using `children` or prop functions. Function receives data and returns React elements. Enables code sharing. Being replaced by custom hooks in modern React.

**Q:** How do you structure large React apps?
**A:** Feature-based folder structure. Each feature has components, hooks, services, types. Shared components in separate folder. Clear separation of concerns. Scalable architecture.

**Q:** Real-life (Indian SaaS): Implement authentication flow?
**A:** Login form with email/password. Call API with credentials. Store JWT token in httpOnly cookie. Redirect to dashboard. Implement auto-logout on token expiry. Refresh token mechanism.

**Q:** Real-life: Optimize large list rendering (10,000 items)?
**A:** Virtual scrolling (react-window) - only render visible items. Pagination or infinite scroll. Memoize list items with `React.memo`. Debounce filter/search. Server-side sorting/filtering.

**Q:** Real-life: Debug memory leak from unremoved event listeners?
**A:** Check Chrome DevTools memory profiler. Look for detached DOM nodes. Verify `useEffect` cleanup functions remove listeners. Check for circular references. Use `useEffect` return for cleanup.

**Q:** Real-life (Indian payment app): Handle 100+ concurrent API requests?
**A:** Use request queue/throttling. Batch requests if possible. Implement retry logic with exponential backoff. Timeout after 30s. Show loading states. Handle failures gracefully with offline mode.

**Q:** Calculation: If component with 50 props re-renders unnecessarily 10 times per minute, what's the cost?
**A:** 50 props × 10 renders/min = 500 prop comparisons/min = 8.3 per second. At 60 ops/ms, this is nothing. But if each prop is complex object requiring deep comparison: 50 objects × deep comparison cost × 10/min = potential 100-200ms wasted per minute. Fix: `React.memo()` with custom comparison, `useMemo()`.

**Q:** Calculation: App initial bundle is 500KB. After code splitting, 200KB initial + 100KB each for 3 features. Total after downloading all features = 500KB. But initial load with splitting = 200KB (60% reduction).

---

## 📋 Quick Reference

| Hook          | Purpose                       |
| ------------- | ----------------------------- |
| `useState`    | Manage component state        |
| `useEffect`   | Side effects, API calls       |
| `useContext`  | Access context values         |
| `useReducer`  | Complex state logic           |
| `useRef`      | DOM access, persistent values |
| `useCallback` | Memoize function references   |
| `useMemo`     | Memoize computed values       |

| Pattern             | Use Case                       |
| ------------------- | ------------------------------ |
| Compound Components | Flexible component APIs        |
| Custom Hooks        | Share logic between components |
| Context API         | Global state management        |
| Error Boundaries    | Error handling                 |
| Portals             | Render outside DOM hierarchy   |
| Lazy Loading        | Code splitting                 |

---

### ❓What is componentWillUnmount in React?

- componentWillUnmount() is a lifecycle method in Class Components that runs just before a component is removed from the DOM.
- It is commonly used for: Removing event listeners, Clearing timers, Cancelling API requests,
- In Functional Components, we use useEffect cleanup function.

### ❓What is the difference between Redux and Redux Toolkit?

- Redux → More code, manual setup.
- Redux Toolkit is the modern, recommended way to use Redux with less boilerplate and easier state management.
- Redux is a state management library that requires actions, reducers, and store setup manually. Redux Toolkit (RTK) is the official Redux solution that reduces boilerplate using createSlice and configureStore.

### ❓Redux vs Context API – When should each be used?

- Context API > Context API is built into React and is used to share simple global data.
  - Small to medium apps, Theme, Auth, User Settings
- Redux / RTK > Redux is a dedicated state management library for handling complex global state.
  - Medium to large apps, Complex global state

```jsx
// Context API > Context -> theme = "dark"
<ThemeProvider>
  <App />
</ThemeProvider>;

// Redux > Redux -> cart = [product]
dispatch(addToCart(product));
```

### ❓dependencies vs devDependencies

- dependencies are required to run the application, while devDependencies are only needed during development, testing, or building the application.
- dependencies: react, axios, redux
- devDependencies: eslint, vite, typescript

### ❓package.json vs package-lock.json

- package.json defines what dependencies a project needs, while package-lock.json locks the exact versions to ensure consistent installations across environments.

### ❓What if we do not use keys in React?

- Warning: Each child in a list should have a unique "key" prop.
- React uses keys to identify which list items changed, added, or removed.
- Without keys: Unnecessary re-renders, Wrong component updates, Performance issues

```js
{
  users.map((user) => <li key={user.id}>{user.name}</li>);
}
```

### ❓Default Export vs Named Export

- Default export allows one export per file and can be imported with any name. Named exports allow multiple exports and must be imported using their exported names.

1. Default Export: Only one per file

- Import name can be anything
- No {} needed

2. Named Export: Multiple per file

- Import name must match
- {} required

```jsx
// Default Export (User.js)
import User from "./User";
import MyUser from "./User"; // ✅ also works

// Named Export (utils.js)
export const add = () => {};
export const sub = () => {};

import { add, sub } from "./utils";
import { add as sum } from "./utils"; // rename
```

### ❓ Context API vs Redux

- Context API is used for lightweight global state sharing, while Redux is a powerful state management library for handling complex application state with better scalability and control.

```jsx
// Context API
const ThemeContext = createContext();
<ThemeContext.Provider value="dark">
  <App />
</ThemeContext.Provider>;

// Redux
const store = configureStore({
  reducer: counterReducer,
});
```

### ❓ How to avoid Prop Drilling?

- Prop drilling happens when you pass props through multiple nested components just to reach a deep child.
- Prop drilling can be avoided using Context API for simple cases and Redux or state management libraries for complex applications.
- Context API is used to avoid prop drilling by providing global access to shared data like user, theme, or settings, and it can hold multiple values in a single context object.
  - createContext()
  - Context.Provider
  - useContext()

```jsx
// Problem (Prop Drilling)
// Without Context, you keep passing props like this: App → Layout → Sidebar → Header → UserProfile
function App() {
  const user = "Ram";
  return <Parent user={user} />;
}
function Parent({ user }) {
  return <Child user={user} />;
}
function Child({ user }) {
  return <GrandChild user={user} />;
}
function GrandChild({ user }) {
  return <h1>{user}</h1>;
}

// Solution 1: Context API (Best simple fix)
const AppContext = createContext();

function App() {
  const data = {
    user: "Ram",
    theme: "dark",
    token: "abc123",
  };

  return (
    <AppContext.Provider value={data}>
      <Child />
    </AppContext.Provider>
  );
}

function UserProfile() {
  const { user, theme } = useContext(AppContext);

  return (
    <div>
      <h1>{user}</h1>
      <p>Theme: {theme}</p>
    </div>
  );
}
```

### ❓ useEffect Hook – Syntax & Parameters

- useEffect is a React hook used for side effects. It takes a function and an optional dependency array, controlling when the effect runs and allowing cleanup logic on unmount.
  - Syntax:
    - A callback function
    - An optional dependency array
- Side effects are anything that happens outside of rendering UI or affects something external to the component.
  - API calls, Timers, DOM manipulation, Local storage access,

```jsx
// Syntax
useEffect(callback, dependencies);
useEffect(() => {
  console.log("Component Mounted"); // side effect logic, runs when dependencies change
}, [dependency]);

// Cleanup Function
useEffect(() => {
  const timer = setInterval(() => {
    console.log("Running...");
  }, 1000);

  return () => {
    clearInterval(timer);
  };
}, []);
```

### ❓ How Dependency Array Works in useEffect?

- Dependency array in useEffect controls when the effect runs:
  - no array means every render
  - empty array means only once
  - values inside array trigger the effect when they change.

```jsx
// First render, Runs Whenever count changes
const [count, setCount] = useState(0);

useEffect(() => {
  console.log("Count updated:", count);
}, [count]);

return (
  <div>
    <h1>Count: {count}</h1>
    <button onClick={() => setCount(count + 1)}>Increase</button>
    <button onClick={() => setCount(count - 1)}>Decrease</button>
  </div>
);
```

### ❓ How Routing works in React?

- React routing works using React Router, which maps URLs to components and updates the UI without reloading the page using client-side routing.
  - Normal Routing: Fixed routes (static paths)
  - Dynamic Routing: Routes with parameters

```jsx
// Normal Routing
<Route path="/about" element={<About />} />

// Dynamic Routing
<Route path="/user/:id" element={<User />} />

import { useParams } from "react-router-dom";
function User() {
  const { id } = useParams();
  return <h1>User ID: {id}</h1>;
}
```

### ❓ Lazy Loading in React?

- Lazy loading in React loads components only when they are needed, improving performance and reducing initial bundle size using React.lazy and Suspense.
  - Usage with Suspense
  - Loads immediately with main bundle
- Do we have to use Suspense with lazy?
  - Yes, Because React.lazy() loads component asynchronously, React needs Suspense fallback UI while loading. Without Suspense, React will throw an error.
- React.lazy is used for code-splitting and loads components on demand, while Suspense is required to show a fallback UI during the loading phase.

```jsx
// Without Lazy Loading
import About from "./About";

// With Lazy Loading
import { lazy, Suspense } from "react";
const About = lazy(() => import("./About"));

// Usage with Suspense
<Suspense fallback={<h1>Loading...</h1>}>
  <About />
</Suspense>;
```

```jsx
import { lazy, Suspense } from "react";
import { BrowserRouter, Routes, Route, Link } from "react-router-dom";

const Home = lazy(() => import("./Home"));
const Profile = lazy(() => import("./Profile"));

export default function App() {
  return (
    <BrowserRouter>
      <nav>
        <Link to="/">Home</Link> | <Link to="/profile">Profile</Link>
      </nav>

      <Suspense fallback={<h3>Loading page...</h3>}>
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/profile" element={<Profile />} />
        </Routes>
      </Suspense>
    </BrowserRouter>
  );
}
```

### ❓ difference between useMemo and useCallback?

- useMemo → memoizes a value
  - expensive calculations
  - cart total, filtering, sorting
- useCallback → memoizes a function
  - pass stable functions to child components
  - button handlers, API calls, child props

```jsx
// useMemo
const total = useMemo(() => price * qty, [price, qty]);

// useCallback
const handleClick = useCallback(() => {
  console.log("Clicked");
}, []);
```

### ❓ difference between Memoization and Memorization?

- Memoization stores computed results for reuse; memorization is remembering information as a human.
- Memoization ✅ JavaScript/Programming concept
- Memorization ✅ Human learning concept

### ❓ difference between State and Props in React?

- Props are read-only inputs from parent; State is mutable data owned by the component.
- State → managed inside component, can change
  - form inputs, loaders, modal visibility, counters
- Props → passed from parent, read-only
  - user data, settings, API data passed down

```jsx
// Props
<Profile name="Nick" />; // name comes from parent → Prop

// State
const [isOpen, setIsOpen] = useState(false); // Modal open/close status → State
```

### ❓ Controlled and Uncontrolled Components in React?

- Controlled components use React state; uncontrolled components use DOM refs.
- Controlled → React state controls the input
- Uncontrolled → DOM controls the input

```jsx
// Controlled
const [name, setName] = useState("");
<input value={name} onChange={(e) => setName(e.target.value)} />;

// Uncontrolled
const inputRef = useRef();
<input ref={inputRef} />;
console.log(inputRef.current.value);
```

### ❓ Higher-Order Component (HOC) in React?

- A HOC is a function that takes a component and returns a new enhanced component.
- A HOC is a function that adds reusable behavior to a component without modifying it.
  - withAuth(Profile), withLoader(Dashboard), withPermission(AdminPage)

```jsx
const withAuth = (Component) => {
  return () => (isLoggedIn ? <Component /> : <h1>Please Login</h1>);
};
const Dashboard = () => <h1>Dashboard</h1>;
const ProtectedDashboard = withAuth(Dashboard);
// if isLoggedIn = true > Dashboard
// if isLoggedIn = false > Please Login
```

- HOC wraps a component and adds reusable behavior like authentication or permissions.

### ❓ Custom Hook in React?

- A Custom Hook is a reusable function that encapsulates React stateful logic, allowing it to be shared across multiple components.
- useCounter(), useFetch(), useLocalStorage(), useDebounce()

```jsx
// useCounter.js
import { useState } from "react";

export function useCounter() {
  const [count, setCount] = useState(0);
  return { count, setCount };
}

// Home.jsx
import { useCounter } from "./useCounter";

function Home() {
  const { count } = useCounter();

  return <h1>{count}</h1>;
}
```

### ❓ Why is Fragment better than a div in React?

- Use Fragment when you need a wrapper but don't want an unnecessary DOM element.
- A div inside table would create invalid HTML.

```jsx
return (
  <>
    <h1>Title</h1>
    <p>Description</p>
  </>
);
```

### ❓ What is Jest?

- Jest is a JavaScript testing framework used to write and run automated tests for React and JavaScript applications.
- Jest is a testing framework used to automatically verify that JavaScript and React code works as expected.

```jsx
// Code
function sum(a, b) {
  return a + b;
}

test("adds two numbers", () => {
  expect(sum(2, 3)).toBe(5);
});
```

### ❓ Redux Toolkit?

- Redux Toolkit is the official Redux library that simplifies state management by reducing boilerplate and providing built-in best practices.

```jsx
import { createSlice } from "@reduxjs/toolkit";

const counterSlice = createSlice({
  name: "counter",
  initialState: { count: 0 },
  reducers: {
    increment: (state) => {
      state.count++;
    },
  },
});

export const { increment } = counterSlice.actions;
```

### ❓ Redux DevTools?

- Redux DevTools is a browser extension that lets you inspect, track, and debug Redux state changes in real time.

```jsx
dispatch(increment());
dispatch(increment());
dispatch(increment());

// Redux DevTools shows:
State Before: { count: 2 }
Action: increment
State After: { count: 3 }
```

### ❓ difference between Real DOM and Virtual DOM?

- Virtual DOM is a lightweight copy of the Real DOM that React uses to detect changes and update only the necessary DOM elements, improving performance.

- Real DOM is the actual browser DOM. (Browser DOM)
  - Real DOM approach → may re-check/update many nodes
  - Slower, Updates Direct, Vanilla JS
- Virtual DOM is a lightweight JavaScript copy of the DOM used by React to optimize updates. (JS Object)
  - Virtual DOM → finds only changed rows and updates them
  - Faster, Compare then update, React

```jsx
setCount(count + 1);

// Step 1: React updates Virtual DOM
// Step 2: Compares old vs new Virtual DOM
// Step 3: Updates only changed elements in Real DOM
```

### ❓ transfer data from a Child Component to a Parent Component?

- Parent-to-child communication uses props. Child-to-parent communication uses callback functions passed through props.
- Parent → Child: Pass data using props.
- Child → Parent: Pass a callback function as a prop and call it from the child.

```jsx
// Parent → Child
function Parent() {
  return <Child name="Nick" />;
}
function Child({ name }) {
  return <h1>{name}</h1>;
}
```

```jsx
// Child → Parent
function Parent() {
  const handleData = (name) => {
    console.log(name);
  };
  return <Child sendData={handleData} />;
}

function Child({ sendData }) {
  return <button onClick={() => sendData("Nick")}>Send</button>;
}
```

### ❓ Pure Component in React?

- A Pure Component performs a shallow comparison of props and state and re-renders only when their values change, helping improve performance by avoiding unnecessary renders.

```jsx
// Code
import React, { PureComponent } from "react";

class User extends PureComponent {
  render() {
    console.log("Rendered");

    return <h1>{this.props.name}</h1>;
  }
}
```

- When parent re-renders frequently, User won't re-render unless name changes.
  - User cards, Product cards, Large tables/lists

### ❓ useReducer in React?

- useReducer is a React hook used to manage complex state using a reducer function and actions, making state updates more predictable and structured than useState.

```jsx
function reducer(state, action) {
  switch (action.type) {
    case "inc":
      return { count: state.count + 1 };
    case "dec":
      return { count: state.count - 1 };
    default:
      return state;
  }
}

const [state, dispatch] = useReducer(reducer, { count: 0 });

dispatch({ type: "inc" });
```

### ❓ Component Lifecycle in React?

- Component lifecycle in React refers to the three phases—mounting, updating, and unmounting, where components are created, re-rendered on state/prop changes, and cleaned up when removed from the DOM.

```jsx
// S1
useEffect(() => {
  console.log("Component mounted");
  return () => {
    console.log("Component unmounted");
  };
}, []);

// S2
useEffect(() => {
  const timer = setInterval(() => {}, 1000);
  return () => clearInterval(timer);
}, []);
```

```text
// Real-life Usage
Fetch API on page load (mount)
Update UI when state changes (update)
Cleanup timers / listeners (unmount)
```

### ❓ Fragment in React?

- A Fragment in React is a wrapper that lets you group multiple elements without adding an extra DOM node.

### ❓

```jsx
// Code
```

### ❓

```jsx
// Code
```

### ❓

```jsx
// Code
```

### ❓

```jsx
// Code
```

### ❓

```jsx
// Code
```

### ❓

```jsx
// Code
```

### ❓

```jsx
// Code
```

### ❓

```jsx
// Code
```

### ❓

```jsx
// Code
```

### ❓

```jsx
// Code
```

### ❓

```jsx
// Code
```

### ❓

```jsx
// Code
```

---
