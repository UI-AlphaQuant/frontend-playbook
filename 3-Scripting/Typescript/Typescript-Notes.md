# 👉 TypeScript

## 📌 What is TypeScript?

- Strongly typed superset of JavaScript
- Developed by Microsoft
- Adds static typing to JS
- Compiles into normal JavaScript
- Improves scalability and maintainability

### Why Use TypeScript?

- Detect errors early
- Better autocomplete & IntelliSense
- Safer refactoring
- Better large-scale app support
- Predictable codebase
- Modern JavaScript support

### JavaScript vs TypeScript

| JavaScript      | TypeScript            |
| --------------- | --------------------- |
| Dynamic typing  | Static typing         |
| Runtime errors  | Compile-time errors   |
| No compilation  | Compiles to JS        |
| Less strict     | More predictable      |
| Harder to scale | Better for large apps |

### Installation

```bash
npm install -g typescript
```

---

## 📌 tsconfig.json

TypeScript configuration file used to control compiler behavior and project settings.

```bash
tsc --init
```

```json
{
  "compilerOptions": {
    "target": "ES2020",
    "module": "ESNext",
    "strict": true,
    "rootDir": "./src",
    "outDir": "./dist",
    "moduleResolution": "Node",
    "esModuleInterop": true,
    "sourceMap": true,
    "baseUrl": "./src",
    "paths": {
      "@/*": ["*"]
    }
  },
  "include": ["src"],
  "exclude": ["node_modules", "dist"]
}
```

| Option             | Purpose                       |
| ------------------ | ----------------------------- |
| `target`           | Output JS version             |
| `module`           | Module system                 |
| `strict`           | Enable strict type checking   |
| `rootDir`          | Source folder                 |
| `outDir`           | Compiled output folder        |
| `sourceMap`        | Debugging support             |
| `allowJs`          | Allow JS files                |
| `checkJs`          | Type check JS files           |
| `noImplicitAny`    | Prevent implicit `any`        |
| `strictNullChecks` | Strict null checking          |
| `esModuleInterop`  | Better CommonJS compatibility |
| `baseUrl`          | Base import path              |
| `paths`            | Import aliases                |

- Always enable `strict`
- Keep source files inside `src`
- Output compiled files to `dist`
- Use path aliases for cleaner imports
- Avoid unnecessary compiler options

---

## 📌 Basic Types

TypeScript provides built-in primitive data types for safer type checking.

| Type        | Description             | Example     |
| ----------- | ----------------------- | ----------- |
| `string`    | Text values             | `"Hello"`   |
| `number`    | Integers & decimals     | `10`, `5.5` |
| `boolean`   | True/False values       | `true`      |
| `null`      | Intentional empty value | `null`      |
| `undefined` | Unassigned value        | `undefined` |
| `symbol`    | Unique identifier       | `Symbol()`  |
| `bigint`    | Large integers          | `10n`       |

```ts
let username: string = "Naimesh";
let age: number = 28;
let isAdmin: boolean = true;

let emptyValue: null = null;
let notAssigned: undefined = undefined;

let uniqueId: symbol = Symbol("id");

let bigNumber: bigint = 12345678901234567890n;
```

- `Explicit` means something is clearly written or manually defined instead of automatically inferred.

| Type          | Example                |
| ------------- | ---------------------- |
| Explicit Type | `let age: number = 25` |
| Inferred Type | `let age = 25`         |

- Prefer type inference when obvious
- Use explicit types for function params
- Avoid unnecessary primitive wrappers (`String`, `Number`)
- Use `bigint` only for very large integers
- Keep types predictable and consistent

---

## 📌 Type System

TypeScript type system adds static typing for safer and predictable code.

| Concept            | Description             | Example            |
| ------------------ | ----------------------- | ------------------ |
| Type Annotation    | Explicitly define type  | `let age: number`  |
| Type Inference     | Auto-detect type        | `let age = 25`     |
| Literal Types      | Fixed exact values      | `"success"`        |
| Union Types        | Multiple possible types | `string \| number` |
| Intersection Types | Combine multiple types  | `A & B`            |
| Type Alias         | Reusable custom type    | `type User = {}`   |

```ts
let username: string = "John";
let city = "Delhi"; // inferred string
let status: "success" = "success";
let id: string | number;

type User = {
  name: string;
};

type Admin = {
  permissions: string[];
};

type SuperUser = User & Admin;
type Username = string;

let user: Username = "John";
```

---

## 📌 Special Types

Special types handle flexible, unknown, impossible, or empty values in TypeScript.

| Type      | Description                | Usage                        |
| --------- | -------------------------- | ---------------------------- |
| `any`     | Disables type checking     | Dynamic values               |
| `unknown` | Safer alternative to `any` | Validate before use          |
| `never`   | Value never occurs         | Infinite loop / thrown error |
| `void`    | No return value            | Functions without return     |

```ts
let value: any = "Hello";

value = 100;
value = true;
```

```ts
let data: unknown = "TypeScript";

if (typeof data === "string") {
  console.log(data.toUpperCase());
}
```

```ts
function throwError(message: string): never {
  throw new Error(message);
}

function logMessage(message: string): void {
  console.log(message);
}
```

- Avoid excessive `any`
- Prefer `unknown` over `any`
- Use `void` for functions without return
- Use `never` for unreachable/impossible states
- Always narrow `unknown` before usage

---

## 📌 Arrays & Tuples

Arrays store multiple values of the same type, while tuples store fixed-length values with specific types.

| Type           | Description                    | Example             |
| -------------- | ------------------------------ | ------------------- |
| Array          | Collection of same-type values | `string[]`          |
| Readonly Array | Prevents modification          | `readonly string[]` |
| Tuple          | Fixed structure & types        | `[string, number]`  |

```ts
let users: string[] = ["Naimesh", "Raj"];
let scores: number[] = [90, 80, 70];
let mixed: (string | number)[] = ["TS", 5];
```

```ts
let readonlyUsers: readonly string[] = ["Admin", "Editor"];
// readonlyUsers.push("User"); ❌ Error
```

```ts
let person: [string, number] = ["Naimesh", 28];
```

```ts
let rgb: [number, number, number] = [255, 0, 0];
```

| Common Array Syntax | Description      |
| ------------------- | ---------------- |
| `string[]`          | Array of strings |
| `number[]`          | Array of numbers |
| `(A \| B)[]`        | Multi-type array |
| `readonly T[]`      | Immutable array  |
| `[A, B]`            | Tuple            |

- Prefer `type[]` syntax over `Array<type>` for simplicity
- Use tuples for fixed structured data
- Use readonly arrays when mutation isn't needed
- Keep arrays strongly typed
- Avoid excessive mixed-type arrays

---

## 📌 Objects

Objects store structured key-value data with defined property types.

| Feature           | Description             | Example               |
| ----------------- | ----------------------- | --------------------- |
| Object Type       | Define object structure | `{ name: string }`    |
| Optional Property | Property may exist      | `age?: number`        |
| Readonly Property | Prevent modification    | `readonly id: number` |
| Nested Object     | Object inside object    | `{ address: {} }`     |
| Index Signature   | Dynamic keys            | `[key: string]: any`  |

```ts
let user: {
  name: string;
  age: number;
} = {
  name: "Naimesh",
  age: 28,
};
```

```ts
let product: {
  name: string;
  price?: number;
} = {
  name: "Laptop",
};
```

```ts
let account: {
  readonly id: number;
  username: string;
} = {
  id: 1,
  username: "naimesh",
};

// account.id = 2; ❌ Error
```

```ts
let employee: {
  name: string;
  address: {
    city: string;
    pincode: number;
  };
} = {
  name: "Raj",
  address: {
    city: "Nadiad",
    pincode: 387001,
  },
};
```

```ts
let settings: {
  [key: string]: string;
} = {
  theme: "dark",
  language: "en",
};
```

- Use interfaces/types for reusable object structures
- Prefer readonly properties for immutable data
- Use optional properties only when necessary
- Keep object types predictable
- Avoid excessive `any` in index signatures

---

## 📌 Interfaces

Interfaces define reusable object structures and contracts in TypeScript.

| Feature             | Description               | Example                 | Real-World Usage         |
| ------------------- | ------------------------- | ----------------------- | ------------------------ |
| Basic Interface     | Define object shape       | `interface User {}`     | API response models      |
| Optional Property   | Property may exist        | `age?: number`          | Optional form fields     |
| Readonly Property   | Immutable property        | `readonly id: number`   | Database IDs             |
| Extending Interface | Reuse multiple interfaces | `extends`               | Role-based user systems  |
| Function Interface  | Define function structure | `(a: number) => number` | Utility/helper functions |

```ts
interface User {
  name: string;
  age: number;
}

const user: User = {
  name: "Naimesh",
  age: 28,
};
```

```ts
interface Product {
  name: string;
  price?: number;
}

const item: Product = {
  name: "Laptop",
};
```

```ts
interface Account {
  readonly id: number;
  username: string;
}

const account: Account = {
  id: 1,
  username: "naimesh",
};

// account.id = 2; ❌ Error
```

```ts
interface Person {
  name: string;
}

interface Employee extends Person {
  role: string;
}

const employee: Employee = {
  name: "Raj",
  role: "Developer",
};
```

```ts
interface Sum {
  (a: number, b: number): number;
}

const add: Sum = (a, b) => a + b;
```

- Use interfaces for object contracts
- Prefer interfaces for scalable applications
- Use `readonly` for immutable properties
- Keep interfaces small and reusable
- Use `extends` for shared structures

---

## 📌 Functions

Functions in TypeScript support parameter typing, return typing, optional values, and reusable function signatures.

| Feature             | Description                  | Example             | Real-World Usage  |
| ------------------- | ---------------------------- | ------------------- | ----------------- |
| Parameter Types     | Define parameter types       | `(name: string)`    | Form/API inputs   |
| Return Types        | Define returned value type   | `(): number`        | Utility functions |
| Optional Parameters | Parameter may be omitted     | `age?: number`      | Optional filters  |
| Default Parameters  | Fallback parameter value     | `count = 0`         | Config/settings   |
| Rest Parameters     | Multiple arguments           | `...nums: number[]` | Dynamic inputs    |
| Function Type       | Reusable function signature  | `(a, b) => number`  | Shared utilities  |
| Function Overloads  | Multiple function signatures | `function fn()`     | Flexible APIs     |

```ts
function greet(name: string): string {
  return `Hello ${name}`;
}
```

```ts
function getUser(name: string, age?: number): string {
  return `${name} ${age}`;
}
```

```ts
function counter(count: number = 0): number {
  return count;
}
```

```ts
function total(...nums: number[]): number {
  return nums.reduce((a, b) => a + b, 0);
}
```

```ts
type MathOperation = (a: number, b: number) => number;

const add: MathOperation = (a, b) => a + b;
```

```ts
function format(value: string): string;
function format(value: number): number;

function format(value: string | number) {
  return value;
}
```

- Always type function parameters
- Prefer explicit return types for reusable functions
- Use optional/default params carefully
- Use type aliases/interfaces for reusable signatures
- Keep functions small and predictable

---

## 📌 Narrowing & Type Guards

Narrowing reduces possible types to a more specific type using checks and conditions.

| Feature           | Description                | Example                 | Real-World Usage       |
| ----------------- | -------------------------- | ----------------------- | ---------------------- |
| `typeof`          | Check primitive type       | `typeof x === "string"` | Input validation       |
| `instanceof`      | Check class instance       | `x instanceof Error`    | Error handling         |
| `in` Operator     | Check property existence   | `"name" in user`        | API response checks    |
| Custom Type Guard | Custom validation function | `value is User`         | Reusable validations   |
| Truthy Narrowing  | Remove falsy values        | `if(value)`             | Optional data handling |

```ts
function print(value: string | number) {
  if (typeof value === "string") {
    console.log(value.toUpperCase());
  }
}
```

```ts
class User {}

const user = new User();

if (user instanceof User) {
  console.log("Valid User");
}
```

```ts
type Admin = {
  permissions: string[];
};

if ("permissions" in admin) {
  console.log(admin.permissions);
}
```

```ts
type User = {
  name: string;
};

function isUser(value: any): value is User {
  return "name" in value;
}
```

```ts
function greet(name?: string) {
  if (name) {
    console.log(name.toUpperCase());
  }
}
```

- Prefer `unknown` with proper narrowing
- Use custom guards for reusable validation
- Avoid unsafe type assertions
- Narrow types before property access
- Keep guards simple and predictable

---

## 📌 Generics

- Generics create reusable, type-safe components that work with multiple data types.
- `T` is a placeholder type variable.

| Feature           | Description              | Example            | Real-World Usage   |
| ----------------- | ------------------------ | ------------------ | ------------------ |
| Generic Function  | Reusable typed function  | `<T>`              | Utility functions  |
| Generic Interface | Reusable typed structure | `interface Api<T>` | API responses      |
| Generic Class     | Reusable typed class     | `class Box<T>`     | Data stores        |
| Constraints       | Restrict allowed types   | `T extends`        | Object validation  |
| Default Generic   | Fallback generic type    | `<T = string>`     | Reusable libraries |

```ts
function identity<T>(value: T): T {
  return value;
}

identity<string>("Hello");
identity<number>(100);
```

```ts
interface ApiResponse<T> {
  success: boolean;
  data: T;
}

const user: ApiResponse<string> = {
  success: true,
  data: "Naimesh",
};
```

```ts
class Box<T> {
  content: T;

  constructor(value: T) {
    this.content = value;
  }
}

const numberBox = new Box<number>(100);
```

```ts
function getLength<T extends { length: number }>(value: T) {
  return value.length;
}
```

```ts
type Config<T = string> = {
  value: T;
};

const theme: Config = {
  value: "dark",
};
```

```ts
// Without Generic
function identity(value: any): any {
  return value;
}
const result = identity("Hello");

// With Generic (`T`)
function identity<T>(value: T): T {
  return value;
}
const result = identity<string>("Hello");
```

| Generic | Meaning |
| ------- | ------- |
| `T`     | Type    |
| `K`     | Key     |
| `V`     | Value   |
| `E`     | Element |

- Use meaningful generic names when needed
- Prefer generics over `any`
- Add constraints for safer types
- Keep generics simple and reusable
- Avoid unnecessary nested generics

---

## 📌 Enums

Enums define a set of named constant values for better readability and maintainability.

| Type         | Description                   | Example          | Real-World Usage          |
| ------------ | ----------------------------- | ---------------- | ------------------------- |
| Numeric Enum | Auto-increment numeric values | `enum Status {}` | Status codes              |
| String Enum  | Fixed string values           | `"ADMIN"`        | User roles                |
| Const Enum   | Inlined optimized enum        | `const enum`     | Performance-critical apps |

```ts
// Numeric Enum
enum Status {
  Pending,
  Approved,
  Rejected,
}

let currentStatus: Status = Status.Approved;
```

```ts
// String Enum
enum Role {
  Admin = "ADMIN",
  User = "USER",
}

let userRole: Role = Role.Admin;
```

```ts
// Const Enum
const enum Direction {
  Up,
  Down,
}

let move = Direction.Up;
```

| Enum Member | Enum Values |
| ----------- | ----------- |
| `Pending`   | `0`         |
| `Approved`  | `1`         |
| `Rejected`  | `2`         |

- Prefer string enums for readability
- Use enums for fixed constant sets
- Avoid excessive large enums
- Prefer union literals for small simple values
- Use `const enum` only when supported by tooling

| Use Case          | Example                           |
| ----------------- | --------------------------------- |
| User Roles        | `Admin`, `User`, `Editor`         |
| API Status        | `Loading`, `Success`, `Error`     |
| Order Status      | `Pending`, `Shipped`, `Delivered` |
| Payment Methods   | `Card`, `UPI`, `Cash`             |
| Directions        | `Up`, `Down`, `Left`, `Right`     |
| Theme Modes       | `Light`, `Dark`                   |
| Permission Levels | `Read`, `Write`, `Delete`         |

---

## 📌 Classes & OOP

Classes are blueprints for creating reusable objects with properties and methods using Object-Oriented Programming principles.

| Feature        | Description                  | Example            | Real-World Usage       |
| -------------- | ---------------------------- | ------------------ | ---------------------- |
| Class          | Blueprint for objects        | `class User {}`    | User models            |
| Constructor    | Initialize object values     | `constructor()`    | Object setup           |
| Public         | Accessible everywhere        | `public name`      | Shared data            |
| Private        | Accessible only inside class | `private password` | Sensitive data         |
| Protected      | Accessible in subclasses     | `protected id`     | Base classes           |
| Inheritance    | Reuse parent class           | `extends`          | Shared systems         |
| Abstract Class | Base incomplete class        | `abstract class`   | Framework architecture |
| Static Member  | Shared class-level value     | `static count`     | Utilities/configs      |
| Implements     | Follow interface contract    | `implements`       | Structured classes     |

```ts
// Basic Class
class User {
  name: string;

  constructor(name: string) {
    this.name = name;
  }

  greet() {
    console.log(`Hello ${this.name}`);
  }
}

const user = new User("Naimesh");
```

```ts
// Access Modifiers
class Account {
  public username: string;
  private password: string;
  protected id: number;

  constructor(username: string, password: string, id: number) {
    this.username = username;
    this.password = password;
    this.id = id;
  }
}
```

```ts
// Inheritance
class Animal {
  move() {
    console.log("Moving");
  }
}

class Dog extends Animal {
  bark() {
    console.log("Barking");
  }
}
```

```ts
// Abstract Class
abstract class Shape {
  abstract area(): number;
}

class Circle extends Shape {
  area() {
    return 100;
  }
}
```

```ts
// Static Members
class Config {
  static appName = "MyApp";
}

console.log(Config.appName);
```

```ts
// Implements Interface
interface Person {
  name: string;
}

class Employee implements Person {
  constructor(public name: string) {}
}
```

- Keep classes focused on single responsibility
- Use `private` for sensitive/internal data
- Prefer composition over deep inheritance
- Use interfaces for contracts
- Avoid unnecessary large class hierarchies

---

## 📌 Modules

Modules split code into reusable files using `export` and `import`.

| Feature        | Description              | Example          | Real-World Usage   |
| -------------- | ------------------------ | ---------------- | ------------------ |
| Named Export   | Export multiple values   | `export const`   | Utility files      |
| Default Export | Export single main value | `export default` | Components/classes |
| Named Import   | Import specific value    | `import { x }`   | Shared functions   |
| Default Import | Import default export    | `import App`     | Main modules       |
| Alias Import   | Rename import            | `as`             | Avoid conflicts    |
| Type Import    | Import only types        | `import type`    | Type-safe projects |
| Re-export      | Export from another file | `export *`       | Central exports    |

```ts
// Named Export
export const appName = "MyApp";

export function greet() {
  console.log("Hello");
}

// Named Import
import { appName, greet } from "./app";
```

```ts
// Default Export
export default class User {}

// Default Import
import User from "./User";
```

```ts
// Alias Import
import { greet as sayHello } from "./app";

console.log(sayHello);
```

```ts
// Type Import
import type { User } from "./types";
```

```ts
// Re-export
export * from "./utils";
```

### Folder Example

```txt
src/
 ├── utils/
 │    └── math.ts
 ├── types/
 │    └── user.ts
 └── app.ts
```

- Prefer named exports for scalability
- Use default exports sparingly
- Use `import type` for type-only imports
- Keep modules small and focused
- Organize shared exports centrally

---

## 📌 Type Assertions

Type assertions tell TypeScript to treat a value as a specific type without changing runtime behavior.

| Feature            | Description                  | Example           | Real-World Usage  |
| ------------------ | ---------------------------- | ----------------- | ----------------- |
| `as` Assertion     | Assert specific type         | `value as string` | DOM elements      |
| Angle Bracket      | Alternative assertion syntax | `<string>value`   | Legacy TS code    |
| Non-Null Assertion | Remove `null`/`undefined`    | `value!`          | Optional elements |
| Const Assertion    | Make values readonly/literal | `as const`        | Config/constants  |

```ts
// `as` Assertion
let value: unknown = "TypeScript";

let length = (value as string).length;
```

```ts
// Angle Bracket Assertion
let value: unknown = "Hello";

let length = (<string>value).length;
```

```ts
// Non-Null Assertion
const button = document.getElementById("btn")!;

button.innerHTML = "Click";
```

```ts
// Const Assertion
const roles = ["Admin", "User"] as const;
```

```ts
// Real-World Example
const input = document.querySelector("input") as HTMLInputElement;

input.value = "Naimesh";
```

- Prefer proper type narrowing over assertions
- Use assertions only when type is certain
- Avoid excessive `as any`
- Prefer `as` syntax over angle brackets
- Use `as const` for fixed immutable values

---

## 📌 Utility Types

Utility types help transform and reuse existing types efficiently.

| Utility Type    | Description                   | Example                  | Real-World Usage                 |
| --------------- | ----------------------------- | ------------------------ | -------------------------------- |
| `Partial<T>`    | Makes all properties optional | `Partial<User>`          | Update forms, PATCH APIs         |
| `Required<T>`   | Makes all properties required | `Required<User>`         | Validation systems               |
| `Readonly<T>`   | Makes properties immutable    | `Readonly<User>`         | App configs, constants           |
| `Pick<T, K>`    | Select specific properties    | `Pick<User, "name">`     | Lightweight API responses        |
| `Omit<T, K>`    | Remove specific properties    | `Omit<User, "password">` | Remove passwords/private fields  |
| `Record<K, T>`  | Create object type            | `Record<string, number>` | Dynamic object maps              |
| `Exclude<T, U>` | Remove types from union       | `Exclude<A, B>`          | Filter invalid states            |
| `Extract<T, U>` | Keep matching union types     | `Extract<A, B>`          | Allow specific permissions/roles |

```ts
// Partial
interface User {
  name: string;
  age: number;
}

const updateUser: Partial<User> = {
  age: 30,
};
```

```ts
// Required
type User = {
  name?: string;
};

const user: Required<User> = {
  name: "Naimesh",
};
```

```ts
// Readonly
type Config = Readonly<{
  apiUrl: string;
}>;

// config.apiUrl = "new"; ❌ Error
```

```ts
// Pick
interface User {
  name: string;
  age: number;
  email: string;
}

type UserPreview = Pick<User, "name" | "email">;
```

```ts
// Omit
type PublicUser = Omit<User, "password">;
```

```ts
// Record
const scores: Record<string, number> = {
  math: 90,
  science: 95,
};
```

```ts
// Exclude
type Status = "success" | "error" | "loading";

type Result = Exclude<Status, "loading">;
```

```ts
// Extract
type Role = "admin" | "user" | "guest";

type AllowedRole = Extract<Role, "admin" | "user">;
```

- Prefer utility types over duplicate types
- Use `Partial` for update operations
- Use `Readonly` for immutable data
- Use `Pick`/`Omit` for cleaner API models
- Keep transformed types simple and readable

---

## 📌 Advanced Types

Advanced types create powerful reusable and dynamic type systems in TypeScript.

| Feature                | Description                 | Example               | Real-World Usage        |
| ---------------------- | --------------------------- | --------------------- | ----------------------- |
| `keyof`                | Get object keys as union    | `keyof User`          | Dynamic property access |
| `typeof`               | Get variable/function type  | `typeof user`         | Shared object types     |
| Indexed Access         | Access property type        | `User["name"]`        | Reusable field types    |
| Mapped Types           | Transform object properties | `[K in keyof T]`      | Dynamic models          |
| Conditional Types      | Apply type conditions       | `T extends U ?`       | Flexible APIs           |
| Template Literal Types | Create string patterns      | `` `btn-${string}` `` | CSS/class systems       |

```ts
// `keyof`
interface User {
  name: string;
  age: number;
}

type UserKeys = keyof User;

// "name" | "age"
```

```ts
// `typeof`
const user = {
  name: "Naimesh",
  age: 28,
};

type User = typeof user;
```

```ts
// Indexed Access Types
interface User {
  name: string;
  age: number;
}

type UserName = User["name"];
```

```ts
// Mapped Types
type ReadonlyUser<T> = {
  readonly [K in keyof T]: T[K];
};
```

```ts
// Conditional Types
type IsString<T> = T extends string ? true : false;
```

```ts
// Template Literal Types
type ButtonClass = `btn-${string}`;
```

```ts
// Real-World Example
interface ApiResponse {
  id: number;
  name: string;
  email: string;
}

type PublicResponse = Pick<ApiResponse, keyof ApiResponse>;
```

- Use advanced types for reusable systems
- Keep type logic readable and simple
- Avoid overly complex nested types
- Prefer utility types when possible
- Use template literals for predictable string patterns

---

## 📌 Async TypeScript

Async TypeScript adds type safety to asynchronous operations like APIs, promises, and async functions.

| Feature        | Description              | Example             | Real-World Usage    |
| -------------- | ------------------------ | ------------------- | ------------------- |
| Promise Type   | Define async result type | `Promise<string>`   | API requests        |
| Async Function | Async function syntax    | `async function`    | Server calls        |
| Await          | Wait for async result    | `await fetch()`     | Data fetching       |
| Typed Response | Strongly typed API data  | `ApiResponse<User>` | Backend integration |

```ts
// Promise Type
function getMessage(): Promise<string> {
  return Promise.resolve("Hello");
}
```

```ts
// Async Function
async function getUser(): Promise<string> {
  return "Naimesh";
}
```

```ts
// Await
async function loadData() {
  const data = await Promise.resolve("Loaded");

  console.log(data);
}
```

```ts
// Typed API Response
interface User {
  id: number;
  name: string;
}

async function fetchUser(): Promise<User> {
  return {
    id: 1,
    name: "Naimesh",
  };
}
```

```ts
// Real-World Example
type ApiResponse<T> = {
  success: boolean;
  data: T;
};

async function getProducts(): Promise<ApiResponse<string[]>> {
  return {
    success: true,
    data: ["Laptop", "Phone"],
  };
}
```

- Always type async return values
- Prefer `async/await` over chained `.then()`
- Use reusable API response types
- Handle errors with `try/catch`
- Avoid excessive nested async logic

---

## 📌 Debugging & Common Errors

TypeScript helps catch type-related issues during development before runtime.

| Error                  | Description               | Example                | Real-World Cause        |
| ---------------------- | ------------------------- | ---------------------- | ----------------------- |
| Type Mismatch          | Wrong value type assigned | `number = "10"`        | API/form data           |
| Implicit `any`         | Missing type definition   | Parameter without type | Unclear function inputs |
| Null/Undefined Error   | Possible missing value    | `user.name`            | Optional API data       |
| Property Doesn't Exist | Invalid property access   | `user.age`             | Wrong object structure  |
| Argument Type Error    | Invalid function argument | `fn(10)`               | Wrong API/helper usage  |
| Generic Type Error     | Incorrect generic usage   | `Promise<number>`      | Reusable utilities      |
| Module Not Found       | Invalid import path       | `import x`             | Wrong alias/path        |

```ts
// Type Mismatch
let age: number = "28"; // ❌ Error
```

```ts
// Implicit `any`
function greet(name) {
  // ❌ Error in strict mode
  return name;
}
```

```ts
// Null / Undefined
type User = {
  name?: string;
};

const user: User = {};

console.log(user.name?.toUpperCase());
```

```ts
// Property Doesn't Exist
const user = {
  name: "Naimesh",
};

console.log(user.age); // ❌ Error
```

```ts
// Argument Type Error
function total(price: number) {}

total("100"); // ❌ Error
```

```ts
// Generic Type Error
const data: Promise<number> = Promise.resolve("Hello"); // ❌ Error
```

```ts
// Module Not Found
import Button from "@/components/Button";
```

```json
{
  "baseUrl": "./src",
  "paths": {
    "@/*": ["*"]
  }
}
```

- Enable `strict` mode
- Avoid excessive `any`
- Use optional chaining for nullable values
- Type function params & returns clearly
- Keep reusable types centralized
- Use IDE IntelliSense & compiler errors actively

---

## 📌 Best Practices

TypeScript best practices improve scalability, readability, maintainability, and type safety.

| Practice                    | Description                      | Real-World Benefit      |
| --------------------------- | -------------------------------- | ----------------------- |
| Prefer Type Inference       | Avoid unnecessary explicit types | Cleaner code            |
| Avoid `any`                 | Preserve type safety             | Fewer runtime bugs      |
| Use Interfaces/Types        | Reuse object structures          | Maintainability         |
| Enable `strict` Mode        | Stronger type checking           | Safer applications      |
| Type Function Params        | Prevent invalid inputs           | Reliable utilities/APIs |
| Use Utility Types           | Reuse transformed types          | Less duplication        |
| Prefer `unknown` over `any` | Safer dynamic values             | Better validation       |
| Keep Types Predictable      | Avoid overly complex types       | Easier debugging        |
| Use Readonly Data           | Prevent accidental mutation      | Immutable state/config  |
| Organize Shared Types       | Centralize reusable models       | Scalable architecture   |

```ts
// Prefer Type Inference
let username = "Naimesh";
```

```ts
// Avoid `any`

// ❌ Avoid
let value: any = "Hello";

// ✅ Better
let value: unknown = "Hello";
```

```ts
// Reusable Interfaces
interface User {
  id: number;
  name: string;
}
```

```json
// Strict Mode
{
  "strict": true
}
```

```ts
// Type Function Parameters
function total(price: number): number {
  return price;
}
```

```ts
// Utility Types
type PublicUser = Omit<User, "password">;
```

```ts
// Readonly Data
type Config = Readonly<{
  apiUrl: string;
}>;
```

```ts
// Real-World Example
interface ApiResponse<T> {
  success: boolean;
  data: T;
}

async function fetchUsers(): Promise<ApiResponse<string[]>> {
  return {
    success: true,
    data: ["Naimesh", "Raj"],
  };
}
```

---

## 📌 Deprecated / Avoid Patterns

Avoiding unsafe or outdated TypeScript patterns improves maintainability and type safety.

| Pattern                | Why Avoid             | Better Alternative          | Real-World Issue        |
| ---------------------- | --------------------- | --------------------------- | ----------------------- |
| Excessive `any`        | Removes type safety   | `unknown`, unions, generics | Runtime bugs            |
| Unsafe Type Assertions | Bypass type checking  | Proper narrowing            | Invalid data access     |
| Deep Nested Types      | Hard to maintain      | Simpler reusable types      | Complex debugging       |
| Large Enums            | Difficult to scale    | Union literal types         | Over-engineered systems |
| Namespace Usage        | Outdated in modern TS | ES Modules                  | Legacy architecture     |
| Duplicate Types        | Repeated structures   | Shared interfaces/types     | Inconsistent models     |
| Overusing Generics     | Reduces readability   | Simpler types               | Confusing APIs          |
| Mutable Shared Data    | Unexpected changes    | `readonly`                  | State bugs              |

```ts
// Excessive `any`

// ❌ Avoid
let data: any = "Hello";

// ✅ Better
let data: unknown = "Hello";
```

```ts
// Unsafe Type Assertions

// ❌ Avoid
const value = input as string;

// ✅ Better
if (typeof input === "string") {
  console.log(input);
}
```

```ts
// Namespace Usage

// ❌ Avoid
namespace Utils {
  export const app = "MyApp";
}

// ✅ Better
export const app = "MyApp";
```

```ts
// Large Enums
// ❌ Large enum
enum Status {
  Pending,
  Approved,
  Rejected,
}
```

```ts
// ✅ Simpler union
type Status = "pending" | "approved" | "rejected";
```

```ts
// Mutable Shared Data
// ✅ Better
type Config = Readonly<{
  apiUrl: string;
}>;
```

- Prefer strict typing over shortcuts
- Keep types simple and reusable
- Use ES Modules instead of namespaces
- Prefer unions for small fixed values
- Avoid bypassing TypeScript safety checks

---
