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

- Context API > Small to medium apps, Theme, Auth, User Settings
- Redux / RTK > Medium to large apps, Complex global state

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

### ❓

- Data

### ❓

- Data

### ❓

- Data

```js
// Code
```

```js
// Code
```

```js
// Code
```

```js
// Code
```

```js
// Code
```

---
