# 👉 Core JavaScript Fundamentals

A programming language used to create interactive and dynamic web applications.

- **Single-Threaded** → JavaScript executes one task at a time on a single main thread.
- **Synchronous** → Code runs line by line, waiting for one task to finish before moving to the next.

---

## 📌 JavaScript Overview

| Item        | Details                              |
| ----------- | ------------------------------------ |
| Type        | High-level, Dynamic, Prototype-based |
| Execution   | Single-threaded, Event-driven        |
| Compilation | Interpreted + JIT Compiled           |
| Standard    | ECMAScript (ES)                      |
| Main Use    | Frontend, Backend, APIs              |

### Runtime Environments

| Environment  | Usage                |
| ------------ | -------------------- |
| Browser      | Frontend Development |
| Node.js      | Backend Development  |
| Electron     | Desktop Apps         |
| React Native | Mobile Apps          |

### JS Engine & Runtime ⚠️

| Item           | Details                               |
| -------------- | ------------------------------------- |
| JS Engine      | Converts JavaScript into machine code |
| Runtime        | Environment where JS executes         |
| Call Stack     | Handles function execution            |
| Web APIs       | Browser-provided async features       |
| Callback Queue | Stores async callbacks                |
| Event Loop     | Moves tasks to call stack             |

### ECMAScript Versions

| Version         | Key Features                                      |
| --------------- | ------------------------------------------------- |
| ES5             | Strict Mode, JSON                                 |
| ES6 (ES2015)    | `let`, `const`, arrow functions, classes, modules |
| ES7+            | Async/Await, optional chaining                    |
| ------------    | ------------------------------------------------- |
| ECMAScript (ES) | Official JavaScript standard                      |
| JavaScript      | Implementation of ECMAScript                      |

✅ Modern JavaScript = ES6+

### JS Engines

| Browser | Engine         |
| ------- | -------------- |
| Chrome  | V8             |
| Firefox | SpiderMonkey   |
| Safari  | JavaScriptCore |

### Modern Features

| Feature           | Example         |
| ----------------- | --------------- |
| Arrow Function    | `()=>{}`        |
| Async/Await       | `await fetch()` |
| Modules           | `import/export` |
| Optional Chaining | `obj?.name`     |

| Area          | Details                      |
| ------------- | ---------------------------- |
| Core Features | Dynamic Typing               |
|               | Async Support                |
|               | OOP + Functional Programming |
|               | DOM Manipulation             |
|               | Event Handling               |
| Common Uses   | SPA Development              |
|               | API Calls                    |
|               | Form Validation              |
|               | Realtime Apps                |
|               | Interactive UI               |

### Avoid

| Deprecated / Bad Practice |
| ------------------------- |
| `var`                     |
| `eval()`                  |
| `document.write()`        |
| Inline JS                 |

---

## 📌 Variables

Containers used to store data values in JavaScript.

| Keyword | Scope    | Reassign | Redeclare | Hoisted |
| ------- | -------- | -------- | --------- | ------- |
| `var`   | Function | ✅       | ✅        | ✅      |
| `let`   | Block    | ✅       | ❌        | ✅      |
| `const` | Block    | ❌       | ❌        | ✅      |

| Type    | Syntax Example      |
| ------- | ------------------- |
| `var`   | `var name = "John"` |
| `let`   | `let age = 25`      |
| `const` | `const PI = 3.14`   |

### Notes

| Keyword | Details                       |
| ------- | ----------------------------- |
| `var`   | Old style, avoid in modern JS |
| `let`   | Use when value changes        |
| `const` | Preferred by default          |

### Naming Rules

| Rule                               | Example              |
| ---------------------------------- | -------------------- |
| Case Sensitive                     | `user` ≠ `User`      |
| Cannot Start with Number           | ❌ `1name`           |
| Only `_` and `$` Allowed Specially | ✅ `_name`, `$price` |
| No Spaces                          | ❌ `user name`       |
| Hyphen Not Allowed                 | ❌ `user-name`       |
| Reserved Keywords Not Allowed      | ❌ `let class = ""`  |

### Naming Conventions

| Item                  | Convention          | Example                  |
| --------------------- | ------------------- | ------------------------ |
| Variables & Functions | camelCase           | `firstName`, `getUser()` |
| Classes               | PascalCase          | `UserProfile`            |
| Constants             | UPPER_CASE          | `API_URL`                |
| Boolean Variables     | `is/has/can` prefix | `isLoggedIn`             |
| Private Fields        | `_` / `#` prefix    | `_id`, `#name`           |

| ✅ Recommended        | ❌ Avoid            |
| --------------------- | ------------------- |
| `const` by default    | Using `var`         |
| Block scope variables | Global variables    |
| Meaningful names      | Short unclear names |

---

## 📌 Data Types

Define the type of value a variable can store in JavaScript.

| Type Category       | Meaning                           | Examples                      |
| ------------------- | --------------------------------- | ----------------------------- |
| Primitive Types     | Store single simple values        | `String`, `Number`, `Boolean` |
| Non-Primitive Types | Store collections or complex data | `Object`, `Array`, `Function` |

| Primitive Types | Details                            | Example     | Real-Life Usage                                    |
| --------------- | ---------------------------------- | ----------- | -------------------------------------------------- |
| String          | Text values                        | `"Hello"`   | User names, messages, product titles               |
| Number          | Integers & decimals                | `100`       | Price, age, quantity, marks                        |
| Boolean         | True/false values                  | `true`      | Login status, dark mode toggle                     |
| Undefined       | Variable declared but not assigned | `undefined` | Data not received yet from API                     |
| Null            | Intentional empty value            | `null`      | Empty user profile image (typeof null // "object") |
| Symbol          | Unique identifier                  | `Symbol()`  | Unique object keys in libraries                    |
| BigInt          | Large integers                     | `123n`      | Banking systems, large calculations                |

| Reference Types | Details                | Example            |
| --------------- | ---------------------- | ------------------ |
| Object          | Key-value collections  | `{ name: "John" }` |
| Array           | Ordered collections    | `[1, 2, 3]`        |
| Function        | Reusable block of code | `function(){}`     |

### Type Checking / Special Cases

| Method / Expression   | Details                       | Result / Example    |
| --------------------- | ----------------------------- | ------------------- |
| `typeof`              | Returns data type             | `typeof "Hi"`       |
| `Array.isArray()`     | Checks if value is array      | `Array.isArray([])` |
| --------------------- | ----------------------------- | ------------------- |
| `typeof null`         | Historical JavaScript bug     | `"object"`          |
| `typeof []`           | Arrays are objects internally | `"object"`          |
| `typeof function(){}` | Functions have special type   | `"function"`        |

| Language   | Type System    | Meaning                             | Example                                 |
| ---------- | -------------- | ----------------------------------- | --------------------------------------- |
| JavaScript | Dynamic Typing | Variable type can change at runtime | `let x = 10; x = "Hello";`              |
| TypeScript | Static Typing  | Variable type stays fixed           | `let x: number = 10; // x = "Hello" ❌` |

---

## 📌 Operators

Symbols used to perform operations on values and variables.

- **Operands** → Values used in an operation (`10`, `5`)
- **Operator** → Symbol that performs operation (`+`)
- **Output** → Final result (`15`)

| Type                | Operators                     | Description            | Example                   | Output |
| ------------------- | ----------------------------- | ---------------------- | ------------------------- | ------ |
| Arithmetic          | +                             | Addition               | 5 + 2                     | 7      |
|                     | -                             | Subtraction            | 5 - 2                     | 3      |
|                     | \*                            | Multiplication         | 5 \* 2                    | 10     |
|                     | /                             | Division               | 5 / 2                     | 2.5    |
|                     | %                             | Modulus (Remainder)    | 5 % 2                     | 1      |
|                     | \*\*                          | Exponentiation (Power) | 5 \*\* 2                  | 25     |
|                     | ++                            | Increment              | let x=5; x++              | 6      |
|                     | --                            | Decrement              | let x=5; x--              | 4      |
| Assignment          | `= += -= *= /= %= **=`        |                        | `x += 2`                  |
| Comparison          | `== === != !== > < >= <=`     |                        | `5 === "5"`               |
| Logical             | `&& \|\| !`                   |                        | `a && b`                  |
| Increment/Decrement | `++ --`                       |                        | `x++`                     |
| Ternary             | `? :`                         |                        | `age > 18 ? "Yes" : "No"` |
| Nullish Coalescing  | `??`                          |                        | `name ?? "Guest"`         |
| Optional Chaining   | `?.`                          |                        | `user?.name`              |
| Type                | `typeof delete instanceof in` |                        | `typeof 10`               |
| Bitwise             | `& \| ^ ~ << >> >>>`          |                        | `5 & 1`                   |
| String              | `+ +=`                        |                        | `"Hi" + " JS"`            |
| Comma               | `,`                           |                        | `x = (1,2)`               |
| Spread/Rest         | `...`                         |                        | `[...arr]`                |

### Equality Operators

| Operator | Purpose                     |
| -------- | --------------------------- |
| `==`     | Equal after type conversion |
| `===`    | Strict equal                |
| `!=`     | Not equal after conversion  |
| `!==`    | Strict not equal            |

### Logical Operators

| Operator | Purpose                |
| -------- | ---------------------- |
| `&&`     | Both conditions true   |
| `\|\|`   | Any one condition true |
| `!`      | Reverses boolean value |

### Comparison Operators

| Operator | Purpose               |
| -------- | --------------------- |
| `>`      | Greater than          |
| `<`      | Less than             |
| `>=`     | Greater than or equal |
| `<=`     | Less than or equal    |

- Prefer `===` over `==`
- Use `??` for null/undefined fallback
- Use `?.` to avoid undefined errors

### Special Operators

| Operator     | Purpose                | Example                |
| ------------ | ---------------------- | ---------------------- |
| `delete`     | Remove Object Property | `delete user.name`     |
| `typeof`     | Get Data Type          | `typeof "John"`        |
| `instanceof` | Check Instance Type    | `user instanceof User` |
| `in`         | Check Property Exists  | `"name" in user`       |
| `new`        | Create Object Instance | `new Date()`           |
| `void`       | Return Undefined       | `void 0`               |
| `?.`         | Optional Chaining      | `user?.address?.city`  |
| `??`         | Nullish Coalescing     | `name ?? "Guest"`      |
| `...`        | Spread / Rest          | `[...arr]`             |
| `!`          | Logical NOT            | `!isLoggedIn`          |

---

## 📌 Type Conversion

Converting a value from one data type to another data type.

| Type                | Details                         | Example        |
| ------------------- | ------------------------------- | -------------- |
| String → Number     | Converts string to number       | `Number("10")` |
| Number → String     | Converts number to string       | `String(100)`  |
| Value → Boolean     | Converts value to boolean       | `Boolean(1)`   |
| Implicit Conversion | Automatic type conversion by JS | `"5" + 1`      |
| Explicit Conversion | Manual conversion by developer  | `Number("5")`  |

### Common Conversions

| Expression     | Result  |
| -------------- | ------- |
| `"5" + 1`      | `"51"`  |
| `"5" - 1`      | `4`     |
| `true + 1`     | `2`     |
| `Boolean(0)`   | `false` |
| `Number(true)` | `1`     |

| Type Conversion | Example           | Result |
| --------------- | ----------------- | ------ |
| Automatic       | `"5" + 1`         | `"51"` |
| Automatic       | `"10" - 2`        | `8`    |
| Manual          | `Number("5") + 1` | `6`    |

### Falsy Values

| Value       | Meaning                 |
| ----------- | ----------------------- |
| `false`     | Boolean false value     |
| `0`         | Zero number             |
| `""`        | Empty string            |
| `null`      | Intentional empty value |
| `undefined` | Variable without value  |
| `NaN`       | Invalid number result   |

- Prefer explicit conversion for predictable results
- Use `===` to avoid unwanted coercion
- `+` with string performs concatenation

---

## 📌 Expressions & Statements

Expression = Code that produces a value  
Statement = Code that performs an action

| Type                  | Details                     | Example                    |
| --------------------- | --------------------------- | -------------------------- |
| Expression            | Produces a value            | `2 + 2`                    |
| Statement             | Performs an action          | `if (x > 5) {}`            |
| Declaration Statement | Declares variable/function  | `let age = 25`             |
| Assignment Expression | Assigns value               | `x = 10`                   |
| Function Expression   | Function stored in variable | `const sum = function(){}` |

### Common Statements

| Statement | Purpose                |
| --------- | ---------------------- |
| `if`      | Conditional execution  |
| `for`     | Loop execution         |
| `switch`  | Multiple conditions    |
| `return`  | Returns function value |

- Expressions return values
- Statements control program flow
- Some code can be both expression and statement

---

## 📌 Strict Mode ⚠️

Strict Mode enables safer and cleaner JavaScript rules.

| Item              | Details                            | Example             |
| ----------------- | ---------------------------------- | ------------------- |
| Syntax            | Enable strict mode                 | `"use strict";`     |
| Scope             | Works for file or function         | `"use strict";`     |
| Implicit Globals  | Prevents undeclared variables      | `x = 10 // ❌`      |
| Silent Errors     | Converts hidden issues into errors | Duplicate params ❌ |
| Reserved Keywords | Restricts unsafe syntax            | `let interface` ❌  |

```js
"use strict";

let name = "John";
```

- Helps catch common mistakes
- Recommended in older scripts
- ES Modules use strict mode automatically

---

## 📌 Conditionals

Conditionals execute code based on conditions.

| Statement        | Purpose                          | Syntax                      |
| ---------------- | -------------------------------- | --------------------------- |
| `if`             | Executes when condition is true  | `if (condition) {}`         |
| `else`           | Executes when condition is false | `else {}`                   |
| `else if`        | Checks multiple conditions       | `else if (condition) {}`    |
| `switch`         | Handles multiple cases           | `switch(value) { case x: }` |
| Ternary Operator | Short conditional syntax         | `condition ? true : false`  |

```js
if (age > 18) {
  console.log("Adult");
} else {
  console.log("Minor");
}
```

```js
if (score > 90) {
  grade = "A";
} else if (score > 70) {
  grade = "B";
} else {
  grade = "C";
}
```

```js
switch (day) {
  case "Mon":
    console.log("Weekday");
    break;

  default:
    console.log("Other");
}
```

```js
const result = age > 18 ? "Adult" : "Minor";
```

- Use ternary for short conditions
- Use `switch` for multiple fixed cases

---

## 📌 Loops

Loops execute code repeatedly until a condition is met.

| Loop         | Purpose                      | Syntax                       |
| ------------ | ---------------------------- | ---------------------------- |
| `for`        | Fixed iterations             | `for(init; condition; step)` |
| `while`      | Runs while condition is true | `while(condition)`           |
| `do...while` | Executes at least once       | `do {} while(condition)`     |
| `for...of`   | Iterates iterable values     | `for (item of arr)`          |
| `for...in`   | Iterates object keys         | `for (key in obj)`           |

```js
for (let i = 0; i < 5; i++) {
  console.log(i);
}
```

```js
while (count < 5) {
  count++;
}
```

```js
do {
  count++;
} while (count < 5);
```

```js
for (const item of arr) {
  console.log(item);
}
```

```js
for (const key in user) {
  console.log(key);
}
```

- Use `for...of` for arrays/iterables
- Use `for...in` for object keys
- Avoid infi

---

## 📌 Functions

Functions are reusable blocks of code.

| Type                 | Purpose                     | Syntax                      |
| -------------------- | --------------------------- | --------------------------- |
| Function Declaration | Standard named function     | `function test(){}`         |
| Function Expression  | Function stored in variable | `const test = function(){}` |
| Arrow Function       | Short modern syntax         | `const test = () => {}`     |
| Parameters           | Input values                | `function(a, b)`            |
| Return               | Returns value from function | `return value`              |

```js
function sum(a, b) {
  return a + b;
}
```

```js
const sum = function (a, b) {
  return a + b;
};
```

```js
const sum = (a, b) => a + b;
```

```js
function greet(name = "Guest") {
  return name;
}
```

### Function Types

| Type                  | Details                      |
| --------------------- | ---------------------------- |
| Callback Function     | Passed into another function |
| Higher Order Function | Accepts/returns function     |
| IIFE                  | Executes immediately         |
| Recursive Function    | Calls itself                 |

- Prefer arrow functions for short callbacks
- Use function declarations for reusable logic
- Keep functions small and focused

---

## 📌 Arrow Functions

Arrow functions provide shorter function syntax.

| Feature             | Details                  | Syntax                   |
| ------------------- | ------------------------ | ------------------------ |
| Basic Syntax        | Short function syntax    | `const fn = () => {}`    |
| Single Parameter    | Parentheses optional     | `x => x * 2`             |
| Implicit Return     | Returns without `return` | `x => x + 1`             |
| Multiple Parameters | Parentheses required     | `(a, b) => a + b`        |
| Object Return       | Wrap object in `()`      | `() => ({ name: "JS" })` |

```js
// Basic Syntax
const greet = () => {
  console.log("Hello");
};
```

```js
// Single Parameter
const square = (x) => x * 2;
```

```js
// Multiple Parameters
const sum = (a, b) => a + b;
```

```js
// Returning Object
const getUser = () => ({
  name: "John",
});
```

| Feature     | Arrow Function             | Regular Function             |
| ----------- | -------------------------- | ---------------------------- |
| `this`      | Uses parent `this`         | Creates own `this`           |
| Constructor | ❌ Cannot use `new`        | ✅ Can use `new`             |
| Best Use    | Callbacks, short functions | Object methods, constructors |

- Prefer for short callbacks
- Avoid as object methods when `this` needed
- Great for array methods

---

## 📌 Constructor

A constructor is a function used to create objects.

| Type                 | Details                    | Example                 |
| -------------------- | -------------------------- | ----------------------- |
| Constructor Function | Creates object using `new` | `new User()`            |
| `this`               | Refers to new object       | `this.name = name`      |
| `new` Keyword        | Creates object instance    | `const u1 = new User()` |

```js
function User(name) {
  this.name = name;
}

const u1 = new User("John");
```

- Common before ES6 classes
- Regular functions can be constructors
- Arrow functions cannot be constructors

---

## 📌 Callbacks

A callback is a function passed into another function.

| Type              | Details            | Example        |
| ----------------- | ------------------ | -------------- |
| Callback Function | Passed as argument | `fn(callback)` |
| Synchronous       | Runs immediately   | `forEach()`    |
| Asynchronous      | Runs later         | `setTimeout()` |

### Common Usage

| Usage         | Methods / APIs                   |
| ------------- | -------------------------------- |
| Events        | `addEventListener()`             |
| API Handling  | `fetch().then()`                 |
| Timers        | `setTimeout()`                   |
| Array Methods | `map()`, `filter()`, `forEach()` |

```js
// Basic Callback
function greet(name, callback) {
  callback(name);
}

greet("John", function (name) {
  console.log(name);
});
```

```js
// Arrow Callback
greet("John", (name) => {
  console.log(name);
});
```

```js
// Timer Callback
setTimeout(() => {
  console.log("Done");
}, 1000);
```

```js
// Event Callback
button.addEventListener("click", () => {
  console.log("Clicked");
});
```

```js
// API Callback
fetch("/users")
  .then((res) => res.json())
  .then((data) => {
    console.log(data);
  });
```

```js
// Array Callback
nums.map((num) => num * 2);
```

- Common in async JavaScript
- Widely used in events, APIs, and array methods
- Excessive nesting creates callback hell

---

## 📌 Higher Order Functions (HOF)

A higher order function accepts or returns another function.

| Type             | Details                         | Example                    |
| ---------------- | ------------------------------- | -------------------------- |
| Accepts Function | Function passed as argument     | `map(callback)`            |
| Returns Function | Function returned from function | `fn()()`                   |
| Common Usage     | Array methods, utilities        | `filter()`, `setTimeout()` |

### Common HOF Methods

| Method      | Purpose                |
| ----------- | ---------------------- |
| `map()`     | Transform array        |
| `filter()`  | Filter values          |
| `reduce()`  | Reduce to single value |
| `forEach()` | Loop items             |
| `sort()`    | Sort values            |

```js
// Accepting Function
function greet(callback) {
  callback();
}

greet(() => {
  console.log("Hello");
});
```

```js
// Returning Function
function multiply(a) {
  return function (b) {
    return a * b;
  };
}

multiply(2)(3);
```

```js
// map()
const nums = [1, 2, 3];

const doubled = nums.map((num) => num * 2);
```

```js
// filter()
const activeUsers = users.filter((user) => user.active);
```

- Core concept in functional programming
- Widely used with array methods
- Makes code reusable and flexible

### Array Methods

| Method        | Purpose                | Example                      | Output         |
| ------------- | ---------------------- | ---------------------------- | -------------- |
| `push()`      | Add item at end        | `arr.push(3)`                | `[1,2,3]`      |
| `pop()`       | Remove last item       | `arr.pop()`                  | `[1,2]`        |
| `shift()`     | Remove first item      | `arr.shift()`                | `[2,3]`        |
| `unshift()`   | Add item at beginning  | `arr.unshift(1)`             | `[1,2,3]`      |
| `map()`       | Transform array        | `nums.map(n => n * 2)`       | `[2,4,6]`      |
| `filter()`    | Filter items           | `nums.filter(n => n > 2)`    | `[3,4]`        |
| `find()`      | First matching item    | `nums.find(n => n > 2)`      | `3`            |
| `findIndex()` | Find matching index    | `nums.findIndex(n => n > 2)` | `2`            |
| `includes()`  | Check value exists     | `arr.includes("JS")`         | `true`         |
| `indexOf()`   | Find value index       | `arr.indexOf("JS")`          | `0`            |
| `some()`      | Check any match        | `nums.some(n => n > 2)`      | `true`         |
| `every()`     | Check all match        | `nums.every(n => n > 0)`     | `true`         |
| `reduce()`    | Reduce to single value | `nums.reduce((a,b)=>a+b,0)`  | `6`            |
| `slice()`     | Copy part of array     | `arr.slice(1,3)`             | `[2,3]`        |
| `splice()`    | Add/remove items       | `arr.splice(1,1)`            | Removed item   |
| `concat()`    | Merge arrays           | `a.concat(b)`                | Merged array   |
| `join()`      | Convert to string      | `arr.join("-")`              | `"1-2-3"`      |
| `reverse()`   | Reverse array          | `arr.reverse()`              | Reversed array |
| `sort()`      | Sort array             | `arr.sort()`                 | Sorted array   |
| `flat()`      | Flatten nested arrays  | `[1,[2]].flat()`             | `[1,2]`        |
| `fill()`      | Fill array values      | `arr.fill(0)`                | `[0,0,0]`      |

| Type      | Definition              | Common Methods                                              |
| --------- | ----------------------- | ----------------------------------------------------------- |
| Mutable   | Changes original array  | `push()` `pop()` `splice()` `sort()` `reverse()`            |
| Immutable | Returns new array/value | `map()` `filter()` `find()` `reduce()` `slice()` `concat()` |

- splice

```js
array.splice(startIndex, deleteCount, item1, item2, ...)
```

---

## 📌 Closures

- A closure allows a function to access variables from its outer scope even after the outer function has finished executing.

| Feature            | Details                   | Example         |
| ------------------ | ------------------------- | --------------- |
| Outer Scope Access | Access parent variables   | Inner function  |
| Data Persistence   | Remembers outer variables | Counter example |
| Encapsulation      | Creates private data      | Private state   |

```js
// Remembering Variable
function greeting() {
  let name = "John";

  return function () {
    console.log(name);
  };
}

const sayHello = greeting();

sayHello(); // John
```

```js
// Counter Example
function counter() {
  let count = 0;

  return function () {
    count++;
    console.log(count);
  };
}

const add = counter();

add(); // 1
add(); // 2
add(); // 3
```

```js
// Private Variable
function bank() {
  let balance = 1000;

  return function () {
    console.log(balance);
  };
}

const checkBalance = bank();

checkBalance(); // 1000
```

| Common Uses        | Purpose           |
| ------------------ | ----------------- |
| Counters           | Preserve state    |
| Event Handlers     | Access outer data |
| Data Privacy       | Private variables |
| Function Factories | Dynamic functions |

- Closures preserve outer scope data
- Useful for private state management
- Common in callbacks and event handlers

---

## 📌 Recursion ⚠️

Recursion is a function calling itself until a condition is met.

---

| Part               | Details                | Example              |
| ------------------ | ---------------------- | -------------------- |
| Recursive Function | Function calls itself  | `fn()` inside `fn()` |
| Base Condition     | Stops recursion        | `if (n === 0)`       |
| Recursive Call     | Repeats function logic | `fn(n - 1)`          |

```js
// Countdown
function countDown(n) {
  if (n === 0) return;

  console.log(n);

  countDown(n - 1);
}

countDown(5);
```

```js
// Factorial
function factorial(n) {
  if (n === 1) return 1;

  return n * factorial(n - 1);
}

factorial(5); // 120
```

```js
// Sum of Numbers
function sum(n) {
  if (n === 1) return 1;

  return n + sum(n - 1);
}

sum(5); // 15
```

| Common Uses    | Purpose                 |
| -------------- | ----------------------- |
| Factorial      | Repeated multiplication |
| Tree Traversal | Nested structures       |
| Countdown      | Repeated operations     |

- Base condition is required
- Missing base condition causes infinite recursion
- Useful for nested or repeated problems

---

## 📌 Scope

Scope defines where variables can be accessed.

| Type           | Details                           | Common Keywords       | Accessible      |
| -------------- | --------------------------------- | --------------------- | --------------- |
| Global Scope   | Declared outside functions/blocks | `var`, `let`, `const` | Entire file/app |
| Function Scope | Accessible only inside function   | `var`                 | Inside function |
| Block Scope    | Accessible only inside `{}` block | `let`, `const`        | Inside block    |
| Lexical Scope  | Inner scope accesses outer scope  | Nested functions      | Parent scope    |

### `var` Scope Behavior

| Location          | Scope                |
| ----------------- | -------------------- |
| Outside Function  | Global Scope         |
| Inside Function   | Function Scope       |
| Inside Block `{}` | Still Function Scope |

```js
// Global Scope
var app = "JavaScript";

function test() {
  console.log(app);
}
```

```js
// Function Scope
function user() {
  var name = "John";

  console.log(name);
}
```

```js
// var ignores block scope
if (true) {
  var age = 25;
}

console.log(age); // 25 ✅
```

```js
// let and const are block scoped
if (true) {
  let city = "NY";
}

console.log(city); // ❌ Error
```

```js
// Lexical Scope
function outer() {
  let message = "Hello";

  function inner() {
    console.log(message);
  }

  inner();
}
```

- Inner scope can access outer scope
- Outer scope cannot access inner scope
- Prefer `let` and `const` over `var`

---

## 📌 Hoisting

Hoisting moves declarations to the top of their scope during execution.

TDZ (Temporal Dead Zone) = TDZ is the time between variable hoisting and initialization where the variable cannot be accessed.

| Type                 | Behavior                                       | Easy Example                   |
| -------------------- | ---------------------------------------------- | ------------------------------ |
| `var`                | Accessible before declaration with `undefined` | `console.log(a)` → `undefined` |
| `let`                | Cannot access before declaration (TDZ)         | `console.log(b)` → ❌ Error    |
| `const`              | Cannot access before declaration (TDZ)         | `console.log(c)` → ❌ Error    |
| Function Declaration | Can call before declaration                    | `greet()` → ✅ Works           |
| Function Expression  | Cannot call before declaration                 | `sayHi()` → ❌ Error           |

```js
// var Hoisting
console.log(a); // undefined

var a = 10;
```

```js
// let Hoisting
console.log(b); // ❌ Error

let b = 20;
```

```js
// Function Declaration
test();

function test() {
  console.log("Hello");
}
```

```js
// Function Expression
sayHi(); // ❌ Error

const sayHi = function () {
  console.log("Hi");
};
```

### TDZ (Temporal Dead Zone)

| Item                         | Details                             |
| ---------------------------- | ----------------------------------- |
| TDZ                          | Time before variable initialization |
| Affects                      | `let` and `const`                   |
| Access Before Initialization | ❌ Error                            |
| Starts                       | Beginning of scope                  |
| Ends                         | Variable initialization             |

- Declarations are hoisted, not initializations
- Prefer `let` and `const` over `var`
- Function declarations are fully hoisted

---

## 📌 Execution Context

Execution Context is the environment where JavaScript code executes.

| Type                       | Details                            |
| -------------------------- | ---------------------------------- |
| Global Execution Context   | Created for global code execution  |
| Function Execution Context | Created whenever function runs     |
| `this`                     | Refers to current execution object |
| Memory Phase               | Stores variables/functions         |
| Execution Phase            | Executes code line by line         |

### Execution Phases

| Phase           | Purpose                                  |
| --------------- | ---------------------------------------- |
| Memory Creation | Allocates memory for variables/functions |
| Code Execution  | Runs code statements                     |

```js
var a = 10;

function greet() {
  var msg = "Hello";
  console.log(msg);
}

greet();
```

### Execution Flow

```txt
1. Global Context Created

Memory:
a → undefined
greet → function
```

```txt
2. Code Execution

a → 10
greet() called
```

```txt
3. Function Context Created

msg → undefined
msg → "Hello"
```

```txt
4. Function Removed After Execution
```

### Call Stack

```txt
| greet() |
| Global  |
```

### Execution Flow

| Step | Action                                    |
| ---- | ----------------------------------------- |
| 1    | Global execution context created          |
| 2    | Memory allocated                          |
| 3    | Code executed                             |
| 4    | Function context created on function call |
| 5    | Function removed after execution          |

- JavaScript executes code inside execution contexts
- Each function creates new execution context
- Managed internally using call stack

---

## 📌 Call Stack

Call Stack is a data structure that manages function execution order.

| Feature        | Details                          |
| -------------- | -------------------------------- |
| Structure      | LIFO (Last In First Out)         |
| Push           | Function added to stack          |
| Pop            | Function removed after execution |
| Global Context | Added first                      |
| Function Calls | Added above current execution    |

```js
// Example
function one() {
  two();
}

function two() {
  console.log("Hello");
}

one();
```

### Call Stack Flow

```txt
| two() |
| one() |
| Global |
```

```txt
After Execution

| Global |
```

### Stack Overflow

```js
function test() {
  test();
}

test();
```

❌ Infinite recursion → Stack Overflow

- Functions execute one at a time
- Last called function executes first
- Used internally by JavaScript engine

---

## 📌 Lexical Environment

Lexical Environment defines how variables/functions are accessible based on code location.

| Part            | Details                    |
| --------------- | -------------------------- |
| Local Memory    | Stores variables/functions |
| Outer Reference | Links to parent scope      |
| Scope Chain     | Searches variables upward  |

```js
let app = "JS";

function outer() {
  let name = "John";

  function inner() {
    console.log(name);
    console.log(app);
  }

  inner();
}

outer();
```

### Scope Lookup

```txt
inner()
  ↓
outer()
  ↓
Global
```

### Variable Access

| Variable | Found In     |
| -------- | ------------ |
| `name`   | `outer()`    |
| `app`    | Global Scope |

- Inner scope can access outer scope
- Outer scope cannot access inner scope
- Core concept behind closures

---

## 📌 Objects

Objects store data as key-value pairs.

| Feature        | Details                | Example        |
| -------------- | ---------------------- | -------------- |
| Property       | Key-value data         | `name: "John"` |
| Method         | Function inside object | `greet() {}`   |
| Nested Object  | Object inside object   | `address: {}`  |
| Dynamic Access | Access using `[]`      | `user["name"]` |

```js
const user = {
  name: "John",
  age: 25,

  greet() {
    console.log("Hello");
  },
};
```

### Accessing Properties

```js
// Dot Notation
user.name;
```

```js
// Bracket Notation
user["age"];
```

### Adding & Updating

```js
// Add Property
user.city = "NY";
```

```js
// Update Property
user.age = 30;
```

### Removing Properties

```js
delete user.city;
```

| Object Usage     | Example                 |
| ---------------- | ----------------------- |
| User Data        | `{ name, email, age }`  |
| API Response     | Server JSON data        |
| Configuration    | App settings/options    |
| DOM Elements     | Browser element objects |
| Form Data        | Input field values      |
| State Management | React/Vue app state     |

### Common Object Methods

| Method             | Purpose                 |
| ------------------ | ----------------------- |
| `Object.keys()`    | Returns keys            |
| `Object.values()`  | Returns values          |
| `Object.entries()` | Returns key-value pairs |

- Objects are reference types
- Keys are usually strings
- Used heavily for structured data

### crypto.randomUUID()

- Every call generates a new unique value.

| Purpose         | Generate Unique Identifier (UUID v4)     |
| --------------- | ---------------------------------------- |
| Returns         | String                                   |
| Browser Support | Modern Browsers                          |
| React Usage     | Keys, Temporary IDs, Client-Side Records |

```ts
crypto.randomUUID();

36b8f84d-df4e-4d49-b662-bcde71a8764f
7c9f2d9e-63df-4d3c-a0e2-f8d8c40b1c93

// Usage
const user = {
  id: crypto.randomUUID(),
  name: "John",
};

// React
const users = [
  {
    id: crypto.randomUUID(),
    name: "John",
  },
];
```

### Object Features

| Feature            | Syntax           | Example                |
| ------------------ | ---------------- | ---------------------- |
| Dot Notation       | `obj.prop`       | `user.name`            |
| Bracket Notation   | `obj[key]`       | `user["name"]`         |
| Destructuring      | `const {x}=obj`  | `const {name}=user`    |
| Spread             | `{...obj}`       | `{...user}`            |
| Optional Chaining  | `obj?.prop`      | `user?.address?.city`  |
| Nullish Coalescing | `a ?? b`         | `user.name ?? "Guest"` |
| Computed Keys      | `{[key]:val}`    | `{[field]:value}`      |
| delete             | `delete obj.key` | `delete user.age`      |

---

## 📌 Arrays

- Arrays store multiple values in ordered collections.
- Arrays are objects in JavaScript, and their indexes are actually keys.

| Feature        | Details                                           | Examples                                              |
| -------------- | ------------------------------------------------- | ----------------------------------------------------- |
| Indexed Values | Array items use numeric indexes starting from `0` | `arr[0]`, `arr.at(1)`                                 |
| Multiple Data  | Stores multiple values in single variable         | `["JS", "React"]`, `[1, true, {}]`                    |
| Dynamic Size   | Items can be added/removed anytime                | `push()`, `pop()`, `shift()`, `unshift()`, `splice()` |
| Iterable       | Supports loops and array methods                  | `for...of`, `forEach()`, `map()`, `filter()`          |

### Array Syntax

```js
const fruits = ["Apple", "Mango", "Orange"];
```

### Accessing Values

```js
fruits[0]; // Apple
```

```js
fruits.length; // 3
```

| Common Methods | Purpose           |
| -------------- | ----------------- |
| `push()`       | Add at end        |
| `pop()`        | Remove from end   |
| `shift()`      | Remove first item |
| `unshift()`    | Add at beginning  |
| `map()`        | Transform array   |
| `filter()`     | Filter items      |
| `find()`       | Find first match  |

```js
// Add Item
fruits.push("Banana");
```

```js
// Loop Array
fruits.forEach((item) => {
  console.log(item);
});
```

```js
// Transform Array
const nums = [1, 2, 3];

const doubled = nums.map((n) => n * 2);
```

| Real-World Usage | Example          |
| ---------------- | ---------------- |
| Product Lists    | Ecommerce items  |
| API Data         | User arrays      |
| Table Data       | Rows/items       |
| Menu Navigation  | Navigation links |

- Arrays are reference types
- Arrays can store mixed data types
- Use array methods instead of manual loops when possible

---

## 📌 Methods

Methods are functions stored inside objects.

| Feature          | Details                  | Example        |
| ---------------- | ------------------------ | -------------- |
| Object Method    | Function inside object   | `user.greet()` |
| Access `this`    | Refers to current object | `this.name`    |
| Shorthand Syntax | Modern method syntax     | `greet() {}`   |

```js
// Object Method
const user = {
  name: "John",

  greet: function () {
    console.log("Hello");
  },
};

user.greet();
```

```js
// Access Object Data
const user = {
  name: "John",

  greet() {
    console.log(this.name);
  },
};
```

```js
// Method Shorthand
const calc = {
  sum(a, b) {
    return a + b;
  },
};
```

| Type   | Common Built-in Methods           |
| ------ | --------------------------------- |
| Array  | `map()`, `filter()`, `push()`     |
| String | `trim()`, `slice()`, `includes()` |
| Object | `keys()`, `values()`, `entries()` |

- Methods are object functions
- `this` commonly refers to current object
- Use shorthand syntax in modern JavaScript

---

## 📌 this

`this` refers to the object currently executing the function.

| Context          | `this` Refers To       | Real-Life Example       |
| ---------------- | ---------------------- | ----------------------- |
| Global Scope     | `window` (browser)     | Global browser access   |
| Object Method    | Current object         | Logged-in user data     |
| Regular Function | `window` / `undefined` | Utility/helper function |
| Arrow Function   | Parent scope `this`    | React callbacks         |
| Event Handler    | Triggered element      | Clicked button/input    |

```js
// Global Scope
console.log(this); // window
```

```js
// Object Method
const user = {
  name: "John",

  greet() {
    console.log(this.name);
  },
};

user.greet(); // John
```

```js
// Regular Function
function show() {
  console.log(this);
}

show();
```

```js
// Arrow Function
const app = {
  name: "Frontend",

  start: () => {
    console.log(this.name);
  },
};

app.start(); // undefined
```

```js
// Event Handler
button.addEventListener("click", function () {
  console.log(this); // clicked button
});
```

| Common Methods | Purpose                      |
| -------------- | ---------------------------- |
| `call()`       | Calls with custom `this`     |
| `apply()`      | Same as call with array args |
| `bind()`       | Returns bound function       |

- `this` depends on how function is called
- Arrow functions do not create own `this`
- Common interview topic

---

## 📌 Destructuring

Destructuring extracts values from arrays or objects into variables.

| Type                 | Details                   | Example            |
| -------------------- | ------------------------- | ------------------ |
| Object Destructuring | Extract object properties | `const {name}`     |
| Array Destructuring  | Extract array values      | `const [a, b]`     |
| Default Values       | Fallback values           | `{age = 18}`       |
| Renaming             | Rename variables          | `{name: userName}` |
| Rest Operator        | Collect remaining values  | `...rest`          |

```js
// Object Destructuring
const user = {
  name: "John",
  age: 25,
};

const { name, age } = user;
```

```js
// Array Destructuring
const colors = ["Red", "Blue"];

const [first, second] = colors;
```

```js
// Default Value
const { city = "NY" } = user;
```

```js
// Renaming Variable
const { name: userName } = user;
```

```js
// Rest Operator
const { name, ...rest } = user;
```

| Real-World Usage    | Example                  |
| ------------------- | ------------------------ |
| API Response        | Extract response data    |
| Function Parameters | Cleaner arguments        |
| React Props         | Component props handling |
| Array Values        | Swap/access values       |

| Benefit                | Without Destructuring  | With Destructuring      |
| ---------------------- | ---------------------- | ----------------------- |
| Cleaner Code           | `user.name`            | `const { name } = user` |
| Faster Access          | Repeated object access | Direct variable usage   |
| Better Readability     | More repetitive code   | Short and clean         |
| Easier Function Params | `props.title`          | `function({ title })`   |
| API Handling           | Manual extraction      | Direct extraction       |

```js
// Without Destructuring
const name = user.name;
const age = user.age;
```

```js
// With Destructuring
const { name, age } = user;
```

- Reduces repetitive code
- Common in React and APIs
- Improves readability

---

## 📌 Spread & Rest (`...`)

`...` is used to expand or collect values.

| Type            | Purpose                   | Example      |
| --------------- | ------------------------- | ------------ |
| Spread Operator | Expands values            | `...[1,2,3]` |
| Rest Operator   | Collects remaining values | `...args`    |

| Feature  | Spread Operator                 | Rest Operator                  |
| -------- | ------------------------------- | ------------------------------ |
| Purpose  | Expands values                  | Collects values                |
| Usage    | Arrays, objects, function calls | Function params, destructuring |
| Position | Anywhere                        | Must be last                   |
| Output   | Individual values               | Array/Object                   |

### Spread Operator

```js
// Array Copy
const arr1 = [1, 2];
const arr2 = [...arr1];
```

```js
// Merge Arrays
const merged = [...a, ...b];
```

```js
// Object Copy
const user2 = { ...user1 };
```

```js
// Add New Values
const nums = [1, 2, ...more];
```

### Rest Operator

```js
// Function Arguments
function sum(...nums) {
  console.log(nums);
}
```

```js
// Object Rest
const { name, ...rest } = user;
```

```js
// Array Rest
const [first, ...others] = arr;
```

| Real-World Usage  | Example                 |
| ----------------- | ----------------------- |
| Clone Data        | Copy arrays/objects     |
| Merge Data        | Combine objects/arrays  |
| Dynamic Params    | Unlimited function args |
| Remove Properties | Extract remaining data  |

- Spread expands values
- Rest collects values
- Common in React and APIs

---

## 📌 Prototype Basics ⚠️

A prototype is an object from which other objects inherit properties and methods.

| Feature         | Details                 | Example           |
| --------------- | ----------------------- | ----------------- |
| Prototype       | Shared parent object    | `User.prototype`  |
| Inheritance     | Access parent methods   | `obj.method()`    |
| Prototype Chain | Links parent prototypes | `obj → prototype` |
| Shared Methods  | Reuse methods in memory | `prototype.greet` |

```js
function User(name) {
  this.name = name;
}

User.prototype.greet = function () {
  console.log("Hello " + this.name);
};

const user1 = new User("John");

user1.greet();
```

### Prototype Chain

```txt
user1
  ↓
User.prototype
  ↓
Object.prototype
  ↓
null
```

### Built-in Prototype Examples

```js
const arr = [1, 2, 3];

arr.push(4);
```

`push()` comes from `Array.prototype`

| Real-World Usage    | Purpose                     |
| ------------------- | --------------------------- |
| Method Sharing      | Reuse common methods        |
| Inheritance         | Access parent functionality |
| Memory Optimization | Avoid duplicate functions   |

- JavaScript uses prototype-based inheritance
- Objects inherit from other objects
- Classes internally use prototypes

---

## 📌 Template Literals

Template literals use backticks `` ` ` `` for dynamic strings.

| Feature                | Details                      | Example            |
| ---------------------- | ---------------------------- | ------------------ |
| Multiline String       | Supports line breaks         | `` `Hello` ``      |
| Variable Interpolation | Insert variables using `${}` | `` `Hi ${name}` `` |
| Expression Support     | Supports JS expressions      | `` `${2 + 2}` ``   |

```js
// Basic Template Literal
const name = "John";

console.log(`Hello ${name}`);
```

```js
// Multiline String
const text = `
Hello
World
`;
```

```js
// Expressions
console.log(`Total: ${5 + 5}`);
```

```js
// Old Way
"Hello " + name;

// Modern Way
`Hello ${name}`;
```

| Real-World Usage | Example           |
| ---------------- | ----------------- |
| Dynamic UI Text  | `Welcome ${user}` |
| HTML Templates   | Dynamic markup    |
| API Messages     | Dynamic responses |

- Uses backticks instead of quotes
- Cleaner than string concatenation
- Common in React and modern JS

---

## 📌 Modules

- Modules split JavaScript into reusable files.
- ES Modules work in vanilla JavaScript without frameworks.

| Feature        | Details                  | Example                     |
| -------------- | ------------------------ | --------------------------- |
| `export`       | Share code from file     | `export default fn`         |
| `import`       | Use exported code        | `import fn from "./app.js"` |
| Named Export   | Export multiple values   | `export { a, b }`           |
| Default Export | Export single main value | `export default User`       |

### Export Examples

```js
// Named Export
export const name = "John";

export function greet() {}
```

```js
// Default Export
export default function App() {}
```

### Import Examples

```js
// Named Import
import { name, greet } from "./app.js";
```

```js
// Default Import
import App from "./app.js";
```

```js
// Import All
import * as utils from "./utils.js";
```

| Real-World Usage   | Purpose              |
| ------------------ | -------------------- |
| Component Files    | React/Vue components |
| Utility Functions  | Shared helpers       |
| API Services       | Separate API logic   |
| Large Applications | Organized structure  |

### Module Types

| Type                   | Example                  |
| ---------------------- | ------------------------ |
| ES Modules (Modern)    | `import/export`          |
| CommonJS (Node.js Old) | `require/module.exports` |

- Helps organize large applications
- Avoids global variable pollution
- ES Modules are modern standard
- Works without React/Vue/etc.
- `Scope` Modules have separate scope

---

## 📌 Optional Chaining (`?.`)

Optional chaining safely accesses nested properties without errors.

| Feature              | Details                       | Example                |
| -------------------- | ----------------------------- | ---------------------- |
| Safe Property Access | Prevents undefined errors     | `user?.name`           |
| Nested Access        | Access deep properties safely | `user?.profile?.email` |
| Optional Method Call | Safely call methods           | `user?.greet?.()`      |
| Array Access         | Safe array lookup             | `arr?.[0]`             |

### Without vs With

```js
// Without Optional Chaining
user && user.profile && user.profile.name;
```

```js
// With Optional Chaining
user?.profile?.name;
```

```js
// Nested Object
const user = {
  profile: {
    name: "John",
  },
};

console.log(user?.profile?.name);
```

```js
// Missing Property
console.log(user?.address?.city); // undefined
```

```js
// Optional Method
user?.greet?.();
```

```js
// Array Access
arr?.[0];
```

| Real-World Usage | Purpose                 |
| ---------------- | ----------------------- |
| API Responses    | Safe nested data access |
| Optional Data    | Handle missing values   |
| Dynamic Objects  | Prevent runtime errors  |

- Returns `undefined` instead of error
- Useful with APIs and dynamic data
- Makes nested checks cleaner

---

## 📌 Nullish Coalescing (`??`)

`??` provides a fallback value only for `null` or `undefined`.

| Feature                | Details                    | Example           |
| ---------------------- | -------------------------- | ----------------- |
| Fallback Value         | Default when value missing | `name ?? "Guest"` |
| Checks Only            | `null` and `undefined`     | `null ?? "Hi"`    |
| Preserves Falsy Values | Keeps `0`, `false`, `""`   | `0 ?? 10`         |

```js
// Basic Usage
const name = null;

console.log(name ?? "Guest");
```

```js
// Keeps 0
const count = 0;

console.log(count ?? 10); // 0
```

```js
// Keeps false
const isAdmin = false;

console.log(isAdmin ?? true); // false
```

### `||` vs `??`

- `||` → Treats all falsy values as missing (`0`, `false`, `""`, `null`, `undefined`, `NaN`)
- `??` → Treats only `null` and `undefined` as missing

### Example Difference

```js
// OR Operator
0 || 10; // 10
```

```js
// Nullish Coalescing
0 ?? 10; // 0
```

- Safer than `||` for default values
- Common with APIs and forms
- Often used with optional chaining

---

## 📌 Sets & Maps

`Set` stores unique values, `Map` stores key-value pairs.

| Type        | Details                      | Example            |
| ----------- | ---------------------------- | ------------------ |
| `Set`       | Stores unique values only    | `new Set([1,2,2])` |
| `Map`       | Stores key-value pairs       | `new Map()`        |
| Set Methods | `add()`, `delete()`, `has()` | `set.add(1)`       |
| Map Methods | `set()`, `get()`, `has()`    | `map.set("a",1)`   |

### Set Examples

```js
// Unique Values
const nums = new Set([1, 2, 2, 3]);

console.log(nums); // {1,2,3}
```

```js
// Add Value
nums.add(4);
```

```js
// Check Value
nums.has(2);
```

### Map Examples

```js
// Create Map
const user = new Map();

user.set("name", "John");
```

```js
// Get Value
user.get("name");
```

```js
// Check Key
user.has("name");
```

| Type  | Real-Life Example                         |
| ----- | ----------------------------------------- |
| `Set` | Prevent duplicate cart items in ecommerce |
|       | Store unique hashtags/tags                |
|       | Track online users in chat app            |
|       | Prevent duplicate form selections         |
| `Map` | Cache API response data                   |
|       | Store user data by ID                     |
|       | Store product details by SKU              |
|       | Manage component/state references         |

- `Set` automatically removes duplicates
- `Map` supports any key type
- Better than objects for dynamic key handling

---

## 📌 Symbols ⚠️

`Symbol` creates unique and immutable identifiers.

| Feature              | Details                  | Example         |
| -------------------- | ------------------------ | --------------- |
| Unique Value         | Every symbol is unique   | `Symbol("id")`  |
| Immutable            | Cannot be changed        | Fixed value     |
| Hidden Property Keys | Avoid property conflicts | `obj[id]`       |
| Non-Enumerable       | Hidden from normal loops | `Object.keys()` |

```js
// Create Symbol
const id = Symbol("id");
```

```js
// Unique Symbols
Symbol("id") === Symbol("id"); // false
```

```js
// Object Property
const user = {
  name: "John",
  [id]: 101,
};
```

```js
// Access Symbol Property
console.log(user[id]);
```

| Real-World Usage            | Purpose                        |
| --------------------------- | ------------------------------ |
| Unique Object Keys          | Prevent key conflicts          |
| Internal Object Data        | Hidden/private-like properties |
| Library/Framework Internals | Safe property management       |

- Every symbol is unique
- Commonly used as hidden object keys
- Rare in everyday frontend development

---

## 📌 BigInt ⚠️

`BigInt` is used for very large integers beyond normal `Number` limits.

| Feature        | Details                      | Example            |
| -------------- | ---------------------------- | ------------------ |
| Large Integers | Supports huge numbers        | `123456789n`       |
| `n` Suffix     | Creates BigInt value         | `100n`             |
| Safe Precision | Avoids number precision loss | Large calculations |
| Type           | Separate primitive type      | `typeof 10n`       |

```js
// BigInt Value
const big = 123456789123456789n;
```

```js
// Using BigInt()
const num = BigInt(100);
```

```js
// Math Operations
const total = 10n + 20n;
```

```js
// Type Check
typeof 10n; // "bigint"
```

| Type     | Safe Integer Limit            |
| -------- | ----------------------------- |
| `Number` | `-(2^53 - 1)` to `(2^53 - 1)` |
| `BigInt` | No practical integer limit    |

| Real-World Usage  | Purpose                 |
| ----------------- | ----------------------- |
| Financial Systems | Large calculations      |
| IDs               | Very large unique IDs   |
| Cryptography      | Huge integer operations |

- Cannot mix directly with normal numbers
- Only works with integers
- Rare in typical frontend apps

---

## 📌 Classes

Classes are templates used to create objects.

| Feature         | Details                     | Example             |
| --------------- | --------------------------- | ------------------- |
| Class           | Blueprint for objects       | `class User {}`     |
| Constructor     | Initializes object data     | `constructor(name)` |
| Method          | Function inside class       | `greet()`           |
| Object Creation | Create instance using `new` | `new User()`        |

```js
// Basic Class
class User {
  constructor(name) {
    this.name = name;
  }

  greet() {
    console.log(this.name);
  }
}

const user1 = new User("John");

user1.greet();
```

```js
// Multiple Objects
const user2 = new User("Mike");
```

| Real-World Usage | Example                |
| ---------------- | ---------------------- |
| User Models      | User/profile objects   |
| Product Systems  | Ecommerce products     |
| Components       | UI component structure |
| Game Objects     | Player/enemy objects   |

### Classes vs Functions

| Class              | Constructor Function  |
| ------------------ | --------------------- |
| Modern syntax      | Older syntax          |
| Cleaner structure  | Prototype-based setup |
| Easier inheritance | More manual code      |

- Classes are built on prototypes internally
- Use `new` to create objects
- Common in large applications

---

## 📌 Inheritance

Inheritance allows one class to use properties and methods of another class.

| Feature            | Details                  | Example                    |
| ------------------ | ------------------------ | -------------------------- |
| `extends`          | Inherit parent class     | `class Admin extends User` |
| `super()`          | Calls parent constructor | `super(name)`              |
| Method Inheritance | Access parent methods    | `admin.greet()`            |
| Method Override    | Replace parent method    | `greet() {}`               |

```js
// Parent Class
class User {
  constructor(name) {
    this.name = name;
  }

  greet() {
    console.log(this.name);
  }
}
```

```js
// Child Class
class Admin extends User {
  constructor(name, role) {
    super(name);

    this.role = role;
  }
}

const admin = new Admin("John", "Admin");

admin.greet();
```

```js
// Method Override
class Manager extends User {
  greet() {
    console.log("Manager");
  }
}
```

### Real-World Usage

| Usage         | Example                     |
| ------------- | --------------------------- |
| User Roles    | Admin, Customer, Manager    |
| UI Components | Base button/card components |
| Game Objects  | Player, Enemy, NPC          |
| Product Types | Digital/Physical products   |

- Reuses common code
- Reduces duplication
- Core concept in OOP

---

## 📌 Encapsulation ⚠️

Encapsulation hides internal data and controls access to it.

| Feature           | Details                | Example          |
| ----------------- | ---------------------- | ---------------- |
| Data Hiding       | Restrict direct access | Private fields   |
| Controlled Access | Access through methods | `getName()`      |
| Private Field     | Hidden class property  | `#name`          |
| Public Method     | Safe interaction       | `user.getName()` |

```js
// Private Field
class User {
  #name;

  constructor(name) {
    this.#name = name;
  }

  getName() {
    return this.#name;
  }
}

const user = new User("John");

console.log(user.getName());
```

```js
// Direct Access
console.log(user.#name); // ❌ Error
```

| Real-World Usage         | Example                | Where It Can Be Used   | Syntax          |
| ------------------------ | ---------------------- | ---------------------- | --------------- |
| Password/Data Protection | Hide user password     | Login/Auth Systems     | `#password`     |
| Banking Apps             | Access balance safely  | Wallet/Balance Systems | `getBalance()`  |
| API/Data Validation      | Validate before update | User/Profile Forms     | `updateEmail()` |
| State Management         | Prevent direct changes | React/Vue Applications | `setState()`    |

- Protects internal data
- Improves security and maintainability
- Common OOP concept

---

## 📌 Prototype Chain 📄

Prototype Chain is the mechanism JavaScript uses to inherit properties and methods.

| Feature           | Details                    | Example               |
| ----------------- | -------------------------- | --------------------- |
| Prototype Lookup  | Searches parent objects    | `user.toString()`     |
| Inheritance Chain | Object linked to prototype | `obj → prototype`     |
| Shared Methods    | Reuse common methods       | `Array.prototype.map` |
| End of Chain      | Stops at `null`            | `Object.prototype`    |

```js
const arr = [1, 2, 3];

arr.push(4);
```

```txt
arr
 ↓
Array.prototype
 ↓
Object.prototype
 ↓
null
```

`push()` is found in `Array.prototype`

### Object Example

```js
const user = {
  name: "John",
};

console.log(user.toString());
```

```txt
user
 ↓
Object.prototype
 ↓
null
```

| Real-World Usage    | Example                   |
| ------------------- | ------------------------- |
| Shared Methods      | Array/String methods      |
| Inheritance         | Parent-child objects      |
| Framework Internals | React/Vue classes/objects |

- JavaScript searches upward through prototypes
- Stops when property is found or reaches `null`
- Core concept behind inheritance

---

## 📌 Currying ⚠️

Currying converts a function with multiple arguments into nested single-argument functions.

| Feature           | Details                  | Example         |
| ----------------- | ------------------------ | --------------- |
| Nested Functions  | Returns another function | `fn(a)(b)`      |
| Partial Execution | Pass values step-by-step | `sum(2)(3)`     |
| Reusable Logic    | Reuse preset values      | `multiplyBy2()` |

```js
// Normal Function
function sum(a, b) {
  return a + b;
}
```

```js
// Curried Function
function sum(a) {
  return function (b) {
    return a + b;
  };
}

sum(2)(3); // 5
```

```js
// Arrow Function
const multiply = (a) => (b) => a * b;

multiply(2)(5); // 10
```

```js
// Reusable Function
const multiplyBy2 = multiply(2);

multiplyBy2(10); // 20
```

| Real-World Usage       | Example                  |
| ---------------------- | ------------------------ |
| Reusable Utilities     | Preset API/config values |
| Event Handlers         | Dynamic callbacks        |
| Functional Programming | Compose reusable logic   |

- Breaks large functions into smaller functions
- Useful for reusable and dynamic logic
- Common in functional programming

---

## 📌 Functional Programming (FP) 📄

Functional Programming focuses on pure, reusable, and predictable functions.

| Concept                | Details                       | Example        |
| ---------------------- | ----------------------------- | -------------- |
| Pure Function          | Same input → same output      | `sum(2,3)`     |
| Immutability           | Avoid modifying original data | `[...]`        |
| First-Class Functions  | Functions treated as values   | `fn(callback)` |
| Higher Order Functions | Accept/return functions       | `map()`        |
| Function Composition   | Combine functions             | `fn1(fn2())`   |

```js
// Pure Function
function sum(a, b) {
  return a + b;
}
```

```js
// Immutability
const arr = [1, 2];

const newArr = [...arr, 3];
```

```js
// Higher Order Function
nums.map((num) => num * 2);
```

```js
// Function Composition
const double = (n) => n * 2;
const square = (n) => n * n;

square(double(2));
```

| Real-World Usage    | Example                         |
| ------------------- | ------------------------------- |
| Array Processing    | `map()`, `filter()`, `reduce()` |
| State Management    | React/Redux immutable updates   |
| Data Transformation | API response formatting         |

- Encourages reusable code
- Reduces side effects
- Common in modern frontend frameworks

### reduce()

- reduce() iterates through an array and reduces it to a single value.
  - Calculate cart total, Count occurrences, Sum marks, prices, quantities

```js
// Syntax
array.reduce((accumulator, currentValue) => {
  return updatedAccumulator;
}, initialValue);

// Usage
let arr = [10, 15, 30];
const sum = arr.reduce((total, item) => total + item, 0);
console.log(sum); // 55

// Flow
// total = 0,  item = 10 (0 + 10 = 10)
// total = 10, item = 15 (10 + 15 = 25)
// total = 25, item = 30 (25 + 30 = 55)
```

- Accumulator that collects and stores data for later use
  - acc → accumulator (stores result)
  - curr → current value
  - 0 → starting value

---

## 📌 Immutability 📄

Immutability means not modifying original data directly.

| Concept             | Details                                      | Example             |
| ------------------- | -------------------------------------------- | ------------------- |
| Immutable Update    | Create new copy instead of changing original | `[...]`, `{...}`    |
| Array Immutability  | Avoid direct array mutation                  | `map()`, `filter()` |
| Object Immutability | Copy object before update                    | `{ ...user }`       |
| Predictable State   | Easier debugging/tracking                    | React state updates |

```js
// Mutable ❌
const arr = [1, 2];

arr.push(3);
```

```js
// Immutable ✅
const arr = [1, 2];

const newArr = [...arr, 3];
```

```js
// Object Update
const user = {
  name: "John",
};

const updatedUser = {
  ...user,
  age: 25,
};
```

```js
// filter()
const active = users.filter((u) => u.active);
```

| Real-World Usage | Example                  |
| ---------------- | ------------------------ |
| React State      | `setState({...})`        |
| Redux Store      | Immutable updates        |
| API Data         | Safe data transformation |

- Prevents accidental data changes
- Easier debugging and state tracking
- Important in React and Redux

---

## 📌 Memory Management 📄

Memory Management controls how JavaScript allocates and removes memory.

| Concept            | Details                              | Example             |
| ------------------ | ------------------------------------ | ------------------- |
| Memory Allocation  | Memory created for variables/objects | `let user = {}`     |
| Memory Release     | Unused memory removed automatically  | Garbage Collection  |
| Garbage Collection | Removes unreachable data             | Unused objects      |
| Memory Leak        | Memory not released properly         | Unremoved listeners |

```js
// Memory Allocation
let user = {
  name: "John",
};
```

```js
// Unused Variable
user = null;
```

```js
// Memory Leak Example
button.addEventListener("click", () => {
  console.log("Clicked");
});
```

| Real-World Usage | Example                      |
| ---------------- | ---------------------------- |
| React Apps       | Cleanup effects/listeners    |
| Large Data Apps  | Avoid unused objects         |
| Realtime Apps    | Prevent growing memory usage |

| Common Causes of Memory Leaks | Example                 |
| ----------------------------- | ----------------------- |
| Unremoved Event Listeners     | `addEventListener()`    |
| Unused Timers                 | `setInterval()`         |
| Global Variables              | Persistent memory usage |

- JavaScript uses automatic garbage collection
- Remove unused references when possible
- Memory leaks reduce app performance

---

## 📌 Regular Expressions (Regex)

Regex is used for pattern matching, validation, searching, and text processing.

| Pattern / Method | Purpose              | Example                   | Real-World Usage  |
| ---------------- | -------------------- | ------------------------- | ----------------- |
| `/abc/`          | Match exact text     | `/hello/`                 | Keyword matching  |
| `test()`         | Check match exists   | `/js/.test("javascript")` | Validation        |
| `match()`        | Get matched values   | `"abc".match(/a/)`        | Search extraction |
| `replace()`      | Replace matched text | `"123".replace(/\d/g,"")` | Input cleanup     |
| `search()`       | Find match index     | `"hello".search(/e/)`     | Search systems    |
| `split()`        | Split using pattern  | `"a,b".split(/,/)`        | CSV parsing       |
| `\d`             | Match digits         | `/\d/`                    | OTP/numbers       |
| `\w`             | Match word chars     | `/\w/`                    | Usernames         |
| `\s`             | Match spaces         | `/\s/`                    | Trim/cleanup      |
| `.`              | Any character        | `/h./`                    | Flexible matching |
| `^`              | Starts with          | `/^https/`                | URL validation    |
| `$`              | Ends with            | `/.png$/`                 | File validation   |
| `[]`             | Match character set  | `/[abc]/`                 | Allowed chars     |
| `()`             | Group patterns       | `/(abc)/`                 | Complex matching  |
| `*`              | 0 or more            | `/lo*/`                   | Flexible text     |
| `+`              | 1 or more            | `/lo+/`                   | Required chars    |
| `?`              | Optional match       | `/colou?r/`               | Optional patterns |
| `{n}`            | Exact count          | `/\d{6}/`                 | OTP validation    |
| `{n,m}`          | Range count          | `/\d{6,10}/`              | Phone validation  |
| `g`              | Global flag          | `/js/g`                   | Replace all       |
| `i`              | Case-insensitive     | `/js/i`                   | Search/filter     |

### Common Regex Examples

```js
// Email Validation
const email = "john@gmail.com";
const pattern = /\S+@\S+\.\S+/;

console.log(pattern.test(email));
// true
```

```js
// 6 Digit OTP
/\d{6}/;
```

```js
// Only Numbers
/^\d+$/;
```

```js
// Remove Spaces
text.replace(/\s/g, "");
```

```js
// Case-Insensitive Search
/hello/i;
```

```js
// Multiple File Extensions
const file = "photo.png";

console.log(/\.(jpg|png|webp)$/.test(file));
// true
```

### Common Operators

| Operator | Meaning                |
| -------- | ---------------------- |
| `\|`     | OR                     |
| `()`     | Group patterns         |
| `[]`     | Character set          |
| `^`      | Starts with            |
| `$`      | Ends with              |
| `?=`     | Must contain condition |

| Real-World Patterns     | Regex Syntax        | Purpose                    |
| ----------------------- | ------------------- | -------------------------- |
| Email Validation        | `/\S+@\S+\.\S+/`    | Validate email format      |
| Phone Validation        | `/^\d{10}$/`        | 10-digit phone number      |
| OTP Validation          | `/^\d{6}$/`         | 6-digit OTP                |
| Only Numbers            | `/^\d+$/`           | Numeric input              |
| Username Validation     | `/^\w+$/`           | Letters/numbers/underscore |
| Password Rules          | `/^(?=.*\d).{8,}$/` | Password validation        |
| Remove Spaces           | `/\s/g`             | Cleanup input              |
| File Extension Check    | `/.png$/`           | Validate image file        |
| URL Validation          | `/^https/`          | Secure URL check           |
| Case-Insensitive Search | `/react/i`          | Search/filter              |
| Replace All Digits      | `/\d/g`             | Remove numbers             |
| Multiple Spaces Cleanup | `/\s+/g`            | Normalize text             |
| Extract Numbers         | `/\d+/g`            | Parse values               |
| HTML Tag Detection      | `/<[^>]+>/g`        | Detect/remove tags         |
| Coupon Validation       | `/^[A-Z0-9]{6}$/`   | Promo codes                |

---

## Array Operations

```js
const users = [
  { id: 1, name: "John", active: true, skills: ["React", "JS"], age: 30 },
  { id: 2, name: "Jane", active: false, skills: ["CSS"], age: 25 },
];

const nums = [30, 10, 20];
const skills = ["HTML", "CSS", "React"];

// map → arr.map(callback)
users.map((user) => user.name); // ["John", "Jane"]

// filter → arr.filter(callback)
users.filter((user) => user.active); // [{ id: 1, name: "John", ... }]

// find → arr.find(callback)
users.find((user) => user.id === 1); // { id: 1, name: "John", ... }

// findIndex → arr.findIndex(callback)
users.findIndex((user) => user.id === 2); // 1

// some → arr.some(callback)
users.some((user) => user.active); // true

// every → arr.every(callback)
users.every((user) => user.active); // false

// reduce → arr.reduce(callback, initialValue)
nums.reduce((sum, num) => sum + num, 0); // 60

// sort → arr.sort(compareFn)
nums.sort((a, b) => a - b); // [10, 20, 30]

// includes → arr.includes(value)
skills.includes("React"); // true

// forEach → arr.forEach(callback)
users.forEach((user) => console.log(user.name)); // John, Jane

// flat → arr.flat(depth)
[
  [1, 2],
  [3, 4],
].flat(); // [1, 2, 3, 4]

// flatMap → arr.flatMap(callback)
users.flatMap((user) => user.skills); // ["React", "JS", "CSS"]

// push → arr.push(value)
skills.push("Vue"); // 4

// pop → arr.pop()
skills.pop(); // "React"

// shift → arr.shift()
skills.shift(); // "HTML"

// unshift → arr.unshift(value)
skills.unshift("Bootstrap"); // 4

// splice → arr.splice(start, deleteCount, items)
skills.splice(1, 1); // ["CSS"]

// reverse → arr.reverse()
skills.reverse(); // ["React", "CSS", "HTML"]
```

## Object Operations

```js
const user = {
  id: 1,
  name: "John",
  age: 30,
  city: "New York",
};

const key = "name";

// Dot Notation → obj.property
user.name; // "John"

// Bracket Notation → obj[key]
user["name"]; // "John"

// Destructuring → const { prop } = obj
const { name } = user; // name = "John"

// Spread → { ...obj }
const copy = { ...user }; // { id: 1, name: "John", age: 30, city: "New York" }

// Optional Chaining → obj?.prop?.nestedProp
user?.address?.city; // undefined

// Nullish Coalescing → value ?? defaultValue
user.country ?? "USA"; // "USA"

// Computed Property → { [key]: value }
const obj = { [key]: "Jane" }; // { name: "Jane" }

// delete → delete obj.property
delete user.age; // true

// Object.keys → Object.keys(obj)
Object.keys(user); // ["id", "name", "age", "city"]

// Object.values → Object.values(obj)
Object.values(user); // [1, "John", 30, "New York"]

// Object.entries → Object.entries(obj)
Object.entries(user); // [["id",1],["name","John"],["age",30],["city","New York"]]

// Object.fromEntries → Object.fromEntries(entries)
Object.fromEntries([
  ["name", "John"],
  ["age", 30],
]); // { name: "John", age: 30 }

// Object.assign → Object.assign(target, ...sources)
Object.assign({}, user, { age: 31 }); // { id: 1, name: "John", age: 31, city: "New York" }

// Object.hasOwn → Object.hasOwn(obj, key)
Object.hasOwn(user, "name"); // true

// Object.freeze → Object.freeze(obj)
Object.freeze(user); // object becomes immutable

// Object.seal → Object.seal(obj)
Object.seal(user); // cannot add/remove properties

// Object.preventExtensions → Object.preventExtensions(obj)
Object.preventExtensions(user); // cannot add new properties
```

## String Operations

```js
const str = "  Hello JavaScript World  ";
const email = "john@example.com";
const text = "React,Vue,Angular";

// length → str.length
str.length; // 26

// trim → str.trim()
str.trim(); // "Hello JavaScript World"

// trimStart → str.trimStart()
str.trimStart(); // "Hello JavaScript World  "

// trimEnd → str.trimEnd()
str.trimEnd(); // "  Hello JavaScript World"

// toUpperCase → str.toUpperCase()
str.toUpperCase(); // "  HELLO JAVASCRIPT WORLD  "

// toLowerCase → str.toLowerCase()
str.toLowerCase(); // "  hello javascript world  "

// includes → str.includes(search)
str.includes("JavaScript"); // true

// startsWith → str.startsWith(search)
email.startsWith("john"); // true

// endsWith → str.endsWith(search)
email.endsWith(".com"); // true

// indexOf → str.indexOf(search)
str.indexOf("JavaScript"); // 8

// lastIndexOf → str.lastIndexOf(search)
"hello hello".lastIndexOf("hello"); // 6

// slice → str.slice(start, end)
str.slice(2, 7); // "Hello"

// substring → str.substring(start, end)
str.substring(2, 7); // "Hello"

// replace → str.replace(search, replace)
str.replace("JavaScript", "JS"); // "  Hello JS World  "

// replaceAll → str.replaceAll(search, replace)
"a-b-c".replaceAll("-", "_"); // "a_b_c"

// split → str.split(separator)
text.split(","); // ["React", "Vue", "Angular"]

// concat → str.concat(value)
"Hello".concat(" World"); // "Hello World"

// repeat → str.repeat(count)
"Hi ".repeat(3); // "Hi Hi Hi "

// charAt → str.charAt(index)
str.charAt(2); // "H"

// at → str.at(index)
str.at(-1); // " "

// padStart → str.padStart(length, pad)
"5".padStart(3, "0"); // "005"

// padEnd → str.padEnd(length, pad)
"5".padEnd(3, "0"); // "500"

// match → str.match(regex)
email.match(/@/); // ["@"]

// search → str.search(regex)
email.search("@"); // 4

// localeCompare → str.localeCompare(other)
"apple".localeCompare("banana"); // -1

// valueOf → str.valueOf()
str.valueOf(); // "  Hello JavaScript World  "

// String → String(value)
String(123); // "123"
```

---
