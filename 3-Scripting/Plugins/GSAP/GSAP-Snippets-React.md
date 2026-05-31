```text
src/
├─ animations/
│  ├─ core.js
│  ├─ presets.js
│  ├─ stagger.js
│  ├─ scroll.js
│  ├─ timelines.js
│  ├─ hover.js
│  ├─ hooks.js
│  ├─ utils.js
│  └─ index.js
│
├─ pages/
│  ├─ home.animation.js
│  └─ Home.jsx
```

### Core

```js
// animations/core.js
import gsap from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

export { gsap, ScrollTrigger };

export const DEFAULTS = {
  duration: 0.8,
  ease: "power2.out",
};

export const EASES = {
  smooth: "power2.out",
  soft: "power3.out",
  bounce: "back.out(1.7)",
  linear: "linear",
};

export const GPU_PROPS = {
  force3D: true,
};

export const prefersReducedMotion =
  typeof window !== "undefined"
    ? window.matchMedia("(prefers-reduced-motion: reduce)").matches
    : false;

export const killAnimation = (animation) => {
  if (!animation) return;

  animation.kill?.();

  if (animation.scrollTrigger) {
    animation.scrollTrigger.kill();
  }
};

export const killAllScrollTriggers = () => {
  ScrollTrigger.getAll().forEach((trigger) => trigger.kill());
};
```

### Presets

```js
// animations/presets.js
import { gsap, DEFAULTS, GPU_PROPS, prefersReducedMotion } from "./core";

// fade up animation
export const fadeUp = (target, options = {}) => {
  if (prefersReducedMotion) return;

  return gsap.from(target, {
    opacity: 0,
    y: 50,

    ...GPU_PROPS,
    ...DEFAULTS,
    ...options,
  });
};

// fade animation
export const fadeIn = (target, options = {}) => {
  if (prefersReducedMotion) return;

  return gsap.from(target, {
    opacity: 0,

    ...GPU_PROPS,
    ...DEFAULTS,
    ...options,
  });
};

// slide left animation
export const slideLeft = (target, options = {}) => {
  if (prefersReducedMotion) return;

  return gsap.from(target, {
    x: 100,
    opacity: 0,

    ...GPU_PROPS,
    ...DEFAULTS,
    ...options,
  });
};

// slide right animation
export const slideRight = (target, options = {}) => {
  if (prefersReducedMotion) return;

  return gsap.from(target, {
    x: -100,
    opacity: 0,

    ...GPU_PROPS,
    ...DEFAULTS,
    ...options,
  });
};

// scale animation
export const scaleIn = (target, options = {}) => {
  if (prefersReducedMotion) return;

  return gsap.from(target, {
    scale: 0.8,
    opacity: 0,
    transformOrigin: "center",

    ...GPU_PROPS,
    ...DEFAULTS,
    ...options,
  });
};

// rotate animation
export const rotateIn = (target, options = {}) => {
  if (prefersReducedMotion) return;

  return gsap.from(target, {
    rotate: 8,
    scale: 0.95,
    opacity: 0,

    ...GPU_PROPS,
    ...DEFAULTS,
    ...options,
  });
};

// text reveal animation
export const revealText = (target, options = {}) => {
  if (prefersReducedMotion) return;

  return gsap.from(target, {
    yPercent: 100,
    opacity: 0,
    stagger: 0.03,
    duration: 0.6,

    ...GPU_PROPS,
    ...options,
  });
};

// floating animation
export const floating = (target, options = {}) =>
  gsap.to(target, {
    y: -20,
    repeat: -1,
    yoyo: true,
    duration: 2,
    ease: "sine.inOut",

    ...options,
  });

// marquee animation
export const marquee = (target, options = {}) =>
  gsap.to(target, {
    xPercent: -50,
    repeat: -1,
    duration: 20,
    ease: "linear",

    ...options,
  });
```

### Stagger

```js
// animations/stagger.js
import { gsap, DEFAULTS, GPU_PROPS, prefersReducedMotion } from "./core";

// stagger fade animation
export const staggerFade = (target, options = {}) => {
  if (prefersReducedMotion) return;

  return gsap.from(target, {
    opacity: 0,
    y: 40,

    stagger: {
      each: 0.08,
    },

    lazy: true,

    ...GPU_PROPS,
    ...DEFAULTS,
    ...options,
  });
};

// stagger scale animation
export const staggerScale = (target, options = {}) => {
  if (prefersReducedMotion) return;

  return gsap.from(target, {
    opacity: 0,
    scale: 0.9,

    stagger: {
      each: 0.08,
    },

    lazy: true,

    ...GPU_PROPS,
    ...DEFAULTS,
    ...options,
  });
};

// grid stagger animation
export const gridStagger = (target, options = {}) => {
  if (prefersReducedMotion) return;

  return gsap.from(target, {
    opacity: 0,
    scale: 0.9,

    stagger: {
      each: 0.08,
      from: "center",
      grid: "auto",
    },

    lazy: true,

    ...GPU_PROPS,
    ...DEFAULTS,
    ...options,
  });
};

// reusable stagger utility
export const createStagger = ({
  target,
  from = {},
  stagger = 0.08,
  options = {},
}) => {
  if (prefersReducedMotion) return;

  return gsap.from(target, {
    stagger,
    lazy: true,

    ...GPU_PROPS,
    ...from,
    ...DEFAULTS,
    ...options,
  });
};
```

### Scroll

```js
// animations/scroll.js
import { gsap, ScrollTrigger, prefersReducedMotion } from "./core";

// scroll reveal animation
export const scrollReveal = (target, options = {}) => {
  if (prefersReducedMotion) return;

  return gsap.from(target, {
    opacity: 0,
    y: 60,
    force3D: true,
    lazy: true,

    scrollTrigger: {
      trigger: target,
      start: "top 85%",
      once: true,
      fastScrollEnd: true,
      invalidateOnRefresh: true,
    },

    duration: 0.8,
    ...options,
  });
};

// batch reveal animation
export const batchReveal = (target, options = {}) => {
  if (prefersReducedMotion) return;

  return ScrollTrigger.batch(target, {
    start: "top 90%",

    onEnter: (elements) => {
      gsap.from(elements, {
        opacity: 0,
        y: 40,
        stagger: 0.08,
        force3D: true,

        ...options,
      });
    },
  });
};

// parallax animation
export const parallax = (target, trigger) => {
  if (prefersReducedMotion) return;

  return gsap.to(target, {
    yPercent: -20,

    scrollTrigger: {
      trigger,
      scrub: true,
    },
  });
};

// pinned section animation
export const pinSection = (target) => {
  if (prefersReducedMotion) return;

  return gsap.to(target, {
    scrollTrigger: {
      trigger: target,
      pin: true,
      scrub: true,
    },
  });
};
```

### Timelines

```js
// animations/timelines.js
import { gsap, DEFAULTS } from "./core";

// reusable timeline
export const createTimeline = (options = {}) =>
  gsap.timeline({
    defaults: DEFAULTS,
    ...options,
  });

// hero section timeline
export const heroTimeline = () => {
  const tl = createTimeline();

  tl.from(".hero-title", {
    y: 80,
    opacity: 0,
  })
    .from(
      ".hero-subtitle",
      {
        y: 40,
        opacity: 0,
      },
      "-=0.5",
    )
    .from(
      ".hero-btn",
      {
        scale: 0.8,
        opacity: 0,
      },
      "-=0.4",
    );

  return tl;
};

// page transition timeline
export const pageTransition = () =>
  createTimeline()
    .to(".transition", {
      scaleY: 1,
      transformOrigin: "bottom",
    })
    .to(".transition", {
      scaleY: 0,
      transformOrigin: "top",
    });

// loader timeline
export const loaderTimeline = () =>
  createTimeline()
    .to(".loader", {
      opacity: 0,
    })
    .set(".loader", {
      display: "none",
    })
    .from(".page", {
      opacity: 0,
      y: 30,
    });
```

### Hover

```js
// animations/hover.js
import { gsap } from "./core";

// button hover animation
export const buttonHover = (element) => {
  if (!element) return;

  const enter = () => {
    gsap.to(element, {
      scale: 1.05,
    });
  };

  const leave = () => {
    gsap.to(element, {
      scale: 1,
    });
  };

  element.addEventListener("mouseenter", enter);
  element.addEventListener("mouseleave", leave);

  return () => {
    element.removeEventListener("mouseenter", enter);
    element.removeEventListener("mouseleave", leave);
  };
};

// magnetic hover animation
export const magnetic = (element) => {
  if (!element) return;

  const move = (e) => {
    const x = e.offsetX - element.clientWidth / 2;
    const y = e.offsetY - element.clientHeight / 2;

    gsap.to(element, {
      x: x * 0.2,
      y: y * 0.2,
      duration: 0.3,
    });
  };

  const leave = () => {
    gsap.to(element, {
      x: 0,
      y: 0,
    });
  };

  element.addEventListener("mousemove", move);
  element.addEventListener("mouseleave", leave);

  return () => {
    element.removeEventListener("mousemove", move);
    element.removeEventListener("mouseleave", leave);
  };
};
```

### Hooks

```js
// animations/hooks.js
import { useRef } from "react";
import { useGSAP } from "@gsap/react";

import { fadeUp } from "./presets";
import { staggerFade } from "./stagger";
import { heroTimeline } from "./timelines";

// fade up hook
export const useFadeUp = () => {
  const container = useRef(null);

  useGSAP(
    () => {
      fadeUp(".fade-up");
    },

    {
      scope: container,
      revertOnUpdate: true,
    },
  );

  return container;
};

// stagger hook
export const useStagger = () => {
  const container = useRef(null);

  useGSAP(
    () => {
      staggerFade(".card");
    },

    {
      scope: container,
      revertOnUpdate: true,
    },
  );

  return container;
};

// hero animation hook
export const useHeroAnimation = () => {
  const container = useRef(null);

  useGSAP(
    () => {
      heroTimeline();
    },

    {
      scope: container,
      revertOnUpdate: true,
    },
  );

  return container;
};
```

### Utils

```js
// animations/utils.js

// query selector
export const $ = (selector) => document.querySelector(selector);

// query selector all
export const $$ = (selector) => document.querySelectorAll(selector);

// random number utility
export const random = (min, max) => Math.random() * (max - min) + min;

// set will-change property
export const setWillChange = (target) => {
  if (!target) return;

  target.style.willChange = "transform";
};
```

### Index

```js
// animations/index.js
export * from "./core";
export * from "./presets";
export * from "./stagger";
export * from "./scroll";
export * from "./timelines";
export * from "./hover";
export * from "./hooks";
export * from "./utils";
```

### Home Animation

```js
// pages/home.animation.js
import { fadeUp, staggerFade, scrollReveal, heroTimeline } from "../animations";

// home page animations
export const homeAnimation = () => {
  heroTimeline();
  fadeUp(".hero-image");
  staggerFade(".card");
  scrollReveal(".section");
};
```

```js
// pages/Home.jsx
import { useFadeUp, useStagger, useHeroAnimation } from "../animations";

const Home = () => {
  const fadeRef = useFadeUp();
  const staggerRef = useStagger();
  const heroRef = useHeroAnimation();

  return (
    <div>
      <section ref={heroRef}>
        <h1 className="hero-title">Hero Title</h1>
        <p className="hero-subtitle">Hero Subtitle</p>
        <button className="hero-btn">Explore</button>
        <div className="hero-image" />
      </section>

      <section ref={fadeRef}>
        <div className="fade-up">Fade Content</div>
      </section>

      <section ref={staggerRef}>
        <div className="card">Card 1</div>
        <div className="card">Card 2</div>
        <div className="card">Card 3</div>
      </section>

      <section className="section">Scroll Section</section>
    </div>
  );
};

export default Home;
```

---
