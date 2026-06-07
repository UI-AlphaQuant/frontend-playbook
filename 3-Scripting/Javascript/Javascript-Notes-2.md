# 👉 Browser, DOM Manipulation

## 📌 DOM Basics

DOM (Document Object Model) represents HTML as JavaScript objects.

| Concept  | Details                | Example        |
| -------- | ---------------------- | -------------- |
| Document | Entire webpage object  | `document`     |
| Element  | HTML tag object        | `<div>`        |
| Node     | Every DOM item         | Text, elements |
| DOM Tree | Hierarchical structure | Parent → Child |

### `window` vs `document`

| Object                 | Method / Property    | Real Syntax Example                               | Purpose                      |
| ---------------------- | -------------------- | ------------------------------------------------- | ---------------------------- |
| rowspan="6" `window`   | `innerWidth`         | `window.innerWidth`                               | Get viewport width           |
|                        | `scrollY`            | `window.scrollY`                                  | Get vertical scroll position |
|                        | `location.href`      | `window.location.href = "/dashboard"`             | Redirect page                |
|                        | `setTimeout()`       | `setTimeout(() => hideLoader(), 1000)`            | Run code after delay         |
|                        | `setInterval()`      | `setInterval(() => updateClock(), 1000)`          | Run repeatedly               |
|                        | `scrollTo()`         | `window.scrollTo({ top: 0, behavior: "smooth" })` | Smooth page scroll           |
| rowspan="8" `document` | `querySelector()`    | `document.querySelector(".card")`                 | Select first element         |
|                        | `querySelectorAll()` | `document.querySelectorAll(".card")`              | Select multiple elements     |
|                        | `getElementById()`   | `document.getElementById("modal")`                | Select element by ID         |
|                        | `createElement()`    | `document.createElement("div")`                   | Create new element           |
|                        | `addEventListener()` | `document.addEventListener("click", closeMenu)`   | Listen events                |
|                        | `innerHTML`          | `box.innerHTML = "<h2>Welcome</h2>"`              | Update HTML                  |
|                        | `append()`           | `list.append(card)`                               | Insert element               |
|                        | `classList.add()`    | `modal.classList.add("open")`                     | Add CSS class                |

### DOM Access

```js
document;

document.body;

document.title;
```

### DOM Structure

```html
<html>
  <body>
    <h1>Hello</h1>
  </body>
</html>
```

```txt
document
 └── html
      └── body
           └── h1
```

| Real-World Usage | Example               |
| ---------------- | --------------------- |
| Update UI        | Change text/content   |
| Handle Events    | Button clicks         |
| Form Handling    | Input validation      |
| Dynamic Content  | Render products/posts |

- Browser creates DOM from HTML
- JavaScript uses DOM to manipulate UI
- Core concept in frontend development

---

## 📌 Traversing

DOM Traversing means navigating between related DOM elements.

| Property / Method        | Details                      | Example                     |
| ------------------------ | ---------------------------- | --------------------------- |
| `parentElement`          | Access parent element        | `el.parentElement`          |
| `children`               | Access child elements        | `el.children`               |
| `firstElementChild`      | First child element          | `el.firstElementChild`      |
| `lastElementChild`       | Last child element           | `el.lastElementChild`       |
| `nextElementSibling`     | Next sibling element         | `el.nextElementSibling`     |
| `previousElementSibling` | Previous sibling element     | `el.previousElementSibling` |
| `closest()`              | Find nearest matching parent | `el.closest(".card")`       |

```js
// Parent Element
element.parentElement;

// Child Elements
element.children;

// First Child
element.firstElementChild;

// Next Sibling
element.nextElementSibling;

// Closest Parent
element.closest(".card");
```

| Real-World Usage | Example                  |
| ---------------- | ------------------------ |
| Form Validation  | Access parent form/group |
| Menus            | Navigate list items      |
| Cards            | Access related content   |
| Tables           | Traverse rows/cells      |

- Helps navigate DOM efficiently
- Common in event handling and dynamic UI
- `closest()` is widely used in modern JS

---

## 📌 Styling & Attributes

JavaScript can modify element styles, classes, and attributes dynamically.

| Method / Property      | Details                    | Example                           |
| ---------------------- | -------------------------- | --------------------------------- |
| `style`                | Apply inline styles        | `el.style.color = "red"`          |
| `className`            | Get/set all classes        | `el.className = "card"`           |
| `classList.add()`      | Add class                  | `el.classList.add("active")`      |
| `classList.remove()`   | Remove class               | `el.classList.remove("active")`   |
| `classList.toggle()`   | Toggle class               | `el.classList.toggle("dark")`     |
| `classList.contains()` | Check class                | `el.classList.contains("active")` |
| `innerHTML`            | Set HTML content           | `el.innerHTML = "<b>Hi</b>"`      |
| `textContent`          | Set plain text             | `el.textContent = "Hello"`        |
| `setAttribute()`       | Add/update attribute       | `el.setAttribute()`               |
| `getAttribute()`       | Get attribute value        | `el.getAttribute()`               |
| `removeAttribute()`    | Remove attribute           | `el.removeAttribute()`            |
| `dataset`              | Access `data-*` attributes | `el.dataset.id`                   |

```js
const box = document.querySelector(".box");

// Inline Style
box.style.color = "red";

// Set All Classes
card.className = "card active";

// Add Class
box.classList.add("active");

// Remove Class
box.classList.remove("hidden");

// Toggle Class
body.classList.toggle("dark");

// Check Class
box.classList.contains("active");

// Add HTML
box.innerHTML = "<b>Hello</b>";

// Add Text
box.textContent = "Hello";

// Set Attribute
input.setAttribute("disabled", true);

// Get Attribute
img.getAttribute("src"); // logo.png

// Remove Attribute
button.removeAttribute("disabled");

// Data Attribute
box.dataset.id;
```

| Real-World Usage | Example                 |
| ---------------- | ----------------------- |
| Dark Mode        | Toggle theme classes    |
| Form Validation  | Add error classes       |
| Modals           | Show/hide popup         |
| Accessibility    | Dynamic ARIA attributes |

- Prefer classes over inline styles
- `classList` is modern and flexible
- Useful for dynamic UI updates

### Commonly Used `style` Properties

| Property             | Example                              |
| -------------------- | ------------------------------------ |
| `display`            | `el.style.display = "none"`          |
| `color`              | `el.style.color = "red"`             |
| `backgroundColor`    | `el.style.backgroundColor = "black"` |
| `width` / `height`   | `el.style.width = "200px"`           |
| `margin` / `padding` | `el.style.padding = "20px"`          |
| `fontSize`           | `el.style.fontSize = "18px"`         |
| `border`             | `el.style.border = "1px solid"`      |
| `opacity`            | `el.style.opacity = "0.5"`           |
| `transform`          | `el.style.transform = "scale(1.1)"`  |
| `transition`         | `el.style.transition = "0.3s"`       |

---

## 📌 Event Listeners

Event listeners run functions when events occur on elements.

| Method                  | Details              | Example                     |
| ----------------------- | -------------------- | --------------------------- |
| `addEventListener()`    | Attach event handler | `btn.addEventListener()`    |
| `removeEventListener()` | Remove event handler | `btn.removeEventListener()` |

| Type            | Event        | Details                         |
| --------------- | ------------ | ------------------------------- |
| Mouse Events    | `click`      | Mouse click                     |
|                 | `dblclick`   | Double click                    |
|                 | `mouseenter` | Mouse enters element            |
|                 | `mouseleave` | Mouse leaves element            |
|                 | `mousemove`  | Mouse movement                  |
| Keyboard Events | `keydown`    | Key pressed down                |
|                 | `keyup`      | Key released                    |
|                 | `keypress`   | Key typed _(deprecated)_        |
| Form Events     | `input`      | Input value changes             |
|                 | `change`     | Value changed after interaction |
|                 | `submit`     | Form submitted                  |
|                 | `focus`      | Element focused                 |
|                 | `blur`       | Element loses focus             |
| Window Events   | `load`       | Page fully loaded               |
|                 | `resize`     | Window resized                  |
|                 | `scroll`     | Page/container scrolled         |

```js
// Click Event
button.addEventListener("click", () => {
  console.log("Clicked");
});

// Input Event
input.addEventListener("input", (e) => {
  console.log(e.target.value);
});

// Form Submit
form.addEventListener("submit", (e) => {
  e.preventDefault();
});

// Add/Remove Event
const button = document.querySelector(".btn");
function handleClick() {
  console.log("Clicked");
}
button.addEventListener("click", handleClick);
button.removeEventListener("click", handleClick);
```

| Real-World Usage   | Example           |
| ------------------ | ----------------- |
| Buttons            | Open modal/menu   |
| Forms              | Validation        |
| Search             | Live search input |
| Keyboard Shortcuts | Hotkeys           |
| Infinite Scroll    | Load more data    |

- Preferred modern event handling method
- Supports multiple listeners
- Commonly used with callbacks
- `e` is the event object automatically passed to event handlers.

---

## 📌 Event Object (`e`)

The event object contains information about the triggered event.

| Property / Method       | Details                  | Example              |
| ----------------------- | ------------------------ | -------------------- |
| `e.target`              | Triggered element        | Clicked button       |
| `e.currentTarget`       | Element with listener    | Parent/container     |
| `e.type`                | Event type               | `"click"`            |
| `e.key`                 | Pressed keyboard key     | `"Enter"`            |
| `e.clientX / e.clientY` | Mouse position           | `120, 300`           |
| `e.preventDefault()`    | Prevent default behavior | Stop form reload     |
| `e.stopPropagation()`   | Stop event bubbling      | Prevent parent event |

```js
// Event Object
button.addEventListener("click", (e) => {
  console.log(e);
});

// Target Element
button.addEventListener("click", (e) => {
  console.log(e.target);
});

// Keyboard Event
document.addEventListener("keydown", (e) => {
  console.log(e.key);
});

// Mouse Position
box.addEventListener("mousemove", (e) => {
  console.log(e.clientX, e.clientY);
});

// Prevent Default
form.addEventListener("submit", (e) => {
  e.preventDefault();
});

// Stop Bubbling
child.addEventListener("click", (e) => {
  e.stopPropagation();
});
```

| Real-World Usage   | Example               |
| ------------------ | --------------------- |
| Forms              | Prevent page reload   |
| Keyboard Shortcuts | Detect pressed keys   |
| Drag/Mouse Effects | Track cursor position |
| Event Delegation   | Identify clicked item |

- Automatically passed to event handlers
- Commonly named `e` or `event`
- Provides event-related data and controls

---

## 📌 Bubbling & Capturing

Events travel through the DOM in two phases: capturing and bubbling.

| Phase     | Direction    | Details                           |
| --------- | ------------ | --------------------------------- |
| Capturing | Top → Bottom | Event moves from parent to target |
| Bubbling  | Bottom → Top | Event moves from target to parent |

### Event Flow

```txt
document
  ↓
parent
  ↓
button
```

```txt
Capturing: document → parent → button
Bubbling: button → parent → document
```

### Usage Example

```js
const parent = document.querySelector(".parent");
const child = document.querySelector(".child");

parent.addEventListener("click", () => {
  console.log("Parent");
});

child.addEventListener("click", () => {
  console.log("Child");
});
```

```txt
Output:
Child
Parent
```

(Default = Bubbling)

### Capturing Example

```js
parent.addEventListener(
  "click",
  () => {
    console.log("Parent Capture");
  },
  true,
);
```

`true` enables capturing phase.

### Stop Bubbling

```js
child.addEventListener("click", (e) => {
  e.stopPropagation();
});
```

| Real-World Usage | Example                         |
| ---------------- | ------------------------------- |
| Dropdowns        | Prevent parent closing          |
| Modals           | Stop overlay click              |
| Nested Menus     | Control event flow              |
| Event Delegation | Handle child clicks from parent |

- Bubbling is default behavior
- Capturing is less commonly used
- `stopPropagation()` stops the event from moving to parent elements.

---

## 📌 Event Delegation

Event Delegation attaches one event listener to a parent instead of multiple child elements.

| Feature          | Details                         | Example                   |
| ---------------- | ------------------------------- | ------------------------- |
| Parent Listener  | Handle child events from parent | `list.addEventListener()` |
| Uses Bubbling    | Child event bubbles upward      | `e.target`                |
| Dynamic Elements | Works for newly added items     | Todo items                |

### Without Delegation ❌

```js
buttons.forEach((btn) => {
  btn.addEventListener("click", () => {
    console.log("Clicked");
  });
});
```

### With Delegation ✅

```js
list.addEventListener("click", (e) => {
  if (e.target.matches(".btn")) {
    console.log("Clicked");
  }
});
```

```html
<ul class="list">
  <li><button class="btn">Edit</button></li>
  <li><button class="btn">Delete</button></li>
</ul>
```

| Real-World Usage | Example              |
| ---------------- | -------------------- |
| Todo Apps        | Dynamic task buttons |
| Tables           | Row actions          |
| Menus            | Dynamic navigation   |
| Ecommerce        | Product card actions |

- Improves performance
- Reduces multiple event listeners
- Commonly used for dynamic content

---

## 📌 Form Events

Form events handle user input, validation, and form interactions.

| Event     | Trigger                 | Common Usage             |
| --------- | ----------------------- | ------------------------ |
| `submit`  | Form submitted          | Validation/API submit    |
| `input`   | Value changes instantly | Live search              |
| `change`  | Value confirmed/changed | Select, checkbox         |
| `focus`   | Element gains focus     | Active input UI          |
| `blur`    | Element loses focus     | Validation               |
| `reset`   | Form reset              | Clear form               |
| `keydown` | Key pressed             | Shortcuts/input handling |
| `keyup`   | Key released            | Search/filter            |
| `invalid` | Validation fails        | Custom validation UI     |

```js
const form = document.querySelector("form");
const input = document.querySelector("input");

// Submit Event
form.addEventListener("submit", (e) => {
  e.preventDefault();
});

// Input Event
input.addEventListener("input", (e) => {
  console.log(e.target.value);
});

// Change Event
select.addEventListener("change", (e) => {
  console.log(e.target.value);
});

// Focus Event
input.addEventListener("focus", () => {
  input.classList.add("active");
});

// Blur Event
input.addEventListener("blur", () => {
  input.classList.remove("active");
});

// Reset Event
form.addEventListener("reset", () => {
  console.log("Form Reset");
});

// Invalid Event
input.addEventListener("invalid", () => {
  console.log("Invalid Input");
});
```

### `input` vs `change`

| Event    | Trigger Timing         |
| -------- | ---------------------- |
| `input`  | Every keystroke/change |
| `change` | After value confirmed  |

| Real-World Usage | Example                     |
| ---------------- | --------------------------- |
| Validation       | Email/password checks       |
| Live Search      | Search while typing         |
| Forms            | Prevent reload/API submit   |
| UI Feedback      | Active/error states         |
| Filters          | Dropdown/category filtering |

- `input` is most used for realtime updates
- `submit` usually uses `preventDefault()`
- `blur` commonly used for validation

### `preventDefault()`

```js
// Without preventDefault()
form.addEventListener("submit", () => {
  console.log("Submitted");
});

// ✅ Form submits + page reloads
```

```js
// With preventDefault()
form.addEventListener("submit", (e) => {
  e.preventDefault();

  console.log("Submitted");
});

// ✅ Prevents form submit + page reload
```

---

## 📌 Keyboard & Mouse Events

Keyboard and mouse events handle user interactions.

| Type     | Event         | Details                  |
| -------- | ------------- | ------------------------ |
| Keyboard | `keydown`     | Key pressed down         |
|          | `keyup`       | Key released             |
|          | `keypress`    | Key typed _(deprecated)_ |
| Mouse    | `click`       | Mouse click              |
|          | `dblclick`    | Double click             |
|          | `mousedown`   | Mouse button pressed     |
|          | `mouseup`     | Mouse button released    |
|          | `mousemove`   | Mouse movement           |
|          | `mouseenter`  | Mouse enters element     |
|          | `mouseleave`  | Mouse leaves element     |
|          | `contextmenu` | Right click              |

```js
// Keydown Event
document.addEventListener("keydown", (e) => {
  console.log(e.key);
});

// Click Event
button.addEventListener("click", () => {
  console.log("Clicked");
});

// Mouse Move
box.addEventListener("mousemove", (e) => {
  console.log(e.clientX, e.clientY);
});

// Right Click
box.addEventListener("contextmenu", (e) => {
  e.preventDefault();
});
```

### Common Event Properties

| Property                | Details           |
| ----------------------- | ----------------- |
| `e.key`                 | Pressed key       |
| `e.target`              | Triggered element |
| `e.clientX / e.clientY` | Mouse position    |
| `e.button`              | Mouse button used |

| Real-World Usage   | Example        |
| ------------------ | -------------- |
| Keyboard Shortcuts | `Ctrl + S`     |
| Gaming/UI Effects  | Mouse tracking |
| Dropdowns/Menus    | Click handling |
| Drag Interactions  | Mouse movement |

- `keydown` is most commonly used for keyboard input
- `mousemove` can trigger frequently, optimize if needed
- `keypress` is deprecated

---

# 👉 DOM & JavaScript Utility Methods

## 📌 Selecting Elements

Selecting elements allows JavaScript to access HTML elements from the DOM.

| Method                     | Details                       | Example               |
| -------------------------- | ----------------------------- | --------------------- |
| `getElementById()`         | Select by ID                  | `#header`             |
| `getElementsByClassName()` | Select by class               | `.card`               |
| `getElementsByTagName()`   | Select by tag                 | `div`                 |
| `querySelector()`          | Select first matching element | `.btn`                |
| `querySelectorAll()`       | Select all matching elements  | `.item`               |
| `closest()`                | Find nearest parent match     | `.closest(".card")`   |
| `matches()`                | Check selector match          | `.matches(".active")` |

```js
document.getElementById("header");
document.getElementsByClassName("card");
document.getElementsByTagName("div");
document.querySelector(".btn");
document.querySelectorAll(".item");

// Closest Parent
element.closest(".card");

// Match Check
element.matches(".active");
```

| Real-World Usage | Example           |
| ---------------- | ----------------- |
| Buttons          | Click handling    |
| Forms            | Input access      |
| Cards/List       | Dynamic updates   |
| Navigation       | Menu interactions |

- `querySelector()` uses CSS selectors
- `querySelectorAll()` returns NodeList
- `getElementById()` is fastest for IDs

---

## 📌 Creating / Removing Elements

JavaScript can dynamically create, insert, replace, and remove DOM elements.

| Method            | Details                    | Example                         |
| ----------------- | -------------------------- | ------------------------------- |
| `createElement()` | Create new element         | `document.createElement("div")` |
| `append()`        | Add element/content at end | `el.append(child)`              |
| `appendChild()`   | Add child node             | `el.appendChild(child)`         |
| `prepend()`       | Add at beginning           | `el.prepend(child)`             |
| `before()`        | Insert before element      | `el.before(node)`               |
| `after()`         | Insert after element       | `el.after(node)`                |
| `replaceWith()`   | Replace element            | `el.replaceWith(node)`          |
| `remove()`        | Remove element             | `el.remove()`                   |

```js
// createElement() → Create new element
const div = document.createElement("div");

// append() → Add at end
document.body.append(div);

// appendChild() → Add child node
parent.appendChild(child);

// prepend() → Add at beginning
list.prepend(item);

// before() → Insert before element
card.before(alertBox);

// after() → Insert after element
title.after(subtitle);

// replaceWith() → Replace element
loader.replaceWith(content);

// remove() → Remove element
div.remove();
```

| Real-World Usage | Example                |
| ---------------- | ---------------------- |
| Todo Apps        | Add/remove tasks       |
| Chat Apps        | Render messages        |
| Ecommerce        | Render product cards   |
| Modals           | Dynamically show popup |

- Used heavily in dynamic UI rendering
- `append()` supports text and nodes
- `remove()` is modern replacement for older methods

---

## 📌 Basic Style Control Helpers

| Property / Method      | Purpose             | Example                           | Real-World Usage        |
| ---------------------- | ------------------- | --------------------------------- | ----------------------- |
| `style`                | Apply inline styles | `el.style.color = "red"`          | Dynamic UI updates      |
| `className`            | Set all classes     | `el.className = "active"`         | Theme switching         |
| `classList.add()`      | Add class           | `el.classList.add("show")`        | Open modals/dropdowns   |
| `classList.remove()`   | Remove class        | `el.classList.remove("hide")`     | Hide alerts/loaders     |
| `classList.toggle()`   | Toggle class        | `el.classList.toggle("dark")`     | Dark mode               |
| `classList.contains()` | Check class         | `el.classList.contains("active")` | Active navigation       |
| `getComputedStyle()`   | Get applied styles  | `getComputedStyle(el)`            | Responsive calculations |

```js
const modal = document.querySelector(".modal");

modal.classList.add("show");

document.body.classList.toggle("dark");

// Adds "show" class (Toggles dark mode class)
```

---

## 📌 String Methods

| Method          | Purpose                           | Detailed Example                         | Real-World Usage        |
| --------------- | --------------------------------- | ---------------------------------------- | ----------------------- |
| `trim()`        | Remove spaces - (beginning & end) | `"  John  ".trim()`                      | Form validation         |
| `includes()`    | Check text exists                 | `"frontend".includes("end")`             | Search/filter           |
| `slice()`       | Extract part                      | `"JavaScript".slice(0,4)`                | Text previews           |
| `replace()`     | Replace text                      | `"Hello John".replace("John", "Mike")`   | Content formatting      |
| `toLowerCase()` | Lowercase text                    | `"ADMIN".toLowerCase()`                  | Case-insensitive search |
| `toUpperCase()` | Uppercase text                    | `"admin".toUpperCase()`                  | Labels/titles           |
| `split()`       | Convert to array                  | `"js,react,vue".split(",")`              | CSV/tag parsing         |
| `startsWith()`  | Check starting text               | `"https://site.com".startsWith("https")` | URL checks              |
| `endsWith()`    | Check ending text                 | `"photo.png".endsWith(".png")`           | File validation         |

```js
const search = "  React JS  ";

console.log(search.trim().toLowerCase());
// "react js"

console.log(search.includes("JS"));
// true
```

---

## 📌 Number & Math Methods

| Method          | Purpose                 | Example              | Real-World Usage       |
| --------------- | ----------------------- | -------------------- | ---------------------- |
| `Number()`      | Convert to number       | `Number("10")`       | Form values            |
| `parseInt()`    | Integer conversion      | `parseInt("10px")`   | CSS calculations       |
| `parseFloat()`  | Float conversion        | `parseFloat("10.5")` | Price/decimal handling |
| `toFixed()`     | Decimal formatting      | `10.456.toFixed(2)`  | Currency formatting    |
| `Math.round()`  | Round value             | `Math.round(4.6)`    | Ratings/scores         |
| `Math.floor()`  | Round down              | `Math.floor(4.9)`    | Pagination             |
| `Math.ceil()`   | Round up                | `Math.ceil(4.1)`     | Total pages            |
| `Math.random()` | Random number           | `Math.random()`      | OTP/random IDs         |
| `Math.max()`    | Largest value           | `Math.max(1,2)`      | Analytics/charts       |
| `Math.min()`    | Smallest value          | `Math.min(1,2)`      | Pricing filters        |
| `Math.abs()`    | Absolute value          | `Math.abs(-10)`      | Distance/calculations  |
| `Math.trunc()`  | Remove decimals         | `Math.trunc(4.9)`    | Integer conversion     |
| `Math.sqrt()`   | Square root             | `Math.sqrt(16)`      | Geometry/calculations  |
| `Math.pow()`    | Power calculation       | `Math.pow(2,3)`      | Charts/math logic      |
| `Math.sign()`   | Positive/negative check | `Math.sign(-5)`      | Trading/calculations   |
| `Math.PI`       | Pi constant             | `Math.PI`            | Circle calculations    |
| `Math.sin()`    | Sine calculation        | `Math.sin(0)`        | Animations/charts      |
| `Math.cos()`    | Cosine calculation      | `Math.cos(0)`        | Motion effects         |
| `Math.log()`    | Logarithm value         | `Math.log(10)`       | Analytics/math         |
| `Math.exp()`    | Exponential value       | `Math.exp(2)`        | Finance/calculations   |

```js
const price = "99.99";

console.log(parseFloat(price).toFixed(2));
// "99.99"

console.log(Math.floor(Math.random() * 10));
// Random number: 0-9
```

---

## 📌 Element Methods & Properties

| Method / Property         | Purpose                   | Example                      | Real-World Usage             |
| ------------------------- | ------------------------- | ---------------------------- | ---------------------------- |
| `innerHTML`               | Set HTML                  | `el.innerHTML`               | Dynamic cards/content        |
| `textContent`             | Set text                  | `el.textContent`             | Safe text rendering          |
| `value`                   | Input value               | `input.value`                | Forms/search                 |
| `checked`                 | Checkbox state            | `checkbox.checked`           | Settings/forms               |
| `src`                     | Image source              | `img.src`                    | Product/media images         |
| `href`                    | Link URL                  | `link.href`                  | Dynamic navigation           |
| `children`                | Child elements            | `el.children`                | Menu/items traversal         |
| `parentElement`           | Parent element            | `el.parentElement`           | Event delegation             |
| `clientWidth`             | Inner element width       | `box.clientWidth`            | Responsive calculations      |
| `clientHeight`            | Inner element height      | `box.clientHeight`           | Dynamic layouts              |
| `offsetWidth`             | Total width incl. border  | `box.offsetWidth`            | Card/modal sizing            |
| `offsetHeight`            | Total height incl. border | `box.offsetHeight`           | Height calculations          |
| `scrollWidth`             | Full scrollable width     | `box.scrollWidth`            | Overflow detection           |
| `scrollHeight`            | Full scrollable height    | `box.scrollHeight`           | Chat/message areas           |
| `append()`                | Add element               | `el.append()`                | Render lists/cards           |
| `remove()`                | Remove element            | `el.remove()`                | Delete items                 |
| `focus()`                 | Focus element             | `input.focus()`              | Form UX                      |
| `blur()`                  | Remove focus              | `input.blur()`               | Validation handling          |
| `getBoundingClientRect()` | Element size/position     | `el.getBoundingClientRect()` | Tooltip/dropdown positioning |

```js
const title = document.querySelector(".title");

title.textContent = "Dashboard"; // Sets text: Dashboard

list.append(item); // Adds item element

card.remove(); // Removes card element
```

---

## 📌 DOM Selection Methods

| Method                     | Purpose                | Example               | Real-World Usage   |
| -------------------------- | ---------------------- | --------------------- | ------------------ |
| `getElementById()`         | Select by ID           | `#box`                | Forms/modals       |
| `getElementsByClassName()` | Select by class        | `.card`               | Card layouts       |
| `getElementsByTagName()`   | Select by tag          | `div`                 | Generic selections |
| `querySelector()`          | First matching element | `.btn`                | Buttons/components |
| `querySelectorAll()`       | All matching elements  | `.item`               | Lists/tables       |
| `closest()`                | Find nearest parent    | `.closest(".card")`   | Nested actions     |
| `matches()`                | Check selector match   | `.matches(".active")` | Delegation checks  |

```js
const button = document.querySelector(".btn"); // First .btn element
const items = document.querySelectorAll(".item"); // NodeList of .item elements
const form = document.getElementById("form"); // Element with id="form"
```

---

## 📌 Window & Browser Properties

| Property / Method     | Purpose                    | Example                  | Real-World Usage         |
| --------------------- | -------------------------- | ------------------------ | ------------------------ |
| `window.innerWidth`   | Viewport width             | `window.innerWidth`      | Responsive layouts       |
| `window.innerHeight`  | Viewport height            | `window.innerHeight`     | Fullscreen sections      |
| `window.outerWidth`   | Full browser width         | `window.outerWidth`      | Window calculations      |
| `window.outerHeight`  | Full browser height        | `window.outerHeight`     | Popup/window sizing      |
| `window.scrollX`      | Horizontal scroll position | `window.scrollX`         | Sticky UI                |
| `window.scrollY`      | Vertical scroll position   | `window.scrollY`         | Scroll effects           |
| `window.scrollTo()`   | Scroll to position         | `window.scrollTo(0,0)`   | Back-to-top button       |
| `window.scrollBy()`   | Scroll relative amount     | `window.scrollBy(0,100)` | Infinite scrolling       |
| `location.href`       | Current URL                | `location.href`          | Redirects/routing        |
| `location.reload()`   | Reload page                | `location.reload()`      | Refresh content          |
| `history.back()`      | Previous page              | `history.back()`         | Navigation buttons       |
| `navigator.userAgent` | Browser info               | `navigator.userAgent`    | Device/browser detection |
| `alert()`             | Alert popup                | `alert("Hi")`            | Quick notifications      |
| `confirm()`           | Confirm dialog             | `confirm()`              | Delete confirmations     |
| `setTimeout()`        | Delay execution            | `setTimeout()`           | Debouncing/loaders       |
| `setInterval()`       | Repeated execution         | `setInterval()`          | Timers/clocks            |

```js
console.log(window.innerWidth);
// Browser width

setTimeout(() => {
  alert("Session Expired");
}, 2000);

// Alert after 2 seconds
```

---

## 📌 JSON Methods

| Method             | Purpose              | Example               | Real-World Usage      |
| ------------------ | -------------------- | --------------------- | --------------------- |
| `JSON.stringify()` | Object → JSON string | `JSON.stringify(obj)` | API/storage data      |
| `JSON.parse()`     | JSON string → Object | `JSON.parse(data)`    | API response handling |

```js
const user = {
  name: "John",
};
const json = JSON.stringify(user);
console.log(json); // '{"name":"John"}'

const data = JSON.parse(json);
console.log(data.name); // "John"
```

```js
// JSON Stringify
const user = {
  name: "John",
  role: "Admin",
};

const json = JSON.stringify(user);
console.log(json); // '{"name":"John","role":"Admin"}'
```

---

## 📌 Date & Time Methods

| Method / Property       | Purpose             | Example                     | Real-World Usage    |
| ----------------------- | ------------------- | --------------------------- | ------------------- |
| `new Date()`            | Create current date | `new Date()`                | Timestamps/logs     |
| `Date.now()`            | Current timestamp   | `Date.now()`                | IDs/cache           |
| `getFullYear()`         | Get year            | `date.getFullYear()`        | Reports/calendars   |
| `getMonth()`            | Get month (0-11)    | `date.getMonth()`           | Date pickers        |
| `getDate()`             | Get day of month    | `date.getDate()`            | Schedules           |
| `getDay()`              | Get weekday (0-6)   | `date.getDay()`             | Calendar apps       |
| `getHours()`            | Get hours           | `date.getHours()`           | Clocks/time         |
| `getMinutes()`          | Get minutes         | `date.getMinutes()`         | Timers              |
| `getSeconds()`          | Get seconds         | `date.getSeconds()`         | Countdowns          |
| `getTime()`             | Timestamp in ms     | `date.getTime()`            | Comparisons/sorting |
| `setDate()`             | Change day          | `date.setDate(20)`          | Date calculations   |
| `setMonth()`            | Change month        | `date.setMonth(5)`          | Scheduling          |
| `toDateString()`        | Readable date       | `date.toDateString()`       | UI display          |
| `toLocaleDateString()`  | Localized date      | `date.toLocaleDateString()` | Regional formatting |
| `toLocaleTimeString()`  | Localized time      | `date.toLocaleTimeString()` | Time display        |
| `toISOString()`         | ISO date format     | `date.toISOString()`        | APIs/database       |
| `Intl.DateTimeFormat()` | Advanced formatting | `new Intl.DateTimeFormat()` | Multi-region apps   |

```js
const date = new Date();

console.log(date);
// Current date/time

console.log(Date.now());
// Timestamp in milliseconds

console.log(date.getFullYear());
// 2026

console.log(date.getMonth());
// 0-11

console.log(date.toLocaleDateString());
// "5/22/2026"

console.log(date.toLocaleTimeString());
// "10:30:20 AM"

console.log(date.toISOString());
// "2026-05-22T10:30:20.000Z"
```

```js
// Date Formatting Example
const formatter = new Intl.DateTimeFormat("en-IN", {
  dateStyle: "medium",
  timeStyle: "short",
});

console.log(formatter.format(new Date()));
// "22 May 2026, 10:30 am"
```

| Common Real-World Usage | Example              |
| ----------------------- | -------------------- |
| Ecommerce               | Order timestamps     |
| Dashboards              | Analytics dates      |
| Calendars               | Events/schedules     |
| Chat Apps               | Message timestamps   |
| Finance Apps            | Trading/session time |
| Authentication          | Token expiration     |

| Important Notes       | Details                      |
| --------------------- | ---------------------------- |
| Month Starts From `0` | January = `0`                |
| Timestamp Unit        | Milliseconds                 |
| ISO Format            | Standard API/database format |
| `Intl.DateTimeFormat` | Preferred modern formatting  |

| Type            | Code / Method               | Example Output               | Usage               |
| --------------- | --------------------------- | ---------------------------- | ------------------- |
| Readable Date   | `date.toDateString()`       | `"Fri May 22 2026"`          | UI display          |
| Full Time       | `date.toTimeString()`       | `"10:30:20 GMT+0530"`        | Detailed time       |
| ISO Format      | `date.toISOString()`        | `"2026-05-22T05:00:20.000Z"` | APIs/database       |
| Locale Date     | `date.toLocaleDateString()` | `"22/05/2026"`               | Regional UI         |
| Locale Time     | `date.toLocaleTimeString()` | `"10:30:20 AM"`              | Chat/clocks         |
| Locale DateTime | `date.toLocaleString()`     | `"22/05/2026, 10:30:20 AM"`  | Orders/logs         |
| Intl Formatting | `Intl.DateTimeFormat()`     | `"Friday, 22 May 2026"`      | Advanced formatting |
| Timestamp       | `Date.now()`                | `1747890000000`              | Cache/sorting       |
| Year            | `date.getFullYear()`        | `2026`                       | Reports/calendars   |
| Month           | `date.getMonth() + 1`       | `5`                          | Date formatting     |
| Day             | `date.getDate()`            | `22`                         | Scheduling          |
| Hours           | `date.getHours()`           | `10`                         | Clocks/timers       |
| Minutes         | `date.getMinutes()`         | `30`                         | Time formatting     |
| Seconds         | `date.getSeconds()`         | `20`                         | Countdowns          |
| Custom Format   | `${d}/${m}/${y}`            | `"22/5/2026"`                | Manual formatting   |
| Custom Time     | `${h}:${m}`                 | `"10:30"`                    | Time UI             |
| India Format    | `DD/MM/YYYY`                | `"22/05/2026"`               | Indian apps         |
| US Format       | `MM/DD/YYYY`                | `"05/22/2026"`               | US apps             |
| API Format      | `YYYY-MM-DD`                | `"2026-05-22"`               | APIs/database       |
| 24h Time        | `HH:mm`                     | `"10:30"`                    | Admin dashboards    |
| 12h Time        | `hh:mm AM/PM`               | `"10:30 AM"`                 | Chat/apps           |

---
