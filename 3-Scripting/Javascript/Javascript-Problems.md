## 📌 Practical Problems

---

### ❓ Problem 1

```js
let x = 10;
if (function solve() {}) {
  x = x + typeof solve; // S1
  x = x - typeof solve; // S2
}
console.log(x);

// S1 Output: "10undefined"
// S2 Output: NaN
```

---

### ❓ Problem 2

```js
let x = [100, 200, 300];
let y = [100, 200, 300];
let z = y;

console.log(x == y, z == y, z == x);
// Output: false true false
```

- Arrays and objects are compared by reference, not by value.
- x and y are different array references.
- z and y point to the same array.

---

### ❓ Problem 3

```js
const obj = {
  pqr: 100,
  abc: 200,
  xyz: {
    pqr: 300,
    abc: 400,
  },
};

const {
  pqr,
  abc,
  xyz: { pqr: p },
} = obj;

console.log(pqr, abc, p);
// Output: 100 200 300

// Reason
const { pqr } = obj; // 100
const { abc } = obj; // 200
const { pqr: p } = obj.xyz; // 300
```

- pqr: p means: Get pqr from xyz, Store it in variable p

---

### ❓ Problem 4

```js
let arr = [1, 2, 3, 4, 5];
const filterArr = arr.map((e) => e > 3);
console.log(filterArr);

// Output: [false, false, false, true, true]

// Reason
1 > 3; // false
2 > 3; // false
3 > 3; // false
4 > 3; // true
5 > 3; // true
```

---

### ❓ Problem 5

- Return Smallest Word from Sentance

```js
function smallestWord(str) {
  return str.split(" ").sort((a, b) => a.length - b.length)[0];
}

console.log(smallestWord("My name is John"));
// Output: My
```

```js
// Step 1
str.split(" "); // "My name is John" > ["My", "name", "is", "John"]

// Step 2
.sort((a, b) => a.length - b.length) // ["My", "is", "name", "John"]
"My"   // 2
"is"   // 2
"name" // 4
"John" // 4

// Step 3
[0] // Gets the first element.
"My"
```

---

### ❓ Problem 6

- What will be the output?

```js
// Normal
a = 5;
console.log(a); // 5

// In Strict Mode
("use strict");
a = 5;
console.log(a); // ReferenceError: a is not defined
```

- Since a is assigned without let, const, or var, JavaScript creates a global variable (in non-strict mode).
- Assigning a variable without let, const, or var creates a global variable in non-strict mode, but throws a ReferenceError in strict mode.

---

### ❓ Problem 7 TDZ

```js
console.log(a, b);
var a = 10;
let b = 100;

// Output:
// undefined
// ReferenceError: Cannot access 'b' before initialization
```

---

### ❓ Problem 8

```js
// String
let name = "John";
name[2] = "J"; // This does NOT modify the original string.
console.log(name); // John

// Array
let arr = ["J", "o", "h", "n"];
arr[2] = "J";
console.log(arr.join(""));
// JoJn
```

```text
"John"
  ↓
try to change index 2 ('h')
  ↓
ignored (no error, no change)
```

- Strings in JavaScript are immutable, so individual characters cannot be changed using indexing.
  - Arrays → mutable
  - Strings → immutable

---

### ❓ Problem 9

```js
let a = 100;
let z = a++;

console.log(a + z); // 201
```

```js
// Step-by-step
z = 100; // old value
a = 101; // then increment
a + z = 101 + 100
```

---

### ❓ Problem 10

```js
// Reverse each world
let str = "My name John";
const result = str
  .split(" ")
  .map((word) => word.split("").reverse().join(""))
  .join(" ");

console.log(result); // "yM eman nhoJ"

// How it works
["My", "name", "John"]; // Split sentence into words
"My" → "ym" // This runs for EACH word: Reverse each word
"yM eman nhoJ" // Join array back into string with spaces
```

- We split the sentence into words, reverse each word using split("") → reverse() → join(""), and then join them back into a string.

---

### ❓ Problem 11

- Character count in a string

```js
let str = "John Smith";

let result = str
  .toLowerCase()
  .split("")
  .reduce((acc, char) => {
    if (char !== " ") {
      acc[char] = (acc[char] || 0) + 1;
    }
    return acc;
  }, {});

console.log(result);
// { j: 1, o: 1, h: 2, n: 1, s: 1, m: 1, i: 1, t: 1 }
```

- We split the string into characters and use a loop or reduce to count occurrences of each character while ignoring spaces.

---

### ❓ Problem 12

```js
function abc(b, ...a) {
  console.log(a);
}
abc(8, 9, 10, 11, 12);
// Output: [9, 10, 11, 12]
```

---

### ❓ Problem 13

- Separate numbers and characters into 2 arrays

```js
const arr = ["a", 1, "b", 2, "c", 3];

const chars = [];
const nums = [];

arr.forEach((item) => {
  if (typeof item === "number") {
    nums.push(item);
  } else {
    chars.push(item);
  }
});

console.log(chars); // ["a", "b", "c"]
console.log(nums); // [1, 2, 3]
```

- We separate values by checking their type using typeof and push them into different arrays using forEach() or reduce().

---

### ❓ Problem 14

- Swap values without 3rd variable

```js
// Problem
let a = 2;
let b = 3;

// Solution
[a, b] = [b, a]; // Using Destructuring
console.log(a, b); // 3 2
```

---

### ❓ Problem 15

- Find the Intersection of Two Arrays

```js
// Problem
const a1 = [1, 2, 3, 4, 5];
const a2 = [3, 4, 5, 6, 7];

// Solution
const result = a1.filter((num) => a2.includes(num));
console.log(result);
// [3, 4, 5]
```

- Array intersection can be found using filter() with includes() or optimized using a Set for faster lookup.

---

### ❓ Problem 16

```js
// Problem 1
var a = 50;
{
  var a = 5000;
}
let b = a;
{
  let b = 50000;
}
console.log(b); // Output: 5000 (var leaks out of block, let stays inside block scope.)

// Problem 2
var a = 50;
function abc1() {
  var a = 5000;
}
let b = a;
function abc() {
  let b = 50000;
}
console.log(b); // Output: 50 (var is function scoped, but no function call = no effect on outer value.)
```

---

### ❓ Problem 17

- What is the output of this code?

```js
console.log(2 - "2"); // 0
console.log("2" - "2"); // 0
console.log("John" - "2"); // NaN
console.log(2 + "2"); // 22
```

- (+) triggers string concatenation
- (-) converts to number, (+) converts to string when one operand is string.

---

### ❓ Problem 18

- find duplicate values in an array?

```js
// Problem
const abc = [2, 2, 1, 5, 6, 8, 10, 1, 7, 8];

// Solution
const duplicates = [
  ...new Set(abc.filter((item, index) => abc.indexOf(item) !== index)),
];

console.log(duplicates); // [2, 1, 8]
```

---

### ❓ Problem 19

- What is the output of this code?

```js
// Problem
console.log([] !== []); // true
```

- Arrays and objects are compared by reference, not by content.
  - [] --> 0x100
  - [] --> 0x200
- Different memory locations = different references.
- Each [] creates a new array in memory, so their references are different.

---

### ❓ Problem 20

- What is the output?

```js
// Problem
console.log(false + false); // 0
console.log(true + true); // 2
console.log(true + false); // 1

console.log("" == 0); // true
```

- In numeric operations, true becomes 1 and false becomes 0.
- With ==, an empty string "" is converted to 0 before comparison.

---

### ❓ Problem 21

```js
// Problem
function fn() {
  return;
  {
    name: "John"; // Never gets returned
  }
}
console.log(fn()); // undefined

// Solution
return { name: "John" }; // { name: 'John' }
```

- Never put an object on the next line after return; Javascript Automatic Semicolon Insertion (ASI) returns undefined.

---

### ❓ Problem 22

- find elements greater than a specific value in an array?

```js
// Problem
let arr = [10, 15, 30, 75, 40, 61, 23];

// Solution
const result = arr.filter((num) => num > 40);
console.log(result); // [75, 61]
```

- Use filter() to return all elements matching a condition.

---

### ❓ Problem 23

- What will be the output?

```js
a = 34;
let a;

console.log(a); // ReferenceError: Cannot access 'a' before initialization
```

- You cannot use a variable before declaring it with let due to Temporal Dead Zone (TDZ).

---

### ❓ Problem 24

```js
// Problem
const a = 10;
const b = "Nick";
const c = a - b;

console.log(typeof c, c);
// Output: number NaN
```

---

### ❓ Problem 25

```js
// Problem
const result1 = ["10", "10", "10"].map(parseInt);
const result2 = ["10", "10", "10", "10", "10"].map(parseInt);
const result3 = ["10", 10, "10", "10", "10"].map(parseInt);

console.log(result1); // Output: [ 10, NaN, 2 ]
console.log(result2); // Output: [ 10, NaN, 2, 3, 4 ]
console.log(result3); // Output: [ 10, NaN, 2, 3, 4 ]
```

```text
// Step-by-step Execution
parseInt("10", 0); // 10 (base 10 default)
parseInt("10", 1); // NaN (invalid radix)
parseInt("10", 2); // 2 (binary)
parseInt("10", 3); // 3 in base-3 → 3
parseInt("10", 4); // 4 in base-4 → 4
parseInt("10", 5); // 5 in base-5 → 5
```

- Wrong function is passed to map
- The output is [10, NaN, 2, 3, 4, 5] because map passes index as the second argument, which is treated as radix in parseInt, leading to unexpected base conversions.
- Yes, you can use parseInt with arrays using map(), but you should not directly pass parseInt into map, because it behaves unexpectedly due to extra arguments.

```js
const arr = ["10", "10", "10"];
console.log(arr.map(Number));
```

---

### ❓ Problem 26

```js
// Problem
const x = [];
x[4] = 1;
x.forEach((i) => {
  console.log("Hi");
});

// Output: Hi
```

```text
> x[4] = 1;
> The array becomes: [ <4 empty items>, 1 ]
> console.log(x.length); // 5
> But indices 0, 1, 2, and 3 are empty slots (holes), not actual values.
> forEach skips empty slots and only runs for existing elements.
```

---

### ❓ Problem 27

```js
// Problem
const name = "Nick";
age = 22; // window.age = 22; (Browser)

console.log(delete name); // false
console.log(delete age); // true
```

- delete can remove object properties but cannot remove variables declared with var, let, or const. Therefore delete name returns false, while delete age returns true because age becomes a property of the global object when assigned without a declaration in non-strict mode.
- Why?
  - name is a variable declaration, not an object property.
  - delete cannot remove variables declared with const, let, or var.
  - Without var, let, or const (in non-strict mode), JavaScript creates a property on the global object.

---

### ❓ Problem 28

```js
// Problem
var name = "Ratan";
function test() {
  console.log(name);
  var name = "Developer";
}
test(); // undefined
```

- Inside test(), the local var name is hoisted. Therefore, console.log(name) accesses the local variable before assignment, resulting in undefined instead of the global value.

---

### ❓ Problem 29

```js
// Problem
const arr = ["a", "b", "c"];
arr.length = 0;
console.log(arr[0]); // Clear existing array
console.log(arr.length); // Because both variables reference the same array object.

// Output: undefined 0
```

- arr.length = 0 is a fast way to clear an array while preserving its reference. It's commonly used in plain JavaScript, but in React state management, creating a new array is preferred.

---

### ❓ Problem 30

- output of the following code and why?

```js
console.log([] + []); // ""
// // [] -> "" // "" + "" -> ""

console.log(0.1 + 0.2); // 0.30000000000000004
// Small precision error

console.log(NaN === NaN); // false
// NaN is the only value in JavaScript that is not equal to itself. (Number.isNaN(NaN); // true)

console.log([] == false); // true
// [] -> "" // false -> 0 // "" -> 0 // 0 == 0

console.log(typeof null); // object
// This is a historical JavaScript bug kept for backward compatibility.
```

- JavaScript automatically converts values during comparisons and operations. Some well-known quirks include floating-point precision issues (0.1 + 0.2), NaN not being equal to itself, loose equality coercion (==), and typeof null returning "object" due to a legacy bug.

---

### ❓ Problem 31

- Why do var and let produce different outputs inside a setTimeout loop?

```js
// Problem
for (var i = 1; i <= 3; i++) {
  setTimeout(() => {
    console.log(i);
  }, 1000);
}
// Output: 4 4 4

// Fix
for (let i = 1; i <= 3; i++) {
  setTimeout(() => {
    console.log(i);
  }, 1000);
}
// Output: 1 2 3
// let > Block Scoped >  New i Created For Each Iteration
```

- In a loop, var creates a single shared variable for all iterations, so asynchronous callbacks see its final value. let creates a new binding for each iteration, allowing callbacks to access the correct value.
  - var is function-scoped, so all callbacks share the same variable. (One Shared Box)
  - let is block-scoped, so each loop iteration gets its own variable copy. (New Box Per Iteration)

- This is a classic closure + var + event loop interview question.
- let creates a new binding for each iteration
- var is function-scoped, so all callbacks share the same i variable.
  - After 1 Second > All Callbacks Access Same i > 4 4 4

---

### ❓ Problem 32

- How do you group users by role using reduce()?

```js
// Problem
const users = [
  { id: 1, name: "Ratan", role: "Admin" },
  { id: 2, name: "Rahul", role: "User" },
  { id: 3, name: "Priya", role: "User" },
  { id: 4, name: "Amit", role: "Manager" },
];

// Solution
const groupedUsers = users.reduce(
  (acc, user) => {
    if (user.role === "Admin") {
      acc.admins.push(user);
    } else if (user.role === "User") {
      acc.users.push(user);
    } else if (user.role === "Manager") {
      acc.managers.push(user);
    }

    return acc;
  },
  {
    // Initial Value (acc)
    admins: [],
    users: [],
    managers: [],
  },
);

console.log(groupedUsers);
```

---

### ❓ Problem 33

- convert an array into an object.

```js
// Problem
const array = [1, 2, 3, 4, 5];

// Solution
const result = { ...array };
console.log(result);
// Output:
// {
//   0: 1,
//   1: 2,
//   2: 3,
//   3: 4,
//   4: 5
// }
```

---

### ❓ Problem 34

```js
// Problem
console.log([] + []); // ""
console.log([] + {}); // "[object Object]"
console.log({} + []); // "[object Object]"
console.log({} + {}); // "[object Object][object Object]"
console.log({} == "[object Object]"); // true
```

- The + operator performs string concatenation if one of the operands becomes a string. Arrays and objects are first converted to primitive values using JavaScript's type coercion rules.
  - Empty Array + Empty Array ("" + "")
  - Empty Array + Empty Object ("" + "[object Object]")
  - Empty Object + Empty Array ("[object Object]" + "")
  - Empty Object + Empty Object ("[object Object]" + "[object Object]")

| Value       | `toString()` Result |
| ----------- | ------------------- |
| `[]`        | `""`                |
| `[1,2,3]`   | `"1,2,3"`           |
| `{}`        | `"[object Object]"` |
| `null`      | `"null"`            |
| `undefined` | `"undefined"`       |

- If I don't explicitly call toString(), why does JavaScript still convert arrays and objects to strings?
- You don't call toString(), JavaScript calls it for you when it needs a primitive value.

```js
// Explicit Conversion
console.log([1, 2, 3].toString());

// Implicit Conversion
console.log([1, 2, 3] + "");
```

```text
Object
 ↓
ToPrimitive()
 ↓
valueOf()
 ↓ (if not primitive)
toString()
 ↓
Primitive Value
```

---

### ❓ Problem 35

- Guess the Output & Why?

```js
// S1
async function getUser() {
  console.log("1");
  await fetch("/api/user");
  console.log("2");
}
getUser();
console.log("3");

// Output:
// 1
// 3
// 2

// S2
async function loadData() {
  console.log("Loading...");
  await new Promise((resolve) => setTimeout(resolve, 3000));
  console.log("Loaded");
}
loadData();
console.log("App Started");
// Output: (The app continues running while loadData() is paused.)
// Loading...
// App Started
// (wait 3 seconds)
// Loaded
```

- await only pauses the execution of the current async function. The JavaScript thread remains free to execute other code, events, and callbacks.
  - await Pause THIS function, Not the whole application
- **Steps:**
  - getUser() > console.log("1")
  - await fetch(...) > Pause getUser()
  - Main Thread Free > console.log("3")
  - API Response Received > Resume getUser()
  - console.log("2")

```js
// S3 (Without await)
function demo() {
  console.log("1");
  fetch("/api/users").then(() => {
    console.log("2");
  });
  console.log("3");
}
demo();

// Output: (Function NEVER pauses)
// 1 3 2

// S4 (With await)
async function demo() {
  console.log("1");
  await fetch("/api/users");
  console.log("2");
  console.log("3");
}
demo();

// Output:
// 1 2 3
```

---

### ❓ Problem 36

```js
// Problem
const arr = [1, 2, 3];
const str = "1,2,3";
console.log(arr == str); // true
```

- because == performs type coercion, and the array is converted to a string using toString().
- Array + String comparison > Array → toString() > [1,2,3] > "1,2,3"

---

### ❓ Problem 37

```js
// Problems
console.log(1 + 2 + "3"); // 33
console.log("1" + 2 + 3); // 123
console.log(1 + "2" + 3); // 123
```

- JavaScript evaluates (+) from left to right. Once a string is involved, subsequent (+) operations perform string concatenation instead of numeric addition.

---

### ❓ Problem 38

```js
// Problem
const x = (0 ?? 2) || 3;
console.log(x); // 3

// Realworld
const display = (stock ?? 0) || "Out of stock";
```

```js
console.log(0 || "Hello"); // Hello
console.log(0 ?? "Hello"); // 0

// x Falsy
// x Not null
// x Not undefined
// 0 is not null or undefined > return 0
```

- Whenever you mix ?? with || or &&, always add parentheses.

---

### ❓ Problem 39

- Comparison operators (<, >, <=, >=) are evaluated from left to right.
- The result of a comparison is a boolean (true or false), and when compared again with a number
  - true -> 1
  - false -> 0

```js
console.log(5 < 8 > 2); // False
// 5 < 8 = true
// true > 2
// 1 > 2 = false

console.log(1 > 19 < 2); // True
// 1 > 19 = false
// false < 2
// 0 < 2 = true

console.log(18 < false < 60); // True
```

---

### ❓ Problem 40

```js
// Problem
const arr = [];
let res = arr.every((x) => x > 0);
console.log(res); // true

// Internally
// for (const item of arr) {
//   if (!(item > 0)) {
//     return false;
//   }
// }
// return true;
// (Since the loop never runs)

[].every((x) => x > 0); // true (No element failed the condition)
[].some((x) => x > 0); // false (No element passed the condition)
```

- Array.prototype.every() returns true if every element satisfies the condition.
- there are no elements that violate the condition.

---

### ❓ Problem 41

```js
// Problem
const arr = [1, 21, 30, 4];
arr.sort();
console.log(arr); // [1, 21, 30, 4]

// Internally, JavaScript does this:
// [1, 21, 30, 4] > ["1", "21", "30", "4"]
// Then compares character by character: "1" < "21" < "30" < "4"
// Since "4" starts with '4', it comes after "30".

// Correct Way to Sort Numbers
const arr = [1, 21, 30, 4];
arr.sort((a, b) => a - b);
console.log(arr);
```

- By default, Array.prototype.sort() converts elements to strings and sorts them lexicographically (dictionary order), not numerically.
- sort() without a comparator sorts elements as strings (lexicographically). For numeric sorting, always provide a compare function like (a, b) => a - b.

---

### ❓ Problem 42

```js
// Syntax
const timerId = setTimeout((arg1, arg2) => {}, 1000, value1, value2);

// E1
setTimeout(
  (a, b) => {
    console.log(a + b);
  },
  0,
  1,
  2,
  37,
);
// 3 (a = 1, b = 2)

// E2
setTimeout(
  (a, b, c) => {
    console.log(a + b + c);
  },
  0,
  1,
  2,
  37,
); // 40 (a = 1, b = 2, c = 37)
```

- setTimeout supports additional arguments after the delay. They are passed to the callback in order, and any extra arguments are ignored if the callback doesn't declare corresponding parameters.

---

### ❓ Problem 43

```js
// Integer-like keys
const x = {
  2: "a",
  1: "b",
  3: "c",
};
console.log(Object.keys(x)); // [ '1', '2', '3' ]
console.log(Object.values(x)); // [ 'b', 'a', 'c' ]

// String Keys
const obj = {
  b: 1,
  a: 2,
  c: 3,
};
console.log(Object.keys(obj)); // ["b", "a", "c"]

// Mixed Example
const obj = {
  b: 1,
  2: "x",
  a: 2,
  1: "y",
};
console.log(Object.keys(obj)); // ["1", "2", "b", "a"]
// 1. Integer keys: "1", "2"
// 2. String keys: "b", "a"
```

- Object keys are always strings internally. If a key is an integer-like string (e.g., "1", "2"), JavaScript automatically orders it numerically. Otherwise, it follows insertion order.
- Object keys are actually strings.
  - For objects, JavaScript follows this property order:
    - Integer-like keys → ascending numeric order.
    - String keys → insertion order.
    - Symbol keys → insertion order.
  - If an object key is an integer-like string, JavaScript automatically orders it numerically.
    - These are considered the same: {2: "a"} | {"2": "a"}

```text
// Integer-like Key
"0"
"1"
"25"
"100"

// Not Integer-like
"01"
"001"
"1.5"
"-1"
"2a"
```

---

### ❓ Problem 44

```js
// Regular Funtion
const obj = {
  a: 10,
  f: function () {
    return this.a;
  },
};
console.log(obj.f()); // 10

// Arrow Funtion
const obj = {
  a: 10,
  f: () => this.a,
};
console.log(obj.f()); // undefined
```

- (this) inside a regular function depends on how the function is called.
  - here (this) refers to (obj) means this === obj
- This pattern is common in objects and classes.
- The arrow functions don't have their own this. They inherit this from the outer scope.

---

### ❓ Problem 45

```js
console.log(5 && 1); // 1 (Since all values are truthy, && returns the last operand.)
console.log(5 || 1); // 5 (|| immediately stops and returns the first truthy value.)

// More examples
console.log(0 && 5); // 0
console.log(0 || 5); // 5
console.log("Hi" && 10); // 10
console.log("" || "JS"); // "JS"

// Realworld
const name = userName || "Guest"; // || for Default Values
isLoggedIn && showDashboard(); // && for Conditional Execution
```

- && and || do not return true or false necessarily. They return one of the operands.
  - && returns the first falsy value, or the last value if all are truthy.
  - || returns the first truthy value, or the last value if all are falsy.

---

### ❓ Problem 46

```js
// Delete
let nums = [1, 2, 3, 4];
delete nums[2];
console.log(nums); // [ 1, 2, <1 empty item>, 4 ]
console.log(nums.length); // 4
console.log(nums[2]); // undefined

// Index 2 still exists conceptually, but its property was deleted.
// Index: 0  1  2  3
// Value: 1  2  _  4

// Splice
let nums = [1, 2, 3, 4];
nums.splice(2, 1);
console.log(nums); // [1, 2, 4]
console.log(nums.length); // 3
```

- delete removes the property from the array, but it does not remove the index or change the array length.
- It creates a hole (empty slot) in the array.
- Difference: delete vs splice:
  - delete is usually used with objects, not arrays.
  - splice Removes element and shifts items

---

### ❓ Problem 47

```js
// >>>>> Reference Types
var arrA = [0];
var arrB = arrA;
arrB[0] = 42;
console.log(arrA); // [ 42 ]
// arrA ─┐
//       ├──► [42]
// arrB ─┘

// >>>>> Primitive Types
let a = 10;
let b = a;
b = 20;
console.log(a); // 10
console.log(b); // 20

// >>>>> Creating a Real Copy
const arrA = [0];
const arrB = [...arrA];
arrB[0] = 42;
console.log(arrA); // [0]
console.log(arrB); // [42]

// React
const newUsers = [...users];
newUsers.push(user);
setUsers(newUsers);
// React relies heavily on creating new arrays/objects instead of mutating existing ones.
```

- Arrays and objects in JavaScript are reference types.
- you are not creating a copy of the array. Both variables point to the same array in memory.

| Type     | Assignment Copies |
| -------- | ----------------- |
| Number   | Value             |
| String   | Value             |
| Boolean  | Value             |
| Array    | Reference         |
| Object   | Reference         |
| Function | Reference         |

---

### ❓ Problem 48

```js
if ([]) {
  console.log(true);
} // true

console.log(Boolean([])); // true
console.log(Boolean({})); // true
console.log(Boolean("")); // false
console.log(Boolean(0)); // false
```

- An empty array ([]) is truthy in JavaScript. It may be empty, but it still exists.
- Because arrays are objects, and all objects are truthy in JavaScript.

---

### ❓ Problem 49

```js
console.log("2" > "10"); // true
console.log("2" > 10); // false

// '2' > '1' = true
// 2 > 10 = false
```

- If both operands are strings, JavaScript compares them lexicographically.
  - String vs String → Lexicographical (dictionary) comparison.
  - "2" starts with '2', "10" starts with '1'
- If one operand is a number, JavaScript converts the other to a number and performs a numeric comparison.
  - String vs Number → Converts the string to a number and performs numeric comparison.

---

### ❓ Problem 50

```js
let x = [20, 1, 3].sort();
console.log(x); // [1, 20, 3]

// [20, 1, 3] > ["20", "1", "3"] > "1" < "2" < "3"
```

- sort() without a compare function converts elements to strings and sorts them lexicographically (dictionary order).

---

### ❓ Problem

```js
// Problem

// Solution
```

---

### ❓ Problem

```js
// Problem

// Solution
```

---

### ❓ Problem

```js
// Problem

// Solution
```

---

### ❓ Problem

```js
// Problem

// Solution
```

---

### ❓ Problem

```js
// Problem

// Solution
```

---

### ❓ Problem

```js
// Problem

// Solution
```

---

### ❓ Problem

```js
// Problem

// Solution
```

---

### ❓ Problem

```js
// Problem

// Solution
```

---

### ❓ Problem

```js
// Problem

// Solution
```

---

### ❓ Problem

```js
// Problem

// Solution
```

---

### ❓ Problem

```js
// Problem

// Solution
```

---

### ❓ Problem

```js
// Problem

// Solution
```

---
