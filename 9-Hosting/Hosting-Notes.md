## 📌 Static Frontend Without Backend on Shared Hosting

- Build a frontend application that:
  - Has good SEO
  - Requires no backend
  - Requires no database
  - Can be hosted on cheap shared hosting
  - Uses static JSON as API data
  - Has low maintenance cost
- Ideal for:
  - Portfolio Website
  - Agency Website
  - Company Website
  - Documentation Website
  - Product Showcase
  - Personal Branding Website

### Next.js Static Export

```txt
Next.js
    ↓
Static Export
    ↓
Shared Hosting
```

```js
// next.config.js
/** @type {import('next').NextConfig} */
const nextConfig = {
  output: "export",
};

module.exports = nextConfig;
```

### Project Structure:

```txt
src/
├── app/
│   ├── page.tsx
│   ├── about/page.tsx
│   ├── projects/page.tsx
│   └── contact/page.tsx

public/
├── api/
│   ├── projects.json
│   ├── blogs.json
│   ├── services.json
│   └── skills.json


https://domain.com/api/projects.json
```

```bash
npm run build
```

```txt
out/
├── index.html
├── about.html
├── assets/
```

### SEO Features

```tsx
// Metadata & Open Graph
export const metadata = {
  title: "My Portfolio",
  description: "Full Stack Developer",
  openGraph: {
    title: "My Portfolio",
    description: "Full Stack Developer",
    images: ["/og-image.jpg"],
  },
};
```

### Sitemap & Robots

```txt
public/
└── sitemap.xml
└── robots.txt
```

```tsx
// Structured Data
<script
  type="application/ld+json"
  dangerouslySetInnerHTML={{
    __html: JSON.stringify(schema),
  }}
/>
```

---
