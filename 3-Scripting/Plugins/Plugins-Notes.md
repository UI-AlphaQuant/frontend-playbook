# 👉 Popular Plugins

## 📌 JavaScript Plugins & Libraries

| Plugin / Library    | Purpose                | Common Usage            | Real-World Apps      |
| ------------------- | ---------------------- | ----------------------- | -------------------- |
| `Axios`             | HTTP requests          | API handling            | Dashboards/SaaS      |
| `Lodash`            | Utility helpers        | Arrays/objects/debounce | Large applications   |
| `Day.js`            | Date formatting        | Time/date handling      | Calendars/apps       |
| `Chart.js`          | Charts & graphs        | Analytics UI            | Trading/admin panels |
| `Swiper.js`         | Sliders/carousels      | Touch sliders           | Ecommerce/banner UI  |
| `GSAP`              | Advanced animations    | Motion effects          | Interactive websites |
| `Anime.js`          | Lightweight animations | UI animations           | Landing pages        |
| `Three.js`          | 3D graphics            | WebGL/3D scenes         | Games/3D sites       |
| `D3.js`             | Data visualization     | Complex charts          | Analytics systems    |
| `Socket.io`         | Realtime communication | Chat/live updates       | Messaging apps       |
| `SortableJS`        | Drag & drop sorting    | Reorder lists           | Kanban/task apps     |
| `FullCalendar`      | Calendar UI            | Scheduling/events       | Booking systems      |
| `Formik`            | Form handling          | Forms/validation        | React apps           |
| `Yup`               | Schema validation      | Form validation         | Enterprise forms     |
| `Zod`               | Type-safe validation   | API/forms validation    | Modern TS apps       |
| `Fuse.js`           | Fuzzy search           | Search/filter           | Product search       |
| `Tippy.js`          | Tooltips/popovers      | UI tooltips             | Dashboards           |
| `Lenis`             | Smooth scrolling       | Scroll effects          | Modern landing pages |
| `Locomotive Scroll` | Scroll animations      | Parallax effects        | Portfolio sites      |
| `Framer Motion`     | React animations       | UI transitions          | React applications   |

### Common Frontend Utility Plugins

| Utility Type  | Popular Choice |
| ------------- | -------------- |
| API Calls     | `Axios`        |
| Date Handling | `Day.js`       |
| Charts        | `Chart.js`     |
| Animations    | `GSAP`         |
| Sliders       | `Swiper.js`    |
| Drag & Drop   | `SortableJS`   |
| Search        | `Fuse.js`      |
| Validation    | `Yup` / `Zod`  |

### Example Syntax

```js
// Axios
axios.get("/users");

// Lodash Debounce
_.debounce(fn, 300);

// Day.js
dayjs().format("DD/MM/YYYY");

// Chart.js
new Chart(ctx, config);

// Swiper
new Swiper(".swiper");
```

### Modern Standards

| Old / Less Preferred | Modern Preferred         |
| -------------------- | ------------------------ |
| `Moment.js`          | `Day.js`                 |
| jQuery plugins       | Native JS / frameworks   |
| Manual animations    | `GSAP` / `Framer Motion` |
| Heavy utility libs   | Small focused libs       |

### Most Used in Modern Frontend

| Category        | Most Popular    |
| --------------- | --------------- |
| HTTP Requests   | `Axios`         |
| Animations      | `GSAP`          |
| Date Library    | `Day.js`        |
| Charts          | `Chart.js`      |
| React Animation | `Framer Motion` |
| Sliders         | `Swiper.js`     |

---

## 📌 Modern Frontend Functionality & Popular Libraries

| Functionality        | Common Use Cases                 | JS  | React | Recommended Library       |
| -------------------- | -------------------------------- | --- | ----- | ------------------------- |
| API Calls            | Backend Integration              | ✅  | ✅    | Fetch, Axios              |
| Server State         | API Caching, Refetching          | ❌  | ✅    | TanStack Query            |
| Global State         | Auth, Theme, User                | ❌  | ✅    | Zustand                   |
| Forms                | Login, Registration, CRUD        | ✅  | ✅    | React Hook Form           |
| Validation           | Forms, Inputs                    | ✅  | ✅    | Zod                       |
| Tables               | Search, Filter, Sort, Pagination | ✅  | ✅    | TanStack Table            |
| Data Grid            | Excel-like Enterprise Tables     | ❌  | ✅    | AG Grid                   |
| Charts               | Analytics, Dashboard             | ✅  | ✅    | Recharts                  |
| File Upload          | Documents, Images                | ✅  | ✅    | React Dropzone            |
| Drag & Drop          | Kanban, Uploads, Sortable Lists  | ✅  | ✅    | Dnd Kit                   |
| Date Handling        | Formatting, Calculations         | ✅  | ✅    | date-fns                  |
| Infinite Scroll      | Feeds, Products                  | ✅  | ✅    | IntersectionObserver      |
| Authentication UI    | Login, Session                   | ✅  | ✅    | JWT                       |
| Permissions UI       | Role-Based UI                    | ✅  | ✅    | Custom Logic              |
| Real-Time            | Chat, Notifications              | ✅  | ✅    | WebSocket, Socket.IO      |
| Maps                 | Location, Tracking               | ✅  | ✅    | Google Maps, Leaflet      |
| Rich Text Editor     | Blogs, CMS                       | ✅  | ✅    | Tiptap                    |
| PDF Viewer           | Documents                        | ✅  | ✅    | React PDF                 |
| Internationalization | Multi Language                   | ✅  | ✅    | react-i18next             |
| Theme Switching      | Light/Dark Mode                  | ✅  | ✅    | next-themes               |
| Animation            | UI Motion                        | ✅  | ✅    | GSAP, Framer Motion       |
| Error Tracking       | Production Monitoring            | ✅  | ✅    | Sentry                    |
| Analytics            | User Tracking                    | ✅  | ✅    | PostHog, Google Analytics |
| Feature Flags        | Beta Features                    | ✅  | ✅    | LaunchDarkly              |
| Payments             | Checkout                         | ✅  | ✅    | Stripe                    |
| Video Player         | Courses, Media                   | ✅  | ✅    | React Player              |
| Image Optimization   | Gallery, CMS                     | ✅  | ✅    | Cloudinary                |
| Slider / Carousel    | Hero Banner, Gallery             | ✅  | ✅    | Embla Carousel            |
| Range Slider         | Price Filter, Volume Control     | ✅  | ✅    | React Range, Radix Slider |
| Resizable Panels     | IDE, Dashboard Layout            | ❌  | ✅    | React Resizable Panels    |
| Tree View            | File Explorer, Categories        | ✅  | ✅    | React Complex Tree        |
| Command Palette      | VS Code Search                   | ❌  | ✅    | CMDK                      |
| Scheduler            | Meetings, Events                 | ❌  | ✅    | FullCalendar              |
| Virtualization       | Large Lists/Tables               | ❌  | ✅    | TanStack Virtual          |
| Image Cropper        | Profile Image Upload             | ✅  | ✅    | React Easy Crop           |
| QR Code              | Payments, Sharing                | ✅  | ✅    | qrcode                    |
| Barcode Scanner      | Inventory                        | ✅  | ✅    | html5-qrcode              |
| Camera Access        | KYC, Scan Docs                   | ✅  | ✅    | MediaDevices API          |
| Audio Recording      | Voice Notes                      | ✅  | ✅    | MediaRecorder API         |
| Video Recording      | Interview Apps                   | ✅  | ✅    | MediaRecorder API         |
| Clipboard            | Copy Coupon, URL                 | ✅  | ✅    | Clipboard API             |
| PWA / Offline Mode   | Mobile-like Apps                 | ✅  | ✅    | Workbox                   |
| Push Notifications   | Alerts                           | ✅  | ✅    | Firebase Cloud Messaging  |
| SEO                  | Meta Tags                        | ❌  | ✅    | React Helmet              |
| Unit Testing         | Component Testing                | ✅  | ✅    | Vitest                    |
| E2E Testing          | Full App Testing                 | ✅  | ✅    | Playwright                |
| UI Slider / Carousel | Hero Banner, Product Gallery     | ✅  | ✅    | Embla Carousel, Swiper    |

---
