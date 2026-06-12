# 👉 Asynchronous JavaScript

## 📌 Sync vs Async

Synchronous code runs line-by-line, while asynchronous code runs without blocking execution.

| Type         | Details                            | Behavior     |
| ------------ | ---------------------------------- | ------------ |
| Synchronous  | Executes one task at a time        | Blocking     |
| Asynchronous | Executes tasks later/in background | Non-blocking |

### Synchronous

```js
console.log("1");
console.log("2");
console.log("3");
```

```txt
Output:
1
2
3
```

### Asynchronous

```js
console.log("1");

setTimeout(() => {
  console.log("2");
}, 1000);

console.log("3");
```

```txt
Output:
1
3
2
```

| Common Async APIs | Usage              |
| ----------------- | ------------------ |
| `setTimeout()`    | Delayed execution  |
| `setInterval()`   | Repeated execution |
| `fetch()`         | API requests       |
| Events            | User interactions  |

### Real-World Usage

| Sync                | Example              | Async             | Example            |
| ------------------- | -------------------- | ----------------- | ------------------ |
| Calculations        | `2 + 2`              | API Calls         | `fetch("/users")`  |
| Loops               | `for` loop execution | Timers            | `setTimeout()`     |
| Variable Operations | `let total = 10`     | Database Requests | Server query       |
| Simple Logic        | `if/else` conditions | File Uploads      | Upload image/file  |
| Array Methods       | `map()`, `filter()`  | User Events       | Button clicks      |
| Object Access       | `user.name`          | Realtime Data     | Chat notifications |
| Function Calls      | `sum()`              | Background Tasks  | Payment processing |

- JavaScript is single-threaded
- Async prevents UI blocking
- Core concept for APIs and frontend apps

---

## 📌 Callbacks

A callback is a function passed into another function to execute later.

| Type                  | Details                      | Common Examples                                                         |
| --------------------- | ---------------------------- | ----------------------------------------------------------------------- |
| Callback Function     | Passed into another function | `fn(callback)`                                                          |
| Synchronous Callback  | Runs immediately             | `forEach()`, `map()`, `filter()`, `reduce()`, `sort()`                  |
| Asynchronous Callback | Runs later                   | `setTimeout()`, `setInterval()`, `fetch().then()`, `addEventListener()` |

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
// Async Callback
setTimeout(() => {
  console.log("Done");
}, 1000);
```

```js
// Array Callback
const nums = [1, 2, 3];

nums.map((num) => num * 2);
```

```js
// Event Callback
button.addEventListener("click", () => {
  console.log("Clicked");
});
```

| Real-World Usage | Example                          |
| ---------------- | -------------------------------- |
| Buttons          | Click handling                   |
| Forms            | Validation                       |
| API Requests     | Handle response data             |
| Timers           | Delayed actions                  |
| Arrays           | `map()`, `filter()`, `forEach()` |

### Callback Hell ❌

```js
login(() => {
  getUser(() => {
    getPosts(() => {
      console.log("Done");
    });
  });
});
```

Too many nested callbacks become hard to manage.

- Common in async JavaScript
- Widely used in events, APIs, and array methods
- Promises/async-await help avoid callback hell

---

## 📌 Promises

A Promise handles asynchronous operations and future results.

| State       | Details               |
| ----------- | --------------------- |
| `pending`   | Initial waiting state |
| `fulfilled` | Operation successful  |
| `rejected`  | Operation failed      |

```js
// Syntax
const promise = new Promise((resolve, reject) => {
  // async work
});
```

| Promise Methods  | Purpose                 | Example             |
| ---------------- | ----------------------- | ------------------- |
| `.then()`        | Handle success          | `promise.then()`    |
| `.catch()`       | Handle errors           | `promise.catch()`   |
| `.finally()`     | Runs always             | `promise.finally()` |
| `Promise.all()`  | Run multiple promises   | `Promise.all([])`   |
| `Promise.race()` | First completed promise | `Promise.race([])`  |

```js
// Create Promise
const promise = new Promise((resolve, reject) => {
  resolve("Success");
});

// Handle Success
promise.then((data) => {
  console.log(data);
});

// Handle Error
promise.catch((err) => {
  console.log(err);
});

// Finally
promise.finally(() => {
  console.log("Done");
});

// Promise.all()
Promise.all([p1, p2]).then((data) => {
  console.log(data);
});
```

### Promise Flow

```txt
Pending
  ↓
Fulfilled → .then()
Rejected  → .catch()
```

| Real-World Usage  | Example         |
| ----------------- | --------------- |
| API Calls         | `fetch()`       |
| Database Requests | Server data     |
| File Uploads      | Upload handling |
| Parallel Requests | Multiple APIs   |

- Solves callback hell problem
- Used heavily with APIs and async tasks
- Foundation for `async/await`

### Example

```js
const foodOrder = new Promise((resolve, reject) => {
  const delivered = true;

  setTimeout(() => {
    if (delivered) {
      resolve("Food Delivered");
    } else {
      reject("Order Cancelled");
    }
  }, 2000);
});

foodOrder
  .then((result) => console.log(result))
  .catch((error) => console.log(error));
```

```txt
Promise Created
↓
Pending
↓
resolve() called → Fulfilled → .then()
OR
reject() called → Rejected → .catch()

// Flow
Order Placed     → Pending
Food Delivered   → Fulfilled → then()
Order Cancelled  → Rejected  → catch()
```

- A Promise starts as Pending and eventually settles into either Fulfilled (resolve) or Rejected (reject), which are handled using .then() and .catch().
- 2000 is just a simulated delay to mimic an asynchronous operation such as an API request. It is not required for Promises.

---

## 📌 Async / Await

`async/await` provides cleaner syntax for working with Promises.

| Keyword       | Details                       | Example            |
| ------------- | ----------------------------- | ------------------ |
| `async`       | Makes function return Promise | `async function()` |
| `await`       | Waits for Promise result      | `await fetch()`    |
| `try...catch` | Handles async errors          | `try {}`           |

```js
// Async Function
async function test() {
  return "Hello";
}

// Await Promise
async function getData() {
  const res = await fetch("/users");

  console.log(res);
}

// Error Handling
async function loadData() {
  try {
    const data = await fetch("/api");
  } catch (err) {
    console.log(err);
  }
}

// Multiple Requests
const [users, posts] = await Promise.all([fetch("/users"), fetch("/posts")]);
```

### Promise vs Async/Await

| Promise           | Async/Await                     |
| ----------------- | ------------------------------- |
| `.then().catch()` | Cleaner synchronous-like syntax |
| More chaining     | Easier to read/manage           |

| Real-World Usage | Example                 |
| ---------------- | ----------------------- |
| API Calls        | Fetch user/product data |
| Authentication   | Login/signup            |
| File Uploads     | Upload images/files     |
| Dashboard Data   | Load multiple APIs      |

- Built on top of Promises
- Makes async code easier to read
- `await` works only inside `async` functions

---

## 📌 Fetch API

Fetch API is used to make HTTP requests in JavaScript.

| Method     | Purpose                  | Example         |
| ---------- | ------------------------ | --------------- |
| `fetch()`  | Send HTTP request        | `fetch("/api")` |
| `.json()`  | Convert response to JSON | `res.json()`    |
| `.then()`  | Handle success           | `.then(data)`   |
| `.catch()` | Handle errors            | `.catch(err)`   |

### GET Request

```js
fetch("/users")
  .then((res) => res.json())
  .then((data) => {
    console.log(data);
  });
```

### Async/Await

```js
async function getUsers() {
  const res = await fetch("/users");

  const data = await res.json();

  console.log(data);
}
```

### POST Request

```js
fetch("/users", {
  method: "POST",

  headers: {
    "Content-Type": "application/json",
  },

  body: JSON.stringify({
    name: "John",
  }),
});
```

```js
// Error Handling
fetch("/users").catch((err) => {
  console.log(err);
});
```

```js
// Check Response Status
fetch("/users")
  .then((res) => {
    if (!res.ok) {
      throw new Error("Request Failed");
    }

    return res.json();
  })
  .then((data) => {
    console.log(data);
  })
  .catch((err) => {
    console.log(err);
  })
  .finally(() => {
    console.log("Completed");
  });
```

| Common HTTP Methods | Usage          |
| ------------------- | -------------- |
| `GET`               | Retrieve data  |
| `POST`              | Create data    |
| `PUT`               | Update data    |
| `PATCH`             | Partial update |
| `DELETE`            | Remove data    |

| Real-World Usage | Example              |
| ---------------- | -------------------- |
| API Calls        | Fetch products/users |
| Forms            | Submit data          |
| Authentication   | Login/signup         |
| Dashboards       | Load dynamic content |

- Returns a Promise
- Commonly used with `async/await`
- Modern replacement for `XMLHttpRequest`

| Property / API    | Purpose                      |
| ----------------- | ---------------------------- |
| `res.ok`          | Check successful response    |
| `res.status`      | HTTP status code             |
| `headers`         | Send request headers         |
| `finally()`       | Runs after request completes |
| `AbortController` | Cancel request               |

### Realistic Fetch API Example

```js
const form = document.querySelector("form");
const loader = document.querySelector(".loader");
const result = document.querySelector(".result");

form.addEventListener("submit", async (e) => {
  e.preventDefault();

  loader.style.display = "block";

  try {
    const res = await fetch("/api/login", {
      method: "POST",

      headers: {
        "Content-Type": "application/json",
      },

      body: JSON.stringify({
        email: "john@mail.com",
        password: "123456",
      }),
    });

    if (!res.ok) {
      throw new Error("Login Failed");
    }

    const data = await res.json();

    result.textContent = data.message;
  } catch (err) {
    result.textContent = err.message;
  } finally {
    loader.style.display = "none";
  }
});
```

### Common HTTP Status Codes

```text
DevTools → Network

- Request URL
- Method
- Headers
- Payload
- Status Code
- Response Data
```

| Status Code    | Meaning                | Common Cause                               |
| -------------- | ---------------------- | ------------------------------------------ |
| 200            | Success                | Request completed successfully             |
| 201            | Created                | New resource created successfully          |
| 400            | Bad Request            | Invalid request body/query/params          |
| 401            | Unauthorized           | Missing or invalid token/login             |
| 403            | Forbidden              | No permission/access denied                |
| 404            | Not Found              | Wrong endpoint/resource not found          |
| 500            | Server Error           | Backend/server crash or unhandled error    |
| CORS Error     | Cross-Origin Blocked   | Backend CORS restriction/policy issue      |
| Undefined Data | Invalid Response Data  | Wrong response structure/property access   |
| Failed Fetch   | Network Request Failed | Internet issue/server down/request blocked |

- Debug API Response

```js
console.log(response);
console.table(response);

// Debug Fetch Errors
catch (error) {
  console.error(error);
}

// Check Request Payload
console.log(JSON.stringify(data));
```

### Best Practice

```js
// Add Token Automatically
headers: {
  "Content-Type": "application/json",
  Authorization: `Bearer ${token}`,
}

// Async Await Best Practice
try {
  const data = await api();
} catch (error) {
  console.error(error);
}

// Loading State Best Practice (Always use finally)
finally {
  hideLoader();
}
```

### Real-World Production Improvements

| Feature             | Why                       | Standard Example                               |
| ------------------- | ------------------------- | ---------------------------------------------- |
| Retry Logic         | Handle temporary failures | Retry API 2-3 times for network/500 errors     |
| Request Timeout     | Prevent infinite waiting  | Abort request after 5s using `AbortController` |
| Debounce Search API | Reduce API calls          | Wait 300ms before search request               |
| Pagination          | Large data handling       | `?page=1&limit=10`                             |
| Caching             | Better performance        | Store API data in memory/localStorage          |
| AbortController     | Cancel old requests       | Cancel previous search request on typing       |
| Refresh Token       | Auto re-login             | Generate new access token automatically        |
| Environment Config  | Multiple servers          | DEV/STAGING/PROD base URLs                     |

---

## 📌 Event Loop

Event Loop manages execution of synchronous and asynchronous JavaScript tasks.

| Part            | Details                         | Examples                              |
| --------------- | ------------------------------- | ------------------------------------- |
| Call Stack      | Executes functions              | `sum()`, `console.log()`              |
| Web APIs        | Browser async features          | `setTimeout()`, `fetch()`, DOM events |
| Callback Queue  | Stores async callbacks          | `setTimeout(callback)`                |
| Event Loop      | Moves tasks when stack is empty | Handles async execution flow          |
| Microtask Queue | High-priority async tasks       | `Promise.then()`, `queueMicrotask()`  |

### Execution Flow

```txt
Call Stack
   ↓
Web APIs
   ↓
Callback Queue / Microtask Queue
   ↓
Event Loop
   ↓
Call Stack
```

### Example

```js
console.log("1");

setTimeout(() => {
  console.log("2");
}, 0);

Promise.resolve().then(() => {
  console.log("3");
});

console.log("4");
```

```txt
Output:
1
4
3
2
```

### Why Output?

| Task             | Queue           |
| ---------------- | --------------- |
| `console.log()`  | Call Stack      |
| `Promise.then()` | Microtask Queue |
| `setTimeout()`   | Callback Queue  |

Microtasks run before callback queue tasks.

| Real-World Usage | Example            |
| ---------------- | ------------------ |
| API Handling     | Promises/fetch     |
| Timers           | `setTimeout()`     |
| UI Updates       | Async rendering    |
| User Events      | Click/input events |

- JavaScript is single-threaded
- Event loop enables non-blocking behavior
- Microtasks have higher priority than callbacks

---

## 📌 Microtasks & Macrotasks

- JavaScript prioritizes async tasks using Microtask and Macrotask queues.
- Microtasks always run before macrotasks.

| Type       | Details                   | Examples                             |
| ---------- | ------------------------- | ------------------------------------ |
| Microtasks | High-priority async tasks | `Promise.then()`, `queueMicrotask()` |
| Macrotasks | Regular async tasks       | `setTimeout()`, `setInterval()`      |

### Execution Priority

```txt
Call Stack
   ↓
Microtasks
   ↓
Macrotasks
```

```js
console.log("1");

setTimeout(() => {
  console.log("2");
}, 0);

Promise.resolve().then(() => {
  console.log("3");
});

console.log("4");
```

```txt
Output:
1
4
3
2
```

### Why Output?

| Code             | Queue           |
| ---------------- | --------------- |
| `console.log()`  | Call Stack      |
| `Promise.then()` | Microtask Queue |
| `setTimeout()`   | Macrotask Queue |

### Real-World Usage

| Microtasks       | Macrotasks        |
| ---------------- | ----------------- |
| Promise handling | Timers            |
| Async/await      | DOM events        |
| Queue updates    | Network callbacks |

- Microtasks run before macrotasks
- Promises use microtask queue
- Important for async execution order

---

## 📌 AJAX

AJAX (Asynchronous JavaScript and XML) updates webpage data without full page reload.

| Feature        | Details                 | Example       |
| -------------- | ----------------------- | ------------- |
| Async Requests | Load data in background | API calls     |
| No Page Reload | Update UI dynamically   | Search/filter |
| Data Formats   | Usually JSON            | `res.json()`  |
| HTTP Requests  | Communicate with server | `GET`, `POST` |

### Modern AJAX (`fetch`)

```js
fetch("/users")
  .then((res) => res.json())
  .then((data) => {
    console.log(data);
  });
```

### Async/Await Example

```js
async function getUsers() {
  const res = await fetch("/users");

  const data = await res.json();

  console.log(data);
}
```

### Old AJAX (`XMLHttpRequest`) ❌

```js
const xhr = new XMLHttpRequest();

xhr.open("GET", "/users");

xhr.onload = () => {
  console.log(xhr.responseText);
};

xhr.send();
```

| Real-World Usage | Example               |
| ---------------- | --------------------- |
| Live Search      | Search suggestions    |
| Forms            | Submit without reload |
| Dashboards       | Load dynamic data     |
| Notifications    | Realtime updates      |

### AJAX Flow

```txt
Browser
   ↓
Server Request
   ↓
Server Response
   ↓
Update UI
```

- Modern apps mainly use `fetch()`
- `XMLHttpRequest` is older approach
- Core concept for dynamic web apps

---

# 👉 Browser APIs

- Browser APIs are built-in features provided by the browser for JavaScript.
- Browser APIs are not part of core JavaScript

| API              | Purpose                | Example                            |
| ---------------- | ---------------------- | ---------------------------------- |
| DOM API          | Manipulate webpage     | `document.querySelector()`         |
| Events API       | Handle events          | `addEventListener()`               |
| Fetch API        | HTTP requests          | `fetch()`                          |
| Storage API      | Store browser data     | `localStorage`                     |
| Geolocation API  | Access user location   | `navigator.geolocation`            |
| History API      | Browser navigation     | `history.pushState()`              |
| Clipboard API    | Copy/read clipboard    | `navigator.clipboard`              |
| Timer API        | Delayed/repeated tasks | `setTimeout()`                     |
| WebSocket API    | Realtime communication | `new WebSocket()`                  |
| Notification API | Browser notifications  | `Notification.requestPermission()` |

| JavaScript          | Browser APIs                 |
| ------------------- | ---------------------------- |
| Core language       | Browser-provided features    |
| ECMAScript standard | Browser environment features |
| Works everywhere    | Mainly browser environment   |

## 📌 LocalStorage

`localStorage` stores data in the browser permanently until manually removed.

| Method         | Details              | Example                     |
| -------------- | -------------------- | --------------------------- |
| `setItem()`    | Save data            | `localStorage.setItem()`    |
| `getItem()`    | Get data             | `localStorage.getItem()`    |
| `removeItem()` | Remove specific item | `localStorage.removeItem()` |
| `clear()`      | Remove all data      | `localStorage.clear()`      |

### Usage Examples

```js
// Save Data
localStorage.setItem("theme", "dark");

// Get Data
const theme = localStorage.getItem("theme");

// Remove Data
localStorage.removeItem("theme");

// Clear All
localStorage.clear();
```

### Store Objects/Arrays

```js
// Save Object
localStorage.setItem(
  "user",
  JSON.stringify({
    name: "John",
  }),
);
```

```js
// Get Object
const user = JSON.parse(localStorage.getItem("user"));
```

| Real-World Usage | Example                  |
| ---------------- | ------------------------ |
| Theme Preference | Dark/light mode          |
| Authentication   | Store tokens _(careful)_ |
| Cart Data        | Save cart items          |
| Form Persistence | Save draft data          |

### Storage Features

| Feature    | Details                       |
| ---------- | ----------------------------- |
| Persistent | Data survives refresh/restart |
| Size Limit | Around 5MB                    |
| Data Type  | Stores strings only           |

- Data stored as strings
- Use `JSON.stringify()` for objects
- Shared across same domain/browser

### sessionStorage vs localStorage

| Feature             | `sessionStorage`        | `localStorage`                  |
| ------------------- | ----------------------- | ------------------------------- |
| Lifetime            | Removed when tab closes | Persists until manually removed |
| Scope               | Per browser tab         | Shared across same origin       |
| Storage Limit       | ~5MB                    | ~5MB                            |
| Persistence         | Temporary               | Permanent                       |
| Shared Between Tabs | ❌ No                   | ✅ Yes                          |

| Method         | Syntax                               | Purpose            |
| -------------- | ------------------------------------ | ------------------ |
| `setItem()`    | `localStorage.setItem("key", value)` | Save Data          |
| `getItem()`    | `localStorage.getItem("key")`        | Read Data          |
| `removeItem()` | `localStorage.removeItem("key")`     | Delete One Item    |
| `clear()`      | `localStorage.clear()`               | Delete Everything  |
| `key()`        | `localStorage.key(index)`            | Get Key By Index   |
| `length`       | `localStorage.length`                | Total Stored Items |

| Task          | Code                                    |
| ------------- | --------------------------------------- |
| Save String   | `setItem("theme", "dark")`              |
| Read String   | `getItem("theme")`                      |
| Save Object   | `setItem("user", JSON.stringify(user))` |
| Read Object   | `JSON.parse(getItem("user"))`           |
| Delete Key    | `removeItem("user")`                    |
| Clear Storage | `clear()`                               |

```js
// localStorage
localStorage.setItem("theme", "dark");

// sessionStorage
sessionStorage.setItem("username", "Nick");
```

| `sessionStorage`     | `localStorage`    |
| -------------------- | ----------------- |
| OTP/session steps    | Theme preference  |
| Temporary form data  | Cart persistence  |
| One-tab workflow     | Remember settings |
| Payment/session flow | User preferences  |

- Both store strings only
- Use `JSON.stringify()` for objects
- Both are browser-only storage APIs

---

## 📌 Cookies

- Cookies store small pieces of data in the browser.
  - Cookie: Can be accessed by both the browser and JavaScript.
  - HttpOnly Cookie: Can be accessed only by the browser and server; JavaScript cannot read it.

| Feature                        | Description                 |
| ------------------------------ | --------------------------- |
| Purpose                        | Store Small Data In Browser |
| Size Limit                     | ~4 KB Per Cookie            |
| Sent To Server                 | ✅ Automatically            |
| Expiration                     | Configurable                |
| Shared Across Tabs             | ✅                          |
| Persists After Browser Restart | ✅ (if expiry set)          |

| Operation | Syntax                                                              | Purpose         |
| --------- | ------------------------------------------------------------------- | --------------- |
| Create    | `document.cookie = "theme=dark"`                                    | Save Cookie     |
| Read All  | `document.cookie`                                                   | Get All Cookies |
| Update    | `document.cookie = "theme=light"`                                   | Update Cookie   |
| Delete    | `document.cookie = "theme=; expires=Thu, 01 Jan 1970 00:00:00 UTC"` | Delete Cookie   |

### Cookie Attributes

| Attribute  | Purpose             |
| ---------- | ------------------- |
| `expires`  | Expiration Date     |
| `max-age`  | Lifetime In Seconds |
| `path`     | Available URL Path  |
| `domain`   | Available Domain    |
| `secure`   | HTTPS Only          |
| `SameSite` | CSRF Protection     |
| `HttpOnly` | JS Cannot Access    |

```js
document.cookie = "theme=dark"; // Set Cookie
document.cookie = "user=John; expires=Fri, 31 Dec 2027 12:00:00 UTC"; // Set Expiry
console.log(document.cookie); // Read Cookies
document.cookie = "theme=; expires=Thu, 01 Jan 1970 00:00:00 UTC"; // Delete Cookie

// Regular Cookie (JavaScript can read it.)
// http: Set-Cookie: username=Rao
Set-Cookie: username=Rao

// HttpOnly Cookie (refreshToken not visible)
// http: Set-Cookie: refreshToken=xyz123; HttpOnly
console.log(document.cookie);
```

### Common Cookie Options

| Option     | Purpose              | Example                                 |
| ---------- | -------------------- | --------------------------------------- |
| `expires`  | Expiration date      | `expires=Fri, 31 Dec 2027 12:00:00 UTC` |
| `max-age`  | Expire after seconds | `max-age=3600`                          |
| `path`     | Cookie path access   | `path=/admin`                           |
| `secure`   | HTTPS only           | `secure`                                |
| `SameSite` | CSRF protection      | `SameSite=Strict`                       |

### Storage Use Cases

| Use Case             | Recommended     |
| -------------------- | --------------- |
| Authentication Token | HttpOnly Cookie |
| Session ID           | Cookie          |
| Theme Preference     | localStorage    |
| Language Preference  | localStorage    |
| Temporary Form Data  | sessionStorage  |

### Cookies vs LocalStorage

| Cookies              | LocalStorage             |
| -------------------- | ------------------------ |
| Sent to server       | Browser only             |
| Small storage (~4KB) | Larger storage (~5MB)    |
| Supports expiration  | Persistent until removed |

- Commonly used for sessions/auth
- Sent automatically with requests
- Use secure/SameSite options for security

---

## 📌 Clipboard API

Clipboard API allows copying and reading clipboard data.

| Method        | Details                | Example                           |
| ------------- | ---------------------- | --------------------------------- |
| `writeText()` | Copy text to clipboard | `navigator.clipboard.writeText()` |
| `readText()`  | Read clipboard text    | `navigator.clipboard.readText()`  |

```js
// Copy Text
navigator.clipboard.writeText("Hello");

// Copy Input Value
button.addEventListener("click", () => {
  navigator.clipboard.writeText(input.value);
});

// Read Clipboard Text
navigator.clipboard.readText().then((text) => {
  console.log(text);
});

// Async/Await
async function copyText() {
  await navigator.clipboard.writeText("Copied");
}
```

| Real-World Usage | Example            |
| ---------------- | ------------------ |
| Copy Buttons     | Coupon/code copy   |
| Share Links      | Copy URL           |
| OTP/Forms        | Paste values       |
| Editors          | Copy/paste content |

### Important Notes

| Item            | Details                       |
| --------------- | ----------------------------- |
| Browser Support | Modern browsers               |
| HTTPS Required  | Usually required              |
| User Action     | Often needs click interaction |

- Modern replacement for older copy methods
- Works asynchronously using Promises
- Common in modern frontend apps

---

## 📌 Geolocation API

Geolocation API provides the user's current location.

| Method                 | Details                     | Example                                      |
| ---------------------- | --------------------------- | -------------------------------------------- |
| `getCurrentPosition()` | Get current location once   | `navigator.geolocation.getCurrentPosition()` |
| `watchPosition()`      | Track live location updates | `navigator.geolocation.watchPosition()`      |
| `clearWatch()`         | Stop location tracking      | `navigator.geolocation.clearWatch()`         |

```js
// Get Current Location
navigator.geolocation.getCurrentPosition((position) => {
  console.log(position.coords.latitude);
  console.log(position.coords.longitude);
});

// Watch Live Location
const id = navigator.geolocation.watchPosition((position) => {
  console.log(position.coords.latitude);
});

// Stop Watching
navigator.geolocation.clearWatch(id);

// Error Handling
navigator.geolocation.getCurrentPosition(
  (position) => {
    console.log(position);
  },
  (error) => {
    console.log(error.message);
  },
);
```

### Common Position Properties

| Property    | Details           |
| ----------- | ----------------- |
| `latitude`  | Latitude value    |
| `longitude` | Longitude value   |
| `accuracy`  | Location accuracy |
| `speed`     | Movement speed    |

| Real-World Usage | Example                |
| ---------------- | ---------------------- |
| Maps             | User location          |
| Delivery Apps    | Live tracking          |
| Nearby Search    | Find nearby places     |
| Weather Apps     | Location-based weather |

| Important Notes     | Details                  |
| ------------------- | ------------------------ |
| Permission Required | User must allow location |
| HTTPS Required      | Usually required         |
| Accuracy            | Depends on device/GPS    |

| Common Errors        | Meaning               |
| -------------------- | --------------------- |
| Permission Denied    | User blocked location |
| Position Unavailable | Location unavailable  |
| Timeout              | Request took too long |

- Works in modern browsers
- Requires user permission
- Common in maps and tracking apps

---

## 📌 History API

History API allows navigation and URL updates without page reload.

| Method           | Details                       | Example                  |
| ---------------- | ----------------------------- | ------------------------ |
| `back()`         | Go to previous page           | `history.back()`         |
| `forward()`      | Go to next page               | `history.forward()`      |
| `go()`           | Move specific history steps   | `history.go(-1)`         |
| `pushState()`    | Add new history entry         | `history.pushState()`    |
| `replaceState()` | Replace current history entry | `history.replaceState()` |

```js
// Go Back
history.back();
```

```js
// Go Forward
history.forward();
```

```js
// Go Specific Steps
history.go(-1);
```

```js
// Change URL Without Reload
history.pushState({}, "", "/about");
```

```js
// Replace Current URL
history.replaceState({}, "", "/profile");
```

```js
// Listen Route Changes
window.addEventListener("popstate", () => {
  console.log(location.pathname);
});
```

| Real-World Usage   | Example              |
| ------------------ | -------------------- |
| SPA Routing        | React/Vue routing    |
| Browser Navigation | Back/forward buttons |
| Dynamic URLs       | Filter/search pages  |
| Modals/Tabs        | URL state updates    |

| Important Notes  | Details                 |
| ---------------- | ----------------------- |
| No Page Reload   | URL changes dynamically |
| Same-Origin Only | Cannot change domain    |
| Common in SPAs   | Client-side routing     |

- Core API behind frontend routers
- Widely used in SPA applications
- Works with browser navigation history

---

## 📌 Web Workers

Web Workers run JavaScript in background threads without blocking the UI.

| Feature           | Details                          | Example               |
| ----------------- | -------------------------------- | --------------------- |
| Background Thread | Runs separately from main thread | Heavy calculations    |
| Non-Blocking      | Keeps UI responsive              | Large data processing |
| Message-Based     | Communicates using messages      | `postMessage()`       |
| Separate Context  | No direct DOM access             | Worker file           |

```js
// Create Worker
// main.js
const worker = new Worker("worker.js");
```

```js
// Send Data
worker.postMessage("Hello Worker");
```

```js
// Receive Data
worker.onmessage = (e) => {
  console.log(e.data);
};
```

```js
// Worker File
// worker.js
onmessage = (e) => {
  postMessage("Received: " + e.data);
};
```

```js
// Stop Worker
worker.terminate();
```

| Domain/System          | Web Worker Usage            |
| ---------------------- | --------------------------- |
| Image Editors          | Resize/compress images      |
| Video Editors          | Video processing/rendering  |
| Trading Dashboards     | Heavy chart calculations    |
| Analytics Systems      | Large data computation      |
| Maps/GIS Apps          | Coordinate calculations     |
| AI/ML Apps             | Background model processing |
| Realtime Collaboration | Background sync             |
| Games                  | Physics/game calculations   |
| PDF/Document Tools     | Generate/process PDFs       |
| Ecommerce              | Product filtering/sorting   |

| Important Notes | Details                  |
| --------------- | ------------------------ |
| No DOM Access   | Cannot use `document`    |
| Separate File   | Usually external JS file |
| Communication   | Uses `postMessage()`     |

- Prevents UI freezing
- Useful for CPU-heavy tasks
- Runs parallel to main thread

---

## 📌 Intersection Observer

Intersection Observer detects when elements enter or leave the viewport.

| Feature            | Details                   | Example               |
| ------------------ | ------------------------- | --------------------- |
| Viewport Detection | Detect visible elements   | Scroll animations     |
| Lazy Loading       | Load content when visible | Images/videos         |
| Infinite Scroll    | Detect page end           | Load more data        |
| Efficient          | Better than scroll events | Performance optimized |

```js
// Create Observer
const observer = new IntersectionObserver((entries) => {
  entries.forEach((entry) => {
    console.log(entry.isIntersecting);
  });
});

// Observe Element
const box = document.querySelector(".box");
observer.observe(box);

// Stop Observing
observer.unobserve(box);
```

| Real-World Usage  | Example               |
| ----------------- | --------------------- |
| Lazy Loading      | Images/videos         |
| Infinite Scroll   | Load more posts       |
| Scroll Animations | Fade/slide effects    |
| Analytics         | Track viewed sections |

### Important Entry Properties

| Property                  | Details                |
| ------------------------- | ---------------------- |
| `entry.isIntersecting`    | Element visible or not |
| `entry.target`            | Observed element       |
| `entry.intersectionRatio` | Visibility percentage  |

```js
const observer = new IntersectionObserver(callback, {
  threshold: 0.5,
});
```

| Common Options | Purpose                 |
| -------------- | ----------------------- |
| `root`         | Custom scroll container |
| `rootMargin`   | Extra detection margin  |
| `threshold`    | Visibility percentage   |

- Modern replacement for many scroll listeners
- Improves scroll performance
- Common in lazy loading and infinite scrolling

---

## 📌 Mutation Observer

Mutation Observer watches for DOM changes dynamically.

| Feature              | Details                         | Example               |
| -------------------- | ------------------------------- | --------------------- |
| DOM Change Detection | Detect added/removed elements   | Dynamic UI            |
| Attribute Watching   | Detect attribute changes        | Class/style updates   |
| Content Monitoring   | Watch text/content changes      | Live updates          |
| Efficient            | Better than old mutation events | Performance optimized |

```js
// Create Observer
const observer = new MutationObserver((mutations) => {
  console.log(mutations);
});

// Observe Element
const box = document.querySelector(".box");

observer.observe(box, {
  childList: true,
  attributes: true,
  subtree: true,
});

// Stop Observer
observer.disconnect();
```

| Common Options  | Purpose                      |
| --------------- | ---------------------------- |
| `childList`     | Watch added/removed children |
| `attributes`    | Watch attribute changes      |
| `subtree`       | Watch nested elements        |
| `characterData` | Watch text changes           |

```js
// Detect Class Change
observer.observe(box, {
  attributes: true,
});

// Detect Added Elements
observer.observe(list, {
  childList: true,
});
```

| Real-World Usage    | Example                | Real App/System        |
| ------------------- | ---------------------- | ---------------------- |
| Dynamic UI          | Detect new elements    | React/Vue dashboards   |
| Third-Party Widgets | Watch injected DOM     | Chat/support widgets   |
| Live Editors        | Detect content changes | Google Docs/Notion     |
| Analytics           | Track DOM interactions | Heatmaps/user tracking |

- Watches DOM changes automatically
- Useful in dynamic applications
- Modern replacement for deprecated mutation events

| ❗ Deprecated Event        | Purpose                 |
| -------------------------- | ----------------------- |
| `DOMNodeInserted`          | Detect added elements   |
| `DOMNodeRemoved`           | Detect removed elements |
| `DOMSubtreeModified`       | Detect subtree changes  |
| `DOMCharacterDataModified` | Detect text changes     |

---

## 📌 REST (Representational State Transfer)

- API > Application Programming Interface
- REST > Representational State Transfer
- URI > Uniform Resource Identifier

| Item               | Description                   |
| ------------------ | ----------------------------- |
| Purpose            | Standard Way To Design APIs   |
| Uses               | HTTP Protocol                 |
| Data Format        | Usually JSON                  |
| Architecture Style | Client ↔ Server Communication |

```txt
Frontend
↓
HTTP Request
↓
REST API
↓
Database
↓
JSON Response
↓
Frontend
```

- Resource-Based URLs

```txt
/users
/products
/orders
/payments
```

### CRUD Mapping

| Operation | HTTP Method | Endpoint   |
| --------- | ----------- | ---------- |
| Create    | POST        | `/users`   |
| Read All  | GET         | `/users`   |
| Read One  | GET         | `/users/1` |
| Update    | PUT/PATCH   | `/users/1` |
| Delete    | DELETE      | `/users/1` |

```json
// Response:
[
  {
    "id": 1,
    "name": "John"
  }
]
```

```ts
// React Example
fetch("/users");
axios.get("/users");
apiClient("/users");
```

## API Versioning

| Purpose         | Manage API Changes Without Breaking Existing Clients |
| --------------- | ---------------------------------------------------- |
| Common Versions | v1, v2, v3                                           |
| Used By         | Public APIs & Enterprise APIs                        |

```http
GET /api/v1/users
GET /api/v2/users
```

```http
GET https://api.company.com/api/v1/users
GET https://api.company.com/api/v2/users
```

---

## 📌 JSON (JavaScript Object Notation)

- JSON is a lightweight key-value data format used for exchanging data between frontend applications, APIs, and backend systems.

| Item        | Description                   |
| ----------- | ----------------------------- |
| Full Form   | JavaScript Object Notation    |
| Purpose     | Data Exchange Format          |
| Used In     | APIs, Config Files, Databases |
| Format      | Key-Value Pairs               |
| Readable By | Humans & Machines             |

- Keys Must Be In Double Quotes
- No Functions
- No Comments

```json
{
  "name": "John",
  "age": 25
}
```

### JSON Data Types

| Type    | Example  |
| ------- | -------- |
| String  | `"John"` |
| Number  | `25`     |
| Boolean | `true`   |
| Null    | `null`   |
| Array   | `[]`     |
| Object  | `{}`     |

```js
const data = {
  name: "John",
  age: 25,
  isAdmin: true,
  salary: null,

  skills: ["React", "TypeScript"],

  address: {
    city: "London",
  },
};
```

### Nested Object

```json
{
  "user": {
    "id": 1,
    "profile": {
      "city": "London",
      "country": "UK"
    }
  }
}
```

### Array Of Objects

```json
{
  "users": [
    {
      "id": 1,
      "name": "John"
    },
    {
      "id": 2,
      "name": "Jane"
    }
  ]
}
```

### Real API Response

```json
// Users Fetched
{
  "success": true,
  "message": "Users fetched successfully",
  "data": [
    {
      "id": 1,
      "name": "John",
      "email": "john@test.com"
    }
  ]
}

// Search + Pagination Response
{
  "page": 1,
  "limit": 10,
  "total": 250,
  "data": [
    {
      "id": 1,
      "name": "John"
    }
  ]
}

//  Request Payload (POST /users)
{
  "name": "John",
  "email": "john@test.com"
}
```

### Converts Methods

| Method           | Converts                | Use When       |
| ---------------- | ----------------------- | -------------- |
| JSON.stringify() | JS Object → JSON String | Sending Data   |
| JSON.parse()     | JSON String → JS Object | Receiving Data |

```txt
API Request Body → stringify()
API Response → parse()
Local Storage Save → stringify()
Local Storage Read → parse()
```

```js
// JavaScript ↔ JSON (Stringify)
const json = JSON.stringify(data);
```

```json
{
  "name": "John",
  "age": 25,
  "isAdmin": true,
  "salary": null,
  "skills": ["React", "TypeScript"],
  "address": {
    "city": "London"
  }
}
```

```js
// JSON → Object (Parse Back)
const parsed = JSON.parse(json);
```

```js
{
  name: "John",
  age: 25,
  isAdmin: true,
  salary: null,
  skills: [
    "React",
    "TypeScript"
  ],
  address: {
    city: "London"
  }
}
```

---

## 📌 Streamed API

- A streamed API sends data in chunks as it becomes available, allowing the frontend to display partial results immediately instead of waiting for the complete response.

- Normal API: Frontend > Request > Backend > Generate Full Response > Send Response > Display
  - User Waits 5 Seconds and Gets Complete Response
- Streamed API: Frontend > Request > Backend > Chunk 1 > Chunk 2 > Chunk 3 > Display Continuously
  - Youtube Video, ChatGPT Typing Effect,

| Item        | Description                                                    |
| ----------- | -------------------------------------------------------------- |
| Purpose     | Receive Data Continuously Instead Of Waiting For Full Response |
| Benefit     | Faster UI Updates                                              |
| Common Uses | AI Chat, Live Notifications, Logs, Stock Prices                |
| Protocols   | HTTP Streaming, SSE, WebSocket                                 |

### Common Streaming Technologies

| Technology               | Direction       |
| ------------------------ | --------------- |
| HTTP Streaming           | Server → Client |
| SSE (Server Sent Events) | Server → Client |
| WebSocket                | Two Way         |
| WebRTC                   | Real-Time Media |

### Real World Product

| Product             | Technology        |
| ------------------- | ----------------- |
| ChatGPT             | HTTP Stream / SSE |
| Claude              | HTTP Stream / SSE |
| Live Logs           | SSE               |
| Stock Market Ticker | WebSocket         |
| Chat App            | WebSocket         |
| Multiplayer Game    | WebSocket         |
| Live Notifications  | SSE               |

---
