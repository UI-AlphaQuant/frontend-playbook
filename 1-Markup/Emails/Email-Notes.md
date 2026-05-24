# 👉 HTML Email Template

## 📌 Overview

- HTML emails are built using **table-based layouts**
- CSS support varies across email clients
- Inline CSS is preferred for compatibility
- Avoid complex layouts, modern CSS, and JavaScript

---

## 📌 Structure

```html id="email-structure"
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>Email</title>
  </head>
  <body>
    <table role="presentation" width="100%" cellpadding="0" cellspacing="0">
      <tr>
        <td align="center">
          <table role="presentation" width="600">
            <tr>
              <td>Email Content</td>
            </tr>
          </table>
        </td>
      </tr>
    </table>
  </body>
</html>
```

---

## 📌 Layout (Tables)

| Element               | Purpose               | Notes                     |
| --------------------- | --------------------- | ------------------------- |
| `<table>`             | Main layout container | Used instead of div       |
| `<tr>`                | Table row             | Structure                 |
| `<td>`                | Table cell            | Content container         |
| `role="presentation"` | Accessibility         | Not treated as data table |

---

## 📌 Attributes

```html id="table-attributes"
<table width="600" cellpadding="0" cellspacing="0" border="0"></table>
```

| Attribute     | Purpose              |
| ------------- | -------------------- |
| `width`       | Layout control       |
| `align`       | Horizontal alignment |
| `valign`      | Vertical alignment   |
| `cellpadding` | Inner spacing        |
| `cellspacing` | Cell spacing         |
| `border`      | Table border         |
| `bgcolor`     | Background color     |

---

## 📌 Styling (Inline CSS)

```html id="inline-css-example"
<td style="font-family:Arial; font-size:16px; color:#333;">Hello World</td>
```

Common supported styles

```txt id="supported-css-properties"
color
background-color
font-family
font-size
text-align
padding
border
```

---

## 📌 Media (Images)

```html id="image-example"
<img src="logo.png" width="200" alt="Company Logo" style="display:block;" />
```

| Attribute       | Purpose              |
| --------------- | -------------------- |
| `src`           | Image URL            |
| `alt`           | Accessibility text   |
| `width/height`  | Prevent layout shift |
| `display:block` | Remove gaps          |

Notes

- Host images online
- Use absolute URLs

---

## 📌 Links & Buttons

```html id="link-example"
<a href="https://example.com" target="_blank">Visit Website</a>
```

Notes

- Use full absolute URLs
- Style links inline
- Use descriptive text

---

### Button (Table-based)

```html id="table-button-example"
<table role="presentation">
  <tr>
    <td align="center">
      <a
        href="https://example.com"
        style="
display:inline-block;
border:12px solid #007BFF;
background:#007BFF;
color:#ffffff;
font-family:Arial, sans-serif;
font-size:16px;
text-decoration:none;"
      >
        Click Here
      </a>
    </td>
  </tr>
</table>
```

---

## 📌 Responsive

```css id="responsive-media-query"
@media only screen and (max-width: 600px) {
  .container {
    width: 100% !important;
  }
}
```

Notes

- Use **600px max width**
- Stack columns on mobile
- Avoid complex layouts

---

## 📌 Limitations

Avoid

```txt id="unsupported-features"
JavaScript
external CSS
flexbox
grid
forms
video
```

Limited support

```txt id="limited-support-css"
position
float
background-image
```

---

## 📌 Accessibility & Best Practices

- Use `alt` text for images
- Use semantic text hierarchy
- Ensure good color contrast
- Avoid image-only emails
- Use **table-based layout**
- Inline CSS for styling
- Keep width **≤ 600px**
- Use **web-safe fonts**
- Optimize images
- Test across email clients

---

## 📌 Dark Mode

Some email clients automatically adjust colors.

### Behaviors

| Type              | Description              | Clients                      |
| ----------------- | ------------------------ | ---------------------------- |
| No change         | Normal render            | Older Outlook                |
| Partial inversion | Background/text adjusted | Apple Mail, iOS Mail         |
| Full inversion    | Entire design inverted   | Outlook mobile, Gmail mobile |

---

### Best Practices

- Avoid pure white `#ffffff`
- Avoid pure black `#000000`
- Use neutral backgrounds (`#f4f6f8`, `#f9fafb`)
- Use dark gray text (`#1f2937`, `#374151`)
- Use transparent logos
- Maintain strong button contrast

Example palette

```txt id="dark-mode-palette"
bg: #f4f6f8
text: #1f2937
secondary: #6b7280
button: #2563eb
```

---

### Optional CSS

```css id="dark-mode-media-query"
@media (prefers-color-scheme: dark) {
  body {
    background: #111;
  }
  .container {
    background: #1a1a1a;
  }
}
```

Supported: Apple Mail, iOS Mail, Outlook Mac
Ignored: Gmail, Outlook Windows
