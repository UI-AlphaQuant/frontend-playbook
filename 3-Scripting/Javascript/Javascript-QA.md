# JavaScript – Interview Q&A

## � BASIC

**Q:** What is JavaScript?
**A:** High-level, dynamic programming language used to create interactive web applications. Runs in browsers and Node.js environments.

**Q:** What is the difference between JavaScript and Java?
**A:** JavaScript is for frontend/backend, Java is for backend/Android. Different syntax, different purposes. Both use similar naming but are completely different.

**Q:** What are the data types in JavaScript?
**A:** Primitive: string, number, boolean, null, undefined, symbol, BigInt. Reference: object, array, function.

**Q:** What is string concatenation?
**A:** Joining two or more strings together using `+` operator or template literals. Example: `"Hello" + " " + "World"` or `` `Hello ${name}` ``.

**Q:** What is template literal?
**A:** String enclosed in backticks (`` ` ``) allowing embedded expressions. Example: `` `Hello ${name}` ``.

**Q:** What is type coercion in JavaScript?
**A:** Automatic conversion of one data type to another during operations. Example: `"5" + 2 = "52"` (string coercion) or `"5" - 2 = 3` (numeric coercion).

**Q:** Difference between `==` and `===`?
**A:** `==` does type coercion before comparing (loose equality). `===` doesn't coerce, strict comparison. `0 == false` is true, but `0 === false` is false.

**Q:** What is `i++` vs `++i`?
**A:** Both increment but differ in return value. `i++` returns old value, `++i` returns new value. In loops, performance is similar.

**Q:** What is hoisting?
**A:** Variables and function declarations are moved to top of scope during compilation. `var` and functions are hoisted, `let`/`const` are hoisted but not initialized (temporal dead zone).

**Q:** Difference between `var`, `let`, and `const`?
**A:** `var` is function-scoped, `let`/`const` are block-scoped. `const` cannot be reassigned. Use `const` by default, `let` when value changes.

**Q:** What is scope?
**A:** Region of code where variable is accessible. Types: global scope, function scope, block scope.

**Q:** What is closure?
**A:** Function that remembers variables from outer scope even after outer function completes. Used for data privacy and callbacks.

**Q:** What is an arrow function?
**A:** Concise syntax for functions using `=>`. Example: `const add = (a, b) => a + b`. Doesn't have own `this` binding.

**Q:** Synchronous vs Asynchronous JavaScript?
**A:** Synchronous executes one task at a time, waiting for each to complete. Asynchronous allows long-running tasks to execute in background while code continues.

**Q:** What is a callback?
**A:** Function passed as argument to another function, called later to complete some action. Often used for asynchronous operations.

**Q:** What is Promise?
**A:** Object representing eventual completion (or failure) of async operation. Has states: pending, fulfilled, rejected. Can chain with `.then()` and `.catch()`.

**Q:** What is async/await?
**A:** Cleaner syntax for working with Promises. `async` function returns promise. `await` pauses execution until promise resolves.

**Q:** What is an event listener?
**A:** Function that waits for specific event (click, input, etc.) then executes code. Example: `element.addEventListener('click', callback)`.

**Q:** What is Event Delegation?
**A:** Technique of attaching listener to parent element instead of individual child elements. Saves memory and handles dynamic elements. Event bubbles up to parent.

---

## � INTERMEDIATE

**Q:** Explain the difference between shallow copy and deep copy?
**A:** Shallow copy copies only references of nested objects. Deep copy recursively copies all levels. Use `structuredClone()` or libraries for deep copy.

**Q:** What is the call stack and callback queue?
**A:** Call stack executes synchronous code. Callback queue holds asynchronous callbacks. Event loop moves callbacks from queue to stack when stack is empty.

**Q:** Explain the event loop?
**A:** JavaScript is single-threaded. Event loop checks call stack. If empty, moves callback from queue to stack. Manages synchronous and asynchronous code execution.

**Q:** What is the difference between `null` and `undefined`?
**A:** `null` is explicitly assigned value meaning "no value". `undefined` is default value for uninitialized variables. `typeof null` returns "object" (JS quirk).

**Q:** What is destructuring?
**A:** Extract values from arrays or objects into distinct variables. Example: `const {name, age} = person` or `const [a, b] = [1, 2]`.

**Q:** What is spread operator (`...`)?
**A:** Expands iterable (array, string) into individual elements. Used for copying arrays, merging, function arguments. Example: `[...arr1, ...arr2]`.

**Q:** What is rest parameter?
**A:** Collects remaining arguments into array. Used in function parameters. Example: `function sum(...numbers)` collects all arguments into array.

**Q:** Difference between `map()` and `forEach()`?
**A:** `map()` returns new array with transformed elements. `forEach()` iterates and performs action, returns undefined. Use `map()` when you need new array.

**Q:** What is `filter()` method?
**A:** Returns new array containing only elements that satisfy condition. Example: `arr.filter(x => x > 5)`.

**Q:** What is `reduce()` method?
**A:** Accumulates array into single value using callback function. Example: `arr.reduce((sum, x) => sum + x, 0)` calculates sum.

**Q:** What is `this` keyword?
**A:** Refers to object that function belongs to. Value depends on how function is called. In arrow functions, `this` is inherited from parent scope.

**Q:** Difference between `call()`, `apply()`, and `bind()`?
**A:** All set `this` context. `call()` passes args individually. `apply()` passes args as array. `bind()` returns new function with fixed context.

**Q:** What is `setTimeout()` and `setInterval()`?
**A:** `setTimeout()` executes code after delay (once). `setInterval()` executes code repeatedly at intervals. Both are asynchronous.

**Q:** What is JSON?
**A:** JavaScript Object Notation. Lightweight text format for data exchange. `JSON.stringify()` converts object to JSON, `JSON.parse()` converts JSON to object.

**Q:** What is the difference between `push()` and `concat()`?
**A:** `push()` modifies original array (mutates). `concat()` returns new array without modifying original.

**Q:** What is optional chaining (`?.`)?
**A:** Safely accesses nested properties without checking if each level exists. Example: `obj?.name?.firstName` returns undefined if any level is null/undefined.

**Q:** What is nullish coalescing (`??`)?
**A:** Returns right operand if left is null or undefined. Different from `||` which treats falsy values (0, false, "") as null. Example: `value ?? 'default'`.

**Q:** What is currying?
**A:** Technique of converting function with multiple args into sequence of functions with single arg. Useful for partial application and function composition.

**Q:** What is memoization?
**A:** Caching technique to store function results and return cached result for same inputs. Improves performance for expensive calculations.

**Q:** Real-life: How would you make API calls efficiently with error handling?
**A:** Use async/await with try-catch. Implement retry logic for failed requests. Cancel previous requests before new ones. Use request timeout. Handle network errors gracefully.

**Q:** Calculation: If array has 1000 items and you call `map()` twice, how many iterations total?
**A:** 2000 iterations total (1000 for first map, 1000 for second map). Chain them: `arr.map(x => x * 2).map(x => x + 1)`.

---

## � ADVANCED

**Q:** Explain JavaScript execution context?
**A:** Global execution context created on page load. Function execution context created when function called. Each has variable object, scope chain, and `this` binding.

**Q:** What is the scope chain?
**A:** JavaScript looks for variables in current scope, then parent scope, then grandparent, etc. until found or reaches global scope. Creates hierarchy of scopes.

**Q:** Explain prototypal inheritance?
**A:** Objects inherit from prototype objects. Every object has `__proto__` pointing to prototype. Chain continues until reaching `null`. ES6 classes are syntactic sugar over prototypes.

**Q:** What is the difference between prototype and `__proto__`?
**A:** `prototype` is property of constructor functions. `__proto__` is reference to prototype object in instance. `obj.__proto__ === Constructor.prototype`.

**Q:** What is `Object.create()` and why use it?
**A:** Creates new object with specified prototype. Allows custom prototype chain without constructor function. Example: `Object.create(parentObj)`.

**Q:** Difference between constructor function and ES6 class?
**A:** ES6 classes are cleaner syntax for constructor functions. Both use prototypes internally. Classes have implicit strict mode, hoisting differs.

**Q:** What is `new` operator?
**A:** Creates new object instance. Sets `this` to new object. Sets object's `__proto__` to constructor's prototype. Returns the object (unless constructor returns object).

**Q:** What are generators?
**A:** Functions that can pause and resume using `yield` keyword. Return iterator objects. Useful for lazy evaluation and custom iteration patterns.

**Q:** What is the difference between `Symbol` and other primitives?
**A:** `Symbol` creates unique, immutable identifier. No two symbols are equal even if created with same description. Used for object property keys to avoid collision.

**Q:** Explain Proxy and Reflect?
**A:** `Proxy` intercepts object operations (get, set, delete, etc.). `Reflect` provides methods to perform default operations. Used for validation, logging, data binding.

**Q:** What is WebWorker?
**A:** Runs JavaScript in background thread separate from main thread. Prevents blocking UI. Can't access DOM. Used for heavy computations, file processing.

**Q:** What is garbage collection in JavaScript?
**A:** Automatic process of freeing memory from unused objects. JavaScript engines use mark-and-sweep algorithm. Objects with no references are collected.

**Q:** Real-life (Indian banking context): Implement secure API token management?
**A:** Store token in secure httpOnly cookie (not localStorage). Implement token refresh mechanism. Use CSRF tokens. Validate on backend. Clear token on logout. Handle token expiration gracefully.

**Q:** Real-life: Optimize large data list rendering (1 million items)?
**A:** Use virtual scrolling (only render visible items). Implement pagination. Use `debounce` or `throttle` for scroll events. Consider server-side pagination. Use `requestAnimationFrame` for smooth rendering.

**Q:** Real-life: Debug memory leak in production?
**A:** Use Chrome DevTools memory profiler. Take heap snapshots. Compare snapshots to find retained objects. Check for detached DOM nodes, circular references, unremoved event listeners.

**Q:** Calculation: If user types character every 50ms, and validation function takes 200ms, how many validation calls are made without debouncing?
**A:** Without debouncing = user typing "hello" (5 chars) = 5 validation calls = 1000ms total wasted. With debouncing (300ms delay) = only 1 final validation call. Save ~4 calls and 800ms.

**Q:** Calculation: Memory calculation - if each object takes 1KB and you have 100,000 objects with references, what's total memory impact?
**A:** Raw objects = 100KB. But with closures/circular references, impact multiplies. Bad practice: `for(var i=0;i<100000;i++)` creates global reference, preventing garbage collection. Could be 1MB+ retained.

---

## Quick Reference

| Concept          | Example                                         |
| ---------------- | ----------------------------------------------- |
| Template Literal | `` `Hello ${name}` ``                           |
| Destructuring    | `const {x, y} = obj` or `const [a, b] = arr`    |
| Spread Operator  | `[...arr]` or `{...obj}`                        |
| Arrow Function   | `const fn = () => {}`                           |
| Async/Await      | `const result = await asyncFunc()`              |
| Promise          | `.then().catch().finally()`                     |
| Closure          | Function accessing outer scope variables        |
| Event Delegation | Listener on parent handles child events         |
| Callback         | Function passed as argument to another function |

---

### ❓ Q: What is Destructuring in JavaScript?

- Destructuring is a JavaScript feature that allows you to extract values from arrays or properties from objects into separate variables in a concise way.

```js
// Array
const colors = ["Red", "Green", "Blue"];
const [first, second] = colors;

console.log(first); // Red
console.log(second); // Green

// Object
const user = {
  name: "Naimesh",
  role: "Frontend Developer",
};
const { name, role } = user;

console.log(name); // Naimesh
console.log(role); // Frontend Developer
```

### ❓ Difference between the Rest (...) and Spread (...) operators.

- Rest Operator: Collects multiple values into one variable
- Spread Operator: Expands values from an array/object

```js
// Rest Operator
function sum(...numbers) {
  return numbers.reduce((a, b) => a + b, 0);
}
sum(10, 20, 30); // 60

// Array Destructuring
const [first, ...others] = [1, 2, 3, 4];
console.log(first); // 1
console.log(others); // [2, 3, 4]
```

```js
// Spread Operator
const arr1 = [1, 2, 3];
const arr2 = [...arr1];
console.log(arr2); // [1, 2, 3]

// Merge Array
const a = [1, 2];
const b = [3, 4];
const result = [...a, ...b];
console.log(result); // [1, 2, 3, 4]

// Passing Props
const props = {
  name: "Naimesh",
  age: 30,
};
<UserCard {...props} />;
```

### ❓ What will be the output?

```js
let person = {
  name: "ram",
  age: 15,
  add: {
    city: "fbd",
  },
};

let employ = person;

employ.name = "shyam";
employ.add.city = "blb";

console.log(person);
console.log(employ);

// Output
{
  name: "shyam",
  age: 15,
  add: {
    city: "blb"
  }
}

{
  name: "shyam",
  age: 15,
  add: {
    city: "blb"
  }
}
```

- Why? Both person and employ point to the same object in memory.
- Because both variables reference the same object.

```js
let employ = person;
```

### ❓ Why were Promises introduced in JavaScript?

- Promises were introduced to simplify asynchronous programming, avoid callback hell, and provide better error handling and chaining.

```js
// Before Promises (Callback Hell)
getUser(function (user) {
  getOrders(user.id, function (orders) {
    getPayment(orders, function (payment) {
      // nested callbacks
    });
  });
});

// With Promises
getUser().then(getOrders).then(getPayment).catch(handleError);
```

### ❓ What are Promises, and how do they help in handling asynchronous operations?

- A Promise is an object that represents the eventual result of an asynchronous operation.
- Promises help manage asynchronous operations by avoiding callback hell and providing cleaner chaining and error handling.
- Without Promises, you would use callbacks. (Too much nesting.)

**Promise States:**

- Pending → Initial state
- Fulfilled → Operation completed successfully
- Rejected → Operation failed

```js
// Without Promise
getUser(function (user) {
  getOrders(user, function (orders) {
    getPayment(orders, function (payment) {
      console.log(payment);
    });
  });
});

// With Promise
getUser()
  .then(getOrders)
  .then(getPayment)
  .then(console.log)
  .catch(console.error);

// A Promise is like ordering food online—you don't get the result immediately, but you're notified later whether it was delivered (resolved) or cancelled (rejected).
const foodOrder = new Promise((resolve, reject) => {
  const delivered = true;

  if (delivered) {
    resolve("Food delivered");
  } else {
    reject("Order cancelled");
  }
});

foodOrder.then((msg) => console.log(msg)).catch((err) => console.log(err));
```

### ❓ Explain the JavaScript Event Loop. What are the Microtask Queue and Macrotask Queue?

- JavaScript is single-threaded, but it can handle async tasks using the Event Loop.

**The Event Loop continuously checks:**

- Call Stack
- Microtask Queue (Higher Priority)
  - Promise.then(), catch(), finally(), queueMicrotask()
- Macrotask Queue
  - setTimeout(), setInterval(), DOM Events

```js
// Example
console.log("1");
setTimeout(() => console.log("2"), 0);
Promise.resolve().then(() => console.log("3"));
console.log("4");

// 1
// 4
// 3
// 2
```

### ❓ null vs undefined

- null: Intentional absence of value
- undefined: Value not assigned

```js
let a;
console.log(a); // undefined

let b = null;
console.log(b); // null

console.log(typeof undefined); // "undefined"
console.log(typeof null); // "object"

console.log(null == undefined); // true
console.log(null === undefined); // false
```

### ❓ Template Literals

- Use backticks ` ` to embed variables and expressions inside strings.

```js
const a = 10;
const b = 20;
const sum = `Sum: ${a + b}`;

console.log(sum);
// Sum: 30
```

### ❓ Why use Optional Chaining (?.)?

- Optional chaining prevents errors when accessing properties that may be null or undefined.
- Optional chaining (?.) safely accesses nested properties without throwing errors if an intermediate value is null or undefined.

```js
// Without Optional Chaining
const user = {};
console.log(user.address.city); // ❌ Cannot read properties of undefined

// With Optional Chaining
const user = {};
console.log(user.address?.city); // undefined

console.log(user?.profile?.name);
```

### ❓ What is a Polyfill?

- A polyfill is custom code that adds support for modern JavaScript features in older browsers that don't natively support them.
- Mostly just a concept to understand nowadays. As a React developer in 2026, you rarely write polyfills manually.
- Babel automatically add required polyfills based on browser support targets.

```text
// Common polyfill
Array.prototype.includes
Array.prototype.flat
Promise
fetch
```

### ❓ What is a Transpiler?

- A transpiler converts code from one version/language to another similar version/language.
- Older browsers may not support modern JS features.
- Common Transpiler: Babel (converts modern JavaScript (ES6+) into browser-compatible JavaScript.)

```js
// Modern JS
const sum = (a, b) => a + b;

// Transpiled to older JavaScript
var sum = function (a, b) {
  return a + b;
};
```

```js
// Operator
```

```js
// Operator
```

```js
// Operator
```

```js
// Operator
```

```js
// Operator
```

```js
// Operator
```

```js
// Operator
```

```js
// Operator
```

```js
// Operator
```

```js
// Operator
```
