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

---

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

---

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

---

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

---

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

---

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

---

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

---

### ❓ Template Literals

- Use backticks ` ` to embed variables and expressions inside strings.

```js
const a = 10;
const b = 20;
const sum = `Sum: ${a + b}`;

console.log(sum);
// Sum: 30
```

---

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

---

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

---

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

---

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

---

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

---

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

---

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

---

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

---

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

---

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

---

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

---

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

---

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

---

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

---

### ❓ Rest Operator (...) Example in JavaScript

- The rest operator (...) collects multiple function arguments or remaining values into a single array.

```js
function sum(...nums) {
  console.log(nums);
}

sum(1, 2, 3, 4); // [1, 2, 3, 4]
```

---

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

---

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

---

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

---

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

---

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

---

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

---

### ❓ Methods vs Keywords in JavaScript

- Keywords: Reserved words in JavaScript with special meaning, You cannot use them as variable names, Define logic
- Methods: Functions that belong to an object, Perform actions

---

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

---

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

---

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
let obj = { name: "Nick" };
let arr = [1, 2, 3];
function fn() {}
```

- Primitive stores value, Non-primitive stores reference.
- Primitive = copy value, Non-primitive = share reference.

---

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

---

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

---

### ❓ What is a constructor?

- A constructor is a special method inside a class that automatically runs when an object is created using new, and it is used to initialize object properties.
- A constructor is used to create multiple objects with the same structure while initializing them with different values.
- Usage:
  - Creating multiple users
  - Product objects in e-commerce
  - Form models in apps
  - API response modeling

```js
class Employee {
  constructor(name, role) {
    this.name = name;
    this.role = role;
  }
}

const emp1 = new Employee("Nick", "Frontend Developer");
const emp2 = new Employee("John", "QA Engineer");

console.log(emp1); // { name: "Nick", role: "Frontend Developer" }
console.log(emp2); // { name: "John", role: "QA Engineer" }
```

---

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

---

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

---

### ❓ typeof null and typeof undefined?

```js
console.log(typeof null); // "object"
console.log(typeof undefined); // "undefined"
```

- Returns "object" (historical JavaScript bug)

---

### ❓ Run a JavaScript file from VS Code terminal?

```bash
node main.js
```

---

### ❓ difference between filter() and find()?

- filter() → returns an array of all matching elements. (array)
- find() → returns only the first matching element or undefined if none is found. (Single value)

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

---

### ❓ difference between some() and every()?

- some() → at least one item matches
  - Check if any required field is empty
- every() → all items must match
  - Validate all form fields before submit

```js
const users = [
  { name: "Nick", active: true },
  { name: "John", active: true },
  { name: "Sam", active: false },
];
const hasInactiveUser = users.some((user) => !user.active); // some -> is any user inactive?
const allUsersActive = users.every((user) => user.active); // every -> are all users active?

console.log(hasInactiveUser); // true
console.log(allUsersActive); // false
```

---

### ❓ Self-Invoking Function (IIFE) in JavaScript?

- An IIFE (Immediately Invoked Function Expression) runs immediately after it is created.
- Common in older JS code before modules

```js
(function () {
  console.log("Hello");
})();
```

---

### ❓ Anonymous Function in JavaScript?

- An anonymous function is a function without a name.

```js
const users = ["Nick", "John"];
const result = users.map(function (user) {
  return user.toUpperCase();
});

console.log(result); // [ 'NICK', 'JOHN' ]
```

---

### ❓ Currying in JavaScript?

- Currying converts a function with multiple arguments into a series of functions that take one argument at a time.
- Currying breaks a function into multiple functions, each taking one argument.

```js
// S1
function add(a) {
  return function (b) {
    return a + b;
  };
}

console.log(add(5)(3)); // 8

// S2
const withAuth = (token) => (url) =>
  fetch(url, {
    headers: { Authorization: token },
  });
```

---

### ❓ scope of var in JavaScript?

- var is function-scoped, not block-scoped.
- var is function-scoped and ignores block scope (if, for, while).

```js
// S1
if (true) {
  var name = "Nick";
}
console.log(name); // Nick

// S1
function user() {
  var role = "Admin";
}
console.log(role); // ReferenceError: role is not defined
```

---

### ❓ Callback Function in JavaScript?

- A callback is a function passed as an argument to another function and executed later.
- Event handlers (onClick), Array methods (map, filter, forEach), Timers (setTimeout)

```js
function greet(name, callback) {
  console.log(`Hello ${name}`);
  callback();
}

greet("Nick", () => console.log("Welcome")); // Hello Nick Welcome
```

---

### ❓ difference between var, let, and const?

- var, let, and const are used to declare variables, but they differ in scope, redeclaration, and reassignment behavior.
  - var - Function Scope, Hoisted
  - let - Block Scope, Hoisted (TDZ)
  - const - Block Scope, Hoisted (TDZ)
- Use const by default, let when the value changes, and avoid var because it is function-scoped and allows redeclaration.

```js
// >>>>> var
var a = 10;
var a = 20; // ✅ redeclare
a = 30; // ✅ update

// >>>>> let
let b = 10;
// let b = 20; // ❌ redeclare
b = 30; // ✅ update

// >>>>> const
const c = 10;
// const c = 20; // ❌ redeclare
// c = 30;       // ❌ update

// >>>>> Real-life Usage
const API_URL = "/users"; // fixed
let count = 0; // changes
var oldCode = "legacy"; // avoid in modern JS
```

---

### ❓ Array Destructuring in JavaScript?

- Array destructuring is a way to extract values from an array into variables using a simple syntax.

```js
const arr = [10, 20, 30];
const [a, b, c] = arr; // OR [a, b, c] = [10, 20, 30]

console.log(a);
console.log(b);
console.log(c);
```

---

### ❓ What is variable shadowing in JavaScript?

- Variable shadowing happens when a local variable (inside a block or function) has the same name as a global variable, and the local one overrides the global one within its scope.

```js
// Comment
let a = 10;

function test() {
  let a = 50; // local shadows global
  console.log(a);
}

test(); // 50
console.log(a); // 10
```

---

### ❓ Hoisting inside a function in JavaScript?

- Hoisting is JavaScript’s behavior where variable and function declarations are moved to the top of their scope (function scope or block scope during compile phase) before code execution.

```js
function test() {
  console.log(a);
  var a = 10;
}

test(); // undefined
```

---

### ❓ Declaration, Assignment, Expression in JavaScript?

- Declaration is creating a variable, while assignment is giving a value to that variable.
- An expression is any valid JavaScript code that produces a value.

```js
let a; // declaration
a = 10; // assignment
let b = 5 + 10; // expression

console.log(a, b); // 10 15
```

- Expressions are used everywhere where values are calculated or assigned.

---

### ❓ What happens if two functions have the same name in JavaScript?

- If two functions have the same name, the latest declaration overrides the previous one due to hoisting behavior.

```js
function greet() {
  console.log("Hello Nick");
}
function greet() {
  console.log("Hello John");
}

greet(); // Hello John
```

---

### ❓ If a function and a variable have the same name, which one has priority in JavaScript?

- Function declarations have higher priority than variables (var) during hoisting, so the function will override the variable.
- Even though function declarations are hoisted first, the var assignment happens later at runtime and overwrites the function, so typeof test becomes "number".

```js
var test = 10;
function test() {
  console.log("Hello");
}
console.log(typeof test); // number
```

```js
// Hoisting phase
function test() {}
var test;
```

- Steps
  - Function is hoisted with full definition (function has priority initially)
  - var test is hoisted as undefined
  - test gets overwritten by 10 (Final value becomes number)

---

### ❓ Execution Context in JavaScript?

- Execution Context is the environment where JavaScript code runs, including variable storage, function execution, and scope management during program execution.
  - Global Execution Context (GEC)
  - Function Execution Context (FEC)
  - Eval Execution Context (rarely used)

```js
// 1. Memory creation phase
a = undefined
test = function

// 2. Execution phase
a = 10
test() runs → new execution context created
```

---

### ❓ difference between Function Declaration and Function Expression?

- Function Declaration is hoisted completely and can be called before definition, while Function Expression is assigned to a variable and behaves like a normal variable, so it is not usable before initialization.
  - Function Declaration
    - Utility helpers
    - Math functions
    - API service functions
  - Function Expression
    - Event handlers
    - Callbacks (map, filter)
    - Conditional assignment

```js
// Declaration → utility functions
function calculateTotal() {
  return 100;
}

// Expression → event handlers
const handleClick = function () {
  console.log("Clicked");
};
```

---

### ❓ Tree Shaking in JavaScript?

- Tree shaking is a build optimization technique that removes unused code (dead code) from the final bundle, resulting in a smaller and faster application.
  - Removing unused helper functions
  - Reducing React app bundle size
  - Used by tools like Webpack, Vite, Rollup

```js
// utils.js
export function add() {}
export function multiply() {}

import { add } from "./utils"; // Only add function is kept in final bundle
```

---

### ❓ CORS in simple terms?

- CORS is a browser security mechanism that controls whether a frontend application can access resources from a different domain, and it prevents unauthorized cross-origin requests.
  - Frontend (React) calling backend APIs
  - Third-party API integrations
  - Payment gateways (Stripe, Razorpay)
  - Prevents unauthorized cross-site data access

```js
fetch("https://api.example.com/data");
// If your frontend is on: https://myapp.com
// and API is on: https://api.example.com

// Output: Blocked by CORS policy OR Data received successfully
```

- CORS is not only for APIs. It is a browser security rule for all cross-origin HTTP requests, including APIs, fonts, images, scripts, and any resource loaded from another domain.

```jsx
fetch("https://api.site.com/data")
<img src="https://cdn.site.com/image.jpg" />
<script src="https://cdn.site.com/lib.js"></script>
```

---

### ❓ What causes UI jank?

- UI jank happens when the main thread is blocked by heavy computations or large DOM updates, causing the browser to drop frames and resulting in a laggy or unresponsive user interface.
  - Scroll / click becomes laggy or frozen
- Real-life Causes:
  - Heavy JavaScript execution on main thread
  - Large DOM updates at once
  - Expensive re-renders in React
  - Synchronous API/data processing
  - Unoptimized loops or calculations

```js
for (let i = 0; i < 1e8; i++) {
  // heavy loop blocking UI
}
// 1e8 = 1 × 10⁸ (100,000,000).
// UI freezes during execution
```

---

### ❓ What is ECMAScript?

- ECMAScript is the standard specification that defines how JavaScript should work. JavaScript is an implementation of ECMAScript.
  - ECMAScript = Rules book
  - JavaScript = Language built using those rules

```js
// ES5 → old JavaScript (var, functions)
// ES6 (ES2015) → modern JS (let, const, arrow functions, classes)
// ES7+ → async/await, optional chaining, etc.
```

---

### ❓ structuredClone() a function or a method?

- structuredClone() is a built-in global function in JavaScript used to create a deep copy of an object.

```js
const user = {
  name: "Nick",
  address: {
    city: "Nadiad",
  },
};
const copy = structuredClone(user);
console.log(copy);
// Output:
// {
//   name: "Nick",
//   address: {
//     city: "Nadiad"
//   }
// }
```

---

### ❓ How do you identify a built-in function vs a built-in method in JavaScript?

- Built-in functions are called directly from the global scope, such as parseInt() and structuredClone(), while built-in methods belong to built-in objects like Array, String, Math, or JSON and are called using dot notation, such as array.map() or Math.max().
  - Built-in Functions are Called directly without an object.
  - Built-in Methods are Called through an object using (.)

```js
// Built-in Functions
parseInt("10");
parseFloat("10.5");
isNaN("abc");
structuredClone(obj);

// Built-in Methods
Math.max(10, 20);
arr.map((x) => x * 2);
str.toUpperCase();
date.getFullYear();
```

---

### ❓ Explain Reflow vs Repaint vs Compositing.

- Reflow (Layout): Browser recalculates element sizes and positions.
  - Recalculate positions, Repaint pixels, Composite layers
- Repaint: Browser redraws element appearance without changing layout.
  - Repaint pixels, Composite layers
- Compositing: Browser combines layers and displays them on screen, often using the GPU. (GPU-Friendly)
  - Reuses existing layer, Moves/fades/scales it

```jsx
// Reflow (Most Expensive)
element.style.width = "200px";
element.style.height = "100px";
element.style.display = "none";

// Repaint (Medium Cost)
element.style.backgroundColor = "red";
element.style.color = "white";

// Compositing (Cheapest)
element.style.transform = "translateX(100px)";
element.style.opacity = "0.5";
```

- Compositing is smoother because the browser can move or blend existing layers directly (often using the GPU) without recalculating layout or repainting pixels.

---

### ❓ Explain Debounce and Throttle with examples.

- Debounce: Executes a function only after the user stops triggering an event for a specified time.
  - Search boxes, Auto-save forms, Username availability checks
  - Only the final value triggers the API call.
  - User stops typing > API call
- Throttle: Executes a function at most once within a specified time interval, no matter how many times the event fires.
  - Scroll events, Window resize, Mouse movement tracking
  - Runs at most once per second.
  - Continuous events > Limited execution rate

```js
// >>>>> Debounce
function debounce(fn, delay) {
  let timer;
  return function (...args) {
    clearTimeout(timer);
    timer = setTimeout(() => {
      fn(...args);
    }, delay);
  };
}
const search = debounce((value) => {
  console.log("API Call:", value);
}, 500);

// >>>>> Throttle
function throttle(fn, delay) {
  let waiting = false;
  return function (...args) {
    if (waiting) return;
    fn(...args);
    waiting = true;
    setTimeout(() => {
      waiting = false;
    }, delay);
  };
}
const handleScroll = throttle(() => {
  console.log("Scroll Event");
}, 1000);
```

```text
// Debounce
T
Te
Tes
Test
(API waits)
API Call: Test

// Throttle
Scroll Event
(wait 1 second)
Scroll Event
(wait 1 second)
Scroll Event
```

---

### ❓ How does browser rendering work internally?

- The browser renders a webpage by parsing HTML into a DOM tree and CSS into a CSSOM tree, combining them into a render tree, calculating layout, painting pixels, and finally compositing layers onto the screen. This pipeline ensures efficient rendering and updates of web pages.
  - DOM (Document Object Model)
  - CSSOM (CSS Object Model)

```text
HTML
 ↓
DOM Tree
 ↓
CSSOM Tree
 ↓
Render Tree
 ↓
Layout (Reflow)
 ↓
Paint (Repaint)
 ↓
Composite
 ↓
Screen
```

1. Parse HTML → DOM Tree
   - Browser creates: structure
2. Parse CSS → CSSOM Tree
   - Browser creates CSS rules tree.
3. Build Render Tree
   - Browser combines: (DOM + CSSOM) to create: Render Tree
   - Only visible elements are included. (display: none;) Not added to Render Tree.
4. Layout (Reflow)
   - Browser calculates: Width, Height, Position, Spacing
5. Paint (Repaint)
   - Browser draws: Text, Colors, Borders, Shadows, Images
6. Composite
   - Browser combines layers and sends them to the GPU. (transform, opacity)
   - Often handled without repainting.

---

### ❓ difference between localStorage and sessionStorage?

- Both localStorage and sessionStorage store data in the browser as key-value pairs, but they differ in how long the data persists.
  - **localStorage** persists data until it is explicitly removed and is shared across tabs of the same origin.
    - Until manually removed
    - All tabs of same origin
    - Survives Browser Restart
  - **sessionStorage** stores data only for the current browser tab and is cleared when that tab is closed.
    - Until tab/browser is closed
    - Current tab only
    - No Browser Restart

```js
// localStorage
localStorage.setItem("datkTheme", true);
console.log(localStorage.getItem("Dark"));

// sessionStorage
sessionStorage.setItem("username", "Nick");
console.log(sessionStorage.getItem("username"));
```

---

### ❓ Explain authentication vs authorization.

- Authentication verifies a user's identity, such as logging in with a username and password, while authorization determines what resources or actions that authenticated user is allowed to access based on roles or permissions.

- Authentication verifies who you are.
  - Enter Username + Password
- Authorization determines what you can access.
  - Access permissions checked
    - Can Rao view account details?
    - Can Rao transfer money?
    - Can Rao access admin panel?

---

### ❓ Access Token vs Refresh Token?

- Access Token is used to access protected APIs.
  - Access APIs
  - Short-lived (minutes/hours)
- Refresh Token is used to obtain a new access token when the current one expires.
  - Generate new Access Token
  - Long-lived (days/weeks/months)

---

### ❓ How do Refresh Tokens work internally?

- A refresh token is a long-lived token used to obtain a new access token when the current access token expires, allowing users to stay logged in without entering credentials again.
- After login, the server issues a short-lived access token and a long-lived refresh token. When the access token expires, the client sends the refresh token to the server, which validates it and issues a new access token, allowing the user to continue using the application without logging in again.

```text
Login (Email + Password)
↓
Server issues:
- Access Token (short expiry)
- Refresh Token (long expiry)
↓
User accesses APIs
↓
Access Token expires
↓
Client sends Refresh Token
↓
Server validates Refresh Token
↓
New Access Token issued
↓
User continues without re-login
```

```text
- Login > Server returns: JSON
{
  "accessToken": "abc123",
  "refreshToken": "xyz789"
}

- API Call
GET /profile
Authorization: Bearer abc123 (Works until access token expires.)

- After Expiry
GET /profile
Authorization: Bearer abc123 (Response: 401 Unauthorized)

- Refresh Flow
POST /refresh-token
{
  "refreshToken": "xyz789"
}

- Server validates refresh token and returns:
{
  "accessToken": "newAccess123"
}

- Retry Original Request
GET /profile
Authorization: Bearer newAccess123
```

- If an access token is stolen: Attacker can use it until expiry
- So we use: Short-lived Access Token + Long-lived Refresh Token
- This reduces risk while keeping users logged in.

```js
try {
  await api.get("/profile");
} catch (error) {
  if (error.status === 401) {
    const { accessToken } = await api.post("/refresh-token");
    localStorage.setItem("accessToken", accessToken);
    return api.get("/profile");
  }
}
```

---

### ❓ How do you securely store tokens in frontend applications?

- Access and refresh tokens should be stored in a way that minimizes the risk of theft through XSS (Cross-Site Scripting) and other attacks.
- Refresh Token
  - Store in: HttpOnly + Secure + SameSite Cookie ✅ Best
  - Cannot be accessed by JavaScript
  - Better protection against XSS
- Access Token
  - Common approaches: Memory (React state, Context, Redux, Zustand) ✅ Good
  - HttpOnly Cookie
- Less Secure
  - localStorage ❌ Least Secure
- sessionStorage ⚠️ Moderate

---

### ❓ What is the delete operator in JavaScript?

- The delete operator removes a property from an object or an element from an array.
- delete does not reindex arrays. The empty slot is skipped.

```js
// Comment
const user = {
  name: "Rao",
  age: 30,
};

delete user.age;

console.log(user);
```

---

### ❓ What are Browser APIs?

- Browser APIs are built-in features provided by the browser that allow JavaScript to interact with the browser, web page, user device, and external resources.
  - JavaScript provides the language, while the browser provides APIs.
  - API's
    - DOM API -> Manipulate HTML elements
    - BOM API -> Interact with browser window
    - Fetch API -> Make HTTP requests
    - Local Storage API -> Store data in browser
    - Session Storage API -> Store session data
    - Geolocation API -> Get user location
    - History API -> Navigate browser history
    - WebSocket API -> Real-time communication
    - Notification API -> Show browser notifications
    - Clipboard API -> Read/write clipboard

```js
// DOM API
document.querySelector(".card");

// Fetch API
fetch("/users")
  .then((res) => res.json())
  .then((data) => console.log(data));

// Local Storage API
localStorage.setItem("theme", "dark");

// Geolocation API
navigator.geolocation.getCurrentPosition((position) => {
  console.log(position.coords.latitude);
});

// Timer API
setTimeout(() => {}, 1000);
setInterval(() => {}, 1000);

// Clipboard API
navigator.clipboard.writeText("SAVE20");

// WebSocket API
WebSocket("wss://example.com/socket");

// History API
history.pushState({}, "", "/profile");
```

---

### ❓ difference between setTimeout() and setInterval()?

- setTimeout() executes a function once after a specified delay. (API delay, notifications)
- setInterval() executes a function repeatedly at a specified interval. (Clock, polling, timers, scroll)

```js
// Comment
```

---

### ❓ Explain browser caching strategies with examples.

- Browser caching stores resources (JS, CSS, images, API responses) locally so the browser can reuse them instead of downloading them again.
- Browser caching improves performance by storing previously fetched resources. Common strategies include Cache-Control, ETag, Last-Modified, and cache busting. These reduce network requests and speed up page loads.
- Caching rules are usually defined by the server through HTTP response headers. The browser reads these headers and decides how long to store files.

```http
Static Assets: Cache-Control: public, max-age=31536000, immutable (JS/CSS served from cache)
HTML: Cache-Control: no-cache (HTML always checked for updates)
```

- Normal HTML/CSS/JS Project
  - Apache (.htaccess)
  - Nginx
- React Application (React itself does not control caching.)
  - Your web server (Nginx, Apache, CDN, Vercel, Netlify, AWS CloudFront) sends cache headers.
  - Vercel (vercel.json)
  - Netlify (\_headers)
  - AWS CloudFront (Cache policies)

---

### ❓ difference between a Node and an Element in the DOM?

- Every Element is a Node, but not every Node is an Element. The DOM contains different node types such as Element nodes, Text nodes, Comment nodes, and Document nodes.
  - A Node is any object in the DOM tree.
  - An Element is a specific type of node that represents an HTML tag.

```js
<div>Hello</div>;
// <div>  → Element + Node
// Hello  → Text Node only

const div = document.querySelector("div");
console.log(div.nodeType); // 1 (1 means Element Node.)
console.log(div instanceof Element); // true

const textNode = document.querySelector("div").firstChild;
console.log(textNode.nodeType); // 3 (3 means Text Node.)
console.log(textNode instanceof Element); // false
```

```js
// >>>>> Access Only HTML Elements
document.querySelectorAll("button");
// Button Elements

// >>>>> Access All Nodes
document.body.childNodes;
// Element Nodes / Text Nodes (spaces/new lines) / Comment Nodes
```

- Node = Generic DOM object
- Element = HTML tag in the DOM

| Node Type | nodeType | Example            |
| --------- | -------- | ------------------ |
| Element   | 1        | `<div>`            |
| Text      | 3        | `Hello`            |
| Comment   | 8        | `<!-- comment -->` |
| Document  | 9        | `document`         |

---

### ❓ What is Infinite Currying in JavaScript?

- Infinite currying is a technique where a function can be called repeatedly with one argument at a time and keeps returning another function until a final value is requested.
- Currying transforms a function with multiple arguments into a sequence of functions. Infinite currying extends this idea by allowing unlimited chained calls until a final terminating call returns the result.

```js
function sum(a) {
  return function (b) {
    if (b === undefined) {
      return a;
    }
    return sum(a + b);
  };
}
console.log(sum(1)(2)(3)(4)()); // 10
```

```jsx
// Each button gets its own configured handler.
products.map((product) => (
  <button key={product.id} onClick={handleDelete(product.id)}>
    Delete
  </button>
));
```

---

### ❓ Explain the JavaScript Event Loop step by step.

- JavaScript is single-threaded, so it can execute only one task at a time. The Event Loop manages asynchronous operations by moving completed tasks from queues to the Call Stack when it's empty.
- The Event Loop continuously checks whether the Call Stack is empty. If it is, it executes pending tasks from the Microtask Queue first (Promises), then from the Callback/Macrotask Queue (setTimeout, setInterval, events).

```js
console.log("1");
setTimeout(() => {
  console.log("2");
}, 0);
Promise.resolve().then(() => {
  console.log("3");
});
console.log("4");

// Output: 1 4 3 2
```

- Queues Priority

| Priority | Queue                    | Examples                            |
| -------- | ------------------------ | ----------------------------------- |
| 1        | Call Stack               | Normal JS                           |
| 2        | Microtask Queue          | Promise, queueMicrotask             |
| 3        | Callback/Macrotask Queue | setTimeout, setInterval, DOM Events |

---

### ❓ Difference between Synchronous and Asynchronous JavaScript?

- Synchronous code executes one task at a time, in order. The next task waits until the current task finishes.
- Asynchronous code allows long-running tasks (API calls, timers, file operations) to run in the background without blocking execution.

```js
// Synchronous
console.log("Start");
console.log("Processing");
console.log("End");

// Asynchronous
console.log("Start");
setTimeout(() => {
  console.log("Processing");
}, 1000);
console.log("End");

// API Request
console.log("Loading Users");
fetch("/api/users").then(() => console.log("Users Loaded"));
console.log("UI Ready");
```

- Asynchronous API's
  - setTimeout()
  - fetch()
  - Promise
  - async/await
  - WebSocket

---

### ❓ How do you handle API retries and failures gracefully?

- I handle API failures using try/catch, display user-friendly error messages, implement retry logic for temporary failures, add loading states, and use fallback UI. For React apps, libraries like React Query can manage retries automatically.

```js
// Basic Error Handling
try {
  const response = await fetch("/api/users");
  if (!response.ok) {
    throw new Error("Failed");
  }
  const data = await response.json();
} catch (error) {
  setError("Unable to load users");
}

// Retry 3 Times
async function fetchWithRetry(url, retries = 3) {
  try {
    const response = await fetch(url);
    if (!response.ok) {
      throw new Error();
    }
    return response.json();
  } catch (error) {
    if (retries > 0) {
      return fetchWithRetry(url, retries - 1);
    }
    throw error;
  }
}

// React Loading + Error State
const [loading, setLoading] = useState(false);
const [error, setError] = useState("");
setLoading(true);
try {
  await fetchData();
} catch {
  setError("Something went wrong");
} finally {
  setLoading(false);
}
```

- Common Failure Handling

| Scenario           | Solution        |
| ------------------ | --------------- |
| Network Error      | Retry           |
| 500 Server Error   | Retry           |
| 404 Not Found      | Show Error      |
| Unauthorized (401) | Redirect Login  |
| Slow API           | Loading Spinner |
| Permanent Failure  | Fallback UI     |

---

### ❓ Explain JWT authentication end-to-end with refresh token flow.

- JWT (JSON Web Token) is a token-based authentication mechanism where the server issues an Access Token and a Refresh Token after login.
  - Access Token → Short-lived, used for API requests. (Short (15m-1h))
  - Refresh Token → Long-lived, used to obtain a new Access Token. (Long (Days/Weeks))
- After successful login, the server issues an access token and refresh token. The frontend sends the access token with API requests. When it expires, the frontend uses the refresh token to get a new access token without forcing the user to log in again.

```json
{
  "accessToken": "jwt-access-token",
  "refreshToken": "refresh-token"
}
```

```js
// Add Access Token
axios.get("/profile", {
  headers: {
    Authorization: `Bearer ${token}`,
  },
});

// Refresh Interceptor
axios.interceptors.response.use(
  (response) => response,
  async (error) => {
    if (error.response.status === 401) {
      const newToken = await refreshToken();
      error.config.headers.Authorization = `Bearer ${newToken}`;
      return axios(error.config);
    }
    return Promise.reject(error);
  },
);
```

---

### ❓ How do Service Workers improve frontend applications?

- A Service Worker is a JavaScript file that runs in the background, separate from the web page, and can intercept network requests.
- Service Workers improve performance, reliability, and user experience by enabling caching, offline support, background synchronization, and push notifications.

```js
// Register Service Worker
if ("serviceWorker" in navigator) {
  navigator.serviceWorker.register("/sw.js");
}

// Cache Static Assets
self.addEventListener("install", (event) => {
  event.waitUntil(
    caches
      .open("v1")
      .then((cache) => cache.addAll(["/", "/app.js", "/styles.css"])),
  );
});
```

---

### ❓ What happens internally when a user types a URL in the browser?

- When a URL is entered, the browser performs several steps: finding the server, requesting the page, downloading resources, and rendering the UI.
- The browser resolves the domain via DNS, establishes a connection, sends an HTTP request, receives the response, parses HTML/CSS/JS, builds the DOM and CSSOM, creates the render tree, paints the page, and executes JavaScript.

1. URL Parsing > https://example.com/products
   - Protocol → HTTPS
   - Domain → example.com
   - Path → /products
2. DNS Lookup
   - example.com > 93.184.216.34
3. TCP Connection
   - Browser > Server
4. TLS Handshake (HTTPS)
   - Browser > Verify SSL Certificate > Secure Connection
5. HTTP Request
   - GET /products HTTP/1.1
   - Host: example.com
6. Server Response
   - 200 OK
   - Content-Type: text/html
7. HTML Parsing
   - Create DOM Tree
8. CSS Parsing
   - Create CSSOM
9. Render Tree Creation
   - DOM + CSSOM
10. Layout (Reflow)
    - Position, Width, Height
11. Paint
    - Pixels Drawn On Screen
12. JavaScript Execution
    - document.querySelector("button");

---

### ❓ Explain frontend security vulnerabilities developers should know.

- Frontend security focuses on protecting users, data, and applications from common attacks.
- The most important frontend security vulnerabilities are XSS, CSRF, insecure token storage, clickjacking, sensitive data exposure, and dependency vulnerabilities. Developers should validate input, escape output, use HTTPS, and follow secure authentication practices.

---

### ❓ How do you monitor frontend applications in production?

- Frontend monitoring helps track errors, performance issues, crashes, and user experience in real-world usage.
- monitor frontend applications using error tracking, performance monitoring, logging, analytics, and Real User Monitoring (RUM). Tools like Sentry, Datadog, and Google Analytics help identify issues before they affect many users.

```js
// Error Tracking
try {
  await fetchData();
} catch (error) {
  Sentry.captureException(error);
}

// Global Error Handler
window.addEventListener("error", (event) => {
  console.error(event.error);
});
```

---

### ❓ How would you optimize an eCommerce product listing page?

- Optimizing a product listing page focuses on improving load time, rendering performance, API efficiency, and user experience.
  - Lazy Load Images
  - Memoize Product Card
  - Search Debouncing
  - Infinite Scrolling

```js
// Comment
```

---

### ❓

```js
// Comment
```

---

### ❓

```js
// Comment
```

---

### ❓

```js
// Comment
```

---

### ❓

```js
// Comment
```

---
