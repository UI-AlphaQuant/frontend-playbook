# Vue.js – Interview Q&A

## � BASIC

**Q:** What is Vue.js?
**A:** Progressive JavaScript framework for building user interfaces. Reactive data binding, component-based. Simpler than React, more powerful than jQuery. Good for small to large applications.

**Q:** What are the key features of Vue?
**A:** Reactive data binding, components, directives, routing, state management, CLI tools, large ecosystem. Less boilerplate than React. Easier learning curve for beginners.

**Q:** What is Vue instance?
**A:** Root Vue component. Created with `new Vue()`. Contains data, methods, lifecycle hooks. `el` property mounts to DOM. `data` stores reactive state.

**Q:** What is reactivity in Vue?
**A:** Automatic UI updates when data changes. Data properties wrapped as getters/setters. Changes tracked automatically. DOM updates efficiently. Core feature of Vue.

**Q:** What are Vue templates?
**A:** HTML with special syntax. `{{ variable }}` for data binding. `v-if`, `v-for`, `@click` for directives. Compiled to render function. More readable than JSX for many.

**Q:** What are directives?
**A:** Special HTML attributes adding behavior. `v-if` (conditional), `v-for` (loop), `v-bind` (binding), `v-on` (events), `v-model` (two-way binding), `v-show` (visibility).

**Q:** What is `v-model`?
**A:** Two-way data binding. Syntax: `<input v-model="name">`. Changes to input update `name`, changes to `name` update input. Used for forms, interactive components.

**Q:** What is computed property?
**A:** Derived property cached based on dependencies. Syntax: `computed: { fullName: function() { return this.firstName + ' ' + this.lastName; } }`. Reactive, efficient. Recalculated when dependencies change.

**Q:** What is watcher?
**A:** Function running when specific data changes. Syntax: `watch: { name: function(newVal, oldVal) { } }`. More control than computed. Used for side effects, async operations.

**Q:** What are components?
**A:** Reusable Vue instances. Template, script, style encapsulated. Props for input data. Events for output. Build UIs from components.

**Q:** What are props?
**A:** Pass data from parent to child component. Syntax: `props: ['title']`, then `{{ title }}`. One-way data flow. Child cannot modify props directly.

**Q:** What are events in Vue?
**A:** Communicate child to parent. Syntax: `this.$emit('eventName', data)`. Parent listens: `@eventName="handler"`. Built-in and custom events.

---

## � INTERMEDIATE

**Q:** What is Vue Router?
**A:** Official routing library. Enable navigation between pages. `router-link` for links, `router-view` for rendering. Lazy load components per route. Single Page App routing.

**Q:** What is Vuex?
**A:** State management library. Centralized state with `state`, `mutations`, `actions`. Use `mapState`, `mapActions` helpers. Similar to Redux. For complex applications.

**Q:** What is Pinia?
**A:** Modern state management replacing Vuex. Simpler API, better TypeScript support. Composition API friendly. Recommended for Vue 3 projects.

**Q:** What is Vue Composition API?
**A:** Alternative to Options API. Organize code by feature not type. `setup()` function, `ref()`, `computed()`, `watch()`. Better for reusability, TypeScript. Vue 3 preferred.

**Q:** What is `ref()` and `reactive()`?
**A:** `ref()`: wraps primitive values, accessed via `.value`. `reactive()`: wraps objects. `reactive()` preferred for objects, `ref()` for anything. Both make data reactive.

**Q:** What is lifecycle in Vue?
**A:** Stages component goes through. Hooks: `beforeCreate`, `created`, `beforeMount`, `mounted`, `beforeUpdate`, `updated`, `beforeUnmount`, `unmounted`. Run code at specific times.

**Q:** What is `onMounted` hook?
**A:** Composition API hook running after component mounted to DOM. Used for API calls, DOM access, subscriptions. Replaces `mounted` in Options API.

**Q:** What is `onUnmounted` hook?
**A:** Runs before component removed from DOM. Used for cleanup: remove listeners, cancel requests, clear timers. Prevents memory leaks.

**Q:** What is `v-slot`?
**A:** Define named slots for flexible layouts. Parent passes content to child slots. Enables template composition, reusable patterns.

**Q:** What is scoped slots?
**A:** Slots accessing child component data. Syntax: `<template slot-scope="slotProps">{{ slotProps.item }}</template>`. Pass parent prop data to parent template.

**Q:** What is provide/inject?
**A:** Pass data to deeply nested components without prop drilling. Parent `provide()`, child `inject()`. Less verbose than passing through many levels. Useful for themes, configs.

**Q:** Real-life (Indian e-commerce): Build shopping cart component?
**A:** Vuex/Pinia store for cart state. Add/remove items mutations. Computed total price. Two-way binding for quantities. Persist to localStorage. Parent and child components.

**Q:** Real-life: Implement authentication flow?
**A:** Login form component. API call to authenticate. Store token in Vuex. Router guards check authentication. Redirect unauthorized users. Logout clears state.

---

## � ADVANCED

**Q:** What is Virtual DOM in Vue?
**A:** In-memory representation of real DOM. Vue updates Virtual DOM, compares with previous, patches only changes. Improves performance. Vue handles automatically.

**Q:** What is diffing algorithm?
**A:** Algorithm comparing two Virtual DOM trees. Identifies minimum changes needed. Updates real DOM efficiently. Vue uses key-based matching for lists.

**Q:** What is Vue 3 reactivity system?
**A:** Uses Proxy and Reflect instead of `Object.defineProperty`. Handles arrays directly. Simpler, more powerful. Enables reactivity on new properties dynamically.

**Q:** What is `<script setup>`?
**A:** Syntactic sugar for Composition API. Simplified syntax inside `<script setup>`. Variables automatically exposed to template. Less boilerplate. Vue 3.2+ feature.

**Q:** What is teleport?
**A:** Move template to different DOM location. Syntax: `<Teleport to="body">`. Renders outside current component hierarchy. Used for modals, toasts at root level.

**Q:** What is Suspense?
**A:** Handle async component loading. Syntax: `<Suspense><template #default><AsyncComp/></template><template #fallback>Loading...</template></Suspense>`. Shows fallback while loading.

**Q:** What is code splitting in Vue?
**A:** Dynamic imports reduce bundle size. Syntax: `const Component = defineAsyncComponent(() => import('./Component.vue'))`. Lazy load heavy components. Router lazy loads route components.

**Q:** What is custom directives?
**A:** Create reusable logic as directives. Syntax: `v-my-directive`. Lifecycle hooks: `mounted`, `updated`. Used for DOM manipulation, focus management, analytics.

**Q:** Real-life: Optimize large list rendering?
**A:** Virtual scrolling (vue-virtual-scroller). Only render visible items. Pagination or infinite scroll. Keyed lists for efficient diffing. Computed for filtering.

**Q:** Real-life: Handle error boundaries in Vue?
**A:** `errorCaptured` hook catches child errors. Global error handler `app.config.errorHandler`. Display fallback UI. Log errors. Prevent white screen of death.

**Q:** Real-life: Implement search with debounce?
**A:** Watch search input with debounce. `watch` with debounce function. Reduce API calls. Display results in real-time. Better UX, less server load.

**Q:** Calculation: Component renders 100 items. With virtual scrolling: only 10 visible items rendered = 10x fewer operations. Smooth scrolling, reduced memory (DOM nodes from 100 to 10).

---

## 📋 Quick Reference

| Directive | Purpose                     |
| --------- | --------------------------- |
| `v-if`    | Conditional rendering       |
| `v-for`   | Loop/list rendering         |
| `v-bind`  | Bind attribute to data      |
| `v-on`    | Event handling              |
| `v-model` | Two-way binding             |
| `v-show`  | Toggle display (not remove) |
| `v-slot`  | Named slots                 |

| Hook           | When                 |
| -------------- | -------------------- |
| `mounted`      | After DOM mount      |
| `updated`      | After data update    |
| `unmounted`    | Before removal       |
| `beforeCreate` | Before instance init |
