## 📌 useLocalStorage

```tsx
import { useState, useEffect } from "react";

export function useLocalStorage<T>(key: string, initialValue: T) {
  const [value, setValue] = useState<T>(() => {
    const item = localStorage.getItem(key);
    return item ? JSON.parse(item) : initialValue;
  });

  useEffect(() => {
    localStorage.setItem(key, JSON.stringify(value));
  }, [key, value]);

  return [value, setValue] as const;
}
```

- Usage:
  - Theme
  - User Preferences
  - Sidebar State
  - Language Selection
  - Persisting State

```tsx
// Syntax → const [value, setValue] = useLocalStorage(key, initialValue);

const [theme, setTheme] = useLocalStorage("theme", "dark"); // "dark"
const [user, setUser] = useLocalStorage("user", {
  id: 1,
  name: "John",
}); // persisted object
```

---

## 📌 useFetch

```tsx
import { useState, useEffect } from "react";

export function useFetch<T>(url: string) {
  const [data, setData] = useState<T | null>(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState<string | null>(null);

  useEffect(() => {
    fetch(url)
      .then((res) => res.json())
      .then(setData)
      .catch((err) => setError(err.message))
      .finally(() => setLoading(false));
  }, [url]);

  return {
    data,
    loading,
    error,
  };
}
```

- Usage:
  - Dashboard Data
  - User Lists
  - Products
  - CMS Content
  - Simple API Calls

```tsx
// Syntax → const { data, loading, error } = useFetch<T>(url);

interface User {
  id: number;
  name: string;
}
const { data, loading, error } = useFetch<User[]>("/api/users");
```

---

## 📌 useDebounce

```tsx
import { useState, useEffect } from "react";

export function useDebounce<T>(value: T, delay = 500) {
  const [debouncedValue, setDebouncedValue] = useState(value);

  useEffect(() => {
    const timer = setTimeout(() => {
      setDebouncedValue(value);
    }, delay);

    return () => clearTimeout(timer);
  }, [value, delay]);

  return debouncedValue;
}
```

- Usage:
  - Search
  - Filters
  - Autocomplete
  - API Optimization

```tsx
// Syntax → const debouncedValue = useDebounce(value, delay);

const debouncedSearch = useDebounce(search, 500); // delayed search value
```

---

## 📌 useWindowSize

```tsx
import { useState, useEffect } from "react";

export function useWindowSize() {
  const [size, setSize] = useState({
    width: window.innerWidth,
    height: window.innerHeight,
  });
  useEffect(() => {
    const handleResize = () => {
      setSize({
        width: window.innerWidth,
        height: window.innerHeight,
      });
    };
    window.addEventListener("resize", handleResize);
    return () => window.removeEventListener("resize", handleResize);
  }, []);

  return size;
}
```

- Usage:
  - Responsive Layouts
  - Breakpoint Checks
  - Mobile Detection
  - Conditional Rendering

```tsx
// Syntax → const { width, height } = useWindowSize();

const { width, height } = useWindowSize(); // viewport size
```

---

## 📌 useMediaQuery

```tsx
import { useState, useEffect } from "react";

export function useMediaQuery(query: string) {
  const [matches, setMatches] = useState(window.matchMedia(query).matches);
  useEffect(() => {
    const media = window.matchMedia(query);
    const listener = () => setMatches(media.matches);
    media.addEventListener("change", listener);
    return () => media.removeEventListener("change", listener);
  }, [query]);

  return matches;
}
```

- Usage:
  - Mobile Detection
  - Responsive Components
  - Layout Switching
  - Device Specific UI
  - Breakpoint Checks

```tsx
// Syntax → const matches = useMediaQuery(query);

const isMobile = useMediaQuery("(max-width:768px)"); // true | false
const isTablet = useMediaQuery("(min-width:769px) and (max-width:1024px)"); // true | false
const isDarkMode = useMediaQuery("(prefers-color-scheme: dark)"); // true | false

return isMobile ? <MobileMenu /> : <DesktopMenu />;
```

---

## 📌 useToggle

```tsx
import { useState } from "react";

export function useToggle(initialValue = false) {
  const [value, setValue] = useState(initialValue);
  const toggle = () => setValue((prev) => !prev);
  return [value, toggle] as const;
}
```

- Usage:
  - Modal
  - Drawer
  - Accordion
  - Dropdown
  - Sidebar
  - Show/Hide Password

```tsx
// Syntax → const [value, toggle] = useToggle(initialValue);

const [isOpen, toggle] = useToggle(); // false
const [isModalOpen, toggleModal] = useToggle(true); // true

<button onClick={toggle}>Toggle Menu</button>;
{
  isOpen && <Menu />;
}
```

---

## 📌 usePrevious

```tsx
import { useEffect, useRef } from "react";

export function usePrevious<T>(value: T) {
  const ref = useRef<T>();
  useEffect(() => {
    ref.current = value;
  }, [value]);
  return ref.current;
}
```

- Usage:
  - Compare Previous vs Current Values
  - Detect Changes
  - Animations
  - Form Tracking
  - Debugging

```tsx
// Syntax → const previous = usePrevious(value);

const prevCount = usePrevious(count); // previous count
const prevUser = usePrevious(user); // previous user

const [count, setCount] = useState(0);
const prevCount = usePrevious(count);
count; // 5
prevCount; // 4
```

---

## 📌 useOnClickOutside

```tsx
import { useEffect, RefObject } from "react";

export function useOnClickOutside<T extends HTMLElement>(
  ref: RefObject<T | null>,
  callback: () => void,
) {
  useEffect(() => {
    const handleClick = (event: MouseEvent) => {
      if (ref.current && !ref.current.contains(event.target as Node)) {
        callback();
      }
    };
    document.addEventListener("mousedown", handleClick);
    return () => {
      document.removeEventListener("mousedown", handleClick);
    };
  }, [ref, callback]);
}
```

- Usage:
  - Modal
  - Dropdown
  - Popover
  - Context Menu
  - Sidebar
  - Date Picker

```tsx
// Syntax → useOnClickOutside(ref, callback);

useOnClickOutside(modalRef, closeModal); // closes modal
useOnClickOutside(dropdownRef, () => setOpen(false)); // closes dropdown

const modalRef = useRef<HTMLDivElement>(null);
const [isOpen, setIsOpen] = useState(true);
useOnClickOutside(modalRef, () => setIsOpen(false));
return <div ref={modalRef}>Modal Content</div>;
```

---

## 📌 useCopyToClipboard

```tsx
export function useCopyToClipboard() {
  return async (text: string) => {
    try {
      await navigator.clipboard.writeText(text);

      return true;
    } catch {
      return false;
    }
  };
}
```

- Usage:
  - Coupon Codes
  - Invite Links
  - Share URLs
  - Referral Codes
  - API Keys
  - Copy Buttons

```tsx
// Syntax → const copy = useCopyToClipboard();

const copy = useCopyToClipboard();
copy("Hello World"); // copied
copy("https://example.com"); // copied URL

<button onClick={() => copy("WELCOME10")}>Copy Code</button>;
```

---

## 📌 useInterval

```tsx
import { useEffect, useRef } from "react";
export function useInterval(callback: () => void, delay: number) {
  const savedCallback = useRef(callback);
  useEffect(() => {
    savedCallback.current = callback;
  }, [callback]);
  useEffect(() => {
    const id = setInterval(() => savedCallback.current(), delay);
    return () => clearInterval(id);
  }, [delay]);
}
```

- Usage:
  - Polling APIs
  - Live Dashboard
  - Stock Prices
  - Auto Refresh
  - Notifications
  - Timers

```tsx
// Syntax → useInterval(callback, delay);

useInterval(fetchUsers, 5000); // every 5 seconds
useInterval(() => setCount((c) => c + 1), 1000); // every 1 second
```

---

## 📌 useTimeout

```tsx
import { useEffect, useRef } from "react";

export function useTimeout(callback: () => void, delay: number) {
  const savedCallback = useRef(callback);

  useEffect(() => {
    savedCallback.current = callback;
  }, [callback]);

  useEffect(() => {
    const id = setTimeout(() => savedCallback.current(), delay);
    return () => clearTimeout(id);
  }, [delay]);
}
```

- Usage:
  - Toast Messages
  - Notifications
  - Delayed Actions
  - Auto Logout
  - Redirects
  - Splash Screens

```tsx
// Syntax → useTimeout(callback, delay);

useTimeout(closeToast, 3000); // after 3 seconds
useTimeout(() => navigate("/login"), 5000); // after 5 seconds

const [visible, setVisible] = useState(true);
useTimeout(() => setVisible(false), 3000);
visible; // true → false (after 3s)
```

---

## 📌 useMounted

```tsx
import { useEffect, useState } from "react";

export function useMounted() {
  const [mounted, setMounted] = useState(false);

  useEffect(() => {
    setMounted(true);
  }, []);

  return mounted;
}
```

- Usage:
  - Client-Only Logic
  - SSR Checks
  - Hydration Safety
  - Browser APIs
  - localStorage Access
  - window/document Access

```tsx
// Syntax → const mounted = useMounted();

const mounted = useMounted(); // false → true
if (!mounted) return null;
return <div>Client Rendered</div>;
```

---

## 📌 useScrollPosition

```tsx
import { useEffect, useState } from "react";

export function useScrollPosition() {
  const [scrollY, setScrollY] = useState(0);
  useEffect(() => {
    const handleScroll = () => setScrollY(window.scrollY);
    window.addEventListener("scroll", handleScroll);
    return () => window.removeEventListener("scroll", handleScroll);
  }, []);

  return scrollY;
}
```

- Usage:
  - Sticky Header
  - Scroll Progress
  - Back To Top Button
  - Infinite Scroll
  - Hide/Show Navbar
  - Scroll Animations

```tsx
// Syntax → const scrollY = useScrollPosition();

const scrollY = useScrollPosition(); // 450
const showButton = scrollY > 300; // true
{
  scrollY > 100 ? <StickyHeader /> : <Header />;
}
```

---

## 📌 useInfiniteScroll

```tsx
import { useEffect, useRef } from "react";

export function useInfiniteScroll(callback: () => void) {
  const ref = useRef<HTMLDivElement>(null);
  useEffect(() => {
    const observer = new IntersectionObserver((entries) => {
      if (entries[0].isIntersecting) {
        callback();
      }
    });
    if (ref.current) {
      observer.observe(ref.current);
    }
    return () => observer.disconnect();
  }, [callback]);

  return ref;
}
```

- Usage:
  - Social Media Feeds
  - Product Listings
  - Blog Posts
  - Comments
  - Search Results
  - Pagination Without Buttons

```tsx
// Syntax → useInfiniteScroll(callback);

const loadMore = () => {
  setPage((prev) => prev + 1);
};
const loadMoreRef = useInfiniteScroll(loadMore); // fetch next page
```

---

## 📌 useAuth

```tsx
import { createContext, useContext, useState } from "react";

type User = {
  id: number;
  name: string;
};

type AuthContextType = {
  user: User | null;
  login: (user: User) => void;
  logout: () => void;
  isAuthenticated: boolean;
};

const AuthContext = createContext<AuthContextType | undefined>(undefined);

export function AuthProvider({ children }: { children: React.ReactNode }) {
  const [user, setUser] = useState<User | null>(null);
  const login = (user: User) => setUser(user);
  const logout = () => setUser(null);

  return (
    <AuthContext.Provider
      value={{
        user,
        login,
        logout,
        isAuthenticated: !!user,
      }}
    >
      {children}
    </AuthContext.Provider>
  );
}

export function useAuth() {
  const context = useContext(AuthContext);
  if (!context) {
    throw new Error("useAuth must be used within AuthProvider");
  }
  return context;
}
```

- Usage:
  - Authentication
  - Protected Routes
  - User Profile
  - Role Management
  - Permissions
  - Login / Logout

```tsx
// Syntax → const { user, login, logout, isAuthenticated } = useAuth();

const { user, login, logout, isAuthenticated } = useAuth();
user; // { id: 1, name: "John" }
isAuthenticated; // true
```

---

## 📌 useQueryParams

```tsx
import { useSearchParams } from "react-router-dom";

export function useQueryParams() {
  const [searchParams, setSearchParams] = useSearchParams();
  const params = Object.fromEntries(searchParams.entries());
  return [params, setSearchParams] as const;
}
```

- Usage:
  - Search
  - Filters
  - Pagination
  - Sorting
  - Deep Linking
  - Shareable URLs

```tsx
// Syntax → const [params, setParams] = useQueryParams();

// /products?page=1&search=react&sort=price
const [params, setParams] = useQueryParams();
params.page; // "1"
params.search; // "react"
params.sort; // "price"
```

---

## 📌 usePagination

```tsx
import { useMemo, useState } from "react";

export function usePagination<T>(data: T[], itemsPerPage = 10) {
  const [currentPage, setCurrentPage] = useState(1);
  const totalPages = Math.ceil(data.length / itemsPerPage);
  const currentData = useMemo(() => {
    const start = (currentPage - 1) * itemsPerPage;
    return data.slice(start, start + itemsPerPage);
  }, [data, currentPage, itemsPerPage]);

  const nextPage = () =>
    setCurrentPage((page) => Math.min(page + 1, totalPages));
  const prevPage = () => setCurrentPage((page) => Math.max(page - 1, 1));

  return {
    currentPage,
    totalPages,
    currentData,
    nextPage,
    prevPage,
    setCurrentPage,
  };
}
```

- Usage:
  - Tables
  - Product Listings
  - User Lists
  - Reports
  - Search Results
  - Client-Side Pagination

```tsx
// Syntax → const pagination = usePagination(data, itemsPerPage);

const pagination = usePagination(users, 10);

pagination.currentPage; // 1
pagination.totalPages; // 5
pagination.currentData; // current page data
```

---

## 📌 useDarkMode

```tsx
import { useEffect, useState } from "react";

export function useDarkMode() {
  const [darkMode, setDarkMode] = useState(() => {
    return localStorage.getItem("theme") === "dark";
  });

  useEffect(() => {
    document.documentElement.classList.toggle("dark", darkMode);
    localStorage.setItem("theme", darkMode ? "dark" : "light");
  }, [darkMode]);

  return [darkMode, setDarkMode] as const;
}
```

- Usage:
  - Theme Switching
  - User Preferences
  - Dark / Light UI
  - Persist Theme
  - System Theme Detection

```tsx
// Syntax → const [darkMode, setDarkMode] = useDarkMode();

const [darkMode, setDarkMode] = useDarkMode(); // true

<button onClick={() => setDarkMode(!darkMode)}>Toggle Theme</button>;
{
  darkMode ? "🌙 Dark" : "☀️ Light";
}
```

---
