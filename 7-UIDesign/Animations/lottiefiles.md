## 📌 Lottie Files

Lottie uses lightweight JSON-based animations exported from Adobe After Effects for scalable web and mobile animations.

| Feature              | Usage                        |
| -------------------- | ---------------------------- |
| JSON Animation       | Lightweight vector animation |
| Cross Platform       | Web, React, Mobile           |
| Scalable             | No quality loss              |
| Interactive          | Play, pause, loop            |
| Performance Friendly | Smaller than GIF/video       |

### Create Lottie

| Method                    | Usage                             |
| ------------------------- | --------------------------------- |
| After Effects + Bodymovin | Most common professional workflow |
| LottieFiles Creator       | Browser-based editor              |
| Figma Plugins             | Export simple animations          |
| SVG to Lottie Tools       | Convert SVG animations            |
| Custom JSON Editing       | Manual advanced editing           |
| AI Animation Tools        | Generate/export motion            |

```txt
After Effects
  ↓
Bodymovin Plugin
  ↓
Export JSON
  ↓
Use in App
```

## 📌 Lottie JSON Structure

Lottie animations are stored as JSON files describing layers, shapes, timing, transforms, and motion.

### JSON Sample

```json
{
  "v": "5.7.4",
  "fr": 30,
  "ip": 0,
  "op": 60,
  "w": 500,
  "h": 500,
  "layers": []
}
```

### Common JSON Keys

| Key      | Meaning          |
| -------- | ---------------- |
| `v`      | Lottie version   |
| `fr`     | Frame rate       |
| `ip`     | Start frame      |
| `op`     | End frame        |
| `w`      | Width            |
| `h`      | Height           |
| `layers` | Animation layers |
| `assets` | Images/assets    |
| `nm`     | Layer name       |

### What Happens Internally?

```txt
JSON Data
  ↓
Lottie Parser
  ↓
SVG / Canvas Rendering
  ↓
Animation Playback
```

### Lottie Formats

| Format    | Usage                       |
| --------- | --------------------------- |
| JSON      | Standard Lottie animation   |
| `.lottie` | Compressed optimized format |
| SVG       | Vector rendering            |
| Canvas    | Heavy animation rendering   |
| GIF       | Legacy alternative          |
| MP4/WebM  | Video fallback              |

---

### HTML Usage

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/bodymovin/5.12.2/lottie.min.js"></script>
```

```html
<div id="lottie"></div>
```

```js
lottie.loadAnimation({
  container: document.getElementById("lottie"),
  renderer: "svg",
  loop: true,
  autoplay: true,
  path: "/animations/loading.json",
});
```

```js
// HTML Playback Controls
animation.stop(); // Stop Animation
animation.pause(); // Pause Animation
animation.play(); // Play Animation
animation.setSpeed(2); // Set Speed
animation.playSegments([10, 40], true); // Play Specific Frames
```

---

### React Usage

```bash
npm install lottie-react
```

```tsx
// Basic Usage
import Lottie from "lottie-react";
import animationData from "./loading.json";

function Loader() {
  return <Lottie animationData={animationData} />;
}
```

```tsx
<Lottie animationData={animation} loop /> // Loop Animation
<Lottie animationData={success} loop={false} /> // Play Once

// Custom Size
<Lottie
  animationData={animation}
  style={{
    width: 200,
    height: 200,
  }}
/>;

// Conditional Rendering
{
  isLoading && <Lottie animationData={loading} />;
}
```

```tsx
// React Playback Controls
const lottieRef = useRef(); //Using Ref

lottieRef.current?.pause(); // Pause
lottieRef.current?.play(); // Play
lottieRef.current?.stop(); // Stop
```

---

| Option/Prop     | Usage                   | Example                             | HTML | React |
| --------------- | ----------------------- | ----------------------------------- | ---- | ----- |
| `animationData` | JSON animation object   | `animationData={loadingJson}`       | ❌   | ✅    |
| `path`          | External JSON file path | `path: "/animations/loading.json"`  | ✅   | ❌    |
| `container`     | Target HTML element     | `document.getElementById("lottie")` | ✅   | ❌    |
| `renderer`      | Rendering type          | `"svg"`                             | ✅   | ❌    |
| `loop`          | Repeat animation        | `loop={true}`                       | ✅   | ✅    |
| `autoplay`      | Auto start animation    | `autoplay={true}`                   | ✅   | ✅    |
| `style`         | Width/height styling    | `style={{ width: 200 }}`            | ❌   | ✅    |
| `className`     | Custom CSS styling      | `className="lottie-loader"`         | ❌   | ✅    |

| Performance Tips        | Reason              |
| ----------------------- | ------------------- |
| Optimize animation size | Faster loading      |
| Avoid huge JSON files   | Better performance  |
| Lazy load animations    | Reduced bundle size |
| Reuse shared animations | Consistency         |

### Accessibility

| Area                 | Best Practice           |
| -------------------- | ----------------------- |
| Reduced Motion       | Respect motion settings |
| Decorative Animation | Avoid distraction       |
| Critical Feedback    | Combine with text/icons |

- Reduced Motion Example

```css
@media (prefers-reduced-motion: reduce) {
  .lottie-animation {
    display: none;
  }
}
```

| Common Problems        | Better Approach          |
| ---------------------- | ------------------------ |
| Huge animation files   | Optimize/export smaller  |
| Overusing animations   | Use subtle motion        |
| Blocking UI            | Lazy load animations     |
| GIF replacement misuse | Use proper vector motion |

- Keep animations lightweight
- Use subtle purposeful motion
- Prefer JSON over GIFs
- Respect reduced motion settings
- Reuse shared animation assets
- Avoid excessive looping animations
- Optimize for performance

---
