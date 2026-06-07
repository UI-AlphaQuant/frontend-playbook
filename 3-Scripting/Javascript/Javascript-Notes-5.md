# 👉 Canvas

## 📌 HTML Canvas API

Canvas API is used for graphics, games, animations, charts, image editing, and visual rendering.

### Canvas Setup

| Method / Property | Purpose             | Example                   | Real-World Usage   |
| ----------------- | ------------------- | ------------------------- | ------------------ |
| `<canvas>`        | Drawing area        | `<canvas></canvas>`       | Graphics rendering |
| `getContext()`    | Get drawing context | `canvas.getContext("2d")` | Drawing system     |
| `canvas.width`    | Canvas width        | `canvas.width = 800`      | Responsive canvas  |
| `canvas.height`   | Canvas height       | `canvas.height = 400`     | Game/charts size   |

```html
<canvas id="canvas"></canvas>
```

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

canvas.width = 800;
canvas.height = 400;
```

### Shapes & Drawing

| Method         | Purpose             | Example            | Real-World Usage |
| -------------- | ------------------- | ------------------ | ---------------- |
| `fillRect()`   | Filled rectangle    | `ctx.fillRect()`   | UI/cards         |
| `strokeRect()` | Rectangle border    | `ctx.strokeRect()` | Charts/borders   |
| `clearRect()`  | Clear area          | `ctx.clearRect()`  | Animations       |
| `beginPath()`  | Start path          | `ctx.beginPath()`  | Shape drawing    |
| `moveTo()`     | Move cursor         | `ctx.moveTo()`     | Line drawing     |
| `lineTo()`     | Draw line           | `ctx.lineTo()`     | Charts/graphs    |
| `stroke()`     | Draw border         | `ctx.stroke()`     | Canvas shapes    |
| `fill()`       | Fill shape          | `ctx.fill()`       | Graphics         |
| `closePath()`  | Close path          | `ctx.closePath()`  | Polygon shapes   |
| `arc()`        | Draw circle/arc     | `ctx.arc()`        | Avatars/charts   |
| `rect()`       | Draw rectangle path | `ctx.rect()`       | Shape systems    |

```js
ctx.fillRect(50, 50, 100, 100); // x, y, width, height
ctx.strokeRect(200, 50, 100, 100); // x, y, width, height
```

### Styling & Colors

| Property      | Purpose          | Example                     | Real-World Usage |
| ------------- | ---------------- | --------------------------- | ---------------- |
| `fillStyle`   | Fill color       | `ctx.fillStyle = "blue"`    | Shapes/UI        |
| `strokeStyle` | Border color     | `ctx.strokeStyle = "red"`   | Charts           |
| `lineWidth`   | Border thickness | `ctx.lineWidth = 2`         | Drawing apps     |
| `globalAlpha` | Opacity          | `ctx.globalAlpha = 0.5`     | Fade effects     |
| `shadowColor` | Shadow color     | `ctx.shadowColor = "black"` | UI effects       |
| `shadowBlur`  | Shadow blur      | `ctx.shadowBlur = 10`       | Glow/shadow      |

```js
ctx.fillStyle = "blue"; // fill color
ctx.strokeStyle = "black"; // border color
ctx.lineWidth = 2; // border thickness
ctx.globalAlpha = 0.5; // opacity
ctx.shadowColor = "black"; // shadow color
ctx.shadowBlur = 10; // shadow blur amount
```

### Text Drawing

| Method / Property | Purpose      | Example                   | Real-World Usage |
| ----------------- | ------------ | ------------------------- | ---------------- |
| `font`            | Text style   | `ctx.font = "20px Arial"` | Labels/charts    |
| `fillText()`      | Filled text  | `ctx.fillText()`          | UI text          |
| `strokeText()`    | Outline text | `ctx.strokeText()`        | Posters/design   |

```js
ctx.font = "20px Arial"; // text size and font family
ctx.fillText("Hello Canvas", 50, 50); // text, x position, y position
ctx.strokeText("Hello", 100, 100); // text, x position, y position
```

### Images

| Method        | Purpose             | Example              | Real-World Usage  |
| ------------- | ------------------- | -------------------- | ----------------- |
| `drawImage()` | Draw image          | `ctx.drawImage()`    | Editors/galleries |
| `toDataURL()` | Export canvas image | `canvas.toDataURL()` | Downloads/sharing |

```js
const img = new Image();

img.src = "photo.jpg";

img.onload = () => {
  ctx.drawImage(img, 0, 0); // image, x, y
};

canvas.toDataURL(); // export canvas as image base64
```

### Transformations

| Method        | Purpose           | Example           | Real-World Usage |
| ------------- | ----------------- | ----------------- | ---------------- |
| `save()`      | Save canvas state | `ctx.save()`      | Complex drawings |
| `restore()`   | Restore state     | `ctx.restore()`   | Animations       |
| `translate()` | Move origin       | `ctx.translate()` | Games            |
| `rotate()`    | Rotate canvas     | `ctx.rotate()`    | Visual effects   |
| `scale()`     | Resize drawings   | `ctx.scale()`     | Zooming          |

```js
ctx.save(); // save current canvas state
ctx.translate(100, 100); // move x, move y
ctx.rotate(Math.PI / 4); // rotation angle
ctx.scale(2, 2); // horizontal scale, vertical scale
ctx.restore(); // restore previous state
```

### Curves & Advanced Paths

| Method               | Purpose               | Example                  | Real-World Usage |
| -------------------- | --------------------- | ------------------------ | ---------------- |
| `quadraticCurveTo()` | Simple curve          | `ctx.quadraticCurveTo()` | Drawing tools    |
| `bezierCurveTo()`    | Advanced curve        | `ctx.bezierCurveTo()`    | Design editors   |
| `clip()`             | Restrict drawing area | `ctx.clip()`             | Image cropping   |

```js
ctx.quadraticCurveTo(100, 50, 200, 100); // control x, control y, end x, end y
ctx.bezierCurveTo(50, 50, 150, 150, 200, 100); // cp1 x, cp1 y, cp2 x, cp2 y, end x, end y
ctx.clip(); // restrict drawing area
```

### Gradients

| Method                   | Purpose           | Example                      | Real-World Usage |
| ------------------------ | ----------------- | ---------------------------- | ---------------- |
| `createLinearGradient()` | Linear gradient   | `ctx.createLinearGradient()` | Modern UI        |
| `createRadialGradient()` | Circular gradient | `ctx.createRadialGradient()` | Effects/charts   |

```js
const gradient = ctx.createLinearGradient(0, 0, 200, 0); // start x, start y, end x, end y
gradient.addColorStop(0, "blue"); // position, color
gradient.addColorStop(1, "purple"); // position, color
ctx.fillStyle = gradient;
```

### Animation

| Method                    | Purpose               | Example                   | Real-World Usage |
| ------------------------- | --------------------- | ------------------------- | ---------------- |
| `requestAnimationFrame()` | Smooth animation loop | `requestAnimationFrame()` | Games/UI         |
| `clearRect()`             | Clear previous frame  | `ctx.clearRect()`         | Animations       |

```js
function animate() {
  ctx.clearRect(0, 0, canvas.width, canvas.height); // start x, start y, width, height
  ctx.fillRect(50, 50, 100, 100);
  requestAnimationFrame(animate);
}
animate();
```

### Mouse Interaction

| Event       | Purpose       | Example                     | Real-World Usage |
| ----------- | ------------- | --------------------------- | ---------------- |
| `mousemove` | Track mouse   | `canvas.addEventListener()` | Drawing apps     |
| `click`     | Detect click  | `canvas.addEventListener()` | Games/UI         |
| `mousedown` | Mouse press   | `canvas.addEventListener()` | Dragging         |
| `mouseup`   | Mouse release | `canvas.addEventListener()` | Drawing tools    |

```js
canvas.addEventListener("mousemove", (e) => {
  console.log(e.offsetX, e.offsetY); // mouse x, mouse y inside canvas
});
```

| Canvas Utilities          | Purpose         | Example                          | Real-World Usage   |
| ------------------------- | --------------- | -------------------------------- | ------------------ |
| `getBoundingClientRect()` | Canvas position | `canvas.getBoundingClientRect()` | Mouse calculations |
| Device Pixel Ratio        | Sharp rendering | `window.devicePixelRatio`        | Retina screens     |
| Collision Detection       | Object overlap  | Manual calculations              | Games              |

| Real-World Canvas Systems | Canvas Usage       |
| ------------------------- | ------------------ |
| Charts                    | Trading dashboards |
| Games                     | Browser games      |
| Whiteboards               | Drawing apps       |
| Image Editors             | Crop/filter tools  |
| Data Visualization        | Analytics          |
| Realtime Graphics         | Maps/simulations   |
| Animations                | Interactive UI     |

| Important Notes        | Details                      |
| ---------------------- | ---------------------------- |
| `2d` Context           | Most commonly used           |
| No DOM Elements Inside | Pure drawing surface         |
| High Performance       | Good for graphics-heavy apps |
| Common with Games      | Widely used                  |
| Pixel-Based Rendering  | Not DOM-based                |
| Canvas State           | Use `save()` / `restore()`   |

---

## 📌 Famous JavaScript Quirks / WTFs

| Code                 | Result                | Why?                     |
| -------------------- | --------------------- | ------------------------ |
| `typeof null`        | `"object"`            | Historical Bug           |
| `[] + []`            | `""`                  | Array → String           |
| `[] + {}`            | `"[object Object]"`   | Type Coercion            |
| `{}` + []            | `0`                   | Parsed As Empty Block    |
| `1 + "1"`            | `"11"`                | Number → String          |
| `"5" - 1`            | `4`                   | String → Number          |
| `"5" + 1`            | `"51"`                | String Concatenation     |
| `true + true`        | `2`                   | `true = 1`               |
| `false + false`      | `0`                   | `false = 0`              |
| `[] == false`        | `true`                | Type Coercion            |
| `"" == 0`            | `true`                | Type Coercion            |
| `null == undefined`  | `true`                | Special Equality Rule    |
| `null === undefined` | `false`               | Different Types          |
| `NaN === NaN`        | `false`               | NaN Never Equals Itself  |
| `0.1 + 0.2`          | `0.30000000000000004` | Floating Point Precision |
