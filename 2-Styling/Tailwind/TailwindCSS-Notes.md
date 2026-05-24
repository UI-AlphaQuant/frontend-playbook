# 👉 Tailwind CSS Fundamentals

## 📌 Compare & Architecture

Tailwind CSS is a utility-first CSS framework for building custom UI using utility classes directly in markup.

| Feature     | Tailwind        | SCSS         |
| ----------- | --------------- | ------------ |
| Type        | Utility-first   | Preprocessor |
| Styling     | Utility classes | Custom CSS   |
| Flexibility | High            | Very High    |
| CSS Output  | Small (JIT)     | Depends      |

### Architecture

```txt
Content Scan → JIT Engine → Generate Utility CSS
```

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

| Layer      | Purpose         |
| ---------- | --------------- |
| Base       | Reset styles    |
| Components | Reusable styles |
| Utilities  | Utility classes |

---

### JIT Engine

Generates only used utility classes during development/build.

```html
<div class="w-[350px] bg-[#121212]"></div>
```

| Feature          | Usage          |
| ---------------- | -------------- |
| On-demand CSS    | Smaller bundle |
| Arbitrary Values | Custom values  |
| Fast Builds      | Better DX      |

---

### Advantages & Limitations

| Advantages               | Limitations                        |
| ------------------------ | ---------------------------------- |
| Fast UI development      | Long class lists                   |
| Small CSS output         | Noisy HTML                         |
| Highly customizable      | Learning curve                     |
| Responsive utilities     | Repeated utilities                 |
| Consistent design system | Complex components need extraction |

- Prefer reusable components
- Use theme tokens over many arbitrary values
- Keep class order consistent
- Avoid excessive `@apply`

```jsx
<div className="rounded-xl bg-white p-6 shadow">
  <button className="rounded bg-blue-600 px-4 py-2 text-white">Continue</button>
</div>
```

---

## 📌 Installation & Setup

Tailwind CSS can be used in static projects and modern frameworks using PostCSS or build tools like Vite.

| Setup                          | Install                                                   |
| ------------------------------ | --------------------------------------------------------- |
| Static / Basic                 | `npm install -D tailwindcss @tailwindcss/cli`             |
| React / Vue / Angular / NextJS | `npm install -D tailwindcss @tailwindcss/postcss postcss` |

### Init CSS File

```css
@import "tailwindcss";
```

### Static Project

Build CSS

```bash
npx @tailwindcss/cli -i ./src/input.css -o ./dist/output.css --watch
```

```html
<link rel="stylesheet" href="./dist/output.css" />
```

### React / Vue (Vite)

```bash
npm install -D tailwindcss @tailwindcss/vite
```

```js
// vite.config.js
import tailwindcss from "@tailwindcss/vite";

export default {
  plugins: [tailwindcss()],
};
```

### Angular

```bash
npm install tailwindcss @tailwindcss/postcss postcss --force
```

```json
// .postcssrc.json
{
  "plugins": {
    "@tailwindcss/postcss": {}
  }
}
```

### Next.js

```bash
npm install tailwindcss @tailwindcss/postcss postcss
```

```js
// postcss.config.mjs
export default {
  plugins: {
    "@tailwindcss/postcss": {},
  },
};
```

## 📌 Configuration

| File                 | Purpose                      | Details                                                               |
| -------------------- | ---------------------------- | --------------------------------------------------------------------- |
| `input.css`          | Tailwind import              | Main CSS entry file containing Tailwind directives/imports            |
| `postcss.config.*`   | PostCSS setup                | Processes Tailwind + other PostCSS plugins during build               |
| `vite.config.*`      | Vite plugin setup            | Enables Tailwind integration inside Vite build system                 |
| `tailwind.config.js` | Tailwind configuration       | Customize theme, colors, spacing, breakpoints, plugins, content paths |
| `package.json`       | Project dependencies/scripts | Stores Tailwind packages and build/dev commands                       |
| `dist/output.css`    | Generated CSS output         | Final compiled optimized Tailwind CSS file                            |
| `node_modules/`      | Installed packages           | Contains Tailwind and project dependencies                            |

```txt
Content Files → Scan Classes → JIT Engine → Generate CSS
```

| Step         | Purpose              |
| ------------ | -------------------- |
| Scan Content | Detect used classes  |
| JIT Generate | Create required CSS  |
| Build Output | Optimized CSS bundle |

- Use Vite for faster development
- Keep content paths accurate
- Avoid CDN for production
- Use theme extension instead of heavy custom CSS
- Keep Tailwind CSS in a single entry file

```jsx
export default function App() {
  return (
    <div className="flex min-h-screen items-center justify-center">
      <button className="rounded bg-blue-600 px-4 py-2 text-white">
        Login
      </button>
    </div>
  );
}
```

---

## 📌 Core Concepts

Tailwind CSS works using utility classes, variants.

### Utility System

Utility-first approach using small reusable classes.

```html
<div class="flex items-center gap-4 p-6"></div>
```

| Utility       | Usage            |
| ------------- | ---------------- |
| `p-4`         | Padding          |
| `m-4`         | Margin           |
| `flex`        | Flexbox          |
| `grid`        | Grid             |
| `text-lg`     | Typography       |
| `bg-blue-500` | Background color |

### Variants

Variants apply styles based on screen size or state.

```html
<button class="md:px-6 hover:bg-blue-700"></button>
```

| Variant           | Usage         |
| ----------------- | ------------- |
| `sm:` `md:` `lg:` | Responsive    |
| `hover:`          | Hover state   |
| `focus:`          | Focus state   |
| `active:`         | Active state  |
| `dark:`           | Dark mode     |
| `group-hover:`    | Parent state  |
| `peer-invalid:`   | Sibling state |

### Modern Features

Modern Tailwind supports dynamic utilities and selectors.

```html
<div class="w-[350px] data-[active=true]:bg-green-500"></div>
```

| Feature             | Usage                    |
| ------------------- | ------------------------ |
| Arbitrary Values    | `w-[350px]`              |
| Arbitrary Colors    | `bg-[#121212]`           |
| Arbitrary Selectors | `[&>*]:p-4`              |
| Data Variants       | `data-[open=true]:block` |
| Container Queries   | `@md:flex`               |

- Prefer utility composition
- Use responsive variants properly
- Avoid excessive arbitrary values
- Keep content paths accurate
- Reuse common utility patterns

```jsx
<div className="rounded-xl bg-white p-6 shadow md:flex md:items-center">
  <button className="mt-4 rounded bg-blue-600 px-4 py-2 text-white hover:bg-blue-700">
    Continue
  </button>
</div>
```

---

## 📌 Layout & Spacing Utilities

Tailwind provides utility classes for layout, spacing, alignment, sizing, and positioning.

### Display & Layout

```html
<div class="block hidden flex grid container"></div>
```

| Utility           | Usage                |
| ----------------- | -------------------- |
| `block`           | Block element        |
| `inline-block`    | Inline block         |
| `hidden`          | Hide element         |
| `flex`            | Flex layout          |
| `grid`            | Grid layout          |
| `container`       | Responsive container |
| `overflow-hidden` | Hide overflow        |
| `aspect-square`   | Aspect ratio         |

### Flexbox Utilities

```html
<div class="flex items-center justify-between gap-4"></div>
```

| Utility           | Usage          |
| ----------------- | -------------- |
| `flex-row`        | Horizontal     |
| `flex-col`        | Vertical       |
| `flex-wrap`       | Wrap items     |
| `items-center`    | Align items    |
| `justify-center`  | Center content |
| `justify-between` | Space between  |
| `gap-4`           | Spacing        |
| `grow`            | Flex grow      |

### Grid Utilities

```html
<div class="grid grid-cols-3 gap-4"></div>
```

| Utility              | Usage        |
| -------------------- | ------------ |
| `grid-cols-2`        | 2 columns    |
| `grid-cols-3`        | 3 columns    |
| `col-span-2`         | Column span  |
| `grid-rows-2`        | Grid rows    |
| `place-items-center` | Center items |
| `auto-cols-fr`       | Auto columns |
| `gap-4`              | Grid gap     |

### Spacing & Sizing

```html
<div class="m-4 p-6 w-full h-screen"></div>
```

| Utility     | Usage                |
| ----------- | -------------------- |
| `m-*`       | Margin               |
| `p-*`       | Padding              |
| `mx-auto`   | Center horizontally  |
| `space-x-*` | Horizontal spacing   |
| `space-y-*` | Vertical spacing     |
| `w-full`    | Full width           |
| `h-screen`  | Full viewport height |
| `max-w-*`   | Max width            |

### Positioning

```html
<div class="relative">
  <div class="absolute top-0 right-0"></div>
</div>
```

| Utility    | Usage           |
| ---------- | --------------- |
| `relative` | Relative parent |
| `absolute` | Absolute child  |
| `fixed`    | Fixed position  |
| `sticky`   | Sticky element  |
| `top-0`    | Top position    |
| `inset-0`  | Full inset      |
| `z-10`     | Z-index         |

- Prefer Flexbox for 1D layouts
- Prefer Grid for 2D layouts
- Use gap utilities instead of margins
- Keep spacing scale consistent
- Avoid excessive positioning

```jsx
<div className="grid gap-6 md:grid-cols-3">
  <div className="rounded-xl bg-white p-6 shadow">Card</div>
</div>
```

---

## 📌 Typography & Colors

### Typography Utilities

```html
<h1 class="text-3xl font-bold leading-tight tracking-wide"></h1>
```

| Utility                    | Usage          |
| -------------------------- | -------------- |
| `text-sm` → `text-9xl`     | Font size      |
| `font-light` → `font-bold` | Font weight    |
| `text-left` `text-center`  | Text align     |
| `leading-*`                | Line height    |
| `tracking-*`               | Letter spacing |
| `uppercase`                | Text transform |
| `truncate`                 | Text overflow  |
| `whitespace-nowrap`        | Prevent wrap   |

### Colors

```html
<div class="bg-blue-600 text-white border-gray-200"></div>
```

| Utility         | Usage            |
| --------------- | ---------------- |
| `text-*`        | Text color       |
| `bg-*`          | Background color |
| `border-*`      | Border color     |
| `from-*` `to-*` | Gradient colors  |
| `opacity-*`     | Opacity          |

### Background Styling

```html
<div class="bg-cover bg-center bg-no-repeat"></div>
```

| Utility            | Usage              |
| ------------------ | ------------------ |
| `bg-cover`         | Cover background   |
| `bg-contain`       | Contain background |
| `bg-center`        | Center position    |
| `bg-top`           | Top position       |
| `bg-no-repeat`     | Disable repeat     |
| `bg-gradient-to-r` | Gradient direction |
| `bg-fixed`         | Fixed background   |

- Use consistent typography scale
- Prefer theme colors over arbitrary values
- Use gradients minimally
- Maintain proper text contrast
- Keep typography responsive

```jsx
<div className="rounded-xl bg-gradient-to-r from-blue-600 to-indigo-600 p-6 text-white">
  <h2 className="text-2xl font-bold">Dashboard</h2>

  <p className="mt-2 text-sm opacity-80">Modern Tailwind UI</p>
</div>
```

---

## 📌 Visual Styling Utilities

### Borders & Rings

```html
<div class="border rounded-xl ring-2 ring-blue-500"></div>
```

| Utility                    | Usage              |
| -------------------------- | ------------------ |
| `border`                   | Add border         |
| `border-2`                 | Border width       |
| `border-gray-200`          | Border color       |
| `rounded` → `rounded-full` | Border radius      |
| `divide-x` `divide-y`      | Child borders      |
| `ring-*`                   | Focus/outline ring |
| `ring-offset-*`            | Ring spacing       |

### Effects

```html
<div class="shadow-lg opacity-80 backdrop-blur"></div>
```

| Utility                    | Usage           |
| -------------------------- | --------------- |
| `shadow-sm` → `shadow-2xl` | Box shadow      |
| `opacity-*`                | Opacity         |
| `blur-*`                   | Blur            |
| `brightness-*`             | Brightness      |
| `contrast-*`               | Contrast        |
| `grayscale`                | Grayscale       |
| `backdrop-blur-*`          | Background blur |

- Use subtle shadows
- Prefer rings over outline
- Keep border radius consistent
- Avoid excessive blur/effects
- Maintain visual hierarchy

```jsx
<div className="rounded-2xl border border-gray-200 bg-white p-6 shadow-sm ring-1 ring-gray-100 backdrop-blur">
  Modern Card
</div>
```

---

## 📌 Responsive Design

### Breakpoints

```html
<div class="text-sm md:text-lg lg:text-2xl"></div>
```

| Prefix | Min Width |
| ------ | --------- |
| `sm:`  | 640px     |
| `md:`  | 768px     |
| `lg:`  | 1024px    |
| `xl:`  | 1280px    |
| `2xl:` | 1536px    |

---

### Responsive Workflow

Mobile styles are default, larger screens override using prefixes.

```html
<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4"></div>
```

| Pattern              | Usage               |
| -------------------- | ------------------- |
| Base Class           | Mobile default      |
| `md:*`               | Tablet styles       |
| `lg:*`               | Desktop styles      |
| Responsive Flex/Grid | Adaptive layouts    |
| Responsive Spacing   | Adjust padding/gaps |

### Modern Responsive Features

```html
<div class="@container">
  <div class="@md:flex"></div>
</div>
```

| Feature               | Usage                       |
| --------------------- | --------------------------- |
| Container Queries     | Parent-based responsiveness |
| Arbitrary Breakpoints | `max-[900px]:hidden`        |
| Responsive Variants   | `md:hover:bg-blue-600`      |
| Dynamic Layouts       | Auto-fit grids              |

- Design mobile-first
- Use fewer breakpoints
- Prefer Grid/Flex responsiveness
- Keep spacing responsive
- Avoid unnecessary custom media queries

```jsx
<div className="grid grid-cols-1 gap-6 md:grid-cols-2 xl:grid-cols-4">
  <div className="rounded-xl bg-white p-6 shadow">Card</div>
</div>
```

---

## 📌 State & Interaction Variants

### State Variants

```html
<button class="hover:bg-blue-700 focus:ring active:scale-95"></button>
```

| Variant          | Usage          |
| ---------------- | -------------- |
| `hover:`         | Hover state    |
| `focus:`         | Focus state    |
| `active:`        | Active state   |
| `disabled:`      | Disabled state |
| `checked:`       | Checked input  |
| `focus-visible:` | Keyboard focus |

### Parent & Sibling States

```html
<div class="group">
  <button class="group-hover:bg-blue-600"></button>
</div>
```

```html
<input class="peer" />
<p class="peer-invalid:block"></p>
```

| Variant         | Usage              |
| --------------- | ------------------ |
| `group-hover:`  | Parent hover       |
| `group-focus:`  | Parent focus       |
| `peer-invalid:` | Sibling validation |
| `peer-checked:` | Sibling checked    |

### Advanced Variants

```html
<div class="data-[active=true]:bg-green-500"></div>
```

| Variant            | Usage           |
| ------------------ | --------------- |
| `dark:`            | Dark mode       |
| `data-*`           | Data attributes |
| `aria-*`           | ARIA states     |
| `supports-*`       | Feature support |
| Arbitrary Variants | `[&>*]:p-4`     |

- Use variants instead of custom CSS
- Prefer `group` for parent interaction
- Use `peer` for form states
- Keep state styling predictable
- Avoid deeply nested arbitrary selectors

```jsx
<button className="rounded bg-blue-600 px-4 py-2 text-white transition hover:bg-blue-700 focus:ring-2 focus:ring-blue-400 active:scale-95">
  Submit
</button>
```

---

## 📌 Motion & Animation

### Transforms

```html
<div class="scale-105 rotate-6 translate-y-2"></div>
```

| Utility       | Usage            |
| ------------- | ---------------- |
| `scale-*`     | Scale element    |
| `rotate-*`    | Rotate           |
| `translate-*` | Move position    |
| `skew-*`      | Skew element     |
| `origin-*`    | Transform origin |

### Transitions

```html
<button class="transition duration-300 ease-in-out"></button>
```

| Utility          | Usage             |
| ---------------- | ----------------- |
| `transition`     | Enable transition |
| `duration-*`     | Animation speed   |
| `delay-*`        | Delay start       |
| `ease-*`         | Timing function   |
| `transition-all` | Animate all       |

### Animations

```html
<div class="animate-spin"></div>
```

| Utility          | Usage        |
| ---------------- | ------------ |
| `animate-spin`   | Spinner      |
| `animate-pulse`  | Pulse effect |
| `animate-bounce` | Bounce       |
| `animate-ping`   | Ping effect  |

- Keep animations subtle
- Use transitions for interactions
- Avoid excessive motion
- Prefer GPU-friendly transforms
- Use reduced motion when needed

```jsx
<button className="rounded bg-blue-600 px-4 py-2 text-white transition duration-300 hover:scale-105 hover:bg-blue-700 active:scale-95">
  Continue
</button>
```

---

```txt
@keyframes → animation config → utility class
```

### Built-in Animations

| Class            | Usage   |
| ---------------- | ------- |
| `animate-spin`   | Spinner |
| `animate-pulse`  | Pulse   |
| `animate-bounce` | Bounce  |
| `animate-ping`   | Ping    |

---

### Custom Animation

```js
// tailwind.config.js
extend: {
  keyframes: {
    float: {
      '0%,100%': {
        transform: 'translateY(0)',
      },
      '50%': {
        transform: 'translateY(-10px)',
      },
    },
  },

  animation: {
    float: 'float 3s ease-in-out infinite',
  },
}
```

```html
<div class="animate-float"></div>
```

### Animation Structure

| Part          | Purpose         |
| ------------- | --------------- |
| `keyframes`   | Motion steps    |
| `animation`   | Speed/timing    |
| Utility class | Apply animation |

- Prefer subtle animations
- Use transform-based animations
- Keep durations short
- Reuse animations via config

```jsx
<div className="animate-pulse rounded bg-blue-600 p-4 text-white">
  Loading...
</div>
```

---

## 📌 Dark Mode & Theming

### Dark Mode

```html
<div class="bg-white text-black dark:bg-gray-900 dark:text-white"></div>
```

| Variant | Usage               |
| ------- | ------------------- |
| `dark:` | Apply dark styles   |
| `media` | System theme        |
| `class` | Manual theme toggle |

```js
// tailwind.config.js
export default {
  darkMode: "class",
};
```

### Theme Switching

```html
<html class="dark"></html>
```

| Method        | Usage         |
| ------------- | ------------- |
| System Theme  | Auto detect   |
| Class Toggle  | Manual switch |
| Local Storage | Persist theme |

### CSS Variables

```css
:root {
  --primary: #2563eb;
}
```

```html
<div class="bg-[var(--primary)]"></div>
```

- Prefer `class` strategy
- Use CSS variables for themes
- Maintain proper contrast
- Keep dark/light spacing same

```jsx
<div className="rounded-xl bg-white p-6 text-black dark:bg-gray-900 dark:text-white">
  Dashboard
</div>
```

---

## 📌 Customization & Configuration

Tailwind customization is done using `tailwind.config.js`.

```js
export default {
  theme: {
    extend: {
      colors: {
        primary: "#2563eb",
      },

      spacing: {
        18: "4.5rem",
      },
    },
  },
};
```

| Config       | Usage         |
| ------------ | ------------- |
| `colors`     | Custom colors |
| `spacing`    | Spacing scale |
| `fontFamily` | Fonts         |
| `screens`    | Breakpoints   |
| `shadow`     | Shadows       |

### Advanced Configuration

| Config     | Purpose               |
| ---------- | --------------------- |
| `content`  | Scan project files    |
| `plugins`  | Add plugins           |
| `extend`   | Extend defaults       |
| `presets`  | Shared config         |
| `darkMode` | Dark mode strategy    |
| `safelist` | Prevent purge removal |

### Content Configuration

```js
content: ["./src/**/*.{js,jsx,ts,tsx}"];
```

### Plugins

```js
plugins: [require("@tailwindcss/forms")];
```

- Extend instead of overwrite
- Keep config centralized
- Use semantic theme tokens
- Keep content paths accurate
- Avoid excessive custom utilities

```js
extend: {
  colors: {
    primary: '#0f172a',
    secondary: '#2563eb',
  },
}
```

---

## 📌 Directives & Layers

Tailwind uses directives and layers to organize generated CSS.

| Directive               | Usage                   |
| ----------------------- | ----------------------- |
| `@import "tailwindcss"` | Import Tailwind         |
| `@theme`                | Define theme variables  |
| `@utility`              | Create custom utilities |
| `@variant`              | Apply variants in CSS   |
| `@source`               | Add extra scan sources  |
| `@apply`                | Reuse utilities inline  |

### Layers

```txt
Base → Components → Utilities
```

| Layer      | Purpose                   |
| ---------- | ------------------------- |
| Base       | Reset/default styles      |
| Components | Reusable component styles |
| Utilities  | Atomic utility classes    |

### Custom Utility

```css
@utility flex-center {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

### Variant Usage

```css
.card {
  @variant hover {
    opacity: 0.8;
  }
}
```

- Prefer utilities over custom CSS
- Keep custom utilities minimal
- Use components layer for reusable patterns
- Avoid large custom style systems

```css
.btn-primary {
  @apply rounded bg-blue-600 px-4 py-2 text-white;
}
```

---

## 📌 Reusable Styling & Architecture

Tailwind encourages reusable utility patterns, scalable structure, and design systems.

### `@apply`

```css
.btn {
  @apply rounded bg-blue-600 px-4 py-2 text-white;
}
```

### Component Extraction

```jsx
<Button variant="primary" />
```

| Method              | Usage                |
| ------------------- | -------------------- |
| `@apply`            | Reuse utility groups |
| Components          | Reusable UI          |
| Utility Composition | Combine utilities    |

### Design Systems

| Concept       | Usage                 |
| ------------- | --------------------- |
| Theme Tokens  | Shared colors/spacing |
| UI Patterns   | Consistent components |
| Variants      | Reusable states       |
| Shared Config | Centralized design    |

```js
colors: {
  primary: '#2563eb',
}
```

### Scalability

| Structure            | Purpose           |
| -------------------- | ----------------- |
| `components/`        | Reusable UI       |
| `layouts/`           | Layout wrappers   |
| `ui/`                | Shared primitives |
| `tailwind.config.js` | Central theme     |

- Prefer reusable components
- Use semantic design tokens
- Keep utility patterns consistent
- Avoid duplicate class chains
- Centralize theme configuration

```jsx
<button className="btn-primary">Continue</button>
```

```css
.btn-primary {
  @apply rounded bg-blue-600 px-4 py-2 text-white hover:bg-blue-700;
}
```

| Approach        | Example                         | Preferred      |
| --------------- | ------------------------------- | -------------- |
| Utility Classes | `class="px-4 py-2 bg-blue-600"` | ✅ Recommended |
| `@apply`        | `.btn { @apply px-4 py-2 }`     | ⚠ Limited use  |

### When to Use `@apply`

✅ Good For:

- Repeated button styles
- Form controls
- Third-party library styling
- Small reusable patterns

❌ Avoid For:

- Entire layouts
- Large components
- Everything by default

---

## 📌 Plugins & Ecosystem

| Official Plugins                 | Usage                  |
| -------------------------------- | ---------------------- |
| `@tailwindcss/forms`             | Better form styling    |
| `@tailwindcss/typography`        | Rich content styling   |
| `@tailwindcss/aspect-ratio`      | Aspect ratio utilities |
| `@tailwindcss/container-queries` | Container queries      |

```bash
npm install @tailwindcss/forms
```

### Utility Libraries

| Library          | Usage                     |
| ---------------- | ------------------------- |
| `clsx`           | Conditional classes       |
| `tailwind-merge` | Merge conflicting classes |
| `cva`            | Variant-based components  |

```jsx
clsx("px-4", active && "bg-blue-600");
```

### UI Ecosystem

| Library       | Usage                      | Popularity      |
| ------------- | -------------------------- | --------------- |
| `shadcn/ui`   | Modern component system    | ⭐ Most Popular |
| `Radix UI`    | Accessible primitives      | Very High       |
| `Headless UI` | Unstyled accessible UI     | Very High       |
| `DaisyUI`     | Tailwind component library | High            |
| `Flowbite`    | Prebuilt Tailwind UI       | Medium          |

- Prefer official plugins
- Use `clsx` + `tailwind-merge`
- Use scalable customizable UI systems
- Tailwind works best with React/Next.js

```jsx
<button
  className={clsx("rounded px-4 py-2", active && "bg-blue-600 text-white")}
>
  Save
</button>
```

---

## 📌 Optimization & Performance

### Optimization

```txt
Content Scan → JIT Engine → Optimized CSS
```

| Feature             | Benefit            |
| ------------------- | ------------------ |
| JIT Engine          | Small CSS output   |
| Content Scan        | Removes unused CSS |
| On-demand Utilities | Faster builds      |
| Tree Shaking        | Optimized bundle   |

| Optimization                     | Usage               |
| -------------------------------- | ------------------- |
| Accurate `content` paths         | Prevent missing CSS |
| Minified build                   | Smaller file size   |
| Reusable utilities               | Less duplication    |
| Avoid excessive arbitrary values | Cleaner output      |

- Keep `content` paths accurate
- Prefer reusable utility patterns
- Avoid unnecessary custom CSS
- Use production builds only

```js
content: ["./src/**/*.{js,jsx,ts,tsx}"];
```

---

## 📌 Accessibility

| Accessibility Utilities | Usage              |
| ----------------------- | ------------------ |
| `focus:*`               | Focus states       |
| `focus-visible:*`       | Keyboard focus     |
| `sr-only`               | Screen reader only |
| `not-sr-only`           | Restore visibility |
| `motion-reduce:*`       | Reduced motion     |

| Accessibility Practices | Usage                  |
| ----------------------- | ---------------------- |
| Proper contrast         | Readability            |
| Keyboard navigation     | Accessible interaction |
| Semantic HTML           | Better structure       |
| Visible focus states    | Accessibility feedback |

- Always add focus states
- Maintain proper contrast
- Use semantic HTML
- Respect reduced motion

```jsx
<button className="rounded bg-blue-600 px-4 py-2 text-white focus-visible:outline-2">
  Submit
</button>
```

---

## 📌 Best Practices & Maintainability

| Best Practices                    | Usage              |
| --------------------------------- | ------------------ |
| Keep class order consistent       | Better readability |
| Prefer reusable components        | Less duplication   |
| Use theme tokens                  | Consistent design  |
| Use responsive utilities properly | Cleaner layouts    |

### Maintainability

| Practice                     | Usage              |
| ---------------------------- | ------------------ |
| Extract repeated patterns    | Reusable UI        |
| Avoid huge class chains      | Cleaner markup     |
| Prefer utility composition   | Less custom CSS    |
| Organize components properly | Better scalability |

- Prefer utility-first workflow
- Keep components small/reusable
- Avoid excessive `@apply`
- Use scalable folder structure

```jsx
<button className="rounded bg-blue-600 px-4 py-2 text-white hover:bg-blue-700">
  Save
</button>
```

---

## 📌 Common UI Patterns

| Layout Patterns | Usage            |
| --------------- | ---------------- |
| Navbar          | Navigation       |
| Sidebar         | App layouts      |
| Hero Section    | Landing pages    |
| Responsive Grid | Adaptive layouts |

| Content Patterns | Usage             |
| ---------------- | ----------------- |
| Cards            | Content blocks    |
| Tables           | Data display      |
| Pricing Cards    | Plans/features    |
| Stats Grid       | Dashboard metrics |

| Interactive Patterns | Usage             |
| -------------------- | ----------------- |
| Forms                | User input        |
| Modals               | Dialogs           |
| Dropdowns            | Menus             |
| Tabs                 | Content switching |

- Prefer reusable components
- Keep layouts responsive
- Use consistent spacing
- Reuse utility patterns

```jsx
<div className="grid gap-6 md:grid-cols-3">
  <div className="rounded-xl bg-white p-6 shadow">Card</div>
</div>
```

---

## 📌 Debugging & Troubleshooting

Common Tailwind issues usually come from configuration, class conflicts, or content scanning.

| Common Problems               | Solution              |
| ----------------------------- | --------------------- |
| Styles not applied            | Check `content` paths |
| Missing utilities             | Restart dev server    |
| Class conflicts               | Use `tailwind-merge`  |
| Dynamic classes not generated | Use safelist          |
| Build CSS too large           | Remove unused styles  |

### Responsive & Theme Issues

| Issue                         | Solution                    |
| ----------------------------- | --------------------------- |
| Responsive styles not working | Check breakpoint order      |
| Dark mode not working         | Verify `darkMode` config    |
| Hover/focus missing           | Use proper variants         |
| Layout breaking               | Inspect Flex/Grid utilities |

### Best Practices

- Keep config clean
- Verify scanned files
- Avoid conflicting utilities
- Use browser dev tools

```js
content: ["./src/**/*.{js,jsx,ts,tsx}"];
```

---

## 📌 Modern vs Deprecated Features

Modern Tailwind focuses on JIT, arbitrary values, variants, and utility-first workflows.

| Modern Features     | Usage                    |
| ------------------- | ------------------------ |
| Built-in JIT        | On-demand CSS generation |
| Arbitrary Values    | `w-[350px]`              |
| Arbitrary Selectors | `[&>*]:p-4`              |
| Data Variants       | `data-[open=true]:block` |
| Container Queries   | Responsive containers    |

| Deprecated / Less Used   | Status                         |
| ------------------------ | ------------------------------ |
| Old JIT setup            | Deprecated                     |
| External PurgeCSS        | Mostly unnecessary             |
| Legacy `purge` option    | Replaced by `content`          |
| Heavy `@apply` usage     | Less preferred                 |
| Large custom CSS systems | Against utility-first workflow |

- Prefer built-in JIT
- Use modern variants/selectors
- Prefer utility-first patterns
- Avoid SCSS-like abstraction

```html
<div class="w-[350px] data-[active=true]:bg-green-500"></div>
```

---

## 📌 Real-World Tailwind Systems

Modern Tailwind projects use component-driven, scalable UI systems.

| Common Systems      | Usage                    |
| ------------------- | ------------------------ |
| Design Systems      | Shared UI standards      |
| Component Libraries | Reusable components      |
| Multi-theme Systems | Light/dark/custom themes |
| SaaS Dashboards     | Admin/product UI         |
| Marketing Sites     | Landing pages            |
| Enterprise Apps     | Large scalable apps      |

### Common Stack

```txt
Tailwind CSS
 + React / Next.js
 + shadcn/ui
 + Radix UI
 + clsx / cva / tailwind-merge
```

### Typical Structure

```txt
components/
layouts/
pages/
ui/
tailwind.config.js
```

| Architecture Patterns    | Usage             |
| ------------------------ | ----------------- |
| Utility-first UI         | Fast development  |
| Component composition    | Reusable UI       |
| Theme tokens             | Consistent design |
| Variant-based components | Scalable styling  |

- Build reusable UI primitives
- Keep theme centralized
- Prefer component composition
- Use scalable folder structure

```jsx
<Card className="rounded-xl border bg-white p-6 shadow-sm">Dashboard</Card>
```

---
