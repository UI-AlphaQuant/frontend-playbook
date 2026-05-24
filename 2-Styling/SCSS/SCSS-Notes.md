# 👉 SCSS Core Fundamentals

## 📌 SCSS vs Sass vs CSS

| Feature                      | CSS                        | SCSS                | Sass                |
| ---------------------------- | -------------------------- | ------------------- | ------------------- |
| Type                         | Native stylesheet language | Modern Sass syntax  | Older Sass syntax   |
| File Extension               | `.css`                     | `.scss`             | `.sass`             |
| Browser Support              | ✅ Direct                  | ❌ Compile Required | ❌ Compile Required |
| Syntax                       | Standard CSS               | CSS-like            | Indentation-based   |
| Curly Braces / Semicolons    | ✅ Yes                     | ✅ Yes              | ❌ No               |
| Variables / Nesting / Mixins | ❌ Limited                 | ✅ Yes              | ✅ Yes              |
| Popularity                   | High                       | Highest             | Low                 |
| Recommended                  | ✅ Yes                     | ✅ Yes              | ❌ Rarely Used      |

### CSS

```css
.card {
  background: royalblue;
}
```

### SCSS

```scss
$primary: royalblue;

.card {
  background: $primary;

  &:hover {
    opacity: 0.8;
  }
}
```

### Sass

```sass
$primary: royalblue

.card
  background: $primary
```

- Learn CSS first
- Prefer SCSS for modern projects
- Avoid old Sass syntax in new projects

---

## 📌 How SCSS Works (Compilation)

| Step | Process                           |
| ---- | --------------------------------- |
| 1    | Write styles in `.scss` files     |
| 2    | Sass compiler converts SCSS → CSS |
| 3    | Browser reads generated CSS       |

| Compiler  | Status         |
| --------- | -------------- |
| Dart Sass | ✅ Recommended |
| Node Sass | ❌ Deprecated  |
| Ruby Sass | ❌ Deprecated  |

- Use Dart Sass for modern projects
- Keep SCSS modular and organized
- Prefer `@use` instead of deprecated `@import`

---

## 📌 Installing SCSS

| Project Type                  | Setup                          |
| ----------------------------- | ------------------------------ |
| Static Project (Without Node) | Use VS Code Live Sass Compiler |
| Vite / React / Vue / Angular  | `npm install -D sass`          |

| Method             | Purpose                 |
| ------------------ | ----------------------- |
| Live Sass Compiler | Auto compile SCSS → CSS |
| Sass Package       | Framework SCSS support  |

### Static Project (Without Node)

Install VS Code extension:

```text
Live Sass Compiler
```

Folder Structure & Usage

```text
project/
├── scss/
│   └── style.scss
├── css/
│   └── style.css
└── index.html
```

```html
<link rel="stylesheet" href="css/style.css" />
```

### React / Vue / Angular (Vite)

```bash
npm install -D sass
```

```js
import "./style.scss";
```

- Use Live Sass Compiler for simple static projects
- Use package installation for modern frameworks
- Keep SCSS source files separated from compiled CSS

---

## 📌 SCSS Syntax Essentials

| Feature             | Details                                     |
| ------------------- | ------------------------------------------- |
| Syntax              | SCSS uses CSS-like syntax with `{}` and `;` |
| Nesting             | Allows writing selectors inside selectors   |
| Parent Selector `&` | Refers to current parent selector           |
| Single-line Comment | `// Comment` → not compiled                 |
| Multi-line Comment  | `/* Comment */` → compiled                  |

```scss
$primary: royalblue;

.button {
  background: $primary;

  &:hover {
    opacity: 0.8;
  }

  &.active {
    border: 2px solid black;
  }
}
```

- Keep nesting shallow
- Use `&` for hover, active, and modifier states

---

## 📌 Variables

| Syntax          | Purpose              |
| --------------- | -------------------- |
| `$name: value;` | Create variable      |
| `!global`       | Make variable global |
| `!default`      | Set fallback value   |
| `#{$var}`       | Interpolation        |

| Variable Type | Example                         |
| ------------- | ------------------------------- |
| Color         | `$primary: royalblue;`          |
| Spacing       | `$space-md: 20px;`              |
| Font          | `$font-primary: Arial;`         |
| Breakpoint    | `$md: 768px;`                   |
| Shadow        | `$shadow-sm: 0 2px 10px #0001;` |

| Scope           | Details                      |
| --------------- | ---------------------------- |
| Global Variable | Accessible everywhere        |
| Local Variable  | Accessible only inside block |

| SCSS Variables           | CSS Variables        |
| ------------------------ | -------------------- |
| Compile-time             | Runtime              |
| Not available in browser | Available in browser |
| Better for logic & loops | Better for theming   |
| Starts with `$`          | Starts with `--`     |

```scss
$primary: #2563eb;
$secondary: #0f172a;

$font-primary: "Poppins", sans-serif;

$space-xs: 4px;
$space-sm: 8px;
$space-md: 16px;
$space-lg: 24px;

$radius-sm: 6px;
$radius-md: 12px;

$shadow-sm: 0 2px 8px #0001;

$mobile: 480px;
$tablet: 768px;
$desktop: 1200px;
```

- Use SCSS variables for reusable design values
- Prefer CSS variables for themes and runtime changes
- Keep variables centralized in `_variables.scss`
- Use meaningful and scalable naming

---

## 📌 Data Types

| Data Type | Example                |
| --------- | ---------------------- |
| Number    | `16px`, `1.5rem`       |
| String    | `"Poppins"`            |
| Color     | `#2563eb`, `royalblue` |
| Boolean   | `true`, `false`        |
| Null      | `null`                 |
| List      | `10px 20px 30px`       |
| Map       | `(primary: #2563eb)`   |

```scss
$primary: #2563eb;
$font: "Poppins";
$space: 20px;
$spaces: 4px, 8px, 16px, 24px;
$shadow: 0 4px 10px #0002;
$breakpoints: (
  sm: 480px,
  md: 768px,
  lg: 1024px,
  xl: 1200px,
);

.card {
  background: $primary;
  font-family: $font;
  padding: $space;
  box-shadow: $shadow;
  width: 33.33%;

  @media (max-width: map-get($breakpoints, md)) {
    width: 50%;
  }

  @media (max-width: map-get($breakpoints, sm)) {
    width: 100%;
  }
}
```

- Maps and lists are common in design systems
- Use meaningful variable types
- Keep tokens centralized

---

## 📌 Nested Structure

Nested selectors improve structure by placing related styles inside parent selectors.

| Feature           | Details                         |
| ----------------- | ------------------------------- |
| Nested Selectors  | Child selectors inside parent   |
| Nested Properties | Group related properties        |
| Nesting Depth     | Avoid deep nesting              |
| Readability       | Keep structure clean and simple |
| BEM Nesting       | Use `&` for modifiers/elements  |
| Practical Usage   | Components, layouts, states     |

| Recommended Nesting | Status   |
| ------------------- | -------- |
| 1–3 Levels          | ✅ Good  |
| 4+ Levels           | ❌ Avoid |

```scss
.card {
  padding: 20px;

  font: {
    family: Arial;
    size: 16px;
    weight: 400;
  }

  h2 {
  }

  p {
  }

  &:hover {
  }

  /* Children: .card__title */
  &__title {
  }

  /* Children: .card--active */
  &--active {
  }
}
```

- Keep nesting shallow
- Avoid long selector chains
- Use `&` for BEM modifiers and states
- Nest only logically related elements

---

## 📌 Parent Selector (`&`)

The `&` symbol refers to the current parent selector and helps create reusable, dynamic selectors.

| Usage             | Example     |
| ----------------- | ----------- |
| Hover State       | `&:hover`   |
| Focus State       | `&:focus`   |
| Active Class      | `&.active`  |
| BEM Modifier      | `&--large`  |
| BEM Element       | `&__title`  |
| Pseudo Element    | `&::before` |
| Parent Context    | `.dark &`   |
| Adjacent Selector | `& + &`     |
| Child Selector    | `& > li`    |

```scss
.button {
  /* .button:hover */
  &:hover {
    opacity: 0.8;
  }

  /* .button.active */
  &.active {
  }

  /* .button--large */
  &--large {
  }

  /* .button::before */
  &::before {
    content: "";
  }

  /* .dark .button */
  .dark & {
    background: white;
  }

  /* .button + .button */
  & + & {
  }

  /* .button > span */
  & > span {
  }
}
```

- Use `&` for states and modifiers
- Prefer BEM-friendly structure
- Avoid overly complex selector chains

---

## 📌 Partials & Structure

Partials are reusable SCSS files used to organize styles into smaller modules.

| Feature      | Details                             |
| ------------ | ----------------------------------- |
| Partial File | Starts with `_`                     |
| Compilation  | Not compiled directly               |
| Usage        | Imported into main file             |
| Purpose      | Better organization and scalability |

| Common Partials   | Purpose          |
| ----------------- | ---------------- |
| `_variables.scss` | Variables        |
| `_mixins.scss`    | Mixins           |
| `_reset.scss`     | Base styles      |
| `_buttons.scss`   | Component styles |
| `_layout.scss`    | Layout styles    |

```text
scss/
├── abstracts/
│   ├── _variables.scss
│   └── _mixins.scss
├── base/
│   └── _reset.scss
├── components/
│   └── _button.scss
├── layout/
│   └── _header.scss
└── main.scss
```

```scss
// main.scss
@use "abstracts/variables";
@use "components/button";
```

- Split SCSS into reusable modules
- Keep one responsibility per file
- Prefer `@use` over deprecated `@import`

---

## 📌 Mixins

| Feature     | Details                |
| ----------- | ---------------------- |
| `@mixin`    | Create reusable styles |
| `@include`  | Use mixin              |
| Parameters  | Pass dynamic values    |
| Reusability | Reuse common patterns  |

| Mixin Type    | Purpose                   |
| ------------- | ------------------------- |
| Flex Center   | Center alignment          |
| Container     | Consistent layout width   |
| Typography    | Font sizing and weights   |
| Media Query   | Responsive utilities      |
| Shadow        | Consistent shadow styles  |
| Transition    | Reusable animations       |
| Text Ellipsis | Single-line text truncate |

```scss
@mixin flex-center {
  display: flex;
  justify-content: center;
  align-items: center;
}

@mixin button($bg) {
  background: $bg;
  padding: 12px 20px;
}

.card {
  @include flex-center;
}

.button {
  @include button(royalblue);
}
```

- Use mixins for reusable style patterns
- Prefer parameters for flexibility
- Avoid very large mixins

---

## 📌 Import System

The import system organizes SCSS into reusable modular files.

| Rule       | Purpose                     |
| ---------- | --------------------------- |
| `@use`     | Import module (Recommended) |
| `@forward` | Re-export modules           |
| `@import`  | Deprecated import system    |

| `@use` Features      | Details              |
| -------------------- | -------------------- |
| Namespace Support    | Prevents conflicts   |
| Scoped Imports       | Cleaner architecture |
| No Duplicate Imports | Better optimization  |

| Deprecated `@import` Issues | Details          |
| --------------------------- | ---------------- |
| Global Scope                | Naming conflicts |
| Duplicate Loading           | Repeated CSS     |
| No Namespace                | Hard to maintain |

```scss
// _variables.scss
$primary: royalblue;
```

```scss
// _mixins.scss
@mixin flex-center {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

```scss
// main.scss
@use "variables";
@use "mixins";

.card {
  background: variables.$primary;
  @include mixins.flex-center;
}
```

- Prefer `@use` in modern SCSS
- Avoid deprecated `@import`
- Keep modules small and reusable

## 📌 Namespace

`@use` adds a namespace to avoid naming conflicts and keep imports scoped.

| Syntax                   | Usage                      |
| ------------------------ | -------------------------- |
| `variables.$primary`     | ✅ Default & Recommended   |
| `$primary`               | ❌ Not directly accessible |
| `@use "variables" as *;` | Removes namespace          |

```scss
@use "variables" as *;

.card {
  background: $primary;
}
```

- Prefer namespace in scalable projects
- `as *` is okay for small projects

---

## 📌 Extend & Placeholders

`@extend` reuses existing styles, and `%placeholders` create reusable styles without generating extra CSS unless used.

| Feature        | Details                              |
| -------------- | ------------------------------------ |
| `@extend`      | Inherit styles from another selector |
| `%placeholder` | Reusable non-output selector         |
| Reusability    | Reduce repeated CSS                  |
| Best Use       | Shared utility styles                |

```scss
%flex-center {
  display: flex;
  justify-content: center;
  align-items: center;
}

.card {
  @extend %flex-center;
  padding: 20px;
}

.modal {
  @extend %flex-center;
  height: 100vh;
}
```

```css
.card,
.modal {
  display: flex;
  justify-content: center;
  align-items: center;
}

.card {
  padding: 20px;
}

.modal {
  height: 100vh;
}
```

- Use placeholders for shared styles
- Avoid excessive `@extend`
- Prefer mixins for dynamic reusable styles

---

# 👉 SCSS Advance

## 📌 Functions

Functions return values and help create reusable dynamic logic in SCSS.

| Feature            | Details                      |
| ------------------ | ---------------------------- |
| `@function`        | Create custom function       |
| `@return`          | Return value                 |
| Built-in Functions | Colors, math, strings, lists |
| Custom Functions   | Reusable calculations        |

| Common Usage  | Example                  |
| ------------- | ------------------------ |
| Colors        | `darken()`, `lighten()`  |
| Math          | `percentage()`, `calc()` |
| Theme Logic   | Dynamic values           |
| Function Type | Purpose                  |
| ---           | ---                      |
| Spacing       | px → rem conversion      |
| Typography    | Dynamic font sizing      |
| Breakpoints   | Responsive values        |
| Z-index       | Layer management         |

```scss
$themes: (
  light: (
    bg: #ffffff,
    text: #111111,
  ),
  dark: (
    bg: #111111,
    text: #ffffff,
  ),
);

@function theme($mode, $key) {
  @return map-get(map-get($themes, $mode), $key);
}

.card-light {
  background: theme(light, bg);
  color: theme(light, text);
}

.card-dark {
  background: theme(dark, bg);
  color: theme(dark, text);
}
```

- Use functions for reusable calculations
- Keep functions simple and focused
- Prefer functions over repeated values

---

## 📌 Operators & Calculations

Operators help create scalable spacing, layouts, typography, and responsive sizing.

| Practical Usage   | Example            |
| ----------------- | ------------------ |
| Spacing Scale     | `$space * 2`       |
| Grid Width        | `100% / 3`         |
| Responsive Height | `100vh - 80px`     |
| Font Scaling      | `$font-size + 2px` |
| Card Width        | `calc(50% - 20px)` |

```scss
$space: 12px;
$sidebar: 280px;
$header: 80px;

.layout {
  gap: $space * 2;
}

.card {
  width: calc(50% - #{$space});
  padding: $space + 8px;
}

.main {
  width: calc(100% - #{$sidebar});
  min-height: calc(100vh - #{$header});
}
```

- Commonly used in layouts and design systems
- Combine variables with calculations
- Keep calculations readable

---

## 📌 Maps

| Usage       | Example              |
| ----------- | -------------------- |
| Colors      | `(primary: #2563eb)` |
| Breakpoints | `(md: 768px)`        |
| Z-index     | `(modal: 1000)`      |

```scss
$colors: (
  primary: #2563eb,
  success: #16a34a,
);

.button {
  background: map-get($colors, primary);
}
```

- Common in design systems
- Keeps values centralized
- Often used with functions and loops

---

## 📌 Control Directives

Control directives add logic and dynamic CSS generation in SCSS.

| Directive | Purpose                 |
| --------- | ----------------------- |
| `@if`     | Conditional styles      |
| `@else`   | Alternate condition     |
| `@for`    | Fixed loops             |
| `@each`   | Loop through lists/maps |
| `@while`  | Repeat until condition  |

| Common Usage         | Example                   |
| -------------------- | ------------------------- |
| Utility Classes      | Margin, padding utilities |
| Theme Variants       | Conditional styling       |
| Responsive Utilities | Dynamic breakpoints       |

```scss
@for $i from 1 through 3 {
  .m-#{$i} {
    margin: #{$i * 10}px;
  }
}
```

```css
.m-1 {
  margin: 10px;
}

.m-2 {
  margin: 20px;
}

.m-3 {
  margin: 30px;
}
```

- Common in utility generation
- Prefer `@each` for maps and lists
- Keep logic simple and readable

---

# 👉 Practical Usage

## 📌 SCSS Design Systems

Design systems use centralized tokens and reusable styles for consistent UI development.

| Design Token | Purpose                 |
| ------------ | ----------------------- |
| Colors       | Brand/theme colors      |
| Typography   | Font sizes & weights    |
| Spacing      | Consistent gaps/padding |
| Breakpoints  | Responsive sizes        |
| Shadows      | Elevation system        |

| Common Structure | Purpose           |
| ---------------- | ----------------- |
| Variables        | Design tokens     |
| Mixins           | Reusable patterns |
| Functions        | Dynamic values    |
| Components       | Shared UI styles  |

```scss
$colors: (
  primary: #2563eb,
  danger: #dc2626,
);

$space-md: 16px;

.button {
  background: map-get($colors, primary);
  padding: $space-md;
}

.alert {
  background: map-get($colors, danger);
}
```

- Keep design tokens centralized
- Reuse styles through mixins/functions
- Maintain consistent spacing and colors

---

## 📌 Utility Generation

Utility generation creates reusable utility classes dynamically using loops and maps.

| Utility Type | Example            |
| ------------ | ------------------ |
| Margin       | `.m-1`, `.m-2`     |
| Padding      | `.p-1`, `.p-2`     |
| Font Size    | `.fs-sm`, `.fs-lg` |
| Colors       | `.bg-primary`      |

```scss
$spaces: (
  1: 4px,
  2: 8px,
  3: 16px,
);

@each $key, $value in $spaces {
  .p-#{$key} {
    padding: $value;
  }
}
```

- Common in utility-first systems
- Use maps for scalable utilities
- Keep utility naming consistent

---

## 📌 SCSS in Modern Development

| Technology  | Usage                   |
| ----------- | ----------------------- |
| React       | Component styling       |
| Vue         | Scoped component styles |
| Angular     | Built-in SCSS support   |
| Vite        | Fast SCSS integration   |
| CSS Modules | Scoped class names      |

| Common Usage     | Purpose                  |
| ---------------- | ------------------------ |
| Global Styles    | Base styles & resets     |
| Component Styles | Isolated UI styling      |
| Design Systems   | Shared reusable styles   |
| Theming          | Centralized theme tokens |

---

## 📌 Optimization & Maintainability

Optimization reduces CSS size and improves performance, while maintainability keeps SCSS scalable and easier to manage.

| Optimization           | Purpose              |
| ---------------------- | -------------------- |
| Reduce Nesting         | Smaller CSS output   |
| Avoid Duplicate Styles | Cleaner compiled CSS |
| Generate Utilities     | Reusable classes     |

| Maintainability   | Purpose            |
| ----------------- | ------------------ |
| Modular Structure | Easier scaling     |
| Consistent Naming | Better readability |
| Scoped Imports    | Prevent conflicts  |

---

## 📌 Debugging

SCSS provides debugging tools for inspecting values and handling errors during compilation.

| Directive | Purpose                     |
| --------- | --------------------------- |
| `@debug`  | Print values in terminal    |
| `@warn`   | Show warnings               |
| `@error`  | Stop compilation with error |

| Common Usage      | Purpose               |
| ----------------- | --------------------- |
| Variable Checking | Inspect values        |
| Validation        | Prevent invalid input |
| Development       | Debug SCSS logic      |

```scss
$primary: royalblue;

@debug $primary;

@if $primary == null {
  @error "Primary color is missing";
}
```

```text
Debug: royalblue
```

- Use debugging during development only
- Helpful for functions, loops, and maps
- Remove unnecessary debug logs in production

---

## 📌 Modern vs Deprecated

| Modern / Recommended | Deprecated / Avoid    |
| -------------------- | --------------------- |
| `@use`               | `@import`             |
| Dart Sass            | Node Sass / Ruby Sass |
| Modular Structure    | Large global files    |
| Scoped Imports       | Global imports        |
| CSS Variables + SCSS | Only SCSS variables   |
| Shallow Nesting      | Deep nesting          |

| Modern Practice      | Purpose            |
| -------------------- | ------------------ |
| Component-based SCSS | Better scalability |
| Design Tokens        | Centralized values |
| Utility Generation   | Reusable utilities |

## 📌 Real-world SCSS Systems

| System            | Purpose                         |
| ----------------- | ------------------------------- |
| Design Tokens     | Colors, spacing, typography     |
| Utility System    | Margin, padding, flex utilities |
| Component System  | Buttons, cards, forms           |
| Theme System      | Light/Dark modes                |
| Responsive System | Centralized breakpoints         |

| Common Structure | Purpose                      |
| ---------------- | ---------------------------- |
| `abstracts`      | Variables, mixins, functions |
| `components`     | Reusable UI components       |
| `utilities`      | Utility classes              |
| `themes`         | Theme tokens                 |

- Keep tokens centralized
- Build reusable utilities and components
- Use modular architecture
