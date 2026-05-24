# 👉 Core Fundamentals

## 📌 Introduction to Next.js

Next.js is a React framework for building full-stack web applications with routing, server rendering, APIs, SEO, and performance optimization.

| Core Features      | Usage                       |
| ------------------ | --------------------------- |
| File-based Routing | Automatic routes from files |
| SSR                | Server-rendered pages       |
| SSG                | Static pre-rendered pages   |
| ISR                | Incremental static updates  |
| Server Components  | Server-side rendering       |
| API Routes         | Backend APIs                |
| Middleware         | Auth, redirects, rewrites   |
| Image Optimization | Optimized responsive images |
| SEO Support        | Metadata & indexing         |

| Rendering Types | Usage           |
| --------------- | --------------- |
| CSR             | Interactive UI  |
| SSR             | Dynamic content |
| SSG             | Static pages    |
| ISR             | Hybrid updates  |

### React vs Next.js

| React            | Next.js              |
| ---------------- | -------------------- |
| UI library       | Full-stack framework |
| Manual routing   | Built-in routing     |
| Separate backend | Built-in APIs        |
| CSR-focused      | SSR/SSG/ISR support  |

### Installation

```bash
npx create-next-app@latest my-app
cd my-app
npm run dev
```

```txt
app/
components/
public/
next.config.js
package.json
```

| Important Files  | Purpose            |
| ---------------- | ------------------ |
| `app/page.js`    | Route page         |
| `app/layout.js`  | Shared layout      |
| `app/loading.js` | Loading UI         |
| `app/error.js`   | Error handling     |
| `middleware.js`  | Request middleware |

- Prefer App Router
- Use Server Components by default
- Keep Client Components minimal
- Use `next/image`
- Fetch data on server when possible

```jsx
// app/page.js

export default async function Home() {
  const res = await fetch("https://api.example.com/posts");
  const posts = await res.json();

  return (
    <main>
      {posts.map((post) => (
        <h2 key={post.id}>{post.title}</h2>
      ))}
    </main>
  );
}
```

---

## 📌 Project Setup

Project setup initializes a Next.js app with React, routing, TypeScript, linting, and production tooling.

| Command           | Usage                   |
| ----------------- | ----------------------- |
| `create-next-app` | Create project          |
| `npm run dev`     | Start dev server        |
| `npm run build`   | Production build        |
| `npm start`       | Start production server |
| `npm run lint`    | Run ESLint              |

```bash
npx create-next-app@latest my-app
cd my-app
npm run dev
```

| Setup Option   | Usage            |
| -------------- | ---------------- |
| TypeScript     | Static typing    |
| ESLint         | Code quality     |
| Tailwind CSS   | Styling          |
| App Router     | Modern routing   |
| src/ Directory | Better structure |

```txt
app/
components/
public/
styles/
next.config.js
package.json
tsconfig.json
```

| File             | Purpose                |
| ---------------- | ---------------------- |
| `package.json`   | Dependencies & scripts |
| `next.config.js` | Next.js config         |
| `.env.local`     | Environment variables  |
| `app/layout.js`  | Root layout            |
| `app/page.js`    | Main page              |

```env
NEXT_PUBLIC_API_URL=https://api.example.com
DB_URL=database_url
```

| Prefix         | Access          |
| -------------- | --------------- |
| `NEXT_PUBLIC_` | Client + Server |
| No Prefix      | Server only     |

- Prefer App Router
- Use TypeScript
- Keep `.env.local` private
- Store reusable UI in `components/`
- Use `src/` for large projects

```tsx
// app/page.tsx

export default function HomePage() {
  return <h1>Next.js App Ready</h1>;
}
```

---

## 📌 Routing System

Next.js uses file-based routing where folders and files automatically become application routes.

| Routing Type        | Usage                         |
| ------------------- | ----------------------------- |
| App Router          | Modern routing system         |
| Pages Router        | Legacy routing system         |
| Static Routes       | Fixed routes                  |
| Dynamic Routes      | Dynamic URL segments          |
| Nested Routes       | Routes inside folders         |
| Catch-all Routes    | Match multiple segments       |
| Route Groups        | Organize routes               |
| Parallel Routes     | Multiple route views          |
| Intercepting Routes | Load routes in current layout |

```txt
app/
├── page.js
├── about/
│   └── page.js
├── blog/
│   └── [slug]/
│       └── page.js
```

| File                      | Route         |
| ------------------------- | ------------- |
| `app/page.js`             | `/`           |
| `app/about/page.js`       | `/about`      |
| `app/blog/[slug]/page.js` | `/blog/react` |

### Dynamic Routes

| Syntax        | Usage              |
| ------------- | ------------------ |
| `[id]`        | Dynamic segment    |
| `[...slug]`   | Catch-all route    |
| `[[...slug]]` | Optional catch-all |

```tsx
// app/blog/[slug]/page.tsx

export default function Blog({ params }) {
  return <h1>{params.slug}</h1>;
}
```

### Navigation

| API           | Usage                   |
| ------------- | ----------------------- |
| `Link`        | Client-side navigation  |
| `useRouter()` | Programmatic navigation |
| `redirect()`  | Server redirects        |

```tsx
import Link from "next/link";

<Link href="/about">About</Link>;
```

```tsx
"use client";

import { useRouter } from "next/navigation";

const router = useRouter();

router.push("/dashboard");
```

### Special Route Files

| File           | Usage          |
| -------------- | -------------- |
| `layout.js`    | Shared layout  |
| `loading.js`   | Loading UI     |
| `error.js`     | Error handling |
| `not-found.js` | 404 page       |

- Prefer App Router
- Use nested layouts
- Use `Link` instead of `<a>`
- Keep routes modular
- Avoid deeply nested routes

```tsx
// app/products/[id]/page.tsx

async function getProduct(id: string) {
  const res = await fetch(`https://api.com/products/${id}`);
  return res.json();
}

export default async function ProductPage({ params }) {
  const product = await getProduct(params.id);

  return <h1>{product.title}</h1>;
}
```

---

## 📌 Layouts & Templates

Layouts and templates help share UI structure across routes while controlling rendering behavior in Next.js App Router.

| File           | Usage                      |
| -------------- | -------------------------- |
| `layout.js`    | Shared persistent layout   |
| `template.js`  | Re-rendered layout wrapper |
| `page.js`      | Route page                 |
| `loading.js`   | Loading UI                 |
| `error.js`     | Error boundary             |
| `not-found.js` | 404 page                   |

### Root Layout

- Required in App Router
- Wraps entire application
- Persistent across navigation

```tsx
// app/layout.tsx

export default function RootLayout({ children }) {
  return (
    <html lang="en">
      <body>{children}</body>
    </html>
  );
}
```

### Nested Layout

- Shared UI for route segments
- Keeps sidebar/navbar persistent

```txt
app/
├── dashboard/
│   ├── layout.js
│   └── page.js
```

```tsx
// app/dashboard/layout.tsx

export default function DashboardLayout({ children }) {
  return (
    <div>
      <aside>Sidebar</aside>
      <main>{children}</main>
    </div>
  );
}
```

### Templates

- Similar to layouts
- Re-render on navigation
- Useful for animations/forms

```tsx
// app/template.tsx

export default function Template({ children }) {
  return <div>{children}</div>;
}
```

| Layout             | Template               |
| ------------------ | ---------------------- |
| Persistent         | Re-rendered            |
| State preserved    | State resets           |
| Better performance | Useful for transitions |

### Loading UI

```tsx
// app/loading.tsx

export default function Loading() {
  return <p>Loading...</p>;
}
```

### Error Handling

```tsx
"use client";

// app/error.tsx

export default function Error({ error, reset }) {
  return (
    <div>
      <p>Something went wrong</p>
      <button onClick={reset}>Retry</button>
    </div>
  );
}
```

```tsx
// app/not-found.tsx

export default function NotFound() {
  return <h1>404 - Page Not Found</h1>;
}
```

- Keep root layout minimal
- Use nested layouts for dashboards
- Use templates only when needed
- Avoid heavy client logic in layouts
- Use loading/error boundaries properly

```tsx
// app/dashboard/layout.tsx

export default function DashboardLayout({ children }) {
  return (
    <section>
      <nav>Dashboard Nav</nav>
      <main>{children}</main>
    </section>
  );
}
```

- Next.js supports nested layouts and templates for different sections/pages of the application.

| Structure          | Usage                        |
| ------------------ | ---------------------------- |
| Root Layout        | Shared across entire app     |
| Nested Layout      | Shared inside route section  |
| Multiple Layouts   | Different UI per section     |
| Multiple Templates | Different re-render behavior |

```txt
app/
├── layout.tsx
├── page.tsx
├── dashboard/
│   ├── layout.tsx
│   ├── page.tsx
│   └── analytics/
│       └── page.tsx
├── admin/
│   ├── layout.tsx
│   └── page.tsx
```

| Layout File            | Applied To       |
| ---------------------- | ---------------- |
| `app/layout.tsx`       | Entire app       |
| `dashboard/layout.tsx` | Dashboard routes |
| `admin/layout.tsx`     | Admin routes     |

```tsx
// app/dashboard/layout.tsx

export default function DashboardLayout({ children }) {
  return (
    <div>
      <aside>Dashboard Sidebar</aside>
      <main>{children}</main>
    </div>
  );
}
```

---

## 📌 Rendering Methods

Next.js supports multiple rendering strategies for performance, SEO, and dynamic content handling.

| Method         | Full Form                       | Usage            |
| -------------- | ------------------------------- | ---------------- |
| CSR            | Client Side Rendering           | Interactive apps |
| SSR            | Server Side Rendering           | Dynamic pages    |
| SSG            | Static Site Generation          | Static content   |
| ISR            | Incremental Static Regeneration | Hybrid updates   |
| Streaming      | Progressive UI rendering        | Faster loading   |
| Edge Rendering | Render near user location       | Low latency      |

### CSR

- Rendered in browser
- Uses client-side JavaScript
- Slower initial load

```tsx
"use client";

import { useEffect, useState } from "react";

export default function Users() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    fetch("/api/users")
      .then((res) => res.json())
      .then(setUsers);
  }, []);

  return <div>{users.length}</div>;
}
```

### SSR

- Rendered on every request
- Good for dynamic SEO pages

```tsx
export default async function Page() {
  const res = await fetch("https://api.com/posts", {
    cache: "no-store",
  });

  const posts = await res.json();

  return <div>{posts.length}</div>;
}
```

### SSG

- Generated at build time
- Fast performance
- Best for static content

```tsx
export default async function Page() {
  const res = await fetch("https://api.com/posts", {
    cache: "force-cache",
  });

  const posts = await res.json();

  return <div>{posts.length}</div>;
}
```

### ISR

- Static page with periodic updates
- Combines SSG + SSR benefits

```tsx
export const revalidate = 60;

export default async function Page() {
  const res = await fetch("https://api.com/posts");
  const posts = await res.json();

  return <div>{posts.length}</div>;
}
```

| Cache Option  | Usage                     |
| ------------- | ------------------------- |
| `force-cache` | Static cached data        |
| `no-store`    | Always fresh data         |
| `revalidate`  | Regenerate after interval |

### Streaming

- Send UI in chunks
- Faster perceived loading
- Works with Suspense

```tsx
import { Suspense } from "react";

<Suspense fallback={<p>Loading...</p>}>
  <Posts />
</Suspense>;
```

### Edge Rendering

```ts
export const runtime = "edge";
```

| Runtime  | Usage                 |
| -------- | --------------------- |
| `nodejs` | Default runtime       |
| `edge`   | Fast global execution |

- Use SSG for static pages
- Use SSR for dynamic SEO pages
- Use ISR for frequently updated content
- Avoid unnecessary CSR
- Use streaming for heavy pages

```tsx
export const revalidate = 300;

export default async function ProductsPage() {
  const res = await fetch("https://api.com/products");
  const products = await res.json();

  return (
    <main>
      {products.map((item) => (
        <h2 key={item.id}>{item.title}</h2>
      ))}
    </main>
  );
}
```

---

## 📌 Server & Client Components

Next.js App Router uses Server Components by default and Client Components for browser interactivity.

| Component Type    | Usage                 |
| ----------------- | --------------------- |
| Server Components | Server-side rendering |
| Client Components | Interactive UI        |
| Shared Components | Reusable components   |
| Async Components  | Server data fetching  |

| Feature             | Server  | Client |
| ------------------- | ------- | ------ |
| Runs on server      | ✅      | ❌     |
| Runs in browser     | ❌      | ✅     |
| SEO friendly        | ✅      | ⚠️     |
| Access browser APIs | ❌      | ✅     |
| Bundle size         | Smaller | Larger |
| Data fetching       | ✅      | ⚠️     |

### Server Component

- Default in App Router
- Supports async/await
- Better performance

```tsx
// app/page.tsx

export default async function Page() {
  const res = await fetch("https://api.com/posts");
  const posts = await res.json();

  return <div>{posts.length}</div>;
}
```

### Client Component

- Uses `"use client"`
- Required for hooks/events/browser APIs

```tsx
"use client";

import { useState } from "react";

export default function Counter() {
  const [count, setCount] = useState(0);

  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
```

| Client-only Features | Usage                    |
| -------------------- | ------------------------ |
| `useState`           | State                    |
| `useEffect`          | Side effects             |
| Event handlers       | Interactions             |
| Browser APIs         | `window`, `localStorage` |

### Component Composition

```tsx
// Server Component
import Counter from "./Counter";

export default function Page() {
  return <Counter />;
}
```

- Server Components can import Client Components
- Client Components cannot import Server Components directly

| Common Rules                      | Notes                    |
| --------------------------------- | ------------------------ |
| `"use client"` at top             | Enables client rendering |
| Avoid overusing Client Components | Increases bundle size    |
| Fetch on server when possible     | Better performance       |
| Keep interactive UI isolated      | Smaller JS bundles       |

- Prefer Server Components by default
- Use Client Components only for interactivity
- Keep client bundle minimal
- Fetch data in Server Components
- Avoid unnecessary `"use client"`

```tsx
// app/products/page.tsx

import AddToCart from "@/components/AddToCart";

export default async function ProductsPage() {
  const res = await fetch("https://api.com/products");
  const products = await res.json();

  return (
    <main>
      {products.map((item) => (
        <div key={item.id}>
          <h2>{item.title}</h2>
          <AddToCart product={item} />
        </div>
      ))}
    </main>
  );
}
```

---

## 📌 Data Fetching

Next.js supports server-side and client-side data fetching with caching, revalidation, and streaming support.

| Fetch Type        | Usage                    |
| ----------------- | ------------------------ |
| Server Fetching   | Default recommended      |
| Client Fetching   | Interactive/live data    |
| Static Fetching   | Cached build-time data   |
| Dynamic Fetching  | Fresh request data       |
| Parallel Fetching | Faster multiple requests |
| Streaming         | Progressive loading UI   |

### Server-side Fetching

- Default in Server Components
- SEO friendly
- Better performance

```tsx
export default async function Page() {
  const res = await fetch("https://api.com/posts");
  const posts = await res.json();

  return <div>{posts.length}</div>;
}
```

### Client-side Fetching

- Used for interactive/live updates
- Requires Client Component

```tsx
"use client";

import { useEffect, useState } from "react";

export default function Users() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    fetch("/api/users")
      .then((res) => res.json())
      .then(setUsers);
  }, []);

  return <div>{users.length}</div>;
}
```

| Cache Option  | Usage                     |
| ------------- | ------------------------- |
| `force-cache` | Static cached data        |
| `no-store`    | Always fresh data         |
| `revalidate`  | Regenerate after interval |

```tsx
// Static Fetching
await fetch("https://api.com/posts", {
  cache: "force-cache",
});
```

```tsx
// Dynamic Fetching
await fetch("https://api.com/posts", {
  cache: "no-store",
});
```

```tsx
// Revalidation
export const revalidate = 60;
```

- Rebuild cached data every 60 seconds

```tsx
// Parallel Fetching
const [posts, users] = await Promise.all([
  fetch("https://api.com/posts").then((r) => r.json()),
  fetch("https://api.com/users").then((r) => r.json()),
]);
```

```tsx
// Streaming with Suspense
import { Suspense } from "react";

<Suspense fallback={<p>Loading...</p>}>
  <Posts />
</Suspense>;
```

```tsx
// Error Handling
const res = await fetch("https://api.com/posts");

if (!res.ok) {
  throw new Error("Failed to fetch");
}
```

- Prefer server-side fetching
- Use `no-store` for real-time data
- Use `revalidate` for ISR
- Fetch in parallel when possible
- Avoid unnecessary client fetching

```tsx
export const revalidate = 300;

export default async function ProductsPage() {
  const res = await fetch("https://api.com/products");
  const products = await res.json();

  return (
    <main>
      {products.map((item) => (
        <h2 key={item.id}>{item.title}</h2>
      ))}
    </main>
  );
}
```

---

## 📌 Route Handlers & APIs

Route Handlers allow building backend APIs directly inside Next.js App Router using standard HTTP methods.

| Method   | Usage          |
| -------- | -------------- |
| `GET`    | Fetch data     |
| `POST`   | Create data    |
| `PUT`    | Update data    |
| `PATCH`  | Partial update |
| `DELETE` | Remove data    |

```txt
app/
└── api/
    └── users/
        └── route.ts
```

| File            | Usage              | Used                                        |
| --------------- | ------------------ | ------------------------------------------- |
| `route.js`      | API route handler  | Create backend API endpoints inside Next.js |
| `middleware.js` | Request middleware | Run logic before request reaches route/page |

### GET Request

```tsx
// app/api/users/route.ts

export async function GET() {
  return Response.json([{ id: 1, name: "John" }]);
}
```

### POST Request

```tsx
export async function POST(req: Request) {
  const body = await req.json();

  return Response.json({
    success: true,
    data: body,
  });
}
```

### Dynamic API Routes

```txt
app/api/users/[id]/route.ts
```

```tsx
export async function GET(req: Request, { params }) {
  return Response.json({
    id: params.id,
  });
}
```

### Request Helpers

| API              | Usage          |
| ---------------- | -------------- |
| `req.json()`     | Read JSON body |
| `req.formData()` | Read form data |
| `req.headers`    | Access headers |
| `req.cookies`    | Access cookies |

### Response Helpers

| API               | Usage                      |
| ----------------- | -------------------------- |
| `Response.json()` | JSON response              |
| `redirect()`      | Redirect request           |
| `NextResponse`    | Advanced response handling |

### Status Codes

```tsx
return Response.json({ error: "Not Found" }, { status: 404 });
```

### Middleware

```tsx
// middleware.ts

import { NextResponse } from "next/server";

export function middleware() {
  return NextResponse.next();
}
```

- Keep APIs lightweight
- Validate request data
- Use proper status codes
- Separate business logic
- Prefer server-side operations

```tsx
// app/api/products/route.ts

export async function GET() {
  const products = await db.product.findMany();

  return Response.json(products);
}
```

---

## 📌 Server Actions

Server Actions allow running server-side functions directly from components without creating separate API routes.

| Feature          | Usage                         |
| ---------------- | ----------------------------- |
| `"use server"`   | Mark server action            |
| Form Actions     | Handle form submission        |
| Server Mutations | Create/update/delete data     |
| Revalidation     | Refresh cached pages          |
| Secure Logic     | Keep sensitive code on server |

### Basic Server Action

```tsx
// app/actions.ts

"use server";

export async function createUser(formData: FormData) {
  const name = formData.get("name");

  console.log(name);
}
```

### Form Action

```tsx
import { createUser } from "./actions";

export default function Page() {
  return (
    <form action={createUser}>
      <input name="name" />
      <button type="submit">Save</button>
    </form>
  );
}
```

| API                | Usage                 |
| ------------------ | --------------------- |
| `FormData`         | Access form values    |
| `revalidatePath()` | Refresh route cache   |
| `redirect()`       | Navigate after action |

### Revalidate Data

```tsx
"use server";

import { revalidatePath } from "next/cache";

export async function addPost() {
  await db.post.create();

  revalidatePath("/posts");
}
```

### Redirect After Action

```tsx
"use server";

import { redirect } from "next/navigation";

export async function login() {
  redirect("/dashboard");
}
```

### Client Component Usage

```tsx
"use client";

export default function Form({ action }) {
  return (
    <form action={action}>
      <button>Submit</button>
    </form>
  );
}
```

- Use Server Actions for mutations
- Keep sensitive logic on server
- Validate form data
- Use revalidation after updates
- Avoid unnecessary API routes

```tsx
// app/actions.ts

"use server";

import { revalidatePath } from "next/cache";

export async function createProduct(formData: FormData) {
  await db.product.create({
    data: {
      title: formData.get("title"),
    },
  });

  revalidatePath("/products");
}
```

---

## 📌 Styling

Next.js supports multiple styling methods including CSS Modules, global CSS, SCSS, Tailwind CSS, and CSS-in-JS.

| Styling Method    | Usage                   |
| ----------------- | ----------------------- |
| CSS Modules       | Scoped component styles |
| Global CSS        | App-wide styles         |
| SCSS/SASS         | Advanced CSS features   |
| Tailwind CSS      | Utility-first styling   |
| Styled Components | CSS-in-JS styling       |
| Inline Styles     | Dynamic styles          |

### CSS Modules

- Scoped locally
- Prevents style conflicts

```txt
Button.module.css
```

```css
.button {
  background: black;
  color: white;
}
```

```tsx
import styles from "./Button.module.css";

<button className={styles.button}>Save</button>;
```

### Global CSS

```txt
app/globals.css
```

```tsx
import "./globals.css";
```

| Rule               | Notes                  |
| ------------------ | ---------------------- |
| Import once        | Usually in `layout.js` |
| Affects entire app | Global styling         |

### SCSS

```bash
npm install sass
```

```scss
$primary: black;

.button {
  color: $primary;
}
```

### Tailwind CSS

```bash
npm install -D tailwindcss
```

```tsx
<button className="bg-black text-white px-4 py-2">Save</button>
```

| Utility       | Usage            |
| ------------- | ---------------- |
| `flex`        | Flexbox          |
| `grid`        | Grid layout      |
| `p-4`         | Padding          |
| `text-center` | Text alignment   |
| `bg-black`    | Background color |

### Styled Components

```bash
npm install styled-components
```

```tsx
"use client";

import styled from "styled-components";

const Button = styled.button`
  background: black;
  color: white;
`;
```

```tsx
<button className={isActive ? "active" : ""}>Click</button>
```

- Prefer CSS Modules or Tailwind
- Keep global CSS minimal
- Avoid deeply nested SCSS
- Reuse utility classes/components
- Keep styles component-based

```tsx
export default function Card() {
  return (
    <div className="p-4 rounded-lg shadow">
      <h2>Product Card</h2>
    </div>
  );
}
```

---

## 📌 Fonts & Images

Next.js provides built-in optimization for fonts and images using `next/font` and `next/image`.

| Feature            | Usage                         |
| ------------------ | ----------------------------- |
| `next/font`        | Optimized font loading        |
| `next/image`       | Optimized responsive images   |
| Lazy Loading       | Load images on demand         |
| Image Optimization | Resize/compress automatically |
| Local Fonts        | Self-host custom fonts        |
| Google Fonts       | Built-in Google font support  |

### Google Fonts

```tsx
import { Inter } from "next/font/google";

const inter = Inter({
  subsets: ["latin"],
});

export default function Layout({ children }) {
  return <body className={inter.className}>{children}</body>;
}
```

| Option     | Usage                 |
| ---------- | --------------------- |
| `subsets`  | Font language support |
| `weight`   | Font weight           |
| `variable` | CSS variable font     |

### Local Fonts

```txt
app/
├── fonts/
│   └── Geist-Regular.woff2
```

```tsx
import localFont from "next/font/local";

const geist = localFont({
  src: "./fonts/Geist-Regular.woff2",
  variable: "--font-geist",
});

export default function RootLayout({ children }) {
  return (
    <html lang="en">
      <body className={geist.className}>{children}</body>
    </html>
  );
}
```

### next/image

```txt
public/
├── images/
│   ├── products/
│   │   ├── shoe-1.jpg
│   │   └── shoe-2.jpg
│   ├── banners/
│   │   └── hero.jpg
│   ├── users/
│   │   └── avatar.png
│   └── icons/
│       └── cart.svg
```

- Automatic optimization
- Responsive images
- Lazy loading by default
- Keep images inside `public/images`
- Use lowercase filenames
- Prefer `.webp` or `.avif`
- Keep SVGs in separate folder

```tsx
import Image from "next/image";

<Image src="/product.jpg" alt="Product" />;
```

| Prop       | Usage                   |
| ---------- | ----------------------- |
| `src`      | Image path              |
| `alt`      | Accessibility text      |
| `width`    | Image width             |
| `height`   | Image height            |
| `fill`     | Fill parent container   |
| `priority` | Preload important image |

```tsx
// Responsive Image
<div className="relative h-64">
  <Image src="/banner.jpg" alt="Banner" fill className="object-cover" />
</div>
```

```js
// Remote Images

// next.config.js
module.exports = {
  images: {
    domains: ["images.unsplash.com"],
  },
};
```

- Prefer `next/image`
- Always add `alt`
- Use modern formats (`webp`, `avif`)
- Use `priority` for above-the-fold images
- Use `next/font` instead of external CDN fonts

```tsx
import Image from "next/image";

export default function ProductCard() {
  return (
    <div>
      <Image src="/shoe.jpg" alt="Shoe" width={400} height={300} />

      <h2>Running Shoe</h2>
    </div>
  );
}
```

---

## 📌 Metadata & SEO

Next.js provides built-in SEO support using the Metadata API for titles, descriptions, Open Graph tags, sitemaps, and robots configuration.

| Feature          | Usage                 |
| ---------------- | --------------------- |
| Metadata API     | SEO metadata          |
| Dynamic Metadata | Route-based SEO       |
| Open Graph       | Social sharing        |
| Twitter Cards    | Twitter preview       |
| Sitemap          | Search indexing       |
| robots.txt       | Crawler rules         |
| Canonical URL    | Prevent duplicate SEO |

### Basic Metadata

```tsx
// app/layout.tsx

export const metadata = {
  title: "My App",
  description: "Next.js application",
};
```

| Property       | Usage           |
| -------------- | --------------- |
| `title`        | Page title      |
| `description`  | SEO description |
| `keywords`     | Search keywords |
| `metadataBase` | Base URL        |
| `icons`        | Favicon/icons   |

### Dynamic Metadata

```tsx
// app/blog/[slug]/page.tsx

export async function generateMetadata({ params }) {
  return {
    title: params.slug,
  };
}
```

### Open Graph

```tsx
export const metadata = {
  openGraph: {
    title: "My App",
    description: "Next.js website",
    images: ["/banner.jpg"],
  },
};
```

### Twitter Cards

```tsx
export const metadata = {
  twitter: {
    card: "summary_large_image",
    title: "My App",
  },
};
```

### Canonical URL

```tsx
export const metadata = {
  alternates: {
    canonical: "https://example.com",
  },
};
```

### robots.txt

```txt
app/robots.ts
```

```txt
User-agent: *
Allow: /
```

### Sitemap

```tsx
// app/sitemap.ts

export default function sitemap() {
  return [
    {
      url: "https://example.com",
    },
  ];
}
```

- Add metadata for every page
- Use dynamic metadata for dynamic routes
- Add Open Graph images
- Use canonical URLs
- Keep titles/descriptions unique

```tsx
// app/products/[id]/page.tsx

export async function generateMetadata({ params }) {
  const product = await getProduct(params.id);

  return {
    title: product.title,
    description: product.description,
    openGraph: {
      images: [product.image],
    },
  };
}
```

---

## 📌 Performance Optimization

Next.js provides built-in optimization features for faster loading, smaller bundles, and better Core Web Vitals.

| Optimization       | Usage                       |
| ------------------ | --------------------------- |
| Code Splitting     | Load JS only when needed    |
| Dynamic Imports    | Lazy-load components        |
| Image Optimization | Optimized responsive images |
| Font Optimization  | Faster font loading         |
| Streaming          | Progressive rendering       |
| Caching            | Reduce server requests      |
| Prefetching        | Faster navigation           |
| Partial Hydration  | Smaller client JS           |

### Dynamic Imports

- Load components only when required
- Reduces initial bundle size

```tsx
import dynamic from "next/dynamic";

const Chart = dynamic(() => import("./Chart"), {
  ssr: false,
});
```

| Option       | Usage                 |
| ------------ | --------------------- |
| `ssr: false` | Client-only component |
| `loading`    | Custom loading UI     |

### Lazy Loading

```tsx
import { Suspense } from "react";

<Suspense fallback={<p>Loading...</p>}>
  <Posts />
</Suspense>;
```

### Image Optimization

```tsx
import Image from "next/image";

<Image src="/banner.jpg" alt="Banner" width={1200} height={500} priority />;
```

| Prop       | Usage                   |
| ---------- | ----------------------- |
| `priority` | Preload important image |
| `fill`     | Responsive image        |
| `sizes`    | Responsive sizing       |

### Font Optimization

```tsx
import { Inter } from "next/font/google";

const inter = Inter({
  subsets: ["latin"],
});
```

### Caching

| Cache Type    | Usage                 |
| ------------- | --------------------- |
| `force-cache` | Static cached data    |
| `no-store`    | Fresh data            |
| `revalidate`  | Periodic regeneration |

```tsx
await fetch("https://api.com/posts", {
  next: { revalidate: 60 },
});
```

### Prefetching

```tsx
import Link from "next/link";

<Link href="/products">Products</Link>;
```

- Routes auto-prefetch in viewport

### Streaming

```tsx
import { Suspense } from "react";

<Suspense fallback={<p>Loading...</p>}>
  <Products />
</Suspense>;
```

### Bundle Analysis

```bash
npm install @next/bundle-analyzer
```

- Use Server Components by default
- Use dynamic imports for heavy components
- Optimize images/fonts
- Avoid unnecessary client JS
- Fetch data on server when possible

```tsx
import dynamic from "next/dynamic";
import Image from "next/image";

const ProductChart = dynamic(() => import("@/components/ProductChart"), {
  ssr: false,
});

export default function ProductPage() {
  return (
    <main>
      <Image
        src="/images/products/shoe.jpg"
        alt="Shoe"
        width={500}
        height={300}
        priority
      />

      <ProductChart />
    </main>
  );
}
```

---

## 📌 Caching System

Next.js caching improves performance by storing data, routes, and server responses to reduce repeated rendering and requests.

| Cache Type          | Usage                     |
| ------------------- | ------------------------- |
| Request Memoization | Prevent duplicate fetches |
| Data Cache          | Cache fetched data        |
| Full Route Cache    | Cache rendered routes     |
| Router Cache        | Cache client navigation   |
| Revalidation        | Refresh stale cache       |
| Cache Tags          | Selective cache updates   |

### Request Memoization

- Same fetch request reused automatically
- Works in single request cycle

```tsx
await fetch("https://api.com/posts");
await fetch("https://api.com/posts");
```

### Data Cache

| Option        | Usage                  |
| ------------- | ---------------------- |
| `force-cache` | Static cached data     |
| `no-store`    | Always fresh data      |
| `revalidate`  | Periodic cache refresh |

```tsx
await fetch("https://api.com/posts", {
  cache: "force-cache",
});
```

```tsx
// Dynamic Fetching
await fetch("https://api.com/posts", {
  cache: "no-store",
});
```

```tsx
// Revalidation
export const revalidate = 60;
```

- Regenerates cache every 60 seconds

```tsx
// Fetch Revalidation
await fetch("https://api.com/posts", {
  next: { revalidate: 120 },
});
```

```tsx
// Cache Tags
await fetch("https://api.com/products", {
  next: {
    tags: ["products"],
  },
});
```

```tsx
// Revalidate Tags
import { revalidateTag } from "next/cache";

revalidateTag("products");
```

### Full Route Cache

- Caches rendered HTML/RSC payload
- Improves route performance

### Router Cache

- Client-side navigation cache
- Faster page transitions

### Best Practices

- Use `force-cache` for static data
- Use `no-store` for real-time data
- Use revalidation for hybrid content
- Use cache tags for selective updates
- Avoid unnecessary dynamic rendering

```tsx
export const revalidate = 300;

export default async function ProductsPage() {
  const res = await fetch("https://api.com/products", {
    next: {
      tags: ["products"],
    },
  });

  const products = await res.json();

  return (
    <main>
      {products.map((item) => (
        <h2 key={item.id}>{item.title}</h2>
      ))}
    </main>
  );
}
```

---

## 📌 Middleware

Middleware runs before a request is completed and is used for authentication, redirects, rewrites, headers, and request handling.

| Usage            | Purpose              |
| ---------------- | -------------------- |
| Authentication   | Protect routes       |
| Redirects        | Navigate users       |
| Rewrites         | Modify request paths |
| Headers          | Add custom headers   |
| Cookies          | Read/write cookies   |
| Geo/Locale Logic | Region-based routing |

### Middleware File

```txt
middleware.ts
```

- Placed in project root
- Runs before matching routes

### Basic Middleware

```tsx
// middleware.ts

import { NextResponse } from "next/server";

export function middleware() {
  return NextResponse.next();
}
```

| API                       | Usage            |
| ------------------------- | ---------------- |
| `NextResponse.next()`     | Continue request |
| `NextResponse.redirect()` | Redirect request |
| `NextResponse.rewrite()`  | Rewrite route    |

### Redirect Example

```tsx
import { NextResponse } from "next/server";

export function middleware(req) {
  const isLoggedIn = false;

  if (!isLoggedIn) {
    return NextResponse.redirect(new URL("/login", req.url));
  }

  return NextResponse.next();
}
```

### Matcher Config

```tsx
export const config = {
  matcher: ["/dashboard/:path*"],
};
```

| Matcher             | Usage                |
| ------------------- | -------------------- |
| `/dashboard/:path*` | Match nested routes  |
| `/admin/:path*`     | Protect admin routes |

### Access Request Data

```tsx
export function middleware(req) {
  const token = req.cookies.get("token");

  console.log(req.nextUrl.pathname);

  return NextResponse.next();
}
```

| Request API   | Usage           |
| ------------- | --------------- |
| `req.cookies` | Access cookies  |
| `req.headers` | Read headers    |
| `req.nextUrl` | Access URL info |

### Rewrite Example

```tsx
return NextResponse.rewrite(new URL("/new-route", req.url));
```

- Keep middleware lightweight
- Use matcher to limit execution
- Avoid heavy DB operations
- Use for auth/redirect logic only
- Prefer Edge-compatible code

```tsx
// middleware.ts

import { NextResponse } from "next/server";

export function middleware(req) {
  const token = req.cookies.get("token");

  if (!token) {
    return NextResponse.redirect(new URL("/login", req.url));
  }

  return NextResponse.next();
}

export const config = {
  matcher: ["/dashboard/:path*"],
};
```

---
