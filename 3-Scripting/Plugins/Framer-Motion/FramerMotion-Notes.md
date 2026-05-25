# 👉 Framer Motion

## 📌 Fundamentals

- Framer Motion is a React animation library for building smooth, interactive UI animations with simple declarative APIs.
- Framer Motion is completely free and open-source for development usage in React applications.

| Framework    | Support                                   |
| ------------ | ----------------------------------------- |
| React        | ✅ Official                               |
| Next.js      | ✅ Official                               |
| Remix        | ✅ Supported                              |
| Gatsby       | ✅ Supported                              |
| React Native | ❌ Use `moti` / `react-native-reanimated` |
| Vue          | ❌ Not supported                          |
| Angular      | ❌ Not supported                          |
| Vanilla JS   | ❌ Not supported                          |

| Install | Command                     |
| ------- | --------------------------- |
| npm     | `npm install framer-motion` |
| yarn    | `yarn add framer-motion`    |

| Topic        | Usage                      |
| ------------ | -------------------------- |
| `motion`     | Animated component wrapper |
| `initial`    | Starting animation state   |
| `animate`    | Target animation state     |
| `exit`       | Unmount animation          |
| `transition` | Animation timing/config    |
| `whileHover` | Hover animation            |
| `whileTap`   | Tap/click animation        |
| `variants`   | Reusable animation states  |

### Setup

```jsx
import { motion } from "framer-motion";

function App() {
  return (
    <motion.div initial={{ opacity: 0 }} animate={{ opacity: 1 }}>
      Hello
    </motion.div>
  );
}
```

### motion Component

```jsx
<motion.div />
<motion.button />
<motion.img />
<motion.section />
```

| HTML      | Motion Version   |
| --------- | ---------------- |
| `div`     | `motion.div`     |
| `button`  | `motion.button`  |
| `img`     | `motion.img`     |
| `section` | `motion.section` |

### Animation Properties

| Property          | Usage           |
| ----------------- | --------------- |
| `x`               | Horizontal move |
| `y`               | Vertical move   |
| `scale`           | Zoom effect     |
| `rotate`          | Rotation        |
| `opacity`         | Fade effect     |
| `backgroundColor` | Color animation |

```jsx
<motion.div
  animate={{
    x: 100,
    scale: 1.2,
    rotate: 45,
    opacity: 0.5,
  }}
/>
```

### Transition

```jsx
<motion.div
  animate={{ x: 100 }}
  transition={{
    duration: 0.5,
    ease: "easeInOut",
  }}
/>
```

| Transition Prop | Usage           |
| --------------- | --------------- |
| `duration`      | Animation speed |
| `delay`         | Start delay     |
| `ease`          | Easing style    |
| `type`          | Tween/spring    |

```jsx
// Hover & Tap Animation
<motion.button whileHover={{ scale: 1.05 }} whileTap={{ scale: 0.95 }}>
  Button
</motion.button>
```

## Variants

```jsx
const cardVariants = {
  hidden: {
    opacity: 0,
    y: 30,
  },
  visible: {
    opacity: 1,
    y: 0,
  },
};

<motion.div variants={cardVariants} initial="hidden" animate="visible" />;
```

```jsx
// Exit Animation
import { AnimatePresence, motion } from "framer-motion";

<AnimatePresence>
  {show && <motion.div exit={{ opacity: 0 }} />}
</AnimatePresence>;
```

- Prefer `transform` animations (`x`, `y`, `scale`)
- Keep durations short and smooth
- Reuse variants for scalability
- Avoid excessive animation
- Use subtle motion for better UX
- Use `AnimatePresence` for exit animation

```jsx
import { motion } from "framer-motion";

function Card() {
  return (
    <motion.div
      initial={{ opacity: 0, y: 20 }}
      animate={{ opacity: 1, y: 0 }}
      whileHover={{ scale: 1.03 }}
      transition={{ duration: 0.3 }}
      className="rounded-xl border p-6"
    >
      Product Card
    </motion.div>
  );
}
```

---

## 📌 Core Animation Properties

Core animation properties control movement, scaling, rotation, fading, and visual transformation of elements.

| Property          | Usage                |
| ----------------- | -------------------- |
| `x`               | Horizontal move      |
| `y`               | Vertical move        |
| `scale`           | Resize element       |
| `scaleX`          | Horizontal scale     |
| `scaleY`          | Vertical scale       |
| `rotate`          | Rotation             |
| `opacity`         | Fade effect          |
| `backgroundColor` | Background animation |
| `color`           | Text color animation |
| `borderRadius`    | Shape morphing       |
| `width`           | Width animation      |
| `height`          | Height animation     |
| `filter`          | Blur/visual effects  |

```jsx
<motion.div
  animate={{
    // Position
    x: 100,
    y: 50,
    z: 20,

    // Scale
    scale: 1.1,
    scaleX: 1.2,
    scaleY: 0.9,

    // Rotation
    rotate: 45,
    rotateX: 20,
    rotateY: 10,
    rotateZ: 5,

    // Visibility
    opacity: 0.8,

    // Size
    width: 300,
    height: 200,

    // Spacing
    top: 20,
    left: 40,
    right: 10,
    bottom: 10,

    // Colors
    backgroundColor: "#000",
    color: "#fff",
    borderColor: "#fff",

    // Borders
    borderRadius: "20px",

    // Shadow
    boxShadow: "0 10px 30px rgba(0,0,0,0.2)",

    // Filters
    filter: "blur(4px)",

    // CSS Transform
    skewX: 10,
    skewY: 5,

    // Transform Origin
    originX: 0.5,
    originY: 0.5,

    // SVG
    pathLength: 1,
    fill: "#000",
    stroke: "#fff",
  }}
  transition={{
    duration: 0.5,
  }}
/>
```

| Category  | Properties / Examples                          |
| --------- | ---------------------------------------------- |
| Position  | `x`, `y`, `z`, `top`, `left`                   |
| Scale     | `scale`, `scaleX`, `scaleY`                    |
| Rotation  | `rotate`, `rotateX`, `rotateY`, `rotateZ`      |
| Opacity   | `0` = Hidden, `1` = Visible                    |
| Size      | `width`, `height`                              |
| Colors    | `backgroundColor`, `color`, `borderColor`      |
| Borders   | `borderRadius`                                 |
| Shadow    | `boxShadow`                                    |
| Filters   | `blur(4px)`, `brightness(1.2)`, `grayscale(1)` |
| Transform | `skewX`, `skewY`                               |
| Origin    | `originX`, `originY`                           |
| SVG       | `pathLength`, `fill`, `stroke`                 |

| Rotation Type | Example       |
| ------------- | ------------- |
| Normal        | `rotate: 45`  |
| Full Spin     | `rotate: 360` |

- Prefer `transform` properties for performance
- Avoid animating `width`/`height` frequently
- Keep motion subtle and smooth
- Use GPU-friendly animations
- Combine multiple transforms carefully
- Use short durations for UI interactions

---

## 📌 Gestures & Interaction

Framer Motion provides built-in gesture animations for hover, tap, drag, focus, and pointer interactions.

| Gesture           | Usage                 |
| ----------------- | --------------------- |
| `whileHover`      | Hover animation       |
| `whileTap`        | Click/tap animation   |
| `whileFocus`      | Focus state animation |
| `whileDrag`       | Animation during drag |
| `drag`            | Enable dragging       |
| `dragConstraints` | Limit drag area       |
| `dragElastic`     | Drag flexibility      |
| `dragMomentum`    | Inertia effect        |
| `onHoverStart`    | Hover start event     |
| `onHoverEnd`      | Hover end event       |
| `onTap`           | Click/tap event       |
| `onPan`           | Pointer movement      |

```jsx
<motion.div
  // Hover
  whileHover={{
    scale: 1.05,
    rotate: 2,
  }}
  // Tap
  whileTap={{
    scale: 0.95,
  }}
  // Focus
  whileFocus={{
    outline: "2px solid #000",
  }}
  // Drag
  drag
  whileDrag={{
    scale: 1.1,
    cursor: "grabbing",
  }}
  // Drag Limits
  dragConstraints={{
    top: -50,
    bottom: 50,
    left: -50,
    right: 50,
  }}
  // Drag Settings
  dragElastic={0.2}
  dragMomentum={false}
  // Events
  onHoverStart={() => console.log("Hover")}
  onHoverEnd={() => console.log("Leave")}
  onTap={() => console.log("Tap")}
  onPan={(e, info) => console.log(info.offset)}
/>
```

### Drag Types

| Value      | Usage           |
| ---------- | --------------- |
| `drag`     | Free dragging   |
| `drag="x"` | Horizontal only |
| `drag="y"` | Vertical only   |

### Drag Config

| Property           | Usage                 |
| ------------------ | --------------------- |
| `dragConstraints`  | Limit movement        |
| `dragElastic`      | Stretch effect        |
| `dragMomentum`     | Inertia after release |
| `dragSnapToOrigin` | Return to start       |

### Event Info Object

| Property   | Usage                    |
| ---------- | ------------------------ |
| `point`    | Current pointer position |
| `delta`    | Movement difference      |
| `offset`   | Total movement           |
| `velocity` | Pointer speed            |

- Keep hover effects subtle
- Use drag only for interactive UI
- Disable drag momentum when unnecessary
- Add cursor styles during drag
- Avoid excessive rotation on hover
- Use gestures for feedback, not distraction

```jsx
<motion.button
  whileHover={{
    scale: 1.03,
  }}
  whileTap={{
    scale: 0.97,
  }}
  className="rounded-lg bg-black px-5 py-3 text-white"
>
  Add to Cart
</motion.button>
```

---

## 📌 Variants System

Variants help organize reusable animation states and coordinate parent-child animations cleanly.

| Feature           | Usage                       |
| ----------------- | --------------------------- |
| `variants`        | Reusable animation states   |
| `initial`         | Starting variant            |
| `animate`         | Active variant              |
| `exit`            | Exit variant                |
| `whileHover`      | Hover variant               |
| `whileTap`        | Tap variant                 |
| `staggerChildren` | Delay child animations      |
| `delayChildren`   | Delay child start           |
| `when`            | Parent/child timing control |

### Basic Variant

```jsx
const cardVariants = {
  hidden: {
    opacity: 0,
    y: 30,
  },
  visible: {
    opacity: 1,
    y: 0,
  },
};

<motion.div variants={cardVariants} initial="hidden" animate="visible" />;
```

### Parent + Child Variants

```jsx
const containerVariants = {
  hidden: {},
  visible: {
    transition: {
      staggerChildren: 0.2,
      delayChildren: 0.1,
    },
  },
};

const itemVariants = {
  hidden: {
    opacity: 0,
    y: 20,
  },
  visible: {
    opacity: 1,
    y: 0,
  },
};

<motion.ul variants={containerVariants} initial="hidden" animate="visible">
  <motion.li variants={itemVariants} />
  <motion.li variants={itemVariants} />
  <motion.li variants={itemVariants} />
</motion.ul>;
```

### Dynamic Variants

```jsx
const boxVariants = {
  active: (custom) => ({
    x: custom,
    opacity: 1,
  }),
};

<motion.div custom={100} variants={boxVariants} animate="active" />;
```

### Hover & Tap Variants

```jsx
const buttonVariants = {
  hover: {
    scale: 1.05,
  },
  tap: {
    scale: 0.95,
  },
};

<motion.button variants={buttonVariants} whileHover="hover" whileTap="tap" />;
```

### Transition Control

| Property               | Usage                       |
| ---------------------- | --------------------------- |
| `staggerChildren`      | Animate children one-by-one |
| `delayChildren`        | Delay child animations      |
| `when: beforeChildren` | Parent first                |
| `when: afterChildren`  | Children first              |

### Variant Structure Pattern

```jsx
export const fadeUp = {
  hidden: {
    opacity: 0,
    y: 30,
  },
  visible: {
    opacity: 1,
    y: 0,
    transition: {
      duration: 0.4,
    },
  },
};
```

- Reuse shared variants
- Keep naming consistent
- Separate animation configs into files
- Use variants for scalable UI systems
- Prefer parent-child orchestration
- Avoid deeply nested complex variants

```jsx
const cardVariants = {
  hidden: {
    opacity: 0,
    y: 20,
  },
  visible: {
    opacity: 1,
    y: 0,
  },
};

<motion.div
  variants={cardVariants}
  initial="hidden"
  whileInView="visible"
  viewport={{ once: true }}
  className="rounded-xl border p-6"
>
  Feature Card
</motion.div>;
```

---

## 📌 Layout Animation

Layout animations smoothly animate size, position, and shared element changes automatically.

| Feature           | Usage                     |
| ----------------- | ------------------------- |
| `layout`          | Animate layout changes    |
| `layoutId`        | Shared element transition |
| `LayoutGroup`     | Sync layout animations    |
| `AnimatePresence` | Layout exit animation     |

```jsx
<motion.div layout className={isOpen ? "h-60" : "h-32"} />

// Shared Layout Animation
<>{isOpen ? <motion.div layoutId="card" /> : <motion.div layoutId="card" />}</>
```

| Property   | Usage                    |
| ---------- | ------------------------ |
| `layout`   | Auto animate layout      |
| `layoutId` | Shared element animation |

```jsx
// LayoutGroup Example
import { LayoutGroup } from "framer-motion";

<LayoutGroup>
  <motion.div layout />
  <motion.div layout />
</LayoutGroup>;

// AnimatePresence + Layout
<AnimatePresence>
  {show && (
    <motion.div
      layout
      initial={{ opacity: 0 }}
      animate={{ opacity: 1 }}
      exit={{ opacity: 0 }}
    />
  )}
</AnimatePresence>;
```

| UI Pattern | Use Cases                 |
| ---------- | ------------------------- |
| Accordion  | Smooth expand/collapse    |
| Tabs       | Animated active indicator |
| Modal      | Shared transition         |
| Sidebar    | Width transition          |
| Cards      | Grid/list transition      |
| Gallery    | Shared image preview      |

- Use `layout` for size/position changes
- Use `layoutId` for shared transitions
- Keep layout animations subtle
- Avoid animating huge lists heavily
- Combine with `AnimatePresence`
- Prefer transform-based transitions when possible

```jsx
<motion.div
  layout
  whileHover={{ scale: 1.02 }}
  className="rounded-xl border p-6"
>
  Expandable Card
</motion.div>
```

---

## 📌 AnimatePresence

`AnimatePresence` enables exit/unmount animations for conditional React components.

| Feature           | Usage                     |
| ----------------- | ------------------------- |
| `AnimatePresence` | Enable exit animations    |
| `exit`            | Unmount animation         |
| `mode`            | Animation sequencing      |
| `initial`         | Disable initial animation |
| `onExitComplete`  | Callback after exit       |

```jsx
import { AnimatePresence, motion } from "framer-motion";

<AnimatePresence>
  {show && (
    <motion.div
      initial={{ opacity: 0 }}
      animate={{ opacity: 1 }}
      exit={{ opacity: 0 }}
    />
  )}
</AnimatePresence>;
```

| mode Options  | Usage                          |
| ------------- | ------------------------------ |
| `"sync"`      | Default simultaneous animation |
| `"wait"`      | Wait for exit before enter     |
| `"popLayout"` | Layout-aware transitions       |

```jsx
<AnimatePresence mode="wait">
  <motion.div
    key={page}
    initial={{ opacity: 0 }}
    animate={{ opacity: 1 }}
    exit={{ opacity: 0 }}
  />
</AnimatePresence>
```

```jsx
// initial={false}
// Disable initial mount animation.
<AnimatePresence initial={false}>
  {show && <motion.div animate={{ opacity: 1 }} exit={{ opacity: 0 }} />}
</AnimatePresence>
```

```jsx
// onExitComplete
<AnimatePresence
  onExitComplete={() => {
    console.log("Exit done");
  }}
>
  {show && <motion.div exit={{ opacity: 0 }} />}
</AnimatePresence>
```

### Common Exit Patterns

```jsx
exit={{ opacity: 0 }} // Fade Out
exit={{ x: -100 }} // Slide Out
exit={{ scale: 0.8 }} // Scale Out
// Combined
exit={{
  opacity: 0,
  y: 20,
  scale: 0.95,
}}
```

| UI Pattern       | Usage                  |
| ---------------- | ---------------------- |
| Modal            | Smooth close animation |
| Toast            | Exit notification      |
| Dropdown         | Menu hide animation    |
| Route Transition | Page switching         |
| Tabs             | Content transition     |
| Accordion        | Collapse animation     |

- Always use unique `key` values
- Wrap only conditional components
- Keep exit animations short
- Use `mode="wait"` for page transitions
- Combine with `layout` carefully
- Avoid heavy nested AnimatePresence trees

```jsx
<AnimatePresence mode="wait">
  {open && (
    <motion.div
      initial={{
        opacity: 0,
        scale: 0.95,
      }}
      animate={{
        opacity: 1,
        scale: 1,
      }}
      exit={{
        opacity: 0,
        scale: 0.95,
      }}
      transition={{
        duration: 0.2,
      }}
      className="rounded-xl bg-white p-6 shadow-xl"
    >
      Modal Content
    </motion.div>
  )}
</AnimatePresence>
```

---

## 📌 Scroll Animations

Scroll animations trigger or sync animations based on viewport visibility and scroll progress.

| Feature           | Usage                     |
| ----------------- | ------------------------- |
| `whileInView`     | Animate on viewport entry |
| `viewport`        | Viewport behavior config  |
| `useScroll`       | Track scroll progress     |
| `useTransform`    | Map scroll values         |
| `scrollY`         | Current scroll position   |
| `scrollYProgress` | Scroll percentage         |

```jsx
// whileInView
<motion.div
  initial={{
    opacity: 0,
    y: 40,
  }}
  whileInView={{
    opacity: 1,
    y: 0,
  }}
  viewport={{
    once: true,
    amount: 0.3,
  }}
/>
```

### viewport Options

| Property | Usage                  |
| -------- | ---------------------- |
| `once`   | Animate once only      |
| `amount` | Visibility threshold   |
| `margin` | Custom viewport margin |

```jsx
// useScroll
import { motion, useScroll } from "framer-motion";
const { scrollY, scrollYProgress } = useScroll();

// useTransform
import { motion, useScroll, useTransform } from "framer-motion";
const { scrollYProgress } = useScroll();
const scale = useTransform(scrollYProgress, [0, 1], [0.8, 1]);
<motion.div style={{ scale }} />;

// Scroll Progress Bar
const { scrollYProgress } = useScroll();
<motion.div
  style={{
    scaleX: scrollYProgress,
    transformOrigin: "left",
  }}
  className="fixed left-0 top-0 h-1 w-full bg-black"
/>;

// Parallax Effect
const y = useTransform(scrollYProgress, [0, 1], [0, -200]);
<motion.div style={{ y }} />;
```

| Pattern          | Usage              |
| ---------------- | ------------------ |
| Fade In Sections | Landing pages      |
| Progress Bar     | Reading progress   |
| Parallax         | Hero sections      |
| Sticky Animation | Storytelling UI    |
| Reveal Cards     | Scroll interaction |
| Image Zoom       | Portfolio/gallery  |

- Use `whileInView` for simple reveal effects
- Keep scroll motion smooth and subtle
- Avoid excessive parallax movement
- Use `once: true` when possible
- Prefer transform animations for performance
- Avoid heavy animations on large pages

```jsx
<motion.section
  initial={{
    opacity: 0,
    y: 50,
  }}
  whileInView={{
    opacity: 1,
    y: 0,
  }}
  viewport={{
    once: true,
  }}
  transition={{
    duration: 0.5,
  }}
  className="py-20"
>
  Features Section
</motion.section>
```

---

## 📌 Motion Values

Motion Values are reactive animated values used for smooth performant animations without unnecessary React re-renders.

| Hook                | Usage                  |
| ------------------- | ---------------------- |
| `useMotionValue`    | Create reactive value  |
| `useTransform`      | Map value ranges       |
| `useSpring`         | Smooth animations      |
| `useVelocity`       | Track speed            |
| `useMotionTemplate` | Dynamic motion strings |

```jsx
import {
  motion,
  useMotionValue,
  useTransform,
  useSpring,
  useVelocity,
  useMotionTemplate,
} from "framer-motion";

const x = useMotionValue(0);
const scale = useTransform(x, [-200, 0, 200], [0.8, 1, 1.2]);
const smoothX = useSpring(x, {
  stiffness: 100,
  damping: 20,
});
const velocity = useVelocity(x);
const blur = useMotionTemplate`
  blur(${x}px)
`;

<motion.div
  drag="x"
  style={{
    x: smoothX,
    scale,
    filter: blur,
  }}
/>;
```

```jsx
// useMotionValue
const x = useMotionValue(0);
x.set(100);
```

| Method   | Usage              |
| -------- | ------------------ |
| `.set()` | Update value       |
| `.get()` | Read current value |

```jsx
// useTransform
// Map one value into another.
const opacity = useTransform(x, [0, 200], [0, 1]);
```

```jsx
// useSpring
// Smooth reactive motion.
const smoothX = useSpring(x, {
  stiffness: 120,
  damping: 20,
});
```

| Property    | Usage           |
| ----------- | --------------- |
| `stiffness` | Spring strength |
| `damping`   | Smoothness      |
| `mass`      | Weight/inertia  |

```jsx
// useVelocity
// Track motion speed.
const velocity = useVelocity(x);

// useMotionTemplate
// Dynamic animated CSS values.
const shadow = useMotionTemplate`
  0 0 ${x}px rgba(0,0,0,0.2)
`;
```

| Common Use Cases | Usage             |
| ---------------- | ----------------- |
| Drag UI          | Reactive dragging |
| Parallax         | Scroll transforms |
| Progress Bars    | Dynamic width     |
| Mouse Tracking   | Cursor effects    |
| Card Tilt        | Interactive cards |
| Dynamic Filters  | Blur/brightness   |

- Use Motion Values for high-frequency updates
- Prefer Motion Values over React state for animation
- Combine with `useSpring` for smooth motion
- Avoid excessive chained transforms
- Use transform properties for performance
- Keep interactions subtle

```jsx
const x = useMotionValue(0);
const rotate = useTransform(x, [-200, 200], [-15, 15]);

<motion.div
  drag="x"
  style={{
    x,
    rotate,
  }}
  className="rounded-xl border p-6"
>
  Interactive Card
</motion.div>;
```

---

## 📌 Animation Controls

Animation Controls allow manual, sequence-based, and programmatic animation handling.

| Hook / Feature  | Usage                    |
| --------------- | ------------------------ |
| `useAnimation`  | Manual animation control |
| `start()`       | Start animation          |
| `stop()`        | Stop animation           |
| `set()`         | Instantly set values     |
| Async Animation | Sequential animations    |
| Event Trigger   | Control from interaction |

```jsx
// Basic useAnimation
import { motion, useAnimation } from "framer-motion";

const controls = useAnimation();

<motion.div animate={controls} />;
```

```jsx
import {
  motion,
  useAnimation,
} from "framer-motion";

const controls = useAnimation();

const handleAnimate = async () => {
  await controls.start({
    x: 100,
    transition: {
      duration: 0.3,
    },
  });

  await controls.start({
    rotate: 180,
  });

  controls.set({
    scale: 1,
  });
};

<motion.div
  animate={controls}
  whileHover={{
    scale: 1.05,
  }}
/>

<button onClick={handleAnimate}>
  Animate
</button>
```

| Control Methods | Usage                  |
| --------------- | ---------------------- |
| `start()`       | Run animation          |
| `stop()`        | Stop current animation |
| `set()`         | Apply instantly        |

```jsx
// start() Example
controls.start({
  opacity: 1,
  y: 0,
});

// stop() Example
controls.stop();

// set() Example
controls.set({
  x: 0,
  opacity: 1,
});

// Sequence Animation
await controls.start({
  x: 100,
});

await controls.start({
  rotate: 90,
});
```

```jsx
// Event Trigger Animation
<button
  onMouseEnter={() => {
    controls.start({
      scale: 1.1,
    });
  }}
>
  Hover
</button>
```

| Common Use Cases  | Usage                |
| ----------------- | -------------------- |
| Step Animation    | Sequential UI motion |
| Interactive Cards | Manual hover/tap     |
| Sliders           | Dynamic transitions  |
| Game UI           | Trigger-based motion |
| Page Intro        | Timed sequence       |
| Notification      | Controlled entrance  |

- Use controls for complex interactions
- Prefer variants for reusable animation
- Keep sequences short and smooth
- Avoid excessive async chains
- Use `await` for predictable flow
- Combine with gestures carefully

```jsx
const controls = useAnimation();

<button
  onClick={() => {
    controls.start({
      scale: 1.1,
      rotate: 5,
    });
  }}
>
  Animate
</button>

<motion.div
  animate={controls}
  className="rounded-xl border p-6"
/>
```

---

## 📌 SVG Animation

Framer Motion can animate SVG paths, strokes, fills, transforms, and drawing effects smoothly.

| Feature       | Usage                  |
| ------------- | ---------------------- |
| `pathLength`  | Drawing animation      |
| `pathOffset`  | Path movement          |
| `pathSpacing` | Dash spacing           |
| `fill`        | Fill color animation   |
| `stroke`      | Stroke color animation |
| `strokeWidth` | Stroke thickness       |
| `rotate`      | SVG rotation           |
| `scale`       | SVG scaling            |

```jsx
// SVG Animation
import { motion } from "framer-motion";

<motion.svg
  width="120"
  height="120"
  viewBox="0 0 100 100"
  initial={{
    rotate: 0,
  }}
  animate={{
    rotate: 360,
  }}
  transition={{
    duration: 2,
    repeat: Infinity,
    ease: "linear",
  }}
>
  <motion.circle
    cx="50"
    cy="50"
    r="40"
    fill="transparent"
    stroke="#000"
    strokeWidth="6"
    initial={{
      pathLength: 0,
      opacity: 0,
    }}
    animate={{
      pathLength: 1,
      opacity: 1,
      stroke: "#000",
    }}
    transition={{
      duration: 1.5,
    }}
  />
</motion.svg>;
```

| SVG Properties | Usage            |
| -------------- | ---------------- |
| `pathLength`   | Draw path        |
| `pathOffset`   | Move dash offset |
| `pathSpacing`  | Dash spacing     |
| `fill`         | Fill color       |
| `stroke`       | Stroke color     |
| `strokeWidth`  | Stroke size      |
| `opacity`      | Fade effect      |
| `rotate`       | Rotation         |
| `scale`        | Zoom effect      |

```jsx
// Drawing Effect
<motion.path
  initial={{
    pathLength: 0,
  }}
  animate={{
    pathLength: 1,
  }}
/>

// Fill Animation
<motion.path
  animate={{
    fill: "#000",
  }}
/>

// Stroke Animation
<motion.path
  animate={{
    stroke: "#fff",
    strokeWidth: 4,
  }}
/>

// Infinite Loader
<motion.circle
  animate={{
    rotate: 360,
  }}
  transition={{
    repeat: Infinity,
    duration: 1,
    ease: "linear",
  }}
/>
```

| Common Use Cases | Usage                 |
| ---------------- | --------------------- |
| Loaders          | Spinner animation     |
| Icons            | Interactive SVG icons |
| Logos            | Animated branding     |
| Progress Rings   | Circular progress     |
| Illustration     | Drawing effect        |
| Charts           | Animated data visuals |

- Use SVG for scalable animation
- Prefer `pathLength` for draw effects
- Keep SVG markup optimized
- Avoid extremely complex paths
- Use linear easing for loaders
- Combine with Motion Values for advanced effects

```jsx
<motion.svg width="80" height="80" viewBox="0 0 100 100">
  <motion.circle
    cx="50"
    cy="50"
    r="40"
    fill="transparent"
    stroke="#000"
    strokeWidth="6"
    initial={{
      pathLength: 0,
    }}
    animate={{
      pathLength: 1,
    }}
    transition={{
      duration: 1,
    }}
  />
</motion.svg>
```

---

## 📌 Advanced Features

Framer Motion includes advanced APIs for performance optimization, orchestration, drag sorting, and scalable animation systems.

## 📌 Advanced Features Reference

| Feature        | One-Time Setup?            | Usage                      | Common Config / Example          |
| -------------- | -------------------------- | -------------------------- | -------------------------------- |
| `MotionConfig` | Usually App-level          | Global motion settings     | `transition={{ duration: 0.3 }}` |
| `LazyMotion`   | Usually App-level          | Reduce bundle size         | `features={domAnimation}`        |
| `domAnimation` | Passed inside `LazyMotion` | Basic lightweight features | Simple animations                |
| `domMax`       | Passed inside `LazyMotion` | Full feature support       | Drag + layout + gestures         |
| `Reorder`      | Per component              | Sortable drag lists        | `axis="y"`                       |
| `useCycle`     | Per component              | Toggle states              | `useCycle(false, true)`          |
| `useAnimate`   | Per component              | Imperative animation       | `animate(scope.current)`         |
| `useInView`    | Per component              | Viewport detection         | `useInView(ref)`                 |

```jsx
// MotionConfig
import { MotionConfig, motion } from "framer-motion";

<MotionConfig
  transition={{
    duration: 0.3,
  }}
>
  <motion.div animate={{ x: 100 }} />
</MotionConfig>;
```

```jsx
// LazyMotion
import { LazyMotion, domAnimation, motion } from "framer-motion";

<LazyMotion features={domAnimation}>
  <motion.div animate={{ opacity: 1 }} />
</LazyMotion>;
```

| Feature Set    | Usage                |
| -------------- | -------------------- |
| `domAnimation` | Basic animations     |
| `domMax`       | Full feature support |

```jsx
// Reorder API

import { Reorder } from "framer-motion";

<Reorder.Group axis="y" values={items} onReorder={setItems}>
  {items.map((item) => (
    <Reorder.Item key={item} value={item}>
      {item}
    </Reorder.Item>
  ))}
</Reorder.Group>;
```

```jsx
// useCycle
import { useCycle, motion } from "framer-motion";

const [active, toggle] = useCycle(false, true);

<motion.div
  animate={{
    scale: active ? 1.2 : 1,
  }}
  onClick={toggle}
/>;
```

```jsx
// useAnimate
import { useAnimate } from "framer-motion";

const [scope, animate] = useAnimate();

animate(scope.current, { opacity: 1 }, { duration: 0.3 });
```

```jsx
// useInView
// Detect viewport visibility.
import { useInView } from "framer-motion";

const ref = useRef(null);

const isInView = useInView(ref);
```

| Common Use Cases    | Usage              |
| ------------------- | ------------------ |
| Global Timing       | Shared transitions |
| Bundle Optimization | LazyMotion         |
| Sortable Lists      | Reorder API        |
| Toggle Animation    | useCycle           |
| Imperative Control  | useAnimate         |
| Scroll Reveal       | useInView          |

- Use `LazyMotion` in large apps
- Prefer `domAnimation` unless advanced gestures needed
- Use `MotionConfig` for shared timing
- Keep reorder lists lightweight
- Prefer declarative animation when possible
- Use imperative APIs only for complex flows

```jsx
<MotionConfig
  transition={{
    duration: 0.25,
  }}
>
  <motion.button
    whileHover={{
      scale: 1.05,
    }}
    whileTap={{
      scale: 0.95,
    }}
    className="rounded-lg bg-black px-5 py-3 text-white"
  >
    Checkout
  </motion.button>
</MotionConfig>
```

---

## 📌 React Integration

Framer Motion integrates directly with React components, state, hooks, and conditional rendering.

### React Setup

| Step             | Usage                                    |
| ---------------- | ---------------------------------------- |
| Install          | `npm install framer-motion`              |
| Import           | `import { motion } from "framer-motion"` |
| Replace Elements | `div → motion.div`                       |

### motion Component

| ✅ Use Often     | ❌ Avoid Usually  |
| ---------------- | ----------------- |
| `motion.div`     | `motion.canvas`   |
| `motion.button`  | `motion.video`    |
| `motion.span`    | `motion.select`   |
| `motion.img`     | `motion.textarea` |
| `motion.section` | `motion.label`    |
| `motion.ul`      | `motion.main`     |
| `motion.li`      | `motion.aside`    |
| `motion.form`    | `motion.article`  |
| `motion.input`   | `motion.footer`   |
| `motion.a`       | `motion.header`   |
| `motion.nav`     | `motion.polygon`  |
| `motion.svg`     | `motion.ellipse`  |
| `motion.path`    | `motion.line`     |
| `motion.circle`  | `motion.text`     |

```jsx
<motion.div animate={{ opacity: 1 }} />
```

```jsx
// State Driven Animation
const [open, setOpen] = useState(false);

<motion.div
  animate={{
    height: open ? 200 : 100,
  }}
/>;
```

| State   | Animation |
| ------- | --------- |
| `true`  | Expanded  |
| `false` | Collapsed |

```jsx
// Conditional Rendering
// Use with `AnimatePresence` for mount/unmount animation.
<AnimatePresence>
  {show && (
    <motion.div
      initial={{ opacity: 0 }}
      animate={{ opacity: 1 }}
      exit={{ opacity: 0 }}
    />
  )}
</AnimatePresence>
```

```jsx
// Event Based Animation
<motion.button
  whileHover={{
    scale: 1.05,
  }}
  whileTap={{
    scale: 0.95,
  }}
>
  Button
</motion.button>
```

| Event        | Usage                   |
| ------------ | ----------------------- |
| `whileHover` | Hover interaction       |
| `whileTap`   | Click/tap effect        |
| `onClick`    | Trigger animation logic |

```jsx
// useAnimation Hook
// Manual animation control.
const controls = useAnimation();

controls.start({
  x: 100,
});

<motion.div animate={controls} />;
```

```jsx
// Dynamic Variants
const variants = {
  active: (distance) => ({
    x: distance,
  }),
};

<motion.div custom={100} variants={variants} animate="active" />;
```

```jsx
// List Animation
{
  items.map((item) => (
    <motion.li key={item.id} initial={{ opacity: 0 }} animate={{ opacity: 1 }}>
      {item.name}
    </motion.li>
  ));
}
```

| Requirement       | Usage                     |
| ----------------- | ------------------------- |
| `key`             | Stable animation identity |
| `AnimatePresence` | Exit animation            |

```jsx
// Ref Integration
const ref = useRef(null);

const isInView = useInView(ref);

<motion.div ref={ref} />;
```

| Common React Patterns | Usage                 |
| --------------------- | --------------------- |
| Modal                 | Conditional rendering |
| Accordion             | State-based layout    |
| Tabs                  | Variant switching     |
| Sidebar               | Toggle animation      |
| Lists                 | Stagger animation     |
| Forms                 | Validation feedback   |

- Use variants for reusable animations
- Keep animation state predictable
- Use stable `key` props
- Prefer transform animations
- Avoid unnecessary re-renders
- Keep interactions subtle

```jsx
import { motion, AnimatePresence } from "framer-motion";

function Modal({ open }) {
  return (
    <AnimatePresence>
      {open && (
        <motion.div
          initial={{
            opacity: 0,
            scale: 0.95,
          }}
          animate={{
            opacity: 1,
            scale: 1,
          }}
          exit={{
            opacity: 0,
            scale: 0.95,
          }}
          className="rounded-xl bg-white p-6 shadow-xl"
        >
          Modal Content
        </motion.div>
      )}
    </AnimatePresence>
  );
}
```

### Tailwind Integration

- Use Tailwind for styling only
- Use Framer Motion for animation logic
- Prefer transform animations
- Keep motion subtle
- Combine variants with reusable Tailwind classes
- Avoid mixing CSS animation unnecessarily

---

## 📌 Next.js Integration

Framer Motion works seamlessly with Next.js for page transitions, interactive UI, and animated layouts.

### Installation

| Package       | Command                     |
| ------------- | --------------------------- |
| Framer Motion | `npm install framer-motion` |

```bash
npm install framer-motion
```

---

### Client Component Requirement

Framer Motion must run in Client Components.

```jsx
"use client";

import { motion } from "framer-motion";
```

| Requirement                       | Usage                                  |
| --------------------------------- | -------------------------------------- |
| `"use client"`                    | Required in App Router                 |
| Client Component                  | Motion runs on client side             |
| No Server Components              | Motion cannot run in server components |
| Route transitions in `layout.jsx` | Common App Router pattern              |
| Use stable `key` for routes       | Required for page transitions          |

```jsx
// Basic Animation
"use client";

import { motion } from "framer-motion";

export default function Hero() {
  return (
    <motion.section initial={{ opacity: 0 }} animate={{ opacity: 1 }}>
      Hero
    </motion.section>
  );
}
```

```jsx
// Page Transition
<AnimatePresence mode="wait">
  <motion.div
    key={pathname}
    initial={{ opacity: 0 }}
    animate={{ opacity: 1 }}
    exit={{ opacity: 0 }}
  >
    {children}
  </motion.div>
</AnimatePresence>
```

| Feature           | Usage                  |
| ----------------- | ---------------------- |
| `AnimatePresence` | Page exit animation    |
| `key`             | Detect route change    |
| `mode="wait"`     | Smooth page transition |

```jsx
// Layout Animation
<motion.div layout className="rounded-xl" />

// Shared Layout Animation
<motion.div layoutId="active-tab" />
```

| Feature    | Usage                     |
| ---------- | ------------------------- |
| `layout`   | Animate layout changes    |
| `layoutId` | Shared element transition |

```jsx
// Scroll Animation
<motion.section
  initial={{ opacity: 0 }}
  whileInView={{ opacity: 1 }}
  viewport={{ once: true }}
/>
```

| Feature           | Usage                    |
| ----------------- | ------------------------ |
| Server Components | Default in App Router    |
| Motion Components | Must be client-side      |
| Shared Layout     | Works inside client tree |
| Route Animation   | Usually in `layout.jsx`  |

```txt
app/
├── layout.jsx
├── page.jsx
├── components/
│   ├── MotionWrapper.jsx
│   └── AnimatedCard.jsx
```

| Common Use Cases | Usage                |
| ---------------- | -------------------- |
| Page Transition  | Route animation      |
| Hero Animation   | Landing pages        |
| Modal            | Shared layout        |
| Navbar           | Active tab indicator |
| Scroll Reveal    | Content sections     |
| Sidebar          | Animated navigation  |

- Use `"use client"` only where needed
- Keep animations inside client components
- Prefer transform-based animations
- Use `LazyMotion` in large apps
- Avoid heavy layout animation on huge lists
- Keep page transitions subtle

```jsx
"use client";

import { motion, AnimatePresence } from "framer-motion";

export default function Page() {
  return (
    <motion.main
      initial={{
        opacity: 0,
        y: 20,
      }}
      animate={{
        opacity: 1,
        y: 0,
      }}
      exit={{
        opacity: 0,
      }}
      transition={{
        duration: 0.3,
      }}
      className="p-10"
    >
      Dashboard
    </motion.main>
  );
}
```

---

## 📌 Best Practices

Follow scalable, performant, and maintainable animation patterns for production-ready UI.

### Animation Performance

| Practice                               | Reason                |
| -------------------------------------- | --------------------- |
| Prefer `x`, `y`, `scale`, `rotate`     | GPU accelerated       |
| Avoid animating `width`/`height` often | Prevent layout reflow |
| Keep durations short                   | Better UX             |
| Use subtle motion                      | Avoid distracting UI  |
| Avoid excessive blur/shadow animation  | Expensive rendering   |

```jsx
<motion.div
  animate={{
    x: 100,
    scale: 1.05,
  }}
/>
```

### Variants & Reusability

| Practice                        | Reason                |
| ------------------------------- | --------------------- |
| Reuse variants                  | Scalable architecture |
| Keep animation configs separate | Cleaner code          |
| Use consistent naming           | Easier maintenance    |
| Share transition configs        | UI consistency        |

```jsx
export const fadeUp = {
  hidden: {
    opacity: 0,
    y: 30,
  },
  visible: {
    opacity: 1,
    y: 0,
  },
};
```

### Interaction Design

| Practice                        | Reason                 |
| ------------------------------- | ---------------------- |
| Keep hover effects subtle       | Better accessibility   |
| Avoid long page transitions     | Faster navigation feel |
| Use gestures carefully          | Prevent UX overload    |
| Animate important elements only | Better focus           |

```jsx
whileHover={{
  scale: 1.03,
}}
```

### React & Next.js

| Practice                            | Reason                     |
| ----------------------------------- | -------------------------- |
| Use stable `key` props              | Correct animation tracking |
| Use `"use client"` only when needed | Better optimization        |
| Keep motion in client components    | Required in App Router     |
| Avoid unnecessary re-renders        | Smoother animation         |

### Large Scale Apps

| Practice                            | Reason                   |
| ----------------------------------- | ------------------------ |
| Use `LazyMotion`                    | Reduce bundle size       |
| Use `MotionConfig`                  | Shared transition system |
| Organize variants in separate files | Better scalability       |
| Prefer reusable animation wrappers  | Cleaner components       |

### Accessibility

| Practice                          | Reason                |
| --------------------------------- | --------------------- |
| Respect reduced motion            | Accessibility support |
| Avoid aggressive flashing motion  | Safer UX              |
| Keep motion predictable           | Better usability      |
| Avoid constant infinite animation | Reduce distraction    |

| Avoid Patterns                    | Reason                |
| --------------------------------- | --------------------- |
| Over-animation                    | Poor UX               |
| Huge spring values                | Jittery motion        |
| Animating large lists heavily     | FPS drops             |
| Deep nested animations            | Hard maintenance      |
| Mixing too many animation systems | Inconsistent behavior |

```txt
components/
├── motion/
│   ├── variants.js
│   ├── transitions.js
│   └── MotionWrapper.jsx
```

```jsx
<motion.button
  whileHover={{
    scale: 1.03,
  }}
  whileTap={{
    scale: 0.97,
  }}
  transition={{
    duration: 0.2,
  }}
  className="rounded-lg bg-black px-5 py-3 text-white"
>
  Checkout
</motion.button>
```

---

## 📌 Debugging & Troubleshooting

Common Framer Motion issues usually come from incorrect rendering, layout conflicts, or missing animation setup.

| Animation Not Working     | Fix                               |
| ------------------------- | --------------------------------- |
| Animation not running     | Check `initial` / `animate` props |
| No motion import          | Import from `framer-motion`       |
| Invalid motion component  | Use `motion.div` etc              |
| State not updating        | Verify React state flow           |
| Animation instantly jumps | Add `transition`                  |

```jsx
<motion.div initial={{ opacity: 0 }} animate={{ opacity: 1 }} />
```

| AnimatePresence Issues     | Fix                         |
| -------------------------- | --------------------------- |
| Exit animation not working | Wrap with `AnimatePresence` |
| Exit not triggering        | Use conditional rendering   |
| Wrong animation order      | Use `mode="wait"`           |
| Re-render issue            | Add stable `key`            |

```jsx
<AnimatePresence mode="wait">
  {open && <motion.div exit={{ opacity: 0 }} />}
</AnimatePresence>
```

| Layout Animation Issues | Fix                      |
| ----------------------- | ------------------------ |
| Layout animation jumps  | Add `layout` prop        |
| Shared animation broken | Match same `layoutId`    |
| Janky layout transition | Reduce layout complexity |
| Grid animation flickers | Use stable structure     |

```jsx
<motion.div layout />
```

| Next.js Issues                   | Fix                                |
| -------------------------------- | ---------------------------------- |
| Motion not working in App Router | Add `"use client"`                 |
| Server component error           | Move to client component           |
| Route transition not working     | Use route `key`                    |
| Hydration mismatch               | Avoid browser-only logic on server |

```jsx
"use client";
```

| Scroll Animation Issues      | Fix                             |
| ---------------------------- | ------------------------------- |
| `whileInView` not triggering | Check viewport visibility       |
| Animation repeats            | Use `viewport={{ once: true }}` |
| Scroll progress incorrect    | Verify scroll container         |
| Parallax lag                 | Reduce transform intensity      |

```jsx
viewport={{
  once: true,
}}
```

| Drag Issues         | Fix                    |
| ------------------- | ---------------------- |
| Drag not moving     | Add `drag` prop        |
| Drag overflowing    | Use `dragConstraints`  |
| Weird momentum      | Disable `dragMomentum` |
| Cursor not updating | Add cursor styles      |

```jsx
<motion.div drag dragMomentum={false} />
```

| Performance Issues  | Fix                           |
| ------------------- | ----------------------------- |
| Laggy animation     | Prefer transform properties   |
| FPS drops           | Reduce heavy layout animation |
| Blur/shadow lag     | Avoid expensive filters       |
| Too many re-renders | Use Motion Values             |
| Large bundle size   | Use `LazyMotion`              |

| Debugging Checklist     | Purpose               |
| ----------------------- | --------------------- |
| Correct import          | Motion APIs available |
| Motion component used   | Animation support     |
| Stable React keys       | Proper transitions    |
| Proper client component | Next.js compatibility |
| Transition configured   | Smooth animation      |

- Prefer transform animations
- Keep variants predictable
- Use stable layout structure
- Avoid animating large DOM trees
- Use browser DevTools performance tab
- Test animations on low-end devices

```jsx
<AnimatePresence mode="wait">
  {open && (
    <motion.div
      key="modal"
      initial={{
        opacity: 0,
        scale: 0.95,
      }}
      animate={{
        opacity: 1,
        scale: 1,
      }}
      exit={{
        opacity: 0,
        scale: 0.95,
      }}
      transition={{
        duration: 0.2,
      }}
    />
  )}
</AnimatePresence>
```

---

## 📌 Advanced Animation Concepts

Advanced animation concepts help create smoother, more natural, and scalable UI motion systems.

| Animation Types | Usage                   |
| --------------- | ----------------------- |
| Tween           | Precise timed animation |
| Spring          | Natural physics motion  |
| Keyframes       | Multi-step animation    |
| Inertia         | Momentum-based movement |

```jsx
transition={{
  type: "spring",
  stiffness: 120,
  damping: 20,
}}
```

| Physics-Based Animation | Usage                  |
| ----------------------- | ---------------------- |
| `stiffness`             | Spring strength        |
| `damping`               | Motion smoothness      |
| `mass`                  | Weight/inertia         |
| `velocity`              | Initial movement speed |

```jsx
transition={{
  type: "spring",
  stiffness: 100,
  damping: 15,
  mass: 1,
}}
```

### Keyframe Animation

```jsx
<motion.div
  animate={{
    x: [0, 100, 50, 120],
    opacity: [0, 1, 0.5, 1],
  }}
/>
```

### Animation Sequencing

```jsx
// Run animations step-by-step.
await controls.start({
  x: 100,
});

await controls.start({
  rotate: 90,
});
```

### Animation Orchestration

| Property          | Usage                  |
| ----------------- | ---------------------- |
| `staggerChildren` | Delay child animations |
| `delayChildren`   | Delay child start      |
| `when`            | Parent/child order     |

```jsx
transition={{
  staggerChildren: 0.15,
}}
```

### Motion Value Interpolation

```jsx
const rotate = useTransform(x, [-200, 200], [-15, 15]);
```

### Shared State Animation

```jsx
animate={{
  scale: active ? 1.1 : 1,
}}
```

### Gesture Physics

| Feature           | Usage              |
| ----------------- | ------------------ |
| `dragElastic`     | Stretch effect     |
| `dragMomentum`    | Inertia after drag |
| `bounceStiffness` | Bounce strength    |
| `bounceDamping`   | Bounce smoothness  |

```jsx
dragElastic={0.2}
dragMomentum={false}
```

### Layout Transition Concepts

| Feature       | Usage                      |
| ------------- | -------------------------- |
| `layout`      | Automatic layout animation |
| `layoutId`    | Shared element transition  |
| `LayoutGroup` | Sync layout changes        |

### Timing & Easing

| Easing        | Usage           |
| ------------- | --------------- |
| `"linear"`    | Constant speed  |
| `"easeIn"`    | Slow start      |
| `"easeOut"`   | Smooth finish   |
| `"easeInOut"` | Balanced motion |

```jsx
transition={{
  duration: 0.4,
  ease: "easeInOut",
}}
```

| Advanced Patterns    | Usage                |
| -------------------- | -------------------- |
| Stagger Lists        | Sequential UI reveal |
| Shared Layout        | Tabs/modals          |
| Scroll Linked Motion | Parallax             |
| Drag Physics         | Interactive cards    |
| Motion Mapping       | Cursor effects       |
| Chained Animation    | Multi-step UI        |

- Prefer spring for interactive UI
- Keep easing consistent across app
- Avoid excessive bounce values
- Use orchestration for lists
- Use Motion Values for reactive animation
- Keep animation systems reusable

```jsx
<motion.div
  drag
  whileHover={{
    scale: 1.03,
  }}
  whileTap={{
    scale: 0.97,
  }}
  transition={{
    type: "spring",
    stiffness: 120,
    damping: 15,
  }}
  className="rounded-xl border p-6"
>
  Interactive Card
</motion.div>
```

---

## 📌 Common APIs

Framer Motion provides components, hooks, and utilities for animations, gestures, layout transitions, and motion control.

| Core API          | Usage              | Example               |
| ----------------- | ------------------ | --------------------- |
| `motion`          | Animated elements  | `motion.div`          |
| `AnimatePresence` | Exit animations    | `<AnimatePresence />` |
| `LayoutGroup`     | Shared layout sync | `<LayoutGroup />`     |
| `MotionConfig`    | Global config      | `<MotionConfig />`    |
| `LazyMotion`      | Lazy-load features | `<LazyMotion />`      |
| `Reorder`         | Sortable lists     | `<Reorder.Group />`   |

```jsx
<motion.div animate={{ opacity: 1 }} />
```

| Motion Hooks        | Usage                    | Example                  |
| ------------------- | ------------------------ | ------------------------ |
| `useAnimation`      | Manual animation control | `controls.start()`       |
| `useScroll`         | Scroll tracking          | `scrollYProgress`        |
| `useTransform`      | Map motion values        | `useTransform(x)`        |
| `useSpring`         | Smooth reactive values   | `useSpring(x)`           |
| `useMotionValue`    | Reactive motion state    | `useMotionValue(0)`      |
| `useVelocity`       | Track speed              | `useVelocity(x)`         |
| `useCycle`          | Toggle states            | `useCycle(false, true)`  |
| `useAnimate`        | Imperative animation     | `animate(scope.current)` |
| `useInView`         | Viewport detection       | `useInView(ref)`         |
| `useMotionTemplate` | Dynamic motion strings   | `useMotionTemplate`      |

| Gesture APIs | Usage               |
| ------------ | ------------------- |
| `whileHover` | Hover animation     |
| `whileTap`   | Click/tap animation |
| `whileFocus` | Focus animation     |
| `whileDrag`  | Drag interaction    |
| `drag`       | Enable dragging     |

```jsx
<motion.button
  whileHover={{
    scale: 1.05,
  }}
/>
```

| Layout APIs   | Usage                 |
| ------------- | --------------------- |
| `layout`      | Auto layout animation |
| `layoutId`    | Shared transitions    |
| `LayoutGroup` | Sync layout animation |

```jsx
<motion.div layout />
```

| Scroll APIs   | Usage              |
| ------------- | ------------------ |
| `whileInView` | Viewport animation |
| `viewport`    | Viewport settings  |
| `useScroll`   | Scroll progress    |

```jsx
whileInView={{
  opacity: 1,
}}
```

| Variant APIs | Usage           |
| ------------ | --------------- |
| `variants`   | Reusable states |
| `initial`    | Starting state  |
| `animate`    | Active state    |
| `exit`       | Exit state      |

```jsx
variants = { fadeUp };
```

| Transition APIs | Usage            |
| --------------- | ---------------- |
| `transition`    | Animation config |
| `duration`      | Timing           |
| `delay`         | Delay start      |
| `ease`          | Easing           |
| `type`          | Tween/spring     |

```jsx
transition={{
  duration: 0.3,
}}
```

| Most Used APIs    | Usage              |
| ----------------- | ------------------ |
| `motion.div`      | General animation  |
| `whileHover`      | Hover effects      |
| `AnimatePresence` | Exit animation     |
| `variants`        | Reusable animation |
| `layout`          | Layout transition  |
| `useScroll`       | Scroll animation   |
| `useTransform`    | Value mapping      |

- Prefer variants for reusable animation
- Use Motion Values for reactive motion
- Use `layout` sparingly on large lists
- Keep transitions consistent
- Use `LazyMotion` in large apps
- Prefer transform animations

---

---

---

---

---
