# 🎯 CSS – Interview Q&A

---

## 🟢 BASIC

#### 1. What is CSS?

**Answer:** Cascading Style Sheets. Language for styling HTML elements. Controls layout, colors, fonts, spacing. Separates content from presentation. Essential for web design.

#### 2. What are CSS selectors?

**Answer:** Patterns used to select HTML elements to style. Types: element selectors (`p`), class (`.class`), ID (`#id`), attribute (`[type="text"]`), universal (`*`).

#### 3. What is a CSS property?

**Answer:** Attribute of selector that defines styling. Examples: `color`, `background`, `font-size`, `margin`, `padding`, `border`. Property: value pairs define styles.

#### 4. What is the CSS box model?

**Answer:** Model describing layout of elements. Components: content, padding, border, margin. Content size + padding + border = element size. Margin is outside.

#### 5. What are classes and IDs?

**Answer:** Classes (`.className`) - multiple elements can have same class, can be reused. IDs (`#idName`) - unique per page, use for specific elements. Classes more flexible than IDs.

#### 6. What is specificity in CSS?

**Answer:** Ranking system determining which CSS rule applies. Inline styles (1000) > IDs (100) > classes/attributes (10) > elements (1). More specific rules override general ones.

#### 7. What is the difference between inline, internal, and external CSS?

**Answer:** Inline: styles in HTML tag (`style="color:red"`). Internal: `<style>` in `<head>`. External: separate `.css` file linked via `<link>`. External is preferred.

#### 8. What is inheritance in CSS?

**Answer:** Some properties inherited from parent to child elements. Example: `color`, `font-size` inherited. Others not: `margin`, `padding`, `border`. Use `inherit` value to force inheritance.

#### 9. What is the cascade in CSS?

**Answer:** Determines which styles apply when multiple rules target same element. Later rules override earlier ones (if same specificity). Specificity matters more than order.

#### 10. What is display property?

**Answer:** Controls element layout behavior. Values: `block` (full width, new line), `inline` (flows with text), `inline-block` (inline but accepts width/height), `flex`, `grid`, `none` (hidden).

#### 11. What is the difference between `margin` and `padding`?

**Answer:** Margin: space outside element border. Padding: space inside element border. Margin can be negative. Margin collapses between adjacent elements, padding doesn't.

#### 12. What are pseudo-classes?

**Answer:** Keywords targeting element in specific state. Examples: `:hover`, `:focus`, `:nth-child()`, `:first-child`, `:last-child`, `:active`. Activated by user action or element state.

#### 13. What are pseudo-elements?

**Answer:** Keywords selecting specific part of element. Examples: `::before`, `::after`, `::first-line`, `::first-letter`. Create new pseudo-elements without adding HTML.

#### 14. What is `z-index`?

**Answer:** Controls stacking order of overlapping elements. Higher values appear on top. Only works with positioned elements (`position: relative/absolute/fixed`). Creates stacking context.

#### 15. What is flexbox?

**Answer:** CSS layout model for distributing space. `display: flex` creates flex container. Properties: `flex-direction`, `justify-content`, `align-items`, `flex-wrap`, `gap`. Easier 1D layouts.

---

## 🟡 INTERMEDIATE

#### 1. What is CSS Grid?

**Answer:** 2D layout system. `display: grid` creates grid container. Define rows/columns with `grid-template-rows`, `grid-template-columns`. Place items with `grid-row`, `grid-column`. Powerful for 2D layouts.

#### 2. Flexbox vs CSS Grid?

**Answer:** Flexbox for 1D (rows or columns). Grid for 2D (rows and columns together). Flexbox flexible sizing. Grid precise positioning. Often use together: Grid for layout, Flexbox for alignment.

#### 3. What is responsive design?

**Answer:** Websites adapt to different screen sizes. Use fluid layouts, flexible images, media queries. Breakpoints: mobile (320px), tablet (768px), desktop (1024px), large (1440px).

#### 4. What are media queries?

**Answer:** Apply styles based on device characteristics. Syntax: `@media (condition) { /* styles */ }`. Common: `(max-width: 768px)`, `(min-width: 768px)`, `(orientation: landscape)`.

#### 5. What is mobile-first vs desktop-first?

**Answer:** Mobile-first: design for mobile first, add styles for larger screens using `min-width`. Desktop-first: design for desktop, override with `max-width` for mobile. Mobile-first preferred.

#### 6. What is a CSS preprocessor?

**Answer:** Tool extending CSS with variables, functions, nesting. Popular: Sass, Less, PostCSS. Compiles to standard CSS. Improves maintainability and reduces repetition.

#### 7. What are CSS variables (custom properties)?

**Answer:** Reusable values defined with `--name: value` and used with `var(--name)`. Example: `--primary-color: #3498db; color: var(--primary-color)`. Dynamic, can be changed with JavaScript.

#### 8. What is semantic CSS?

**Answer:** Using class names describing purpose, not appearance. Example: `.button-primary` instead of `.blue-button`. BEM (Block, Element, Modifier) naming convention. Improves maintainability.

#### 9. What is CSS transitions?

**Answer:** Smooth change of CSS property values. `transition: property duration timing-function delay`. Example: `transition: all 0.3s ease-in-out`. Improves UX with animations.

#### 10. What is CSS animations?

**Answer:** Define keyframe animations using `@keyframes`. More control than transitions. Example: `@keyframes slide { 0% {left: 0;} 100% {left: 100%;} }`. Used for complex animations.

#### 11. What is transform property?

**Answer:** Modifies element appearance. Values: `translate()`, `scale()`, `rotate()`, `skew()`. Applied in 2D or 3D space. Doesn't affect document flow (no reflow).

#### 12. What is filter property?

**Answer:** Applies graphical effects to elements. Values: `blur()`, `brightness()`, `contrast()`, `grayscale()`, `opacity()`, `sepia()`. Used for image effects, hover states.

#### 13. What is shadow (box-shadow, text-shadow)?

**Answer:** `box-shadow`: creates shadow around element. `text-shadow`: shadow under text. Syntax: `offset-x offset-y blur-radius color`. Used for depth, emphasis.

#### 14. What is position property?

**Answer:** Controls element positioning. Values: `static` (default), `relative` (relative to normal position), `absolute` (relative to positioned parent), `fixed` (relative to viewport), `sticky` (relative with scroll).

#### 15. What is stacking context?

**Answer:** 3D conceptualization of HTML elements. `z-index` only works within same stacking context. Created by `position`, `z-index`, `opacity` < 1, `transform`, etc.

#### 16. What is overflow property?

**Answer:** Controls content overflow behavior. Values: `visible` (default), `hidden` (crop), `scroll` (always scrollbar), `auto` (scrollbar if needed). Applied to width/height constraints.

#### 17. Difference between relative and absolute positioning?

**Answer:** Relative: positioned relative to normal position, still takes up space. Absolute: positioned relative to nearest positioned ancestor, removed from flow. Absolute used for overlays, modals.

---

## 🔴 ADVANCED

#### 1. Explain CSS painting and rendering process?

**Answer:** Browser parses CSS, creates CSSOM. Combines with DOM into render tree. Layout (reflow) calculates positions. Paint rasterizes elements. Composition layers. Repaint: style changes. Reflow: layout changes (expensive).

#### 2. What causes reflow and repaint?

**Answer:** Reflow: layout changes (width, height, position, display). Repaint: style changes (color, background, shadow). Reflow triggers repaint. Group DOM changes, read computed styles carefully, use transforms for animations.

#### 3. What is CSS performance optimization?

**Answer:** Minimize reflows/repaints. Use CSS transforms for animations. Avoid expensive selectors. Optimize images. Minify CSS. Use hardware acceleration (`will-change`, `transform`). CSS-in-JS trade-offs.

#### 4. What are CSS specificity wars and how to avoid?

**Answer:** Overusing IDs, `!important`, deeply nested selectors increases specificity debt. Avoid `!important`. Use class-based architecture (BEM, SMACSS). Keep specificity consistent. Use CSS preprocessors for organization.

#### 5. What is BEM naming convention?

**Answer:** Block, Element, Modifier. Structure: `.block__element--modifier`. Example: `.button__text--disabled`. Improves maintainability, reduces conflicts. Popular in large projects.

#### 6. What is SMACSS methodology?

**Answer:** Scalable and Modular Architecture. Categories: Base, Layout, Module, State, Theme. Reduces cascading issues. Improves maintainability. Used for large stylesheets.

#### 7. What is will-change property?

**Answer:** Hints browser which properties will change. Example: `will-change: transform`. Triggers hardware acceleration. Use sparingly, can degrade performance if overused. Remove after animation.

#### 8. What is containment in CSS?

**Answer:** `contain` property isolates element's styles/layout from rest of DOM. Improves performance for large documents. Values: `layout`, `paint`, `size`, `style`. Relatively new feature.

#### 9. What is CSS Grid auto-placement algorithm?

**Answer:** Automatically places grid items in empty cells. Follows row-major or column-major order. Can be overridden with explicit positioning. Handles responsive layouts automatically.

#### 10. How to create responsive images?

**Answer:** Use `<picture>` element with `<source>` for different sizes. Use `srcset` attribute. CSS: `max-width: 100%` for fluid images. Lazy-load with `loading="lazy"`. Modern: use WebP format with fallbacks.

#### 11. Real-life (Indian e-commerce): Design responsive grid layout for product listings?

**Answer:** Desktop: 4 columns grid. Tablet: 2 columns. Mobile: 1 column. Use CSS Grid: `grid-template-columns: repeat(auto-fit, minmax(250px, 1fr))`. Add media queries for adjustments. Images responsive with `max-width: 100%`.

#### 12. Real-life: Create smooth page transition animations?

**Answer:** Use `transition: opacity 0.3s ease-in-out`. Or CSS animations for complex. Avoid `left`, `top` (causes reflow). Use `transform: translateX()` instead (no reflow). Add loading states.

#### 13. Real-life: Optimize large stylesheet for production?

**Answer:** Minify CSS. Remove unused CSS (PurgeCSS, Tailwind). Code split CSS by route/component. Use CSS-in-JS for component isolation. Implement critical CSS inlining. Use modern CSS features with fallbacks.

#### 14. Calculation: If page has 1000 CSS rules and each selector has specificity of 50, and you add 1 ID rule, what's impact?

**Answer:** ID specificity (100) > all 1000 class rules (50 each). You'd need multiple IDs to override. Creates specificity debt. Hard to maintain. Avoid this approach. Use consistent specificity levels.

#### 15. Calculation: CSS file 500KB, with minification reduces to 150KB (70% reduction). With gzip compression reduces further to 30KB (94% reduction from original). Impact: faster initial load, reduced bandwidth usage.

---

## 📋 Quick Reference

| Property          | Values                                                    |
| ----------------- | --------------------------------------------------------- |
| `display`         | block, inline, inline-block, flex, grid, none             |
| `position`        | static, relative, absolute, fixed, sticky                 |
| `flex-direction`  | row, column, row-reverse, column-reverse                  |
| `align-items`     | flex-start, center, flex-end, stretch                     |
| `justify-content` | flex-start, center, flex-end, space-around, space-between |

| Optimization   | Benefit               |
| -------------- | --------------------- |
| Avoid reflows  | Better performance    |
| Use transforms | Hardware acceleration |
| Minify CSS     | Smaller file size     |
| Media queries  | Responsive design     |
| CSS variables  | DRY principle         |

---

### ❓ display: none vs visibility: hidden?

- display: none
  - Element is completely removed from layout
  - Element not rendered
- visibility: hidden
  - Element is invisible but space remains
  - Element still rendered
- Both make element non-interactive (no clicks possible)

### ❓ CSS Specificity (Lowest → Highest)

- CSS specificity determines priority of styles, where \* has the lowest priority and !important has the highest, overriding all other rules.
- CSS specificity decides which style will win when multiple rules apply.
  - Lowest Specificity → Universal Selector
  - Highest → !important
- Lowest → \* → element → class → ID → inline → !important → Highest

### ❓ Flexbox vs Grid (CSS)?

- Flexbox (1D Layout): Works in one direction only (row OR column) Ex. Navbar
- Grid (2D Layout): Works in rows AND columns together Ex. PageLayout

### ❓ pseudo-classes and pseudo-elements in CSS?

- Pseudo-classes define the state of an element, while pseudo-elements style a specific part of an element.
- Pseudo-classes target element states like hover or focus, while pseudo-elements style specific parts of an element like first letter, first line, or adding content before/after.

```css
/* pseudo-class */
button:hover {
  background: blue;
}

/* pseudo-element */
p::first-line {
  color: red;
}
```

```text
/* Pseudo-classes */
:hover
:focus
:nth-child(n)
:first-child
:last-child
:active
:checked
:disabled
:visited

/* Pseudo-elements */
::before
::after
::first-letter
::first-line
::selection
```

### ❓ different CSS position types?

- CSS position defines how an element is positioned in a document flow.

```text
static → normal flow
relative → shifted position
absolute → removed from flow, positioned to parent
fixed → fixed on screen
sticky → switches between relative & fixed on scroll
```

```css
.static {
  position: static;
}
.relative {
  position: relative;
  top: 10px;
}
.absolute {
  position: absolute;
  top: 0;
  right: 0;
}
.fixed {
  position: fixed;
  bottom: 0;
}
.sticky {
  position: sticky;
  top: 0;
}
```

### ❓

```css

```

### ❓

```css

```

### ❓

```css

```

### ❓

```css

```

### ❓

```css

```

### ❓

```css

```

### ❓

```css

```

### ❓

```css

```

### ❓

```css

```

### ❓

```css

```

### ❓

```css

```

### ❓

```css

```

### ❓

```css

```

---
