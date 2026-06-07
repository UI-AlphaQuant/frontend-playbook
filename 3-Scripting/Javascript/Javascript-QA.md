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

### ❓ Undeclared vs Undefined

- Undeclared: Variable does not exist (Never declared)
  - Causes ReferenceError
- Undefined: Variable exists but has no value (Declared but not assigned)
  - No error

```js
// Undeclared
console.log(b); // ReferenceError: b is not defined

// Undefined
let a;
console.log(a);
```

### ❓ Types of Errors in JavaScript

- Common JavaScript errors are SyntaxError, ReferenceError, TypeError, RangeError, and URIError. The most frequently encountered are ReferenceError and TypeError.

- Syntax Error - Invalid JavaScript syntax.
- Reference Error - Using a variable that doesn't exist.
- Type Error - Operation performed on the wrong type.
- Range Error - Value out of allowed range.
- URI Error - Incorrect URI encoding/decoding.
- Eval Error (Rare)

```js
// SyntaxError
console.log("Hello" // SyntaxError: missing ) after argument list

// Reference Error
console.log(a); //ReferenceError: user is not defined

// Type Error
const num = 10;
num.toUpperCase(); // TypeError: num.toUpperCase is not a function

// Range Error
const arr = new Array(-1); // RangeError: Invalid array length

// URI Error
decodeURIComponent("%"); // URIError: URI malformed

// Eval Error
throw new Error("Something went wrong"); // Error: Something went wrong
```

- EvalError is a legacy error type related to eval(). Modern JavaScript engines rarely throw it in real-world applications.

### ❓ Can let and const be redeclared?

- No. Both let and const cannot be redeclared in the same scope.
- let and const cannot be redeclared in the same scope. let can be reassigned, while const cannot.

```js
let a = 10;
let a = 20;
// SyntaxError: Identifier 'a' has already been declared

// Reassignment
let a = 10;
a = 20; // ✅ Allowed

const b = 10;
b = 20; // TypeError: Assignment to constant variable
```

### ❓ What is Temporal Dead Zone (TDZ)?

- The Temporal Dead Zone is the period between entering a scope and the point where a let or const variable is declared.
- During this period, accessing the variable throws an error.

```js
// TDZ starts
console.log(a);
// ReferenceError: Cannot access 'a' before initialization
// TDZ ends

let a = 10;
```

- let and const are hoisted, but they are not initialized until their declaration is reached.

```js
console.log(a); // undefined

var a = 10;
```

### ❓ Object Destructuring

- Object destructuring is a way to extract values from an object into variables.

```js
const user = {
  name: "Ram",
  age: 25,
};

const { name, age } = user;

console.log(name); // Ram
console.log(age); // 25
```

### ❓ How to delete object properties in JavaScript?

- The delete operator removes a property from an object, but it does not affect variables or reassign the object itself.

```js
// Delete operator
const user = {
  name: "Ram",
  age: 25,
};
delete user.age;
console.log(user); // { name: "Ram" }

// Delete Nested Property
const user = {
  name: "Ram",
  address: {
    city: "FBD",
  },
};
delete user.address.city;
console.log(user.address);

// You cannot use delete on normal variables.
let a = 10;
delete a;
console.log(a); // 10 (unchanged)
```

- delete → only works on object properties (not on variables)
- Cannot delete variables declared with let, const, var
- Variables are stored in memory scope, not object properties.

### ❓ Looping Structures in JavaScript

- Loops are used to repeat code multiple times.
- Different loops serve different purposes:
  - for (fixed iteration), while (condition-based), do-while (run once first), for...of (values), for...in (object keys), and forEach (array functional iteration).
- JavaScript provides loops like for, while, do-while, for...of, for...in, and forEach to iterate over data structures.
  1. for - When you know exact number of iterations
     - Fixed range looping, Index-based iteration
  2. while - When condition decides repetition
     - Unknown number of iterations, Run until condition becomes false
  3. do...while - Runs at least once
     - Execute first, then check condition, Input validation cases
  4. for...of - Iterate values of arrays / iterables
     - Get values directly, Clean array iteration
  5. for...in - Iterate keys of object
     - Loop through object properties
  6. forEach - Array method for iteration
     - Functional style looping, Cleaner array operations, No manual index handling

```js
// >>>>> for loop
for (let i = 0; i < 5; i++) {
  console.log(i);
}
// Print: 0 to 4

// >>>>> while loop
let i = 0;
while (i < 5) {
  console.log(i);
  i++;
}
// Print: 0 to 4

// >>>>> do...while loop
let i = 0;
do {
  console.log(i);
  i++;
} while (i < 5);
// Print: 0 to 4

// >>>>> for...of loop (arrays)
const arr = [10, 20, 30];
for (let val of arr) {
  console.log(val);
}
// 10
// 20
// 30

// >>>>> for...in loop (objects)
const obj = { a: 1, b: 2 };
for (let key in obj) {
  console.log(key, obj[key]);
}
// a 1
// b 2

// >>>>> forEach loop (array method)
[1, 2, 3].forEach((num) => {
  console.log(num);
});
// 1
// 2
// 3
```

### ❓ How to convert an object into an array in JavaScript

- Use Object.keys() for keys, Object.values() for values, and Object.entries() for key-value pairs when converting objects into arrays.

```js
// Object.keys() → keys array
const obj = { a: 1, b: 2 };
console.log(Object.keys(obj)); // ["a", "b"]

// Object.values() → values array
const obj = { a: 1, b: 2 };
console.log(Object.values(obj)); // [1, 2]

// Object.entries() → key-value pairs array
const obj = { a: 1, b: 2 };
console.log(Object.entries(obj)); // [["a", 1], ["b", 2]]
```

```js
// Convert entries back to array processing
const obj = { a: 1, b: 2 };
const arr = Object.entries(obj).map(([key, value]) => {
  return key + value;
});

console.log(arr); // ["a1", "b2"]
```

### ❓ Function Declaration vs Function Expression

- Function declaration is hoisted and can be called before definition, while function expression is not hoisted and is assigned to a variable.

```js
// >>>>> Function declaration
// Hoisted (can be called before declaration)
function greet() {
  console.log("Hello");
}
greet(); // Hello

// >>>>> Function expression
// Not hoisted (cannot be called before)
const greet = function () {
  console.log("Hello");
};
greet(); // Hello
```

### ❓ Higher Order Function (HOF)

- A Higher Order Function is a function that takes another function as an argument or returns a function.
- Common HOFs in JS: map(), filter(), reduce(), forEach()

```js
// Takes function as argument
function greet(name) {
  return `Hello ${name}`;
}
function processUser(fn) {
  console.log(fn("Ram"));
}
processUser(greet); // Hello Ram

// Real Example (Array Methods)
[1, 2, 3].map((num) => num * 2); // [2, 4, 6]
```

- map() iterates over an array, applies a function to each element, and returns a new transformed array.

### ❓ map() vs forEach()

- map() returns a new transformed array, while forEach() is used only for iteration and does not return anything.
- map()
  - Used for transformation
  - Chainable
- forEach()
  - Used for iteration
  - Not chainable

```js
// map → when you need transformed data
const prices = [100, 200, 300];
const gstPrices = prices.map((p) => p * 1.18);
console.log(gstPrices); // [ 118, 236, 354 ]

// forEach → when you just want to perform action
prices.forEach((p) => console.log(p)); // 100, 200, 300
```

### ❓ Rest Operator (...) Example in JavaScript

- The rest operator (...) collects multiple function arguments or remaining values into a single array.

```js
function sum(...nums) {
  console.log(nums);
}

sum(1, 2, 3, 4); // [1, 2, 3, 4]
```

### ❓ JSON.parse() Usage in JavaScript?

- JSON.parse() converts a JSON string into a JavaScript object
- JSON.parse works only on valid JSON string

```js
const response = '{"id":1,"product":"Phone","price":20000}';
const data = JSON.parse(response);
console.log(data.product); // Phone

// Another example:
JSON.parse("{name: Ram}"); // Error (keys must be in double quotes)
```

### ❓ JSON Methods in JavaScript

- JSON.parse() > Converts JSON string → JavaScript object
- JSON.stringify() > Converts JavaScript object → JSON string

```js
// parse
const str = '{"name":"Ram","age":25}';
const obj = JSON.parse(str);
console.log(obj.name); // Ram

// stringify
const obj = { name: "Ram", age: 25 };
const str = JSON.stringify(obj);
console.log(str); // {"name":"Ram","age":25}
```

- Real-life use: API request/response

```js
// sending data
fetch("/api", {
  method: "POST",
  body: JSON.stringify({ name: "Ram" }),
});

// receiving data
const data = JSON.parse(response);
```

### ❓ call, apply, bind in JavaScript

- All three are used to control this context in functions.
  - call() - Calls function immediately, Arguments passed one by one
  - apply() - Calls function immediately, Arguments passed as array
  - bind() - Does NOT call immediately, Returns a new function

```js
// call
function order(city) {
  console.log(this.name + " orders food from " + city);
}
const user = { name: "Ram" };
order.call(user, "Delhi"); // Ram orders food from Delhi

// apply
order.apply(user, ["Delhi"]); // Ram orders food from Delhi

// bind
const task = order.bind(user, "Delhi");
task(); // Ram orders food from Delhi
```

```text
greet() called
→ this = undefined (or window in non-strict)
→ output may be undefined

// Call
1. Function is called
2. JS sets this = user
3. Executes immediately
4. prints "Ram"

// apply
1. Function is called
2. this = user
3. arguments passed as array
4. executes immediately

// bind
STEP 1:
bind() creates NEW function
→ this is locked to user
→ NOT executed yet

STEP 2:
fn() called later
→ now function executes
→ prints "Ram"
```

### ❓ Normal Function vs Arrow Function

```js
// Normal Funtion
function sum(a, b) {
  return a + b;
}

// Arrow Function
const sum = (a, b) => a + b;
```

- Normal Funtion, use function keyword
  - Normal Function → has its own this
  - Own this
  - Fully hoisted (can use before declaration)
- Arrow Function, use =>
  - Arrow Function → no own this (inherits)
  - Lexical this
  - Only variable is hoisted (as undefined)

### ❓ Types of Scope in JavaScript?

- Global Scope - Variables declared outside any function/block
- Local Scope (Function Scope) - Variables Only accessible inside function
- Block Scope - Variables inside { } (with let, const)
- Lexical Scope - Inner function can access outer variables

```js
// Global Scope
let a = 10;
function test() {
  console.log(a);
}
test(); // 10

// Function Scope (Local Scope)
function test() {
  let b = 20;
  console.log(b);
}
test(); // 20

// Block Scope
{
  let c = 30;
  const d = 40;
}
console.log(c); // ❌ Error
console.log(d); // ❌ Error

// Lexical Scope
function outer() {
  let x = 50;
  function inner() {
    console.log(x);
  }
  inner();
}
outer(); // 50
```

### ❓ Lexical Scope vs Closure

- Closure is not just lexical scope; it is a function that remembers variables from its lexical scope even after the outer function has finished execution.

```js
function outer() {
  let x = 10;
  return function inner() {
    console.log(x);
  };
}
const fn = outer();
fn(); // 10
```

```text
outer() runs → finishes execution
but inner() still remembers x = 10
this "memory + function" = closure
```

- Lexical scope → house rules (who can access what)
- Closure → you took keys of the house with you after leaving
  - Closure = lexical scope + function + preserved memory

### ❓ Methods vs Keywords in JavaScript

- Keywords: Reserved words in JavaScript with special meaning, You cannot use them as variable names, Define logic
- Methods: Functions that belong to an object, Perform actions

### ❓ ES6 Features

```js
// let / const
// Block scoped variables.
// Let vs Var fix (Block scope introduced in ES6)

// Arrow Functions
const sum = (a, b) => a + b;

// Template Literals
`Hello ${name}`;

// Destructuring
const { name, age } = user;
const [a, b] = arr;

// Default Parameters
function add(a = 0, b = 0) {}

// spread / rest
const newArr = [...arr, 4];
function sum(...nums) {}

// Promises
fetch(url).then((res) => res.json());

// Modules
import x from "./file";
export default x;
```

### ❓ Difference between == and ===?

- == compares values after converting types
- === compares value + type without conversion

```js
console.log("1" == 1); // true
console.log("1" === 1); // false

console.log([] == []); // false
console.log([] === []); // false
```

- Arrays are reference types, so comparison checks memory address, not content.
- Objects/arrays are compared by reference, not value.

### ❓ primitive and non-primitive data types?

- Primitive → single value, stored by value
- Non-Primitive → objects, stored by reference

```js
// Primitive
let num = 10;
let str = "hello";
let bool = true;
let n = null;
let u = undefined;
let sym = Symbol("id");
let big = 123n;

// Non-Primitive
let obj = { name: "Rao" };
let arr = [1, 2, 3];
function fn() {}
```

- Primitive stores value, Non-primitive stores reference.
- Primitive = copy value, Non-primitive = share reference.

### ❓ difference between every() and some()?

- every() → all elements must pass condition
  - Form Validation (every)
- some() → at least one element must pass condition
  - Permission / Feature Check (some)

```js
const nums = [2, 4, 6];

// every
console.log(nums.every((n) => n % 2 === 0)); // true

// some
console.log(nums.some((n) => n > 5)); // true
```

- every() = all true, some() = any one true.

### ❓ difference between then() and finally() in Promises?

- then() → runs when promise is resolved (success) show API data on UI
- finally() → runs always (success or error) stop loader/spinner

```js
let loading = true;

fetch("/api/data")
  .then((res) => res.json()) // Converts response to JSON (success step)
  .then((data) => console.log(data)) // Uses the data (success handling)
  .finally(() => {
    loading = false; // hide loader
  }); // Runs ALWAYS (success or error) → cleanup step
```

### ❓ What is a constructor?

- A constructor is a special function used to create and initialize objects.

```js
class User {
  constructor(name) {
    this.name = name;
  }
}

const u1 = new User("Smith");
console.log(u1.name); // Smith
```

### ❓ add and remove values in an array?

- push/unshift = add, pop/shift = remove.

```js
let arr = [1, 2, 3];

// add
arr.push(4); // end
arr.unshift(0); // start

// remove
arr.pop(); // end
arr.shift(); // start
```

### ❓ add and remove elements in the middle of an array?

```js
// Example (Remove in between)
let arr = [10, 20, 30, 40];
arr.splice(2, 1); // remove index 2
console.log(arr); // [10, 20, 40] // start at index 1, remove 2 items

// Example (Add in between)
let arr = [10, 40];
arr.splice(1, 0, 20, 30);
console.log(arr); // [10, 20, 30, 40] // at index 1, remove 0 items, add values
```

### ❓ typeof null and typeof undefined?

```js
console.log(typeof null); // "object"
console.log(typeof undefined); // "undefined"
```

- Returns "object" (historical JavaScript bug)

### ❓ Run a JavaScript file from VS Code terminal?

```bash
node main.js
```

### ❓ difference between filter() and find()?

- filter() → returns all matching items (array)
- find() → returns first matching item

```js
const users = [
  { id: 1, name: "Nick", active: true },
  { id: 2, name: "John", active: false },
  { id: 3, name: "Sam", active: true },
];
const activeUsers = users.filter((user) => user.active);
const user = users.find((user) => user.id === 2);

console.log(activeUsers); // find -> get user with id 2
console.log(user); // filter -> get all active users
```

### ❓

```js
// Comment
```

### ❓

```js
// Comment
```

### ❓

```js
// Comment
```

### ❓

```js
// Comment
```

### ❓

```js
// Comment
```
