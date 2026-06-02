# TypeScript – Interview Q&A

## � BASIC

**Q:** What is TypeScript?
**A:** Programming language built on JavaScript. Adds static typing. Catches errors at compile time before runtime. Compiled to JavaScript for browser/Node.js. Improves code quality, developer experience.

**Q:** Why use TypeScript?
**A:** Type safety catches bugs early. Better IDE autocomplete and suggestions. Self-documenting code. Easier refactoring. Scales to large projects. Improves maintainability and collaboration.

**Q:** What is type annotation?
**A:** Explicitly declaring variable type. Syntax: `const name: string = "John";`. Types: `string`, `number`, `boolean`, `array`, `any`. Enables type checking by TypeScript compiler.

**Q:** What are basic types in TypeScript?
**A:** `string` (text), `number` (integers, floats), `boolean` (true/false), `any` (any type, avoid), `null`, `undefined`, `void` (no return value), `never` (never returns).

**Q:** What is an interface?
**A:** Contract defining object shape. Syntax: `interface User { name: string; age: number; }`. Objects must match interface structure. Used for type checking, documentation.

**Q:** What is a type?
**A:** Defines data structure. Syntax: `type User = { name: string; age: number; }`. Similar to interface but more flexible. Can use unions, tuples, literals. Type preferred for primitive/union types.

**Q:** Interface vs Type?
**A:** Interfaces: object contracts, can be extended/merged. Types: broader use, unions, tuples, primitives. Interfaces for object shapes. Types for anything else. Both work for most cases.

**Q:** What is a union type?
**A:** Variable can be multiple types. Syntax: `let value: string | number;`. Useful for flexibility. Must check type before use. Example: `if (typeof value === 'string') { }`.

**Q:** What is an intersection type?
**A:** Combines multiple types. Syntax: `type Admin = User & { role: 'admin' };`. Object must satisfy all types. More restrictive than union. Used for type composition.

**Q:** What are generics?
**A:** Write reusable code for multiple types. Syntax: `function log<T>(value: T): T { return value; }`. `T` is type parameter. Enables type-safe flexibility for collections, functions, classes.

**Q:** What is an enum?
**A:** Set of named constants. Syntax: `enum Direction { Up = 0, Down = 1 }`. Useful for predefined values. Generates reverse mapping at runtime. Alternative: union types for modern approach.

**Q:** What is the `any` type?
**A:** Disables type checking. Syntax: `let value: any;`. Avoid using. Last resort for libraries without types. Use `unknown` instead for safety. Defeats purpose of TypeScript.

**Q:** What is the `unknown` type?
**A:** Type-safe version of `any`. Must check type before use. Syntax: `if (typeof value === 'string') { }`. Preferred over `any`. Prevents accidental type errors.

---

## � INTERMEDIATE

**Q:** What are optional properties?
**A:** Property may or may not exist. Syntax: `interface User { name: string; age?: number; }`. Question mark makes optional. Accessing undefined property safe with `?.` optional chaining.

**Q:** What are readonly properties?
**A:** Property cannot be modified after initialization. Syntax: `readonly name: string`. Compile error if modified. Enables immutability. Used for constants, preventing accidental mutations.

**Q:** What is the `as` keyword (type assertion)?
**A:** Explicitly tell TypeScript variable type. Syntax: `const value = something as string;`. Use when you know type better than TypeScript. Bypasses type checking. Use carefully.

**Q:** What is type guard?
**A:** Function checking variable type. Syntax: `function isString(value: unknown): value is string { return typeof value === 'string'; }`. Narrow type in conditional. Custom type narrowing.

**Q:** What is function overloading?
**A:** Function with multiple signatures handling different argument types. Syntax: `function add(a: number, b: number): number;` and `function add(a: string, b: string): string;`. Choose signature based on arguments.

**Q:** What is tuple type?
**A:** Fixed-length array with specific types at each position. Syntax: `type Point = [number, number];`. Different from array. First element number, second element number. Used for structured data.

**Q:** What is conditional type?
**A:** Type determined by condition. Syntax: `type IsString<T> = T extends string ? true : false;`. Advanced feature. Used in libraries for flexible typing. Rarely in application code.

**Q:** What is mapped type?
**A:** Transform type properties. Syntax: `type Readonly<T> = { readonly [K in keyof T]: T[K]; }`. Iterate object properties, modify them. Enables type transformations, code reuse.

**Q:** What is partial type?
**A:** Make all properties optional. Syntax: `Partial<User>` makes all `User` properties optional. Built-in utility type. Useful for partial updates, optional props.

**Q:** What is record type?
**A:** Object with specific key-value structure. Syntax: `Record<'admin' | 'user', User>`. Keys must be from union. Useful for maps, configuration objects.

**Q:** What is Omit utility type?
**A:** Create type excluding specific properties. Syntax: `Omit<User, 'password'>`. Removes properties from type. Useful for API responses, public types.

**Q:** What is Pick utility type?
**A:** Create type with specific properties only. Syntax: `Pick<User, 'name' | 'email'>`. Includes only selected properties. Useful for subsets, API payloads.

**Q:** What is keyof operator?
**A:** Get union of object property names. Syntax: `keyof User` returns `'name' | 'age' | 'email'`. Used for type-safe property access, generics.

**Q:** Real-life (Indian banking): Define safe API response type?
**A:** `interface ApiResponse<T> { status: 'success' | 'error'; data: T; message: string; }`. Use generics for flexibility. Response type known at compile time. Catch API mismatches.

**Q:** Real-life: Create type-safe Redux action types?
**A:** `type Action = { type: 'ADD_USER'; payload: User } | { type: 'DELETE_USER'; payload: string };`. Union ensures correct payload types. Reducer knows types for each action.

---

## � ADVANCED

**Q:** What is type narrowing?
**A:** Refine variable type in conditional. Syntax: `if (typeof value === 'string') { }` narrows `value` to string. TypeScript understands type is narrower in block. Prevents type errors.

**Q:** What is control flow analysis?
**A:** TypeScript tracking variable type through code. `typeof` checks, `instanceof`, truthiness, type guards narrow types. Enables type safety without explicit assertions.

**Q:** What is satisfies operator?
**A:** Validate type without changing inferred type. Syntax: `const config = { ... } satisfies Config;`. TypeScript 4.9+. Checks conformance while preserving literal types. Modern type safety.

**Q:** What is extract utility type?
**A:** Extract specific type from union. Syntax: `Extract<string | number | boolean, string>` returns `string`. Filters union types. Used for type manipulation.

**Q:** What is exclude utility type?
**A:** Exclude specific type from union. Syntax: `Exclude<string | number | boolean, boolean>` returns `string | number`. Opposite of Extract. Filters out types.

**Q:** What is typeof operator?
**A:** Get type of variable. Syntax: `type Point = typeof point;` where `point = { x: 1, y: 2 }`. Infers type from value. Useful for constants, avoiding manual type definitions.

**Q:** What are template literal types?
**A:** Generate types from string patterns. Syntax: `type EventName = \`on\${Capitalize<K>}\`;`. Maps strings to types. Advanced, used in libraries (Vue, React type definitions).

**Q:** What is declaration merging?
**A:** Multiple declarations with same name combined. Interfaces can merge, module augmentation. Extends built-in types, libraries. Example: augment Window interface with custom properties.

**Q:** What is module augmentation?
**A:** Add types to existing modules. Syntax: `declare global { interface Window { myProp: string; } }`. Extend third-party libraries, globals. Used for monkey-patching types safely.

**Q:** How to define complex async operation types?
**A:** `type AsyncResult<T> = Promise<T | Error>`. Or `type Result<T, E = Error> = Success<T> | Failure<E>;`. Discriminated unions for error handling. Type-safe async patterns.

**Q:** Real-life (Indian SaaS): Define form validation types?
**A:** `type Validation<T> = { [K in keyof T]: { valid: boolean; error?: string; } };`. For each field, track validation state. Type-safe form builder. Prevents prop mismatches.

**Q:** Real-life: Create type-safe API client?
**A:** `class API<T> { get<K extends keyof T>(key: K): Promise<T[K]> {} }`. Generic ensures type-safe endpoints. Compile-time verification of API calls. Prevent typos, wrong types.

**Q:** Real-life: Implement type-safe event emitter?
**A:** `class EventEmitter<Events> { on<K extends keyof Events>(event: K, listener: (arg: Events[K]) => void) {} }`. Event type maps listeners. Type-safe event arguments. Prevents event misuse.

**Q:** Calculation: Project with 1000 JavaScript files. Adding TypeScript catches ~20% type bugs (200 bugs). Saves QA time, reduces production issues. ROI in bug prevention, maintainability.

---

1. How do you optimize a large React application for performance?
2. Explain the difference between controlled and uncontrolled components in React.
3. What are the benefits of using TypeScript in frontend projects?
4. How would you implement lazy loading and code splitting in React?
5. What is the difference between useEffect and useLayoutEffect?
6. How does the virtual DOM work internally?
7. How do you manage state across complex React applications (Context API vs Redux vs Recoil)?
8. Explain how browsers render a webpage (from HTML parsing to painting).
9. What are common causes of memory leaks in React and how do you fix them?
10. How do you secure a frontend application against XSS and CSRF attacks?
11. How do you handle API errors and retries in frontend applications?
12. Explain how React’s reconciliation algorithm (diffing) works.
13. How do you improve Lighthouse performance scores for a web app?
14. What’s the difference between server-side rendering (SSR) and client-side rendering (CSR)?
15. How do you handle environment variables and secrets in frontend builds?

---

## 📋 Quick Reference

| Type         | Example                                            |
| ------------ | -------------------------------------------------- |
| Basic        | `string`, `number`, `boolean`, `null`, `undefined` |
| Array        | `string[]` or `Array<string>`                      |
| Union        | `string \| number`                                 |
| Intersection | `A & B`                                            |
| Generic      | `Array<T>`, `function<T>()`                        |
| Interface    | `interface User { name: string; }`                 |
| Type         | `type User = { name: string; }`                    |
| Enum         | `enum Color { Red = 0, Green = 1 }`                |
| Utility      | `Partial<T>`, `Pick<T>`, `Omit<T>`, `Record<K, V>` |
