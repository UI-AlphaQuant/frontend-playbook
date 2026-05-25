## 📌 Introduction to GSAP

- GSAP (GreenSock Animation Platform) is a high-performance JavaScript animation library used for smooth UI, SVG, scroll, and complex timeline animations.
- GSAP offers free core features with optional premium plugins via Club GSAP.

### Plans & Features

| Feature / Plugin | Free | Paid (Club GSAP) | Usage                 |
| ---------------- | ---- | ---------------- | --------------------- |
| Core GSAP        | ✅   | ✅               | Basic animations      |
| Timelines        | ✅   | ✅               | Sequence animations   |
| Easing           | ✅   | ✅               | Motion control        |
| ScrollTrigger    | ✅   | ✅               | Scroll animations     |
| React Support    | ✅   | ✅               | React integration     |
| SVG Animations   | ✅   | ✅               | SVG motion            |
| MatchMedia       | ✅   | ✅               | Responsive animations |
| SplitText        | ❌   | ✅               | Text splitting        |
| MorphSVG         | ❌   | ✅               | SVG morphing          |
| DrawSVG          | ❌   | ✅               | SVG stroke animation  |
| GSDevTools       | ❌   | ✅               | Animation debugging   |
| Physics2D        | ❌   | ✅               | Physics motion        |
| PhysicsProps     | ❌   | ✅               | Realistic movement    |
| InertiaPlugin    | ❌   | ✅               | Momentum effects      |
| ScrollSmoother   | ❌   | ✅               | Smooth scrolling      |
| ScrambleText     | ❌   | ✅               | Text scramble effects |

### What GSAP Can Animate

| Type           | Example              |
| -------------- | -------------------- |
| DOM Elements   | Divs, buttons, cards |
| CSS Properties | Opacity, transform   |
| SVG            | Paths, shapes        |
| Canvas         | Game/UI animations   |
| WebGL          | Three.js objects     |
| Scroll         | Scroll-based effects |

### Why Use GSAP

| Feature           | Usage                       |
| ----------------- | --------------------------- |
| Tween Animations  | Animate elements/properties |
| Timelines         | Sequence animations         |
| Scroll Animations | ScrollTrigger plugin        |
| SVG Support       | Animate paths/shapes        |
| Framework Support | React, Vue, Angular         |
| High Performance  | Smooth 60fps animations     |

### Core Concepts

| Concept  | Description                 |
| -------- | --------------------------- |
| Tween    | Single animation            |
| Timeline | Multiple animation sequence |
| Target   | Element/object to animate   |
| Ease     | Animation motion style      |
| Plugin   | Extra GSAP features         |

### Installation

| Method | Syntax                                                 |
| ------ | ------------------------------------------------------ |
| NPM    | `npm install gsap`                                     |
| CDN    | `https://cdn.jsdelivr.net/npm/gsap@3/dist/gsap.min.js` |

```js
// Import
// core
import gsap from "gsap";

// plugin
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);
```

```js
// animate to values
gsap.to(".box", {
  x: 200,
  duration: 1,
});

// animate from values
gsap.from(".box", {
  opacity: 0,
  y: 100,
  duration: 1,
});

// timeline animation
const tl = gsap.timeline();
tl.to(".box", { x: 100 }).to(".circle", { rotation: 360 });
```

- Prefer `x/y/scale` over `top/left`
- Use timelines for complex animations
- Register plugins once globally
- Avoid animating layout-heavy properties
- Cleanup animations in frameworks

| Use Case           | Example                |
| ------------------ | ---------------------- |
| Landing Pages      | Hero animations        |
| Dashboards         | Card/chart transitions |
| UI Interactions    | Hover/click effects    |
| Storytelling Sites | Scroll animations      |
| SVG Graphics       | Logo/icon animations   |
| Loaders            | Intro animations       |

---

## 📌 Installation

Install GSAP using CDN or package manager for Vanilla JS and React projects.

### Core (Vanilla JS)

| Method | Syntax                                                 |
| ------ | ------------------------------------------------------ |
| NPM    | `npm install gsap`                                     |
| Yarn   | `yarn add gsap`                                        |
| PNPM   | `pnpm add gsap`                                        |
| CDN    | `https://cdn.jsdelivr.net/npm/gsap@3/dist/gsap.min.js` |

```html
<!-- GSAP Core -->
<script src="https://cdn.jsdelivr.net/npm/gsap@3/dist/gsap.min.js"></script>

<!-- ScrollTrigger Plugin -->
<script src="https://cdn.jsdelivr.net/npm/gsap@3/dist/ScrollTrigger.min.js"></script>
```

### Core Import

```js
import gsap from "gsap"; // gsap core
import { ScrollTrigger } from "gsap/ScrollTrigger"; // plugin

gsap.registerPlugin(ScrollTrigger);
```

### React Installation

| Package       | Usage                  |
| ------------- | ---------------------- |
| `gsap`        | Core animation library |
| `@gsap/react` | React hook utilities   |

```bash
npm install gsap @gsap/react
```

```jsx
// React Import
import gsap from "gsap"; // gsap
import { useGSAP } from "@gsap/react"; // react hook
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(useGSAP, ScrollTrigger);
```

```jsx
// Basic React Setup
import { useRef } from "react";
import gsap from "gsap";
import { useGSAP } from "@gsap/react";

function App() {
  const container = useRef();

  useGSAP(
    () => {
      gsap.to(".box", {
        x: 200,
        duration: 1,
      });
    },
    { scope: container },
  );

  return (
    <div ref={container}>
      <div className="box">Box</div>
    </div>
  );
}

export default App;
```

- Register plugins once globally
- Prefer `useGSAP()` in React
- Scope animations in React using refs
- Use tree-shakable imports
- Cleanup animations on component unmount

---

## 📌 Core Concepts

GSAP animations are built using tweens, timelines, targets, eases, and plugins.

| Concept  | Usage                               |
| -------- | ----------------------------------- |
| Tween    | Single animation                    |
| Timeline | Sequence multiple animations        |
| Target   | Element/object being animated       |
| Ease     | Motion style/speed                  |
| Plugin   | Extra GSAP functionality            |
| Duration | Animation time                      |
| Delay    | Wait before animation               |
| Stagger  | Animate multiple items sequentially |

```js
// tween
gsap.to(".box", {
  x: 200,
  duration: 1,
});

// timeline
const tl = gsap.timeline();
tl.to(".box", { x: 100 }).to(".circle", { rotation: 360 });
```

- Use timelines for complex flows
- Prefer transform properties
- Keep animations reusable
- Use plugins only when needed

### Tween Animations

Tween is the basic GSAP animation that animates properties from one state to another.

| Tween Methods   | Usage                     |
| --------------- | ------------------------- |
| `gsap.to()`     | Current → target values   |
| `gsap.from()`   | Given → current values    |
| `gsap.fromTo()` | Custom start → end values |
| `gsap.set()`    | Instantly set values      |

| Properties | Usage            |
| ---------- | ---------------- |
| `x`, `y`   | Position         |
| `scale`    | Resize           |
| `rotation` | Rotate           |
| `opacity`  | Fade             |
| `duration` | Animation time   |
| `delay`    | Delay start      |
| `ease`     | Motion effect    |
| `repeat`   | Repeat animation |
| `yoyo`     | Reverse repeat   |

```js
// to
gsap.to(".box", {
  x: 200,
  duration: 1,
});

// from
gsap.from(".box", {
  opacity: 0,
  y: 100,
});

// fromTo
gsap.fromTo(".box", { scale: 0 }, { scale: 1, duration: 1 });

// set
gsap.set(".box", {
  opacity: 0,
});
```

| Use Case        | Example          |
| --------------- | ---------------- |
| Fade In         | Cards/modals     |
| Slide Animation | Menus/sidebar    |
| Hover Effect    | Buttons/images   |
| Loader          | Repeating motion |

- Prefer `x/y` over `left/top`
- Keep durations consistent
- Avoid excessive repeats
- Use easing for natural motion

---

## 📌 Basic Animation Methods

GSAP provides multiple methods for animating elements between different states.

| Method          | Usage                             |
| --------------- | --------------------------------- |
| `gsap.to()`     | Animate current → target values   |
| `gsap.from()`   | Animate given → current values    |
| `gsap.fromTo()` | Animate custom start → end values |
| `gsap.set()`    | Instantly set values              |

| gsap.to() | Example    |
| --------- | ---------- |
| Move      | `x`, `y`   |
| Resize    | `scale`    |
| Rotate    | `rotation` |
| Fade      | `opacity`  |

| gsap.from()          | Example       |
| -------------------- | ------------- |
| Entry Animation      | Fade/slide in |
| Initial Hidden State | `opacity: 0`  |
| Scale Intro          | `scale: 0`    |

| gsap.fromTo()    | Example             |
| ---------------- | ------------------- |
| Explicit Control | Custom start/end    |
| Reset States     | Reusable animations |
| Dynamic Motion   | Complex transitions |

| gsap.set()       | Example        |
| ---------------- | -------------- |
| Initial State    | Hide elements  |
| Immediate Update | No animation   |
| Reset Animation  | Restore values |

```js
// set initial state
gsap.set(".box", { opacity: 0 });

// entry animation
gsap.from(".box", {
  y: 100,
  opacity: 0,
  duration: 1,
});

// hover animation
gsap.to(".box", {
  scale: 1.1,
  duration: 0.3,
});

// custom animation
gsap.fromTo(".circle", { rotation: 0 }, { rotation: 360, duration: 2 });
```

- Use `set()` for initial states
- Prefer `to()` for most animations
- Use `fromTo()` for explicit control
- Animate transform properties for performance

---

## 📌 Animation Properties

GSAP animation properties control motion, timing, transforms, and visual effects.

### Animation Properties

| Property      | Usage                  | Example                     |
| ------------- | ---------------------- | --------------------------- |
| `duration`    | Animation time         | `duration: 1`               |
| `delay`       | Delay start            | `delay: 0.5`                |
| `ease`        | Motion style           | `ease: "power2.out"`        |
| `repeat`      | Repeat animation       | `repeat: -1`                |
| `repeatDelay` | Delay between repeats  | `repeatDelay: 1`            |
| `yoyo`        | Reverse animation      | `yoyo: true`                |
| `stagger`     | Animate sequentially   | `stagger: 0.2`              |
| `paused`      | Start paused           | `paused: true`              |
| `defaults`    | Shared timeline values | `defaults: { duration: 1 }` |

### CSS Properties

| Property          | Usage            | Example                      |
| ----------------- | ---------------- | ---------------------------- |
| `opacity`         | Fade effect      | `opacity: 0`                 |
| `backgroundColor` | Background color | `backgroundColor: "red"`     |
| `color`           | Text color       | `color: "#fff"`              |
| `width`           | Element width    | `width: 300`                 |
| `height`          | Element height   | `height: 200`                |
| `borderRadius`    | Rounded corners  | `borderRadius: "50%"`        |
| `boxShadow`       | Shadow effect    | `boxShadow: "0 0 20px #000"` |

### Transform Properties

| Property          | Usage            | Example                     |
| ----------------- | ---------------- | --------------------------- |
| `x`               | Horizontal move  | `x: 200`                    |
| `y`               | Vertical move    | `y: 100`                    |
| `scale`           | Resize element   | `scale: 1.5`                |
| `scaleX`          | Horizontal scale | `scaleX: 2`                 |
| `scaleY`          | Vertical scale   | `scaleY: 0.5`               |
| `rotation`        | Rotate element   | `rotation: 360`             |
| `rotationX`       | 3D X rotation    | `rotationX: 45`             |
| `rotationY`       | 3D Y rotation    | `rotationY: 45`             |
| `skewX`           | Horizontal skew  | `skewX: 20`                 |
| `skewY`           | Vertical skew    | `skewY: 10`                 |
| `transformOrigin` | Transform center | `transformOrigin: "center"` |

```js
gsap.to(".box", {
  // animation
  duration: 1,
  delay: 0.5,
  ease: "power2.out",

  // css
  opacity: 1,
  backgroundColor: "#000",

  // transforms
  x: 200,
  y: 100,
  scale: 1.2,
  rotation: 360,
});
```

---

## 📌 Timing & Motion

Timing and motion properties control animation speed, flow, repetition, and realism.

| Ease             | Usage            |
| ---------------- | ---------------- |
| `"none"`         | Linear motion    |
| `"power1.out"`   | Smooth end       |
| `"power2.inOut"` | Smooth start/end |
| `"bounce.out"`   | Bounce effect    |
| `"elastic.out"`  | Elastic effect   |
| `"back.out"`     | Overshoot effect |

### Duration & Delay

| Property   | Usage           | Example       |
| ---------- | --------------- | ------------- |
| `duration` | Animation time  | `duration: 1` |
| `delay`    | Delay animation | `delay: 0.5`  |

### Repeat & Yoyo

| Property      | Usage                 | Example          |
| ------------- | --------------------- | ---------------- |
| `repeat`      | Repeat animation      | `repeat: -1`     |
| `repeatDelay` | Delay between repeats | `repeatDelay: 1` |
| `yoyo`        | Reverse on repeat     | `yoyo: true`     |

```js
// floating animation
gsap.to(".card", {
  y: -20,
  duration: 1,
  ease: "power1.inOut",
  repeat: -1,
  yoyo: true,
});

// delayed fade
gsap.from(".title", {
  opacity: 0,
  y: 50,
  duration: 1,
  delay: 0.3,
  ease: "back.out",
});
```

| Feature | Example            |
| ------- | ------------------ |
| Easing  | Smooth UI motion   |
| Delay   | Staggered sections |
| Repeat  | Loaders/spinners   |
| Yoyo    | Floating elements  |

- Use subtle easing for UI animations
- Keep durations consistent
- Avoid excessive bounce/elastic effects
- Use infinite repeat carefully

---

## 📌 Animation Techniques

GSAP provides stagger and keyframe animations for creating smooth sequential and multi-step motion effects.

### Stagger Animations

Animate multiple elements one after another with automatic delay.

| Property  | Usage               | Example          |
| --------- | ------------------- | ---------------- |
| `stagger` | Delay between items | `stagger: 0.2`   |
| `each`    | Delay per item      | `each: 0.1`      |
| `from`    | Start position      | `from: "center"` |
| `grid`    | Grid staggering     | `grid: [3,3]`    |
| `axis`    | Direction control   | `axis: "x"`      |

### Stagger Directions

| Value      | Usage          |
| ---------- | -------------- |
| `"start"`  | First → last   |
| `"end"`    | Last → first   |
| `"center"` | Center outward |
| `"edges"`  | Edges inward   |
| `"random"` | Random order   |

```js
// stagger animation
gsap.from(".card", {
  opacity: 0,
  y: 50,
  scale: 0.9,
  duration: 0.8,
  stagger: {
    each: 0.15,
    from: "start",
  },
  ease: "power2.out",
});
```

### Keyframes

Create multi-step animations inside a single tween.

| Property    | Usage                     |
| ----------- | ------------------------- |
| `keyframes` | Multiple animation states |
| `duration`  | Total animation time      |
| `ease`      | Motion easing             |

```js
// keyframe animation
gsap.to(".loader", {
  keyframes: [
    { scale: 1.2, duration: 0.3 },
    { rotation: 180, duration: 0.5 },
    { scale: 1, rotation: 360, duration: 0.5 },
  ],
  repeat: -1,
  ease: "power1.inOut",
});
```

| Feature           | Example                   |
| ----------------- | ------------------------- |
| Stagger           | Card/list animations      |
| Keyframes         | Loaders/multi-step motion |
| Grid Stagger      | Gallery animations        |
| Sequential Motion | Hero sections             |

- Use small stagger values for smooth UI
- Avoid excessive keyframe steps
- Keep motion natural and readable
- Combine stagger with opacity/transforms

---

## 📌 Callback Functions

GSAP callbacks allow executing logic during different animation lifecycle stages.

| Callback Methods    | Usage                         |
| ------------------- | ----------------------------- |
| `onStart`           | Trigger when animation starts |
| `onUpdate`          | Trigger on every frame        |
| `onComplete`        | Trigger after animation ends  |
| `onRepeat`          | Trigger on repeat             |
| `onReverseComplete` | Trigger after reverse ends    |

```js
gsap.to(".box", {
  x: 300,
  duration: 2,
  repeat: 1,

  onStart: () => {
    console.log("Animation Started");
  },

  onUpdate: () => {
    console.log("Animating...");
  },

  onComplete: () => {
    console.log("Animation Completed");
  },

  onRepeat: () => {
    console.log("Animation Repeated");
  },
});
```

- Keep callbacks lightweight
- Avoid heavy DOM operations in `onUpdate`
- Use callbacks for animation flow control

---

## 📌 Utility Methods

GSAP utility methods help control, optimize, and manage animations efficiently.

| Method                | Usage                    |
| --------------------- | ------------------------ |
| `gsap.set()`          | Instantly set values     |
| `gsap.killTweensOf()` | Stop animations          |
| `gsap.delayedCall()`  | Run function after delay |
| `gsap.getProperty()`  | Get animated property    |
| `gsap.quickTo()`      | Smooth frequent updates  |
| `gsap.quickSetter()`  | High-performance setter  |

```js
// set initial state
gsap.set(".box", {
  opacity: 0,
  x: 100,
});

// delayed animation
gsap.delayedCall(1, () => {
  gsap.to(".box", {
    opacity: 1,
    x: 0,
    duration: 1,
  });
});

// stop animation
gsap.killTweensOf(".box");

// get property
const x = gsap.getProperty(".box", "x");
console.log(x);

// fast setter
const setX = gsap.quickSetter(".cursor", "x", "px");
const setY = gsap.quickSetter(".cursor", "y", "px");

window.addEventListener("mousemove", (e) => {
  setX(e.clientX);
  setY(e.clientY);
});
```

- Use `quickSetter()` for mousemove animations
- Kill animations during cleanup
- Prefer `set()` over direct DOM styles
- Avoid unnecessary repeated tweens

---

## 📌 Timelines

GSAP timelines help sequence and control multiple animations efficiently.

| Method            | Usage                  |
| ----------------- | ---------------------- |
| `gsap.timeline()` | Create timeline        |
| `.to()`           | Animate to values      |
| `.from()`         | Animate from values    |
| `.fromTo()`       | Animate custom values  |
| `.set()`          | Instantly set values   |
| `.add()`          | Add animation/callback |
| `.call()`         | Run function           |

| Timeline Controls | Usage              |
| ----------------- | ------------------ |
| `.play()`         | Start animation    |
| `.pause()`        | Pause animation    |
| `.resume()`       | Continue animation |
| `.reverse()`      | Reverse animation  |
| `.restart()`      | Restart animation  |
| `.seek()`         | Jump to position   |
| `.kill()`         | Destroy timeline   |

### Timeline Positioning

| Value     | Usage                |
| --------- | -------------------- |
| `"+=1"`   | Delay next animation |
| `"-=0.5"` | Overlap animation    |
| `"<"`     | Start with previous  |
| `">"`     | Start after previous |

```js
// Timeline Position
const tl = gsap.timeline();

tl.to(".box", {
  x: 200,
  duration: 1,
})

  .to(
    ".circle",
    {
      rotation: 360,
      duration: 1,
    },
    "-=0.5",
  )

  .from(
    ".title",
    {
      opacity: 0,
      y: 50,
    },
    "<",
  );

// Control Example
const tl = gsap.timeline({ paused: true });

tl.to(".box", {
  x: 300,
  duration: 1,
});

// controls
tl.play();
tl.pause();
tl.reverse();
```

- Use timelines for related animations
- Set shared defaults in timelines
- Keep animation sequences organized
- Prefer positioning over manual delays
- Reuse timeline configs when possible

### Nested Timelines

Nested timelines help organize complex animation sequences into reusable timeline modules.

| Benefit         | Usage                       |
| --------------- | --------------------------- |
| Reusability     | Reuse animation blocks      |
| Maintainability | Cleaner animation structure |
| Scalability     | Manage complex animations   |
| Modularity      | Separate sections logically |

```js
// Hero Animation
const heroTl = gsap.timeline();
heroTl
  .from(".title", {
    opacity: 0,
    y: 50,
    duration: 1,
  })
  .from(".subtitle", {
    opacity: 0,
    y: 30,
    duration: 0.8,
  });

// Cards Animation
const cardsTl = gsap.timeline();
cardsTl.from(".card", {
  opacity: 0,
  y: 50,
  stagger: 0.2,
  duration: 0.8,
});

// Main Timeline
const masterTl = gsap.timeline();
masterTl.add(heroTl).add(cardsTl, "-=0.5");
```

- Split large animations into smaller timelines
- Use reusable timeline functions
- Keep nested timelines focused
- Use master timeline for orchestration
- Avoid deeply nested structures

---

## 📌 Responsive & Context APIs

GSAP provides context and responsive APIs for scoped, adaptive, and cleanup-friendly animations.

### Responsive & Context APIs

| API                 | Usage                 |
| ------------------- | --------------------- |
| `gsap.context()`    | Scope animations      |
| `gsap.matchMedia()` | Responsive animations |
| `context.revert()`  | Cleanup animations    |

### gsap.context()

Scopes selectors and animations to a specific container.

```js
const container = document.querySelector(".wrapper");

const ctx = gsap.context(() => {
  gsap.from(".box", {
    opacity: 0,
    y: 50,
    stagger: 0.2,
  });
}, container);

// cleanup
ctx.revert();
```

### gsap.matchMedia()

```js
const mm = gsap.matchMedia();

mm.add("(min-width: 768px)", () => {
  gsap.to(".box", {
    x: 300,
    duration: 1,
  });
});

mm.add("(max-width: 767px)", () => {
  gsap.to(".box", {
    y: 200,
    duration: 1,
  });
});
```

### React

```js
import { useRef } from "react";
import gsap from "gsap";
import { useGSAP } from "@gsap/react";

function App() {
  const container = useRef();

  useGSAP(
    () => {
      gsap.from(".box", {
        opacity: 0,
        y: 50,
      });
    },
    { scope: container },
  );

  return (
    <div ref={container}>
      <div className="box">Box</div>
    </div>
  );
}
```

- Scope animations using `context()`
- Use `matchMedia()` instead of manual resize listeners
- Keep mobile animations lightweight
- Respect reduced motion preferences
- Cleanup animations properly
- Avoid duplicate animation logic

---

## 📌 Scroll Animations

GSAP scroll animations create motion effects triggered and controlled by page scrolling.

| ScrollTrigger Properties | Usage                    |
| ------------------------ | ------------------------ |
| `trigger`                | Trigger element          |
| `start`                  | Animation start position |
| `end`                    | Animation end position   |
| `scrub`                  | Sync with scroll         |
| `pin`                    | Pin section              |
| `markers`                | Debug markers            |
| `toggleActions`          | Scroll behavior          |

```js
// Basic Scroll Animation
gsap.to(".box", {
  x: 300,

  scrollTrigger: {
    trigger: ".box",
    start: "top center",
    end: "bottom top",
    scrub: true,
  },
});
```

```js
// Stagger Scroll Animation
gsap.from(".card", {
  opacity: 0,
  y: 100,
  stagger: 0.2,

  scrollTrigger: {
    trigger: ".cards",
    start: "top 80%",
  },
});
```

### Scrub & Pin

- `scrub` and `pin` control how animations behave while scrolling.
- `scrub` connects animation progress directly with scroll position.
- `scrub` controls animation progress with scroll, while `pin` keeps an element fixed during scrolling.

| Feature      | What GSAP Does                              |
| ------------ | ------------------------------------------- |
| `scrub`      | Links scroll distance to animation progress |
| `pin`        | Temporarily makes section fixed/sticky      |
| `pinSpacing` | Adds temporary spacer below section         |

| Value  | Usage                       |
| ------ | --------------------------- |
| `true` | Exact scroll syncing        |
| `1`    | Smooth delay effect         |
| `2`    | More smooth/slower catch-up |

| Scroll Action  | `scrub`              | `pin`                  |
| -------------- | -------------------- | ---------------------- |
| Scroll down    | Animation progresses | Section stays fixed    |
| Scroll up      | Animation reverses   | Section still pinned   |
| Stop scrolling | Animation stops      | Section remains pinned |
| End reached    | Animation completes  | Section unpins         |

```js
// Pin Section
gsap.to(".section", {
  scale: 1.2,

  scrollTrigger: {
    trigger: ".section",
    start: "top top",
    end: "+=100%",
    pin: true,
    scrub: true,
  },
});
```

- Use `scrub` for interactive motion
- Use `pin` for sticky section effects
- Combine both for storytelling experiences
- Avoid pinning too many sections
- Keep scrub animations lightweight

```js
// Scroll Timeline
const tl = gsap.timeline({
  scrollTrigger: {
    trigger: ".hero",
    start: "top top",
    end: "+=100%",
    pin: true,
    scrub: true,
  },
});

tl.to(".title", {
  scale: 1.2,
})

  .to(
    ".image",
    {
      y: -100,
    },
    "-=0.5",
  );
```

```js
// toggleActions
gsap.from(".box", {
  opacity: 0,

  scrollTrigger: {
    trigger: ".box",
    start: "top 80%",
    toggleActions: "play none none reset",
  },
});
```

```js
// markers
gsap.to(".box", {
  x: 200,

  scrollTrigger: {
    trigger: ".box",
    start: "top center",
    markers: true,
  },
});
```

- Register plugins once globally
- Use `scrub` carefully for performance
- Avoid excessive pinned sections
- Use `markers` only during development
- Prefer transform animations
- Keep mobile animations lightweight

---

## 📌 SVG & Motion Graphics

GSAP provides powerful tools for animating SVG elements, paths, and motion-based graphics.

| SVG Animation Features | Usage                 |
| ---------------------- | --------------------- |
| SVG Elements           | Animate shapes/icons  |
| Motion Paths           | Move along paths      |
| Morphing               | Shape transformation  |
| Draw Effects           | SVG stroke animation  |
| Transform Control      | Rotate/scale/move SVG |

| SVG Properties     | Usage           |
| ------------------ | --------------- |
| `x`, `y`           | Move SVG        |
| `scale`            | Resize SVG      |
| `rotation`         | Rotate SVG      |
| `opacity`          | Fade SVG        |
| `transformOrigin`  | Rotation center |
| `strokeDashoffset` | Draw effect     |

```js
// Basic SVG Animation
gsap.to("#circle", {
  x: 200,
  rotation: 360,
  duration: 2,
});

// SVG Fade & Scale
gsap.from("#logo", {
  opacity: 0,
  scale: 0,
  duration: 1,
  ease: "back.out",
});

// Motion Path Animation
gsap.to(".ball", {
  duration: 3,

  motionPath: {
    path: "#path",
    align: "#path",
    autoRotate: true,
  },
});

// Draw SVG Effect
gsap.from(".path", {
  strokeDashoffset: 1000,
  duration: 2,
});

// SVG Timeline
const tl = gsap.timeline();

tl.from("#logo", {
  opacity: 0,
  scale: 0,
})
  .to("#circle", {
    x: 100,
    rotation: 360,
  })
  .from(".path", {
    strokeDashoffset: 500,
  });
```

- Use `transformOrigin: "center"`
- Optimize SVG before animating
- Prefer transforms over layout changes
- Keep SVG paths lightweight
- Use timelines for complex sequences

---

## 📌 UI & Interaction Animations

GSAP helps create smooth UI interactions, hover effects, loaders, transitions, and engaging micro animations.

| UI Animation Features | Usage              |
| --------------------- | ------------------ |
| Hover Effects         | Buttons/cards      |
| Fade In               | Sections/modals    |
| Text Reveal           | Hero titles        |
| Stagger Effects       | Lists/cards        |
| Loader Animations     | Spinners/progress  |
| Cursor Effects        | Interactive UI     |
| Page Transitions      | Route/page changes |
| Floating Motion       | Cards/icons        |

| Common Properties | Usage                |
| ----------------- | -------------------- |
| `opacity`         | Fade effect          |
| `x`, `y`          | Move elements        |
| `scale`           | Resize element       |
| `rotation`        | Rotate element       |
| `stagger`         | Sequential animation |
| `repeat`          | Infinite motion      |
| `yoyo`            | Reverse animation    |

```js
// Hover Animation
const card = document.querySelector(".card");

card.addEventListener("mouseenter", () => {
  gsap.to(card, {
    scale: 1.05,
    y: -10,
    duration: 0.3,
  });
});

card.addEventListener("mouseleave", () => {
  gsap.to(card, {
    scale: 1,
    y: 0,
    duration: 0.3,
  });
});

// Text Reveal
gsap.from(".title", {
  opacity: 0,
  y: 100,
  duration: 1,
  ease: "power3.out",
});

// Stagger Cards
gsap.from(".card", {
  opacity: 0,
  y: 50,
  stagger: 0.15,
  duration: 0.8,
});

// Loader Animation
gsap.to(".loader", {
  rotation: 360,
  repeat: -1,
  duration: 1,
  ease: "none",
});

// Cursor Follow
const cursor = document.querySelector(".cursor");

window.addEventListener("mousemove", (e) => {
  gsap.to(cursor, {
    x: e.clientX,
    y: e.clientY,
    duration: 0.2,
  });
});

// Page Transition
const tl = gsap.timeline();

tl.to(".page", {
  opacity: 0,
  y: -50,
})

  .from(".next-page", {
    opacity: 0,
    y: 50,
  });
```

- Keep UI animations subtle
- Use short durations for interactions
- Prefer transforms for performance
- Avoid excessive motion
- Maintain consistent animation timing

---

## 📌 Split Text Animations

Split text animations animate words, lines, or characters individually for dynamic text effects.

| Split Animation Features | Usage                      |
| ------------------------ | -------------------------- |
| Character Animation      | Animate each letter        |
| Word Animation           | Animate words sequentially |
| Line Animation           | Animate text lines         |
| Stagger Effects          | Sequential motion          |
| Text Reveal              | Hero headings              |
| Mask Animations          | Smooth reveal effects      |

| Common Properties | Usage                |
| ----------------- | -------------------- |
| `stagger`         | Sequential animation |
| `opacity`         | Fade effect          |
| `y`               | Vertical motion      |
| `rotation`        | Rotate characters    |
| `scale`           | Resize text          |
| `duration`        | Animation speed      |

```js
// SplitText Plugin
import gsap from "gsap";
import SplitText from "gsap/SplitText";

gsap.registerPlugin(SplitText);

// Split Characters
const split = new SplitText(".title", {
  type: "chars",
});

gsap.from(split.chars, {
  opacity: 0,
  y: 100,
  rotation: 10,
  stagger: 0.05,
  duration: 1,
  ease: "power3.out",
});

// Split Words
const words = new SplitText(".subtitle", {
  type: "words",
});

gsap.from(words.words, {
  opacity: 0,
  y: 50,
  stagger: 0.1,
  duration: 0.8,
});

// Split Lines
const lines = new SplitText(".text", {
  type: "lines",
});

gsap.from(lines.lines, {
  opacity: 0,
  y: 30,
  stagger: 0.15,
  duration: 1,
});

// Timeline Text Animation
const tl = gsap.timeline();

tl.from(split.chars, {
  y: 100,
  opacity: 0,
  stagger: 0.03,
})

  .from(
    words.words,
    {
      opacity: 0,
      stagger: 0.08,
    },
    "-=0.5",
  );
```

- Use small stagger values for readability
- Prefer word/line animations over excessive character motion
- Keep text animations fast and smooth
- Avoid heavy rotations/scaling on large text
- Use timelines for multi-text sequences

---

## 📌 Advanced Motion

GSAP advanced motion features help create realistic, interactive, and high-end animation experiences.

| Advanced Motion Features | Usage                    |
| ------------------------ | ------------------------ |
| Physics Motion           | Natural movement         |
| Flip Animations          | Layout transitions       |
| Draggable                | Drag interactions        |
| Observer                 | Gesture/scroll detection |
| Inertia Motion           | Momentum effects         |
| Motion Paths             | Complex movement         |
| 3D Motion                | Depth interactions       |

| Common Plugins     | Usage                    |
| ------------------ | ------------------------ |
| `Flip`             | State/layout transitions |
| `Draggable`        | Drag & drop              |
| `Observer`         | Scroll/touch events      |
| `InertiaPlugin`    | Momentum effects         |
| `MotionPathPlugin` | Path animations          |

```js
// Flip Animation
import { Flip } from "gsap/Flip";
gsap.registerPlugin(Flip);

const state = Flip.getState(".card");
container.appendChild(document.querySelector(".card"));

Flip.from(state, {
  duration: 0.8,
  ease: "power2.inOut",
});

// Draggable
import { Draggable } from "gsap/Draggable";
gsap.registerPlugin(Draggable);

Draggable.create(".box", {
  type: "x,y",
  inertia: true,
});

// Observer
import { Observer } from "gsap/Observer";
gsap.registerPlugin(Observer);

Observer.create({
  target: window,

  onUp: () => {
    console.log("Scroll Up");
  },

  onDown: () => {
    console.log("Scroll Down");
  },
});

// Physics Motion
gsap.to(".ball", {
  y: 500,
  duration: 2,
  ease: "bounce.out",
});

// Motion Path
gsap.to(".object", {
  duration: 3,

  motionPath: {
    path: "#path",
    autoRotate: true,
  },
});
```

- Use advanced motion sparingly
- Keep interactions smooth and responsive
- Prefer subtle physics effects
- Avoid excessive motion complexity
- Optimize draggable and observer events

---

## 📌 Canvas & Graphics

GSAP can animate Canvas, WebGL, and graphics-based elements for high-performance visual effects.

| Canvas & Graphics Features | Usage                 |
| -------------------------- | --------------------- |
| Canvas Animation           | Draw/animate shapes   |
| Particle Effects           | Interactive particles |
| Game Motion                | Object movement       |
| Three.js Integration       | 3D animations         |
| WebGL Effects              | GPU graphics          |
| Render Loop Control        | Smooth rendering      |

| Properties | Usage           |
| ---------- | --------------- |
| `x`, `y`   | Position        |
| `rotation` | Rotate objects  |
| `scale`    | Resize graphics |
| `opacity`  | Fade effects    |
| `duration` | Animation speed |
| `repeat`   | Infinite motion |

```js
// Canvas Animation
const canvas = document.querySelector("canvas");
const ctx = canvas.getContext("2d");
const circle = {
  x: 100,
  y: 100,
  radius: 30,
};

gsap.to(circle, {
  x: 500,
  duration: 2,

  onUpdate: render,
});

function render() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);

  ctx.beginPath();
  ctx.arc(circle.x, circle.y, circle.radius, 0, Math.PI * 2);
  ctx.fill();
}

// Particle Motion
const particle = {
  x: 0,
  y: 0,
};

gsap.to(particle, {
  x: 300,
  y: 200,
  repeat: -1,
  yoyo: true,
  duration: 2,
});

// Three.js Animation
gsap.to(mesh.rotation, {
  y: Math.PI * 2,
  duration: 3,
  repeat: -1,
  ease: "none",
});

// WebGL Uniform Animation
gsap.to(material.uniforms.uProgress, {
  value: 1,
  duration: 2,
});
```

- Use GSAP for animation logic, not rendering
- Keep canvas redraws lightweight
- Use `onUpdate()` for render loops
- Prefer GPU-friendly transforms
- Optimize particle counts for performance

---

## 📌 Framework Integration

GSAP works smoothly with modern frameworks for component-based and lifecycle-safe animations.

| Framework Integration | Usage                      |
| --------------------- | -------------------------- |
| React                 | Component animations       |
| Vue                   | Reactive animations        |
| Angular               | Lifecycle-based animations |
| Next.js               | Client-side motion         |
| useGSAP               | React animation hook       |
| Refs                  | Scoped element targeting   |

| Common APIs         | Usage             |
| ------------------- | ----------------- |
| `useGSAP()`         | React GSAP hook   |
| `useRef()`          | Element reference |
| `gsap.context()`    | Scoped animations |
| `onMounted()`       | Vue setup         |
| `ngAfterViewInit()` | Angular setup     |

```js
// React
import { useRef } from "react";
import gsap from "gsap";
import { useGSAP } from "@gsap/react";

function App() {
  const container = useRef();

  useGSAP(
    () => {
      gsap.from(".box", {
        opacity: 0,
        y: 50,
        duration: 1,
      });
    },
    { scope: container },
  );

  return (
    <div ref={container}>
      <div className="box">Box</div>
    </div>
  );
}
```

```js
// Vue
import { ref, onMounted } from "vue";
import gsap from "gsap";

const box = ref(null);

onMounted(() => {
  gsap.from(box.value, {
    opacity: 0,
    y: 50,
    duration: 1,
  });
});
```

```js
// Angular
import { AfterViewInit, ElementRef } from "@angular/core";
import gsap from "gsap";

export class AppComponent implements AfterViewInit {
  constructor(private el: ElementRef) {}

  ngAfterViewInit() {
    gsap.from(this.el.nativeElement.querySelector(".box"), {
      opacity: 0,
      y: 50,
      duration: 1,
    });
  }
}
```

```js
// Next.js Client Component
"use client";

import gsap from "gsap";
```

- Scope animations using refs/context
- Cleanup animations on unmount
- Use `useGSAP()` in React projects
- Avoid global selectors in components
- Run animations after component mount

---

## 📌 Performance & Optimization

Optimize GSAP animations for smooth rendering, lower CPU usage, and better user experience.

| Performance Features  | Usage              |
| --------------------- | ------------------ |
| Transform Animations  | GPU acceleration   |
| Opacity Animations    | Cheap rendering    |
| Timeline Control      | Fewer reflows      |
| quickSetter           | Fast updates       |
| requestAnimationFrame | Smooth rendering   |
| Lazy Rendering        | Better performance |

| ❌ Avoid                 | ✅ Prefer           |
| ------------------------ | ------------------- |
| `top/left`               | `x/y` transforms    |
| `width/height` animation | `scale` transforms  |
| Heavy box-shadows        | Lightweight effects |
| Multiple layout updates  | Batched animations  |
| Excessive scroll effects | Optimized triggers  |

```js
// ✅ Prefer transforms
gsap.to(".box", {
  x: 300,
  y: 100,
  scale: 1.2,
  duration: 1,
});

// ❌ Avoid layout-heavy properties
// bad
gsap.to(".box", {
  left: 300,
  width: 500,
});
```

```js
// quickSetter
const setX = gsap.quickSetter(".cursor", "x", "px");
const setY = gsap.quickSetter(".cursor", "y", "px");

window.addEventListener("mousemove", (e) => {
  setX(e.clientX);
  setY(e.clientY);
});

// Timeline Optimization
const tl = gsap.timeline({
  defaults: {
    duration: 0.6,
    ease: "power2.out",
  },
});

tl.from(".title", {
  opacity: 0,
  y: 50,
})

  .from(
    ".card",
    {
      opacity: 0,
      y: 30,
      stagger: 0.1,
    },
    "-=0.3",
  );

// Scroll Optimization
gsap.to(".section", {
  y: -100,

  scrollTrigger: {
    trigger: ".section",
    scrub: 1,
  },
});
```

- Prefer `transform` and `opacity`
- Use timelines instead of many separate tweens
- Keep stagger values small
- Avoid animating large DOM trees
- Optimize scroll and scrub animations
- Use `quickSetter()` for mousemove effects
- Test animations on mobile devices

---

## 📌 Architecture & Maintainability

Organize GSAP animations for scalability, reusability, and easier long-term maintenance.

| Architecture Patterns | Usage                |
| --------------------- | -------------------- |
| Reusable Functions    | Shared animations    |
| Timelines             | Organized sequences  |
| Animation Configs     | Centralized settings |
| Scoped Animations     | Prevent conflicts    |
| Modular Files         | Better structure     |
| Utility Helpers       | Shared logic         |

| Recommended Structure | Usage                 |
| --------------------- | --------------------- |
| `animations/`         | Animation modules     |
| `timelines/`          | Timeline sequences    |
| `utils/`              | Shared helpers        |
| `constants/`          | Shared configs        |
| `hooks/`              | React animation hooks |

```txt
src/
├─ gsap/
├─── animations/ // fade, hover, scroll, text, loader, parallax, transition
├─── timelines/ // heroTimeline, introTimeline, pageTransition, dashboardTimeline
├─ hooks/ // useFadeAnimation, useScrollAnimation, useHoverAnimation, usePageTransition
├─ utils/ // registerPlugins, mediaQueries, animationDefaults, cleanupAnimations
├─ constants/ // durations, easings, breakpoints, presets
```

```js
// constants/presets.js
export const fadeUp = {
  opacity: 0,
  y: 50,
  duration: 0.8,
  ease: "power2.out",
};

export const scaleIn = {
  opacity: 0,
  scale: 0.8,
  duration: 0.6,
  ease: "back.out(1.7)",
};
```

```js
// animations/fade.js
import gsap from "gsap";
import { fadeUp } from "../constants/presets";

export function animateFadeUp(target, options = {}) {
  return gsap.from(target, {
    ...fadeUp,
    ...options,
  });
}

export function animateCards(target) {
  return gsap.from(target, {
    ...fadeUp,
    stagger: 0.15,
  });
}
```

```js
// timelines/heroTimeline.js
import gsap from "gsap";
import { fadeUp, scaleIn } from "../constants/presets";

export function heroTimeline() {
  const tl = gsap.timeline();

  tl.from(".title", fadeUp)

    .from(
      ".subtitle",
      {
        ...fadeUp,
        y: 30,
      },
      "-=0.4",
    )

    .from(
      ".button",
      {
        ...scaleIn,
      },
      "-=0.3",
    );

  return tl;
}
```

```js
// hooks/useHeroAnimation.js
import { useGSAP } from "@gsap/react";
import { heroTimeline } from "../timelines/heroTimeline";

export function useHeroAnimation() {
  useGSAP(() => {
    heroTimeline();
  });
}
```

```js
// pages/Home.js
import { animateCards } from "../animations/fade";
import { useHeroAnimation } from "../hooks/useHeroAnimation";

function Home() {
  useHeroAnimation();

  useGSAP(() => {
    animateCards(".card");
  });

  return <section>Home</section>;
}
```

```js
import gsap from "gsap";

// reusable fade animation
export function fadeUp(target, options = {}) {
  return gsap.from(target, {
    opacity: 0,
    y: 50,
    duration: 0.8,
    ease: "power2.out",
    ...options,
  });
}

// reusable stagger animation
export function staggerCards(target) {
  return gsap.from(target, {
    opacity: 0,
    y: 30,
    stagger: 0.15,
    duration: 0.6,
  });
}

// reusable hover animation
export function hoverScale(target) {
  target.addEventListener("mouseenter", () => {
    gsap.to(target, {
      scale: 1.05,
      duration: 0.3,
    });
  });

  target.addEventListener("mouseleave", () => {
    gsap.to(target, {
      scale: 1,
      duration: 0.3,
    });
  });
}

// reusable scroll animation
export function scrollReveal(target) {
  return gsap.from(target, {
    opacity: 0,
    y: 80,

    scrollTrigger: {
      trigger: target,
      start: "top 80%",
    },
  });
}

// usage
fadeUp(".title");
fadeUp(".subtitle", {
  delay: 0.3,
});
staggerCards(".card");
hoverScale(document.querySelector(".button"));
scrollReveal(".section");
```

- Reuse configs and helper functions
- Keep timelines modular
- Avoid repeated animation values
- Use scoped selectors in components
- Separate animation logic from UI logic
- Group related animations together
- Use timelines for complex sequences

---

## 📌 Deprecated / Avoid Patterns

Avoid bad animation patterns that hurt performance, maintainability, and user experience.

| Avoid Pattern             | Prefer                     |
| ------------------------- | -------------------------- |
| `left/top` animation      | `x/y` transforms           |
| `width/height` animation  | `scale` transforms         |
| Multiple separate tweens  | Timelines                  |
| Global selectors in React | Scoped refs/context        |
| Excessive `scrub` usage   | Lightweight scroll effects |
| Heavy infinite animations | Minimal looping            |
| Massive stagger values    | Small stagger timing       |
| Animating large DOM trees | Target specific elements   |
| Direct DOM style changes  | `gsap.set()`               |
| Manual resize listeners   | `gsap.matchMedia()`        |

```js
// bad
gsap.to(".box", {
  left: 300,
  top: 100,
  width: 500,
});

// good
gsap.to(".box", {
  x: 300,
  y: 100,
  scale: 1.2,
});
```

```js
// bad
gsap.to(".title", { opacity: 1 });
gsap.to(".card", { opacity: 1 });
gsap.to(".button", { opacity: 1 });

// good
const tl = gsap.timeline();

tl.to(".title", { opacity: 1 })
  .to(".card", { opacity: 1 })
  .to(".button", { opacity: 1 });
```

```js
// bad
window.addEventListener("resize", () => {
  // animation logic
});

// good
const mm = gsap.matchMedia();

mm.add("(min-width: 768px)", () => {
  gsap.to(".box", {
    x: 200,
  });
});
```

```js
// wrong
import { ScrollTrigger } from "gsap/ScrollTrigger";
// missing registerPlugin
// correct
gsap.registerPlugin(ScrollTrigger);
```

```js
// wrong
useGSAP(() => {
  gsap.to(".box", {
    x: 300,
  });
});

// correct
useGSAP(() => {
  gsap.to(".box", {
    x: 300,
  });

  return () => {
    gsap.killTweensOf(".box");
  };
});
```

```js
// wrong
gsap.to(".box", {
  scrub: true,
});

// correct
gsap.to(".box", {
  scrollTrigger: {
    trigger: ".box",
    scrub: 1,
  },
});
```

- Register plugins once globally
- Cleanup animations on unmount
- Keep motion subtle and purposeful
- Test animations on low-end/mobile devices
- Use timelines for organized animation flow
- Scope animations properly in frameworks
- Reuse timelines and animation presets

---

## 📌 Plugins & Ecosystem

GSAP plugins extend animation capabilities for scroll effects, text animations, dragging, physics, SVG motion, and advanced interactions.

| Plugin             | Usage                    | Free / Paid |
| ------------------ | ------------------------ | ----------- |
| `ScrollTrigger`    | Scroll animations        | Free        |
| `Flip`             | Layout transitions       | Free        |
| `Observer`         | Gesture/scroll detection | Free        |
| `MotionPathPlugin` | Path animations          | Free        |
| `Draggable`        | Drag interactions        | Free        |
| `SplitText`        | Split text animations    | 🔴 Paid     |
| `MorphSVGPlugin`   | SVG morphing             | 🔴 Paid     |
| `DrawSVGPlugin`    | SVG draw effects         | 🔴 Paid     |
| `ScrollSmoother`   | Smooth scrolling         | 🔴 Paid     |
| `GSDevTools`       | Timeline debugging       | 🔴 Paid     |
| `Physics2DPlugin`  | Physics motion           | 🔴 Paid     |
| `InertiaPlugin`    | Momentum effects         | 🔴 Paid     |

```js
// ScrollTrigger
import { ScrollTrigger } from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

// SplitText
import SplitText from "gsap/SplitText";
gsap.registerPlugin(SplitText);

// Flip
import { Flip } from "gsap/Flip";
gsap.registerPlugin(Flip);

// Draggable
import { Draggable } from "gsap/Draggable";
gsap.registerPlugin(Draggable);

// Observer
import { Observer } from "gsap/Observer";
gsap.registerPlugin(Observer);

// MotionPathPlugin
import { MotionPathPlugin } from "gsap/MotionPathPlugin";
gsap.registerPlugin(MotionPathPlugin);

// Flip Animation
const state = Flip.getState(".card");
container.appendChild(document.querySelector(".card"));
Flip.from(state, {
  duration: 0.8,
});

// Draggable
Draggable.create(".box", {
  type: "x,y",
});

// Motion Path
gsap.to(".ball", {
  duration: 3,
  motionPath: {
    path: "#path",
    autoRotate: true,
  },
});
```

- Register plugins once globally
- Load only required plugins
- Use free plugins before paid alternatives
- Keep plugin usage focused and lightweight
- Organize plugin setup in shared config files

---

## 📌 Debugging

GSAP debugging helps identify animation issues, scroll problems, layout jumps, and performance bottlenecks.

| Debugging Tool            | Usage                   |
| ------------------------- | ----------------------- |
| `markers`                 | Visual scroll positions |
| `id`                      | Label ScrollTriggers    |
| `console.log()`           | Inspect values          |
| `ScrollTrigger.refresh()` | Recalculate positions   |
| `ScrollTrigger.getAll()`  | Inspect all triggers    |
| `ScrollTrigger.killAll()` | Remove triggers         |
| `GSDevTools`              | Timeline debugging      |

| Common Problems         | Cause                      |
| ----------------------- | -------------------------- |
| Animation not running   | Wrong selector/plugin      |
| Scroll animation broken | Missing `registerPlugin()` |
| Layout jumping          | Large pinned sections      |
| Laggy animations        | Heavy scrub/infinite loops |
| React memory leaks      | Missing cleanup            |
| Wrong trigger positions | Missing `refresh()`        |

```js
// markers
gsap.to(".box", {
  x: 300,

  scrollTrigger: {
    trigger: ".box",
    start: "top center",
    markers: true,
  },
});

// trigger id
gsap.to(".card", {
  y: -100,

  scrollTrigger: {
    id: "cards-animation",
    trigger: ".cards",
    markers: true,
  },
});

ScrollTrigger.refresh(); // refresh
console.log(ScrollTrigger.getAll()); // inspect triggers
ScrollTrigger.killAll(); // remove triggers
```

```js
// React cleanup
useGSAP(() => {
  gsap.to(".box", {
    x: 300,
  });

  return () => {
    gsap.killTweensOf(".box");
  };
});
```

- Debug one animation at a time
- Register plugins once globally
- Test animations on mobile devices
- Avoid excessive scrub animations

---

## 📌 Real-world Use Cases

GSAP is widely used for modern UI motion, storytelling websites, interactive experiences, and high-end animations.

| Use Case              | Usage                     |
| --------------------- | ------------------------- |
| Landing Pages         | Hero animations           |
| Storytelling Websites | Scroll-driven experiences |
| Dashboards            | Card/chart transitions    |
| SaaS Products         | UI interactions           |
| Portfolios            | Cursor/motion effects     |
| E-commerce            | Product reveals           |
| Loaders               | Intro animations          |
| Navigation Menus      | Smooth transitions        |
| Sliders/Carousels     | Interactive motion        |
| SVG Graphics          | Logo/icon animations      |
| Page Transitions      | SPA navigation            |
| Micro Interactions    | Hover/click feedback      |

```js
// Hero Section Animation
const tl = gsap.timeline();

tl.from(".title", {
  opacity: 0,
  y: 100,
  duration: 1,
})

  .from(
    ".subtitle",
    {
      opacity: 0,
      y: 50,
    },
    "-=0.5",
  )

  .from(
    ".button",
    {
      opacity: 0,
      scale: 0.8,
    },
    "-=0.3",
  );

// Scroll Storytelling
gsap.to(".image", {
  y: -200,

  scrollTrigger: {
    trigger: ".section",
    scrub: true,
  },
});

// Dashboard Cards
gsap.from(".card", {
  opacity: 0,
  y: 30,
  stagger: 0.1,
});

// Loader
gsap.to(".loader", {
  rotation: 360,
  repeat: -1,
  duration: 1,
  ease: "none",
});

// Cursor Effect
window.addEventListener("mousemove", (e) => {
  gsap.to(".cursor", {
    x: e.clientX,
    y: e.clientY,
    duration: 0.2,
  });
});
```

- Keep animations purposeful
- Use subtle motion for UI interactions
- Prefer timelines for landing pages
- Optimize scroll effects for mobile
- Avoid excessive animation complexity

---
