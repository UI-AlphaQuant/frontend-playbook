# 👉 Styled Component

| Feature                | Purpose                  | Common Usage          |
| ---------------------- | ------------------------ | --------------------- |
| Tagged Templates       | Create styled components | `styled.button`       |
| Props Styling          | Dynamic styles           | Variants/themes       |
| Scoped CSS             | Prevent style conflicts  | Component styling     |
| ThemeProvider          | Shared themes            | Dark/light themes     |
| Global Styles          | Inject global CSS        | Resets/base styles    |
| Extending Styles       | Reuse component styles   | Variant components    |
| CSS Helper             | Shared style blocks      | Utility patterns      |
| attrs()                | Default props/attributes | Forms/buttons         |
| Keyframes              | Component animations     | Loaders/transitions   |
| Polymorphic Components | Change rendered element  | `as="a"`              |
| Nesting                | Child element styling    | Structured CSS        |
| Pseudo Classes         | Interactive states       | `:hover` `:focus`     |
| Media Queries          | Responsive styling       | Mobile-first UI       |
| Component Selectors    | Style nested components  | Complex UI systems    |
| Ref Forwarding         | DOM references           | Inputs/modals         |
| State-based Styling    | Conditional UI styles    | Alerts/buttons        |
| Theming                | Shared design tokens     | Design systems        |
| Dynamic Animations     | Animation props          | Speed/variant control |

---

## 📌 Required Imports

```jsx
import styled, {
  ThemeProvider,
  createGlobalStyle,
  css,
  keyframes,
} from "styled-components";
```

---

## 📌 Tagged Templates

```jsx
const Button = styled.button`
  background: #2563eb;
  color: white;
`;
```

- Creates styled React components
- Uses template literal syntax

---

## 📌 Props Styling

```jsx
const Button = styled.button`
  background: ${(props) => (props.primary ? "#2563eb" : "#111")};
`;
```

- Dynamic styles using component props
- Common for variants/themes

---

## 📌 Scoped CSS

```jsx
const Card = styled.div`
  padding: 20px;
`;
```

- Auto-generated unique class names
- Prevents global CSS conflicts

---

## 📌 ThemeProvider

```jsx
const theme = {
  primary: "#2563eb",
};

<ThemeProvider theme={theme}>
  <App />
</ThemeProvider>;
```

- Shared global theme values
- Common in design systems

---

## 📌 Global Styles

```jsx
const GlobalStyle = createGlobalStyle`
  body {
    margin: 0;
  }
`;
```

- Injects global CSS
- Useful for resets/base styles

---

## 📌 Extending Styles

```jsx
const Button = styled.button`
  padding: 10px;
`;

const RoundedButton = styled(Button)`
  border-radius: 999px;
`;
```

- Reuse existing styled components
- Avoids duplicate styles

---

## 📌 CSS Helper

```jsx
const center = css`
  display: flex;
  justify-content: center;
`;

const Box = styled.div`
  ${center}
`;
```

- Shared reusable style blocks
- Useful for common patterns

---

## 📌 attrs()

```jsx
const Input = styled.input.attrs({
  type: "text",
})`
  padding: 10px;
`;
```

- Default props/attributes
- Common for forms/buttons

---

## 📌 Keyframes

```jsx
const fade = keyframes`
  from {
    opacity: 0;
  }

  to {
    opacity: 1;
  }
`;

const Box = styled.div`
  animation: ${fade} 0.3s ease;
`;
```

- Component-scoped animations
- Uses CSS keyframes syntax

---

## 📌 Pseudo Classes

```jsx
const Button = styled.button`
  &:hover {
    background: black;
  }
`;
```

---

## 📌 Media Queries

```jsx
const Box = styled.div`
  @media (min-width: 768px) {
    width: 50%;
  }
`;
```

---

## 📌 Component Selectors

```jsx
const Icon = styled.span`
  color: red;
`;

const Button = styled.button`
  ${Icon} {
    margin-right: 8px;
  }
`;
```

---

## 📌 Polymorphic Components

```jsx
<Button as="a" href="/">
  Home
</Button>
```

- Changes rendered HTML element
- Keeps same styles

---

## 📌 Styling Based on State

```jsx
const Alert = styled.div`
  background: ${(props) => (props.error ? "red" : "green")};
`;
```

## 📌 Theming

```jsx
const theme = {
  colors: {
    primary: "#2563eb",
    text: "#ffffff",
  },
};
```

```jsx
// Theme Provider
<ThemeProvider theme={theme}>
  <App />
</ThemeProvider>
```

```jsx
// Using Theme Values
const Button = styled.button`
  background: ${(props) => props.theme.colors.primary};
  color: ${(props) => props.theme.colors.text};
`;
```

---

- Popular in React ecosystems
- Scoped component-based styling
- Useful for dynamic/themed UI
- Runtime styling may impact large apps

---
