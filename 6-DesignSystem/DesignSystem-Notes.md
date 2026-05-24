# 👉 Design System

## 📌 Core Foundations

| Foundation    | Purpose                  |
| ------------- | ------------------------ |
| Colors        | Brand & UI consistency   |
| Typography    | Readable text hierarchy  |
| Spacing       | Consistent layout rhythm |
| Grid/Layout   | Structured responsive UI |
| Breakpoints   | Responsive behavior      |
| Radius        | Shape consistency        |
| Shadows       | Elevation/depth          |
| Icons         | Unified visuals          |
| Motion        | Interaction feedback     |
| Accessibility | Inclusive UI             |

| Principle       | Usage                       |
| --------------- | --------------------------- |
| Consistency     | Reusable visual language    |
| Scalability     | Easier large-scale growth   |
| Reusability     | Shared styles/components    |
| Predictability  | Same UI behavior everywhere |
| Maintainability | Easier updates/refactoring  |

### Foundation Structure

```txt
design-system/
├── tokens/
├── typography/
├── colors/
├── spacing/
├── layouts/
├── icons/
├── motion/
├── accessibility/
└── themes/
```

### Primitive vs Semantic Tokens

| Token Type       | Purpose                 | Example                            | Real Usage              |
| ---------------- | ----------------------- | ---------------------------------- | ----------------------- |
| Primitive Tokens | Raw reusable values     | `--blue-500: #2563eb`              | Base design palette     |
| Semantic Tokens  | Meaning-based UI values | `--color-primary: var(--blue-500)` | Buttons, links, actions |

### Color Tokens

```css
:root {
  /* Brand */
  --color-primary-50: #eff6ff;
  --color-primary-100: #dbeafe;
  --color-primary-300: #93c5fd;
  --color-primary-500: #2563eb;
  --color-primary-700: #1d4ed8;
  --color-primary-900: #1e3a8a;

  /* Neutral */
  --color-gray-50: #f9fafb;
  --color-gray-100: #f3f4f6;
  --color-gray-200: #e5e7eb;
  --color-gray-300: #d1d5db;
  --color-gray-400: #9ca3af;
  --color-gray-500: #6b7280;
  --color-gray-600: #4b5563;
  --color-gray-700: #374151;
  --color-gray-800: #1f2937;
  --color-gray-900: #111827;

  /* Semantic */
  --color-success-bg: #ecfdf5;
  --color-success-light: #dcfce7;
  --color-success: #16a34a;
  --color-success-dark: #166534;

  --color-warning-bg: #fffbeb;
  --color-warning-light: #fef3c7;
  --color-warning: #f59e0b;
  --color-warning-dark: #92400e;

  --color-danger-bg: #fef2f2;
  --color-danger-light: #fee2e2;
  --color-danger: #dc2626;
  --color-danger-dark: #991b1b;

  --color-info-bg: #eff6ff;
  --color-info-light: #dbeafe;
  --color-info: #0ea5e9;
  --color-info-dark: #0369a1;

  /* Text */
  --color-text-primary: #111827;
  --color-text-secondary: #4b5563;
  --color-text-muted: #6b7280;
  --color-text-inverse: #ffffff;

  /* Borders */
  --color-border-light: #f3f4f6;
  --color-border: #e5e7eb;
  --color-border-dark: #cbd5e1;

  /* ERP Surfaces */
  --color-background: #f5f7fb;
  --color-surface: #ffffff;
  --color-sidebar: #111827;
  --color-sidebar-hover: #1f2937;
  --color-header: #ffffff;
  --color-card: #ffffff;
  --color-overlay: rgba(0, 0, 0, 0.5);
}
```

### Typography Tokens

```css
:root {
  /* Font Family */
  --font-family-base: Inter, sans-serif;
  --font-family-heading: Poppins, sans-serif;
  --font-family-mono: monospace;

  /* Font Weight */
  --font-weight-light: 300;
  --font-weight-regular: 400;
  --font-weight-medium: 500;
  --font-weight-semibold: 600;
  --font-weight-bold: 700;

  /* Font Sizes */
  --text-2xs: 10px;
  --text-xs: 12px;
  --text-sm: 14px;
  --text-md: 16px;
  --text-lg: 18px;
  --text-xl: 20px;
  --text-2xl: 24px;
  --text-3xl: 30px;
  --text-4xl: 36px;
  --text-5xl: 48px;

  /* Line Heights */
  --leading-tight: 1.2;
  --leading-normal: 1.5;
  --leading-relaxed: 1.8;

  /* Letter Spacing */
  --tracking-tight: -0.02em;
  --tracking-normal: 0;
  --tracking-wide: 0.03em;
}
```

### Spacing Tokens

```css
:root {
  --space-1: 4px;
  --space-2: 8px;
  --space-3: 12px;
  --space-4: 16px;
  --space-5: 24px;
  --space-6: 32px;
  --space-7: 48px;
}
```

### Radius Tokens

```css
:root {
  --radius-sm: 4px;
  --radius-md: 8px;
  --radius-lg: 16px;
  --radius-full: 9999px;
}
```

### Shadow Tokens

```css
:root {
  --shadow-sm: 0 1px 2px rgba(0, 0, 0, 0.05);
  --shadow-md: 0 4px 8px rgba(0, 0, 0, 0.08);
  --shadow-lg: 0 10px 20px rgba(0, 0, 0, 0.12);
}
```

### Breakpoint Tokens

```css
:root {
  --bp-xs: 480px; /* Small Mobile */
  --bp-sm: 640px; /* Mobile */
  --bp-md: 768px; /* Tablet */
  --bp-lg: 1024px; /* Laptop */
  --bp-xl: 1280px; /* Desktop */
  --bp-2xl: 1536px; /* Large Desktop */
  --bp-3xl: 1920px; /* Ultra-wide Monitor */
}
```

### Container Tokens

```css
:root {
  --container-xs: 480px;
  --container-sm: 640px;
  --container-md: 768px;
  --container-lg: 1024px;
  --container-xl: 1280px;
  --container-2xl: 1440px;
  --container-full: 100%;
}
```

### Z-Index Tokens

```css
:root {
  --z-dropdown: 100;
  --z-sticky: 200;
  --z-modal: 500;
  --z-toast: 700;
  --z-tooltip: 900;
}
```

### Motion Tokens

```css
:root {
  --duration-fast: 150ms;
  --duration-normal: 250ms;
  --duration-slow: 400ms;

  --ease-default: ease;
  --ease-in-out: ease-in-out;
}
```

### Size Tokens

```css
:root {
  --size-xs: 24px;
  --size-sm: 32px;
  --size-md: 40px;
  --size-lg: 48px;
  --size-xl: 64px;
}
```

### Gap Tokens

```css
:root {
  --gap-xs: 4px;
  --gap-sm: 8px;
  --gap-md: 16px;
  --gap-lg: 24px;
  --gap-xl: 32px;
  --gap-2xl: 48px;
  --gap-3xl: 64px;
  --gap-4xl: 80px;
}
```

### Accessibility Tokens

```css
:root {
  /* Focus Tokens */
  --focus-ring-width: 2px;
  --focus-ring-offset: 2px;
  --focus-ring-color: #2563eb;
  --focus-ring-shadow: 0 0 0 2px #ffffff, 0 0 0 4px #2563eb;

  /* Disable Tokens */
  --opacity-disabled: 0.5;
  --color-disabled-bg: #e5e7eb;
  --color-disabled-text: #9ca3af;
  --color-disabled-border: #aaaaaa;
}
```

---

## 📌 Component System

A component system organizes reusable UI building blocks into structured categories for scalable application development.

### Component Hierarchy

```txt
Primitive Components
  ↓
Common UI Components
  ↓
Complex Components
  ↓
Patterns
  ↓
Pages
```

| Level              | Purpose                     |
| ------------------ | --------------------------- |
| Primitive          | Small reusable foundations  |
| Common Components  | Everyday UI building blocks |
| Complex Components | Advanced reusable sections  |
| Patterns           | Reusable workflows/layouts  |

---

## 📌 Primitive Components

Low-level reusable foundation components.

| Component | Usage                |
| --------- | -------------------- |
| Text      | Typography rendering |
| Icon      | Visual symbols       |
| Button    | Actions              |
| Input     | User input           |
| Avatar    | User profile         |
| Badge     | Status labels        |
| Spinner   | Loading indicator    |

---

### Common UI Components

Frequently used application UI components.

| Category     | Components               |
| ------------ | ------------------------ |
| Forms        | Input, Select, Checkbox  |
| Navigation   | Navbar, Tabs, Breadcrumb |
| Feedback     | Alert, Toast, Progress   |
| Data Display | Card, Table, List        |
| Overlay      | Modal, Drawer, Tooltip   |
| Layout       | Grid, Stack, Container   |

| Form Components | Usage         |
| --------------- | ------------- |
| Input           | Text input    |
| Select          | Dropdown      |
| Checkbox        | Multi-select  |
| Radio           | Single select |
| Switch          | Toggle state  |
| Textarea        | Long text     |

| Navigation Components | Usage             |
| --------------------- | ----------------- |
| Navbar                | Top navigation    |
| Sidebar               | App navigation    |
| Tabs                  | Content switching |
| Breadcrumb            | Page hierarchy    |
| Pagination            | Page navigation   |

| Feedback Components | Usage               |
| ------------------- | ------------------- |
| Alert               | Important messages  |
| Toast               | Temporary messages  |
| Spinner             | Loading UI          |
| Skeleton            | Loading placeholder |
| Progress            | Task progress       |

| Data Display Components | Usage             |
| ----------------------- | ----------------- |
| Card                    | Content grouping  |
| Table                   | Structured data   |
| List                    | Repeated content  |
| Avatar                  | User display      |
| Badge                   | Status indicators |

| Overlay Components | Usage            |
| ------------------ | ---------------- |
| Modal              | Dialog window    |
| Drawer             | Side panel       |
| Tooltip            | Hover info       |
| Dropdown           | Menu options     |
| Popover            | Floating content |

---

Reusable layout structure components.

| Layout Components | Usage            |
| ----------------- | ---------------- |
| Container         | Width control    |
| Grid              | Page layout      |
| Flex              | Alignment        |
| Stack             | Vertical spacing |
| Section           | Page grouping    |

```tsx
<Stack gap="md">
  <Input />
  <Button />
</Stack>
```

---

### Complex Components

Advanced reusable application components.

| Component        | Usage            |
| ---------------- | ---------------- |
| Data Table       | ERP/admin data   |
| Date Picker      | Date selection   |
| File Upload      | Upload system    |
| Multi-step Form  | Workflow forms   |
| Dashboard Widget | Analytics blocks |
| Rich Text Editor | Content editing  |

```tsx
<DataTable sortable selectable pagination />
```

### Component Variants

Reusable style variations.

```tsx
<Button variant="primary" />
<Button variant="secondary" />
<Button size="lg" />
```

| Variant   | Usage              |
| --------- | ------------------ |
| Primary   | Main actions       |
| Secondary | Supporting actions |
| Outline   | Low emphasis       |
| Ghost     | Minimal UI         |
| Danger    | Destructive action |

### Component States

| State    | Purpose              |
| -------- | -------------------- |
| Default  | Normal state         |
| Hover    | Mouse interaction    |
| Focus    | Keyboard interaction |
| Active   | Pressed state        |
| Disabled | Non-interactive      |
| Loading  | Async action         |
| Error    | Validation state     |

```tsx
<Button loading disabled>
  Saving...
</Button>
```

---

### Component Composition

Build complex UI using reusable smaller components.

```tsx
<Card>
  <CardHeader />
  <CardContent />
  <CardFooter />
</Card>
```

### Component Anatomy

Internal structure of a component.

```txt
Button
├── Container
├── Icon
├── Label
└── Loading State
```

### Accessibility in Components

| Area             | Requirement      |
| ---------------- | ---------------- |
| Keyboard Support | Focus navigation |
| ARIA Labels      | Screen readers   |
| Focus Ring       | Visible focus    |
| Contrast         | Readable UI      |

### Token Usage in Components

```css
.button {
  background: var(--color-primary);
  padding: var(--space-2) var(--space-4);
  border-radius: var(--radius-md);
  gap: var(--gap-sm);
}
```

### Folder Structure

```txt
components/
├── primitives/     -> Small reusable foundation components
├── layouts/        -> Reusable layout structures
├── forms/          -> User input & form handling
├── feedback/       -> User feedback & states
├── navigation/     -> App/page navigation UI
├── data-display/   -> Data rendering components
├── overlays/       -> Floating/overlay UI
└── complex/        -> Advanced business components
```

| Folder          | Common Examples                                                                  |
| --------------- | -------------------------------------------------------------------------------- |
| `primitives/`   | Button, Text, Icon, Link, Spinner, Divider, Avatar, Badge                        |
| `layouts/`      | Container, Grid, Flex, Stack, Section, PageLayout, AppShell                      |
| `forms/`        | Input, Select, Checkbox, Radio, Switch, Textarea, DatePicker, FileUpload         |
| `feedback/`     | Alert, Toast, Snackbar, Progress, Skeleton, EmptyState, Loader                   |
| `navigation/`   | Navbar, Sidebar, Tabs, Breadcrumb, Pagination, Menu, Stepper                     |
| `data-display/` | Card, Table, List, Accordion, Timeline, AvatarGroup, Badge                       |
| `overlays/`     | Modal, Drawer, Tooltip, Dropdown, Popover, ContextMenu                           |
| `complex/`      | DataTable, RichTextEditor, Calendar, KanbanBoard, DashboardWidget, MultiStepForm |

- Build primitives first
- Keep components reusable
- Prefer composition over huge props
- Standardize variants/states
- Keep APIs predictable
- Use semantic tokens
- Support accessibility by default
- Avoid duplicated UI logic

---

## 📌 Component Variants

Component variants provide reusable visual styles and behavior variations for the same component.

| Variant Type         | Standard Values                                   |
| -------------------- | ------------------------------------------------- |
| Visual Variants      | Default, Primary, Secondary, Outline, Ghost, Link |
| Size Variants        | xs, sm, md, lg, xl                                |
| State Variants       | Loading, Disabled, Error, Success, Active         |
| Shape Variants       | Rounded, Pill, Square                             |
| Theme Variants       | Light, Dark                                       |
| Intent Variants      | Success, Warning, Danger, Info                    |
| Orientation Variants | Horizontal, Vertical                              |
| Surface Variants     | Filled, Soft, Transparent                         |
| Border Variants      | Solid, Dashed, None                               |
| Layout Variants      | Inline, Block, Full Width                         |

### Variant Architecture

```txt
Component
  ├── Variant
  ├── Size
  ├── State
  └── Theme
```

### Common Variant Patterns

| Component  | Common Variants                                  |
| ---------- | ------------------------------------------------ |
| Button     | Primary, Secondary, Outline, Ghost, Link, Danger |
| Input      | Default, Error, Disabled, Readonly               |
| Select     | Default, Searchable, MultiSelect                 |
| Checkbox   | Default, Checked, Indeterminate, Disabled        |
| Radio      | Default, Checked, Disabled                       |
| Switch     | Default, Checked, Disabled                       |
| Badge      | Solid, Soft, Outline                             |
| Alert      | Success, Warning, Danger, Info                   |
| Toast      | Success, Warning, Danger, Info                   |
| Card       | Flat, Elevated, Outlined                         |
| Modal      | Centered, Fullscreen, Drawer                     |
| Drawer     | Left, Right, Top, Bottom                         |
| Tooltip    | Top, Bottom, Left, Right                         |
| Tabs       | Underline, Pills, Segmented                      |
| Avatar     | Circle, Rounded, Square                          |
| Table      | Striped, Bordered, Compact                       |
| Pagination | Default, Compact                                 |
| Navbar     | Fixed, Sticky, Transparent                       |
| Sidebar    | Expanded, Collapsed                              |
| Dropdown   | Default, Searchable                              |
| Progress   | Linear, Circular                                 |
| Skeleton   | Text, Card, Avatar                               |
| Spinner    | Small, Medium, Large                             |
| Accordion  | Single, Multiple                                 |
| Breadcrumb | Default, Compact                                 |
| Stepper    | Horizontal, Vertical                             |
| EmptyState | Default, Illustrated                             |
| Banner     | Info, Warning, Success, Danger                   |
| Chip/Tag   | Filled, Outline, Closable                        |
| Text       | Heading, Body, Caption, Label                    |
| List       | Ordered, Unordered, Divided                      |
| Divider    | Horizontal, Vertical                             |
| Calendar   | SingleDate, Range                                |
| DataTable  | Sortable, Selectable, Expandable                 |
| FileUpload | DragDrop, ButtonUpload                           |
| Menu       | Context, Dropdown                                |
| Popover    | Click, Hover                                     |
| Timeline   | Vertical, Horizontal                             |

- Keep variant names semantic
- Reuse variants across components
- Avoid too many custom variants
- Keep APIs predictable
- Use consistent naming conventions
- Separate variants from business logic
- Standardize sizes system-wide

---

## 📌 State Design

State design defines how UI components visually and behaviorally respond to user interaction, data changes, and system events.

| State Type          | Common States                     |
| ------------------- | --------------------------------- |
| Interaction States  | Default, Hover, Focus, Active     |
| Feedback States     | Success, Warning, Error, Info     |
| Data States         | Loading, Empty, Loaded            |
| Availability States | Disabled, Readonly                |
| Selection States    | Selected, Checked                 |
| Visibility States   | Open, Closed, Expanded, Collapsed |
| Validation States   | Valid, Invalid                    |
| Async States        | Loading, Success, Failed          |

### Data States

| State   | Usage              |
| ------- | ------------------ |
| Loading | Data fetching      |
| Empty   | No available data  |
| Loaded  | Successful content |
| Error   | Failed request     |

### Feedback States

| State        | Common Color  |
| ------------ | ------------- |
| Success      | Green         |
| Warning      | Yellow/Orange |
| Danger/Error | Red           |
| Info         | Blue          |

### State Flow

```txt
Idle
  ↓
Loading
  ↓
Success / Error
```

### Input States

```tsx
<Input error />
<Input disabled />
<Input readonly />
```

### CSS State

```css
.button:hover {
  opacity: 0.9;
}

.button:focus-visible {
  outline: 2px solid var(--color-primary);
}

.button:disabled {
  opacity: 0.5;
}
```

### Accessibility States

| State    | Accessibility Requirement |
| -------- | ------------------------- |
| Focus    | Visible keyboard focus    |
| Disabled | Proper disabled semantics |
| Error    | Screen reader support     |
| Loading  | Announce async updates    |

### State Patterns

| Component | Common States            |
| --------- | ------------------------ |
| Button    | Hover, Loading, Disabled |
| Input     | Focus, Error, Disabled   |
| Modal     | Open, Closed             |
| Accordion | Expanded, Collapsed      |
| Table     | Loading, Empty, Selected |
| Tabs      | Active, Disabled         |

```css
:root {
  --opacity-disabled: 0.5;

  --color-success: #16a34a;
  --color-warning: #f59e0b;
  --color-danger: #dc2626;

  --focus-ring-color: #2563eb;
}
```

### Common State UI Patterns

| Pattern           | Example                 |
| ----------------- | ----------------------- |
| Skeleton Loading  | Content placeholders    |
| Inline Validation | Form errors             |
| Toast Feedback    | Success messages        |
| Retry State       | Failed request handling |
| Empty Placeholder | No results              |

- Always design loading & empty states
- Keep state behavior consistent
- Use semantic colors for feedback
- Maintain visible focus states
- Avoid relying only on color changes
- Provide clear error messages
- Support keyboard interactions
- Keep async feedback responsive

| Product       | State Usage            |
| ------------- | ---------------------- |
| ERP Dashboard | Loading/data states    |
| SaaS Platform | Form validation        |
| E-commerce    | Cart/loading states    |
| Admin Panel   | Table selection/errors |

---

## 📌 Icons System

An icons system provides consistent visual symbols for actions, navigation, feedback, and status across the UI.

| Icon Type           | Common Examples                   |
| ------------------- | --------------------------------- |
| Action Icons        | Add, Edit, Delete, Save, Search   |
| Navigation Icons    | Menu, Arrow, Chevron, Back, Close |
| Feedback Icons      | Success, Warning, Error, Info     |
| File Icons          | PDF, Image, Video, Folder         |
| User Icons          | User, Team, Avatar, Profile       |
| Commerce Icons      | Cart, Payment, Wishlist           |
| Communication Icons | Mail, Bell, Chat, Phone           |
| System Icons        | Settings, Dashboard, Filter       |

| Icon Variants Type | Standard Values          |
| ------------------ | ------------------------ |
| Size Variants      | xs, sm, md, lg, xl       |
| Style Variants     | Outline, Filled, Duotone |
| Shape Variants     | Rounded, Square          |
| State Variants     | Active, Disabled         |
| Theme Variants     | Light, Dark              |

### Icon Accessibility

| Area             | Requirement              | Example                   |
| ---------------- | ------------------------ | ------------------------- |
| Decorative Icons | Hide from screen readers | `aria-hidden="true"`      |
| Action Icons     | Add accessible label     | `aria-label="Close"`      |
| Contrast         | Visible on all surfaces  | Accessible color contrast |
| Touch Area       | Minimum clickable size   | `44px+` touch target      |

### Common Icon Libraries

| Library          | Usage                     | Free/Paid   | Collection | Variant Types                             |
| ---------------- | ------------------------- | ----------- | ---------- | ----------------------------------------- |
| Lucide           | Modern apps               | Free        | 1K+        | Outline                                   |
| Heroicons        | Tailwind ecosystem        | Free        | 300+       | Outline, Solid                            |
| Material Icons   | Google ecosystem          | Free        | 2K+        | Filled, Outlined, Rounded, Sharp          |
| Font Awesome     | Large icon ecosystem      | Free + Paid | 20K+       | Solid, Regular, Light, Duotone, Brands    |
| Tabler Icons     | Minimal UI                | Free        | 5K+        | Outline                                   |
| Phosphor Icons   | Flexible styles           | Free        | 9K+        | Thin, Light, Regular, Bold, Fill, Duotone |
| Remix Icon       | Clean modern UI           | Free        | 2K+        | Line, Fill                                |
| Feather Icons    | Lightweight outline icons | Free        | 280+       | Outline                                   |
| Bootstrap Icons  | Bootstrap ecosystem       | Free        | 2K+        | Filled, Outline                           |
| Radix Icons      | Headless/Radix UI         | Free        | 300+       | Outline                                   |
| Ant Design Icons | Enterprise dashboards     | Free        | 800+       | Filled, Outlined, TwoTone                 |
| Carbon Icons     | IBM Carbon system         | Free        | 2K+        | Filled, Outline                           |
| Fluent UI Icons  | Microsoft ecosystem       | Free        | 1K+        | Regular, Filled                           |
| Ionicons         | Mobile/hybrid apps        | Free        | 1K+        | Outline, Sharp, Filled                    |
| Eva Icons        | Dashboard/admin UI        | Free        | 480+       | Outline, Fill                             |
| Unicons          | General-purpose UI        | Free + Paid | 4K+        | Line, Solid, Monochrome                   |
| Line Awesome     | Font Awesome alternative  | Free        | 1K+        | Solid, Regular                            |
| Boxicons         | Clean modern apps         | Free        | 1.5K+      | Regular, Solid, Logos                     |
| SVG Repo         | Huge SVG collection       | Free + Paid | 500K+      | Mixed Styles                              |
| Iconoir          | Minimal modern icons      | Free        | 1K+        | Outline                                   |

### Icon Folder Structure

```txt
icons/
├── actions/
├── navigation/
├── feedback/
├── commerce/
├── files/
├── users/
└── system/
```

- Use a single icon library
- Keep icon sizes consistent
- Maintain consistent stroke width
- Use semantic icon naming
- Avoid mixing icon styles
- Keep accessible labels for actions
- Use tokens for icon sizing/colors
- Prefer SVG icons over images/fonts

---

## 📌 Elevation & Shadows

Elevation and shadow systems create visual depth, hierarchy, focus, and layered UI structure.

| Elevation Level | Common Usage      |
| --------------- | ----------------- |
| None            | Flat surfaces     |
| xs              | Inputs/dividers   |
| sm              | Cards/buttons     |
| md              | Dropdowns         |
| lg              | Sticky elements   |
| xl              | Modals/dialogs    |
| 2xl             | Floating overlays |

### Elevation Tokens

```css
:root {
  --shadow-none: none;
  --shadow-xs: 0 1px 1px rgba(0, 0, 0, 0.04);
  --shadow-sm: 0 1px 2px rgba(0, 0, 0, 0.06);
  --shadow-md: 0 4px 8px rgba(0, 0, 0, 0.08);
  --shadow-lg: 0 10px 24px rgba(0, 0, 0, 0.12);
  --shadow-xl: 0 20px 40px rgba(0, 0, 0, 0.16);
  --shadow-2xl: 0 30px 60px rgba(0, 0, 0, 0.24);
}
```

| Shadow Type     | Usage           |
| --------------- | --------------- |
| Soft Shadow     | Modern cards    |
| Hard Shadow     | Strong emphasis |
| Inner Shadow    | Inputs/inset UI |
| Floating Shadow | Modals/popovers |
| Glow Shadow     | Focus/highlight |

### Layer Hierarchy Example

```txt
Base Surface
  ↓
Cards
  ↓
Dropdowns
  ↓
Sticky Elements
  ↓
Modals
  ↓
Tooltips
```

```css
/* Inner Shadow Example */
.input {
  box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.06);
}
```

```css
/* Glow Shadow Example */
.button:focus-visible {
  box-shadow: 0 0 0 4px rgba(37, 99, 235, 0.2);
}
```

```css
/* Dark Theme Shadow Example */
[data-theme="dark"] {
  --shadow-md: 0 4px 12px rgba(0, 0, 0, 0.4);
}
```

| Component     | Elevation Patterns |
| ------------- | ------------------ |
| Button        | xs/sm              |
| Card          | sm/md              |
| Dropdown      | md                 |
| Sticky Navbar | lg                 |
| Drawer        | xl                 |
| Modal         | xl/2xl             |
| Tooltip       | 2xl                |

- Use limited shadow levels
- Keep shadows subtle and consistent
- Increase elevation only when needed
- Maintain clear layer hierarchy
- Prefer softer modern shadows
- Avoid excessive blur/spread
- Adjust shadows for dark mode
- Combine elevation with spacing/radius

---

## 📌 Motion & Animation

Motion and animation improve interaction feedback, transitions, navigation flow, and perceived responsiveness.

| Motion Type               | Common Usage           | Examples                        |
| ------------------------- | ---------------------- | ------------------------------- |
| Hover Animation           | Buttons/cards          | Scale, Elevation, Color Change  |
| Transition Animation      | UI state changes       | Background, Border, Opacity     |
| Loading Animation         | Spinners/skeletons     | Spinner, Pulse, Progress Bar    |
| Entrance Animation        | Modals/drawers         | Fade In, Slide In, Scale In     |
| Exit Animation            | Closing UI             | Fade Out, Slide Out             |
| Micro Interactions        | Small UI feedback      | Like Button, Toggle Switch      |
| Gesture Animation         | Mobile interactions    | Swipe, Pull-to-Refresh          |
| Scroll Animation          | Page transitions       | Fade on Scroll, Sticky Header   |
| Navigation Animation      | Route/page changes     | Page Slide, Fade Transition     |
| Feedback Animation        | Status/action feedback | Success Bounce, Error Shake     |
| Notification Animation    | Alerts/toasts          | Toast Slide, Snackbar Fade      |
| Attention Animation       | Important actions      | Pulse, Wiggle, Glow             |
| Expand/Collapse Animation | Accordions/dropdowns   | Height Expand, Collapse         |
| Drag Animation            | Drag/drop interfaces   | Reorder Lists, Kanban Drag      |
| Background Animation      | Decorative motion      | Gradient Shift, Particle Motion |

### Common Animation Types

| Animation      | Usage                |
| -------------- | -------------------- |
| Fade           | Modals/tooltips      |
| Scale          | Dropdowns/cards      |
| Slide          | Drawers/navigation   |
| Rotate         | Loaders/icons        |
| Bounce         | Notifications        |
| Skeleton Pulse | Loading placeholders |

```css
/* Fade Animation */
.modal {
  animation: fadeIn var(--duration-normal) var(--ease-out);
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }

  to {
    opacity: 1;
  }
}
```

```css
/* Scale Animation */
.dropdown {
  animation: scaleIn 150ms ease-out;
}

@keyframes scaleIn {
  from {
    opacity: 0;
    transform: scale(0.95);
  }

  to {
    opacity: 1;
    transform: scale(1);
  }
}
```

```css
/* Slide Animation */
.drawer {
  animation: slideIn 250ms ease-out;
}

@keyframes slideIn {
  from {
    transform: translateX(100%);
  }

  to {
    transform: translateX(0);
  }
}
```

```css
/* Spinner Animation */
.spinner {
  animation: spin 1s linear infinite;
}

@keyframes spin {
  to {
    transform: rotate(360deg);
  }
}
```

```css
/* Reduced Motion Support */
@media (prefers-reduced-motion: reduce) {
  * {
    animation: none !important;
    transition: none !important;
  }
}
```

| Component | Common Motion Patterns |
| --------- | ---------------------- |
| Button    | Hover/focus            |
| Card      | Elevation/scale        |
| Modal     | Fade/scale             |
| Drawer    | Slide                  |
| Tooltip   | Fade                   |
| Dropdown  | Scale/fade             |
| Skeleton  | Pulse                  |

### Motion Libraries

| Library       | Usage                | Example                              |
| ------------- | -------------------- | ------------------------------------ |
| Framer Motion | React animations     | Page transitions, modal animations   |
| GSAP          | Advanced animations  | Scroll animations, timelines         |
| Motion One    | Lightweight motion   | Simple fade/slide effects            |
| React Spring  | Physics-based motion | Drag interactions, natural UI motion |
| Anime.js      | Timeline animations  | SVG animations, sequencing           |
| Lottie        | JSON animations      | App onboarding, illustrations        |

- Keep animations subtle
- Use consistent durations/easing
- Prefer transitions over complex animations
- Avoid excessive motion
- Support reduced motion accessibility
- Use motion to improve UX clarity
- Maintain fast responsive interactions
- Animate opacity/transform for performance

| Product/System      | Motion Usage                                              |
| ------------------- | --------------------------------------------------------- |
| ERP Dashboard       | Hover elevation, sidebar collapse, table loading          |
| SaaS Platform       | Modal fade, drawer slide, page transitions                |
| E-commerce          | Product hover, add-to-cart feedback, image zoom           |
| Admin Panel         | Navigation transitions, tabs switch, loading states       |
| Mobile App          | Swipe gestures, pull-to-refresh, bottom sheet animations  |
| Analytics Dashboard | Chart transitions, counter animations, filter updates     |
| Chat/Messaging App  | Message slide, typing indicator, badge updates            |
| Landing Page        | Scroll reveal, hero animations, parallax effects          |
| Productivity App    | Drag-drop, task completion, Kanban movement               |
| Streaming App       | Progress animation, hover preview, fullscreen transitions |

---

## 📌 Accessibility (A11Y)

Accessibility ensures applications are usable for keyboard users, screen readers, assistive technologies, and all users.

| Accessibility Area    | Common Usage               | Real-World Examples                 |
| --------------------- | -------------------------- | ----------------------------------- |
| Keyboard Navigation   | Tab, Enter, Escape support | Modals, dropdowns, navigation menus |
| Focus Management      | Visible focus states       | Buttons, inputs, tabs               |
| Semantic HTML         | Proper HTML structure      | `<button>`, `<nav>`, `<main>`       |
| Screen Reader Support | ARIA labels/roles          | Icon buttons, dialogs, accordions   |
| Color Contrast        | Readable UI                | Buttons, alerts, text readability   |
| Touch Targets         | Accessible clickable areas | Mobile buttons, icon actions        |
| Reduced Motion        | Motion accessibility       | Disable heavy animations            |
| Form Accessibility    | Labels/errors/help text    | Login, checkout, registration forms |

### Keyboard Accessibility

| Key        | Usage                 |
| ---------- | --------------------- |
| Tab        | Navigate elements     |
| Enter      | Activate actions      |
| Space      | Toggle controls       |
| Escape     | Close overlays        |
| Arrow Keys | Menus/tabs/navigation |

### Focus State

```css
.button:focus-visible {
  outline: 2px solid var(--color-primary);
  outline-offset: 2px;
}
```

### ARIA Attributes

```tsx
<button aria-expanded="true">Menu</button>
<input aria-invalid="true" />
```

### Accessible State Patterns

| State      | Accessibility Requirement |
| ---------- | ------------------------- |
| Disabled   | Proper disabled semantics |
| Loading    | Announce async updates    |
| Error      | Screen reader feedback    |
| Modal Open | Trap keyboard focus       |

### Color Contrast

| Text Type     | Recommended Contrast |
| ------------- | -------------------- |
| Normal Text   | 4.5:1                |
| Large Text    | 3:1                  |
| UI Components | 3:1                  |

### Reduced Motion Support

```css
@media (prefers-reduced-motion: reduce) {
  * {
    animation: none !important;
    transition: none !important;
  }
}
```

### Touch Target Sizes

```css
.button {
  min-height: 44px;
  min-width: 44px;
}
```

| Size  | Usage                |
| ----- | -------------------- |
| 44px+ | Mobile accessibility |
| 48px+ | Touch-friendly UI    |

### Screen Reader Utilities

```css
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  overflow: hidden;
}
```

### Modal Accessibility

```tsx
<dialog
  aria-labelledby="modal-title"
>
```

### Common Accessibility Tools

| Tool         | Usage                 |
| ------------ | --------------------- |
| Lighthouse   | Accessibility audits  |
| axe DevTools | Accessibility testing |
| WAVE         | Accessibility checks  |
| NVDA         | Screen reader testing |
| VoiceOver    | macOS/iOS testing     |

### Common Accessibility Issues

| Problem             | Better Approach      |
| ------------------- | -------------------- |
| Div buttons         | Use `<button>`       |
| Missing labels      | Add `<label>`        |
| No focus styles     | Visible focus ring   |
| Color-only feedback | Add text/icons       |
| Tiny buttons        | Larger touch targets |

- Use semantic HTML first
- Always support keyboard navigation
- Maintain visible focus states
- Add labels for all form controls
- Ensure proper color contrast
- Support screen readers with ARIA
- Respect reduced motion settings
- Test accessibility regularly

---

## 📌 Documentation System

A documentation system explains component usage, behavior, standards, and implementation across the design system.

| Documentation Area | Common Content                |
| ------------------ | ----------------------------- |
| Component Docs     | Usage, props, variants        |
| Design Guidelines  | Spacing, typography, colors   |
| Accessibility Docs | Keyboard, ARIA, contrast      |
| Pattern Docs       | Forms, tables, workflows      |
| Token Docs         | Colors, spacing, shadows      |
| Layout Docs        | Grid, containers, breakpoints |
| Motion Docs        | Animation usage               |
| Contribution Docs  | Development standards         |

### Component Documentation

| Section       | Example                  |
| ------------- | ------------------------ |
| Usage         | When to use component    |
| Props/API     | Component configuration  |
| Variants      | Primary, Outline, Ghost  |
| States        | Loading, Disabled, Error |
| Accessibility | Keyboard/ARIA support    |
| Examples      | Real usage snippets      |

### Design Guidelines

| Guideline  | Example                 |
| ---------- | ----------------------- |
| Colors     | Semantic token usage    |
| Typography | Heading hierarchy       |
| Spacing    | Shared gap system       |
| Elevation  | Shadow scale            |
| Icons      | Consistent icon library |

### Pattern Documentation

| Pattern        | Example           |
| -------------- | ----------------- |
| Authentication | Login/signup flow |
| CRUD           | Data management   |
| Tables         | Sorting/filtering |
| Checkout       | Payment flow      |
| Dashboard      | Analytics layout  |

### Accessibility Documentation

| Area                  | Example            |
| --------------------- | ------------------ |
| Keyboard Navigation   | Tab/focus behavior |
| Screen Reader Support | ARIA labels        |
| Contrast Rules        | WCAG compliance    |
| Motion Accessibility  | Reduced motion     |

### Folder Structure Documentation

```txt
components/
tokens/
layouts/
patterns/
icons/
docs/
```

### Documentation Tools

| Tool       | Usage                   |
| ---------- | ----------------------- |
| Storybook  | Component documentation |
| Zeroheight | Design system docs      |
| Figma      | UI guidelines           |
| Notion     | Internal documentation  |
| Docusaurus | Developer docs          |

| Documentation Pages | Content           |
| ------------------- | ----------------- |
| Getting Started     | Setup/install     |
| Foundations         | Tokens/guidelines |
| Components          | APIs/examples     |
| Patterns            | Workflows/layouts |
| Accessibility       | A11Y standards    |
| Changelog           | Version updates   |

### Documentation Workflow

```txt
Design
  ↓
Component Build
  ↓
Usage Examples
  ↓
Accessibility Notes
  ↓
Testing
  ↓
Publish Docs
```

- Document all reusable components
- Include real usage examples
- Keep docs consistent and updated
- Add accessibility guidelines
- Show variants and states clearly
- Use interactive component previews
- Keep documentation searchable
- Document breaking changes properly

---

## 📌 Naming Conventions

Naming conventions create predictable, scalable, and maintainable design system architecture.

| Naming Area        | Common Convention       | Examples                            |
| ------------------ | ----------------------- | ----------------------------------- |
| Components         | PascalCase              | `Button`, `DataTable`, `PageLayout` |
| Files              | PascalCase / kebab-case | `Button.tsx`, `data-table.tsx`      |
| Folders            | kebab-case              | `data-display/`, `design-tokens/`   |
| CSS Classes        | kebab-case              | `.card-header`, `.sidebar-menu`     |
| Tokens             | Semantic naming         | `--color-primary`, `--gap-md`       |
| Hooks              | `use` prefix            | `useModal()`, `useTheme()`          |
| Constants          | UPPER_CASE              | `API_URL`, `MAX_FILE_SIZE`          |
| Boolean Variables  | `is/has` prefix         | `isLoading`, `hasError`             |
| Functions/Handlers | camelCase               | `handleSubmit()`, `fetchUsers()`    |
| Props              | camelCase               | `isOpen`, `onClose`                 |
| Variants           | Semantic naming         | `primary`, `outline`, `ghost`       |
| States             | Semantic naming         | `loading`, `disabled`, `active`     |

### Common Anti-Patterns

| Avoid        | Better          |
| ------------ | --------------- |
| `Btn`        | `Button`        |
| `tbl`        | `Table`         |
| `blueButton` | `PrimaryButton` |
| `data1`      | `userData`      |

- Use semantic naming
- Keep names predictable
- Avoid abbreviations
- Keep naming consistent system-wide
- Name by purpose, not appearance
- Use scalable folder/file naming
- Standardize variants and states
- Prefer readability over short names

---

## 📌 Folder Structures

A scalable folder structure improves maintainability, organization, and team collaboration in large frontend applications.

| Folder             | Common Usage             |
| ------------------ | ------------------------ |
| `app/` or `pages/` | Routing/pages            |
| `components/`      | Reusable UI components   |
| `layouts/`         | App/page layouts         |
| `features/`        | Feature-based modules    |
| `hooks/`           | Custom React hooks       |
| `services/`        | API/service logic        |
| `store/`           | Global state management  |
| `contexts/`        | React contexts           |
| `styles/`          | Global styles/themes     |
| `tokens/`          | Design tokens            |
| `icons/`           | SVG/icon system          |
| `utils/`           | Helper functions         |
| `types/`           | TypeScript types         |
| `constants/`       | Shared constants         |
| `assets/`          | Images/fonts/files       |
| `config/`          | App configuration        |
| `lib/`             | External libraries/setup |
| `tests/`           | Testing utilities        |

### Common Frontend Structure

```txt
src/
├── app/
├── components/
├── layouts/
├── features/
├── hooks/
├── services/
├── store/
├── contexts/
├── styles/
├── tokens/
├── icons/
├── utils/
├── types/
├── constants/
├── assets/
├── config/
├── lib/
└── tests/
```

### Component Structure

```txt
components/
├── primitives/
├── forms/
├── feedback/
├── navigation/
├── data-display/
├── overlays/
├── layouts/
└── complex/
```

### Feature-Based Structure

```txt
features/
├── auth/
├── dashboard/
├── users/
├── products/
└── settings/
```

### Feature Module Example

```txt
features/auth/
├── components/
├── hooks/
├── services/
├── store/
├── types/
└── utils/
```

### Design System Structure

```txt
design-system/
├── tokens/
├── components/
├── icons/
├── themes/
├── styles/
└── docs/
```

### Assets Structure

```txt
assets/
├── images/
├── icons/
├── fonts/
└── videos/
```

### Styles Structure

```txt
styles/
├── globals.css
├── themes/
├── utilities/
└── animations/
```

### API/Service Structure

```txt
services/
├── api/
├── auth/
├── users/
└── products/
```

### Testing Structure

```txt
tests/
├── unit/
├── integration/
├── e2e/
└── mocks/
```

- Organize by scalability
- Prefer feature-based architecture
- Keep reusable UI separated
- Avoid deeply nested folders
- Group related files together
- Standardize naming conventions
- Separate business logic from UI
- Keep shared utilities centralized

---

## 📌 Theming System

A theming system allows applications to support multiple visual styles using shared semantic design tokens.

| Theme Type          | Common Usage          |
| ------------------- | --------------------- |
| Light Theme         | Default UI            |
| Dark Theme          | Low-light interfaces  |
| Brand Theme         | Multi-brand products  |
| High Contrast Theme | Accessibility support |
| Custom Theme        | User personalization  |

### Theme Architecture

```txt
Primitive Tokens
  ↓
Semantic Tokens
  ↓
Theme Variables
  ↓
Components
```

### Theme Token

```css
:root {
  --color-primary: #2563eb;
  --color-surface: #ffffff;
  --color-text: #111827;
}
```

### Dark Theme

```css
[data-theme="dark"] {
  --color-surface: #111827;
  --color-text: #ffffff;
  --color-border: #374151;
}
```

### Brand Theme

```css
[data-theme="brand-green"] {
  --color-primary: #16a34a;
}
```

### Theme Switching

```tsx
document.documentElement.setAttribute("data-theme", "dark");
```

### Theme Folder Structure

```txt
themes/
├── light.css
├── dark.css
├── brand.css
└── index.ts
```

### Common Theme Areas

| Area       | Theme Usage        |
| ---------- | ------------------ |
| Colors     | Background/text    |
| Shadows    | Elevation styles   |
| Borders    | Surface separation |
| Typography | Readability        |
| Icons      | Contrast support   |

### Theme Modes

| Mode   | Usage               |
| ------ | ------------------- |
| Light  | Default UI          |
| Dark   | Night mode          |
| System | OS preference       |
| Custom | User-selected theme |

### System Theme

```css
@media (prefers-color-scheme: dark) {
  :root {
    --color-background: #111827;
  }
}
```

### Enterprise Theme

```txt
themes/
├── light/
├── dark/
├── enterprise-blue/
└── enterprise-green/
```

| Accessibility Themes | Purpose              |
| -------------------- | -------------------- |
| High Contrast        | Better readability   |
| Reduced Motion       | Motion accessibility |
| Dark Mode            | Eye comfort          |

```tsx
// Theme State
const [theme, setTheme] = useState("light");
```

| Theming Strategies | Usage                 |
| ------------------ | --------------------- |
| CSS Variables      | Most common           |
| Theme Provider     | React apps            |
| Tailwind Dark Mode | Utility-first theming |
| CSS-in-JS          | Dynamic themes        |

- Use semantic tokens for themes
- Avoid hardcoded component colors
- Support light & dark modes
- Keep themes centralized
- Maintain accessible contrast ratios
- Reuse shared token structure
- Support system theme preferences
- Keep component APIs theme-independent

---

## 📌 Dark Mode Strategy

Dark mode strategies provide scalable, maintainable, and accessible theme switching across applications.

| Strategy          | Common Usage           |
| ----------------- | ---------------------- |
| CSS Variables     | Design systems         |
| Theme Provider    | React applications     |
| Tailwind `dark:`  | Tailwind projects      |
| System Preference | OS theme sync          |
| Class-Based Theme | Manual theme switching |

### Recommended Strategy

```txt
Primitive Tokens
  ↓
Semantic Tokens
  ↓
Theme Variables
  ↓
Components
```

### CSS Variable Strategy

```css
:root {
  --color-background: #ffffff;
  --color-surface: #f8fafc;
  --color-text-primary: #111827;
}

[data-theme="dark"] {
  --color-background: #111827;
  --color-surface: #1f2937;
  --color-text-primary: #ffffff;
}
```

### Theme Switching

```tsx
document.documentElement.setAttribute("data-theme", "dark");
```

### Tailwind Dark Mode

```tsx
<div className="bg-white dark:bg-gray-900">
```

### React Theme Provider

```tsx
<ThemeProvider theme="dark">
  <App />
</ThemeProvider>
```

### System Preference Detection

```css
@media (prefers-color-scheme: dark) {
  :root {
    --color-background: #111827;
  }
}
```

### Common Dark Mode Areas

| Area        | Dark Mode Usage     |
| ----------- | ------------------- |
| Backgrounds | Dark surfaces       |
| Text        | High readability    |
| Borders     | Subtle separation   |
| Shadows     | Softer elevation    |
| Icons       | Accessible contrast |

### Theme Folder Structure

```txt
themes/
├── light.css
├── dark.css
└── theme-provider.tsx
```

### Accessibility in Dark Mode

| Area         | Requirement            |
| ------------ | ---------------------- |
| Contrast     | WCAG readability       |
| Focus States | Visible focus ring     |
| Motion       | Reduced motion support |
| Icons        | Clear visibility       |

### Common Dark Mode Problems

| Problem           | Better Approach        |
| ----------------- | ---------------------- |
| Pure black UI     | Use dark gray surfaces |
| Low contrast text | Accessible text colors |
| Hardcoded colors  | Semantic tokens        |
| Bright shadows    | Softer dark shadows    |

- Use semantic tokens
- Avoid hardcoded component colors
- Prefer dark gray over pure black
- Maintain accessible contrast ratios
- Support system preferences
- Keep shadows softer in dark mode
- Reuse same component APIs
- Test all states in dark mode

| Product       | Dark Mode Usage        |
| ------------- | ---------------------- |
| ERP Dashboard | Dark analytics UI      |
| SaaS Platform | Theme switching        |
| Admin Panel   | Low-light dashboards   |
| Mobile App    | System-based dark mode |

---

## 📌 Design System Workflow

A design system workflow defines the process for creating, maintaining, documenting, and scaling reusable UI systems.

| Stage             | Common Tasks                |
| ----------------- | --------------------------- |
| Foundations       | Colors, typography, spacing |
| Tokens            | Primitive & semantic tokens |
| Components        | Build reusable UI           |
| Variants & States | Sizes, themes, interactions |
| Accessibility     | Keyboard, ARIA, contrast    |
| Documentation     | Usage/examples              |
| Testing           | UI & accessibility testing  |
| Release           | Publish/versioning          |
| Maintenance       | Updates/refactoring         |

```txt
Research
  ↓
Foundations
  ↓
Tokens
  ↓
Components
  ↓
Patterns
  ↓
Documentation
  ↓
Testing
  ↓
Release
  ↓
Maintenance
```

1. Foundations

| Area       | Examples         |
| ---------- | ---------------- |
| Colors     | Brand palette    |
| Typography | Font scale       |
| Spacing    | Gap system       |
| Layout     | Grid/container   |
| Motion     | Animation tokens |

2.  Token Creation
3.  Build Primitive Components
4.  Build Common Components
5.  Add Variants & States
6.  Accessibility Review
7.  Documentation
8.  Testing

| Testing Type          | Usage             |
| --------------------- | ----------------- |
| Unit Testing          | Component logic   |
| Visual Testing        | UI consistency    |
| Accessibility Testing | A11Y validation   |
| Snapshot Testing      | Regression checks |

9.  Release & Versioning

### Design System Team Workflow

| Role                | Responsibility     |
| ------------------- | ------------------ |
| Designers           | Foundations/tokens |
| Frontend Developers | Components/system  |
| QA                  | Testing            |
| Accessibility Team  | A11Y validation    |

| Common Tools  | Usage            |
| ------------- | ---------------- |
| Figma         | UI design        |
| Storybook     | Component docs   |
| Chromatic     | Visual testing   |
| Tokens Studio | Token management |
| GitHub        | Version control  |

### Enterprise Workflow

```txt
Figma Design
  ↓
Token Sync
  ↓
Component Development
  ↓
Storybook Docs
  ↓
Testing
  ↓
NPM Package Release
```

- Build foundations before components
- Keep tokens centralized
- Reuse primitives everywhere
- Document all reusable components
- Validate accessibility early
- Maintain consistent naming
- Keep workflows automated
- Version design system changes properly

### Design System Architecture

| Layer                | Common Examples             |
| -------------------- | --------------------------- |
| Foundations          | Colors, typography, spacing |
| Tokens               | Semantic design values      |
| Primitive Components | Button, Input, Icon         |
| Common Components    | Card, Modal, Tabs           |
| Complex Components   | DataTable, Calendar         |
| Patterns             | Forms, dashboards           |
| Pages                | Full application screens    |

---

## 📌 Design Tools

Design tools help teams create, document, prototype, test, and maintain scalable design systems and frontend workflows.

| Tool          | Common Usage                     | Type               |
| ------------- | -------------------------------- | ------------------ |
| Figma         | UI/UX design, design systems     | Design Tool        |
| FigJam        | Wireframes, flows, brainstorming | Collaboration Tool |
| Storybook     | Component documentation          | Frontend Tool      |
| Chromatic     | Visual regression testing        | Testing Tool       |
| Zeroheight    | Design system documentation      | Documentation Tool |
| Tokens Studio | Design token management          | Token Tool         |
| Adobe XD      | UI/UX design                     | Design Tool        |
| Sketch        | macOS UI design                  | Design Tool        |
| InVision      | Interactive prototypes           | Prototype Tool     |
| Framer        | Interactive design/prototyping   | Motion Tool        |
| Zeplin        | Design handoff                   | Collaboration Tool |
| Miro          | Whiteboarding/workflows          | Collaboration Tool |
| Notion        | Documentation/project management | Documentation Tool |
| Docusaurus    | Developer documentation          | Docs Tool          |
| LottieFiles   | JSON animations                  | Animation Tool     |

### Common Workflow

```txt
Research
  ↓
Wireframes
  ↓
UI Design
  ↓
Prototype
  ↓
Design System
  ↓
Development
  ↓
Testing
```

### Figma Usage

| Feature     | Example Usage     |
| ----------- | ----------------- |
| Components  | Reusable UI       |
| Variants    | Button states     |
| Auto Layout | Responsive design |
| Variables   | Design tokens     |
| Prototypes  | User flows        |

### Storybook Usage

```tsx
export const Primary = {
  args: {
    variant: "primary",
  },
};
```

| Storybook Feature | Usage             |
| ----------------- | ----------------- |
| Component Preview | Isolated UI       |
| Controls          | Interactive props |
| Docs              | Component usage   |
| Accessibility     | A11Y testing      |

### Tokens Studio Usage

```txt
Colors
Typography
Spacing
Radius
Shadows
```

### Chromatic Usage

| Feature         | Usage              |
| --------------- | ------------------ |
| Visual Testing  | UI regression      |
| Snapshot Review | Design consistency |
| Review Workflow | Team collaboration |

### Framer Usage

| Feature       | Usage             |
| ------------- | ----------------- |
| Motion Design | UI animations     |
| Prototyping   | Interactive flows |
| Landing Pages | Marketing UI      |

### Zeroheight Usage

| Feature       | Usage                |
| ------------- | -------------------- |
| Design Docs   | System documentation |
| Guidelines    | Brand rules          |
| Collaboration | Design/dev sync      |

### Common Tool Categories

| Category      | Common Tools      |
| ------------- | ----------------- |
| UI Design     | Figma, Sketch     |
| Documentation | Storybook, Notion |
| Testing       | Chromatic         |
| Prototyping   | Framer, InVision  |
| Collaboration | FigJam, Miro      |
| Tokens        | Tokens Studio     |

### Design System Workflow

```txt
Figma
  ↓
Tokens Studio
  ↓
Frontend Components
  ↓
Storybook
  ↓
Chromatic Testing
```

- Centralize design system files
- Use shared component libraries
- Sync design tokens with code
- Keep documentation updated
- Use visual regression testing
- Standardize collaboration workflows
- Reuse shared UI patterns
- Maintain developer/designer consistency

---

## 📌 UI Patterns

UI patterns are reusable user interface structures and workflows used across applications for consistent user experience.

| Pattern Type        | Common Examples                                                        |
| ------------------- | ---------------------------------------------------------------------- |
| Authentication      | Login, Signup, Forgot Password, OTP Verification, Reset Password       |
| Navigation          | Navbar, Sidebar, Tabs, Breadcrumb, Pagination, Menu, Bottom Navigation |
| CRUD                | Create, Read, Update, Delete, Bulk Actions                             |
| Forms               | Validation, Multi-step Form, Auto Save, Floating Labels                |
| Dashboard           | Analytics Cards, Charts, Widgets, Filters, Sidebar Layout              |
| Search              | Global Search, Filters, Sorting, Search Suggestions                    |
| Tables              | Sorting, Filtering, Pagination, Row Selection, Expandable Rows         |
| Feedback            | Toast, Alert, Snackbar, Progress Bar, Success Message                  |
| Overlay             | Modal, Drawer, Tooltip, Popover, Dropdown, Context Menu                |
| E-commerce          | Product Card, Wishlist, Cart, Checkout, Order Tracking                 |
| Empty States        | No Data UI, No Results, No Notifications                               |
| Loading States      | Skeleton Loader, Spinner, Progress Indicator, Retry State              |
| Mobile Patterns     | Bottom Sheet, Swipe Actions, Pull to Refresh                           |
| Enterprise Patterns | DataTable, Kanban Board, Role Permissions, Audit Logs                  |

- Reuse proven UI patterns
- Keep interactions predictable
- Standardize layouts and workflows
- Keep patterns responsive
- Reduce unnecessary complexity
- Prioritize user clarity

---

## 📌 Testing Design Systems

Testing design systems ensures UI consistency, accessibility, responsiveness, and component reliability across applications.

| Testing Type          | Common Examples                |
| --------------------- | ------------------------------ |
| Unit Testing          | Component logic, props, states |
| Integration Testing   | Forms, workflows, interactions |
| Visual Testing        | UI consistency, regression     |
| Accessibility Testing | Keyboard, ARIA, contrast       |
| Snapshot Testing      | UI output comparison           |
| E2E Testing           | Full user workflows            |
| Responsive Testing    | Mobile/tablet/desktop          |
| Cross-Browser Testing | Chrome, Firefox, Safari        |

### Unit Testing

```tsx
render(<Button />);
```

| Common Checks    |
| ---------------- |
| Props rendering  |
| Variant behavior |
| State handling   |
| Event handling   |

### Integration Testing

```txt
Form Submission
Modal Open/Close
Search Workflow
```

### Visual Testing

| Common Checks        |
| -------------------- |
| Layout consistency   |
| Spacing issues       |
| Broken UI            |
| Regression detection |

### Accessibility Testing

| Common Checks       |
| ------------------- |
| Keyboard navigation |
| Focus visibility    |
| ARIA labels         |
| Contrast ratio      |

### Snapshot Testing

```tsx
expect(container).toMatchSnapshot();
```

### E2E Testing

```txt
Login Flow
Checkout Flow
Dashboard Workflow
```

### Common Testing Tools

| Tool                  | Usage                  |
| --------------------- | ---------------------- |
| Jest                  | Unit testing           |
| Vitest                | Fast unit testing      |
| React Testing Library | Component testing      |
| Cypress               | E2E testing            |
| Playwright            | Cross-browser E2E      |
| Chromatic             | Visual regression      |
| Storybook             | Component testing/docs |
| axe DevTools          | Accessibility testing  |

### Storybook Testing

| Feature             | Usage               |
| ------------------- | ------------------- |
| Component Preview   | UI isolation        |
| Controls            | Interactive testing |
| Accessibility Addon | A11Y validation     |

### Responsive Testing

| Device  | Common Testing  |
| ------- | --------------- |
| Mobile  | Layout/touch UI |
| Tablet  | Responsive grid |
| Desktop | Full layouts    |

```txt
Build Component
  ↓
Unit Test
  ↓
Visual Test
  ↓
Accessibility Test
  ↓
E2E Test
```

- Test all variants and states
- Validate accessibility early
- Use visual regression testing
- Keep tests reusable
- Test responsive layouts
- Cover critical user workflows
- Automate testing pipelines
- Test components in isolation

---

## 📌 Scalability & Maintainability

Scalable and maintainable design systems keep UI consistent, reusable, and easy to manage as applications grow.

| Area             | Common Practices                |
| ---------------- | ------------------------------- |
| Tokens           | Centralized semantic tokens     |
| Components       | Reusable composable UI          |
| Folder Structure | Organized scalable architecture |
| Naming           | Consistent conventions          |
| Theming          | Shared theme system             |
| Documentation    | Updated usage guidelines        |
| Accessibility    | Built-in A11Y support           |
| Testing          | Automated UI validation         |

---

## 📌 Common Mistakes

Common design system mistakes reduce scalability, consistency, accessibility, and maintainability.

| Mistake                              | Better Approach               |
| ------------------------------------ | ----------------------------- |
| Hardcoded colors/styles              | Use semantic tokens           |
| Duplicate components                 | Reuse shared components       |
| Large monolithic components          | Split into smaller components |
| Inconsistent spacing                 | Shared spacing system         |
| Too many variants                    | Keep variants standardized    |
| Mixing icon libraries                | Use one icon system           |
| No accessibility support             | Build A11Y by default         |
| Deep folder nesting                  | Keep structure simple         |
| Poor naming conventions              | Use consistent naming         |
| No documentation                     | Maintain component docs       |
| Ignoring dark mode                   | Use theme tokens              |
| No loading/empty states              | Design all UI states          |
| Overusing animations                 | Keep motion subtle            |
| Business logic inside UI             | Separate concerns             |
| Using primitives directly everywhere | Create reusable patterns      |
| No responsive testing                | Test mobile/tablet/desktop    |
| Inconsistent component APIs          | Standardize props             |
| No versioning strategy               | Use semantic versioning       |
| Skipping visual testing              | Add regression testing        |
| Overengineering early                | Start simple and scale        |

```css
/* ❌ Hardcoded styling */
.button {
  background: blue;
}

/* ✅ Semantic token usage */
.button {
  background: var(--color-primary);
}
```

- Build reusable foundations first
- Standardize tokens/variants/states
- Prioritize accessibility
- Keep architecture scalable
- Avoid unnecessary complexity

---

## 📌 Popular Frontend Libraries

Popular frontend libraries help build scalable, reusable, and modern UI applications.

| Library | Type                          | Common Usage                |
| ------- | ----------------------------- | --------------------------- |
| React   | UI Library                    | SPA, dashboards, SaaS       |
| Vue     | Progressive Framework         | Lightweight modern apps     |
| Angular | Full Framework                | Enterprise applications     |
| Svelte  | Compiler-based Framework      | High-performance apps       |
| SolidJS | Reactive UI Library           | Fast reactive interfaces    |
| Preact  | Lightweight React Alternative | Small bundle apps           |
| Next.js | React Framework               | SSR, fullstack apps         |
| Nuxt    | Vue Framework                 | SSR Vue applications        |
| Remix   | React Framework               | Nested routing/data loading |
| Astro   | Content-focused Framework     | Static/content websites     |

### UI Libraries

| Library              | Common Usage               | Strong Areas                |
| -------------------- | -------------------------- | --------------------------- |
| Material UI (MUI)    | Enterprise apps            | Material Design, components |
| Ant Design           | Admin dashboards           | Data-heavy enterprise UI    |
| Chakra UI            | React apps                 | Accessibility, DX           |
| Mantine              | Modern React apps          | Rich components/hooks       |
| shadcn/ui            | Custom UI systems          | Full customization          |
| Bootstrap            | Responsive websites        | Fast UI development         |
| Tailwind UI          | Tailwind projects          | Utility-first components    |
| PrimeReact           | Enterprise React apps      | Data tables/forms           |
| Semantic UI          | Traditional UI apps        | Semantic class system       |
| Fluent UI            | Microsoft ecosystem        | Enterprise accessibility    |
| Carbon Design System | IBM ecosystem              | Enterprise systems          |
| Headless UI          | Fully custom UI            | Unstyled accessibility      |
| Radix UI             | Accessible primitives      | Headless components         |
| DaisyUI              | Tailwind component library | Fast prototyping            |

### State Libraries

| Library       | Common Usage           |
| ------------- | ---------------------- |
| Redux Toolkit | Large state management |
| Zustand       | Lightweight state      |
| MobX          | Reactive state         |
| Recoil        | React state management |

### Data Libraries

| Library        | Common Usage          |
| -------------- | --------------------- |
| TanStack Query | API/server state      |
| Axios          | HTTP requests         |
| SWR            | Data fetching/caching |

### Form Libraries

| Library         | Common Usage       |
| --------------- | ------------------ |
| React Hook Form | Performant forms   |
| Formik          | Form handling      |
| Zod             | Schema validation  |
| Yup             | Validation schemas |

### Animation Libraries

| Library       | Common Usage        |
| ------------- | ------------------- |
| Framer Motion | React animations    |
| GSAP          | Advanced animations |
| Lottie        | JSON animations     |

- Choose libraries based on project scale
- Avoid unnecessary dependencies
- Prefer actively maintained libraries
- Standardize libraries across projects
- Prioritize accessibility and performance

---

## 📌 Headless UI vs Styled UI

Headless UI libraries provide behavior/accessibility only, while styled UI libraries include ready-made visual design.

| Type        | Meaning                    | Examples                   |
| ----------- | -------------------------- | -------------------------- |
| Headless UI | Logic + accessibility only | Radix UI, Headless UI      |
| Styled UI   | Pre-styled components      | MUI, Ant Design, Chakra UI |

| Feature           | Headless UI           | Styled UI            |
| ----------------- | --------------------- | -------------------- |
| Styling           | Fully custom          | Prebuilt styles      |
| Flexibility       | Very high             | Moderate             |
| Design Freedom    | Complete control      | Limited/customizable |
| Accessibility     | Built-in behavior     | Built-in components  |
| Development Speed | Slower setup          | Faster development   |
| Consistency       | Developer-managed     | Built-in UI patterns |
| Customization     | High                  | Medium               |
| Bundle Size       | Usually smaller       | Usually larger       |
| Learning Curve    | Higher                | Easier               |
| Best For          | Custom design systems | Fast development     |

### Common Headless Libraries

| Library     | Common Usage          |
| ----------- | --------------------- |
| Radix UI    | Accessible primitives |
| Headless UI | Tailwind projects     |
| Ariakit     | Accessible components |
| React Aria  | Adobe accessibility   |

### Common Styled Libraries

| Library    | Common Usage        |
| ---------- | ------------------- |
| MUI        | Enterprise apps     |
| Ant Design | Admin dashboards    |
| Chakra UI  | Accessible React UI |
| Mantine    | Modern React apps   |

### When to Use

| Use Case              | Better Choice |
| --------------------- | ------------- |
| Custom Design System  | Headless UI   |
| Fast MVP Development  | Styled UI     |
| Full Branding Control | Headless UI   |
| Enterprise Dashboards | Styled UI     |
| Tailwind Projects     | Headless UI   |
| Rapid Prototyping     | Styled UI     |

- Use headless UI for custom systems
- Use styled UI for faster development
- Avoid mixing multiple styled libraries
- Prefer accessibility-first libraries
- Combine headless UI with design tokens/themes

---

## 📌 CSS Strategy in Design Systems

CSS strategies define how styles are structured, scaled, shared, and maintained across applications.

| Strategy            | Common Usage             | Examples                   |
| ------------------- | ------------------------ | -------------------------- |
| Global CSS          | Base styles/themes       | `globals.css`              |
| CSS Modules         | Scoped component styles  | `Button.module.css`        |
| Utility-First CSS   | Fast styling system      | Tailwind CSS               |
| CSS-in-JS           | Dynamic component styles | styled-components, Emotion |
| Atomic CSS          | Small reusable classes   | UnoCSS, Tailwind           |
| BEM Methodology     | Structured class naming  | `.card__header--active`    |
| Headless Styling    | Fully custom UI styling  | Radix UI + Tailwind        |
| Token-Based Styling | Semantic design tokens   | CSS variables              |

### Recommended Design System Strategy

```txt
Design Tokens
  ↓
Global Theme Variables
  ↓
Reusable Components
  ↓
Utility/Scoped Styles
```

### CSS Modules Example

```css
.button {
  border-radius: 8px;
}
```

```tsx
import styles from "./Button.module.css";
```

### CSS Architecture

```txt
styles/
├── globals.css
├── tokens.css
├── themes/
├── utilities/
└── components/
```

| Styling Approaches  | Best For                |
| ------------------- | ----------------------- |
| Tailwind CSS        | Fast scalable UI        |
| CSS Modules         | Scoped maintainable CSS |
| CSS Variables       | Theming/tokens          |
| CSS-in-JS           | Dynamic styling         |
| Headless + Tailwind | Custom design systems   |

### Enterprise Strategy Example

```txt
Tokens
  ↓
Themes
  ↓
Primitive Components
  ↓
Feature Components
```

- Keep styles scalable and reusable
- Prefer component-scoped styling
- Centralize themes and tokens
- Minimize global CSS leakage
- Use utility classes carefully

---

## 📌 Enterprise Design System Features

Enterprise design systems provide scalable, reusable, and standardized UI architecture for large applications and teams.

| Feature Area         | Common Features                 | Examples                      |
| -------------------- | ------------------------------- | ----------------------------- |
| Design Tokens        | Colors, spacing, typography     | `--color-primary`, `--gap-md` |
| Component Library    | Reusable UI components          | Button, Modal, Table          |
| Theming              | Light/dark/brand themes         | Dark Mode, Brand Themes       |
| Accessibility        | Keyboard, ARIA, contrast        | Focus Ring, `aria-label`      |
| Documentation        | Usage guidelines/examples       | Storybook, Design Docs        |
| Responsive System    | Mobile/tablet/desktop support   | Responsive Grid, Breakpoints  |
| Layout System        | Grid, containers, spacing       | AppShell, Container           |
| State Management     | Loading, error, empty states    | Skeleton, Error Alert         |
| Variant System       | Sizes, styles, themes           | Primary, Outline, `lg`        |
| Icon System          | Shared icon library             | Lucide, Material Icons        |
| Motion System        | Standard animations/transitions | Fade In, Slide Drawer         |
| Testing System       | UI/A11Y/visual testing          | Jest, Chromatic               |
| Versioning           | Semantic releases/changelog     | `v2.1.0`, Changelog           |
| Multi-Brand Support  | Theme customization             | Brand Blue, Brand Green       |
| Internationalization | RTL/language support            | Arabic RTL, Locale Switch     |
| Permissions UI       | Role-based interfaces           | Admin/User Views              |
| Data Components      | Tables, filters, charts         | DataTable, Analytics Chart    |
| Form System          | Validation/workflows            | Multi-step Form, Validation   |
| Developer Tooling    | Storybook, tokens sync          | Tokens Studio, Storybook      |
| CI/CD Integration    | Automated releases/testing      | GitHub Actions, npm Publish   |

### Enterprise Architecture

```txt
Tokens
  ↓
Themes
  ↓
Primitive Components
  ↓
Business Components
  ↓
Applications
```

| Common Enterprise Priorities | Focus                 |
| ---------------------------- | --------------------- |
| Scalability                  | Large applications    |
| Consistency                  | Shared UI standards   |
| Accessibility                | Enterprise compliance |
| Maintainability              | Reusable architecture |
| Performance                  | Optimized UI          |
| Team Collaboration           | Shared workflows      |

- Centralize tokens/themes
- Build reusable primitives first
- Standardize variants/states
- Prioritize accessibility
- Maintain strong documentation
- Automate testing and releases
- Keep APIs predictable
- Design for multi-team scalability

---

## 📌 Best Practices

Best practices help maintain scalable, consistent, accessible, and production-ready design systems.

| Area            | Best Practice                         |
| --------------- | ------------------------------------- |
| Tokens          | Use semantic design tokens            |
| Components      | Build reusable primitives first       |
| Styling         | Avoid hardcoded values                |
| Naming          | Follow consistent conventions         |
| Variants        | Keep variants standardized            |
| Accessibility   | Build A11Y by default                 |
| Theming         | Support light/dark themes             |
| Layouts         | Use shared spacing/grid systems       |
| Documentation   | Document reusable components          |
| Testing         | Automate UI and accessibility testing |
| Performance     | Avoid unnecessary complexity          |
| Architecture    | Separate UI and business logic        |
| State Design    | Handle loading/error/empty states     |
| Responsiveness  | Design mobile-first layouts           |
| Icons           | Use one consistent icon library       |
| Motion          | Keep animations subtle                |
| Versioning      | Follow semantic versioning            |
| Maintainability | Reuse patterns and utilities          |

- Prefer composition over duplication
- Keep APIs predictable
- Design for scalability early
- Maintain accessibility standards
- Keep systems simple and reusable

---

## 📌 Deprecated / Avoid Patterns

Avoid outdated or poor design system patterns that reduce scalability, accessibility, and maintainability.

| ❌ Avoid                | Example                     | ✅ Better             | Example                  |
| ----------------------- | --------------------------- | --------------------- | ------------------------ |
| Hardcoded styles        | `background: blue;`         | Semantic tokens       | `var(--color-primary)`   |
| Inline styling          | `<div style={{}}>`          | Reusable styling      | CSS Modules/Tailwind     |
| Global CSS conflicts    | `.button {}`                | Scoped styles         | `Button.module.css`      |
| Large components        | `Dashboard.tsx` 2000+ lines | Composable components | `CardHeader`, `CardBody` |
| Deep nesting            | `components/ui/base/...`    | Flat structure        | `components/forms/`      |
| Too many variants       | `blueLargeRounded`          | Standard variants     | `primary`, `outline`     |
| Multiple UI libraries   | MUI + Ant + Bootstrap       | Single system         | Only Chakra UI           |
| Mixing icon libraries   | Lucide + FontAwesome        | One icon system       | Only Lucide              |
| Non-semantic HTML       | `<div onclick="">`          | Semantic elements     | `<button>`               |
| No accessibility        | Missing ARIA/focus          | Built-in A11Y         | Focus + `aria-label`     |
| No dark mode strategy   | Hardcoded colors            | Theme tokens          | Light/Dark themes        |
| Arbitrary spacing       | `margin: 19px;`             | Shared spacing        | `var(--gap-md)`          |
| Business logic in UI    | API calls in Button         | Separate concerns     | Services/hooks           |
| Duplicate components    | `BlueButton`                | Shared components     | Reusable `Button`        |
| No loading/error states | Blank loading UI            | Full state design     | Skeleton/Error UI        |
| Overusing animations    | Constant bouncing           | Subtle motion         | Hover elevation          |
| Primitive tokens in UI  | `--blue-500`                | Semantic tokens       | `--color-surface`        |
| Over-customized APIs    | 50+ props                   | Predictable APIs      | Simple reusable props    |
| No documentation        | Undocumented UI             | Component docs        | Storybook                |
| No visual testing       | Manual testing only         | Regression testing    | Chromatic                |
| No responsive testing   | Desktop-only UI             | Mobile-first testing  | Responsive breakpoints   |
| No versioning strategy  | Random releases             | Semantic versioning   | `v2.1.0`                 |

- Keep systems scalable and predictable
- Prefer semantic tokens and reusable patterns
- Standardize naming, spacing, and variants
- Prioritize accessibility and responsiveness
- Avoid unnecessary complexity

---
