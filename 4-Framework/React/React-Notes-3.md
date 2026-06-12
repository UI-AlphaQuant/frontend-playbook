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

## 📌 REST vs GraphQL

- REST exposes multiple resource-based endpoints, while GraphQL uses a single endpoint that allows clients to request exactly the data they need.

| Feature        | REST             | GraphQL                 |
| -------------- | ---------------- | ----------------------- |
| Type           | API Architecture | Query Language For APIs |
| Endpoint       | Multiple         | Single                  |
| Data Fetching  | Fixed Response   | Client Chooses Data     |
| Over Fetching  | Possible         | ❌                      |
| Under Fetching | Possible         | ❌                      |
| Learning Curve | Easy             | Medium                  |
| Caching        | Easy             | More Complex            |
| Popularity     | Most Common      | Growing                 |

| Scenario                  | REST | GraphQL |
| ------------------------- | ---- | ------- |
| CRUD Applications         | ✅   | ⚠️      |
| Admin Panels              | ✅   | ⚠️      |
| ERP Systems               | ✅   | ⚠️      |
| CRM Systems               | ✅   | ⚠️      |
| Internal Business Tools   | ✅   | ⚠️      |
| E-Commerce APIs           | ✅   | ✅      |
| Mobile Apps               | ⚠️   | ✅      |
| Social Media Apps         | ⚠️   | ✅      |
| Complex Dashboards        | ⚠️   | ✅      |
| Data-Heavy Applications   | ⚠️   | ✅      |
| Multiple Data Sources     | ❌   | ✅      |
| Microservices Aggregation | ❌   | ✅      |

---

## 📌 CMS (Content Management System)

- In React applications, a CMS is typically used as a backend content source. React fetches content (pages, blogs, banners, products, FAQs, etc.) from the CMS via APIs and renders it dynamically.

| Item          | Description                           |
| ------------- | ------------------------------------- |
| Purpose       | Manage Website Content Without Coding |
| Used By       | Content Editors, Marketing Teams      |
| Content Types | Blogs, Pages, Products, FAQs          |
| React Role    | Frontend Consumes CMS Data            |

| Type            | Description                 | Examples                   |
| --------------- | --------------------------- | -------------------------- |
| Traditional CMS | Frontend + Backend Together | WordPress, Drupal          |
| Headless CMS    | Backend Only, API Driven    | Contentful, Strapi, Sanity |
| Hybrid CMS      | Traditional + Headless      | WordPress Headless         |

```text
CMS > Stores Content
React > Displays Content
API > Connects Both
```

```txt
Contentful (CMS)
↓
REST / GraphQL (API)
↓
React (App)
↓
Blog Page (UI)
```

| Project            | CMS Needed? |
| ------------------ | ----------- |
| Blog               | ✅          |
| News Website       | ✅          |
| Company Website    | ✅          |
| Documentation      | ✅          |
| E-Commerce Content | ✅          |
| CRM                | ❌          |
| ERP                | ❌          |
| Admin Dashboard    | ❌          |

| Frontend         | SEO          |
| ---------------- | ------------ |
| React SPA (Vite) | ❌ Poor      |
| Next.js + CMS    | ✅ Excellent |
| Astro + CMS      | ✅ Excellent |
| Gatsby + CMS     | ✅ Excellent |

| CMS        | Self Hosted | Free Tier | Paid Starts       |
| ---------- | ----------- | --------- | ----------------- |
| WordPress  | ✅          | ✅        | Hosting Cost Only |
| Strapi     | ✅          | ✅        | Free Self Hosted  |
| Directus   | ✅          | ✅        | Free Self Hosted  |
| Contentful | ❌          | ✅        | $$$               |
| Sanity     | ❌          | ✅        | $$                |
| Storyblok  | ❌          | ✅        | $$$               |
| Prismic    | ❌          | ✅        | $$                |
| Ghost      | ✅          | Limited   | $$                |

- Next.js
  - Provides: Frontend, SSR, SSG, ISR, API Routes, Server Actions
  - Not provide: Content Management UI, Rich Text Editor, Media Library, Content Workflows, Non-Developer Editing

### Headless WordPress

- WordPress becomes: CMS Only
- Next.js becomes: Frontend Only

```txt
Content Editor
 ↓
WordPress Admin
 ↓
MySQL
 ↓
REST API / GraphQL
 ↓
Next.js
 ↓
Browser
```

| Feature              | Strapi           | WordPress           |
| -------------------- | ---------------- | ------------------- |
| Technology           | Node.js          | PHP                 |
| Database             | PostgreSQL/MySQL | MySQL               |
| API First            | ✅               | ⚠️ Originally No    |
| Headless CMS         | ✅ Native        | ⚠️ Via REST/GraphQL |
| Frontend Included    | ❌               | ✅                  |
| Self Hosted          | ✅               | ✅                  |
| Developer Experience | ⭐⭐⭐⭐⭐       | ⭐⭐⭐              |

---

## 📌 API Learning Path (Frontend Developer)

| Step | Learn                      | Example            |
| ---- | -------------------------- | ------------------ |
| 1    | Consume Public API         | Users, Products    |
| 2    | GET Request                | Fetch Data         |
| 3    | POST Request               | Create Data        |
| 4    | PUT/PATCH Request          | Update Data        |
| 5    | DELETE Request             | Delete Data        |
| 6    | Authentication             | JWT / Bearer Token |
| 7    | Build Own API              | Node.js + Express  |
| 8    | Connect Frontend & Backend | React ↔ API        |

```jsx
const res = await fetch("https://jsonplaceholder.typicode.com/users");
const data = await res.json();

// Display in React:
{
  users.map((user) => <li>{user.name}</li>);
}
```

| Operation | HTTP Method | Example APIs |
| --------- | ----------- | ------------ |
| Read      | GET         | /users       |
| Create    | POST        | /users       |
| Update    | PUT / PATCH | /users/1     |
| Delete    | DELETE      | /users/1     |

### Use Fake APIs

| API             | Purpose       |
| --------------- | ------------- |
| JSONPlaceholder | Users, Posts  |
| DummyJSON       | Products      |
| FakeStoreAPI    | E-Commerce    |
| ReqRes          | Auth Examples |

- Industry Standard Stack

```txt
React
 ↓
Axios / Fetch
 ↓
Node.js + Express
 ↓
Prisma
 ↓
PostgreSQL
```

---

## 📌 Environment Variables (.env)

| Purpose   | Store Configuration Outside Code                |
| --------- | ----------------------------------------------- |
| Used For  | API URLs, Keys, Secrets, Configs                |
| File Name | `.env`                                          |
| Benefits  | Security, Flexibility, Environment-Based Config |

### Accessing Variables

| Framework | Syntax                            |
| --------- | --------------------------------- |
| Vite      | `import.meta.env.VITE_API_URL`    |
| CRA       | `process.env.REACT_APP_API_URL`   |
| Next.js   | `process.env.NEXT_PUBLIC_API_URL` |
| Node.js   | `process.env.DB_HOST`             |

```js
// env file: VITE_API_URL=https://api.com
fetch(`${import.meta.env.VITE_API_URL}/users`);
```

| Environment Files  | Purpose            |
| ------------------ | ------------------ |
| `.env`             | Default            |
| `.env.local`       | Local Machine Only |
| `.env.development` | Development        |
| `.env.production`  | Production         |
| `.env.test`        | Testing            |

---

## 📌 dangerouslySetInnerHTML

- dangerouslySetInnerHTML allows React to render raw HTML content directly into the DOM and is commonly used for CMS or rich-text content, but should be sanitized to prevent XSS attacks.

| Purpose             | Render Raw HTML Inside React         |
| ------------------- | ------------------------------------ |
| React Equivalent Of | `element.innerHTML`                  |
| Use Case            | CMS Content, Rich Text, Blog Content |
| Risk                | XSS (Cross-Site Scripting)           |

```jsx
const htmlContent = "<h2>Hello</h2>";

return (
  <div
    dangerouslySetInnerHTML={{
      __html: htmlContent,
    }}
  />
);
```

| Source     | Example          |
| ---------- | ---------------- |
| WordPress  | Blog Content     |
| Strapi     | Rich Text        |
| Contentful | CMS Content      |
| TinyMCE    | Editor Output    |
| CKEditor   | Rich Text Output |

```json
// API:
{
  "content": "<p>Learn React</p>"
}
```

```jsx
// React:
<div
  dangerouslySetInnerHTML={{
    __html: post.content,
  }}
/>
```

### Safe Usage

```bash
npm install dompurify
```

```jsx
import DOMPurify from "dompurify";

<div
  dangerouslySetInnerHTML={{
    __html: DOMPurify.sanitize(htmlContent),
  }}
/>;
```

| Approach                              | Result              |
| ------------------------------------- | ------------------- |
| `{html}`                              | Render As Text      |
| `dangerouslySetInnerHTML`             | Render As HTML      |
| `DOMPurify + dangerouslySetInnerHTML` | Safe HTML Rendering |

---
