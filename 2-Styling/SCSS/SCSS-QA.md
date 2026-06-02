# SCSS – Interview Q&A

## � BASIC

**Q:** What is SCSS?
**A:** Syntactically Awesome StyleSheets. Superset of CSS with additional features. Compiles to standard CSS. Features: variables, nesting, mixins, functions. Improves CSS maintainability.

**Q:** What is the difference between SCSS and Sass?
**A:** Sass (indented syntax): no braces or semicolons, cleaner. SCSS: CSS-like syntax with braces and semicolons. Both compile to CSS. SCSS is more popular, easier for CSS developers.

**Q:** What are SCSS variables?
**A:** Store reusable values. Syntax: `$variable-name: value;`. Used with `$`. Scoped to selector. Example: `$primary-color: #3498db;` then `color: $primary-color;`.

**Q:** What is nesting in SCSS?
**A:** Nesting selectors inside parent selector. Creates hierarchy. Example: `.button { &:hover { color: red; } }`. Reduces repetition, improves organization. `&` refers to parent selector.

**Q:** What are SCSS mixins?
**A:** Reusable blocks of CSS rules. Define with `@mixin name() {}`. Include with `@include name();`. Can accept arguments. Example: `@mixin button($color) { background: $color; }`.

**Q:** What is the `&` selector?
**A:** References parent selector in nested rules. Example: `.button { &:hover {} }` compiles to `.button:hover {}`. Used for pseudo-classes, pseudo-elements, parent selectors.

**Q:** What are SCSS variables vs CSS custom properties?
**A:** SCSS: compile-time variables, scope limited. CSS custom properties: runtime variables, inherited, can be changed via JavaScript. Use SCSS for static values, CSS for dynamic.

**Q:** What is @import in SCSS?
**A:** Import other SCSS files. Syntax: `@import 'path/file'`. Files combined into single CSS file. Better than CSS @import (reduces HTTP requests). Use for file organization.

**Q:** What is the difference between `@extend` and `@include`?
**A:** `@include`: copies mixin code into selector (creates duplicate code). `@extend`: makes selector inherit from another (cleaner output). `@extend` preferred when possible.

**Q:** What is @extend?
**A:** Makes selector inherit styles from another selector. Syntax: `@extend .className;`. Cleaner than mixins for simple inheritance. Avoids code duplication in CSS output.

**Q:** What are SCSS functions?
**A:** Built-in functions for calculations, color operations, string manipulation. Examples: `lighten()`, `darken()`, `mix()`, `rgba()`, `length()`, `map-get()`. Create custom functions with `@function`.

**Q:** What is @media in SCSS?
**A:** Media query support same as CSS. Can be nested inside selectors. Example: `.element { @media (max-width: 768px) { color: red; } }`. Organizes responsive styles with selectors.

---

## � INTERMEDIATE

**Q:** What are SCSS maps?
**A:** Key-value pairs similar to objects. Syntax: `$map: (key: value, key: value)`. Access with `map-get($map, key)`. Useful for organizing related values, configuration.

**Q:** What is @for loop in SCSS?
**A:** Iterate specific number of times. Syntax: `@for $i from 1 through 10 { /* code */ }`. Generate classes, utilities dynamically. Example: generate `.mb-1` to `.mb-10` margin utilities.

**Q:** What is @each loop in SCSS?
**A:** Iterate through list or map. Syntax: `@each $item in $list { /* code */ }`. Useful for generating variants. Example: generate hover states for multiple colors.

**Q:** What is @while loop in SCSS?
**A:** Loop while condition true. Syntax: `@while $i > 0 { /* code */ $i: $i - 1; }`. Less common than @for and @each. Used for specific iteration patterns.

**Q:** What is @if, @else if, @else?
**A:** Conditional logic in SCSS. Syntax: `@if condition { } @else if condition { } @else { }`. Dynamically generate styles. Example: generate different styles for mobile vs desktop.

**Q:** What are SCSS lists?
**A:** Collection of values separated by space or comma. Syntax: `$list: value1 value2 value3;`. Access with `nth($list, 1)`. Iterate with `@each`. Used for managing related values.

**Q:** What is string interpolation (`#{}`)?
**A:** Embed variables or expressions in strings. Syntax: `#{$variable}`. Example: `background: url('#{$image-path}image.png');`. Essential for dynamic property values.

**Q:** What are SCSS color functions?
**A:** Built-in functions for color manipulation. Examples: `lighten($color, 10%)`, `darken($color, 10%)`, `saturate()`, `desaturate()`, `mix()`, `complement()`. Useful for theme generation.

**Q:** What is @mixin with arguments?
**A:** Mixins accepting parameters. Syntax: `@mixin box-shadow($x, $y, $blur) { box-shadow: $x $y $blur rgba(0,0,0,0.1); }`. Enables reusable patterns with variations.

**Q:** What is @mixin with rest arguments?
**A:** `@mixin name($args...) { }` collects multiple arguments. Used for variable-length argument lists. Less common but useful for flexible mixins.

**Q:** What is placeholder selectors (`%`)?
**A:** Class-like selector not compiled to CSS output. Syntax: `%placeholder { /* code */ }`. Extended with `@extend %placeholder`. Used for internal organization, no bloat in output.

**Q:** What is parent selector reference (`&`)?
**A:** Refers to parent selector. Used in nested rules. Examples: `&-modifier`, `&:hover`, `&::before`. Helps organize related selectors hierarchically.

---

## � ADVANCED

**Q:** Explain SCSS compilation process?
**A:** SCSS parsed into Abstract Syntax Tree (AST). Processed through various stages (variables, mixins, functions evaluated). Generated CSS output. Build tools (Webpack, Vite) automate compilation.

**Q:** What is Sass architecture (folder structure)?
**A:** Organized SCSS files by functionality. Common structure: `_variables.scss`, `_mixins.scss`, `_functions.scss`, `_base.scss`, `layout/`, `components/`, `pages/`. `_` prefix for partials (not compiled alone).

**Q:** What is SCSS nesting depth and why limit it?
**A:** Deep nesting creates specificity issues, readability problems, hard-to-maintain styles. Best practice: max 3 levels nesting. Forces modular thinking. Use mixins/functions for complex patterns.

**Q:** How do you avoid CSS specificity issues in SCSS?
**A:** Use mixins instead of @extend (avoid specificity wars). Keep nesting shallow (max 3 levels). Use consistent naming (BEM). Avoid IDs. Organize by component. Use sass-lint for validation.

**Q:** What is SCSS file organization best practice?
**A:** Create partials for each concern. `_variables.scss` for all variables. `_mixins.scss` for mixins. `components/` for component styles. Import in main.scss. Enables scalability, maintainability.

**Q:** What is DRY principle in SCSS?
**A:** Don't Repeat Yourself. Use variables for repeated values. Mixins for repeated code blocks. Functions for calculations. Reduces maintenance burden, improves readability, prevents bugs.

**Q:** How to optimize SCSS compilation size?
**A:** Remove unused code. Limit mixin usage (creates duplicate code). Use functions for one-off calculations. Compress output CSS. Tree-shake unused imports. Monitor compiled file size.

**Q:** What are SCSS functions vs mixins?
**A:** Functions return values (used in properties). Mixins output CSS code. Use functions for calculations/transformations. Use mixins for code blocks. Functions cleaner for computation.

**Q:** What is backwards compatibility in SCSS?
**A:** SCSS compiles to standard CSS. Works in all browsers supporting compiled CSS version. Use vendor prefixes for older browsers. Modern SCSS features may require newer compiler versions.

**Q:** What is namespace (@use) vs @import?
**A:** @import: global namespace, variables accessible everywhere. @use: namespace isolation, prevents conflicts. @use: `@use 'colors' as c;` then `c.$primary`. Modern approach, recommended.

**Q:** Real-life (Indian design system): Create comprehensive SCSS variables for branding?
**A:** Create `_variables.scss` with colors, typography, spacing, breakpoints. Example: `$primary-color`, `$font-family-base`, `$spacing-unit`, `$bp-mobile`, `$bp-tablet`. Use throughout components. Enables easy rebrand.

**Q:** Real-life: Build reusable button component using SCSS mixins?
**A:** Create `_button.mixin.scss` with size, color, disabled states. Use `@mixin button($size, $color) { /* styles */ }`. Include in different button classes. Generates clean CSS output.

**Q:** Real-life: Optimize SCSS for large project (1000+ components)?
**A:** Use file organization by feature. Create global variables, mixins, functions. Use namespace (@use) to avoid conflicts. Lazy-load component styles. Monitor compile time. Use sass-lint for consistency.

**Q:** Calculation: SCSS file 300 lines with 50 mixins. Each mixin used 10 times = 500 mixin insertions. Compared to CSS with repeated rules: SCSS generates cleaner code (same size compiled) but easier to maintain.

---

## 📋 Quick Reference

| Feature   | Syntax                                     |
| --------- | ------------------------------------------ |
| Variables | `$variable: value;`                        |
| Nesting   | `.parent { .child {} }`                    |
| Mixins    | `@mixin name() {}` then `@include name();` |
| Functions | `@function name() { @return value; }`      |
| @extend   | `@extend .selector;`                       |
| @import   | `@import 'file';`                          |
| Maps      | `$map: (key: value);`                      |
| @for      | `@for $i from 1 through 10 {}`             |
| @each     | `@each $item in $list {}`                  |
| @if       | `@if condition {}`                         |
