# 👉 Core React

## 📌 React Fundamentals

React is a JavaScript library used to build reusable and dynamic user interfaces.

### Core

React is a JavaScript library for building UI using reusable components.

Instead of manually updating DOM:

```js
document.getElementById("title").innerText = "Hello";

function App() {
  return <h1>Hello</h1>;
}
```

- Babel
  Its main job is to convert modern JavaScript and JSX into code that browsers can understand.
  JSX → JavaScript

```html
<script type="text/babel">
  const element = <h1>Hello</h1>;
</script>
```

```js
// Babel Convert
const element = React.createElement("h1", null, "Hello");
```

```text
Modern React apps use: Vite, Webpack, Parcel, Next.js
These compile JSX during build time.

App.jsx
   ↓
Babel
   ↓
Bundle
   ↓
Browser
```

---

| Concept             | Details                     |
| ------------------- | --------------------------- |
| React               | UI library by Meta          |
| SPA                 | Single Page Application     |
| Component-Based     | Build UI using components   |
| Declarative UI      | Describe UI using state     |
| Virtual DOM         | Optimized DOM updates       |
| Reusable Components | Reuse UI blocks             |
| One-Way Data Flow   | Parent → Child data flow    |
| Reactive Rendering  | UI updates on state changes |

| Rendering Type | Purpose                     |
| -------------- | --------------------------- |
| CSR            | Client-side rendering       |
| SSR            | Server-side rendering       |
| SSG            | Static site generation      |
| Hydration      | Attach React to server HTML |

| Core Features | Usage                          |
| ------------- | ------------------------------ |
| JSX           | Write HTML-like syntax         |
| Props         | Pass data between components   |
| State         | Store dynamic data             |
| Hooks         | Add React features to function |
| Events        | Handle user interactions       |
| Routing       | Navigate between pages         |

```jsx
function App() {
  return <h1>Hello React</h1>;
}

export default App;
```

### React Flow

```txt
Component
   ↓
State / Props Change
   ↓
Render JSX
   ↓
Create New Virtual DOM
   ↓
Diffing Algorithm Compare Changes
   ↓
Find Updated Elements
   ↓
Reconciliation Process
   ↓
Update Changed Parts in Real DOM
   ↓
Browser Updates UI
```

| Best Practice         | Notes                         |
| --------------------- | ----------------------------- |
| Keep components small | Easier maintenance            |
| Reuse components      | Avoid duplicate UI            |
| Use state carefully   | Prevent unnecessary renders   |
| Prefer composition    | Better scalability            |
| Use hooks properly    | Cleaner functional components |

| Real-World Usage | Example                   |
| ---------------- | ------------------------- |
| Dashboard UI     | Admin panels              |
| E-commerce       | Product pages             |
| SaaS Apps        | CRM / ERP systems         |
| Social Apps      | Feeds & chat systems      |
| Mobile Apps      | React Native applications |

### CSR vs SSR vs SSG

CSR, SSR, and SSG are different rendering methods used in React applications.

| Type | Full Form              | Rendering Location | Speed          | SEO       | Best For                   |
| ---- | ---------------------- | ------------------ | -------------- | --------- | -------------------------- |
| CSR  | Client-Side Rendering  | Browser            | Slower initial | Weak      | Dashboards, SaaS apps      |
| SSR  | Server-Side Rendering  | Server             | Faster initial | Strong    | SEO-heavy websites         |
| SSG  | Static Site Generation | Build time         | Very fast      | Excellent | Blogs, docs, landing pages |

| Rendering Type | Process                        | Common Technology |
| -------------- | ------------------------------ | ----------------- |
| CSR            | JS loads → React renders UI    | React             |
| SSR            | Server renders HTML on request | Next.js           |
| SSG            | HTML generated during build    | Next.js, Gatsby   |

```jsx
// CSR
root.render(<App />);

// SSR (Next.js)
export async function getServerSideProps() {
  return { props: {} };
}

// SSG (Next.js)
export async function getStaticProps() {
  return { props: {} };
}
```

### Rendering Flow

```txt
CSR:
Browser → Load JS → Render React UI

SSR:
Request → Server Render HTML → Browser Hydration

SSG:
Build Time → Generate HTML → Serve Static Files
```

| Best Practice            | Notes                       |
| ------------------------ | --------------------------- |
| Use CSR for apps         | Better interactivity        |
| Use SSR for SEO          | Faster first page load      |
| Use SSG for static pages | Maximum performance         |
| Mix rendering strategies | Common in modern React apps |

| Real-World Usage | Rendering Type |
| ---------------- | -------------- |
| Admin Dashboard  | CSR            |
| E-commerce SEO   | SSR            |
| Blog Website     | SSG            |
| Documentation    | SSG            |

---

## 📌 Environment Setup

React projects require Node.js, a package manager, and a build tool like Vite.

| Tool / Package | Purpose                 | Example                  |
| -------------- | ----------------------- | ------------------------ |
| Node.js        | JavaScript runtime      | `node -v`                |
| npm            | Package manager         | `npm install`            |
| Vite           | Fast React build tool   | `npm create vite@latest` |
| React          | UI library              | `react`                  |
| React DOM      | Render React in browser | `react-dom`              |

| Command                  | Purpose                  |
| ------------------------ | ------------------------ |
| `npm create vite@latest` | Create React project     |
| `npm install`            | Install dependencies     |
| `npm run dev`            | Start dev server         |
| `npm run build`          | Create production build  |
| `npm run preview`        | Preview production build |

```bash
# Create React Project
npm create vite@latest my-app

# Move to Project
cd my-app

# Install Packages
npm install

# Start Development Server
npm run dev
```

| Folders       | Purpose                 | Example Usage            |
| ------------- | ----------------------- | ------------------------ |
| `src/`        | Main application code   | Components, pages, hooks |
| `public/`     | Static public files     | favicon, robots.txt      |
| `assets/`     | Images, fonts, icons    | logos, SVGs, fonts       |
| `components/` | Reusable UI components  | Button, Card, Modal      |
| `pages/`      | Application pages       | Home, Dashboard          |
| `layouts/`    | Shared layouts          | AdminLayout              |
| `routes/`     | Routing configuration   | React Router setup       |
| `hooks/`      | Custom hooks            | `useFetch`, `useAuth`    |
| `context/`    | Context API logic       | AuthContext              |
| `store/`      | Global state management | Redux, Zustand           |
| `services/`   | API/backend calls       | Axios services           |
| `utils/`      | Helper functions        | formatters, validators   |
| `constants/`  | Static constants        | API URLs, config         |
| `styles/`     | Global styles           | SCSS, Tailwind styles    |
| `types/`      | TypeScript types        | interfaces, custom types |
| `config/`     | App configuration       | environment setup        |
| `providers/`  | Global providers        | ThemeProvider            |
| `features/`   | Feature-based modules   | Auth, Products           |
| `tests/`      | Testing files           | unit/component tests     |

| File                | Purpose                  | Example Usage          |
| ------------------- | ------------------------ | ---------------------- |
| `main.jsx`          | React entry point        | Render app             |
| `App.jsx`           | Root component           | Main application UI    |
| `.env`              | Environment variables    | API URLs, secret keys  |
| `.gitignore`        | Ignore files in Git      | node_modules, dist     |
| `package.json`      | Dependencies & scripts   | npm scripts            |
| `package-lock.json` | Dependency lock file     | Exact package versions |
| `vite.config.js`    | Vite configuration       | aliases, plugins       |
| `jsconfig.json`     | Path aliases/config      | absolute imports       |
| `tsconfig.json`     | TypeScript configuration | TS compiler options    |
| `README.md`         | Project documentation    | setup instructions     |
| `index.html`        | Root HTML template       | app mounting point     |

### Setup Flow

```txt
Install Node.js
      ↓
Create React Project
      ↓
Install Dependencies
      ↓
Run Dev Server
      ↓
Start Building UI
```

| Best Practice         | Notes                  |
| --------------------- | ---------------------- |
| Use Vite              | Faster development     |
| Keep clean structure  | Easier scalability     |
| Use components folder | Reusable architecture  |
| Separate assets       | Better maintainability |

---

## 📌 JSX

JSX (JavaScript XML) allows writing HTML-like syntax inside JavaScript.

| JSX Feature       | Purpose                   | Example                    |
| ----------------- | ------------------------- | -------------------------- |
| JSX Syntax        | HTML-like UI syntax       | `<h1>Hello</h1>`           |
| Expressions       | Dynamic values in JSX     | `{name}`                   |
| Attributes        | Add HTML attributes       | `src=""`, `alt=""`         |
| `className`       | CSS class in JSX          | `className="card"`         |
| Inline Styles     | Apply styles using object | `style={{ color: "red" }}` |
| Fragments         | Avoid extra wrapper       | `<>...</>`                 |
| Conditional JSX   | Render conditionally      | `{show && <Box />}`        |
| Lists Rendering   | Render arrays dynamically | `users.map()`              |
| Components in JSX | Render components         | `<Header />`               |

| JSX Rule             | Notes                  |
| -------------------- | ---------------------- |
| Return single parent | Wrap elements properly |
| Close all tags       | `<img />`, `<input />` |
| Use camelCase        | `onClick`, `className` |
| JS inside `{}`       | Dynamic expressions    |
| Components uppercase | `<Header />`           |

```jsx
function App() {
  const name = "React";

  return (
    <>
      <h1 className="title">{name}</h1>

      <p style={{ color: "blue" }}>JSX Example</p>
    </>
  );
}
```

### JSX Flow

```txt
JSX
  ↓
Babel Transpiles JSX
  ↓
React.createElement()
  ↓
Virtual DOM Object
  ↓
Render UI
```

| Best Practice           | Notes                      |
| ----------------------- | -------------------------- |
| Keep JSX clean          | Easier readability         |
| Split large JSX         | Better maintainability     |
| Use fragments           | Avoid unnecessary wrappers |
| Move logic outside JSX  | Cleaner UI code            |
| Use reusable components | Better scalability         |

### JSX vs TSX

JSX and TSX are syntax extensions used in React components.

| Feature        | JSX                     | TSX                         |
| -------------- | ----------------------- | --------------------------- |
| Full Form      | JavaScript XML          | TypeScript XML              |
| Language       | JavaScript              | TypeScript                  |
| Type Safety    | No                      | Yes                         |
| File Extension | `.jsx`                  | `.tsx`                      |
| Props Typing   | Not supported directly  | Strongly typed              |
| Error Checking | Runtime                 | Compile-time                |
| Best For       | Small/medium React apps | Large scalable applications |

| Syntax Example | JSX        | TSX          |
| -------------- | ---------- | ------------ |
| Component File | `App.jsx`  | `App.tsx`    |
| Props          | Normal JS  | Typed props  |
| Events         | Generic JS | Typed events |

```jsx
// JSX
function Button({ text }) {
  return <button>{text}</button>;
}
```

```tsx
// TSX
type ButtonProps = {
  text: string;
};

function Button({ text }: ButtonProps) {
  return <button>{text}</button>;
}
```

### JSX vs TSX Flow

```txt
JSX
  ↓
JavaScript
  ↓
React UI

TSX
  ↓
TypeScript Type Checking
  ↓
JavaScript
  ↓
React UI
```

| Best Practice        | Notes                       |
| -------------------- | --------------------------- |
| Use JSX for learning | Simpler syntax              |
| Use TSX for scaling  | Better maintainability      |
| Type props/events    | Safer React development     |
| Prefer TSX in teams  | Better developer experience |

---

## 📌 Components

Components are reusable UI building blocks used to create React interfaces.

| Type                     | Purpose                  | Example                |
| ------------------------ | ------------------------ | ---------------------- |
| Functional Component     | Standard React component | `function Header() {}` |
| Arrow Component          | Short functional syntax  | `const App = () => {}` |
| Parent Component         | Holds child components   | `<Layout />`           |
| Child Component          | Nested inside parent     | `<Card />`             |
| Presentational Component | Handles UI only          | `ProductCard`          |
| Container Component      | Handles logic/data       | `ProductContainer`     |
| Reusable Component       | Reused multiple times    | `<Button />`           |

| Component Feature | Purpose               | Example                  |
| ----------------- | --------------------- | ------------------------ |
| `props`           | Pass data             | `<Card title="React" />` |
| `children`        | Nested content        | `<Modal>...</Modal>`     |
| Re-rendering      | Update UI dynamically | State/props changes      |
| Composition       | Combine components    | Layout systems           |

```jsx
function Header() {
  return <h1>Header</h1>;
}

const Button = ({ text }) => {
  return <button>{text}</button>;
};

export default function App() {
  return (
    <div>
      <Header />
      <Button text="Login" />
    </div>
  );
}
```

### Component Flow

```txt
Parent Component
        ↓
Pass Props
        ↓
Child Component
        ↓
Render JSX UI
```

| Best Practice         | Notes                  |
| --------------------- | ---------------------- |
| Keep components small | Easier maintenance     |
| Use reusable UI       | Avoid duplication      |
| Use composition       | Cleaner structure      |
| Separate UI & logic   | Better scalability     |
| Use feature folders   | Organized architecture |

| Real-World Usage | Example           |
| ---------------- | ----------------- |
| Navbar           | `<Navbar />`      |
| Product Card     | `<ProductCard />` |
| Modal            | `<Modal />`       |
| Form UI          | `<Input />`       |
| Dashboard Widget | `<StatsCard />`   |

---

## 📌 Component Lifecycle

- Component lifecycle is the process of a React component being created, updated, and removed.
- React automatically unmounts components when they are removed from the UI.

| Lifecycle Phase | Purpose                    | Common Usage        |
| --------------- | -------------------------- | ------------------- |
| Mounting        | Component created/rendered | API calls, setup    |
| Updating        | Component re-renders       | State/props changes |
| Unmounting      | Component removed          | Cleanup tasks       |

| Lifecycle Action | Example                 |
| ---------------- | ----------------------- |
| Initial Render   | First UI render         |
| State Update     | Re-render component     |
| Props Change     | Update child UI         |
| Cleanup          | Remove timers/listeners |

| Hook Usage       | Purpose                   |
| ---------------- | ------------------------- |
| `useEffect()`    | Handle lifecycle logic    |
| Cleanup Function | Run before unmount/update |
| Dependency Array | Control effect execution  |

```jsx
import { useEffect } from "react";

export default function App() {
  useEffect(() => {
    console.log("Mounted");

    return () => {
      console.log("Unmounted");
    };
  }, []);

  return <h1>Lifecycle Example</h1>;
}
```

### Component Lifecycle Flow

```txt
Mount Component
      ↓
Render UI
      ↓
State / Props Update
      ↓
Re-render Component
      ↓
Unmount Component
      ↓
Cleanup Functions Run
```

### Unmounting

| Situation             | Does Unmount Happen? | Example                           |
| --------------------- | -------------------- | --------------------------------- |
| Route Change          | Yes                  | Navigate to another page          |
| Conditional Rendering | Yes                  | `show && <Modal />` becomes false |
| Parent Removed        | Yes                  | Parent component removed          |
| Page Refresh          | Yes                  | Full app reload                   |

```jsx
{
  show && <Modal />;
}
```

```jsx
useEffect(() => {
  // Connect to chat server
  console.log("Chat Connected");

  return () => {
    // Disconnect when component removed
    console.log("Chat Disconnected");
  };
}, []);
```

| Best Practice               | Notes                     |
| --------------------------- | ------------------------- |
| Use cleanup functions       | Prevent memory leaks      |
| Keep effects focused        | Easier maintenance        |
| Use dependency array wisely | Avoid unnecessary renders |
| Separate multiple effects   | Cleaner lifecycle logic   |
| Avoid heavy logic in render | Better performance        |

| Cleanup Purpose   | Example                 |
| ----------------- | ----------------------- |
| Remove Timers     | `clearInterval()`       |
| Remove Listeners  | `removeEventListener()` |
| Cancel API Calls  | `AbortController()`     |
| Close Connections | WebSocket cleanup       |

---

## 📌 Props

Props (properties) are used to pass data from parent to child components.

| Props Feature  | Purpose                     | Example                     |
| -------------- | --------------------------- | --------------------------- |
| Data Passing   | Send data to child          | `<Card title="React" />`    |
| Destructuring  | Cleaner props access        | `({ title })`               |
| Dynamic Props  | Pass variables              | `title={name}`              |
| Children Prop  | Pass nested content         | `<Modal>Content</Modal>`    |
| Function Props | Pass functions/events       | `onClick={handleClick}`     |
| Default Props  | Fallback values             | `title = "Default"`         |
| Props Drilling | Passing through many levels | Parent → Child → Grandchild |

| Props Type | Example                   |
| ---------- | ------------------------- |
| String     | `title="React"`           |
| Number     | `count={10}`              |
| Boolean    | `active={true}`           |
| Array      | `items={["A", "B"]}`      |
| Object     | `user={{ name: "John" }}` |
| Function   | `onClick={handleClick}`   |
| JSX        | `icon={<Icon />}`         |

```jsx
function Card({ title, children }) {
  return (
    <div>
      <h2>{title}</h2>
      {children}
    </div>
  );
}

export default function App() {
  return (
    <Card title="React">
      <p>Props Example</p>
    </Card>
  );
}
```

| Best Practice        | Notes                       |
| -------------------- | --------------------------- |
| Use destructuring    | Cleaner code                |
| Keep props minimal   | Easier maintenance          |
| Avoid deep drilling  | Use Context/store if needed |
| Use meaningful names | Better readability          |
| Keep props immutable | Never modify props directly |

---

## 📌 State

State stores dynamic data that updates and re-renders the UI in React.

| State Feature     | Purpose                     | Example                    |
| ----------------- | --------------------------- | -------------------------- |
| `useState()`      | Create local state          | `useState(0)`              |
| State Update      | Change UI dynamically       | `setCount(count + 1)`      |
| Re-rendering      | Update component UI         | State change               |
| Functional Update | Update using previous value | `setCount(prev => prev+1)` |
| Object State      | Store objects               | `setUser({...})`           |
| Array State       | Store arrays                | `setItems([...items])`     |
| Derived State     | Calculate from existing     | `items.length`             |
| Local State       | Component-specific state    | Form input                 |
| Global State      | Shared application state    | Auth/cart store            |

| State Type        | Example                          |
| ----------------- | -------------------------------- |
| String            | `useState("")`                   |
| Number            | `useState(0)`                    |
| Boolean           | `useState(false)`                |
| Null              | `useState(null)`                 |
| Undefined         | `useState(undefined)`            |
| Array             | `useState([])`                   |
| Object            | `useState({})`                   |
| Nested Object     | `useState({ user: {} })`         |
| Array of Objects  | `useState([{ id: 1 }])`          |
| Date              | `useState(new Date())`           |
| Function          | `useState(() => calculate())`    |
| Enum/String Union | `useState("loading")`            |
| Multiple Values   | `useState({ name: "", age: 0 })` |

```jsx
import { useState } from "react";

export default function Counter() {
  const [count, setCount] = useState(0);

  return <button onClick={() => setCount(count + 1)}>Count: {count}</button>;
}
```

| Part       | Meaning                  | Explanation                     |
| ---------- | ------------------------ | ------------------------------- |
| `count`    | Current state value      | Current stored value            |
| `setCount` | Function to update state | Changes the stored value        |
| `useState` | React state hook         | Creates memory inside component |

### State Flow

```txt
User Action
      ↓
Update State
      ↓
Component Re-renders
      ↓
Updated UI Displayed
```

| Best Practice          | Notes                      |
| ---------------------- | -------------------------- |
| Keep state minimal     | Reduce unnecessary renders |
| Use functional updates | Safer async updates        |
| Avoid direct mutation  | Always create new values   |
| Split unrelated state  | Better readability         |
| Lift state when needed | Share state properly       |

### Local vs Global State

| State Type   | Scope                    | Best For             | Example           |
| ------------ | ------------------------ | -------------------- | ----------------- |
| Local State  | Single component only    | Small UI logic       | Modal toggle      |
| Global State | Shared across components | App-wide shared data | Auth, cart, theme |

```jsx
// Local State
const [open, setOpen] = useState(false);

// Global State Example
const user = useAuthStore((state) => state.user);
```

---

## 📌 Event Handling

Event handling is used to respond to user interactions in React.

| Event Type     | Purpose            | Example                   |
| -------------- | ------------------ | ------------------------- |
| `onClick`      | Button click       | `onClick={handleClick}`   |
| `onChange`     | Input value change | `onChange={handleInput}`  |
| `onSubmit`     | Form submit        | `onSubmit={handleSubmit}` |
| `onKeyDown`    | Keyboard press     | `onKeyDown={handleKey}`   |
| `onMouseEnter` | Mouse hover        | `onMouseEnter={show}`     |
| `onMouseLeave` | Mouse leave        | `onMouseLeave={hide}`     |
| `onFocus`      | Input focus        | `onFocus={handleFocus}`   |
| `onBlur`       | Input blur         | `onBlur={handleBlur}`     |

| Event Feature    | Purpose                     | Example                     |
| ---------------- | --------------------------- | --------------------------- |
| Event Object     | Access event details        | `event.target.value`        |
| Arrow Function   | Pass parameters             | `onClick={() => save(id)}`  |
| Prevent Default  | Stop default browser action | `event.preventDefault()`    |
| Stop Propagation | Stop event bubbling         | `event.stopPropagation()`   |
| Synthetic Event  | React wrapper for events    | Cross-browser compatibility |

```jsx
export default function App() {
  const handleClick = () => {
    alert("Button Clicked");
  };

  const handleSubmit = (event) => {
    event.preventDefault();
    console.log("Form Submitted");
  };

  return (
    <form onSubmit={handleSubmit}>
      <button onClick={handleClick}>Click Me</button>
    </form>
  );
}
```

### Event Flow

```txt
User Action
      ↓
React Event Triggered
      ↓
Event Handler Function Runs
      ↓
Update State / UI
```

| Best Practice            | Notes                         |
| ------------------------ | ----------------------------- |
| Use separate handlers    | Cleaner code                  |
| Prevent default wisely   | Avoid unwanted reloads        |
| Avoid inline heavy logic | Better readability            |
| Use meaningful names     | `handleSubmit`, `handleClick` |
| Update state carefully   | Prevent unnecessary renders   |

---

## 📌 Conditional Rendering

Conditional rendering displays UI based on conditions or state values.

| Method           | Purpose                 | Common Usage           | Example                  |
| ---------------- | ----------------------- | ---------------------- | ------------------------ |
| `if/else`        | Multiple conditions     | Role-based UI          | `if (isAdmin)`           |
| Ternary Operator | Inline condition        | Auth UI                | `isLogin ? A : B`        |
| `&&` Operator    | Render if true          | Modal toggle           | `show && <Modal />`      |
| Early Return     | Stop rendering early    | Loading/error handling | `if (!user) return null` |
| `switch`         | Multiple case rendering | Status-based UI        | `switch(status)`         |

```jsx
export default function App() {
  const isLogin = true;
  const showModal = true;

  return (
    <div>
      {isLogin ? <h1>Dashboard</h1> : <h1>Login</h1>}

      {showModal && <p>Modal Open</p>}
    </div>
  );
}
```

| Best Practice             | Notes                    |
| ------------------------- | ------------------------ |
| Use ternary for simple UI | Cleaner inline rendering |
| Use `&&` for toggles      | Compact conditional UI   |
| Avoid nested ternaries    | Hard to read             |
| Use early return          | Cleaner component logic  |
| Keep conditions readable  | Better maintainability   |

---

## 📌 Lists & Keys

Lists are used to render multiple items dynamically in React using array methods like `map()`.

| Concept       | Purpose                  | Example                | Real-World Usage  |
| ------------- | ------------------------ | ---------------------- | ----------------- |
| `map()`       | Render array items       | `items.map()`          | Product lists     |
| `key`         | Unique item identifier   | `key={item.id}`        | Stable UI updates |
| Filtered List | Render filtered items    | `items.filter().map()` | Search results    |
| Nested Lists  | Render child collections | Comments/replies       | Chat systems      |
| Empty State   | Handle no data UI        | `items.length === 0`   | Empty dashboards  |

```jsx
const products = [
  { id: 1, name: "Laptop" },
  { id: 2, name: "Phone" },
];

export default function App() {
  return (
    <ul>
      {products.map((product) => (
        <li key={product.id}>{product.name}</li>
      ))}
    </ul>
  );
}
```

| Best Practice              | Notes                    |
| -------------------------- | ------------------------ |
| Use unique keys            | Prevent rendering issues |
| Prefer database IDs        | Stable unique values     |
| Avoid array index key      | UI issues on reordering  |
| Keep list components small | Better maintainability   |
| Use conditional rendering  | Handle empty/loading UI  |

| Real-World Usage | Example        |
| ---------------- | -------------- |
| E-commerce       | Product grids  |
| Dashboards       | Data tables    |
| Social Media     | Posts/comments |
| Messaging Apps   | Chat lists     |

---

## 📌 Forms

Forms are used to collect and manage user input in React applications.

| Form Concept           | Purpose                    | Example                   | Real-World Usage   |
| ---------------------- | -------------------------- | ------------------------- | ------------------ |
| Controlled Component   | React controls input state | `value={name}`            | Login forms        |
| Uncontrolled Component | DOM handles input state    | `useRef()`                | Simple forms       |
| `onChange`             | Update input state         | `onChange={handleChange}` | Live typing        |
| `onSubmit`             | Handle form submission     | `onSubmit={handleSubmit}` | Registration forms |
| Multiple Inputs        | Manage many fields         | `name="email"`            | Profile forms      |
| Validation             | Validate user data         | Required/email checks     | Checkout forms     |
| Form Reset             | Clear form values          | `setForm(initialState)`   | Search/reset forms |

```jsx
import { useState } from "react";

export default function App() {
  const [form, setForm] = useState({
    email: "",
  });

  const handleChange = (e) => {
    setForm({
      ...form,
      [e.target.name]: e.target.value,
    });
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    console.log(form);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        type="email"
        name="email"
        value={form.email}
        onChange={handleChange}
      />

      <button type="submit">Submit</button>
    </form>
  );
}
```

| Common Input Type | Example           |
| ----------------- | ----------------- |
| Text Input        | Name, username    |
| Email Input       | Login email       |
| Password Input    | Authentication    |
| Checkbox          | Accept terms      |
| Radio Button      | Gender selection  |
| Select Dropdown   | Country/category  |
| Textarea          | Comments/messages |

| Best Practice            | Notes                     |
| ------------------------ | ------------------------- |
| Use controlled forms     | Predictable form handling |
| Keep form state grouped  | Easier management         |
| Validate before submit   | Prevent invalid data      |
| Use reusable inputs      | Cleaner form architecture |
| Show validation feedback | Better UX                 |

- Controlled components use React state to manage form values, while uncontrolled components use the DOM directly.

| Feature           | Controlled  | Uncontrolled |
| ----------------- | ----------- | ------------ |
| Data Source       | React state | DOM          |
| Validation        | Easier      | Harder       |
| Real-time Updates | Yes         | Limited      |
| Code Complexity   | More        | Less         |
| Predictability    | High        | Lower        |

---

## 📌 React Hooks

Hooks are special React functions that add state, lifecycle, and other React features to functional components.

| Hook          | Purpose                          | Example                     | Real-World Usage    |
| ------------- | -------------------------------- | --------------------------- | ------------------- |
| `useState`    | Manage component state           | `useState(0)`               | Counters, forms     |
| `useEffect`   | Handle side effects              | `useEffect(() => {})`       | API calls           |
| `useRef`      | Access DOM / store mutable value | `useRef()`                  | Input focus         |
| `useContext`  | Access global context            | `useContext(AuthContext)`   | Theme/auth          |
| `useMemo`     | Memoize expensive values         | `useMemo(() => {}, [])`     | Large calculations  |
| `useCallback` | Memoize functions                | `useCallback(() => {}, [])` | Optimized callbacks |
| `useReducer`  | Complex state management         | `useReducer(reducer,{})`    | Large forms         |
| Custom Hook   | Reusable hook logic              | `useAuth()`                 | Shared app logic    |

| Hook Rule                        | Notes                   |
| -------------------------------- | ----------------------- |
| Use hooks at top level           | Avoid conditional hooks |
| Use only inside components/hooks | React rule              |
| Prefix custom hooks with `use`   | `useFetch()`            |
| Keep hooks focused               | Better maintainability  |

```jsx
import { useState } from "react";

export default function Counter() {
  const [count, setCount] = useState(0);

  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
```

| Hook          | Real-World Usage             |
| ------------- | ---------------------------- |
| `useState`    | Forms, toggles, counters     |
| `useEffect`   | API calls, timers, listeners |
| `useRef`      | Input focus, DOM access      |
| `useContext`  | Theme, auth, cart state      |
| `useMemo`     | Expensive calculations       |
| `useCallback` | Optimized event handlers     |
| `useReducer`  | Complex forms/state logic    |
| Custom Hook   | Shared reusable logic        |

---

## 📌 useEffect

`useEffect` is used to handle side effects in React components.

| Feature               | Purpose                       | Example                   | Real-World Usage  |
| --------------------- | ----------------------------- | ------------------------- | ----------------- |
| Side Effects          | Run external logic            | API calls                 | Fetch users       |
| Dependency Array      | Control effect execution      | `[count]`                 | Search updates    |
| Empty Dependency `[]` | Run once on mount             | `useEffect(() => {}, [])` | Initial API fetch |
| No Dependency Array   | Run on every render           | `useEffect(() => {})`     | Debugging         |
| Cleanup Function      | Cleanup before unmount/update | `return () => {}`         | Remove listeners  |
| State-based Effect    | Run on state change           | `[search]`                | Live filtering    |

| Dependency Array | Meaning                | Real Example                   |
| ---------------- | ---------------------- | ------------------------------ |
| `[]`             | Run only once on mount | Fetch users on page load       |
| `[value]`        | Run when value changes | Search API when input changes  |
| No array         | Run on every render    | Debugging/logging every render |

```jsx
// [] → Run once
useEffect(() => {
  fetchUsers();
}, []);

// [search] → Run when search changes
useEffect(() => {
  searchProducts(search);
}, [search]);
```

```jsx
import { useEffect, useState } from "react";

export default function App() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log("Count Changed");
  }, [count]);

  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
```

```jsx
// Cleanup Example
useEffect(() => {
  const timer = setInterval(() => {
    console.log("Running");
  }, 1000);

  return () => {
    clearInterval(timer);
  };
}, []);
```

| Best Practice                 | Notes                   |
| ----------------------------- | ----------------------- |
| Use dependency array properly | Avoid unnecessary runs  |
| Cleanup side effects          | Prevent memory leaks    |
| Separate multiple effects     | Cleaner logic           |
| Avoid heavy logic inside      | Better performance      |
| Use for external effects      | APIs, timers, listeners |

| Real-World Usage | Example                |
| ---------------- | ---------------------- |
| API Fetching     | Fetch products/users   |
| Timers           | Countdown timer        |
| Search Feature   | Live search API        |
| Event Listeners  | Window resize tracking |
| Chat Systems     | Socket connection      |

---

## 📌 API Calls

API calls are used to fetch or send data between React applications and servers.

| Concept        | Purpose                 | Example               | Real-World Usage   |
| -------------- | ----------------------- | --------------------- | ------------------ |
| `fetch()`      | Native API request      | `fetch("/api/users")` | Get products/users |
| `axios`        | Popular HTTP library    | `axios.get()`         | Production APIs    |
| `GET` Request  | Fetch data              | Product list          | Dashboards         |
| `POST` Request | Send data               | Login/signup          | Forms              |
| Loading State  | Show loading UI         | `isLoading`           | Spinners/loaders   |
| Error Handling | Handle failed requests  | `try/catch`           | Error messages     |
| `useEffect()`  | Run API on mount/update | `useEffect(() => {})` | Initial data fetch |
| Async/Await    | Handle async code       | `await fetch()`       | Cleaner API logic  |

| HTTP Method | Purpose     | Example Usage  |
| ----------- | ----------- | -------------- |
| `GET`       | Fetch data  | Products/users |
| `POST`      | Create data | Signup form    |
| `PUT`       | Update data | Edit profile   |
| `DELETE`    | Remove data | Delete product |

```jsx
import { useEffect, useState } from "react";

export default function App() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    async function fetchUsers() {
      const response = await fetch(
        "https://jsonplaceholder.typicode.com/users",
      );

      const data = await response.json();

      setUsers(data);
    }

    fetchUsers();
  }, []);

  return (
    <ul>
      {users.map((user) => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}
```

```jsx
// Axios Example
import axios from "axios";
import { useEffect, useState } from "react";

export default function App() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    async function fetchUsers() {
      try {
        const response = await axios.get(
          "https://jsonplaceholder.typicode.com/users",
        );

        setUsers(response.data);
      } catch (error) {
        console.log(error);
      }
    }

    fetchUsers();
  }, []);

  return (
    <ul>
      {users.map((user) => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}
```

| Best Practice              | Notes                |
| -------------------------- | -------------------- |
| Use loading state          | Better UX            |
| Handle API errors          | Prevent app crashes  |
| Use async/await            | Cleaner async code   |
| Keep API logic separated   | Use services/hooks   |
| Cleanup requests if needed | Prevent memory leaks |

### Infinite Loop Issues

```jsx
// ❌ Infinite Loop
useEffect(() => {
  setCount(count + 1);
});

// ✅ Correct
useEffect(() => {
  setCount((prev) => prev + 1);
}, []);
```

```jsx
// ❌ Function Dependency Issue
useEffect(() => {
  fetchData();
}, [fetchData]);

// ✅ Fix with useCallback
const fetchData = useCallback(() => {
  console.log("Fetch");
}, []);
```

---

## 📌 useRef

`useRef` is used to access DOM elements or store mutable values without re-rendering the component.

| Feature                 | Purpose                        | Example               | Real-World Usage         |
| ----------------------- | ------------------------------ | --------------------- | ------------------------ |
| DOM Access              | Access HTML elements           | `inputRef.current`    | Input focus              |
| Mutable Value Store     | Store values without re-render | `ref.current = value` | Previous value storage   |
| Persist Between Renders | Keep value across renders      | Timer ID storage      | Intervals/timeouts       |
| Avoid Re-render         | Update value silently          | `ref.current++`       | Performance optimization |

| Common Usage   | Example                    |
| -------------- | -------------------------- |
| Input Focus    | `inputRef.current.focus()` |
| Scroll Element | `scrollIntoView()`         |
| Store Timer ID | `timerRef.current`         |
| Previous State | `prevValue.current`        |

```jsx
import { useEffect, useRef } from "react";

export default function App() {
  const canvasRef = useRef();

  useEffect(() => {
    const canvas = canvasRef.current;
    const ctx = canvas.getContext("2d");

    ctx.fillStyle = "blue";
    ctx.fillRect(50, 50, 150, 100);
  }, []);

  return <canvas ref={canvasRef} />;
}
```

```jsx
// Store Previous Value
const prevCount = useRef();

useEffect(() => {
  prevCount.current = count;
}, [count]);
```

| `useRef` vs `useState` | `useRef` | `useState` |
| ---------------------- | -------- | ---------- |
| Re-render Component    | No       | Yes        |
| Store Mutable Value    | Yes      | Yes        |
| DOM Access             | Yes      | No         |

| Best Practice             | Notes                        |
| ------------------------- | ---------------------------- |
| Use refs for DOM access   | Focus, scroll, media control |
| Avoid replacing state     | `useRef` doesn't re-render   |
| Use for persistent values | Timers, previous values      |
| Keep refs minimal         | Avoid excessive direct DOM   |

- Store mutable value without re-rendering

| Use Case              | Example                  |
| --------------------- | ------------------------ |
| Access DOM Element    | Focus Input              |
| Previous Value        | Track Previous State     |
| Timer ID              | setTimeout / setInterval |
| AbortController       | Cancel API Request       |
| WebSocket Instance    | Store Socket Connection  |
| Render Count          | Debugging                |
| Scroll Position       | Infinite Scroll          |
| Video/Audio Control   | Play, Pause              |
| Third-Party Libraries | Charts, Maps, GSAP       |

```tsx
const sectionRef = useRef<HTMLDivElement>(null);

function scrollToContact() {
  sectionRef.current?.scrollIntoView({
    behavior: "smooth",
  });
}

return (
  <div>
    <button onClick={scrollToContact}>Contact Us</button>
    <div ref={sectionRef}>Contact Section</div>
  </div>
);
```

---

## 📌 Context API

Context API is used to share global data across components without props drilling.

| Concept              | Purpose                    | Example                      | Real-World Usage     |
| -------------------- | -------------------------- | ---------------------------- | -------------------- |
| `createContext()`    | Create global context      | `createContext()`            | Theme/auth           |
| `Provider`           | Share data with components | `<AuthProvider>`             | App-wide state       |
| `useContext()`       | Access context data        | `useContext(AuthContext)`    | User/theme access    |
| Global State         | Shared application data    | Auth, language, cart         | Large applications   |
| Avoid Props Drilling | Skip deep prop passing     | Parent → nested child access | Cleaner architecture |

```jsx
import { createContext, useContext } from "react";

const ThemeContext = createContext();

function Child() {
  const theme = useContext(ThemeContext);

  return <h1>{theme}</h1>;
}

export default function App() {
  return (
    <ThemeContext.Provider value="dark">
      <Child />
    </ThemeContext.Provider>
  );
}
```

### Context API Flow

```txt
Create Context
      ↓
Wrap with Provider
      ↓
Share Global Data
      ↓
Access with useContext()
```

| Best Practice            | Notes                         |
| ------------------------ | ----------------------------- |
| Use for shared data      | Theme, auth, language         |
| Avoid excessive context  | Can cause unnecessary renders |
| Split contexts logically | Better scalability            |
| Use custom hooks         | Cleaner context access        |
| Keep local state local   | Avoid overusing global state  |

| Real-World Usage | Example             |
| ---------------- | ------------------- |
| Theme Switching  | Dark/light mode     |
| Authentication   | Logged-in user data |
| Shopping Cart    | Shared cart state   |
| Language Switch  | Multi-language apps |
| Permissions      | Role-based access   |

### Providers in React

- A React app can have multiple providers.
- Each provider manages different global data.

| Provider Type     | Purpose                | Real-World Usage |
| ----------------- | ---------------------- | ---------------- |
| Theme Provider    | Theme state            | Dark/light mode  |
| Auth Provider     | User authentication    | Login system     |
| Cart Provider     | Shopping cart data     | E-commerce       |
| Language Provider | Multi-language support | i18n apps        |
| Query Provider    | API caching/state      | React Query      |

```jsx
<AuthProvider>
  <ThemeProvider>
    <CartProvider>
      <App />
    </CartProvider>
  </ThemeProvider>
</AuthProvider>
```

---

## 📌 Component Communication

Component communication is the process of sharing data or actions between React components.

| Communication Type   | Purpose                   | Example                  | Real-World Usage |
| -------------------- | ------------------------- | ------------------------ | ---------------- |
| Parent → Child       | Pass data using props     | `<Card title="React" />` | Product cards    |
| Child → Parent       | Send data using callbacks | `onClick={handleClick}`  | Form submit      |
| Sibling → Sibling    | Share data via parent     | Shared state             | Tabs/modals      |
| Global Communication | Share app-wide data       | Context/Redux            | Auth/cart/theme  |

```jsx
// Parent → Child
function Child({ message }) {
  return <h1>{message}</h1>;
}

export default function App() {
  return <Child message="Hello" />;
}
```

```jsx
// Child → Parent
function Child({ onSend }) {
  return <button onClick={() => onSend("Data")}>Send</button>;
}

export default function App() {
  const handleData = (data) => {
    console.log(data);
  };

  return <Child onSend={handleData} />;
}
```

```jsx
// Sibling Communication
function App() {
  const [count, setCount] = useState(0);

  return (
    <>
      <Counter count={count} />
      <Buttons setCount={setCount} />
    </>
  );
}
```

| Common Communication Method | Usage                 |
| --------------------------- | --------------------- |
| Props                       | Parent → Child        |
| Callback Functions          | Child → Parent        |
| Lifted State                | Sibling communication |
| Context API                 | Global communication  |
| Redux/Zustand               | Large global state    |

| Best Practice              | Notes                        |
| -------------------------- | ---------------------------- |
| Keep state close to usage  | Better maintainability       |
| Avoid deep prop drilling   | Use Context/store            |
| Use callbacks clearly      | Predictable child actions    |
| Lift shared state wisely   | Better component structure   |
| Use global state minimally | Avoid unnecessary complexity |

---

## 📌 Styling in React

React supports multiple styling approaches for building reusable and scalable UI.

| Styling Method        | Purpose                 | Example                    | Real-World Usage    |
| --------------------- | ----------------------- | -------------------------- | ------------------- |
| CSS File              | Global/component styles | `import "./App.css"`       | Small projects      |
| Inline Styles         | Dynamic styles          | `style={{ color: "red" }}` | Conditional styling |
| CSS Modules           | Scoped component styles | `styles.card`              | Large applications  |
| SCSS/SASS             | Advanced CSS features   | Variables/nesting          | Scalable styling    |
| Styled Components     | CSS-in-JS styling       | `styled.button`` `         | Dynamic themes      |
| Tailwind CSS          | Utility-first CSS       | `className="flex gap-4"`   | Modern React apps   |
| Conditional Classes   | Dynamic class switching | `isActive ? "active" : ""` | Tabs/buttons        |
| `clsx` / `classnames` | Manage dynamic classes  | `clsx(active && "show")`   | Complex UI states   |

```jsx
// CSS File
import "./App.css";
export default function App() {
  return <h1 className="title">React</h1>;
}

// Inline Style
<h1 style={{ color: "blue" }}>Hello</h1>;

// CSS Module
import styles from "./Card.module.css";
<div className={styles.card}>Card</div>;

// Tailwind CSS
<button className="bg-blue-500 text-white px-4 py-2">Button</button>;
```

| Best Practice                | Notes                       |
| ---------------------------- | --------------------------- |
| Use CSS Modules/Tailwind     | Better scalability          |
| Avoid excessive inline CSS   | Harder maintenance          |
| Keep styles component-based  | Easier reusability          |
| Use utility helpers          | Cleaner conditional classes |
| Separate global/local styles | Better architecture         |

| Real-World Usage | Styling Method     |
| ---------------- | ------------------ |
| Dashboard UI     | Tailwind CSS       |
| Design Systems   | Styled Components  |
| Enterprise Apps  | CSS Modules + SCSS |
| Dynamic Themes   | CSS-in-JS          |

---

## 📌 React Router

React Router is used for navigation and routing in React applications.

| Feature          | Purpose                     | Example                      | Real-World Usage     |
| ---------------- | --------------------------- | ---------------------------- | -------------------- |
| `BrowserRouter`  | Enable routing              | `<BrowserRouter>`            | SPA navigation       |
| `Routes`         | Group route definitions     | `<Routes>`                   | App routes           |
| `Route`          | Define route path/component | `<Route path="/" />`         | Page navigation      |
| `Link`           | Navigate without reload     | `<Link to="/about" />`       | Navbar links         |
| `NavLink`        | Active navigation links     | `<NavLink />`                | Sidebar menus        |
| Dynamic Route    | Dynamic URL params          | `/product/:id`               | Product pages        |
| `useParams()`    | Access route params         | `const { id } = useParams()` | Details pages        |
| `useNavigate()`  | Navigate programmatically   | `navigate("/login")`         | Redirect after login |
| Nested Routes    | Child route structure       | Dashboard routes             | Admin panels         |
| Protected Routes | Restrict route access       | Auth-based routes            | Private pages        |
| 404 Route        | Handle missing pages        | `path="*"`                   | Error pages          |

```bash
npm install react-router-dom
```

```jsx
import { BrowserRouter, Routes, Route, Link } from "react-router-dom";

function Home() {
  return <h1>Home</h1>;
}

function About() {
  return <h1>About</h1>;
}

export default function App() {
  return (
    <BrowserRouter>
      <nav>
        <Link to="/">Home</Link>
        <Link to="/about">About</Link>
      </nav>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </BrowserRouter>
  );
}
```

```jsx
// Dynamic Route
<Route path="/product/:id" element={<Product />} />
```

```jsx
// useParams
const { id } = useParams();
```

```jsx
// useNavigate
const navigate = useNavigate();

navigate("/dashboard");
```

| RR Components | Purpose           |
| ------------- | ----------------- |
| BrowserRouter | Router Provider   |
| Routes        | Route Container   |
| Route         | Route Definition  |
| Link          | Navigation        |
| NavLink       | Active Navigation |
| Outlet        | Nested Routes     |
| Navigate      | Redirect          |

| Property      | Purpose                     | Example                        |
| ------------- | --------------------------- | ------------------------------ |
| path          | URL Pattern                 | `path="/users"`                |
| element       | Component To Render         | `element={<Users />}`          |
| index         | Default Child Route         | `index`                        |
| children      | Nested Routes               | `<Route><Route /></Route>`     |
| loader        | Fetch Data Before Render    | `loader={getUsers}`            |
| action        | Handle Form Submission      | `action={saveUser}`            |
| errorElement  | Error UI                    | `errorElement={<ErrorPage />}` |
| caseSensitive | Case Sensitive URL Matching | `caseSensitive`                |

### Default Child Route

```tsx
<Route path="/settings" element={<Settings />}>
  <Route index element={<Profile />} />
</Route>
```

```txt
/settings
↓
Profile (Default)
```

```tsx
// loader
<Route path="/users" loader={getUsers} element={<Users />} />
```

### URL Handling In React Router

| Feature      | Hook                | Example URL     |
| ------------ | ------------------- | --------------- |
| Route Params | `useParams()`       | `/users/123`    |
| Query Params | `useSearchParams()` | `/users?page=1` |
| Current URL  | `useLocation()`     | `/users?page=1` |
| Navigation   | `useNavigate()`     | Redirect User   |

```txt
>> Route Params: Used for resource identifiers.

/users/123
/products/50
/orders/10
```

```tsx
const { id } = useParams();
```

```txt
>> Query Parameters: Used for UI state.

/users?page=1
/users?search=john
/users?sort=name
/users?status=active
```

```tsx
const [params] = useSearchParams();
const page = params.get("page");

// Update
setSearchParams({
  page: "2",
});
```

```txt
>> Multiple Filters: URL

/products?search=iphone&category=mobile&sort=price&page=2
```

```tsx
const search = params.get("search");
const category = params.get("category");
const sort = params.get("sort");
```

| Best Practice             | Notes                     |
| ------------------------- | ------------------------- |
| Use route-based structure | Better scalability        |
| Keep routes organized     | Easier maintenance        |
| Use protected routes      | Secure private pages      |
| Lazy load routes          | Better performance        |
| Use nested layouts        | Cleaner routing structure |

---

## 📌 API Handling

API handling is used to fetch, send, update, and manage server data in React applications.

| Concept               | Purpose                 | Example                        | Real-World Usage     |
| --------------------- | ----------------------- | ------------------------------ | -------------------- |
| `fetch()`             | Native API requests     | `fetch("/api/users")`          | Basic API handling   |
| `axios`               | HTTP request library    | `axios.get()`                  | Production APIs      |
| `GET` Request         | Fetch data              | Product/user list              | Dashboards           |
| `POST` Request        | Send data               | Login/signup                   | Forms                |
| `PUT/PATCH`           | Update data             | Edit profile                   | Settings page        |
| `DELETE`              | Remove data             | Delete item                    | Admin panels         |
| Loading State         | Show loading UI         | `isLoading`                    | Spinners/loaders     |
| Error Handling        | Handle failed requests  | `try/catch`                    | Error messages       |
| `useEffect()`         | Run API on mount/update | `useEffect(() => {})`          | Initial fetch        |
| Async/Await           | Handle async operations | `await fetch()`                | Cleaner async logic  |
| AbortController       | Cancel API requests     | `controller.abort()`           | Prevent memory leaks |
| Environment Variables | Store API URLs/secrets  | `import.meta.env.VITE_API_URL` | Production apps      |

| HTTP Method | Purpose        | Example Usage  |
| ----------- | -------------- | -------------- |
| `GET`       | Fetch data     | Products/users |
| `POST`      | Create data    | Signup form    |
| `PUT`       | Replace data   | Edit profile   |
| `PATCH`     | Partial update | Update status  |
| `DELETE`    | Remove data    | Delete product |

```jsx
import { useEffect, useState } from "react";

export default function App() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    async function fetchUsers() {
      try {
        const response = await fetch(
          "https://jsonplaceholder.typicode.com/users",
        );

        const data = await response.json();

        setUsers(data);
      } catch (error) {
        console.log(error);
      }
    }

    fetchUsers();
  }, []);

  return (
    <ul>
      {users.map((user) => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}
```

```jsx
// Axios Example
const response = await axios.get("/api/users");
```

```jsx
// AbortController Example
useEffect(() => {
  const controller = new AbortController();

  fetch("/api/users", {
    signal: controller.signal,
  });

  return () => controller.abort();
}, []);
```

| Best Practice               | Notes                  |
| --------------------------- | ---------------------- |
| Use loading & error states  | Better UX              |
| Separate API logic          | Use services/hooks     |
| Use async/await             | Cleaner async handling |
| Cancel unnecessary requests | Prevent memory leaks   |
| Store API URLs in `.env`    | Safer configuration    |

---

## 📌 State Management

State management is used to store, update, and share application data across React components.

| State Type    | Purpose                  | Example           | Real-World Usage   |
| ------------- | ------------------------ | ----------------- | ------------------ |
| Local State   | Component-specific state | `useState()`      | Form inputs        |
| Global State  | Shared app-wide state    | Auth/cart/theme   | Large applications |
| Context API   | Built-in global sharing  | `createContext()` | Theme/auth         |
| Redux Toolkit | Centralized state store  | Redux store       | Enterprise apps    |
| Zustand       | Lightweight global store | `create()`        | Modern React apps  |
| useReducer    | Complex local state      | `useReducer()`    | Multi-step forms   |

| Tool / Library | Type             | Included in React? | Best For                  |
| -------------- | ---------------- | ------------------ | ------------------------- |
| `useState`     | React Hook       | Yes                | Simple local state        |
| `useReducer`   | React Hook       | Yes                | Complex component logic   |
| Context API    | React Feature    | Yes                | Small/medium global state |
| Redux Toolkit  | External Library | No                 | Large scalable apps       |
| Zustand        | External Library | No                 | Minimal global state      |

```jsx
// Local State
const [count, setCount] = useState(0);

// Context API
const ThemeContext = createContext();

// Zustand Store
const useStore = create((set) => ({
  count: 0,
}));
```

```bash
# Install Redux Toolkit
npm install @reduxjs/toolkit react-redux

# Install Zustand
npm install zustand
```

| Best Practice                  | Notes                    |
| ------------------------------ | ------------------------ |
| Use local state first          | Simpler architecture     |
| Avoid unnecessary global state | Prevent complexity       |
| Split stores by feature        | Better scalability       |
| Keep state minimal             | Reduce re-renders        |
| Use Context for small apps     | Lightweight global state |

### Redux

| Redux Part      | Simple Meaning                   | Example                   |
| --------------- | -------------------------------- | ------------------------- |
| Store           | Global storage box               | Entire app data           |
| Slice           | One section of global state      | Cart slice, auth slice    |
| State           | Stored data                      | `count: 0`                |
| Reducer         | Function that updates state      | Increase/decrease counter |
| Action          | Instruction to change state      | `increment()`             |
| `useSelector()` | Read data from store             | Get cart items/count      |
| `useDispatch()` | Send update instruction          | Add/remove product        |
| `Provider`      | Makes store available everywhere | Wrap entire React app     |

- Simple Redux Flow

```txt
Click Button
    ↓
Dispatch Action
    ↓
Reducer Updates State
    ↓
Store Updates
    ↓
UI Re-renders
```

### Compare

| Libraries Comparison | Context API (React)    | Zustand                   | Redux                 |
| -------------------- | ---------------------- | ------------------------- | --------------------- |
| Difficulty           | Easy                   | Easy                      | Hard                  |
| Setup Effort         | Very low               | Low                       | High                  |
| Boilerplate          | Minimal                | Minimal                   | High                  |
| Performance          | Good (small apps)      | Very good                 | Very good             |
| Scalability          | Low–Medium             | Medium–High               | Very High             |
| Best Use Case        | Small apps, auth/theme | Medium apps, global state | Large enterprise apps |
| Learning Curve       | Very easy              | Easy                      | Steep                 |
| Middleware Support   | Limited                | Basic                     | Advanced              |
| DevTools             | Basic                  | Limited                   | Excellent             |
| Community Adoption   | High                   | Growing                   | Very high             |

#### Context API (Built-in React)

```js
// CartContext.js
import React, { createContext, useContext, useState } from "react";

const CartContext = createContext();

export function CartProvider({ children }) {
  const [cart, setCart] = useState([]);
  const addItem = (item) => {
    setCart([...cart, item]);
  };

  return (
    <CartContext.Provider value={{ cart, addItem }}>
      {children}
    </CartContext.Provider>
  );
}

export const useCart = () => useContext(CartContext);

// Usage in Component
import { useCart } from "./CartContext";

function Product() {
  const { cart, addItem } = useCart();

  return (
    <div>
      <button onClick={() => addItem("Apple")}>Add Apple</button>
      <p>Cart Count: {cart.length}</p>
    </div>
  );
}
```

#### Redux (Predictable Global Store)

```js
// cartSlice.js
import { createSlice } from "@reduxjs/toolkit";

const cartSlice = createSlice({
  name: "cart",
  initialState: [],
  reducers: {
    addItem: (state, action) => {
      state.push(action.payload);
    },
  },
});

export const { addItem } = cartSlice.actions;
export default cartSlice.reducer;

// store.js
import { configureStore } from "@reduxjs/toolkit";
import cartReducer from "./cartSlice";

export const store = configureStore({
  reducer: {
    cart: cartReducer,
  },
});

// Usage in Component
import { useSelector, useDispatch } from "react-redux";
import { addItem } from "./cartSlice";

function Product() {
  const cart = useSelector((state) => state.cart);
  const dispatch = useDispatch();

  return (
    <div>
      <button onClick={() => dispatch(addItem("Apple"))}>Add Apple</button>

      <p>Cart Count: {cart.length}</p>
    </div>
  );
}
```

#### Zustand (Minimal & Fast Store)

```js
// store.js
import { create } from "zustand";

const useCartStore = create((set) => ({
  cart: [],
  addItem: (item) => set((state) => ({ cart: [...state.cart, item] })),
}));

export default useCartStore;

// Usage in Component
import useCartStore from "./store";

function Product() {
  const { cart, addItem } = useCartStore();

  return (
    <div>
      <button onClick={() => addItem("Apple")}>Add Apple</button>
      <p>Cart Count: {cart.length}</p>
    </div>
  );
}
```

### Lifting State Up

| Purpose  | Share state between multiple components |
| -------- | --------------------------------------- |
| Concept  | Move state to closest common parent     |
| Use When | Sibling components need same data       |

- SearchInput updates value, UserList needs value (Pass Data Via Props)

```txt
Parent
 ├── SearchInput
 └── UserList
```

```tsx
function UsersPage() {
  const [search, setSearch] = useState("");

  return (
    <>
      <SearchInput value={search} onChange={setSearch} />
      <UserList search={search} />
    </>
  );
}
```

```txt
Search + Table
Filters + Product List
Cart Items + Cart Total
Theme Toggle + Layout
Form Inputs + Preview
Modal State + Multiple Components
```

### Controlled Inputs

| Purpose         | React controls input value using state |
| --------------- | -------------------------------------- |
| Source of Truth | React State                            |
| Use When        | Forms, Validation, Dynamic UI          |

| Feature              | Context API | Lifting State Up |
| -------------------- | ----------- | ---------------- |
| Sibling Components   | ✅          | ✅               |
| Deep Component Tree  | ✅          | ❌               |
| Avoid Prop Drilling  | ✅          | ❌               |
| Small Global State   | ✅          | ⚠️               |
| Simple State Sharing | ⚠️          | ✅               |

---
