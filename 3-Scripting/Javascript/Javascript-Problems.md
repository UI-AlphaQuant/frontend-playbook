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
