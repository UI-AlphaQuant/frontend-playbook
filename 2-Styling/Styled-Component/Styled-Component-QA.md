# Styled-Components – Interview Q&A

## � BASIC

**Q:** What are styled-components?
**A:** CSS-in-JS library for React. Write CSS directly in JavaScript. Tagged template literals. Scoped styles per component. Dynamic styling based on props. Modern approach to styling React apps.

**Q:** What is CSS-in-JS?
**A:** Writing CSS inside JavaScript code. Alternative to CSS files, preprocessors. Dynamic styling, component-scoped. Libraries: styled-components, Emotion, CSS Modules. Growing trend in React ecosystem.

**Q:** What is template literal?
**A:** String syntax using backticks (`` ` ``). Allows variables, expressions inside. `${variable}`. Used in styled-components for interpolation. Enables dynamic CSS.

**Q:** How do you create styled component?
**A:** `const Button = styled.button\`color: red; padding: 10px;\`;`. Component wraps HTML element. CSS inside template literal. Returns React component. Use like normal component: `<Button>`.

**Q:** What is prop-based styling?
**A:** Change styles based on component props. `${props => props.primary ? 'blue' : 'gray'}`. Inline function receiving props. Dynamic styling without separate logic.

**Q:** What are advantages of styled-components?
**A:** Scoped styles (no naming conflicts). Dynamic styling. Component-scoped CSS. Automatic vendor prefixes. No unused CSS (component-based). Better maintainability. Hot reloading support.

**Q:** What are disadvantages?
**A:** JavaScript bundle size (runtime). CSS-in-JS overhead. Learning curve for CSS-first developers. Debugging harder (generated class names). Performance impact compared to static CSS.

**Q:** What is automatic critical CSS?
**A:** Only styles for rendered components sent initially. Reduces initial CSS payload. Server-side rendering support. Improves performance. Styled-components removes unused styles.

**Q:** How to extend styled component?
**A:** `const ExtendedButton = styled(Button)\`background: green;\`;`. Inheritance. Extends parent component styles. Adds additional CSS. Reuse and customize components.

**Q:** What is global styles?
**A:** `createGlobalStyle` for app-wide styles. Resets, fonts, defaults. Use: `<GlobalStyle />`. Not scoped to component. Complements component-scoped styles.

**Q:** What is theme provider?
**A:** `<ThemeProvider theme={theme}>` wraps app. Provides theme object to all components. `${props => props.theme.colors.primary}`. Enables consistent theming, dark mode support.

---

## � INTERMEDIATE

**Q:** How to pass props and use in styles?
**A:** `const Box = styled.div\`color: ${props => props.color};\`;`. Props available in template literal. Receive as argument. Dynamic CSS based on runtime props.

**Q:** What is transient props?
**A:** Props prefixed with `$` not passed to DOM. `${props => props.$size}`. Prevent React warnings. Filter out styling props from HTML. Example: `$color`, `$size`.

**Q:** What is attrs method?
**A:** Set default props. `styled.input.attrs({ type: 'text' })`. Define attributes for styled component. Pass dynamic attributes. Example: `Button.attrs({ disabled: props => props.isLoading })`.

**Q:** How to use styled-components with TypeScript?
**A:** Extend component with generics. `styled.button<Props>\`\``. Type props in component. Type-safe styling. Autocomplete in IDE. Better developer experience.

**Q:** What is animation in styled-components?
**A:** `keyframes` for animations. `animation: ${spin} 2s linear infinite;`. Define keyframes, apply to component. CSS animations in JavaScript.

**Q:** How to handle media queries?
**A:** Template literal with media queries. `@media (max-width: 768px) { /* styles */ }`. Responsive design. No special syntax needed. Same CSS media query syntax.

**Q:** What is nesting in styled-components?
**A:** Ampersand `&` refers to component. `&:hover { }` for pseudo-classes. `& + &` for adjacent selectors. Nested syntax like Sass. Logical grouping of related styles.

**Q:** How to style nested elements?
**A:** `${StyledChild}` reference another styled component. Target: `${StyledChild} { color: red; }`. Style child components from parent. Enable complex hierarchies.

**Q:** What is server-side rendering (SSR) support?
**A:** Extract critical CSS on server. Send with HTML. Prevent flash of unstyled content. `ServerStyleSheet` for SSR. Better performance for server-rendered apps.

**Q:** How to optimize bundle size?
**A:** Minify CSS output. Remove unused styles. Use smaller library (Emotion). Tree-shake if possible. Consider CSS-in-JS trade-offs. Monitor bundle with `webpack-bundle-analyzer`.

---

## � ADVANCED

**Q:** Explain styled-components rendering process?
**A:** Component renders → styled-component generates unique class name → injects CSS into page `<style>` tag. Re-renders update styles dynamically. Runtime overhead for CSS generation.

**Q:** What is how styled-components prevents class name conflicts?
**A:** Generates unique class names per styled component. Hashes component + styles. No global namespace collisions. BEM naming unnecessary. CSS scoped automatically.

**Q:** What is the performance impact?
**A:** Runtime overhead: generating CSS at runtime. JavaScript bundle larger. CSS smaller (no unused styles). Trade-off: larger JS, smaller CSS. Overall impact: depends on use case.

**Q:** How to use with React Native?
**A:** Similar API but limited CSS support. Platform-specific styling. `styled(View)\`...`. Not full CSS available. Different for React Native vs React web.

**Q:** What is testing styled-components?
**A:** Snapshot tests common but not recommended (generated class names). Unit test component functionality, not styles. Integration tests verify visual output. Avoid snapshot tests for maintainability.

**Q:** How to implement dark mode?
**A:** `ThemeProvider` with theme object. Switch theme on user preference. `${props => props.theme.bgColor}`. Re-renders with new theme. localStorage for persistence.

**Q:** What is styled-components documentation approach?
**A:** Read docs thoroughly. Understand advanced patterns. Best practices for performance. TypeScript setup. Server-side rendering configuration. Address specific use cases.

**Q:** How styled-components compares to CSS Modules?
**A:** CSS Modules: static, build-time, scoped. Styled-components: dynamic, runtime, JavaScript-based. Modules: simpler, better performance. Styled-components: more flexible, prop-based styling.

**Q:** How styled-components compares to Emotion?
**A:** Both CSS-in-JS libraries. Emotion: smaller, faster. Styled-components: larger but more features. Emotion: `css` and `styled` APIs. Similar capabilities, different philosophies.

**Q:** Real-life: Build component library with styled-components?
**A:** Create base styled components. Export for consumption. Theming support for customization. TypeScript for type safety. Storybook for documentation. Versioning for changes.

**Q:** Real-life: Implement dynamic theming?
**A:** `ThemeProvider` with theme object. User selects theme (light/dark/custom). Update theme state → re-render → all components reflect new theme. localStorage for persistence.

**Q:** Real-life (Indian UI library): Scale styled-components for large app?
**A:** Organize styles by feature. Create utility styled components. Theme variables for consistency. CSS variables for runtime changes. Document pattern. Monitor bundle size growth.

**Q:** Calculation: Component library with 50 styled components. Each generates 100 bytes of CSS. Static CSS modules: 5KB. Styled-components with per-component generation: similar size but runtime overhead (~50KB JS lib). Trade-off: 45KB extra for flexibility.

---

## 📋 Quick Reference

| Feature     | Syntax                                         |
| ----------- | ---------------------------------------------- |
| Basic       | `const Button = styled.button\`color: red;\`;` |
| Props       | `${props => props.color}`                      |
| Extend      | `styled(Button)\`...\``                        |
| Attrs       | `styled.button.attrs({ type: 'text' })`        |
| Global      | `createGlobalStyle\`...\``                     |
| Theme       | `${props => props.theme.color}`                |
| Media Query | `@media (max-width: 768px) { }`                |
| Animation   | `keyframes` then `animation: ${spin}`          |

| Comparison      | Styled-Components   | CSS Modules |
| --------------- | ------------------- | ----------- |
| Type            | Runtime CSS-in-JS   | Static CSS  |
| Dynamic Styling | ✅ Easy             | ⚠️ Complex  |
| Performance     | ⚠️ Runtime overhead | ✅ Better   |
| Bundle Size     | Larger              | Smaller     |
| Learning Curve  | Moderate            | Easy        |
| Scoping         | Automatic           | Automatic   |
| Theming         | ✅ Built-in         | Manual      |
