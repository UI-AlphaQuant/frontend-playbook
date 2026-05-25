# 👉 Animation & Tools

## 📌 Animation Ecosystem & Related Tools

Modern animation tools provide UI motion, timelines, physics, SVG animation, 3D effects, and interactive experiences.

| Tool            | Type                        | Works With    | Best For              |
| --------------- | --------------------------- | ------------- | --------------------- |
| `Framer Motion` | UI Animation Library        | React only    | Modern React UI       |
| `GSAP`          | Animation Engine            | Any framework | Complex timelines     |
| `React Spring`  | Physics Animation           | React only    | Natural motion        |
| `Anime.js`      | JS Animation Library        | Any framework | Lightweight animation |
| `Motion One`    | WAAPI Animation             | Any framework | Modern web animation  |
| `Popmotion`     | Functional Animation Engine | JS/React      | Low-level animation   |

### Native Browser Animation

| Tool               | Type        | Works With    | Best For                  |
| ------------------ | ----------- | ------------- | ------------------------- |
| CSS Transitions    | Native CSS  | Any framework | Hover/focus effects       |
| CSS Animations     | Native CSS  | Any framework | Simple repeated animation |
| Web Animations API | Browser API | Any framework | Native JS animation       |

### SVG & Vector Animation

| Tool      | Type                         | Works With    | Best For              |
| --------- | ---------------------------- | ------------- | --------------------- |
| `Lottie`  | JSON Animation Renderer      | Any framework | Designer animations   |
| `Rive`    | Interactive Vector Animation | Any framework | Interactive UI motion |
| `SVGator` | SVG Animation Tool           | SVG/Web       | Animated SVG exports  |

### 3D & Canvas Animation

| Tool                | Type              | Works With    | Best For                |
| ------------------- | ----------------- | ------------- | ----------------------- |
| `Three.js`          | 3D Engine         | Any framework | 3D scenes               |
| `React Three Fiber` | React 3D Renderer | React only    | React-based 3D          |
| `PixiJS`            | WebGL Renderer    | Any framework | High-performance canvas |
| `Matter.js`         | Physics Engine    | Any framework | Physics simulation      |

### Scroll & Smooth Motion

| Tool                | Type                 | Works With    | Best For         |
| ------------------- | -------------------- | ------------- | ---------------- |
| `Lenis`             | Smooth Scroll Engine | Any framework | Smooth scrolling |
| `Locomotive Scroll` | Scroll Animation     | Any framework | Scroll effects   |
| `ScrollTrigger`     | GSAP Plugin          | Any framework | Scroll timelines |

### Gesture & Interaction

| Tool          | Type            | Works With    | Best For                |
| ------------- | --------------- | ------------- | ----------------------- |
| `Hammer.js`   | Gesture Library | Any framework | Touch gestures          |
| `use-gesture` | Gesture Hooks   | React only    | Drag/swipe interactions |

| Tool Comparison | Strength                 | Limitation              |
| --------------- | ------------------------ | ----------------------- |
| Framer Motion   | Easy React animation     | React-only              |
| GSAP            | Extremely powerful       | Larger API surface      |
| React Spring    | Smooth physics           | More setup              |
| Anime.js        | Lightweight              | Less React integration  |
| CSS Animation   | Native/browser optimized | Limited orchestration   |
| Lottie          | Designer-friendly        | Limited runtime control |

| When to Use Scenario         | Recommended Tool   |
| ---------------------------- | ------------------ |
| React UI animation           | Framer Motion      |
| Complex timelines            | GSAP               |
| Physics-heavy UI             | React Spring       |
| Lightweight animation        | Anime.js           |
| Native browser animation     | CSS / WAAPI        |
| SVG designer animation       | Lottie             |
| Interactive vector animation | Rive               |
| 3D animation                 | Three.js           |
| Smooth scrolling             | Lenis              |
| Scroll storytelling          | GSAP ScrollTrigger |

- Use one primary animation system
- Prefer CSS for simple transitions
- Use Framer Motion for React UI
- Use GSAP for advanced timelines
- Avoid mixing multiple heavy animation libraries
- Optimize animation bundle size

---
