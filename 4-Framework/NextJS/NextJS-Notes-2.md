# 👉 Advanced

## 📌 Deployment

Next.js applications can be deployed on platforms like Vercel, Netlify, Docker, VPS, or cloud providers.

| Deployment Type | Usage                      |
| --------------- | -------------------------- |
| Vercel          | Official Next.js hosting   |
| Netlify         | Frontend deployment        |
| Docker          | Containerized deployment   |
| VPS/Cloud       | Custom hosting             |
| Edge Deployment | Global low-latency runtime |

### Production Build

| Command         | Usage                   |
| --------------- | ----------------------- |
| `npm run build` | Create production build |
| `npm start`     | Start production server |

```bash
npm run build
npm start
```

### Environment Variables

```env
NEXT_PUBLIC_API_URL=https://api.com
DATABASE_URL=database_url
```

| Prefix         | Usage           |
| -------------- | --------------- |
| `NEXT_PUBLIC_` | Client + Server |
| No Prefix      | Server only     |

### Vercel Deployment

```bash
npm install -g vercel
vercel
```

| Feature               | Usage                  |
| --------------------- | ---------------------- |
| Automatic Deployments | Git-based deploy       |
| Preview Deployments   | Test branches          |
| Edge Functions        | Global execution       |
| Built-in Analytics    | Performance monitoring |

### Netlify Deployment

```bash
npm run build
```

| Setting           | Value           |
| ----------------- | --------------- |
| Build Command     | `npm run build` |
| Publish Directory | `.next`         |

### Docker Deployment

```dockerfile
FROM node:20

WORKDIR /app

COPY . .

RUN npm install
RUN npm run build

CMD ["npm", "start"]
```

### next.config.js

```js
module.exports = {
  reactStrictMode: true,
};
```

### Common Deployment Files

```txt
.next/
public/
.env.local
next.config.js
Dockerfile
```

- Use Vercel for easiest deployment
- Keep secrets in environment variables
- Optimize images/fonts before deploy
- Enable caching & compression
- Test production build locally

```bash
git init
git add .
git commit -m "Initial deploy"

vercel
```

---

## 📌 Edge Runtime

Edge Runtime runs code closer to users using global edge servers for lower latency and faster response times.

| Runtime  | Usage                  |
| -------- | ---------------------- |
| `nodejs` | Default server runtime |
| `edge`   | Fast global execution  |

### Enable Edge Runtime

```tsx
export const runtime = "edge";
```

### Supported Features

| Feature        | Edge Support |
| -------------- | ------------ |
| Route Handlers | ✅           |
| Middleware     | ✅           |
| Streaming      | ✅           |
| Fetch API      | ✅           |
| Web APIs       | ✅           |
| Node.js APIs   | ❌           |

### Edge Route Handler

```tsx
// app/api/users/route.ts

export const runtime = "edge";

export async function GET() {
  return Response.json({
    success: true,
  });
}
```

### Edge Middleware

```tsx
// middleware.ts

import { NextResponse } from "next/server";

export function middleware() {
  return NextResponse.next();
}
```

| Common Use Cases | Purpose                 |
| ---------------- | ----------------------- |
| Authentication   | Fast auth checks        |
| Redirects        | Geo-based redirects     |
| Middleware       | Request handling        |
| Personalization  | Region/user-specific UI |
| APIs             | Low-latency responses   |

| Limitation       | Notes                    |
| ---------------- | ------------------------ |
| No Node.js APIs  | `fs`, `crypto`, etc.     |
| Limited Packages | Node-dependent libs fail |
| Smaller Runtime  | Lightweight only         |

| Feature          | Node.js | Edge |
| ---------------- | ------- | ---- |
| Full Node APIs   | ✅      | ❌   |
| Global Execution | ❌      | ✅   |
| Lower Latency    | ⚠️      | ✅   |
| Heavy Processing | ✅      | ⚠️   |

- Use Edge for lightweight logic
- Avoid heavy server operations
- Use for middleware/auth APIs
- Keep edge functions fast
- Avoid unsupported Node packages

```tsx
// app/api/location/route.ts

export const runtime = "edge";

export async function GET(req: Request) {
  return Response.json({
    country: req.headers.get("x-vercel-ip-country"),
  });
}
```

---

## 📌 Monitoring & Debugging

Monitoring and debugging help identify rendering issues, performance bottlenecks, API failures, and production errors in Next.js apps.

| Tool/Feature   | Usage                      |
| -------------- | -------------------------- |
| Error Handling | Catch application errors   |
| Logging        | Debug server/client issues |
| Web Vitals     | Performance metrics        |
| Lighthouse     | SEO & performance audit    |
| DevTools       | Browser debugging          |
| Source Maps    | Better error tracing       |

### Error Handling

```tsx
// app/error.tsx

"use client";

export default function Error({ error, reset }) {
  return (
    <div>
      <p>{error.message}</p>

      <button onClick={reset}>Retry</button>
    </div>
  );
}
```

```tsx
// Logging
console.log("Debug log");
console.error("Error log");
```

| Log Type          | Usage             |
| ----------------- | ----------------- |
| `console.log()`   | General debugging |
| `console.error()` | Error debugging   |
| `console.table()` | Structured data   |

### Hydration Errors

| Cause                          | Fix                    |
| ------------------------------ | ---------------------- |
| Browser-only APIs on server    | Use Client Component   |
| Random values                  | Generate on client     |
| Different server/client output | Keep render consistent |

```tsx
"use client";

import { useEffect, useState } from "react";

export default function Time() {
  const [time, setTime] = useState("");

  useEffect(() => {
    setTime(new Date().toLocaleTimeString());
  }, []);

  return <p>{time}</p>;
}
```

```tsx
// API Error Handling
const res = await fetch("https://api.com");

if (!res.ok) {
  throw new Error("Failed request");
}
```

### Web Vitals

| Metric | Usage                    |
| ------ | ------------------------ |
| LCP    | Largest Contentful Paint |
| FID    | First Input Delay        |
| CLS    | Layout shift             |
| FCP    | First paint              |

### Lighthouse

```bash
npm run build
npm start
```

- Open Chrome DevTools
- Run Lighthouse audit

### next.config.js Debugging

```js
module.exports = {
  reactStrictMode: true,
};
```

| Common Issues      | Cause                    |
| ------------------ | ------------------------ |
| Hydration mismatch | Different render output  |
| Slow page load     | Large client bundle      |
| API errors         | Invalid response         |
| Layout shift       | Missing image dimensions |

- Use Error Boundaries
- Check production build locally
- Keep logs meaningful
- Optimize client bundle size
- Monitor Core Web Vitals

```tsx
export default async function ProductsPage() {
  try {
    const res = await fetch("https://api.com/products");

    if (!res.ok) {
      throw new Error("Failed");
    }

    const products = await res.json();

    return <div>{products.length}</div>;
  } catch (error) {
    return <p>Something went wrong</p>;
  }
}
```

---

## 📌 Advanced Routing

Advanced routing in Next.js App Router provides flexible layouts, parallel rendering, intercepting routes, and route-level rendering control.

| Feature             | Usage                            |
| ------------------- | -------------------------------- |
| Parallel Routes     | Multiple route views             |
| Intercepting Routes | Open route inside current layout |
| Route Groups        | Organize routes                  |
| Dynamic Segments    | Dynamic URLs                     |
| Catch-all Routes    | Match nested segments            |
| Route Config        | Control rendering behavior       |

### Parallel Routes

- Render multiple pages simultaneously
- Common in dashboards/modals

```txt
app/
├── dashboard/
│   ├── @analytics/
│   ├── @users/
│   └── page.tsx
```

```tsx
export default function Layout({ analytics, users }) {
  return (
    <>
      {analytics}
      {users}
    </>
  );
}
```

### Intercepting Routes

- Open route without leaving current page
- Common for modals

```txt
app/
├── feed/
├── photo/
│   └── [id]/
├── (.)photo/
│   └── [id]/
```

| Syntax  | Usage           |
| ------- | --------------- |
| `(.)`   | Same level      |
| `(..)`  | One level above |
| `(...)` | Root level      |

### Route Groups

```txt
app/
├── (marketing)/
├── (dashboard)/
```

- Organize routes
- Does not affect URL

### Dynamic Segments

```txt
app/blog/[slug]/page.tsx
```

```tsx
export default function Page({ params }) {
  return <h1>{params.slug}</h1>;
}
```

### Catch-all Routes

| Syntax        | Usage              |
| ------------- | ------------------ |
| `[...slug]`   | Catch all segments |
| `[[...slug]]` | Optional catch all |

```txt
/docs/react/hooks/useState
```

### Route Segment Config

```tsx
export const dynamic = "force-dynamic";

export const revalidate = 60;

export const runtime = "edge";
```

| Config       | Usage                     |
| ------------ | ------------------------- |
| `dynamic`    | Dynamic rendering control |
| `revalidate` | ISR interval              |
| `runtime`    | Node.js or Edge           |

- Use parallel routes for dashboards
- Use intercepting routes for modals
- Keep route structure organized
- Avoid deeply nested routes
- Use route groups for large apps

```txt
Dashboard
├── Analytics Panel
├── User Panel
├── Settings Modal
```

```tsx
export default function Dashboard({ analytics, users }) {
  return (
    <main>
      {analytics}
      {users}
    </main>
  );
}
```

---

## 📌 Advanced Data Handling

Advanced data handling in Next.js improves performance using caching, streaming, revalidation, and optimistic UI updates.

| Feature       | Usage                     |
| ------------- | ------------------------- |
| React Cache   | Prevent duplicate fetches |
| Server Cache  | Cache server responses    |
| Revalidation  | Refresh stale data        |
| Cache Tags    | Selective cache updates   |
| Streaming     | Progressive rendering     |
| Optimistic UI | Instant UI updates        |

### React Cache

- Cache async functions
- Avoid repeated requests

```tsx
import { cache } from "react";

export const getPosts = cache(async () => {
  const res = await fetch("https://api.com/posts");

  return res.json();
});
```

### Server Cache

```tsx
await fetch("https://api.com/posts", {
  cache: "force-cache",
});
```

| Cache Option  | Usage              |
| ------------- | ------------------ |
| `force-cache` | Static cached data |
| `no-store`    | Always fresh data  |
| `revalidate`  | Regenerate cache   |

### Revalidation

```tsx
export const revalidate = 60;
```

```tsx
await fetch("https://api.com/posts", {
  next: {
    revalidate: 60,
  },
});
```

### Cache Tags

```tsx
await fetch("https://api.com/products", {
  next: {
    tags: ["products"],
  },
});
```

### Revalidate Tags

```tsx
import { revalidateTag } from "next/cache";

revalidateTag("products");
```

### Streaming

```tsx
import { Suspense } from "react";

<Suspense fallback={<p>Loading...</p>}>
  <Products />
</Suspense>;
```

### Optimistic UI

- Update UI before server response
- Better user experience

```tsx
"use client";

import { useOptimistic } from "react";

const [items, addOptimistic] = useOptimistic(data);
```

### Server Action Mutation

```tsx
"use server";

import { revalidatePath } from "next/cache";

export async function createPost() {
  await db.post.create();

  revalidatePath("/posts");
}
```

- Cache static data aggressively
- Use `no-store` for live data
- Use cache tags for selective updates
- Use streaming for heavy pages
- Keep optimistic updates lightweight

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

## 📌 Next.js Internals

Next.js internally combines React Server Components, routing, caching, streaming, and hydration for optimized full-stack rendering.

| Internal Concept       | Usage                          |
| ---------------------- | ------------------------------ |
| Hydration              | Attach React to HTML           |
| Rendering Lifecycle    | Server → Client rendering flow |
| React Flight           | Server Component payload       |
| Streaming              | Send UI progressively          |
| Compiler Optimizations | Faster builds/runtime          |
| Bundling               | Split client/server code       |

### Rendering Flow

```txt
Request
   ↓
Server Rendering
   ↓
HTML Response
   ↓
Hydration
   ↓
Interactive UI
```

### Hydration

- React attaches event listeners to server HTML
- Makes UI interactive in browser

```tsx
"use client";

import { useState } from "react";

export default function Counter() {
  const [count, setCount] = useState(0);

  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
```

| Problem            | Cause                          |
| ------------------ | ------------------------------ |
| Hydration mismatch | Different server/client output |
| Large hydration    | Too many Client Components     |

### React Flight

- Special payload for Server Components
- Sends minimal component data to client
- Reduces JavaScript bundle size

```txt
Server Components
   ↓
React Flight Payload
   ↓
Client Rendering
```

### Streaming

- Send HTML in chunks
- Faster perceived loading

```tsx
import { Suspense } from "react";

<Suspense fallback={<p>Loading...</p>}>
  <Products />
</Suspense>;
```

### Compiler Optimizations

| Optimization   | Usage                     |
| -------------- | ------------------------- |
| Tree Shaking   | Remove unused code        |
| Code Splitting | Smaller bundles           |
| Fast Refresh   | Instant updates           |
| Turbopack      | Faster development builds |

### Server vs Client Bundle

| Bundle        | Contains                 |
| ------------- | ------------------------ |
| Server Bundle | Server Components & APIs |
| Client Bundle | Interactive UI code      |

### Rendering Types Internally

| Type | Internal Behavior          |
| ---- | -------------------------- |
| SSG  | Build-time HTML generation |
| SSR  | Per-request rendering      |
| ISR  | Cached regeneration        |
| CSR  | Browser rendering          |

- Prefer Server Components
- Keep client bundle small
- Avoid hydration mismatches
- Use streaming for large pages
- Avoid unnecessary `"use client"`

```tsx
// Server Component

import AddToCart from "./AddToCart";

export default async function ProductsPage() {
  const products = await getProducts();

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

## 📌 Internationalization (i18n)

Internationalization (i18n) enables multi-language routing, translations, and locale-based content in Next.js applications.

| Feature                     | Usage                  |
| --------------------------- | ---------------------- |
| Locale Routing              | Language-based routes  |
| Dynamic Translations        | Multi-language content |
| Language Switcher           | Change locale          |
| SEO Localization            | Locale-specific SEO    |
| Middleware Locale Detection | Auto language redirect |

### i18n Routing Structure

```txt
app/
├── [locale]/
│   ├── page.tsx
│   ├── about/
│   │   └── page.tsx
```

| Route | Usage   |
| ----- | ------- |
| `/en` | English |
| `/fr` | French  |
| `/hi` | Hindi   |

### Dynamic Locale Page

```tsx
// app/[locale]/page.tsx

export default function Home({ params }) {
  return <h1>{params.locale}</h1>;
}
```

### Translation Messages

```txt
messages/
├── en.json
├── fr.json
```

```json
{
  "title": "Welcome"
}
```

### Load Translations

```tsx
import messages from "@/messages/en.json";

<h1>{messages.title}</h1>;
```

### Language Switcher

```tsx
import Link from "next/link";

<Link href="/en">English</Link>
<Link href="/fr">French</Link>
```

### Middleware Locale Redirect

```tsx
// middleware.ts

import { NextResponse } from "next/server";

export function middleware(req) {
  return NextResponse.redirect(new URL("/en", req.url));
}
```

### SEO Localization

```tsx
export const metadata = {
  alternates: {
    languages: {
      en: "/en",
      fr: "/fr",
    },
  },
};
```

### Common Libraries

| Library        | Usage                  |
| -------------- | ---------------------- |
| `next-intl`    | Modern i18n            |
| `next-i18next` | Pages Router i18n      |
| `react-intl`   | Translation formatting |

- Keep translations separate
- Use locale-based routing
- Translate metadata/SEO
- Avoid hardcoded text
- Use middleware for locale redirects

```tsx
// app/[locale]/products/page.tsx

import messages from "@/messages/en.json";

export default function Products() {
  return (
    <main>
      <h1>{messages.title}</h1>
    </main>
  );
}
```

---

## 📌 Security

Next.js security focuses on protecting applications from XSS, CSRF, sensitive data exposure, insecure APIs, and unauthorized access.

| Security Area         | Usage                    |
| --------------------- | ------------------------ |
| XSS Protection        | Prevent script injection |
| CSRF Protection       | Secure form requests     |
| Secure Headers        | Improve browser security |
| Authentication        | Protect users/routes     |
| API Security          | Secure backend endpoints |
| Environment Variables | Protect secrets          |

### Environment Variables

```env
DATABASE_URL=secret
JWT_SECRET=my_secret
```

| Variable Type   | Usage                  |
| --------------- | ---------------------- |
| `NEXT_PUBLIC_*` | Public client variable |
| Without prefix  | Server-only secret     |

### Secure Headers

```js
// next.config.js

module.exports = {
  headers: async () => [
    {
      source: "/(.*)",
      headers: [
        {
          key: "X-Frame-Options",
          value: "DENY",
        },
      ],
    },
  ],
};
```

| Header                      | Usage                   |
| --------------------------- | ----------------------- |
| `X-Frame-Options`           | Prevent clickjacking    |
| `Content-Security-Policy`   | Restrict script sources |
| `Strict-Transport-Security` | Force HTTPS             |

### Authentication Middleware

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
```

### Secure API Route

```tsx
// app/api/users/route.ts

export async function GET(req: Request) {
  const token = req.headers.get("authorization");

  if (!token) {
    return Response.json({ error: "Unauthorized" }, { status: 401 });
  }

  return Response.json({ success: true });
}
```

### Input Validation

```tsx
if (!email.includes("@")) {
  throw new Error("Invalid email");
}
```

### Cookies

```tsx
cookies().set("token", value, {
  httpOnly: true,
  secure: true,
});
```

| Option     | Usage             |
| ---------- | ----------------- |
| `httpOnly` | Prevent JS access |
| `secure`   | HTTPS only        |
| `sameSite` | CSRF protection   |

### Common Security Risks

| Risk                | Prevention                |
| ------------------- | ------------------------- |
| XSS                 | Escape user input         |
| CSRF                | Use secure cookies/tokens |
| Secret Leakage      | Use server env variables  |
| Unauthorized Access | Middleware/auth checks    |

- Keep secrets server-side
- Validate all inputs
- Use HTTPS only
- Protect routes with middleware
- Avoid exposing sensitive APIs

```tsx
// app/api/admin/route.ts

export async function GET(req: Request) {
  const token = req.headers.get("authorization");

  if (token !== process.env.ADMIN_TOKEN) {
    return Response.json({ error: "Forbidden" }, { status: 403 });
  }

  return Response.json({
    success: true,
  });
}
```

---

## 📌 Best Practices

Best practices improve scalability, performance, maintainability, SEO, and developer experience in Next.js applications.

| Practice               | Usage                    |
| ---------------------- | ------------------------ |
| Server-first Approach  | Better performance & SEO |
| Component Organization | Cleaner structure        |
| Code Splitting         | Smaller bundles          |
| SEO Optimization       | Better indexing          |
| Accessibility          | Better UX                |
| Error Handling         | Stable applications      |
| Environment Separation | Secure configs           |

### Folder Structure

```txt
src/
├── app/
│   ├── layout.tsx
│   ├── page.tsx
│   ├── globals.css
│   ├── loading.tsx
│   ├── error.tsx
│   ├── not-found.tsx
│   ├── api/
│   ├── dashboard/
│   └── products/
│
├── components/
│   ├── ui/
│   ├── forms/
│   ├── layout/
│   ├── cards/
│   └── shared/
│
├── lib/
│   ├── db.ts
│   ├── auth.ts
│   ├── utils.ts
│   └── validations.ts
│
├── services/
│   ├── product.service.ts
│   ├── auth.service.ts
│   └── user.service.ts
│
├── hooks/
│   ├── useAuth.ts
│   ├── useDebounce.ts
│   └── useTheme.ts
│
├── types/
│   ├── product.ts
│   ├── user.ts
│   └── api.ts
│
├── store/
│   ├── auth.store.ts
│   └── cart.store.ts
│
├── styles/
│   ├── globals.css
│   └── variables.css
│
├── public/
│   ├── images/
│   ├── icons/
│   ├── fonts/
│   └── favicon.ico
│
├── middleware.ts
├── next.config.js
├── tsconfig.json
├── package.json
└── .env.local
```

| Folder        | Usage              |
| ------------- | ------------------ |
| `components/` | Reusable UI        |
| `lib/`        | Utilities/helpers  |
| `services/`   | API/business logic |
| `hooks/`      | Custom hooks       |
| `types/`      | TypeScript types   |

### Server-first Approach

- Prefer Server Components
- Fetch data on server
- Minimize client bundle

```tsx
export default async function Page() {
  const data = await fetchData();

  return <div>{data.title}</div>;
}
```

### Component Best Practices

| Practice                | Usage              |
| ----------------------- | ------------------ |
| Small Components        | Easier maintenance |
| Reusable UI             | Avoid duplication  |
| Feature-based structure | Better scalability |
| Shared layouts          | Consistent UI      |

### Performance Practices

| Optimization    | Usage              |
| --------------- | ------------------ |
| `next/image`    | Optimized images   |
| `next/font`     | Optimized fonts    |
| Dynamic imports | Lazy-load heavy UI |
| Streaming       | Faster rendering   |

```tsx
import dynamic from "next/dynamic";

const Chart = dynamic(() => import("./Chart"));
```

### SEO Practices

```tsx
export const metadata = {
  title: "Products",
  description: "Product listing",
};
```

| SEO Practice      | Usage           |
| ----------------- | --------------- |
| Unique titles     | Better ranking  |
| Meta descriptions | Search preview  |
| Open Graph        | Social sharing  |
| Sitemap           | Search indexing |

### Environment Variables

```env
DATABASE_URL=secret
NEXT_PUBLIC_API_URL=https://api.com
```

### Accessibility

| Practice            | Usage                 |
| ------------------- | --------------------- |
| `alt` text          | Accessible images     |
| Semantic HTML       | Better screen readers |
| Keyboard navigation | Accessibility support |

### Error Handling

```tsx
if (!res.ok) {
  throw new Error("Failed request");
}
```

- Prefer App Router
- Keep client components minimal
- Use TypeScript
- Use server-side fetching
- Keep APIs secure
- Optimize assets/images/fonts
- Use modular architecture

```tsx
import Image from "next/image";

export default async function ProductsPage() {
  const products = await getProducts();

  return (
    <main>
      {products.map((item) => (
        <article key={item.id}>
          <Image src={item.image} alt={item.title} width={400} height={300} />

          <h2>{item.title}</h2>
        </article>
      ))}
    </main>
  );
}
```

---

## 📌 Scalability & Maintainability

Scalability and maintainability help keep large Next.js applications organized, reusable, performant, and easier to manage long-term.

| Practice                   | Usage               |
| -------------------------- | ------------------- |
| Modular Structure          | Easier scaling      |
| Reusable Components        | Reduce duplication  |
| Feature-based Architecture | Better organization |
| Utility Separation         | Cleaner code        |
| Type-safe APIs             | Safer development   |
| Shared Configs             | Consistent setup    |

### Feature-based Structure

```txt
src/
├── features/
│   ├── auth/
│   ├── products/
│   ├── cart/
│   └── dashboard/
```

| Feature Folder | Contains           |
| -------------- | ------------------ |
| `components/`  | Feature UI         |
| `services/`    | API/business logic |
| `hooks/`       | Feature hooks      |
| `types/`       | Feature types      |

### Reusable Components

```txt
components/
├── ui/
├── forms/
├── layout/
└── shared/
```

```tsx
export default function Button({ children }) {
  return <button className="btn">{children}</button>;
}
```

### Utility Separation

```txt
lib/
├── utils.ts
├── auth.ts
├── db.ts
└── validations.ts
```

| File             | Usage           |
| ---------------- | --------------- |
| `utils.ts`       | Common helpers  |
| `auth.ts`        | Auth logic      |
| `db.ts`          | Database config |
| `validations.ts` | Form validation |

### Type-safe APIs

```tsx
type Product = {
  id: number;
  title: string;
};
```

```tsx
async function getProducts(): Promise<Product[]> {
  return fetchProducts();
}
```

### Shared Configs

```txt
config/
├── site.ts
├── api.ts
└── constants.ts
```

### Environment Separation

```env
.env.local
.env.production
.env.development
```

### State Management Structure

```txt
store/
├── auth.store.ts
├── cart.store.ts
└── theme.store.ts
```

### Code Organization

| Practice         | Usage              |
| ---------------- | ------------------ |
| Small Components | Easier maintenance |
| Shared Hooks     | Reusable logic     |
| Centralized APIs | Cleaner data flow  |
| Aliases          | Cleaner imports    |

```json
{
  "paths": {
    "@/*": ["./src/*"]
  }
}
```

- Use feature-based architecture
- Keep components reusable
- Separate business logic from UI
- Centralize configs/constants
- Use TypeScript everywhere
- Avoid deeply nested folders
- Keep imports clean with aliases

```txt
src/
├── features/
│   └── products/
│       ├── components/
│       ├── services/
│       ├── hooks/
│       └── types/
```

```tsx
import ProductCard from "@/features/products/components/ProductCard";
import { getProducts } from "@/features/products/services/product.service";

export default async function ProductsPage() {
  const products = await getProducts();

  return (
    <main>
      {products.map((item) => (
        <ProductCard key={item.id} product={item} />
      ))}
    </main>
  );
}
```

---

## 📌 Deprecated / Avoid Patterns

Avoid outdated or inefficient patterns that increase bundle size, reduce performance, or make Next.js apps harder to maintain.

| Avoid Pattern                    | Why Avoid              |
| -------------------------------- | ---------------------- |
| Overusing Client Components      | Larger JS bundles      |
| Unnecessary `useEffect` Fetching | Poor performance       |
| Deep Prop Drilling               | Hard maintenance       |
| Large Global State               | Unnecessary re-renders |
| Mixing Server/Client Logic       | Hydration issues       |
| Heavy Middleware Logic           | Slower requests        |
| Unoptimized Images               | Poor performance       |
| Pages Router for New Apps        | App Router preferred   |

### Avoid Unnecessary Client Components

❌ Avoid:

```tsx
"use client";

export default function Page() {
  return <h1>Static Content</h1>;
}
```

✅ Prefer Server Components:

```tsx
export default function Page() {
  return <h1>Static Content</h1>;
}
```

### Avoid Fetching in useEffect

❌ Avoid:

```tsx
"use client";

useEffect(() => {
  fetch("/api/posts");
}, []);
```

✅ Prefer Server Fetching:

```tsx
export default async function Page() {
  const res = await fetch("https://api.com/posts");

  return <div />;
}
```

### Avoid Deep Prop Drilling

❌ Avoid:

```tsx
<App user={user} />
```

Passing through many nested components.

✅ Prefer:

- Context API
- Zustand
- Shared hooks

### Avoid Large Global State

❌ Avoid storing everything globally.

✅ Keep state:

- Local when possible
- Server-side when possible
- Minimal global state

### Avoid Heavy Middleware

❌ Avoid:

- Database queries
- Large computations
- Heavy business logic

✅ Use middleware only for:

- Auth checks
- Redirects
- Headers

### Avoid Unoptimized Images

❌ Avoid:

```tsx
<img src="/banner.jpg" />
```

✅ Prefer:

```tsx
import Image from "next/image";
```

### Avoid Hardcoded Configs

❌ Avoid:

```tsx
const API = "https://api.com";
```

✅ Prefer:

```env
NEXT_PUBLIC_API_URL=https://api.com
```

### Avoid Mixed Rendering Logic

❌ Avoid:

- Browser APIs in Server Components
- Server-only logic in Client Components

### Deprecated / Less Preferred

| Deprecated           | Preferred         |
| -------------------- | ----------------- |
| Pages Router         | App Router        |
| `getServerSideProps` | Server Components |
| `getStaticProps`     | Fetch caching     |
| Client-heavy apps    | Server-first apps |

- Prefer Server Components
- Fetch data on server
- Keep client bundle minimal
- Use modular architecture
- Optimize assets/images/fonts
- Avoid unnecessary global state

❌ Old Pattern:

```tsx
"use client";

useEffect(() => {
  fetch("/api/products");
}, []);
```

✅ Modern Next.js Pattern:

```tsx
export default async function ProductsPage() {
  const res = await fetch("https://api.com/products");

  const products = await res.json();

  return <div>{products.length}</div>;
}
```

---

## 📌 Testing

Testing ensures Next.js applications work correctly across components, APIs, pages, and user interactions.

| Testing Type        | Usage                                |
| ------------------- | ------------------------------------ |
| Unit Testing        | Test individual functions/components |
| Integration Testing | Test connected features              |
| E2E Testing         | Test complete user flow              |
| API Testing         | Test route handlers/APIs             |
| UI Testing          | Test rendered UI                     |

### Common Testing Tools

| Tool                  | Usage             |
| --------------------- | ----------------- |
| Jest                  | Unit testing      |
| React Testing Library | Component testing |
| Playwright            | E2E testing       |
| Cypress               | Browser testing   |
| MSW                   | Mock API requests |

### Install Testing Tools

```bash
npm install -D jest jest-environment-jsdom
npm install -D @testing-library/react
npm install -D @testing-library/jest-dom
```

### Jest Config

```js
// jest.config.js

module.exports = {
  testEnvironment: "jsdom",
};
```

### Component Testing

```tsx
// Button.test.tsx

import { render, screen } from "@testing-library/react";
import Button from "./Button";

test("renders button", () => {
  render(<Button>Save</Button>);

  expect(screen.getByText("Save")).toBeInTheDocument();
});
```

### API Route Testing

```tsx
import { GET } from "./route";

test("returns users", async () => {
  const res = await GET();

  expect(res.status).toBe(200);
});
```

### Playwright E2E

```bash
npm init playwright@latest
```

```tsx
import { test, expect } from "@playwright/test";

test("homepage", async ({ page }) => {
  await page.goto("/");

  await expect(page.getByText("Home")).toBeVisible();
});
```

### Mock API Requests

```tsx
global.fetch = jest.fn(() =>
  Promise.resolve({
    json: () => Promise.resolve([]),
  }),
);
```

### Testing Best Practices

| Practice                     | Usage                  |
| ---------------------------- | ---------------------- |
| Test user behavior           | Better reliability     |
| Keep tests isolated          | Easier debugging       |
| Mock external APIs           | Stable tests           |
| Avoid implementation details | Better maintainability |

### Folder Structure

```txt
src/
├── __tests__/
├── e2e/
├── components/
└── app/
```

- Test critical business flows
- Prefer behavior testing
- Keep tests simple
- Mock APIs/services
- Use E2E for important journeys

```tsx
// ProductCard.test.tsx

import { render, screen } from "@testing-library/react";
import ProductCard from "./ProductCard";

test("shows product title", () => {
  render(<ProductCard product={{ title: "Shoe" }} />);

  expect(screen.getByText("Shoe")).toBeInTheDocument();
});
```

---

## 📌 Version & Migration

Next.js versions introduce new features, routing systems, rendering improvements, and migration paths for modern development.

| Version Feature   | Usage                   |
| ----------------- | ----------------------- |
| Pages Router      | Legacy routing system   |
| App Router        | Modern routing system   |
| Server Components | Server-first rendering  |
| Server Actions    | Direct server mutations |
| Turbopack         | Faster dev bundler      |
| Streaming         | Progressive rendering   |

### Pages Router vs App Router

| Pages Router         | App Router        |
| -------------------- | ----------------- |
| `pages/` directory   | `app/` directory  |
| `getServerSideProps` | Server Components |
| `getStaticProps`     | Fetch caching     |
| Client-heavy apps    | Server-first apps |
| Limited layouts      | Nested layouts    |

### App Router Structure

```txt
app/
├── layout.tsx
├── page.tsx
├── loading.tsx
├── error.tsx
└── api/
```

### Migration Steps

| Step                      | Usage                 |
| ------------------------- | --------------------- |
| Create `app/` folder      | Enable App Router     |
| Move pages gradually      | Incremental migration |
| Replace old data fetching | Use server fetch      |
| Convert layouts           | Use `layout.tsx`      |
| Replace API patterns      | Use Route Handlers    |

### Old vs New Fetching

❌ Pages Router:

```tsx
export async function getServerSideProps() {
  return {
    props: {},
  };
}
```

✅ App Router:

```tsx
export default async function Page() {
  const res = await fetch("https://api.com");

  return <div />;
}
```

### Layout Migration

❌ Old Pattern:

```tsx
// pages/_app.tsx
```

✅ New Pattern:

```tsx
// app/layout.tsx
```

### Metadata Migration

❌ Old Pattern:

```tsx
import Head from "next/head";
```

✅ New Pattern:

```tsx
export const metadata = {
  title: "My App",
};
```

### Common Migration Changes

| Old              | New            |
| ---------------- | -------------- |
| `_app.tsx`       | `layout.tsx`   |
| `_document.tsx`  | Root layout    |
| `next/head`      | Metadata API   |
| API Routes       | Route Handlers |
| `getStaticProps` | Cached fetch   |

| Breaking Changes          | Notes                  |
| ------------------------- | ---------------------- |
| Server Components default | App Router behavior    |
| Async layouts/pages       | Supported              |
| Different routing system  | File structure changed |
| New caching system        | Fetch-based caching    |

- Prefer App Router for new apps
- Migrate gradually
- Use Server Components by default
- Replace old data fetching APIs
- Test routes after migration

```txt
Old Project
├── pages/
├── _app.tsx
└── api/

Modern Project
├── app/
├── layout.tsx
├── route.ts
└── Server Components
```

---
