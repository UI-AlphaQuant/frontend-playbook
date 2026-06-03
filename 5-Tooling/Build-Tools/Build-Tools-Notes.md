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

## 📌 package.json

| Purpose    | Project Configuration & Dependency Management |
| ---------- | --------------------------------------------- |
| Created By | npm init / npm create vite                    |
| Location   | Project Root                                  |

**_Responsibilities_**

- Project Metadata
- Dependencies
- Scripts
- Versions
- Build Commands
- Tool Configuration

### Typical package.json

```json
// React + Vite
{
  "name": "my-app",
  "private": true,
  "version": "1.0.0",

  "scripts": {
    "dev": "vite",
    "build": "tsc && vite build",
    "preview": "vite preview",
    "lint": "eslint ."
  },

  "dependencies": {
    "react": "^19.0.0",
    "react-dom": "^19.0.0"
  },

  "devDependencies": {
    "vite": "^7.0.0",
    "typescript": "^5.8.0",
    "eslint": "^9.0.0"
  }
}
```

| Property        | Purpose              | Example                  |
| --------------- | -------------------- | ------------------------ |
| name            | Project Name         | `"name": "my-react-app"` |
| version         | App Version          | `"version": "1.0.0"`     |
| private         | Prevent npm Publish  | `"private": true`        |
| scripts         | Custom Commands      | `"dev": "vite"`          |
| dependencies    | Production Packages  | `"react": "^19.0.0"`     |
| devDependencies | Development Packages | `"vite": "^7.0.0"`       |

### Common Scripts

| Script  | Purpose                  | Example                     |
| ------- | ------------------------ | --------------------------- |
| dev     | Start Development Server | `"dev": "vite"`             |
| build   | Production Build         | `"build": "vite build"`     |
| preview | Preview Production Build | `"preview": "vite preview"` |
| lint    | Run ESLint               | `"lint": "eslint ."`        |
| test    | Run Tests                | `"test": "vitest"`          |

### Common dependencies

| Package               | Purpose       |
| --------------------- | ------------- |
| react                 | UI Library    |
| react-dom             | DOM Rendering |
| react-router-dom      | Routing       |
| axios                 | API Calls     |
| zustand               | Global State  |
| @tanstack/react-query | Server State  |
| react-hook-form       | Forms         |
| zod                   | Validation    |

### Common devDependencies

| Package                | Purpose           |
| ---------------------- | ----------------- |
| vite                   | Build Tool        |
| typescript             | Type Checking     |
| eslint                 | Code Quality      |
| prettier               | Code Formatting   |
| vitest                 | Unit Testing      |
| @testing-library/react | Component Testing |
| tailwindcss            | Styling           |

- **Dependencies:** Application Needs These To Run, Required to run app in production
- **devDependencies:** Developer Needs These To Build/Test App, Required only during development

| Feature                 | dependencies                      | devDependencies                  |
| ----------------------- | --------------------------------- | -------------------------------- |
| Purpose                 | Required to run app in production | Required only during development |
| Installed In Production | ✅                                | ❌                               |
| Installed Locally       | ✅                                | ✅                               |
| Included In Final Build | ✅                                | ❌                               |
| Examples                | React, Axios, Zustand             | Vite, TypeScript, ESLint         |
| Install Command         | `npm i package`                   | `npm i -D package`               |

---

## 📌 eslint.config.js

| Purpose     | Find Code Quality Issues & Enforce Coding Standards |
| ----------- | --------------------------------------------------- |
| Type        | Static Code Analysis Tool                           |
| Runs During | Development, Build, CI/CD                           |
| Config File | `eslint.config.js` (Modern)                         |

Extension Name: ESLint

**Example Issues**

- Unused Variable
- Missing Dependency

### Modern React + Vite Config

```js
// eslint.config.js
import js from "@eslint/js";
import tseslint from "typescript-eslint";

export default [js.configs.recommended, ...tseslint.configs.recommended];
```

| Common Rules                | Purpose                 |
| --------------------------- | ----------------------- |
| no-unused-vars              | Remove unused variables |
| no-console                  | Prevent console logs    |
| eqeqeq                      | Force `===`             |
| react-hooks/rules-of-hooks  | Hook Rules              |
| react-hooks/exhaustive-deps | useEffect Dependencies  |

| Related Files    | Purpose              |
| ---------------- | -------------------- |
| eslint.config.js | ESLint Configuration |
| package.json     | Lint Scripts         |
| .eslintignore    | Ignore Files/Folders |

### Frontend Setup

```txt
ESLint > Code Quality
Prettier > Code Formatting
Husky > Run Before Commit
```

---

## 📌 VS Code Extensions (Frontend Developer)

| Code Quality             | Free | Purpose                |
| ------------------------ | ---- | ---------------------- |
| ESLint                   | ✅   | Code Quality & Linting |
| Prettier                 | ✅   | Auto Formatting        |
| Error Lens               | ✅   | Inline Error Display   |
| Pretty TypeScript Errors | ✅   | Better TS Errors       |
| Code Spell Checker       | ✅   | Spell Checking         |

| React Development         | Free | Purpose               |
| ------------------------- | ---- | --------------------- |
| ES7+ React Snippets       | ✅   | React Snippets        |
| Simple React Snippets     | ✅   | React Snippets        |
| Tailwind CSS IntelliSense | ✅   | Tailwind Autocomplete |
| SVG Preview               | ✅   | SVG Preview           |
| Import Cost               | ✅   | Show Package Size     |

| Navigation          | Free | Purpose                |
| ------------------- | ---- | ---------------------- |
| Path Intellisense   | ✅   | File Path Autocomplete |
| Material Icon Theme | ✅   | Better File Icons      |
| Project Manager     | ✅   | Manage Projects        |
| Image Preview       | ✅   | Image Preview          |

| Git                  | Free | Purpose              |
| -------------------- | ---- | -------------------- |
| GitLens              | ✅   | Git History & Blame  |
| Git Graph            | ✅   | Branch Visualization |
| GitHub Pull Requests | ✅   | Manage PRs           |
| Conventional Commits | ✅   | Commit Format        |

| API Development | Free | Purpose                |
| --------------- | ---- | ---------------------- |
| Thunder Client  | ✅   | API Testing            |
| REST Client     | ✅   | API Testing In VS Code |
| OpenAPI Editor  | ✅   | Swagger/OpenAPI        |

| Productivity      | Free | Purpose               |
| ----------------- | ---- | --------------------- |
| Auto Rename Tag   | ✅   | Rename Paired Tags    |
| Todo Tree         | ✅   | TODO/FIXME Tracking   |
| Turbo Console Log | ✅   | Generate Console Logs |
| Better Comments   | ✅   | Colored Comments      |
| Peacock           | ✅   | Workspace Colors      |
| DotENV            | ✅   | .env Highlighting     |

| AI Coding      | Free       | Purpose                  |
| -------------- | ---------- | ------------------------ |
| Codeium        | ✅         | AI Code Completion       |
| Continue       | ✅         | Open Source AI Assistant |
| GitHub Copilot | ❌         | AI Code Completion       |
| Cursor AI      | ⚠️ Limited | AI Coding Assistant      |

| HTML/CSS                  | Free | Purpose          |
| ------------------------- | ---- | ---------------- |
| Live Server               | ✅   | Local Dev Server |
| Tailwind CSS IntelliSense | ✅   | Tailwind Support |
| Auto Rename Tag           | ✅   | HTML Tag Sync    |

---
