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

## 📌 Frontend Business Logic

- Frontend Business Logic & Responsibilities

| Use Case                      | Complexity |
| ----------------------------- | ---------- |
| Required Field Validation     | Easy       |
| Email Format Validation       | Easy       |
| Phone Format Validation       | Easy       |
| Password Length Validation    | Easy       |
| Confirm Password Match        | Easy       |
| Character Limits              | Easy       |
| File Size Validation          | Easy       |
| File Type Validation          | Easy       |
| Disable Submit Button         | Easy       |
| Show Loading State            | Easy       |
| Success/Error Messages        | Easy       |
| Input Formatting              | Easy       |
| Date Formatting               | Easy       |
| Number Formatting             | Easy       |
| Conditional Rendering         | Easy       |
| Show/Hide Fields              | Easy       |
| Search UI                     | Easy       |
| Table Filters                 | Easy       |
| Pagination UI                 | Easy       |
| File Preview                  | Easy       |
| Theme Switching               | Easy       |
| Language Switching            | Easy       |
| Route Protection UI           | Medium     |
| Role-Based UI Visibility      | Medium     |
| Authentication UI Flow        | Medium     |
| Refresh Token Handling        | Medium     |
| Notification Display          | Medium     |
| Local Cache Management        | Medium     |
| Form State Management         | Medium     |
| Table Sorting                 | Medium     |
| Infinite Scroll               | Medium     |
| Debounce Search               | Medium     |
| Drag & Drop UI                | Medium     |
| API Integration               | Medium     |
| WebSocket Connection Handling | Hard       |
| Optimistic Updates            | Hard       |
| Complex Dynamic Forms         | Hard       |
| Dashboard Charts Rendering    | Hard       |
| Real-Time UI Synchronization  | Hard       |

- Backend Business Logic & Responsibilities

| Use Case                     | Complexity |
| ---------------------------- | ---------- |
| OTP Generation               | Easy       |
| Email Verification           | Easy       |
| Session Management           | Easy       |
| JWT Generation               | Medium     |
| User Authentication          | Medium     |
| Authorization Enforcement    | Medium     |
| Permission Enforcement       | Medium     |
| Duplicate Record Check       | Medium     |
| Email Uniqueness Check       | Medium     |
| File Storage Management      | Medium     |
| Dashboard Aggregation        | Medium     |
| Report Generation            | Medium     |
| Export File Generation       | Medium     |
| Notification Generation      | Medium     |
| Webhook Processing           | Medium     |
| Database Operations          | Medium     |
| Query Optimization           | Hard       |
| Database Transactions        | Hard       |
| Business Rule Validation     | Hard       |
| Inventory Validation         | Hard       |
| Stock Validation             | Hard       |
| Order Creation Rules         | Hard       |
| Cart Calculation             | Hard       |
| Shipping Calculation         | Hard       |
| Pricing Logic                | Hard       |
| Discount Engine              | Hard       |
| Tax Calculation              | Hard       |
| Revenue Calculation          | Hard       |
| Salary Calculation           | Hard       |
| Commission Calculation       | Hard       |
| Payment Processing           | Hard       |
| Refund Processing            | Hard       |
| Subscription Management      | Hard       |
| Security Rules               | Hard       |
| API Security                 | Hard       |
| Encryption                   | Hard       |
| Rate Limiting                | Hard       |
| Caching Strategy             | Hard       |
| Queue Processing             | Hard       |
| Background Jobs              | Hard       |
| Analytics Calculations       | Hard       |
| Audit Logs                   | Hard       |
| Real-Time Event Broadcasting | Hard       |
| Third-Party Integrations     | Hard       |

- Quick Rule

| Category                | Owner    |
| ----------------------- | -------- |
| UI Rendering            | Frontend |
| Forms & Validation      | Frontend |
| State Management        | Frontend |
| API Consumption         | Frontend |
| Data Formatting         | Frontend |
| Business Rules          | Backend  |
| Database                | Backend  |
| Security                | Backend  |
| Authentication          | Backend  |
| Financial Logic         | Backend  |
| Permissions Enforcement | Backend  |
| Data Integrity          | Backend  |

---

## 📌 Major Frontend Framework Versions

- React

| Framework | Version | Year  | Major Update                                         |
| --------- | ------- | ----- | ---------------------------------------------------- |
| React     | 16      | 2017  | Fiber Architecture, Error Boundaries, Portals        |
| React     | 16.8    | 2019  | Hooks (`useState`, `useEffect`, etc.) ⭐             |
| React     | 17      | 2020  | New JSX Transform, Easier Upgrades                   |
| React     | 18      | 2022  | Concurrent Rendering, Automatic Batching ⭐          |
| React     | 19      | 2024+ | Actions, `use()`, Metadata APIs, RSC Improvements ⭐ |

- Vue

| Framework | Version | Year  | Major Update                                  |
| --------- | ------- | ----- | --------------------------------------------- |
| Vue       | 2       | 2016  | Virtual DOM, Large Enterprise Adoption        |
| Vue       | 3       | 2020  | Composition API, Better TypeScript Support ⭐ |
| Vue       | 3.5+    | 2024+ | Reactivity & Performance Improvements         |

- Angular

| Framework | Version | Year  | Major Update                        |
| --------- | ------- | ----- | ----------------------------------- |
| Angular   | 2       | 2016  | Complete Rewrite, TypeScript        |
| Angular   | 9       | 2020  | Ivy Renderer ⭐                     |
| Angular   | 15      | 2022  | Standalone Components ⭐            |
| Angular   | 16      | 2023  | Signals (Angular Reactivity) ⭐     |
| Angular   | 17      | 2023  | New Control Flow (`@if`, `@for`) ⭐ |
| Angular   | 18+     | 2024+ | Signals Expansion, SSR Improvements |
| Angular   | 20      | 2026  | Latest Stable Release               |

---

## 📌 REST API vs JSON vs HTTP

| Term     | Purpose                | Example                   |
| -------- | ---------------------- | ------------------------- |
| HTTP     | Communication Protocol | Browser ↔ Server          |
| JSON     | Data Format            | API Request/Response Data |
| REST API | API Design Standard    | `/users`, `/orders`       |

### Relationship

```txt
Frontend
    ↓
HTTP Request
    ↓
REST API Endpoint
    ↓
JSON Response
    ↓
Frontend UI
```

### HTTP (HyperText Transfer Protocol)

- Communication between Client and Server

```txt
Examples:-/
GET
POST
PUT
PATCH
DELETE
```

- Request

```http
GET /users
```

- Response

```http
200 OK
```

### JSON (JavaScript Object Notation)

- Exchange Data Between Frontend & Backend

```json
// JSON Response
{
  "id": 1,
  "name": "John Doe",
  "email": "john@test.com"
}

// JSON Request
{
  "name": "John Doe",
  "email": "john@test.com"
}
```

### REST API

- Standard Way To Design APIs

Users Resource

```http
GET    /users
GET    /users/1
POST   /users
PUT    /users/1
DELETE /users/1
```

### Real CRUD Example

1. Create User

```http
POST /users
```

2. Request

```json
{
  "name": "John Doe",
  "email": "john@test.com"
}
```

3. Response

```json
{
  "id": 1,
  "name": "John Doe"
}
```

4. Get Users

```http
GET /users
```

5. Response

```json
[
  {
    "id": 1,
    "name": "John Doe"
  }
]
```

```txt
HTTP: Protocol used for communication between client and server.
JSON: Lightweight data format used for data exchange.
REST API: Architectural style that uses HTTP methods to perform CRUD operations on resources.
```

## Easy Definitions

| Term  | Full Form                          |
| ----- | ---------------------------------- |
| API   | Application Programming Interface  |
| REST  | Representational State Transfer    |
| HTTP  | HyperText Transfer Protocol        |
| HTTPS | HyperText Transfer Protocol Secure |
| JSON  | JavaScript Object Notation         |
| CRUD  | Create, Read, Update, Delete       |
| URL   | Uniform Resource Locator           |
| URI   | Uniform Resource Identifier        |
| JWT   | JSON Web Token                     |
| CORS  | Cross-Origin Resource Sharing      |

---

## 📌 Agile vs Scrum

| Term  | Purpose                          | Description                          |
| ----- | -------------------------------- | ------------------------------------ |
| Agile | Software Development Methodology | Deliver software in small iterations |
| Scrum | Agile Framework                  | Structured way to implement Agile    |

### Agile

```txt
Purpose: Deliver software faster with continuous feedback

Principles:
Small Releases
Customer Feedback
Continuous Improvement
Adapt To Changes

Flow:
Plan
↓
Develop
↓
Test
↓
Release
↓
Feedback
↓
Repeat
```

### Scrum

```txt
Purpose: Organize Agile work into fixed-length sprints

Sprint: Usually 1-2 Weeks

Flow:
Sprint Planning
↓
Development
↓
Daily Standup
↓
Testing
↓
Sprint Review
↓
Retrospective
```

### Agile vs Traditional Waterfall

| Agile               | Waterfall           |
| ------------------- | ------------------- |
| Small Releases      | One Big Release     |
| Continuous Feedback | Feedback At End     |
| Flexible            | Rigid               |
| Frequent Delivery   | Long Delivery Cycle |

| Purpose             | Project Tools                           |
| ------------------- | --------------------------------------- |
| Task Management     | Jira, ClickUp                           |
| Documentation       | Confluence, Notion, GitBook, Docusaurus |
| Communication       | Slack, Microsoft Teams, Zoom            |
| Source Control      | GitHub, GitLab, Bitbucket, Azure Repos  |
| Design              | Figma, Adobe XD                         |
| Version Control     | Git                                     |
| Code Editor         | VS Code, Cursor                         |
| AI Coding Assistant | GitHub Copilot, Cursor AI, Claude Code  |

---

## 📌 CI/CD vs DevOps

| Term   | Purpose                        | Description                            |
| ------ | ------------------------------ | -------------------------------------- |
| CI     | Continuous Integration         | Automatically Build & Test Code        |
| CD     | Continuous Delivery/Deployment | Automatically Release Code             |
| DevOps | Culture & Practices            | Development + Operations Collaboration |

| CI/CD Tools         | Purpose    |
| ------------------- | ---------- |
| GitHub Actions      | CI/CD      |
| GitLab CI/CD        | CI/CD      |
| Jenkins             | Automation |
| Azure Pipelines     | CI/CD      |
| CircleCI            | CI/CD      |
| Bitbucket Pipelines | CI/CD      |

---

## 📌 Common Software Development Tools

| Purpose                 | Tool                                           |
| ----------------------- | ---------------------------------------------- |
| Task Management         | Jira, Azure Boards, Trello, ClickUp, Linear    |
| Documentation           | Confluence, Notion, GitBook, Docusaurus        |
| Communication           | Slack, Microsoft Teams, Discord, Zoom          |
| Source Control          | GitHub, GitLab, Bitbucket, Azure Repos         |
| Design                  | Figma, FigJam, Adobe XD, Sketch, Zeplin        |
| API Testing             | Postman, Insomnia, Bruno                       |
| Version Control         | Git, SVN                                       |
| Package Management      | npm, pnpm, Yarn, Bun                           |
| Build Tools             | Vite, Webpack, Parcel, Rspack, Turbopack       |
| Code Editor             | VS Code, WebStorm, Cursor                      |
| AI Coding Assistant     | GitHub Copilot, Cursor AI, Claude Code         |
| UI Libraries            | Shadcn UI, MUI, Ant Design, Chakra UI, Mantine |
| Styling                 | Tailwind CSS, Sass, Styled Components, Emotion |
| State Management        | Zustand, Redux Toolkit, MobX                   |
| Server State            | TanStack Query, SWR, Apollo Client             |
| Forms                   | React Hook Form, Formik                        |
| Validation              | Zod, Yup                                       |
| Tables                  | TanStack Table, AG Grid                        |
| Charts                  | Recharts, ECharts, Chart.js                    |
| Rich Text Editor        | Tiptap, Quill, CKEditor                        |
| Drag & Drop             | Dnd Kit, React DnD                             |
| Animation               | GSAP, Framer Motion                            |
| Testing (Unit)          | Vitest, Jest                                   |
| Testing (Component)     | React Testing Library                          |
| Testing (E2E)           | Playwright, Cypress                            |
| Code Formatting         | Prettier                                       |
| Code Linting            | ESLint, Stylelint                              |
| Git Hooks               | Husky, Lint-Staged                             |
| CI/CD                   | GitHub Actions, GitLab CI/CD, Jenkins          |
| Hosting                 | Vercel, Netlify, Firebase Hosting              |
| Cloud Platforms         | AWS, Azure, Google Cloud                       |
| Containers              | Docker                                         |
| Container Orchestration | Kubernetes                                     |
| Monitoring              | Sentry, Datadog, New Relic                     |
| Analytics               | Google Analytics, PostHog, Mixpanel            |
| Feature Flags           | LaunchDarkly, ConfigCat                        |
| Authentication          | Auth0, Clerk, Firebase Auth                    |
| Payments                | Stripe, Razorpay, PayPal                       |
| Email Services          | Resend, SendGrid, Mailgun                      |
| Search Services         | Algolia, Elasticsearch                         |
| CDN / Media             | Cloudinary, Imgix                              |
| Maps                    | Google Maps, Mapbox, Leaflet                   |
| Real-Time               | WebSocket, Socket.IO, Pusher                   |
| Push Notifications      | Firebase Cloud Messaging                       |
| CMS                     | WordPress, Strapi, Contentful, Sanity          |
| Backend as a Service    | Supabase, Firebase, Appwrite                   |
| Database                | PostgreSQL, MySQL, MongoDB                     |
| ORM                     | Prisma, TypeORM, Sequelize                     |
| API Documentation       | Swagger/OpenAPI, Redoc                         |
| Logging                 | LogRocket, Datadog Logs                        |
| Error Tracking          | Sentry, Bugsnag                                |

---

## 📌 Node.js

| Purpose  | Run JavaScript Outside Browser            |
| -------- | ----------------------------------------- |
| Type     | JavaScript Runtime                        |
| Built On | Chrome V8 Engine                          |
| Used For | Backend Development, APIs, Scripts, Tools |

**_Before Node.js:_** JavaScript > Browser Only
**_After Node.js:_** JavaScript > Browser + Server

```txt
React App (React + TypeScript)
↓
API Call (fetch / axios)
↓
Node.js Backend (Express / NestJS)
↓
Business Logic
↓
ORM (Prisma)
↓
Database (PostgreSQL)
↓
Prisma Returns Data
↓
Backend Returns JSON
↓
React Updates UI
```

| Layer          | Responsibility       |
| -------------- | -------------------- |
| React          | UI, Forms, API Calls |
| API Client     | HTTP Requests        |
| Express/NestJS | Routes, Middleware   |
| Services       | Business Logic       |
| Prisma         | Database Queries     |
| PostgreSQL     | Data Storage         |

**_Frontend Developer View:_** React > Calls API > Receives JSON > Updates UI

| Node.js Modules | Purpose               |
| --------------- | --------------------- |
| fs              | File System           |
| path            | File Paths            |
| http            | Create Server         |
| os              | System Info           |
| crypto          | Encryption, UUID      |
| stream          | Large Data Processing |

| Backend Frameworks | Purpose            |
| ------------------ | ------------------ |
| Express.js         | Most Popular       |
| NestJS             | Enterprise Backend |
| Fastify            | High Performance   |
| Koa                | Lightweight        |

**_Common Backend Features_**

- REST APIs
- Authentication
- Authorization
- CRUD
- File Upload
- Email Service
- Payments
- WebSocket
- Database Access
- Background Jobs

| Feature                | React | Node.js |
| ---------------------- | ----- | ------- |
| UI Rendering           | ✅    | ❌      |
| Components             | ✅    | ❌      |
| State Management       | ✅    | ❌      |
| API Integration        | ✅    | ❌      |
| REST API Creation      | ❌    | ✅      |
| Database Access        | ❌    | ✅      |
| Authentication         | ❌    | ✅      |
| Business Logic         | ❌    | ✅      |
| File Upload Processing | ❌    | ✅      |

---

## 📌 Chrome DevTools

| Tab         | Purpose          | Real Example                         |
| ----------- | ---------------- | ------------------------------------ |
| Elements    | Inspect HTML/CSS | CSS not applying, Flex/Grid issues   |
| Console     | Logs & Errors    | `console.log()`, JS errors           |
| Network     | API Debugging    | Check request, response, status code |
| Sources     | JS Debugging     | Breakpoints, step through code       |
| Application | Browser Storage  | JWT, LocalStorage, Cookies           |
| Performance | Speed Analysis   | Slow page, heavy rendering           |
| Memory      | Memory Leaks     | Detect unused objects                |
| Lighthouse  | Audit            | Performance, SEO, Accessibility      |

### Elements

```txt
Inspect DOM
Edit CSS Live
Check Flex/Grid

Example:
Button hidden
↓
Inspect CSS
↓
display: none
```

### Console

```js
console.log(user);
console.table(users);
```

```txt
Example:
Cannot read property
↓
Check stack trace
↓
Fix bug
```

### Network

- Most Used Tab

```txt
Example:
User Clicks Login
↓
POST /login
↓
Status 401
↓
Invalid Credentials
```

Check:

```txt
Headers
Payload
Response
Timing
Status Code
```

### Sources

```txt
Add Breakpoints
Pause Execution
Inspect Variables
```

```js
debugger;
```

```txt
Example:
Wrong Calculation
↓
Pause Code
↓
Inspect Variables
```

### Application

```txt
Local Storage
Session Storage
Cookies
```

```txt
Example:
User Logged Out
↓
JWT Missing
↓
Check Local Storage
```

### Performance

```txt
Record
↓
Analyze Rendering
```

```txt
Example:
Page Lagging
↓
Record Performance
↓
Find Slow Component
```

### Memory

```txt
Find Memory Leaks
```

```txt
Example:
Dashboard Open 1 Hour
↓
Memory Keeps Growing
↓
Detect Leaked Objects
```

### Lighthouse

```txt
Performance
Accessibility
SEO
Best Practices
```

```txt
Example:
Before Release
↓
Run Lighthouse
↓
Fix Report Issues
```

### Frontend Debugging Flow

- CSS Issue > Elements
- API Issue > Network
- JS Error > Console
- Logic Bug > Sources
- Auth Issue > Application
- Slow Page > Performance

```txt
Elements: Inspect and modify DOM/CSS.
Network: Debug API requests and responses.
Console: View logs and runtime errors.
Sources: Debug JavaScript using breakpoints.
Application: Inspect LocalStorage, Cookies, Session Storage.
Performance: Analyze rendering and loading bottlenecks.
```

---

## 📌 Micro Frontend Architecture

Micro Frontend Architecture divides a large frontend into independently developed and deployed frontend applications owned by separate teams.

| Purpose    | Split Large Frontend Into Independent Applications |
| ---------- | -------------------------------------------------- |
| Similar To | Microservices For Frontend                         |
| Used By    | Large Enterprise Applications                      |

### Traditional Frontend

- Single React App

```txt
Frontend
├── Dashboard
├── Users
├── Orders
├── Reports
└── Settings
```

- **Problems** : Huge Codebase | Team Conflicts | Slow Deployments | Difficult Scaling

### Micro Frontend Architecture

```txt
Shell App

├── Dashboard App
├── Users App
├── Orders App
├── Reports App
└── Settings App
```

- **Benefits** : Independent Teams | Independent Deployments | Smaller Codebases | Faster Releases

---

## 📌 Progressive Web Applications (PWA)

- Installable websites that work like mobile applications.
- Installable | Offline Support | Push Notifications | Fast Loading | Responsive
- A PWA is typically built using standard web technologies (HTML, CSS, JavaScript/TypeScript) plus Service Workers, Web App Manifest, HTTPS, and optional tools like Workbox or vite-plugin-pwa to provide app-like capabilities.

| Item               | Description                                    |
| ------------------ | ---------------------------------------------- |
| Definition         | Web application that behaves like a mobile app |
| Installable        | ✅                                             |
| Offline Support    | ✅                                             |
| Push Notifications | ✅                                             |
| App Store Required | ❌                                             |
| Platform           | Web, Android, Desktop                          |

```txt
User Visits Website
↓
Install App
↓
App Appears On Home Screen
↓
Works Like Native App
```

| Technology       | Purpose                   |
| ---------------- | ------------------------- |
| Service Worker   | Offline Support & Caching |
| Web App Manifest | App Installation          |
| HTTPS            | Security Requirement      |

- Purpose

```txt
Offline Access, Cache Assets, Background Sync, Push Notifications
```

- Example

```txt
User Opens App > CSS/JS Cached > Internet Lost > App Still Opens
```

| Feature            | Example                  |
| ------------------ | ------------------------ |
| Install App        | Add To Home Screen       |
| Offline Access     | Previously Visited Pages |
| Push Notifications | New Order Alert          |
| Background Sync    | Retry Failed Requests    |
| Fast Loading       | Cached Assets            |

| Real-Life Use Cases | Example               |
| ------------------- | --------------------- |
| E-Commerce          | Product Browsing      |
| Food Delivery       | Order Tracking        |
| CRM                 | Sales Dashboard       |
| ERP                 | Employee Portal       |
| News Portal         | Read Articles Offline |
| Education           | Learning Platform     |
| Banking             | Account Dashboard     |

- Comparison

| Feature            | Website | PWA    | Native App |
| ------------------ | ------- | ------ | ---------- |
| Installable        | ❌      | ✅     | ✅         |
| Offline Support    | ❌      | ✅     | ✅         |
| Push Notifications | ❌      | ✅     | ✅         |
| App Store Required | ❌      | ❌     | ✅         |
| Device Access      | ❌      | ⚠️     | ✅         |
| Development Cost   | Low     | Medium | High       |

- Device Access Comparison

| Feature             | Website    | PWA        | Native App |
| ------------------- | ---------- | ---------- | ---------- |
| Camera              | ❌         | ✅         | ✅         |
| Microphone          | ❌         | ✅         | ✅         |
| GPS Location        | ❌         | ✅         | ✅         |
| Push Notifications  | ❌         | ✅         | ✅         |
| File Upload         | ✅         | ✅         | ✅         |
| Bluetooth           | ❌         | ⚠️ Limited | ✅         |
| NFC                 | ❌         | ⚠️ Limited | ✅         |
| Contacts            | ❌         | ❌         | ✅         |
| SMS                 | ❌         | ❌         | ✅         |
| Call Logs           | ❌         | ❌         | ✅         |
| Background Services | ❌         | ⚠️ Limited | ✅         |
| Biometrics          | ⚠️ Limited | ⚠️ Limited | ✅         |
| Calendar Access     | ❌         | ⚠️ Limited | ✅         |

### PWA-Specific Technologies

| Technology          | Purpose                  |
| ------------------- | ------------------------ |
| Service Worker      | Offline Support, Caching |
| Web App Manifest    | Install App              |
| HTTPS               | Security Requirement     |
| Push API            | Notifications            |
| Cache API           | Store Assets Offline     |
| Background Sync API | Retry Failed Requests    |

```txt
Frontend
├── React
├── TypeScript
├── Vite
├── Tailwind
└── React Query

PWA
├── Workbox
├── Service Worker
├── Manifest
└── Push Notifications

Backend
├── Node.js
├── Express/NestJS
└── PostgreSQL
```

### Minimal React PWA Setup

```bash
npm install -D vite-plugin-pwa
```

```ts
// vite.config.ts
import { VitePWA } from "vite-plugin-pwa";
plugins: [VitePWA()];
```

```txt
React App > Installable (Offline Ready, PWA Enabled)
```

---

## 📌 Web Rendering Models

| Rendering | HTML Generated By  | Best For                   | Examples                   |
| --------- | ------------------ | -------------------------- | -------------------------- |
| CSR       | Browser            | Dashboards, Admin Panels   | React, Vue, Angular        |
| SSR       | Server             | SEO, Public Pages          | Next.js, Nuxt, ASP.NET MVC |
| SSG       | Build Time         | Blogs, Docs, Landing Pages | Astro, Next.js             |
| ISR       | Build + Revalidate | Product Catalogs, News     | Next.js                    |
| Hybrid    | Mix Of Above       | Modern SaaS Products       | Next.js, Nuxt, SvelteKit   |

| Rendering | Technology   |
| --------- | ------------ |
| SSR       | WordPress    |
|           | Laravel      |
|           | Django       |
|           | Rails        |
|           | Spring MVC   |
|           | ASP.NET MVC  |
| CSR       | React + Vite |
|           | Vue + Vite   |
|           | Angular      |
| Hybrid    | Next.js      |
|           | Nuxt.js      |
|           | SvelteKit    |
| SSG       | Astro        |
|           | Gatsby       |

### CSR (Client-Side Rendering)

| Item         | Details                                        |
| ------------ | ---------------------------------------------- |
| How It Works | Browser downloads JavaScript and renders UI    |
| Steps        | Empty HTML → Download JS → Render UI           |
| Technologies | React + Vite, Vue SPA, Angular SPA, Svelte SPA |
| Best For     | CRM, ERP, Admin Panels, Dashboards             |
| Pros         | Fast Navigation, Rich Interactivity            |
| Cons         | Poor SEO, Slower Initial Load                  |

### SSR (Server-Side Rendering)

| Item         | Details                                                                 |
| ------------ | ----------------------------------------------------------------------- |
| How It Works | Server generates HTML before sending page                               |
| Steps        | Request → Server HTML → Content Visible → Hydration                     |
| Technologies | WordPress, Laravel, Django, Rails, Spring MVC, ASP.NET MVC, Next.js SSR |
| Best For     | SEO Websites, E-Commerce, News Portals                                  |
| Pros         | Better SEO, Faster First Content Paint                                  |
| Cons         | More Server Load, Higher Complexity                                     |

### SSG (Static Site Generation)

| Item         | Details                                             |
| ------------ | --------------------------------------------------- |
| How It Works | HTML generated during build process                 |
| Steps        | Build → Generate HTML → Deploy → Serve Static Files |
| Technologies | Astro, Gatsby, Next.js SSG, Docusaurus              |
| Best For     | Blogs, Documentation, Portfolios, Landing Pages     |
| Pros         | Extremely Fast, Cheap Hosting                       |
| Cons         | Requires Rebuild For Content Changes                |

### ISR (Incremental Static Regeneration)

| Item         | Details                                                 |
| ------------ | ------------------------------------------------------- |
| How It Works | Static pages regenerated automatically after deployment |
| Steps        | Build → Serve Static Page → Rebuild In Background       |
| Technologies | Next.js ISR                                             |
| Best For     | Product Catalogs, News Articles                         |
| Pros         | Fast Like SSG, Fresh Like SSR                           |
| Cons         | Framework Support Limited                               |

### Hybrid Rendering

| Item         | Details                                            |
| ------------ | -------------------------------------------------- |
| How It Works | Different pages use different rendering strategies |
| Steps        | Public Pages SSR/SSG + Dashboard CSR               |
| Technologies | Next.js, Nuxt.js, SvelteKit                        |
| Best For     | SaaS, Enterprise Apps, E-Commerce                  |
| Pros         | Best Performance + SEO + UX                        |
| Cons         | More Architecture Complexity                       |

---

## 📌 Data Visualization

- Data Visualization is the graphical representation of data using charts, graphs, maps, and dashboards to help users understand trends, patterns, and insights quickly.

| Item      | Description                                    |
| --------- | ---------------------------------------------- |
| Purpose   | Present Data Visually                          |
| Goal      | Identify Trends, Patterns, Insights            |
| Used In   | Dashboards, Reports, Analytics                 |
| Libraries | Chart.js, D3.js, Recharts, Highcharts, ECharts |

### Common Visualization Types

| Visualization | Best For                       | Example               |
| ------------- | ------------------------------ | --------------------- |
| Bar Chart     | Compare Categories             | Sales By Product      |
| Line Chart    | Trends Over Time               | Revenue Growth        |
| Pie Chart     | Percentage Distribution        | Market Share          |
| Donut Chart   | Part Of Whole                  | Expense Breakdown     |
| Area Chart    | Trends + Volume                | Monthly Users         |
| Scatter Plot  | Relationship Between Variables | Price vs Rating       |
| Histogram     | Data Distribution              | User Age Distribution |
| Heatmap       | Density / Intensity            | Calendar Activity     |
| Tree Map      | Hierarchical Data              | Disk Usage            |
| Gauge Chart   | KPI Progress                   | Server Usage          |
| Table         | Detailed Data                  | User List             |
| Map           | Geographic Data                | Sales By Country      |

| Frontend Libraries | Best For                       |
| ------------------ | ------------------------------ |
| Chart.js           | Simple Charts                  |
| Recharts           | React Applications             |
| D3.js              | Advanced Custom Visualizations |
| Highcharts         | Enterprise Dashboards          |
| Apache ECharts     | Large Datasets                 |
| Nivo               | Modern React Charts            |
| Victory            | React Data Visualization       |

| Dashboard Widget    | Visualization     |
| ------------------- | ----------------- |
| Revenue Trend       | Line Chart        |
| Sales By Category   | Bar Chart         |
| Market Share        | Pie Chart         |
| User Growth         | Area Chart        |
| Product Performance | Table + Bar Chart |
| Geographic Sales    | Map               |
| KPI Metrics         | Gauge / Cards     |

---

## 📌 Frontend Rendering Flow

- HTML - Structure of the webpage
- CSS - Styling rules

| Term            | One-Liner                                        | Processing Cost |
| --------------- | ------------------------------------------------ | --------------- |
| DOM             | Tree representation of HTML elements             | 🟡 Medium       |
| CSSOM           | Tree representation of CSS rules                 | 🟡 Medium       |
| Render Tree     | Combination of DOM and CSSOM used for rendering  | 🟡 Medium       |
| Layout (Reflow) | Calculates size and position of elements         | 🔴 Heavy        |
| Paint (Repaint) | Draws pixels on the screen                       | 🟠 Moderate     |
| Composite       | Combines layers for final rendering (GPU)        | 🟢 Light        |
| Virtual DOM     | Lightweight JavaScript representation of the DOM | 🟢 Light        |
| Hydration       | Attaches JavaScript behavior to SSR HTML         | 🟠 Moderate     |

```txt
Parse HTML
 ↓
DOM Creation
 ↓
CSS Parsing
 ↓
CSSOM Creation
 ↓
Render Tree
 ↓
Layout (Reflow)
 ↓
Paint (Repaint)
 ↓
Composite
 ↓
Screen
```

### Example

- DOM Tree:

```txt
Document
 └─ div
     ├─ h1
     └─ button
```

- CSSOM:

```txt
h1
 └─ color: red
```

- Render Tree:
  - Only visible elements included. (display:none - Not Added)

```txt
DOM + CSSOM

h1
 ├─ text: Hello
 └─ color: red
```

- Layout (Reflow) Calculates:

```txt
Width + Height
Position
Margin + Padding
-----
Button
Width = 120px
X = 100
Y = 50
```

- Paint (Repaint)
  - Browser paints blue text.

```txt
Text
Color
Border
Background
Shadow
```

- Composite
  - Combines layers using GPU.

```text
Move Existing Layer
↓
No Layout
↓
No Paint
-----
transform: translateX(100px);
opacity: 0.5;
```

- Virtual DOM (React)

```txt
JavaScript Object Tree
Not Real DOM
```

```jsx
<h1>Hello</h1>

// React creates:
{
  type: "h1",
  props: {
    children: "Hello"
  }
}
```

- Diffing (Only changed nodes updated.)

```txt
Old Virtual DOM
↓
Compare
↓
New Virtual DOM
```

- Hydration

```txt
Server Sends HTML
↓
Page Visible
↓
React Attaches Events
-----
HTML Visible
↓
Button Click Starts Working
```

### Rendering Stages

| Stage           | Purpose                      | Output       |
| --------------- | ---------------------------- | ------------ |
| DOM             | Parse HTML                   | DOM Tree     |
| CSSOM           | Parse CSS                    | CSS Tree     |
| Render Tree     | Combine DOM + CSSOM          | Render Tree  |
| Layout (Reflow) | Calculate Size & Position    | Layout Data  |
| Paint (Repaint) | Draw Pixels                  | Layers       |
| Composite       | Merge Layers & GPU Rendering | Final Screen |

### Quick Memory Table

| Input       | Output      |
| ----------- | ----------- |
| HTML        | DOM         |
| CSS         | CSSOM       |
| DOM + CSSOM | Render Tree |
| Render Tree | Layout      |
| Layout      | Paint       |
| Paint       | Composite   |
| JSX         | Virtual DOM |
| SSR HTML    | Hydration   |

---
