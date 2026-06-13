## 📌 React Component

```tsx
import React from "react";

interface ProductCardProps {
  // Primitive Types
  title: string;
  price: number;
  inStock: boolean;
  discount: null;

  // Array Types
  tags: string[];
  ratings: number[];
  flags: boolean[];

  // Union Types
  status: "active" | "inactive" | "draft";

  // Optional
  description?: string;

  // Object Type
  seller: {
    name: string;
    city: string;
  };

  // Tuple
  dimensions: [number, number];

  // Function Type
  onBuy: () => void;
  onWishlist: (id: number) => void;

  // Any, Unknown
  rawData: any;
  apiResponse: unknown;

  // Enum Like
  size: "S" | "M" | "L" | "XL";

  // Record
  stockByCity: Record<string, number>;

  // Date
  createdAt: Date;

  // Nested Array Objects
  reviews: {
    user: string;
    rating: number;
  }[];

  // Readonly
  readonly productId: number;
}

const ProductCard = ({
  title,
  price,
  inStock,
  tags,
  status,
  seller,
  dimensions,
  size,
  reviews,
  createdAt,
  onBuy,
  onWishlist,
}: ProductCardProps) => {
  return (
    <div>
      <h2>{title}</h2>
      <p>Price: ₹{price}</p>
      <p>Stock: {inStock ? "Available" : "Out of Stock"}</p>
      <p>Status: {status}</p>
      <p>
        Seller: {seller.name} ({seller.city})
      </p>
      <p>
        Dimensions: {dimensions[0]} × {dimensions[1]} cm
      </p>
      <p>Size: {size}</p>
      <p>Created: {createdAt.toDateString()}</p>
      <button onClick={onBuy}>Buy Now</button>
      <button onClick={() => onWishlist(101)}>Add Wishlist</button>
      <ul>
        {tags.map((tag, index) => (
          <li key={index}>{tag}</li>
        ))}
      </ul>
      <h4>Reviews</h4>
      <ul>
        {reviews.map((review, index) => (
          <li key={index}>
            {review.user} - {review.rating}★
          </li>
        ))}
      </ul>
    </div>
  );
};

export default ProductCard;
```

```tsx
<ProductCard
  productId={101}
  title="Logitech MX Mechanical Keyboard"
  price={14999}
  inStock={true}
  discount={null}
  tags={["Wireless", "Mechanical", "Bluetooth"]}
  ratings={[5, 4, 5]}
  flags={[true, true, false]}
  status="active"
  description="Premium low-profile wireless mechanical keyboard"
  seller={{
    name: "Logitech Store",
    city: "Bangalore",
  }}
  dimensions={[43, 13]}
  onBuy={() => {
    console.log("Proceed to Checkout");
  }}
  onWishlist={(id) => {
    console.log("Added to Wishlist:", id);
  }}
  rawData={{
    inventoryId: "INV-2026-101",
    warehouse: "Mumbai Hub",
  }}
  apiResponse={{
    success: true,
    message: "Product Loaded",
  }}
  size="L"
  stockByCity={{
    Bangalore: 25,
    Mumbai: 18,
    Ahmedabad: 12,
  }}
  createdAt={new Date("2026-01-15")}
  reviews={[
    {
      user: "John",
      rating: 5,
    },
    {
      user: "Rahul",
      rating: 4,
    },
  ]}
/>
```

---

## 📌 React Router & Main files

### main.tsx

```tsx
import React from "react";
import ReactDOM from "react-dom/client";
import { Provider } from "react-redux";
import { store } from "./store";
import App from "./App";
import { I18nProvider } from "./i18n";
import { ErrorBoundary } from "./components";

ReactDOM.createRoot(document.getElementById("root")!).render(
  <React.StrictMode>
    <ErrorBoundary>
      <Provider store={store}>
        <I18nProvider>
          <App />
        </I18nProvider>
      </Provider>
    </ErrorBoundary>
  </React.StrictMode>,
);
```

### App.tsx

```tsx
import { RouterProvider } from "react-router-dom";
import { router } from "./routes/AppRouter";
import { ThemeContextProvider } from "./theme";
import { GlobalStyles } from "./theme/styles/globalStyles";

function App() {
  return (
    <ThemeContextProvider>
      <GlobalStyles />
      <RouterProvider router={router} />
    </ThemeContextProvider>
  );
}

export default App;
```

### AppRouter.tsx

```tsx
import { createBrowserRouter } from "react-router-dom";
import { ROUTES } from "@/constants/routes";
import { AuthLayout, AppLayout } from "@/components/Layout";
import ForgotPassword from "@/pages/Auth/ForgotPassword/ForgotPassword";
import Login from "@/pages/Auth/Login/Login";
import Dashboard from "@/pages/Dashboard/Dashboard";
import { ProtectedLayout } from "./ProtectedRoute";
import UserList from "@/pages/User/UserList/UserList";
import RouteError from "@/pages/Fallback/RouteError/RouteError";

export const router = createBrowserRouter([
  // Public Routes
  {
    element: <AuthLayout />,
    errorElement: <RouteError />,
    children: [
      { path: ROUTES.AUTH.LOGIN, element: <Login /> },
      { path: ROUTES.AUTH.FORGOT_PASSWORD, element: <ForgotPassword /> },
    ],
  },

  // Protected Routes
  {
    element: <ProtectedLayout />,
    errorElement: <RouteError />,
    children: [
      {
        element: <AppLayout />,
        children: [
          { path: ROUTES.APP.DASHBOARD, element: <Dashboard /> },
          { path: ROUTES.APP.USERLIST, element: <UserList /> },
        ],
      },
    ],
  },
]);
```

### ProtectedRoute.tsx

```tsx
import { ACCESS_TOKEN_KEY } from "@/constants/storage";
import { Navigate, Outlet, useLocation } from "react-router-dom";

const DISABLE_AUTH = true; // ON/OFF Protected Route

export function ProtectedLayout() {
  const location = useLocation();
  const token = localStorage.getItem(ACCESS_TOKEN_KEY);

  if (!DISABLE_AUTH && !token) {
    return <Navigate to="/login" state={{ from: location }} replace />;
  }

  return <Outlet />;
}
```

### Sidebar.tsx

```tsx
import { Menu } from "@/components/Antd";
import { SiderContent, SiderHeader, SiderWrap } from "./Sidebar.style";
import { LogoMain } from "@/assets/svgs";
import { getAppMenus } from "@/constants";
import { useLocation, useNavigate } from "react-router-dom";
import { useTranslation } from "react-i18next";
import { useMemo } from "react";

interface SidebarProps {
  collapsed: boolean;
}

export function Sidebar({ collapsed = false }: SidebarProps) {
  const { t } = useTranslation();

  const navigate = useNavigate();
  const location = useLocation();

  const menus = useMemo(() => getAppMenus(t), [t]);

  return (
    <SiderWrap collapsed={collapsed} width={220}>
      <SiderHeader>
        <LogoMain />
      </SiderHeader>
      <SiderContent>
        <Menu
          className="sider-menu"
          mode="inline"
          defaultSelectedKeys={[location.pathname]}
          selectedKeys={[location.pathname]}
          onClick={(e) => navigate(e.key)}
          items={menus}
        />
      </SiderContent>
    </SiderWrap>
  );
}

export default Sidebar;
```

### Navigation

```tsx
import { useNavigate } from "react-router-dom";

export default function Login() {
  const navigate = useNavigate();

  const handleLogin = () => {
    navigate("/dashboard");
  };

  return <button onClick={handleLogin}>Login</button>;
}
```

---

## 📌 React Error Boundary

```text
src/
│
├── components/
│ └── ErrorBoundary.tsx
│
├── pages/
│ └── UserProfile.tsx
│
├── App.tsx
│
└── main.tsx
```

### ErrorBoundary.tsx

```tsx
import React, { Component, ReactNode } from "react";

interface Props {
  children: ReactNode;
}

interface State {
  hasError: boolean;
  errorMessage: string;
}

class ErrorBoundary extends Component<Props, State> {
  state: State = {
    hasError: false,
    errorMessage: "",
  };

  static getDerivedStateFromError(error: Error): State {
    return {
      hasError: true,
      errorMessage: error.message,
    };
  }

  componentDidCatch(error: Error, errorInfo: React.ErrorInfo) {
    console.error(error);
    console.error(errorInfo.componentStack);
  }

  render() {
    if (this.state.hasError) {
      return (
        <div>
          <h2>Something Went Wrong</h2>

          <p>{this.state.errorMessage}</p>
        </div>
      );
    }

    return this.props.children;
  }
}

export default ErrorBoundary;
```

### UserProfile.tsx

```tsx
const UserProfile = () => {
  const hasError = true;

  if (hasError) {
    throw new Error("User Profile Failed");
  }

  return <h2>User Profile</h2>;
};

export default UserProfile;
```

### App.tsx

```tsx
import ErrorBoundary from "./components/ErrorBoundary";
import UserProfile from "./pages/UserProfile";

export default function App() {
  return (
    <ErrorBoundary>
      <UserProfile />
    </ErrorBoundary>
  );
}
```

---

## 📌 Config

### tsconfig.app.json

```json
{
  "compilerOptions": {
    "noEmit": true,
    "target": "ES2022",
    "lib": ["DOM", "DOM.Iterable", "ES2022", "dom", "esnext"],
    "jsx": "react-jsx",
    "module": "ESNext",
    "moduleResolution": "bundler",
    "types": ["vite/client", "jest", "@testing-library/jest-dom"],

    "paths": {
      "@/*": ["./src/*"],
      "@components/*": ["./src/components/*"],
      "@pages/*": ["./src/pages/*"],
      "@routes/*": ["./src/routes/*"],
      "@store/*": ["./src/store/*"],
      "@constants/*": ["./src/constants/*"],
      "@utils/*": ["./src/utils/*"],
      "@theme/*": ["./src/theme/*"],
      "@i18n/*": ["./src/i18n/*"],
      "@test/*": ["./src/test/*"],
      "@config/*": ["./src/config/*"]
    },

    "strict": true,
    "skipLibCheck": true,
    "isolatedModules": true,
    "resolveJsonModule": true,
    "allowSyntheticDefaultImports": true,
    "esModuleInterop": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noFallthroughCasesInSwitch": true
  },
  "include": ["src", ".storybook/**/*", "vitest.shims.d.ts"],
  "exclude": ["node_modules", "dist"]
}
```

### .vscode/settings.json

```json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",

  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[javascriptreact]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[typescript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[typescriptreact]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[json]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },

  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": "always"
  },

  "typescript.tsdk": "node_modules/typescript/lib",

  "editor.tabSize": 2,
  "editor.insertSpaces": true,

  "files.eol": "\n",

  "files.exclude": {
    "**/node_modules": true,
    "**/dist": true,
    "**/coverage": true
  },

  "search.exclude": {
    "**/node_modules": true,
    "**/dist": true
  }
}
```

### .vscode/extensions.json

```json
{
  "recommendations": [
    "esbenp.prettier-vscode",
    "dbaeumer.vscode-eslint",
    "ms-vscode.vscode-typescript-next",
    "styled-components.vscode-styled-components",
    "eamodio.gitlens"
  ]
}
```

---

## 📌 Custom Hooks

### useLocalStorage.js

```tsx
import { useState } from "react";

export function useLocalStorage(key, initialValue) {
  const [value, setValue] = useState(localStorage.getItem(key) || initialValue);

  const updateValue = (newValue) => {
    localStorage.setItem(key, newValue);
    setValue(newValue);
  };

  return [value, updateValue];
}

// Usage
const [theme, setTheme] = useLocalStorage("theme", "light");

console.log(theme);
```

---

## 📌 Local Font in React

```txt
src/
├─ assets/
│  └─ fonts/
│      ├─ Inter-Regular.woff2
│      └─ Inter-Bold.woff2
├─ styles/
│  └─ fonts.css
```

```css
/* fonts.css */
@font-face {
  font-family: "Inter";
  src: url("../assets/fonts/Inter-Regular.woff2") format("woff2");
  font-weight: 400;
  font-style: normal;
}

@font-face {
  font-family: "Inter";
  src: url("../assets/fonts/Inter-Bold.woff2") format("woff2");
  font-weight: 700;
  font-style: normal;
}

body {
  font-family: "Inter", sans-serif;
}
```

```tsx
// main.tsx
import "./styles/fonts.css";
```

### Google Fonts (CDN)

```html
<!-- index.html -->
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link
  href="https://fonts.googleapis.com/css2?family=Inter:wght@400;700&display=swap"
  rel="stylesheet"
/>
```

### NPM Package

```bash
npm install @fontsource/inter
```

```tsx
// main.tsx
import "@fontsource/inter";
import "@fontsource/inter/700.css";
```

---
