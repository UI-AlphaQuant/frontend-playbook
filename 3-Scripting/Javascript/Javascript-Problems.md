## 📌 Practical Problems

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

### ❓ Problem 7 TDZ

```js
console.log(a, b);
var a = 10;
let b = 100;

// Output:
// undefined
// ReferenceError: Cannot access 'b' before initialization
```

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

### ❓ Problem 12

```js
function abc(b, ...a) {
  console.log(a);
}
abc(8, 9, 10, 11, 12);
// Output: [9, 10, 11, 12]
```

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

### ❓ Problem

```js
// Problem

// Solution
```

### ❓ Problem

```js
// Problem

// Solution
```

### ❓ Problem

```js
// Problem

// Solution
```

### ❓ Problem

```js
// Problem

// Solution
```

### ❓ Problem

```js
// Problem

// Solution
```

### ❓ Problem

```js
// Problem

// Solution
```

---
