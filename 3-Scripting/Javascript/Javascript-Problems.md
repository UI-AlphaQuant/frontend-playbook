## 📌 Practical Problems

### Problem 1

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

### Problem 2

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

### Problem 3

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

### Problem 4

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

### Problem 5

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

### Problem 6

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

---
