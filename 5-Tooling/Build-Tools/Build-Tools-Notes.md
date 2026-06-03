## 📌 Frontend Build Tools Overview

```txt
Your React Code
      ↓
Build Tools
      ↓
Optimized JS/CSS Files
      ↓
Browser
```

| Tool    | Purpose    | Main Job                           | Used In             |
| ------- | ---------- | ---------------------------------- | ------------------- |
| Babel   | Compiler   | Convert Modern JS/JSX → Browser JS | React, Vue, Angular |
| Webpack | Bundler    | Combine JS/CSS/Assets into bundles | React, Vue, Angular |
| Vite    | Build Tool | Dev Server + Build + Bundling      | React, Vue, Svelte  |

| Task             | Babel | Webpack | Vite       |
| ---------------- | ----- | ------- | ---------- |
| JSX → JS         | ✅    | ❌      | Uses Babel |
| ES6 → ES5        | ✅    | ❌      | Uses Babel |
| Bundle Files     | ❌    | ✅      | ✅         |
| Dev Server       | ❌    | ⚠️      | ✅         |
| HMR              | ❌    | ✅      | ✅         |
| Production Build | ❌    | ✅      | ✅         |
| Asset Handling   | ❌    | ✅      | ✅         |
| Fast Startup     | ❌    | ❌      | ✅         |

```txt
Babel: Transpiles modern JavaScript/JSX into browser-compatible JavaScript.
Webpack: Bundles project assets into optimized files.
Vite: Modern build tool providing fast development server and production builds.
```

### Example

```jsx
// Input
const App = () => {
  return <h1>Hello</h1>;
};

//Output
const App = function () {
  return React.createElement("h1", null, "Hello");
};
```

### Without Babel

```txt
Old Browsers
Cannot Understand:
JSX
Optional Chaining
Arrow Functions
```

---

## 📌 Version Control & Collaboration Ecosystem

| Tool        | Purpose                     | Main Job              |
| ----------- | --------------------------- | --------------------- |
| Git         | Version Control             | Track Code Changes    |
| GitHub      | Repository Hosting          | Collaboration         |
| GitLab      | Repository + DevOps         | Collaboration + CI/CD |
| Bitbucket   | Repository Hosting          | Atlassian Ecosystem   |
| Azure Repos | Repository Hosting          | Azure DevOps          |
| SVN         | Centralized Version Control | Legacy Systems        |

| Git Concepts | Purpose                  |
| ------------ | ------------------------ |
| Repository   | Project Storage          |
| Commit       | Save Snapshot            |
| Branch       | Separate Development     |
| Merge        | Combine Changes          |
| Rebase       | Clean Commit History     |
| Tag          | Version Release          |
| Stash        | Temporary Save           |
| Cherry Pick  | Copy Specific Commit     |
| Fork         | Personal Repository Copy |
| Clone        | Download Repository      |
| Pull         | Get Latest Changes       |
| Push         | Upload Changes           |

| CI/CD Tool      | Purpose           |
| --------------- | ----------------- |
| GitHub Actions  | CI/CD             |
| GitLab CI/CD    | CI/CD             |
| Jenkins         | Automation Server |
| Azure Pipelines | CI/CD             |
| CircleCI        | CI/CD             |
| Travis CI       | CI/CD             |

| Git Hooks  | Purpose                |
| ---------- | ---------------------- |
| pre-commit | Validate Before Commit |
| commit-msg | Check Commit Format    |
| pre-push   | Run Tests Before Push  |

| Code Quality Tools | Purpose         |
| ------------------ | --------------- |
| ESLint             | Code Quality    |
| Prettier           | Code Formatting |
| Stylelint          | CSS Linting     |
| SonarQube          | Code Analysis   |

---

## 📌 Unit Testing (Jest + React Testing Library)

| Tool                        | Purpose                 | Main Job                              |
| --------------------------- | ----------------------- | ------------------------------------- |
| Jest                        | Test Runner             | Run Tests, Mock Functions, Assertions |
| React Testing Library (RTL) | Component Testing       | Test UI Like Real User                |
| Vitest                      | Modern Jest Alternative | Faster Testing With Vite              |
| Playwright                  | E2E Testing             | Test Complete User Flows              |

```txt
Unit Tests
↓
Component Logic

Integration Tests
↓
Multiple Components

E2E Tests
↓
Entire Application
```

| Test Case             | Example                 |
| --------------------- | ----------------------- |
| Component Rendering   | Login Form Visible      |
| Button Click          | Submit Button Works     |
| Form Validation       | Email Required          |
| API States            | Loading, Success, Error |
| Conditional Rendering | Admin Menu Visible      |
| User Interaction      | Open Modal              |
| Custom Hooks          | useAuth, useDebounce    |
| Utility Functions     | formatDate()            |

### Example

- Login Form Submit

```tsx
// Component
<button>Login</button>;

// Test
render(<LoginForm />);
await user.click(screen.getByText("Login"));
expect(loginApi).toHaveBeenCalled();
```

| Feature           | What To Test              |
| ----------------- | ------------------------- |
| Login Form        | Email/password validation |
| Registration Form | Required fields           |
| User Table        | Data rendering            |
| Search Box        | Search results update     |
| Modal             | Opens and closes          |
| API Call          | Loading, Success, Error   |
| Pagination        | Next/Previous buttons     |
| Role-Based UI     | Admin menu visibility     |
| Custom Hook       | Auth state changes        |
| Utility Function  | Date formatting           |

---
