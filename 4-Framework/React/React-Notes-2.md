# 👉 Advanced React

## 📌 React vs External API Tools

| Category            | Examples                                              |
| ------------------- | ----------------------------------------------------- |
| React Features      | `useState`, `useEffect`, `useRef`, Context API        |
| External Libraries  | Axios, React Router, Redux Toolkit, Zustand, Tailwind |
| Browser APIs        | `fetch`, `localStorage`, `setTimeout`, Canvas API     |
| JavaScript Features | Async/Await, Promises, Array Methods, ES Modules      |
| Build Tool Features | `.env`, Hot Reload, Path Aliases                      |

| Optional/Common Extras | Usage                  |
| ---------------------- | ---------------------- |
| React Query            | API caching/fetching   |
| Framer Motion          | Animations             |
| React Hook Form        | Form handling          |
| Firebase SDK           | Backend/auth/storage   |
| Socket.io Client       | Real-time apps         |
| i18next                | Multi-language support |

| Usually Misunderstood | Actual Type      |
| --------------------- | ---------------- |
| Axios                 | External library |
| fetch                 | Browser API      |
| Tailwind              | CSS framework    |
| Redux Toolkit         | External library |
| React Router          | External library |

---

## 📌 Advanced Hooks

Advanced hooks help optimize performance, manage complex state, and reuse logic in React applications.

| Hook          | Purpose                     | Example                       | Real-World Usage   |
| ------------- | --------------------------- | ----------------------------- | ------------------ |
| `useMemo`     | Memoize calculated values   | `useMemo(() => total, [])`    | Large filtering    |
| `useCallback` | Memoize functions           | `useCallback(() => {}, [])`   | Optimized handlers |
| `React.memo`  | Prevent unnecessary renders | `export default React.memo()` | Reusable UI        |
| `useReducer`  | Complex state logic         | `useReducer(reducer, state)`  | Multi-step forms   |
| Custom Hooks  | Reusable logic              | `useAuth()`                   | Shared app logic   |

| Hook          | Prevents                | Common Usage          |
| ------------- | ----------------------- | --------------------- |
| `useMemo`     | Expensive recalculation | Tables/search/filter  |
| `useCallback` | Function recreation     | Child prop callbacks  |
| `React.memo`  | Unnecessary re-render   | Large component trees |
| `useReducer`  | Messy multiple states   | Complex forms         |

```jsx
// useMemo
const filteredUsers = useMemo(() => {
  return users.filter((user) => user.name.includes(search));
}, [users, search]);
```

```jsx
// useCallback
const handleClick = useCallback(() => {
  console.log("Clicked");
}, []);
```

```jsx
// React.memo
export default React.memo(Button);
```

```jsx
// useReducer
const [state, dispatch] = useReducer(reducer, initialState);
```

| Best Practice               | Notes                        |
| --------------------------- | ---------------------------- |
| Use only when needed        | Avoid premature optimization |
| Memoize expensive logic     | Better performance           |
| Keep reducers clean         | Easier maintenance           |
| Use custom hooks            | Reusable business logic      |
| Avoid overusing memoization | Adds complexity              |

| Real-World Usage  | Hook          |
| ----------------- | ------------- |
| Product Filtering | `useMemo`     |
| Search Debounce   | `useCallback` |
| Complex Forms     | `useReducer`  |
| Shared Auth Logic | Custom Hook   |
| Large UI Trees    | `React.memo`  |

---

## 📌 Performance Optimization

Performance optimization improves React app speed, rendering efficiency, and user experience.

| Technique      | Purpose                     | Example               | Real-World Usage     |
| -------------- | --------------------------- | --------------------- | -------------------- |
| `React.memo`   | Prevent re-renders          | Memoized components   | Dashboard widgets    |
| `useMemo`      | Cache calculated values     | Filter/search results | Large tables         |
| `useCallback`  | Cache functions             | Stable event handlers | Form handlers        |
| Lazy Loading   | Load components when needed | `React.lazy()`        | Large apps           |
| Code Splitting | Split JS bundles            | Route-based loading   | Faster initial load  |
| Virtualization | Render visible items only   | Large lists/tables    | Chat/product lists   |
| Debouncing     | Delay repeated actions      | Search input          | API optimization     |
| Throttling     | Limit repeated actions      | Scroll/resize events  | Performance-heavy UI |
| Pagination     | Load partial data           | Table pagination      | Admin dashboards     |

| Optimization Target | Solution       |
| ------------------- | -------------- |
| Unnecessary renders | `React.memo`   |
| Heavy calculations  | `useMemo`      |
| Function recreation | `useCallback`  |
| Large bundle size   | Code splitting |
| Slow list rendering | Virtualization |
| Too many API calls  | Debouncing     |

```jsx
// Lazy Loading
const Dashboard = React.lazy(() => import("./Dashboard"));

// React.memo
export default React.memo(Card);

// useMemo
const filteredData = useMemo(() => {
  return items.filter((item) => item.name.includes(search));
}, [items, search]);
```

| Best Practice             | Notes                         |
| ------------------------- | ----------------------------- |
| Optimize only when needed | Avoid premature optimization  |
| Lazy load large pages     | Faster initial load           |
| Memoize expensive logic   | Better rendering performance  |
| Keep components small     | Easier rendering optimization |
| Avoid unnecessary state   | Reduce re-renders             |

| Real-World Usage | Optimization Method       |
| ---------------- | ------------------------- |
| E-commerce       | Lazy-loaded product pages |
| Dashboards       | Memoized widgets          |
| Search Systems   | Debounced API calls       |
| Chat Apps        | Virtualized message list  |

### Code Splitting

```jsx
import React, { Suspense } from "react";

// Load component only when needed
const Dashboard = React.lazy(() => import("./Dashboard"));

export default function App() {
  return (
    <Suspense fallback={<p>Loading...</p>}>
      <Dashboard />
    </Suspense>
  );
}
```

| Part           | Purpose                            |
| -------------- | ---------------------------------- |
| `React.lazy()` | Load component dynamically         |
| `import()`     | Split component into separate file |
| `Suspense`     | Show fallback while loading        |
| `fallback`     | Loading UI                         |

---

## 📌 Custom Hooks

Custom hooks are reusable functions that contain shared React hook logic.

| Concept          | Purpose                        | Example           | Real-World Usage |
| ---------------- | ------------------------------ | ----------------- | ---------------- |
| Reusable Logic   | Share logic between components | `useAuth()`       | Authentication   |
| Hook Composition | Combine multiple hooks         | `useFetch()`      | API handling     |
| State Sharing    | Reuse state logic              | `useToggle()`     | Modal toggles    |
| Side Effects     | Reuse effect logic             | `useWindowSize()` | Responsive UI    |

| Rule                  | Notes                   |
| --------------------- | ----------------------- |
| Must start with `use` | React hook convention   |
| Can use other hooks   | `useState`, `useEffect` |
| Reusable everywhere   | Multiple components     |
| Avoid UI rendering    | Keep logic-focused      |

```jsx
// Custom Hook
import { useState } from "react";

function useToggle(initialValue = false) {
  const [open, setOpen] = useState(initialValue);

  const toggle = () => {
    setOpen((prev) => !prev);
  };

  return {
    open,
    toggle,
  };
}
```

```jsx
// Component Usage
export default function App() {
  const { open, toggle } = useToggle();

  return <button onClick={toggle}>{open ? "Open" : "Closed"}</button>;
}
```

| Common Custom Hook | Usage                    |
| ------------------ | ------------------------ |
| `useFetch`         | API fetching             |
| `useAuth`          | Authentication logic     |
| `useToggle`        | Open/close state         |
| `useDebounce`      | Delay input changes      |
| `useLocalStorage`  | Browser storage handling |
| `useWindowSize`    | Responsive screen logic  |

| Best Practice                | Notes                 |
| ---------------------------- | --------------------- |
| Keep hooks reusable          | Avoid duplicate logic |
| Return clear values          | Easier usage          |
| Separate business logic      | Cleaner components    |
| Avoid unnecessary complexity | Simpler maintenance   |

| Custom Hook Type    | Purpose                | Example Usage            |
| ------------------- | ---------------------- | ------------------------ |
| `useAuth`           | Authentication logic   | Login/logout/user state  |
| `useFetch`          | API fetching           | Products/users API       |
| `useToggle`         | Toggle boolean state   | Modal/sidebar open-close |
| `useDebounce`       | Delay frequent actions | Search input             |
| `useLocalStorage`   | Sync localStorage data | Theme/token storage      |
| `useWindowSize`     | Track screen size      | Responsive UI            |
| `useTheme`          | Theme management       | Dark/light mode          |
| `useForm`           | Form handling          | Validation/forms         |
| `usePagination`     | Pagination logic       | Data tables              |
| `useScrollPosition` | Track scroll           | Sticky navbar            |
| `useOutsideClick`   | Detect outside click   | Dropdown/modal close     |
| `useMediaQuery`     | Responsive breakpoints | Mobile/tablet layout     |
| `usePrevious`       | Store previous value   | Compare old/new state    |
| `useOnlineStatus`   | Detect internet status | Offline banners          |
| `useClipboard`      | Copy to clipboard      | Copy buttons             |
| `useTimeout`        | Timeout handling       | Delayed actions          |
| `useInterval`       | Interval handling      | Timers/countdowns        |
| `useQueryParams`    | URL query handling     | Filter/search state      |
| `useSocket`         | WebSocket handling     | Chat/realtime apps       |
| `usePermissions`    | Role/permission checks | Admin access             |

---

## 📌 Portals

Portals render React components outside the normal parent DOM hierarchy.

| Concept           | Purpose                     | Example                     | Real-World Usage |
| ----------------- | --------------------------- | --------------------------- | ---------------- |
| Portal Rendering  | Render outside parent DOM   | `createPortal()`            | Modals           |
| Overlay UI        | Prevent layout issues       | Popup/tooltip               | Dropdowns        |
| Separate DOM Node | Render into another element | `document.getElementById()` | Global UI layers |
| Escape Overflow   | Avoid clipping/z-index bugs | Fixed overlays              | Sidebar menus    |

```html
<!-- index.html -->
<div id="root"></div>
<div id="portal-root"></div>
```

```jsx
import { createPortal } from "react-dom";

function Modal() {
  return createPortal(
    <div className="modal">Modal Content</div>,
    document.getElementById("portal-root"),
  );
}
```

| Portal Usage   | Purpose/Benefit          | Real-World Example  |
| -------------- | ------------------------ | ------------------- |
| Modals         | Better overlay layering  | Popup dialogs       |
| Tooltips       | Escape parent overflow   | Hover info          |
| Dropdown Menus | Fixed floating UI        | Navbar/profile menu |
| Toast Messages | Global overlay rendering | Notifications       |
| Side Drawers   | Avoid z-index issues     | Mobile sidebar      |

| Best Practice              | Notes                       |
| -------------------------- | --------------------------- |
| Use for overlay UI         | Modals, tooltips, dropdowns |
| Keep separate portal root  | Cleaner structure           |
| Handle focus/accessibility | Better keyboard navigation  |
| Avoid unnecessary portals  | Use only when needed        |

---

## 📌 Error Handling

Error handling prevents app crashes and manages unexpected issues gracefully.

| Error Type        | Solution                 | Example               | Real-World Usage     |
| ----------------- | ------------------------ | --------------------- | -------------------- |
| API Errors        | `try/catch`              | Failed API request    | Network issues       |
| UI Errors         | Error Boundary           | Component crash       | Prevent blank screen |
| Async Errors      | `.catch()` / `try/catch` | Async request failure | Form submission      |
| Validation Errors | Input validation         | Invalid form data     | Login/signup forms   |
| Route Errors      | 404/Error pages          | Invalid route         | Missing pages        |

```jsx
// try/catch
try {
  const response = await fetch("/api/users");
} catch (error) {
  console.log(error);
}
```

```jsx
// Promise Error
fetch("/api/users").catch((error) => {
  console.log(error);
});
```

```jsx
// Error Boundary
class ErrorBoundary extends React.Component {
  state = { hasError: false };

  static getDerivedStateFromError() {
    return { hasError: true };
  }

  render() {
    if (this.state.hasError) {
      return <h1>Something went wrong</h1>;
    }

    return this.props.children;
  }
}
```

| Best Practice            | Notes                     |
| ------------------------ | ------------------------- |
| Always handle API errors | Prevent app crashes       |
| Show user-friendly UI    | Better UX                 |
| Use Error Boundaries     | Catch UI rendering errors |
| Validate user input      | Prevent invalid requests  |
| Log important errors     | Easier debugging          |

| Real-World Usage | Example                |
| ---------------- | ---------------------- |
| API Failure      | Show retry message     |
| Form Validation  | Invalid email/password |
| Page Crash       | Error fallback UI      |
| 404 Route        | Custom not-found page  |

---

## 📌 React Patterns

React patterns are reusable architectural approaches for building scalable and maintainable applications.

| Pattern                  | Purpose                      | Example               | Real-World Usage   |
| ------------------------ | ---------------------------- | --------------------- | ------------------ |
| Component Composition    | Combine reusable components  | Layout systems        | Dashboards         |
| Container/Presentational | Separate logic and UI        | Smart/Dumb components | Large applications |
| Custom Hooks Pattern     | Reuse business logic         | `useAuth()`           | Shared features    |
| Provider Pattern         | Share global state           | Context providers     | Theme/auth         |
| Compound Components      | Related component groups     | Tabs/Accordion        | UI libraries       |
| Render Props             | Share dynamic rendering      | Function as child     | Reusable logic     |
| Higher-Order Component   | Wrap component functionality | Auth wrappers         | Permissions        |
| Controlled Components    | React-controlled state       | Form inputs           | Dynamic forms      |
| Feature-based Structure  | Organize by feature          | `/features/auth`      | Scalable apps      |

```jsx
// Composition Pattern
function Layout({ children }) {
  return <div>{children}</div>;
}
```

```jsx
// Custom Hook Pattern
function useToggle() {
  const [open, setOpen] = useState(false);

  return {
    open,
    setOpen,
  };
}
```

```jsx
// Compound Component
<Tabs>
  <Tabs.List />
  <Tabs.Panel />
</Tabs>
```

| Best Practice              | Notes                  |
| -------------------------- | ---------------------- |
| Prefer composition         | Flexible architecture  |
| Keep logic reusable        | Use custom hooks       |
| Separate UI/business logic | Better maintainability |
| Organize by feature        | Easier scaling         |
| Avoid deeply nested props  | Use Context/store      |

---

## 📌 React Architecture

React architecture defines how React applications are structured, organized, and scaled.

| Architecture Part       | Purpose                 | Example                 | Real-World Usage   |
| ----------------------- | ----------------------- | ----------------------- | ------------------ |
| Component Structure     | Organize reusable UI    | Button, Card, Modal     | Design systems     |
| Feature-based Structure | Group by feature        | `/features/auth`        | Large applications |
| Routing Structure       | Manage pages/navigation | React Router            | Multi-page apps    |
| State Management        | Manage shared data      | Context, Redux, Zustand | Dashboards         |
| API Layer               | Separate backend logic  | `/services/api.js`      | API handling       |
| Hooks Layer             | Reusable business logic | `/hooks/useAuth.js`     | Shared logic       |
| Layout System           | Shared page structure   | Navbar/sidebar/footer   | Admin panels       |
| Global Providers        | App-wide configuration  | Theme/Auth provider     | Large apps         |
| Utility Layer           | Shared helper functions | `/utils/formatDate.js`  | Common logic       |

| Common Folder | Purpose          |
| ------------- | ---------------- |
| `components/` | Reusable UI      |
| `features/`   | Feature modules  |
| `pages/`      | Route pages      |
| `hooks/`      | Custom hooks     |
| `services/`   | API logic        |
| `store/`      | Global state     |
| `layouts/`    | Shared layouts   |
| `utils/`      | Helper functions |

| Best Practice               | Notes                |
| --------------------------- | -------------------- |
| Use feature-based structure | Better scalability   |
| Keep components reusable    | Easier maintenance   |
| Separate business logic     | Cleaner architecture |
| Centralize API/state logic  | Better organization  |
| Avoid deeply nested folders | Simpler structure    |

| Real-World Usage | Architecture Style      |
| ---------------- | ----------------------- |
| SaaS Dashboard   | Feature-based structure |
| E-commerce       | Shared state + services |
| Design System    | Reusable components     |
| Enterprise Apps  | Modular architecture    |

---

## 📌 React + TypeScript

TypeScript adds static typing and better developer safety to React applications.

| Concept            | Purpose                   | Example              | Real-World Usage    |
| ------------------ | ------------------------- | -------------------- | ------------------- |
| Typed Props        | Validate component props  | `type Props = {}`    | Reusable components |
| Typed State        | Strong state types        | `useState<string>()` | Forms               |
| Event Types        | Type-safe events          | `React.ChangeEvent`  | Input handling      |
| Interface / Type   | Define data structure     | `interface User {}`  | API models          |
| Generic Components | Reusable typed components | `<T>`                | Tables/forms        |
| API Response Types | Typed API data            | `User[]`             | API handling        |
| Optional Props     | Flexible props            | `title?: string`     | Shared UI           |
| Type Inference     | Auto type detection       | `const count = 0`    | Cleaner code        |

| Common React Types | Example                               |
| ------------------ | ------------------------------------- |
| Props              | `type Props = { name: string }`       |
| State              | `useState<number>(0)`                 |
| Input Event        | `React.ChangeEvent<HTMLInputElement>` |
| Click Event        | `React.MouseEvent<HTMLButtonElement>` |
| Children           | `React.ReactNode`                     |
| API Data           | `User[]`                              |

```tsx
// Type Inference
type ButtonProps = {
  text: string;
};

function Button({ text }: ButtonProps) {
  return <button>{text}</button>;
}
```

```tsx
const [count, setCount] = useState<number>(0);
```

```tsx
const handleChange = (e: React.ChangeEvent<HTMLInputElement>) => {
  console.log(e.target.value);
};
```

| Best Practice           | Notes                    |
| ----------------------- | ------------------------ |
| Type props and API data | Better safety            |
| Prefer `type` for props | Cleaner component typing |
| Avoid `any`             | Lose TypeScript benefits |
| Reuse shared types      | Better maintainability   |
| Use strict mode         | Catch more errors        |

---

## 📌 Testing

Testing verifies that React components and application features work correctly.

| Testing Type        | Purpose                        | Example            | Real-World Usage   |
| ------------------- | ------------------------------ | ------------------ | ------------------ |
| Unit Testing        | Test single function/component | Button click       | Utility/components |
| Integration Testing | Test connected features        | Form submission    | User flows         |
| UI Testing          | Test rendered UI               | Check text/buttons | Component testing  |
| End-to-End (E2E)    | Test full application flow     | Login → Dashboard  | Production apps    |
| Snapshot Testing    | Detect UI changes              | Component snapshot | Design systems     |

| Tool / Library        | Usage                   |
| --------------------- | ----------------------- |
| Jest                  | Test runner/assertions  |
| React Testing Library | React component testing |
| Vitest                | Fast Vite testing       |
| Cypress               | E2E browser testing     |
| Playwright            | Modern E2E testing      |

```bash
npm install --save-dev jest @testing-library/react
```

```jsx
// Button.jsx
function Button() {
  return <button>Click Me</button>;
}

export default Button;
```

```jsx
// Button.test.jsx
import { render, screen } from "@testing-library/react";
import Button from "./Button";

test("renders button", () => {
  render(<Button />);

  expect(screen.getByText("Click Me")).toBeInTheDocument();
});
```

| Best Practice          | Notes                       |
| ---------------------- | --------------------------- |
| Test user behavior     | Better real-world testing   |
| Keep tests simple      | Easier maintenance          |
| Test critical flows    | Auth, payments, forms       |
| Avoid over-testing UI  | Focus on important behavior |
| Use E2E for full flows | Real application testing    |

---

## 📌 Debugging

Debugging is the process of finding and fixing issues in React applications.

| Debugging Method | Purpose                    | Example                    | Real-World Usage      |
| ---------------- | -------------------------- | -------------------------- | --------------------- |
| `console.log()`  | Inspect values/state       | `console.log(data)`        | API debugging         |
| React DevTools   | Inspect component tree     | State/props inspection     | Component debugging   |
| Browser DevTools | Inspect errors/network     | Console/network tab        | API issues            |
| Error Boundaries | Catch UI crashes           | Fallback UI                | Prevent blank screens |
| Breakpoints      | Pause code execution       | DevTools debugger          | Logic debugging       |
| Network Tab      | Inspect API requests       | Request/response debugging | Backend issues        |
| Source Maps      | Debug original source code | Vite/Webpack source maps   | Production debugging  |

| Common React Issue     | Debugging Solution         |
| ---------------------- | -------------------------- |
| Infinite re-render     | Check `useEffect` deps     |
| Component not updating | Verify state/props changes |
| API not working        | Inspect network tab        |
| UI crash               | Check console errors       |
| Wrong list rendering   | Verify unique `key`        |

```jsx
// Console Debugging
console.log(users);
```

```jsx
// Debug State Changes
useEffect(() => {
  console.log(count);
}, [count]);
```

```jsx
// Error Boundary
<ErrorBoundary>
  <App />
</ErrorBoundary>
```

| Best Practice           | Notes                    |
| ----------------------- | ------------------------ |
| Read console errors     | Fastest debugging source |
| Use React DevTools      | Inspect hooks/state      |
| Debug one issue at time | Easier troubleshooting   |
| Check network requests  | API debugging            |
| Avoid excessive logs    | Cleaner debugging        |

---

## 📌 Accessibility (a11y)

Accessibility makes React applications usable for all users, including keyboard and screen-reader users.

| Accessibility Feature | Purpose                      | Example                       | Real-World Usage |
| --------------------- | ---------------------------- | ----------------------------- | ---------------- |
| Semantic HTML         | Better structure/readability | `<button>`, `<nav>`           | Accessible UI    |
| `alt` Text            | Describe images              | `alt="Product Image"`         | Screen readers   |
| Labels                | Accessible form inputs       | `<label htmlFor="email" />`   | Forms            |
| Keyboard Navigation   | Navigate without mouse       | `tabIndex`                    | Menus/modals     |
| ARIA Attributes       | Extra accessibility info     | `aria-label="Close"`          | Icon buttons     |
| Focus Management      | Control keyboard focus       | `inputRef.current.focus()`    | Modals/forms     |
| Color Contrast        | Improve readability          | Accessible color combinations | UI readability   |

| Common ARIA Attribute | Usage                    |
| --------------------- | ------------------------ |
| `aria-label`          | Accessible label         |
| `aria-hidden`         | Hide from screen readers |
| `aria-expanded`       | Toggle state             |
| `role`                | Define element role      |

```jsx
<label htmlFor="email">
  Email
</label>

<input
  id="email"
  type="email"
/>

<button aria-label="Close Menu">✕</button>

<img src="/product.jpg" alt="Laptop" />
```

| Best Practice             | Notes                      |
| ------------------------- | -------------------------- |
| Use semantic HTML         | Better accessibility       |
| Always add form labels    | Screen-reader support      |
| Ensure keyboard access    | Better navigation          |
| Add meaningful `alt` text | Accessible images          |
| Manage focus properly     | Better modal/navigation UX |

### Accessibility Examples

| Category         | Feature          | Example                                   |
| ---------------- | ---------------- | ----------------------------------------- |
| Semantic         | Button           | `<button>Save</button>`                   |
|                  | Navigation       | `<nav>...</nav>`                          |
|                  | Header           | `<header>...</header>`                    |
|                  | Main             | `<main>...</main>`                        |
|                  | Footer           | `<footer>...</footer>`                    |
|                  | Form             | `<form>...</form>`                        |
|                  | Table            | `<table>...</table>`                      |
|                  | Caption          | `<caption>User Data</caption>`            |
|                  | Link             | `<a href="/about">About</a>`              |
| Forms            | Label            | `<label htmlFor="email">Email</label>`    |
|                  | Input ID         | `<input id="email" />`                    |
|                  | Placeholder      | `<input placeholder="Search" />`          |
|                  | Required         | `<input required />`                      |
|                  | Disabled         | `<button disabled />`                     |
|                  | Checkbox         | `<input type="checkbox" />`               |
|                  | Radio            | `<input type="radio" />`                  |
|                  | Select           | `<select>...</select>`                    |
|                  | Auto Focus       | `<input autoFocus />`                     |
| Keyboard & Focus | Navigation       | `tabIndex={0}`                            |
|                  | Focus Management | `inputRef.current.focus()`                |
|                  | Skip Link        | `<a href="#main">Skip to Content</a>`     |
| ARIA             | Label            | `aria-label="Close"`                      |
|                  | Hidden           | `aria-hidden="true"`                      |
|                  | Expanded         | `aria-expanded={open}`                    |
|                  | Busy             | `aria-busy="true"`                        |
|                  | Live             | `aria-live="polite"`                      |
|                  | Described By     | `aria-describedby="tooltip"`              |
|                  | Icon Button      | `<button aria-label="Search">🔍</button>` |
| Roles            | Dialog           | `role="dialog"`                           |
|                  | Modal            | `role="dialog" aria-modal="true"`         |
|                  | Alert            | `role="alert"`                            |
|                  | Progressbar      | `role="progressbar"`                      |
|                  | Tabs             | `role="tablist"`                          |
|                  | Tab              | `role="tab"`                              |
|                  | Tab Panel        | `role="tabpanel"`                         |

---

## 📌 React Ecosystem

React ecosystem includes libraries, tools, frameworks, and services commonly used with React applications.

| Category             | Tool / Library    | Purpose                    | Real-World Usage      |
| -------------------- | ----------------- | -------------------------- | --------------------- |
| Framework            | Next.js           | Full-stack React framework | Production apps       |
| Build Tool           | Vite              | Fast development/build     | Modern React apps     |
| Routing              | React Router      | SPA navigation             | Multi-page apps       |
| State Management     | Redux Toolkit     | Global state               | Enterprise dashboards |
|                      | Zustand           | Lightweight global store   | SaaS apps             |
| API Handling         | Axios             | HTTP requests              | Backend communication |
|                      | React Query       | API caching/sync           | Server state          |
| Forms                | React Hook Form   | Form handling              | Complex forms         |
| Validation           | Zod               | Schema validation          | Form/API validation   |
| Styling              | Tailwind CSS      | Utility-first styling      | Modern UI             |
|                      | Styled Components | CSS-in-JS                  | Dynamic themes        |
| UI Components        | MUI               | Material UI components     | Admin panels          |
|                      | shadcn/ui         | Modern reusable UI         | Design systems        |
| Animation            | Framer Motion     | Animations                 | Interactive UI        |
| Backend Services     | Firebase          | Backend/auth/database      | Full-stack apps       |
|                      | Supabase          | Open-source backend        | SaaS products         |
| Authentication       | Firebase Auth     | Authentication             | Login systems         |
| Testing              | Jest              | Unit testing               | Component testing     |
|                      | Cypress           | End-to-end testing         | User flows            |
| Realtime             | Socket.io Client  | Real-time communication    | Chat apps             |
| Internationalization | i18next           | Multi-language support     | Global apps           |
| Charts               | Recharts          | Data visualization         | Analytics dashboards  |
| Tables               | TanStack Table    | Advanced tables            | Data-heavy apps       |
| Drag & Drop          | dnd-kit           | Drag/drop interactions     | Kanban boards         |

| Best Practice                   | Notes                        |
| ------------------------------- | ---------------------------- |
| Choose minimal libraries        | Avoid unnecessary complexity |
| Prefer community-standard tools | Better support               |
| Organize ecosystem by feature   | Easier scalability           |
| Avoid overlapping libraries     | Cleaner architecture         |

---

## 📌 Modern & Internal React Concepts

| Concept                    | Purpose                      | Simple Meaning                          | Real-World Usage      |
| -------------------------- | ---------------------------- | --------------------------------------- | --------------------- |
| Reconciliation             | Efficient UI updates         | Compare old/new Virtual DOM             | Fast UI rendering     |
| Diffing Algorithm          | Detect changed elements      | Find what actually changed              | Optimized DOM updates |
| Concurrent Rendering       | Non-blocking rendering       | React updates UI smoothly in background | Better UX/performance |
| Suspense                   | Handle async loading states  | Show fallback while waiting             | Lazy loading/API UI   |
| Suspense for Data Fetching | Wait for async data          | Pause UI until data is ready            | Modern data loading   |
| Server Components          | Render components on server  | Reduce browser JS                       | Next.js apps          |
| Hydration                  | Activate SSR HTML            | Attach React logic to server HTML       | SSR applications      |
| Streaming                  | Send UI in chunks            | Render page progressively               | Faster page loading   |
| React Compiler             | Automatic React optimization | React optimizes code automatically      | Future performance    |

| Concept              | Real Example                  |
| -------------------- | ----------------------------- |
| Reconciliation       | Update changed todo item only |
| Diffing Algorithm    | Detect changed list item      |
| Concurrent Rendering | Smooth search typing          |
| Suspense             | Loading spinner fallback      |
| Server Components    | Server-rendered product page  |
| Hydration            | SSR page becomes interactive  |
| Streaming            | Page loads section by section |
| React Compiler       | Auto memoization optimization |

### Reconciliation Flow

```txt
State Change
      ↓
New Virtual DOM Created
      ↓
Diffing Algorithm Compares Changes
      ↓
React Finds Updated Elements
      ↓
Update Only Changed Real DOM
```

---

## 📌 Deprecated / Avoid Patterns

| Pattern / Feature              | Avoid Reason                 | Preferred Alternative         |
| ------------------------------ | ---------------------------- | ----------------------------- |
| Class Components               | More boilerplate             | Functional Components + Hooks |
| `componentWillMount`           | Deprecated lifecycle         | `useEffect()`                 |
| `componentWillReceiveProps`    | Deprecated lifecycle         | `useEffect()`                 |
| `componentWillUpdate`          | Deprecated lifecycle         | `useEffect()`                 |
| String Refs                    | Legacy ref system            | `useRef()`                    |
| Direct DOM Manipulation        | Breaks React flow            | React state/refs              |
| Props Drilling                 | Hard maintenance             | Context/Zustand/Redux         |
| Mutating State                 | React may not detect updates | Immutable updates             |
| Array Index as Key             | UI/rendering bugs            | Stable unique IDs             |
| Too Many Global States         | Unnecessary complexity       | Keep local state local        |
| Large Components               | Hard readability             | Small reusable components     |
| Nested Ternaries               | Hard to maintain             | Separate logic                |
| Inline Heavy Logic             | Poor readability/performance | Move outside JSX              |
| Excessive `useEffect`          | Complex side effects         | Derived state/direct logic    |
| Overusing Context API          | Unnecessary re-renders       | Split contexts/store          |
| Over-Memoization               | Added complexity             | Optimize only when needed     |
| Uncontrolled Side Effects      | Memory leaks                 | Cleanup functions             |
| Anonymous Functions Everywhere | Unnecessary re-renders       | `useCallback` when needed     |
| Copying Props to State         | Duplicate source of truth    | Use props directly            |
| Massive Global CSS             | Style conflicts              | Scoped/component styles       |

| Legacy / Old       | Modern Standard       |
| ------------------ | --------------------- |
| Classes            | Hooks                 |
| Lifecycle Methods  | `useEffect`           |
| HOC-heavy patterns | Hooks/composition     |
| Redux Boilerplate  | Redux Toolkit/Zustand |
| CRA                | Vite / Next.js        |

---

## 📌 Real-World React Systems

Real-world React systems combine routing, state management, APIs, authentication, performance optimization, and scalable architecture together.

| System Type            | Purpose                    | Common Stack / Usage         |
| ---------------------- | -------------------------- | ---------------------------- |
| SPA Dashboard          | Client-side applications   | React Router + Zustand       |
| SSR Application        | SEO + faster initial load  | Next.js                      |
| SSG Website            | Static pre-rendered pages  | Next.js / Gatsby             |
| Design System          | Reusable UI components     | Storybook + Tailwind         |
| Authentication System  | Login/user management      | Firebase/Auth0/JWT           |
| API-driven App         | Backend-connected frontend | Axios + React Query          |
| E-commerce System      | Cart/payment/products      | Stripe + Redux/Zustand       |
| Realtime System        | Live updates               | Socket.io                    |
| CMS-driven Frontend    | Dynamic content websites   | Headless CMS + React         |
| Admin Panel            | Data-heavy management UI   | Tables/charts/forms          |
| Multi-language System  | Internationalization       | i18next                      |
| Offline-first App      | Offline support            | PWA + Service Workers        |
| Performance-focused UI | Faster rendering           | Memoization + virtualization |

```txt
Large React App Structure

Frontend UI
     ↓
Routing System
     ↓
Global State
     ↓
API Layer
     ↓
Backend Services
```

```txt
Typical Production React Stack

React
 + React Router
 + Zustand/Redux
 + Axios/React Query
 + Tailwind CSS
 + Authentication
 + Backend API
```

| Common Production Features | Example                |
| -------------------------- | ---------------------- |
| Authentication             | Login/signup           |
| Protected Routes           | Admin/dashboard access |
| API Caching                | Faster API responses   |
| Lazy Loading               | Faster initial load    |
| Error Boundaries           | Prevent app crashes    |
| Form Validation            | Secure form handling   |
| Responsive UI              | Mobile/tablet support  |
| Dark Mode                  | Theme switching        |

| Best Practice               | Notes                |
| --------------------------- | -------------------- |
| Use feature-based structure | Better scalability   |
| Keep reusable components    | Easier maintenance   |
| Separate API/business logic | Cleaner architecture |
| Optimize rendering wisely   | Better performance   |
| Use shared design systems   | UI consistency       |

---

## 📌 Deployment

Deployment is the process of building and hosting a React application for production use.

| Concept               | Purpose                  | Example         | Real-World Usage  |
| --------------------- | ------------------------ | --------------- | ----------------- |
| Production Build      | Optimized app files      | `npm run build` | Live websites     |
| Hosting               | Serve app online         | Vercel, Netlify | Public deployment |
| Environment Variables | Store configs/secrets    | `.env`          | API URLs          |
| CI/CD                 | Automatic deployment     | GitHub Actions  | Team workflows    |
| Domain Setup          | Custom website URL       | `myapp.com`     | Production apps   |
| SSL/HTTPS             | Secure connection        | HTTPS           | Secure websites   |
| Static Hosting        | Serve static React build | Netlify/Vercel  | SPA apps          |
| Server Deployment     | Host SSR/full-stack apps | Next.js server  | SSR apps          |

| Deployment Platform | Usage                    |
| ------------------- | ------------------------ |
| Vercel              | React/Next.js hosting    |
| Netlify             | Static frontend hosting  |
| Firebase Hosting    | Firebase app hosting     |
| AWS                 | Enterprise/cloud hosting |
| Render              | Full-stack deployment    |

```bash
# Create Production Build
npm run build

# Preview Production Build
npm run preview
```

```txt
React App
    ↓
Production Build
    ↓
Deploy to Hosting
    ↓
Live Website
```

| Common Deployment Files | Purpose                 |
| ----------------------- | ----------------------- |
| `.env`                  | Environment variables   |
| `dist/`                 | Production build output |
| `vite.config.js`        | Build configuration     |
| `package.json`          | Scripts/dependencies    |

| Best Practice                 | Notes                     |
| ----------------------------- | ------------------------- |
| Use environment variables     | Avoid hardcoded secrets   |
| Optimize production build     | Better performance        |
| Enable HTTPS                  | Secure deployment         |
| Use CI/CD pipelines           | Automated deployments     |
| Test production build locally | Prevent deployment issues |

| Real-World Usage | Deployment Type      |
| ---------------- | -------------------- |
| Portfolio Site   | Netlify/Vercel       |
| SaaS Dashboard   | Vercel + API backend |
| Enterprise App   | AWS/cloud deployment |
| E-commerce       | SSR deployment       |

### CI/CD

- CI/CD automates testing, building, and deploying applications.

| Term        | Full Form                      | Purpose                 | Real-World Usage    |
| ----------- | ------------------------------ | ----------------------- | ------------------- |
| CI          | Continuous Integration         | Auto test/build code    | Team development    |
| CD          | Continuous Deployment/Delivery | Auto deploy application | Production release  |
| Pipeline    | Automated workflow             | Build → Test → Deploy   | DevOps workflow     |
| Build Step  | Create production files        | `npm run build`         | Production build    |
| Test Step   | Run automated tests            | Jest/Cypress            | Prevent broken code |
| Deploy Step | Publish application            | Vercel/Netlify          | Live deployment     |

| Popular CI/CD Tool | Usage                    |
| ------------------ | ------------------------ |
| GitHub Actions     | GitHub automation        |
| GitLab CI/CD       | GitLab pipelines         |
| Jenkins            | Enterprise automation    |
| Vercel CI/CD       | Auto frontend deployment |
| Netlify CI/CD      | Static site deployment   |

---

---

---
