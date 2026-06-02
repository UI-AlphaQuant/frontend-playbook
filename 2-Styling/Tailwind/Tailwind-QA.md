# Tailwind CSS – Interview Q&A

## � BASIC

**Q:** What is Tailwind CSS?
**A:** Utility-first CSS framework. Provides predefined utility classes for styling. Classes like `text-red-500`, `p-4`, `flex`. Alternative to component-based frameworks. Faster development, smaller CSS with PurgeCSS.

**Q:** What does utility-first mean?
**A:** Building UI by composing small utility classes instead of writing custom CSS. Example: `<div class="flex justify-center items-center">` instead of `.container { display: flex; }`. Reusable, consistent, predictable.

**Q:** What is the difference between Tailwind and Bootstrap?
**A:** Bootstrap: component-based (buttons, modals pre-styled). Tailwind: utility-based (compose utilities). Bootstrap: faster for beginners. Tailwind: more flexible, smaller bundle, modern approach.

**Q:** What are Tailwind utility classes?
**A:** Pre-defined classes for common CSS properties. Examples: `w-full` (width: 100%), `bg-blue-500` (background color), `p-4` (padding), `text-center` (text alignment). Combine to create designs.

**Q:** What is responsive design in Tailwind?
**A:** Mobile-first approach. Breakpoints: `sm`, `md`, `lg`, `xl`, `2xl`. Usage: `md:text-2xl` applies style on medium screens and up. Easy responsive design without media queries.

**Q:** What are Tailwind breakpoints?
**A:** `sm`: 640px, `md`: 768px, `lg`: 1024px, `xl`: 1280px, `2xl`: 1536px. Mobile-first: styles apply to all widths by default. Add prefix to apply from breakpoint upward. Example: `md:p-8`.

**Q:** What is `@apply` directive?
**A:** Extract utility classes into custom CSS classes. Syntax: `.btn { @apply px-4 py-2 bg-blue-500 text-white rounded; }`. Used to create reusable components. Bridges custom and utility CSS.

**Q:** What is configuration in Tailwind?
**A:** `tailwind.config.js` file customizing framework. Override colors, fonts, spacing, add new utilities. Example: `theme: { colors: { primary: '#3498db' } }`. Enables brand customization.

**Q:** What are Tailwind dark mode?
**A:** Apply different styles for dark mode. Usage: `dark:bg-gray-800`. Requires configuration: `darkMode: 'class'` or `'media'`. Adds dark variants to utilities. Better UX for users.

**Q:** What is arbitrary values in Tailwind?
**A:** Custom values not in configuration. Usage: `w-[500px]`, `text-[#1a2b3c]`, `top-[117px]`. Enables one-off customization without config changes. Modern Tailwind 3+ feature.

**Q:** What are pseudo-class variants?
**A:** Apply utilities on specific states. Examples: `hover:`, `focus:`, `active:`, `disabled:`, `group-hover:`. Usage: `hover:bg-blue-600`, `focus:ring-2`. Enables state-based styling.

**Q:** What are pseudo-element variants?
**A:** Style pseudo-elements with utilities. Examples: `before:`, `after:`, `first-line:`, `first-letter:`. Usage: `before:content-['']`, `after:block`. Replaces `::before`, `::after` CSS.

**Q:** What is content configuration?
**A:** `content` array in config specifying which files to scan for utility classes. Examples: `['./src/**/*.{js,jsx}']`. Enables PurgeCSS to remove unused styles. Critical for optimized build size.

---

## � INTERMEDIATE

**Q:** What is PurgeCSS in Tailwind?
**A:** Removes unused CSS classes from final build. Enabled by default with `content` configuration. Production builds ~50KB vs dev ~1MB. Scans HTML/JSX for class names.

**Q:** What are Tailwind plugins?
**A:** Extend Tailwind with custom utilities. Syntax: `plugins: [require('@tailwindcss/forms')]`. Official plugins: forms, typography, aspect-ratio. Create custom plugins for brand utilities.

**Q:** What is @tailwind directive?
**A:** Imports Tailwind layers into CSS. Syntax: `@tailwind base;`, `@tailwind components;`, `@tailwind utilities;`. Used in main CSS file. Enables customization with @layer.

**Q:** What is @layer directive?
**A:** Add custom styles to specific layer (base, components, utilities). Syntax: `@layer utilities { .custom { /* styles */ } }`. Respects Tailwind specificity. Keeps organized approach.

**Q:** What are Tailwind layers?
**A:** Three layers: `base` (resets, defaults), `components` (reusable classes), `utilities` (single property). Using layers properly ensures correct CSS specificity and cascading order.

**Q:** What is group utility in Tailwind?
**A:** Apply styles to child elements when parent hovered. Syntax: `<div class="group"> <div class="group-hover:text-blue-500">`. Used for interactive components without JavaScript.

**Q:** What is whitespace and space utilities?
**A:** `space-x-4`: adds horizontal gap between children. `space-y-4`: adds vertical gap. `whitespace-nowrap`: prevents text wrapping. `whitespace-pre-wrap`: preserves whitespace. Essential for layout.

**Q:** What are Tailwind animation utilities?
**A:** Pre-built animations: `animate-spin`, `animate-ping`, `animate-pulse`, `animate-bounce`. Usage: `<div class="animate-spin">`. Limited, extend with config for custom animations.

**Q:** What is container query in Tailwind?
**A:** Style based on container width not viewport. Newer feature (Tailwind 3.2+). Usage: `@container size-sm` then `@sm:text-lg`. Better for component-based design than media queries.

**Q:** What are Tailwind forms plugin?
**A:** Official plugin styling form elements consistently. Provides: `@apply` styles for inputs, selects, checkboxes. Usage: `<input class="form-input">`. Saves time styling forms.

**Q:** What are Tailwind typography plugin?
**A:** Provides `prose` class for rich text content. Automatically styles markdown/blog content. Usage: `<article class="prose">`. Respects color scheme, dark mode support.

**Q:** How to create custom Tailwind utilities?
**A:** Add to `theme` in config or use `@layer utilities`. Syntax: `utilities: { '.flex-center': { @apply flex justify-center items-center; } }`. Enable reusable component classes.

**Q:** Real-life (Indian startup dashboard): Build responsive layout with Tailwind?
**A:** Use `container`, `grid`, `md:`, `lg:` classes. Example: `<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3">`. Mobile-first ensures mobile-friendly. Add `dark:` for theme support.

**Q:** Real-life: Create reusable button component with variants?
**A:** Use `@apply` for base styles, props for variants. `bg-blue-500 hover:bg-blue-600` for primary. `bg-gray-200 hover:bg-gray-300` for secondary. Component: `<Button variant="primary">`.

---

## � ADVANCED

**Q:** Explain Tailwind build process and optimization?
**A:** Tailwind scans content files finding class names. Generates CSS for found classes only. Minifies output. Modern: JIT (Just-In-Time) compilation. Result: small production bundles (~50KB gzipped).

**Q:** What is JIT mode in Tailwind 3?
**A:** Just-In-Time compilation. Generates utilities on-demand as found in code. Replaced dev mode purge in Tailwind 3. Faster development, smaller dev CSS files, enables arbitrary values.

**Q:** How to implement custom theme colors?
**A:** Configure in `tailwind.config.js`: `theme: { colors: { brand: { 50: '#f0f9ff', 500: '#3498db' } } }`. Use `bg-brand-500`, `text-brand-50`. Enables brand consistency across app.

**Q:** What is opacity modifier?
**A:** Add transparency to colors. Usage: `bg-blue-500/50` (50% opacity). Works with any color: `text-white/75`, `border-gray-300/25`. Enables color variations without config changes.

**Q:** How to use Tailwind with CSS-in-JS libraries?
**A:** Use with styled-components, emotion: `const Button = styled.button\`${tw`px-4 py-2 bg-blue-500`}\`;`. Requires `twin.macro`. Combines benefits of both approaches but complex.

**Q:** What is @supports in Tailwind?
**A:** Apply utilities based on CSS feature support. Usage: `@supports (display: flex) { /* utilities */ }`. Used for progressive enhancement, graceful degradation in older browsers.

**Q:** Real-life (Indian e-commerce): Optimize Tailwind bundle size?
**A:** Ensure `content` configured correctly. Use PurgeCSS. Lazy-load heavy utilities. Remove unused plugins. Minify CSS. Gzip compression. Monitor bundle with `npm run build`. Target <50KB gzipped.

**Q:** Real-life: Implement dark mode toggle with Tailwind?
**A:** Configure `darkMode: 'class'`. Add `dark:` variants to utilities. JavaScript toggles `document.documentElement.classList.add('dark')`. Store preference in localStorage. Provide toggle button in UI.

**Q:** Real-life: Build design system components with Tailwind?
**A:** Create component library (React components wrapping Tailwind). Use `@apply` for consistent styling. Export components with variants. Use composition. Example: `<Button variant="primary" size="lg">`. Scales to large teams.

**Q:** Real-life: Create responsive data table with Tailwind?
**A:** Use `overflow-x-auto` for horizontal scroll on mobile. Use `table`, `thead`, `tbody` classes. Add responsive utilities: `hidden md:table-cell` for hiding columns on mobile. Stripe rows with `odd:bg-gray-50`.

**Q:** Calculation: If custom CSS would be 200KB, Tailwind with PurgeCSS produces 50KB (75% reduction). With gzip: 50KB → 12KB (94% from original). Impact: faster load, better performance, mobile-friendly.

**Q:** Calculation: Building form with 10 inputs. Manual CSS = 50+ lines per input = 500+ lines total. With Tailwind: `<input class="form-input">` = reusable. Plus plugin handles styling. Saves 90% code, 10x faster development.

---

## 📋 Quick Reference

| Utility    | Examples                                                   |
| ---------- | ---------------------------------------------------------- |
| Spacing    | `p-4`, `m-2`, `space-x-4`, `gap-6`                         |
| Colors     | `bg-blue-500`, `text-red-600`, `border-green-300`          |
| Sizing     | `w-full`, `h-screen`, `min-h-96`, `max-w-md`               |
| Layout     | `flex`, `grid`, `container`, `relative`, `absolute`        |
| Responsive | `md:text-2xl`, `lg:grid-cols-3`, `sm:block`                |
| States     | `hover:bg-blue-600`, `focus:ring-2`, `disabled:opacity-50` |
| Dark Mode  | `dark:bg-gray-800`, `dark:text-white`                      |

| Breakpoint | Screen Size |
| ---------- | ----------- |
| `sm`       | 640px       |
| `md`       | 768px       |
| `lg`       | 1024px      |
| `xl`       | 1280px      |
| `2xl`      | 1536px      |
