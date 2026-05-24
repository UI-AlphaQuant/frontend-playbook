# DESIGN SYSTEM

This document describes the **foundation and standards** for a reusable, scalable, and accessible **UI design system**, independent of any specific component library. It includes **design tokens, components, layout, accessibility, and documentation guidelines**.

---

## 1. DESIGN TOKENS

### Colors

- **Primary:** #1E90FF
- **Secondary:** #FF4081
- **Success:** #4CAF50
- **Warning:** #FFC107
- **Error:** #F44336
- **Neutral / Gray scale:** #F5F5F5, #E0E0E0, #BDBDBD, #757575, #212121
- **Background:** #FFFFFF
- **Text Primary:** #212121
- **Text Secondary:** #757575

### Typography

- **Font Family:** `'Inter', sans-serif`
- **Font Sizes:** 12, 14, 16, 18, 20, 24, 32, 48
- **Font Weights:** 400 (Regular), 500 (Medium), 600 (Semi-Bold), 700 (Bold)
- **Line Heights:** 1.2, 1.4, 1.6
- **Letter Spacing:** 0, 0.5px, 1px

### Spacing

- Base scale: 4px
- Scale: 4, 8, 12, 16, 20, 24, 32, 40, 48, 64

### Border Radius

- Small: 4px
- Medium: 8px
- Large: 16px
- Pill: 9999px

### Shadows

- Small: `0 1px 3px rgba(0,0,0,0.12)`
- Medium: `0 4px 6px rgba(0,0,0,0.1)`
- Large: `0 10px 20px rgba(0,0,0,0.15)`

---

## 2. COMPONENTS

### Button

| Variant   | Description                                 |
| --------- | ------------------------------------------- |
| Primary   | Main action button                          |
| Secondary | Secondary action                            |
| Default   | Neutral / standard                          |
| Ghost     | Transparent background, border only         |
| Outlined  | Border emphasis without fill                |
| Icon      | Icon-only button                            |
| Size      | Small / Medium / Large                      |
| State     | Normal / Hover / Focus / Disabled / Loading |

---

### Input

| Variant  | Description                                 |
| -------- | ------------------------------------------- |
| Text     | Standard text input                         |
| Password | Password input with hide/show option        |
| Number   | Numeric input                               |
| Search   | Input with search icon and clear option     |
| Disabled | Non-editable input                          |
| States   | Normal / Focus / Error / Success / Disabled |
| Size     | Small / Medium / Large                      |

---

### Select / Dropdown

| Variant    | Description                                 |
| ---------- | ------------------------------------------- |
| Single     | Single selection dropdown                   |
| Multi      | Multi-selection dropdown                    |
| Searchable | Dropdown with search/filter option          |
| Disabled   | Non-editable                                |
| States     | Normal / Focus / Error / Success / Disabled |
| Size       | Small / Medium / Large                      |

---

### Checkbox & Radio

| Component | Description                               |
| --------- | ----------------------------------------- |
| Checkbox  | Single / Group, Checked / Unchecked       |
| Radio     | Single selection group                    |
| Disabled  | Non-interactive state                     |
| States    | Normal / Hover / Focus / Disabled / Error |

---

### Switch / Toggle

- Binary on/off control
- States: On / Off / Disabled / Loading
- Sizes: Small / Medium / Large

---

### Card

- Container for content and actions
- Variants: Default / Elevated / Outline
- Optional: Header, Footer, Media section
- Shadow: Small / Medium / Large
- Padding: Based on spacing scale

---

### Table

- Variants: Default / Striped / Bordered / Hover
- Features: Sortable columns, Pagination, Selectable rows
- States: Loading, Empty, Error

---

### Modal / Dialog

- Variants: Standard / Fullscreen / Confirmation
- Features: Header, Body, Footer, Close button
- Overlay with background shadow
- States: Open / Close / Loading

---

### Tooltip & Popover

- Tooltip: Hover / Focus info
- Popover: Click / Hover triggered content
- Positions: Top / Bottom / Left / Right / Auto
- Accessibility: ARIA labels

---

### Loader / Spinner

- Variants: Circular / Linear / Dots
- Size: Small / Medium / Large
- States: Indeterminate / Determinate

---

### Empty / Error States

- Display meaningful message
- Optional illustration or icon
- Suggest next actions

---

## 3. LAYOUT SYSTEM

- **Grid System:** 12-column flexible grid
- **Breakpoints:**
  - xs: <576px
  - sm: ≥576px
  - md: ≥768px
  - lg: ≥992px
  - xl: ≥1200px
- **Container widths:** Fixed or fluid per breakpoint
- **Gutters / Spacing:** Consistent spacing scale

---

## 4. ACCESSIBILITY STANDARDS

- Use semantic HTML elements
- Provide ARIA labels for interactive components
- Ensure keyboard navigation for all controls
- High contrast text & focus states
- Support screen readers

---

## 5. DOCUMENTATION & USAGE

- **Storybook:** Component showcase with props, states, and examples
- **Code snippets:** Usage examples for each component
- **Do / Don’t:** Best practices & anti-patterns
- **Versioning:** Track component updates & token changes
- **Testing:** Unit / Integration / Visual regression tests

---

## 6. THEMING

- Support **light/dark mode**
- Allow **brand customization** via color tokens
- Theme switching should update all components dynamically

---

## 7. BEST PRACTICES

- **One responsibility per component**
- **Variants over duplication** (don’t make new component for small differences)
- **Centralized tokens** for colors, spacing, typography
- **Consistent states**: hover, focus, disabled, error, loading
- **Library-agnostic**: Works without dependency on Ant Design or Material

---

**This foundation ensures your project is scalable, maintainable, and ready for enterprise-level development.**
