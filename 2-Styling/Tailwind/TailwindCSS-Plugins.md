## 📌 clsx

```bash
npm install clsx
```

- Usage:
  - Conditional Classes
  - Dynamic Styling
  - Tailwind CSS
  - Component Variants
  - Active States

```txt
clsx()
   ↓
Combine Classes
   ↓
Ignore false/null/undefined
   ↓
Return Final Class String
```

### Syntax

```tsx
// clsx → clsx(class1, condition && class2, {...})
clsx("btn", isActive && "active"); // "btn active"

// Single Conditions
import clsx from "clsx";
const className = clsx("btn", isActive && "active"); // "btn active"

// Multiple Conditions
clsx("btn", isActive && "active", isLoading && "loading"); // "btn active loading"
```

```tsx
// Object Syntax
clsx({
  active: true,
  disabled: false,
}); // "active"

// Array Syntax
clsx(["btn", "primary"]); // "btn primary"
```

### Button Variant Example

```tsx
className={clsx(
  "btn",
  variant === "primary" &&
    "btn-primary",

  variant === "danger" &&
    "btn-danger"
)}
```

```tsx
// Common Pattern
className={clsx(
  "base-class",
  condition &&
    "conditional-class"
)}

// Without clsx
className={
  isActive
    ? "btn active"
    : "btn"
}

// With clsx
className={clsx(
  "btn",
  isActive && "active"
)}
```

---

## 📌 CVA (Class Variance Authority)

```bash
npm install class-variance-authority
```

### clsx vs CVA Diff

| Tool         | Purpose             |
| ------------ | ------------------- |
| `clsx`       | Conditional Classes |
| `CVA`        | Component Variants  |
| `clsx + CVA` | Most Common Setup   |

- Usage:
  - Component Variants
  - Design Systems
  - Reusable UI Components
  - Tailwind Projects
  - Button/Input/Card Variants
    Without CVA:

```tsx
// Without CVA:
className={clsx(
  "btn",
  variant === "primary" &&
    "bg-blue-500",

  variant === "danger" &&
    "bg-red-500",

  size === "sm" &&
    "px-2 py-1",

  size === "lg" &&
    "px-6 py-3"
)}
```

### Syntax

```ts
// cva → cva(baseClasses, config)

const buttonVariants = cva("", {
  variants: {},
});
```

```tsx
// Create
import { cva } from "class-variance-authority";
const buttonVariants = cva("rounded font-medium", {
  variants: {
    variant: {
      primary: "bg-blue-500 text-white",
      danger: "bg-red-500 text-white",
    },

    size: {
      sm: "px-2 py-1",
      lg: "px-6 py-3",
    },
  },

  defaultVariants: {
    variant: "primary",
    size: "sm",
  },
});

// Usage
buttonVariants(); // rounded font-medium bg-blue-500 text-white px-2 py-1

buttonVariants({
  variant: "danger",
}); // red button

buttonVariants({
  size: "lg",
}); // large button

buttonVariants({
  variant: "danger",
  size: "lg",
}); // large red button
```

### React Component

```tsx
type ButtonProps = {
  variant?: "primary" | "danger";
  size?: "sm" | "lg";
};

export function Button({ variant, size }: ButtonProps) {
  return (
    <button
      className={buttonVariants({
        variant,
        size,
      })}
    >
      Click
    </button>
  );
}

// Usage
<Button />
<Button
  variant="danger"
/>
<Button
  size="lg"
/>
<Button
  variant="danger"
  size="lg"
/>
```

```tsx
const buttonVariants = cva("rounded font-medium transition", {
  variants: {
    variant: {
      primary: "bg-blue-500 text-white",
      danger: "bg-red-500 text-white",
    },

    size: {
      sm: "px-2 py-1",
      md: "px-4 py-2",
      lg: "px-6 py-3",
    },
  },

  defaultVariants: {
    variant: "primary",
    size: "md",
  },
});

// CVA + clsx
type ButtonProps = {
  variant?: "primary" | "danger";
  size?: "sm" | "md" | "lg";
  disabled?: boolean;
  className?: string;
};

export function Button({ variant, size, disabled, className }: ButtonProps) {
  return (
    <button
      className={clsx(
        buttonVariants({
          variant,
          size,
        }),
        disabled && "opacity-50 pointer-events-none",
        className,
      )}
    />
  );
}

// Usage
<Button />
<Button variant="danger" />
<Button size="lg" />
<Button variant="danger" size="lg" />
<Button disabled />
<Button className="w-full" />
```

---
