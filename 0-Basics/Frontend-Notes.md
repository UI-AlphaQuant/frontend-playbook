## 📌 Frontend Architecture

- Micro Frontend means breaking one large frontend app into smaller independent frontend apps.
- Instead of one huge frontend codebase, different sections are built separately.

| Architecture        | Simple Meaning               | Best For              |
| ------------------- | ---------------------------- | --------------------- |
| Monolithic Frontend | One big frontend app         | Small/medium apps     |
| Micro Frontend      | Multiple small frontend apps | Large enterprise apps |

| Comparison       | Monolithic App       | Micro Frontend               |
| ---------------- | -------------------- | ---------------------------- |
| Codebase         | Single               | Multiple                     |
| Deployment       | Entire app deploy    | Independent deploy           |
| Team Structure   | One frontend team    | Multiple teams               |
| Scalability      | Harder in large apps | Better for huge systems      |
| Tech Flexibility | Usually single stack | Multiple frameworks possible |
| Maintenance      | Harder as app grows  | Modular ownership            |

### Real-Life Analogy

```txt
Monolithic Frontend
→ One huge shopping mall managed by one team

Micro Frontend
→ Different shops managed independently
```

| Real-World Example | Separate Frontend Modules |
| ------------------ | ------------------------- |
| E-commerce         | Cart, Payment, Orders     |
| Banking App        | Loans, Accounts, Payments |
| SaaS Dashboard     | Analytics, Billing, Users |
| Enterprise Portal  | HR, Payroll, Reports      |

| Common Tech       | Usage                    |
| ----------------- | ------------------------ |
| React             | Individual frontend apps |
| Module Federation | Share frontend modules   |
| Single SPA        | Micro frontend framework |
| Nx / Turborepo    | Monorepo management      |

---

## 📌 Frontend Libraries vs Frameworks

Frontend libraries and frameworks help build modern web applications faster and more efficiently.

| Type      | Tool      | Purpose                        | Best For                 |
| --------- | --------- | ------------------------------ | ------------------------ |
| Library   | React     | UI component library           | SPA & scalable UI        |
| Framework | Next.js   | Full-stack React framework     | SSR/production apps      |
| Framework | Angular   | Complete frontend framework    | Enterprise apps          |
| Framework | Vue       | Progressive frontend framework | Beginner + scalable apps |
| Library   | Preact    | Lightweight React alternative  | Small fast apps          |
| Library   | jQuery    | DOM manipulation               | Legacy projects          |
| Framework | SvelteKit | Svelte full-stack framework    | Fast modern apps         |
| Library   | SolidJS   | Reactive UI library            | High-performance apps    |
| Framework | Nuxt.js   | Vue full-stack framework       | Vue SSR apps             |

| Comparison     | Library                      | Framework                    |
| -------------- | ---------------------------- | ---------------------------- |
| Scope          | Specific functionality       | Complete app structure       |
| Control        | Developer controls structure | Framework controls structure |
| Flexibility    | More flexible                | More opinionated             |
| Learning Curve | Usually easier               | Usually larger               |
| Example        | React                        | Angular / Next.js            |

| Technology | Strengths                  | Weakness                     |
| ---------- | -------------------------- | ---------------------------- |
| React      | Huge ecosystem/flexibility | Needs extra libraries        |
| Next.js    | SSR/full-stack/performance | More complexity              |
| Angular    | Enterprise-ready           | Heavy learning curve         |
| Vue        | Easy + scalable            | Smaller ecosystem than React |
| Svelte     | Very fast/lightweight      | Smaller community            |

```txt
Library → You build app structure yourself
Framework → Structure and rules already provided
```

---

## 📌 Frontend vs Backend Developer

- Frontend developers build user interfaces and user experience.
- Backend developers build server logic, APIs, databases, and system architecture.

| Area              | Frontend Developer                 | Backend Developer                  |
| ----------------- | ---------------------------------- | ---------------------------------- |
| Main Focus        | UI/UX                              | Server & business logic            |
| Works On          | Browser/client side                | Server/database side               |
| Technologies      | React, Vue, CSS, JS                | Node.js, Java, Python, PHP         |
| Builds            | Pages, components, interactions    | APIs, authentication, databases    |
| Handles           | UI state, rendering, accessibility | Data processing, security, scaling |
| User Interaction  | Directly visible to users          | Mostly invisible to users          |
| Performance Focus | Rendering/UI speed                 | API/database/server speed          |
| Debugging         | UI/layout/browser issues           | Server/API/database issues         |
| Deployment        | Frontend hosting/CDN               | Servers/cloud/infrastructure       |

### Senior Developer Responsibilities

| Frontend                 | Real-World Work                    |
| ------------------------ | ---------------------------------- |
| Architecture Planning    | Component/system design            |
| UI Scalability           | Design systems/reusable components |
| Performance Optimization | Memoization/lazy loading           |
| Accessibility            | a11y standards                     |
| State Management         | Redux/Zustand architecture         |
| API Integration          | Backend communication              |
| Code Reviews             | Maintain code quality              |
| Mentorship               | Guide junior developers            |
| CI/CD & Deployment       | Frontend pipelines                 |
| Cross-team Collaboration | Design/backend/product sync        |

| Backend                  | Real-World Work                   |
| ------------------------ | --------------------------------- |
| API Architecture         | REST/GraphQL systems              |
| Database Design          | SQL/NoSQL architecture            |
| Authentication/Security  | JWT/OAuth/permissions             |
| Scalability              | High traffic systems              |
| Performance Optimization | Query optimization/caching        |
| Server Infrastructure    | Cloud/server management           |
| System Design            | Microservices/distributed systems |
| CI/CD Pipelines          | Automated deployments             |
| Monitoring & Logging     | Error tracking/analytics          |
| Mentorship               | Technical leadership              |

---

## 📌 HTML Parsing

HTML Parsing is the browser process of reading HTML markup and converting it into a DOM tree that JavaScript and the rendering engine can use to display and interact with a webpage.

### Browser Rendering Flow

```txt
Request HTML
      ↓
Download HTML
      ↓
Parse HTML
      ↓
Create DOM Tree
      ↓
Download CSS
      ↓
Create CSSOM
      ↓
Combine DOM + CSSOM
      ↓
Render Tree
      ↓
Layout
      ↓
Paint
      ↓
Display on Screen
```

### Why Parsing Can Stop?

Normal HTML parsing is continuous, But JavaScript can block it.

```html
<script src="app.js"></script>
```

```txt
Parse HTML
     ↓
Found Script
     ↓
Stop Parsing
     ↓
Download JS
     ↓
Execute JS
     ↓
Resume Parsing
```

### async vs defer

#### async

```html
<script async src="app.js"></script>
```

```txt
Parse HTML
     ↓
Download JS Parallel
     ↓
Execute Immediately
     ↓
Continue Parsing
```

#### defer

```html
<script defer src="app.js"></script>
```

```txt
Parse HTML
     ↓
Download JS Parallel
     ↓
Finish Parsing
     ↓
Execute JS
```

### Understanding parsing helps

- Faster page loads
- Better performance
- Script loading optimization
- Render blocking issues
- DOM manipulation

---
