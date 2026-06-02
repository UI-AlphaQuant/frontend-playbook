# Next.js – Interview Q&A

## � BASIC

**Q:** What is Next.js?
**A:** React framework for production. Provides file-based routing, server-side rendering, static generation. Built on top of React. Simplifies complex configurations. Used for full-stack apps, better performance, SEO.

**Q:** What are the key features of Next.js?
**A:** File-based routing, API routes, SSR/SSG, ISR, middleware, image optimization, font optimization, built-in CSS support, TypeScript support, Vercel deployment.

**Q:** What is the App Router?
**A:** Modern routing system in Next.js 13+. Uses `app/` directory with file structure defining routes. Supports Server Components by default. Replaces Pages Router. Enables nested layouts, streaming.

**Q:** What is the Pages Router?
**A:** Legacy routing system using `pages/` directory. Each file becomes route. Uses `getStaticProps`, `getServerSideProps` for data fetching. Still supported but deprecated for new projects. Replaced by App Router.

**Q:** What is file-based routing?
**A:** Routes determined by file structure. `app/dashboard/page.tsx` becomes `/dashboard`. `app/products/[id]/page.tsx` becomes `/products/123`. Automatic routing without configuration.

**Q:** What is dynamic routing?
**A:** Routes with variable segments. Syntax: `[param]` creates dynamic route. Accessed via `params` object. Example: `app/products/[id]/page.tsx` → `params.id`. For variable URLs like product pages.

**Q:** What is optional catch-all routing?
**A:** `[[...slug]]` matches zero or more segments. Syntax: `app/docs/[[...slug]]` matches `/docs` and `/docs/a/b/c`. Single source for many routes. Useful for documentation sites.

**Q:** What is middleware in Next.js?
**A:** Code running between request and response. File: `middleware.ts`. Runs before route processing. Used for authentication, redirects, logging. Lightweight, runs on server.

**Q:** What are API routes?
**A:** Backend endpoints as files. Syntax: `app/api/users/route.ts` becomes `/api/users`. Export HTTP methods: `GET`, `POST`, `PUT`, `DELETE`. Build backend without separate server.

**Q:** What is Server Component?
**A:** React component running on server only. Default in App Router. Direct database access safe. Smaller client bundle. No hooks like `useState`. Send rendered HTML to client.

**Q:** What is Client Component?
**A:** Component running in browser. Marked with `"use client"`. Can use hooks (`useState`, `useEffect`), event listeners. Increases JavaScript bundle. Use only when needed (interactivity).

**Q:** What is the `use` hook?
**A:** Hook for unwrapping promises/async values in components. Syntax: `const data = use(promise)`. Used in Server Components returning promises. Enables async rendering.

**Q:** What is `useState` in Next.js?
**A:** React hook managing component state. Only works in Client Components (`"use client"`). Triggers re-render on state change. Example: `const [count, setCount] = useState(0)`.

**Q:** What is `useEffect` in Next.js?
**A:** React hook for side effects. Only in Client Components. Runs after render. Use for API calls, subscriptions. Cleanup function prevents memory leaks.

**Q:** What is environment variables?
**A:** Configuration values loaded from `.env.local`, `.env`. Prefix with `NEXT_PUBLIC_` to expose to frontend. Others server-only. Example: `NEXT_PUBLIC_API_URL`, `DATABASE_URL`.

---

## � INTERMEDIATE

**Q:** What is Server-Side Rendering (SSR)?
**A:** Rendering on server per request. HTML generated fresh every request. `export const dynamic = "force-dynamic"`. Slower than SSG. Better for dynamic content. Excellent SEO.

**Q:** What is Static Generation (SSG)?
**A:** Rendering at build time. HTML generated once, reused for all requests. Default in Next.js. Fastest performance. Best for static content. Use `revalidate` for ISR.

**Q:** What is Incremental Static Regeneration (ISR)?
**A:** Regenerate static pages in background. Syntax: `export const revalidate = 60;`. Stale-while-revalidate pattern. Fresh content every 60 seconds. Combines SSG speed with dynamic updates.

**Q:** What is the difference between SSR, SSG, and ISR?
**A:** SSR: fresh per request, slow, dynamic. SSG: build-time, fast, static. ISR: periodic regeneration, fast, updated regularly. Choose based on content type and freshness needs.

**Q:** What is streaming in Next.js?
**A:** Send HTML progressively as components render. Syntax: `<Suspense fallback={...}>`. Improves perceived performance. Browser starts rendering before complete. Better UX for slow networks.

**Q:** What is Suspense for data fetching?
**A:** Experimental feature for async operations. Component suspends during fetch. Shows fallback UI. Syntax: `<Suspense fallback={<Loading />}><Component /></Suspense>`. Cleaner than loading states.

**Q:** What is lazy loading in Next.js?
**A:** Load components on demand. `import dynamic from 'next/dynamic'`. Syntax: `const Component = dynamic(() => import('./Component'))`. Reduces initial bundle size.

**Q:** What is code splitting?
**A:** Automatic in Next.js. Each route gets separate bundle. Loaded on demand. Reduces initial load. Webpack handles splitting with dynamic imports.

**Q:** What is image optimization?
**A:** `next/image` optimizes automatically. Responsive images, WebP format, lazy loading. Improves performance significantly. Better than `<img>` tag.

**Q:** What is font optimization?
**A:** `next/font` automatically optimizes fonts. Downloads from Google, Typekit. Self-hosted, no external requests. Improves performance, prevents layout shift.

**Q:** What are route handlers?
**A:** Modern API routes in App Router. `app/api/users/route.ts` exports `GET`, `POST`. Full request/response control. Replace Pages Router `/api/` pattern.

**Q:** What is `getServerSideProps`?
**A:** Pages Router pattern. Runs on server per request. Return props to page. Deprecated in App Router. Replaced by Server Components. Rendered as SSR.

**Q:** What is `getStaticProps`?
**A:** Pages Router pattern. Runs at build time. Returns props to page. Deprecated in App Router. Replaced by direct fetching in Server Components with caching.

**Q:** What is `getStaticPaths`?
**A:** Pages Router pattern. Specifies dynamic routes to generate at build time. With `fallback: 'blocking'` generates on-demand. Deprecated in App Router.

**Q:** What is cache in Next.js?
**A:** `fetch()` cached by default. `cache: 'force-cache'` (default SSG), `'no-store'` (no cache), `revalidate: 3600` (ISR). Control data freshness.

**Q:** Real-life (Indian e-commerce): Render product list efficiently?
**A:** Use ISR: `revalidate: 300` (5 minutes). Product list cached, regenerated every 5 minutes. Fast, fresh content. Better than SSR for pricing/inventory updates.

**Q:** Real-life: Implement real-time notifications?
**A:** Use Client Component with `useEffect` polling. Or WebSocket for true real-time. API route handling notifications. Server-sent events (SSE) alternative.

---

## � ADVANCED

**Q:** Explain hydration in Next.js?
**A:** Server renders HTML. Browser downloads JavaScript. React attaches to HTML (hydration). Event listeners work. Makes static HTML interactive. Hydration mismatch = console warning.

**Q:** What is React Server Component?
**A:** Components running on server only. Default in `app/` directory. Don't use hooks, only direct DB access, async. Send serialized output to client. Reduce client JavaScript.

**Q:** What is the rendering hierarchy?
**A:** Request → Server renders layout + page components → Serializes output → Sends HTML/JSON to client → Browser hydrates → Interactive UI. Streaming progressively.

**Q:** What is middleware use cases?
**A:** Authentication (check token, redirect), redirects (old URLs), CORS headers, logging, analytics, request modification. Runs before route processing for all requests.

**Q:** What is `notFound()` and `redirect()`?
**A:** `notFound()` shows 404 page. `redirect()` navigates to URL. Used in Server Components. Throws special errors caught by Next.js.

**Q:** What are layout files?
**A:** Shared UI for group of routes. `app/layout.tsx` wraps all. `app/dashboard/layout.tsx` wraps dashboard routes. Nested layouts compose. Enable shared navigation, styling.

**Q:** What is `useRouter` hook?
**A:** Client-side navigation. Syntax: `router.push('/path')`, `router.back()`, `router.refresh()`. Only in Client Components. Programmatic navigation without page reload.

**Q:** What is `useSearchParams` and `usePathname`?
**A:** `useSearchParams`: access query parameters. `usePathname`: get current path. Only in Client Components. Useful for filters, tracking current page.

**Q:** What is script optimization?
**A:** `next/script` with `strategy` prop. `beforeInteractive`, `afterInteractive`, `lazyOnload`, `worker`. Control script loading timing. Improves performance.

**Q:** What is CSS-in-JS vs Tailwind in Next.js?
**A:** CSS-in-JS: styled-components, emotion. Per-component styles, dynamic styles, scoped CSS. Tailwind: utility-first, smaller bundle with PurgeCSS, faster development.

**Q:** What is `next.config.js`?
**A:** Configuration file for Next.js. Customize webpack, env vars, redirects, rewrites. Example: image optimization, compression, security headers.

**Q:** What is deployment on Vercel?
**A:** Official Next.js hosting. Git push triggers auto-deploy. Built-in analytics, preview deployments, edge functions. Zero-config for Next.js. Recommended platform.

**Q:** Real-life (Indian SaaS): Implement role-based access control?
**A:** Middleware checks user role. `redirect()` if unauthorized. Protected routes access-controlled. Server Components access DB for role verification. Role stored in JWT token.

**Q:** Real-life: Handle payment processing securely?
**A:** API route calls payment provider (Razorpay, Stripe). Never expose API keys in frontend. Frontend calls Next.js API. Server handles sensitive operations. Return safe response.

**Q:** Real-life: Implement real-time chat with database sync?
**A:** WebSocket for real-time messages (separate server or service). Next.js API routes manage history. Database stores messages. Client Component displays. Scales with proper infrastructure.

**Q:** Real-life: Optimize CMS-backed blog for SEO?
**A:** Use ISR: `revalidate: 3600` for blog posts. Server Component fetches from CMS. Generates static HTML. Metadata for SEO. Image optimization. Fast, searchable.

**Q:** Calculation: Blog with 10,000 posts. Build time with SSG = 100+ seconds. With ISR: initial build 100 popular posts (~1 sec), rest on-demand. Result: 100x faster builds, instant deploys.

**Q:** Calculation: API route receiving 1000 requests/sec. Without caching: 1000 DB queries. With cache `revalidate: 60`: 17 queries/min (60x less load). Saves cost, improves performance.

---

## 📋 Quick Reference

| Directory    | Purpose                       |
| ------------ | ----------------------------- |
| `app/`       | App Router, file-based routes |
| `app/api/`   | API routes                    |
| `public/`    | Static files                  |
| `.env.local` | Environment variables         |

| Pattern          | Use Case                              |
| ---------------- | ------------------------------------- |
| Server Component | Default, data fetching, DB access     |
| Client Component | Interactivity, hooks, event listeners |
| Middleware       | Auth checks, redirects                |
| API Route        | Backend endpoint                      |
| Route Handler    | App Router API (modern)               |

| Data Fetching | When                                 |
| ------------- | ------------------------------------ |
| SSG + ISR     | Static content with periodic updates |
| SSR           | Dynamic content per user             |
| CSR + API     | Highly interactive, user-specific    |
