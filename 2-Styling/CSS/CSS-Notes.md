# 👉 CSS Fundamentals

## 📌 Overview

- **CSS** → Cascading Style Sheets used to style and layout web pages.
- **Rule** → `selector { property: value; }`
- **Cascade** → Determines which style rule applies.
- **Specificity** → Priority of selectors.

---

## 📌 CSS Syntax

| Part     | Purpose                    |
| -------- | -------------------------- |
| Selector | Targets HTML element       |
| Property | Style type                 |
| Value    | Property setting           |
| `:`      | Separates property & value |
| `;`      | Ends declaration           |
| `{}`     | Contains declarations      |

```css
selector {
  property: value;
}
```

---

## 📌 Applying CSS

| Method   | Usage       | Notes                                  |
| -------- | ----------- | -------------------------------------- |
| Inline   | `style=""`  | Highest specificity, avoid large usage |
| Internal | `<style>`   | Single page styling                    |
| External | `.css` file | Best practice, reusable                |

```html
<h1 style="color:red;">Inline CSS</h1>

<style>
  h1 {
    color: blue;
  }
</style>

<link rel="stylesheet" href="style.css" />
```

---

## 📌 Selectors

### Basic Selectors

| Selector  | Example         | Purpose              |
| --------- | --------------- | -------------------- |
| Element   | `p`             | Targets elements     |
| Class     | `.card`         | Reusable styling     |
| ID        | `#header`       | Unique element       |
| Universal | `*`             | Targets all elements |
| Attribute | `[type="text"]` | Targets attributes   |

```css
p {
}
.card {
}
#header {
}
```

### Combinators

| Selector         | Example   | Purpose                |
| ---------------- | --------- | ---------------------- |
| Descendant       | `div p`   | Nested elements        |
| Child            | `div > p` | Direct child           |
| Adjacent Sibling | `div + p` | Next sibling           |
| General Sibling  | `div ~ p` | All following siblings |

```css
.card > p {
  font-weight: bold;
}
```

### Pseudo Classes

| Selector       | Purpose              |
| -------------- | -------------------- |
| `:hover`       | Mouse hover          |
| `:focus`       | Focused element      |
| `:active`      | Active/click state   |
| `:checked`     | Checked input        |
| `:disabled`    | Disabled element     |
| `:first-child` | First child          |
| `:last-child`  | Last child           |
| `:nth-child()` | Specific child       |
| `:not()`       | Not apply to classes |

```css
button:hover {
  background: black;
}
```

### Pseudo Elements

| Selector        | Purpose               |
| --------------- | --------------------- |
| `::before`      | Insert before content |
| `::after`       | Insert after content  |
| `::placeholder` | Input placeholder     |
| `::selection`   | Selected text         |

```css
.card::before {
  content: "";
}
```

---

## 📌 Box Model

| Layer / Property | Purpose                 |
| ---------------- | ----------------------- |
| Content          | Actual element content  |
| Padding          | Space inside border     |
| Border           | Element border          |
| Margin           | Space outside element   |
| width / height   | Content size            |
| box-sizing       | Size calculation method |

```txt
content
padding
border
margin

content-box
border-box
```

```css
.box {
  width: 200px;
  padding: 20px;
  border: 2px solid black;
  margin: 30px;
  box-sizing: border-box;
}
```

---

## 📌 Specificity

| Selector Type                    | Priority Score |
| -------------------------------- | -------------- |
| Inline styles                    | 1000           |
| ID                               | 100            |
| Class / Attribute / Pseudo-class | 10             |
| Element / Pseudo-element         | 1              |
| Universal `*`                    | 0              |

```txt
!important
inline
#id
.class
element
*
```

- Avoid excessive specificity
- Prefer classes over IDs
- `!important` should be limited

---

## 📌 Units

| Unit | Type     | Purpose                      |
| ---- | -------- | ---------------------------- |
| px   | Absolute | Fixed size                   |
| %    | Relative | Relative to parent           |
| em   | Relative | Relative to parent font-size |
| rem  | Relative | Relative to root font-size   |
| vw   | Relative | Viewport width               |
| vh   | Relative | Viewport height              |
| vmin | Relative | Smaller viewport side        |
| vmax | Relative | Larger viewport side         |

```txt
Absolute:
px

Relative:
%
em
rem
vw
vh
vmin
vmax
```

- `rem` preferred for scalable typography
- `%` depends on parent size
- `vw/vh` useful for full-screen layouts
- Avoid excessive fixed `px` layouts

---

## 📌 Colors

| Format | Example                | Purpose                  |
| ------ | ---------------------- | ------------------------ |
| Named  | `red`                  | Simple colors            |
| Hex    | `#ff0000`              | Common web format        |
| RGB    | `rgb(255,0,0)`         | RGB values               |
| RGBA   | `rgba(255,0,0,0.5)`    | RGB with opacity         |
| HSL    | `hsl(0,100%,50%)`      | Hue/Saturation/Lightness |
| HSLA   | `hsla(0,100%,50%,0.5)` | HSL with opacity         |

```txt
color
background-color
opacity
currentColor
transparent
```

- Hex is most commonly used
- `rgba()` and `hsla()` useful for transparency
- Maintain proper color contrast for accessibility

---

## 📌 Functions

| Function           | Purpose                               |
| ------------------ | ------------------------------------- |
| `calc()`           | Perform calculations with mixed units |
| `min()`            | Uses smallest value                   |
| `max()`            | Uses largest value                    |
| `clamp()`          | Responsive min/max range              |
| `var()`            | Access CSS variables                  |
| `rgb()` / `rgba()` | RGB color values                      |
| `hsl()` / `hsla()` | HSL color values                      |
| `url()`            | External resources                    |
| `attr()`           | Element attribute value               |

```css
.card {
  width: calc(100% - 40px);
  font-size: clamp(14px, 2vw, 20px);
  color: var(--primary);
}
```

- `clamp()` useful for fluid typography
- `calc()` supports mixed units
- Spaces required around `+` and `-` in `calc()`
- `var()` improves maintainability

---

## 📌 CSS Methodologies

| Methodology | Full Form                             | Purpose                        |
| ----------- | ------------------------------------- | ------------------------------ |
| BEM         | Block Element Modifier                | Structured component naming    |
| OOCSS       | Object Oriented CSS                   | Reusable object-based styles   |
| SMACSS      | Scalable Modular Architecture for CSS | Categorized scalable CSS       |
| ITCSS       | Inverted Triangle CSS                 | Layered CSS organization       |
| Atomic CSS  | Utility-first CSS approach            | Single-purpose utility classes |

```css
/* BEM */
.card {
}
.card__title {
}
.card--active {
}

/* OOCSS */
.btn {
}
.rounded {
}

/* Atomic CSS */
.mt-4 {
}
.flex {
}
.text-center {
}
```

- BEM commonly used in component-based UI
- Atomic CSS popularized by Tailwind CSS
- Methodologies improve scalability & maintainability

## 📌 CSS Tooling

### CSS Preprocessors

| Preprocessor | Purpose                                | File Extension  |
| ------------ | -------------------------------------- | --------------- |
| SCSS / Sass  | Most popular advanced CSS preprocessor | `.scss` `.sass` |
| LESS         | Lightweight CSS preprocessor           | `.less`         |
| Stylus       | Flexible minimal syntax preprocessor   | `.styl`         |

```scss
$primary: #2563eb;

.button {
  background: $primary;
}
```

- Adds variables, nesting, mixins & functions
- Requires compilation into normal CSS
- SCSS is industry standard in most projects
- Native CSS now supports many modern alternatives

### PostCSS

| Tool / Plugin  | Purpose                | Common Usage            |
| -------------- | ---------------------- | ----------------------- |
| Autoprefixer   | Adds vendor prefixes   | Browser compatibility   |
| cssnano        | Minifies CSS           | Production optimization |
| Preset Env     | Modern CSS support     | Future CSS features     |
| PostCSS Import | CSS imports            | Modular CSS             |
| Tailwind CSS   | Utility CSS processing | Utility-first workflow  |

```js
module.exports = {
  plugins: {
    autoprefixer: {},
    cssnano: {},
  },
};
```

- CSS transformation tool using plugins
- Commonly used with build tools like Vite/Webpack
- Improves compatibility, optimization & workflow

### CSS Resets

| Reset Type       | Purpose                        | Common Usage              |
| ---------------- | ------------------------------ | ------------------------- |
| CSS Reset        | Removes browser default styles | Consistent layouts        |
| Normalize.css    | Preserves useful defaults      | Cross-browser consistency |
| Modern CSS Reset | Modern minimal reset approach  | Modern projects           |

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

- Reduces browser inconsistencies
- `border-box` commonly included
- Normalize.css safer than aggressive resets

---

## 📌 Inheritance Style

| Property Type | Common Examples                           | Behavior                               |
| ------------- | ----------------------------------------- | -------------------------------------- |
| Inherited     | `color` `font` `line-height` `text-align` | Passed from parent                     |
| Non-Inherited | `margin` `padding` `border` `width`       | Not passed automatically               |
| `inherit`     | `color: inherit`                          | Force parent value                     |
| `initial`     | `margin: initial`                         | Browser default value                  |
| `unset`       | `unset`                                   | Reset inherited/non-inherited behavior |
| `revert`      | `revert`                                  | Revert to browser/user styles          |

```css
body {
  color: #333;
  font-family: Arial;
}

.card {
  color: inherit;
}
```

- Typography-related properties commonly inherit
- Layout/spacing properties usually do not inherit
- `inherit` useful for reusable components

---

# 👉 CSS Properties

## 📌 Font Properties

| Property         | Purpose                  |
| ---------------- | ------------------------ |
| `font-family`    | Font type                |
| `font-size`      | Text size                |
| `font-weight`    | Font thickness           |
| `font-style`     | Italic/normal text       |
| `line-height`    | Line spacing             |
| `letter-spacing` | Space between letters    |
| `font-variant`   | Small caps/text variants |
| `font`           | Font shorthand           |

```css
body {
  font-family: Arial, Helvetica, sans-serif;
}
.text {
  font-family: "Poppins", sans-serif;
  letter-spacing: 1px;
}
```

---

## 📌 Text Properties

| Property          | Purpose                        |
| ----------------- | ------------------------------ |
| `text-align`      | Horizontal text alignment      |
| `text-transform`  | Uppercase/lowercase/capitalize |
| `text-decoration` | Underline/line styles          |
| `text-indent`     | First line spacing             |
| `text-overflow`   | Handle overflowing text        |
| `white-space`     | Text wrapping behavior         |
| `word-break`      | Word breaking control          |
| `overflow-wrap`   | Break long words               |
| `vertical-align`  | Inline/table alignment         |

```css
.title {
  text-align: center;
  text-transform: uppercase;
  text-decoration: underline;
}

.description {
  white-space: nowrap;
  text-overflow: ellipsis;
  overflow: hidden;
}
```

- `ellipsis` requires overflow hidden + nowrap
- Use proper line spacing for better UX

---

## 📌 Web Fonts

| Method         | Purpose                     |
| -------------- | --------------------------- |
| Google Fonts   | Hosted external fonts       |
| `@font-face`   | Self-hosted custom fonts    |
| CDN Fonts      | Third-party font delivery   |
| Variable Fonts | Multiple styles in one file |

```css
@font-face {
  font-family: "MyFont";
  src: url("./fonts/myfont.woff2") format("woff2");
}

body {
  font-family: "Poppins", sans-serif;
}
```

- Use `woff2` for better compression
- Always add fallback fonts

---

## 📌 Layout & Visibility

| Group      | Important Properties / Values                        | Purpose                |
| ---------- | ---------------------------------------------------- | ---------------------- |
| Box Model  | `margin` `padding` `border` `box-sizing`             | Spacing & box behavior |
| Sizing     | `width` `height` `min/max-*` `aspect-ratio`          | Element dimensions     |
| Display    | `block` `inline` `inline-block` `flex` `grid` `none` | Layout flow            |
| Position   | `static` `relative` `absolute` `fixed` `sticky`      | Element positioning    |
| Offset     | `top` `right` `bottom` `left` `z-index`              | Position adjustment    |
| Overflow   | `overflow` `overflow-x/y` `hidden` `scroll` `auto`   | Overflow handling      |
| Visibility | `visibility` `opacity` `display:none`                | Visibility control     |

- `border-box` preferred for layouts
- `flex` and `grid` are primary modern layouts
- `absolute` positions relative to nearest positioned parent

- `display:none` removes layout space
- `visibility:hidden` keeps layout space
- `opacity:0` keeps element interactive

---

## 📌 Flexbox

### Container Properties

| Property          | Common Values                                                                  |
| ----------------- | ------------------------------------------------------------------------------ |
| `display`         | `flex` `inline-flex`                                                           |
| `flex-direction`  | `row` `column` `row-reverse` `column-reverse`                                  |
| `flex-wrap`       | `nowrap` `wrap` `wrap-reverse`                                                 |
| `justify-content` | `flex-start` `center` `flex-end` `space-between` `space-around` `space-evenly` |
| `align-items`     | `stretch` `flex-start` `center` `flex-end` `baseline`                          |
| `align-content`   | `stretch` `center` `space-between` `space-around`                              |
| `gap`             | `10px` `1rem`                                                                  |

### Item Properties

| Property      | Common Values                           |
| ------------- | --------------------------------------- |
| `flex-grow`   | `0` `1`                                 |
| `flex-shrink` | `0` `1`                                 |
| `flex-basis`  | `auto` `200px` `50%`                    |
| `flex`        | `1` `auto` `none`                       |
| `order`       | `0` `1` `-1`                            |
| `align-self`  | `auto` `center` `flex-start` `flex-end` |

```css
.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 20px;
}

.item {
  flex: 1;
}
```

- `justify-content` → main axis alignment
- `align-items` → cross axis alignment
- `flex:1` creates flexible equal-width items
- `gap` preferred over margins

---

## 📌 CSS Grid

### Container Properties

| Property                | Common Values                    |
| ----------------------- | -------------------------------- |
| `display`               | `grid` `inline-grid`             |
| `grid-template-columns` | `1fr 1fr` `repeat(3,1fr)`        |
| `grid-template-rows`    | `auto` `200px` `1fr`             |
| `grid-template-areas`   | `"header header"`                |
| `gap`                   | `10px` `1rem`                    |
| `row-gap`               | `10px`                           |
| `column-gap`            | `10px`                           |
| `justify-items`         | `start` `center` `end` `stretch` |
| `align-items`           | `start` `center` `end` `stretch` |
| `justify-content`       | `start` `center` `space-between` |
| `align-content`         | `start` `center` `space-between` |
| `grid-auto-columns`     | `auto` `1fr`                     |
| `grid-auto-rows`        | `auto` `100px`                   |
| `grid-auto-flow`        | `row` `column` `dense`           |

### Item Properties

| Property       | Common Values                    |
| -------------- | -------------------------------- |
| `grid-column`  | `1 / 3` `span 2`                 |
| `grid-row`     | `1 / 2` `span 2`                 |
| `grid-area`    | `header` `1 / 1 / 3 / 3`         |
| `justify-self` | `start` `center` `end` `stretch` |
| `align-self`   | `start` `center` `end` `stretch` |

```css
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}

.item {
  grid-column: span 2;
}
```

```css
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
}
```

- Best for two-dimensional layouts
- `fr` = fractional space unit
- `repeat()` simplifies repeated columns
- `minmax()` useful for responsive grids

---

## 📌 Display

| Property / Value | Affects                      |
| ---------------- | ---------------------------- |
| `block`          | Full-width block element     |
| `inline`         | Inline flow without sizing   |
| `inline-block`   | Inline element with sizing   |
| `flex`           | One-dimensional layout       |
| `inline-flex`    | Inline flex container        |
| `grid`           | Two-dimensional layout       |
| `inline-grid`    | Inline grid container        |
| `flow-root`      | New block formatting context |
| `contents`       | Removes wrapper box          |
| `list-item`      | List-style behavior          |
| `table`          | Table layout behavior        |
| `table-row`      | Table row display            |
| `table-cell`     | Table cell display           |
| `none`           | Removes from layout          |

```css
.container {
  display: flex;
}
```

- `flex` and `grid` are primary modern layouts
- `inline` ignores width/height
- `display:none` removes layout space
- `flow-root` useful for clearing floats

---

## 📌 Backgrounds

| Property                | Common Values               |
| ----------------------- | --------------------------- |
| `background`            | Shorthand property          |
| `background-color`      | `#fff` `transparent`        |
| `background-image`      | `url()` `linear-gradient()` |
| `background-size`       | `cover` `contain`           |
| `background-position`   | `center` `top`              |
| `background-repeat`     | `no-repeat` `repeat`        |
| `background-attachment` | `scroll` `fixed`            |
| `background-origin`     | `padding-box` `border-box`  |
| `background-clip`       | `padding-box` `text`        |
| `background-blend-mode` | `multiply` `overlay`        |

```css
.hero {
  background-image: linear-gradient(#0006, #0006), url("bg.jpg");
  background-size: cover;
  background-position: center;
}
```

- `cover` commonly used for hero sections
- Gradients often used as overlays

---

## 📌 Borders & Outline

| Property          | Common Values           |
| ----------------- | ----------------------- |
| `border`          | `1px solid #ddd`        |
| `border-width`    | `1px` `2px`             |
| `border-style`    | `solid` `dashed` `none` |
| `border-color`    | `#000` `transparent`    |
| `border-radius`   | `8px` `50%`             |
| `border-collapse` | `collapse` `separate`   |
| `outline`         | `none` `2px solid blue` |
| `outline-offset`  | `2px`                   |

- `border-radius:50%` creates circles
- `outline` does not affect layout size

---

## 📌 Shadows

| Property      | Common Values       |
| ------------- | ------------------- |
| `box-shadow`  | `0 4px 10px rgba()` |
| `text-shadow` | `1px 1px 2px #000`  |

```css
.card {
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}
```

- Avoid excessive heavy shadows
- Multiple shadows can be layered

---

## 📌 Images & Media

| Property          | Common Values                         |
| ----------------- | ------------------------------------- |
| `object-fit`      | `cover` `contain` `fill` `none`       |
| `object-position` | `center` `top`                        |
| `aspect-ratio`    | `16 / 9` `1 / 1`                      |
| `filter`          | `blur()` `grayscale()` `brightness()` |
| `backdrop-filter` | `blur()`                              |
| `image-rendering` | `auto` `pixelated`                    |
| `mix-blend-mode`  | `multiply` `screen`                   |

```css
img {
  aspect-ratio: 16 / 9;
  object-fit: cover;
  object-position: center;
}
```

- `object-fit:cover` common for cards/heroes
- `aspect-ratio` helps prevent layout shift
- `backdrop-filter` has limited browser support

---

## 📌 Interaction Properties

| Property         | Common Values                  | Purpose                 |
| ---------------- | ------------------------------ | ----------------------- |
| `cursor`         | `pointer` `not-allowed` `grab` | Mouse interaction state |
| `user-select`    | `none` `text` `all`            | Text selection control  |
| `pointer-events` | `none` `auto`                  | Mouse event handling    |

```css
.button {
  cursor: pointer;
  user-select: none;
}

.disabled {
  pointer-events: none;
  cursor: not-allowed;
}
```

- `pointer` used for clickable elements
- `user-select:none` common for buttons/UI
- `pointer-events:none` disables interaction

---

## 📌 Transitions

| Property                     | Common Values                 |
| ---------------------------- | ----------------------------- |
| `transition-property`        | `all` `opacity` `transform`   |
| `transition-duration`        | `0.3s` `500ms`                |
| `transition-timing-function` | `ease` `linear` `ease-in-out` |
| `transition-delay`           | `0s` `0.2s`                   |
| `transition`                 | Shorthand property            |

```css
.button {
  transition: background 0.3s ease;
}

.button:hover {
  background: black;
}
```

- Use `transform` & `opacity` for smoother animations
- Avoid transitioning expensive properties
- `ease` most commonly used timing function

---

## 📌 Transform

| Function           | Purpose                     |
| ------------------ | --------------------------- |
| `translate()`      | Move element                |
| `translateX/Y()`   | Move on single axis         |
| `scale()`          | Resize element              |
| `rotate()`         | Rotate element              |
| `skew()`           | Skew element                |
| `transform-origin` | Transformation anchor point |
| `transform`        | Combine transformations     |

```css
.card {
  transform: translateY(-10px) scale(1.05);
}
```

- Multiple transforms can be combined
- `transform` does not affect document flow
- GPU accelerated in most browsers

---

## 📌 CSS Animation

| Property                    | Common Values          |
| --------------------------- | ---------------------- |
| `@keyframes`                | Animation frames       |
| `animation-name`            | `fade` `slide`         |
| `animation-duration`        | `1s` `500ms`           |
| `animation-timing-function` | `ease` `linear`        |
| `animation-delay`           | `0s` `1s`              |
| `animation-iteration-count` | `1` `infinite`         |
| `animation-direction`       | `normal` `alternate`   |
| `animation-fill-mode`       | `forwards` `backwards` |
| `animation-play-state`      | `running` `paused`     |
| `animation`                 | Shorthand property     |

```css
@keyframes fade {
  from {
    opacity: 0;
  }

  to {
    opacity: 1;
  }
}

.box {
  animation: fade 1s ease infinite;
}
```

- Prefer `transform` & `opacity` for performance
- Avoid excessive infinite animations
- `forwards` keeps final animation state

---

## 📌 Media Queries & Mobile First

| Feature                  | Common Values / Examples |
| ------------------------ | ------------------------ |
| `width` / `height`       | `min-width:768px`        |
| `orientation`            | `portrait` `landscape`   |
| `hover`                  | `hover` `none`           |
| `pointer`                | `fine` `coarse`          |
| `aspect-ratio`           | `16/9`                   |
| `prefers-color-scheme`   | `dark` `light`           |
| `prefers-reduced-motion` | `reduce`                 |
| `print`                  | Print styles             |
| `screen`                 | Screen devices           |

```css
/* Mobile First */
.container {
}

/* Tablet */
@media (min-width: 768px) {
}

/* Desktop */
@media (min-width: 1024px) {
}

/* Dark Mode */
@media (prefers-color-scheme: dark) {
}
```

- Mobile First → start from smaller screens
- `min-width` preferred for scalable responsive design
- `pointer:coarse` useful for touch devices
- `prefers-reduced-motion` improves accessibility
- `print` media used for printable layouts

---

## 📌 Lists

| Property              | Common Values          | Affects            |
| --------------------- | ---------------------- | ------------------ |
| `list-style-type`     | `disc` `circle` `none` | Bullet type        |
| `list-style-position` | `inside` `outside`     | Marker placement   |
| `list-style-image`    | `url()`                | Custom markers     |
| `list-style`          | Shorthand              | Full list styling  |
| `marker-side`         | `match-parent`         | Marker positioning |

```css
ul {
  list-style: none;
}
```

---

## 📌 Tables

| Property          | Common Values         | Affects               |
| ----------------- | --------------------- | --------------------- |
| `border-collapse` | `collapse` `separate` | Border merging        |
| `border-spacing`  | `0` `10px`            | Cell spacing          |
| `table-layout`    | `auto` `fixed`        | Column sizing         |
| `caption-side`    | `top` `bottom`        | Caption position      |
| `empty-cells`     | `show` `hide`         | Empty cell visibility |
| `vertical-align`  | `top` `middle`        | Cell alignment        |

```css
table {
  border-collapse: collapse;
}
```

---

## 📌 Scroll

| Property              | Common Values    | Affects                  |
| --------------------- | ---------------- | ------------------------ |
| `scroll-behavior`     | `smooth` `auto`  | Scroll animation         |
| `scroll-snap-type`    | `x mandatory`    | Snap container           |
| `scroll-snap-align`   | `start` `center` | Snap position            |
| `overscroll-behavior` | `contain` `none` | Scroll chaining          |
| `scroll-margin`       | `20px`           | Snap offset              |
| `scroll-padding`      | `20px`           | Scroll container spacing |
| `scrollbar-width`     | `auto` `none`    | Scrollbar thickness      |
| `scrollbar-color`     | `#000 #fff`      | Scrollbar colors         |

```css
html {
  scroll-behavior: smooth;
}
```

---

## 📌 Multi Columns

| Property       | Common Values    | Affects               |
| -------------- | ---------------- | --------------------- |
| `columns`      | `2` `300px`      | Multi-column layout   |
| `column-count` | `2` `3`          | Number of columns     |
| `column-gap`   | `20px`           | Column spacing        |
| `column-rule`  | `1px solid #ddd` | Column divider        |
| `column-fill`  | `auto` `balance` | Content balancing     |
| `column-span`  | `all`            | Cross-column spanning |

```css
.content {
  columns: 2;
}
```

---

## 📌 Object & Blend

| Property                | Common Values       | Affects             |
| ----------------------- | ------------------- | ------------------- |
| `object-fit`            | `cover` `contain`   | Media fitting       |
| `object-position`       | `center`            | Media alignment     |
| `mix-blend-mode`        | `multiply` `screen` | Layer blending      |
| `background-blend-mode` | `overlay`           | Background blending |
| `isolation`             | `isolate`           | Blend isolation     |

```css
img {
  object-fit: cover;
}
```

---

## 📌 Form Element Properties

| Property / Selector      | Common Values                  | Affects                          |
| ------------------------ | ------------------------------ | -------------------------------- |
| `appearance`             | `none`                         | Removes native UI styling        |
| `accent-color`           | `#2563eb`                      | Checkbox/radio/range color       |
| `caret-color`            | `red`                          | Text cursor color                |
| `resize`                 | `none` `vertical` `horizontal` | Textarea resizing                |
| `outline`                | `none` `2px solid`             | Focus outline                    |
| `outline-offset`         | `2px`                          | Outline spacing                  |
| `cursor`                 | `pointer` `text`               | Interaction state                |
| `pointer-events`         | `none` `auto`                  | Mouse interaction                |
| `user-select`            | `none` `text`                  | Text selection                   |
| `field-sizing`           | `content` `fixed`              | Auto field sizing                |
| `ime-mode`               | `auto` `disabled`              | IME input control _(deprecated)_ |
| `::placeholder`          | Placeholder styling            | Input hint text                  |
| `::file-selector-button` | File button styling            | File input button                |
| `::selection`            | Selected text styling          | Text selection                   |
| `:focus`                 | Focus state                    | Active field styling             |
| `:focus-visible`         | Keyboard focus                 | Accessible focus styling         |
| `:focus-within`          | Parent focus detection         | Group/form focus                 |
| `:disabled`              | Disabled state                 | Disabled controls                |
| `:enabled`               | Enabled state                  | Active controls                  |
| `:checked`               | Checked state                  | Checkbox/radio                   |
| `:indeterminate`         | Partial checked state          | Mixed checkbox state             |
| `:valid`                 | Valid input                    | Validation UI                    |
| `:invalid`               | Invalid input                  | Error styling                    |
| `:required`              | Required fields                | Required inputs                  |
| `:optional`              | Optional fields                | Optional inputs                  |
| `:read-only`             | Read-only fields               | Locked editing                   |
| `:read-write`            | Editable fields                | Editable inputs                  |
| `:placeholder-shown`     | Placeholder visible            | Empty field state                |
| `:autofill`              | Autofilled input               | Browser autofill styling         |

```css
input {
  appearance: none;
  accent-color: #2563eb;
}

input:focus-visible {
  outline: 2px solid blue;
}

input:invalid {
  border-color: red;
}
```

- Never remove focus styles without replacement
- `accent-color` simplifies native form styling
- Validation pseudo-classes improve UX
- `appearance:none` commonly used for custom UI

---

## 📌 Appearance & UI

| Property         | Common Values     | Affects            |
| ---------------- | ----------------- | ------------------ |
| `appearance`     | `none`            | Native UI styling  |
| `accent-color`   | `blue` `#2563eb`  | Form control color |
| `caret-color`    | `red`             | Text cursor color  |
| `resize`         | `none` `vertical` | Resize behavior    |
| `outline-offset` | `2px`             | Outline spacing    |
| `touch-action`   | `none` `pan-x`    | Touch gestures     |

```css
input {
  accent-color: #2563eb;
}
```

---

## 📌 Writing & Content

| Property            | Common Values | Affects                   |
| ------------------- | ------------- | ------------------------- |
| `writing-mode`      | `vertical-rl` | Text flow direction       |
| `text-orientation`  | `upright`     | Vertical text orientation |
| `content`           | `""` `"Text"` | Generated content         |
| `quotes`            | `none`        | Quote styling             |
| `counter-reset`     | `section`     | Counter initialization    |
| `counter-increment` | `section`     | Counter incrementing      |

```css
.card::before {
  content: "";
}
```

---

## 📌 Modern Layout

| Property                 | Common Values    | Affects               |
| ------------------------ | ---------------- | --------------------- |
| `contain`                | `layout` `paint` | Rendering isolation   |
| `content-visibility`     | `auto`           | Render optimization   |
| `contain-intrinsic-size` | `300px`          | Placeholder sizing    |
| `container-type`         | `inline-size`    | Container query scope |
| `container-name`         | `sidebar`        | Named query container |

```css
.card-container {
  container-type: inline-size;
}
```

- Mostly advanced/specialized features
- Useful for scalable modern UI systems

---

## 📌 SVG Styling

| Property            | Common Values               | Affects                |
| ------------------- | --------------------------- | ---------------------- |
| `fill`              | `red` `none` `currentColor` | Shape fill color       |
| `stroke`            | `#000` `none`               | Stroke color           |
| `stroke-width`      | `1` `2` `4`                 | Stroke thickness       |
| `stroke-linecap`    | `round` `square`            | Stroke edge style      |
| `stroke-linejoin`   | `round` `bevel`             | Stroke corner style    |
| `stroke-dasharray`  | `5 5`                       | Dashed stroke pattern  |
| `stroke-dashoffset` | `10`                        | Dash animation offset  |
| `opacity`           | `0`–`1`                     | Overall transparency   |
| `fill-opacity`      | `0`–`1`                     | Fill transparency      |
| `stroke-opacity`    | `0`–`1`                     | Stroke transparency    |
| `vector-effect`     | `non-scaling-stroke`        | Prevent stroke scaling |
| `transform`         | `scale()` `rotate()`        | SVG transformations    |
| `filter`            | `blur()` `drop-shadow()`    | SVG effects            |

```css
svg path {
  fill: currentColor;
  stroke: #000;
  stroke-width: 2;
}
```

- `currentColor` syncs SVG with text color
- SVG supports CSS animations/transforms
- `stroke-dasharray` commonly used for line animations

---

## 📌 Modern CSS Features

| Feature / Property     | Common Values            | Affects                   |
| ---------------------- | ------------------------ | ------------------------- |
| `:is()`                | `:is(h1,h2)`             | Selector grouping         |
| `:where()`             | `:where(.card)`          | Zero specificity grouping |
| `:has()`               | `div:has(img)`           | Parent-aware selector     |
| `@layer`               | `base` `components`      | Cascade layer control     |
| `@scope`               | Scoped selectors         | Local styling scope       |
| `subgrid`              | `subgrid`                | Nested grid inheritance   |
| `color-mix()`          | `color-mix(in srgb,...)` | Dynamic color blending    |
| `view-transition-name` | `card`                   | Page/view transitions     |
| `anchor-name`          | `--tooltip`              | Anchor positioning        |
| `position-anchor`      | `--tooltip`              | Positioned anchor linking |

```css
.card-list:has(.active) {
  border-color: blue;
}
```

- `:has()` enables parent-based styling
- `@layer` improves cascade management
- `subgrid` improves nested grid alignment
- Anchor positioning is part of newer CSS specs

---

## 📌 Practical Utility CSS Structure

| Group      | Common Utility Patterns                     | Affects             |
| ---------- | ------------------------------------------- | ------------------- |
| Layout     | `.flex` `.grid` `.block` `.hidden`          | Layout system       |
| Flex/Grid  | `.items-center` `.justify-between` `.gap-4` | Alignment & spacing |
| Spacing    | `.m-4` `.mx-auto` `.p-6`                    | Margin & padding    |
| Sizing     | `.w-full` `.max-w-xl` `.h-screen`           | Width & height      |
| Typography | `.text-lg` `.font-bold` `.leading-6`        | Text styling        |
| Colors     | `.bg-blue-500` `.text-white`                | Color styling       |
| Borders    | `.rounded-lg` `.border`                     | Border styling      |
| Effects    | `.shadow-md` `.opacity-50`                  | Visual effects      |
| Position   | `.relative` `.absolute` `.z-10`             | Positioning         |
| Responsive | `.md:flex` `.lg:grid-cols-4`                | Breakpoint styling  |
| State      | `.hover:bg-black` `.focus:ring-2`           | Interaction states  |

```html
<div class="flex items-center justify-between p-4 rounded-lg shadow-md">
  Content
</div>
```

- Utility classes grouped by responsibility
- Inspired by Tailwind CSS architecture
- Most practical atomic systems use:
  - spacing scale
  - color tokens
  - responsive variants
  - state modifiers
- Avoid random inconsistent utility naming

---

## 📌 Accessibility

| Property / Feature | Common Values    | Affects              |
| ------------------ | ---------------- | -------------------- |
| `outline`          | `2px solid blue` | Focus visibility     |
| `outline-offset`   | `2px`            | Focus spacing        |
| `:focus-visible`   | Focus state      | Keyboard navigation  |
| `accent-color`     | `#2563eb`        | Form control styling |

```css
button:focus-visible {
  outline: 2px solid blue;
  outline-offset: 2px;
}
```

- Never remove focus styles without replacement
- Maintain proper color contrast

---

## 📌 Responsive Accessibility

| Feature                  | Common Values   | Affects                |
| ------------------------ | --------------- | ---------------------- |
| `prefers-reduced-motion` | `reduce`        | Motion accessibility   |
| `prefers-color-scheme`   | `dark` `light`  | Theme preference       |
| `prefers-contrast`       | `more` `less`   | Contrast accessibility |
| `pointer`                | `coarse` `fine` | Touch/mouse detection  |
| `hover`                  | `hover` `none`  | Hover capability       |
| `scroll-behavior`        | `smooth` `auto` | Scroll experience      |

```css
@media (prefers-reduced-motion: reduce) {
  * {
    animation: none;
  }
}
```

- Respect user accessibility preferences
- Responsive accessibility improves usability across devices

---

# 👉 CSS Performance

## 📌 Performance Tips

| Technique / Property     | Use                       | Avoid / Alternative         |
| ------------------------ | ------------------------- | --------------------------- |
| `transform`              | Smooth animations         | Avoid `top/left` animation  |
| `opacity`                | Efficient fading          | Avoid repaint-heavy effects |
| `will-change`            | Complex animations        | Remove after use            |
| `contain`                | Isolated rendering        | Avoid global overuse        |
| `content-visibility`     | Skip offscreen rendering  | Partial browser support     |
| `translate3d()`          | GPU acceleration          | Avoid unnecessary layers    |
| `font-display`           | Faster text rendering     | Avoid blocked text          |
| `prefers-reduced-motion` | Accessibility/performance | Avoid forced animations     |
| `loading="lazy"`         | Delay image loading       | Avoid loading hidden media  |
| `aspect-ratio`           | Prevent layout shift      | Avoid JS placeholders       |

```css
/* top → transform */
top: -5px;
transform: translateY(-5px);

/* width/height → scale */
width: 220px;
transform: scale(1.1);

/* display toggle → opacity */
display: none;
opacity: 0;

/* large blur → subtle shadow */
filter: blur(20px);
box-shadow: 0 2px 8px rgba(0,0,0,0.1);

/* immediate image load → lazy load */
<img src="image.jpg">
<img loading="lazy" src="image.jpg">
```

- Prefer `transform` & `opacity` for animations
- Reduce repaint/reflow heavy properties
- Optimize fonts, images & DOM size

---

## 📌 CSS Variables

| Property / Function | Common Values          | Affects                |
| ------------------- | ---------------------- | ---------------------- |
| `--variable-name`   | `--primary`            | Custom reusable values |
| `var()`             | `var(--primary)`       | Access variable values |
| Fallback            | `var(--primary, blue)` | Default fallback value |
| `:root`             | Global scope           | App-wide variables     |
| Local Variables     | Component scope        | Scoped styling         |

```css
:root {
  --primary: #2563eb;
  --radius: 12px;
}

.button {
  background: var(--primary);
  border-radius: var(--radius);
}
```

- Improves consistency & maintainability
- Useful for theming/design systems
- Variables can be overridden locally
- Native CSS alternative to SCSS variables

---

## 📌 Atomic Design Structure

| Layer         | Common Examples                  | Responsibility         |
| ------------- | -------------------------------- | ---------------------- |
| Design Tokens | colors, spacing, typography      | Shared design values   |
| Utilities     | `.flex` `.mt-4` `.hidden`        | Global helper classes  |
| Atoms         | `button` `input` `icon`          | Basic UI elements      |
| Molecules     | `search-form` `input-group`      | Combined atoms         |
| Organisms     | `navbar` `card-grid` `sidebar`   | Complex UI sections    |
| Templates     | `dashboard-layout` `auth-layout` | Page structure/layout  |
| Pages         | `home-page` `product-page`       | Final composed screens |

```html
<div class="card-grid">
  <button class="btn mt-4">Save</button>
</div>
```

- Design Tokens & Utilities support all layers
- Atomic Design focuses on component composition
- Common in scalable design systems/component architectures

---

## 📌 CSS Prefixes

| Prefix     | Browser            | Example               |
| ---------- | ------------------ | --------------------- |
| `-webkit-` | Chrome Safari Edge | `-webkit-user-select` |
| `-moz-`    | Firefox            | `-moz-appearance`     |
| `-ms-`     | Internet Explorer  | `-ms-overflow-style`  |
| `-o-`      | Old Opera          | `-o-object-fit`       |

```css
.element {
  -webkit-user-select: none;
  -moz-user-select: none;
  user-select: none;
}
```

- Used for experimental/older browser support
- Modern projects usually use Autoprefixer
- Standard property should always be last

---

## 📌 Current Standard CSS

| Feature / Section       | Status              | Common Usage             |
| ----------------------- | ------------------- | ------------------------ |
| Flexbox                 | Standard            | One-dimensional layouts  |
| CSS Grid                | Standard            | Two-dimensional layouts  |
| Responsive Design       | Standard            | Mobile-first UI          |
| CSS Variables           | Standard            | Design systems/theming   |
| Transitions & Transform | Standard            | UI interactions          |
| Animations              | Standard            | Motion effects/loaders   |
| Utility CSS             | Standard / Trending | Tailwind-style workflow  |
| Accessibility           | Essential           | Modern UI requirement    |
| SVG Styling             | Standard            | Icons/charts             |
| PostCSS                 | Standard Tooling    | Autoprefixer/cssnano     |
| SCSS/Sass               | Common              | Large-scale styling      |
| CSS Reset / Normalize   | Standard            | Browser consistency      |
| Container Queries       | Modern Standard     | Component responsiveness |
| `:has()` Selector       | Modern Standard     | Parent-aware styling     |

```css
.container {
  display: grid;
  gap: 20px;
}
```

- Modern CSS focuses on Flexbox, Grid & Responsive Design
- Utility-first workflow increasingly common
- Native CSS replacing many older preprocessors/features

---

## 📌 Deprecated / Legacy CSS

| Feature / Technique     | Status            | Modern Alternative    |
| ----------------------- | ----------------- | --------------------- |
| Float Layouts           | Legacy            | Flexbox / Grid        |
| Table-based Layouts     | Legacy            | Flexbox / Grid        |
| IE-specific Hacks       | Deprecated        | Modern standards      |
| `-ms-` / `-o-` Prefixes | Deprecated        | Autoprefixer          |
| Heavy Vendor Prefixes   | Mostly Deprecated | Standard CSS          |
| `zoom` Layout Hacks     | Deprecated        | Flex/Grid sizing      |
| Old clearfix hacks      | Mostly Legacy     | `flow-root` Flex/Grid |
| LESS                    | Declining         | SCSS / Native CSS     |
| Stylus                  | Rare              | SCSS / Native CSS     |

- Flexbox & Grid replaced most float hacks
- Autoprefixer handles browser compatibility
- Legacy techniques mostly remain in old projects

---

## 📌 Best Practices

| Practice                | Purpose               |
| ----------------------- | --------------------- |
| Prefer classes over IDs | Lower specificity     |
| Use Flexbox/Grid        | Modern layouts        |
| Use CSS Variables       | Reusable values       |
| Mobile-first design     | Better responsiveness |
| Use `border-box`        | Predictable sizing    |
| Keep specificity low    | Easier maintenance    |
| Avoid excessive nesting | Cleaner CSS           |
| Minimize `!important`   | Easier overrides      |
| Maintain accessibility  | Better usability      |

```css
* {
  box-sizing: border-box;
}
```

- Focus on scalable & maintainable CSS
- Prefer reusable component-based styling

---

## 📌 Scalability & Maintainability

| Practice                | Purpose                    |
| ----------------------- | -------------------------- |
| Modular components      | Reusable scalable UI       |
| Consistent naming       | Predictable CSS structure  |
| Low specificity         | Easier overrides           |
| Design tokens/variables | Centralized design values  |
| Utility helpers         | Shared common styles       |
| File separation         | Organized architecture     |
| Methodologies           | Structured large-scale CSS |

```css
.card__title {
  font-size: 20px;
}
```

- Prefer reusable component-based styling
- Keep CSS predictable & loosely coupled
- Important for large/team-based projects

---
