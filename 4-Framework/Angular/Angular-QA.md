# Angular – Interview Q&A

## � BASIC

**Q:** What is Angular?
**A:** TypeScript-based frontend framework by Google. Full-featured framework with built-in solutions (routing, HTTP, forms). Opinionated, bigger learning curve. Used for large enterprise applications.

**Q:** What are the key features of Angular?
**A:** TypeScript support, dependency injection, decorators, modules, services, routing, HTTP client, reactive forms, built-in testing, CLI, strong typing, enterprise features.

**Q:** What is a component?
**A:** Basic building block of Angular UI. Has template (HTML), class (logic), styles (CSS). Uses decorators `@Component`. Reusable, testable. Similar to React components.

**Q:** What is a decorator?
**A:** Function adding metadata to class/property. `@Component`, `@NgModule`, `@Input`, `@Output`. Angular uses decorators extensively. Enables framework features.

**Q:** What is `@Component` decorator?
**A:** Marks class as Angular component. Properties: `selector` (CSS selector), `template`/`templateUrl` (HTML), `styles`/`styleUrls` (CSS). Metadata for Angular to understand component.

**Q:** What are directives?
**A:** Instructions for DOM manipulation. Built-in: `*ngIf`, `*ngFor`, `*ngSwitch`. Used in templates to control rendering, loops, styles. Similar to Vue directives.

**Q:** What is `*ngIf`?
**A:** Conditional rendering. `*ngIf="condition"` renders element if true, removes if false. `*ngIf="condition; else elseBlock"` for else clause. Two-way: add/remove from DOM.

**Q:** What is `*ngFor`?
**A:** Loop through array. Syntax: `*ngFor="let item of items"`. Repeats element for each item. `trackBy` for performance optimization. Create unique keys with `trackById`.

**Q:** What is `*ngSwitch`?
**A:** Switch/case structure. `*ngSwitchCase="value"` for branches. One element renders based on switched value. Alternative to multiple `*ngIf`.

**Q:** What is data binding?
**A:** Connect component class to template. Types: property binding `[property]`, event binding `(event)`, two-way `[(ngModel)]`, interpolation `{{ }}`.

**Q:** What is interpolation?
**A:** Display component data in template. Syntax: `{{ variableName }}`. One-way binding. Automatically updated when data changes. Used for displaying values.

**Q:** What is property binding?
**A:** Bind component property to HTML property. Syntax: `[property]="componentProperty"`. One-way from component to template. Example: `[disabled]="isDisabled"`.

---

## � INTERMEDIATE

**Q:** What is event binding?
**A:** Respond to user events. Syntax: `(event)="handler()"`. Example: `(click)="onClick()"`. Passes event object: `($event)="handler($event)"`. Connect UI interactions to logic.

**Q:** What is two-way binding?
**A:** Data flows both directions. Syntax: `[(ngModel)]="property"`. Update template updates component, update component updates template. Syntax sugar for property + event binding.

**Q:** What is `@Input` decorator?
**A:** Mark property as input from parent. Parent binds: `[property]="value"`. Child receives data. One-way flow: parent → child. Enables component reusability.

**Q:** What is `@Output` decorator?
**A:** Mark property as event emitter. Child emits: `this.myEvent.emit(data)`. Parent listens: `(myEvent)="handler($event)"`. Communicate child → parent.

**Q:** What is a service?
**A:** Reusable class with logic, data, methods. Injected into components. `@Injectable` decorator. Used for HTTP calls, data sharing, utilities. Singleton by default.

**Q:** What is dependency injection (DI)?
**A:** Angular automatically injects dependencies. `constructor(private service: MyService)`. Loosely couples components to services. Testable, maintainable. Angular strength.

**Q:** What is `@Injectable` decorator?
**A:** Marks class as injectable service. `providedIn: 'root'` makes singleton available app-wide. Enables dependency injection. Must have for services.

**Q:** What is Angular routing?
**A:** Navigate between components. `RouterModule`, `Routes` configuration. `<router-outlet>` displays routed component. `routerLink` for navigation. Lazy load modules per route.

**Q:** What is routing module?
**A:** `AppRoutingModule` configures routes. Define routes array with path/component. Import `RouterModule`. Enable lazy loading, guards, resolve.

**Q:** What is route guard?
**A:** Protect routes from unauthorized access. Implement `CanActivate` interface. Check auth before navigating. Redirect if unauthorized. Used for role-based access control.

**Q:** What is `CanActivate` guard?
**A:** Guard executing before route activation. Implement interface with `canActivate()` method. Return boolean or Observable. Stop navigation if returns false. Protect admin routes.

**Q:** What is `CanDeactivate` guard?
**A:** Guard executing before leaving route. Check unsaved changes. Warn user before leaving. Implement `canDeactivate()`. Prevent accidental navigation away.

**Q:** What is resolver in Angular routing?
**A:** Pre-fetch data before component loads. Implement `Resolve` interface. Wait for data, then navigate. Component receives data via `ActivatedRoute`. Better UX than loading in component.

**Q:** Real-life (Indian dashboard): Implement role-based access?
**A:** Create `AuthGuard` implementing `CanActivate`. Check user role. Redirect unauthorized users. Use `ActivatedRoute` to get route data. Protect routes with guard.

**Q:** Real-life: Handle HTTP requests with interceptors?
**A:** Implement `HttpInterceptor`. Add auth tokens to requests. Handle errors globally. Log requests. Implement retry logic. One interceptor for all HTTP calls.

---

## � ADVANCED

**Q:** What is RxJS and Observables?
**A:** Reactive JavaScript library. Observable: lazy stream of values. Emit events over time. Subscribe to observe values. Powerful for async operations, event handling.

**Q:** What are operators in RxJS?
**A:** Functions transforming, filtering, combining observables. Common: `map()`, `filter()`, `switchMap()`, `mergeMap()`, `debounceTime()`, `tap()`. Chainable for data flow.

**Q:** What is `switchMap`?
**A:** Cancel previous observable, subscribe to new one. Used for search: each keystroke cancels previous request. Prevents race conditions. Autocomplete use case.

**Q:** What is `mergeMap`?
**A:** Subscribe to all observables in sequence. Don't cancel previous. Process results in order. Used for parallel operations. Combines multiple streams.

**Q:** What is `debounceTime`?
**A:** Delay emission until specified time since last value. Useful for search input, scroll events. Reduces API calls. Example: `debounceTime(300)`.

**Q:** What is reactive forms?
**A:** Form-centric approach using `FormControl`, `FormGroup`. Reactive programming patterns. Validation observable. Better for complex forms than template-driven.

**Q:** What is `FormBuilder`?
**A:** Helper service building forms programmatically. Cleaner syntax than `new FormGroup()`. `fb.group()`, `fb.array()` for complex nested forms.

**Q:** What is form validation?
**A:** Built-in validators: `required`, `minLength`, `maxLength`, `pattern`, `email`. Custom validators possible. Reactive and template-driven both support validation.

**Q:** What is module in Angular?
**A:** Groups related components, services, directives, pipes. `@NgModule` decorator. Declarations, imports, exports, providers. Organize large applications. Lazy load modules per route.

**Q:** What is lazy loading?
**A:** Load module only when route accessed. Smaller initial bundle. Configure in routing: `loadChildren`. Improves performance, faster app startup.

**Q:** What is Angular CLI?
**A:** Command-line interface. `ng serve`, `ng build`, `ng test`. Generate components, services. Configure build, optimization. Essential tool for Angular development.

**Q:** Real-life (Indian payment app): Handle async payments with RxJS?
**A:** Observable from payment API call. Use `switchMap()` to cancel previous if user retries. Show loading state. Handle errors with `catchError()`. Unsubscribe to prevent memory leaks.

**Q:** Real-life: Implement type-safe HTTP client?
**A:** Create service with typed methods. `HttpClient.get<User[]>()`. Return Observable. Components subscribe and handle. Type safety on responses, compile-time errors.

**Q:** Real-life: Optimize Angular bundle size?
**A:** Lazy load modules, code split routes. Remove unused imports. Use OnPush change detection. Tree-shake with production build. Monitor bundle with webpack-bundle-analyzer.

**Q:** Calculation: App with 50 components, 20 services, 100KB of code. Initial bundle 500KB. Lazy loading by feature: initial 150KB, lazy loaded modules 50-100KB each. Result: 70% faster initial load.

---

## 📋 Quick Reference

| Directive     | Purpose               |
| ------------- | --------------------- |
| `*ngIf`       | Conditional rendering |
| `*ngFor`      | Loop/list rendering   |
| `*ngSwitch`   | Switch/case structure |
| `[property]`  | Property binding      |
| `(event)`     | Event binding         |
| `[(ngModel)]` | Two-way binding       |

| Decorator     | Purpose                  |
| ------------- | ------------------------ |
| `@Component`  | Define component         |
| `@Input`      | Receive data from parent |
| `@Output`     | Emit events to parent    |
| `@Injectable` | Mark as service          |
| `@NgModule`   | Define module            |

| RxJS          | Purpose                   |
| ------------- | ------------------------- |
| `Observable`  | Async data stream         |
| `map()`       | Transform values          |
| `filter()`    | Filter values             |
| `switchMap()` | Cancel, switch observable |
| `subscribe()` | Listen to observable      |
