# 👉 HTML Cheatsheet

## 📌 Overview

- **HTML** → HyperText Markup Language used to structure web pages.
- **Element** → Tag + content + closing tag.
- **Attribute** → Additional information inside a tag.
- **Void Elements** → Tags without closing tag (`img`, `br`, `hr`, `input`, `meta`, `link`).

---

## 📌 Document Structure

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Page Title</title>
  </head>
  <body></body>
</html>
```

| Element           | Purpose                            |
| ----------------- | ---------------------------------- |
| `<!DOCTYPE html>` | HTML5 declaration (standards mode) |
| `<html>`          | Root element (`lang` recommended)  |
| `<head>`          | Metadata, SEO, styles, scripts     |
| `<body>`          | Visible page content               |

---

## 📌 Metadata

`<title>My Website</title>`  
Page title (browser tab, SEO).

`<meta charset="UTF-8">`  
Character encoding (UTF-8 recommended).

`<meta name="viewport" content="width=device-width, initial-scale=1">`  
Responsive layout control for mobile devices.

`<meta name="description" content="Frontend developer portfolio">`  
Search engine page description.

`<meta name="robots" content="index, follow">`  
Search engine crawling instructions.

`<meta http-equiv="refresh" content="30">`  
HTTP-equivalent behavior (e.g., auto refresh, redirects).

`<link rel="stylesheet" href="styles.css">`  
External resources (CSS, icons, fonts).

- Common `rel` values
- `stylesheet` `icon` `preload` `prefetch` `canonical`

`<style>body{margin:0}</style>`  
Internal CSS styles.

`media` target media type

`<script src="app.js" defer></script>`  
Embed or load JavaScript.

- `src` file source
- `defer` run after HTML parsing
- `async` load independently
- `type="module"` ES module script

`<base href="https://example.com/">`  
Base URL for relative links and resources.

---

## 📌 Text Content

| Tag            | Purpose          | Notes             |
| -------------- | ---------------- | ----------------- |
| `<h1>–<h6>`    | Headings         | Structure + SEO   |
| `<p>`          | Paragraph        | Block text        |
| `<br />`       | Line break       | Void              |
| `<hr />`       | Divider          | Thematic break    |
| `<strong>`     | Importance       | Semantic bold     |
| `<em>`         | Emphasis         | Semantic italic   |
| `<mark>`       | Highlight        | Reference text    |
| `<small>`      | Fine text        | Disclaimers       |
| `<span>`       | Inline container | Styling           |
| `<div>`        | Block container  | Layout            |
| `<pre>`        | Preformatted     | Preserves spacing |
| `<code>`       | Code             | Inline code       |
| `<blockquote>` | Block quote      | Long quote        |
| `<q>`          | Inline quote     | Short quote       |
| `<abbr>`       | Abbreviation     | Use `title`       |

---

## 📌 Links & Media

```html
<a href="https://example.com" target="_blank" rel="noopener noreferrer">Link</a>
```

- `href` destination
- `target` open behavior
- `rel` security/relationship
- `download` file download
- `title` tooltip

```html
<img
  src="image.jpg"
  alt="Description"
  loading="lazy"
  width="300"
  height="200"
/>
```

- `src` image URL
- `alt` accessibility text
- `width` `height` size
- `loading` lazy loading
- `srcset` responsive images

```html
<video src="video.mp4" controls width="400" poster="thumb.jpg"></video>
```

- `src` video source
- `controls` player controls
- `autoplay` `loop` `muted`
- `poster` preview image

```html
<audio src="audio.mp3" controls></audio>
```

- `src` audio source
- `controls` `autoplay` `loop` `muted`

```html
<source src="video.webm" type="video/webm" />
```

Defines multiple media sources for `<video>` or `<audio>`.

- `src` media file
- `type` MIME type
- `media` responsive condition

```html
<picture>
  <source srcset="image.webp" />
  <img src="image.jpg" alt="Example" />
</picture>
```

Responsive images or format fallbacks.

- `srcset` responsive image set
- `media` breakpoint conditions

```html
<iframe
  src="https://example.com"
  width="600"
  height="400"
  loading="lazy"
></iframe>
```

Embeds another webpage or external content.

- `src` page URL
- `width` `height` size
- `loading` lazy load
- `allowfullscreen`
- `sandbox`

---

## 📌 Lists

- `<ul>` — Unordered list (bullets)
- `type` bullet style (`disc` `circle` `square`) _(deprecated, use CSS)_
- `<ol>` — Ordered list (numbered)

- `type` attr numbering style (`1` `A` `a` `I` `i`)
- `start` attr starting number
- `reversed` attr descending order

```html
<ol start="5" reversed>
  <li>Item</li>
</ol>
```

- `value` attr custom numbering in ordered lists

```html
<li value="10">Item</li>
```

---

- `<dl>` — Description list (terms and definitions)

```html
<dl>
  <dt>Term</dt>
  <dd>Description</dd>
</dl>
```

Elements

- `<dt>` term
- `<dd>` description

Lists can be nested.

---

## 📌 Tables

```html
<table>
  <caption>
    Example Table
  </caption>

  <colgroup>
    <col span="1" />
  </colgroup>

  <thead>
    <tr>
      <th scope="col">Header</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>Data</td>
    </tr>
  </tbody>

  <tfoot>
    <tr>
      <td>Footer</td>
    </tr>
  </tfoot>
</table>
```

| Element      | Purpose                        |
| ------------ | ------------------------------ |
| `<table>`    | Table container                |
| `<caption>`  | Table title / description      |
| `<colgroup>` | Group of table columns         |
| `<col>`      | Column styling / width control |
| `<thead>`    | Header section                 |
| `<tbody>`    | Table body                     |
| `<tfoot>`    | Footer section                 |
| `<tr>`       | Table row                      |
| `<th>`       | Header cell                    |
| `<td>`       | Data cell                      |

---

### Important Attributes

`colspan` → merge columns
`rowspan` → merge rows
`scope` → header association (`row`, `col`)
`headers` → reference header cells (accessibility)

```html
<th colspan="2">Merged Header</th>
<td rowspan="2">Merged Cell</td>
<th scope="col">Name</th>
```

## 📌 Forms

```html
<form action="/submit" method="post"></form>
```

Form container that sends user input to a server.

- `action` submit URL
- `method` `get|post`
- `enctype` `multipart/form-data` (file upload)
- `target` response location
- `autocomplete`

---

```html
<label for="email">Email</label> <input id="email" name="email" type="email" />
```

Input label associated with a control.

- `for` links to input `id`
- improves accessibility
- clicking label focuses input

---

```html
<input type="text" name="username" placeholder="Enter name" required />
```

Types

- `text` `email` `password` `number` `tel` `url` `date` `time` `color` `range` `checkbox` `radio` `file` `submit` `reset`

Common attributes

- `name` form data key
- `value` default value
- `placeholder` hint text
- `required` mandatory field
- `disabled` disable input
- `readonly` prevent editing
- `min` `max` range
- `step` increment
- `maxlength` character limit
- `pattern` regex validation
- `checked` default selection
- `multiple` multiple values (file/email)
- `accept` allowed file types
- `autocomplete` autofill
- `autofocus` focus on load
- `form` link external form

---

```html
<textarea name="message" rows="4" cols="30"></textarea>
```

Multi-line text input.

- `name` form key
- `rows` height
- `cols` width
- `maxlength` limit
- `placeholder`

---

```html
<select name="country">
  <option value="in">India</option>
  <option value="us" selected>USA</option>
</select>
```

Dropdown selection list.

- `name` form key
- `multiple` allow multiple selections
- `size` visible options

- `option` attributes
- `value` option value
- `selected` default option
- `disabled`

---

```html
<input list="browsers" />
<datalist id="browsers">
  <option value="Chrome"></option>
  <option value="Firefox"></option>
</datalist>
```

Autocomplete suggestions for input fields.

---

```html
<button type="submit">Submit</button>
```

- `type` `submit|button|reset`
- `disabled` prevent interaction
- `form` associate with form

---

```html
<fieldset>
  <legend>Personal Info</legend>
  <input type="text" />
</fieldset>
```

Group related form controls.

- `disabled` disable entire group

---

## 📌 Semantic Elements

| Tag                       | Purpose      |
| ------------------------- | ------------ |
| `<header>`                | Top section  |
| `<nav>`                   | Navigation   |
| `<main>`                  | Main content |
| `<section>`               | Group        |
| `<article>`               | Independent  |
| `<aside>`                 | Sidebar      |
| `<footer>`                | Footer       |
| `<figure>` `<figcaption>` | Media        |
| `<details>` `<summary>`   | Toggle       |

### Benefits

- Improves **accessibility**
- Improves **SEO**
- Provides **clear document structure**
- Helps **screen readers understand page layout**

---

## 📌 Global Attributes

| Attribute         | Purpose                   | Notes                                      |
| ----------------- | ------------------------- | ------------------------------------------ |
| `id`              | Unique element identifier | Used for CSS, JS, anchors.                 |
| `class`           | CSS / JS selector         | Multiple classes allowed.                  |
| `style`           | Inline CSS                | Overrides external styles.                 |
| `title`           | Tooltip text              | Visible on hover.                          |
| `hidden`          | Hide element              | Not rendered visually.                     |
| `tabindex`        | Keyboard navigation order | `0` normal flow • `-1` programmatic focus. |
| `contenteditable` | Editable content          | `true` enables inline editing.             |
| `data-*`          | Custom data attributes    | Used with JavaScript (`dataset`).          |
| `lang`            | Language declaration      | Helps accessibility and SEO.               |
| `dir`             | Text direction            | `ltr` or `rtl`.                            |
| `draggable`       | Drag capability           | `true` enables drag events.                |
| `spellcheck`      | Spell checking            | `true` / `false`.                          |

---

## 📌 Accessibility

- Use semantic HTML (`header`, `nav`, `main`, `section`, `article`).
- Use `<label for="">` with matching input `id`.
- Always include `alt` text for `<img>`.
- Maintain proper heading order (`h1 → h6`).
- Ensure keyboard navigation (`tab`, `tabindex`).
- Use `aria-*` attributes only when semantic HTML is insufficient.
  aria-label
  aria-labelledby
  aria-describedby
  aria-hidden
  role
- Provide accessible form validation and error messages.
- Ensure sufficient color contrast for readability.
- Use descriptive link text (avoid "click here").
- Support screen readers with proper landmarks (`header`, `nav`, `main`, `footer`).

---

## 📌 SEO Basics

- Use descriptive `<title>` for each page.
- Add `<meta name="description">`.
- Maintain proper heading hierarchy (`h1 → h6`).
- Use descriptive `alt` text for images.
- Use semantic HTML (`header`, `main`, `article`, etc.).
- Use meaningful link text (avoid "click here").
- Set correct page language using `<html lang="...">`.
- Use canonical URLs when duplicate pages exist.

---

## 📌 HTML5 Features

- Semantic elements (`header`, `nav`, `main`, `section`, `article`, `footer`)
- Native media support (`audio`, `video`)
- New form input types (`email`, `date`, `range`, `color`, etc.)
- Native form validation (`required`, `pattern`, `min`, `max`)
- Graphics support (`canvas`, `svg`)
- Web storage (`localStorage`, `sessionStorage`)
- Geolocation API
- Drag and Drop API
- Web Workers (background scripts)

---

## 📌 Quick Recall

- HTML → Structure of web pages
- Elements → Building blocks (`<tag>content</tag>`)
- Attributes → Additional element behavior (`name="value"`)
- Semantic HTML → Meaningful structure (better SEO & accessibility)
- Metadata → Page information (`title`, `meta`, `link`)
- Media → Images, audio, video, embedded content
- Forms → User input collection and submission
- Accessibility → Screen readers, keyboard navigation, ARIA

---

## 📌 Deprecated HTML Tags

| Tag          | Purpose               | Modern Replacement                   |
| ------------ | --------------------- | ------------------------------------ |
| `<font>`     | Font styling          | CSS (`font-family`, `color`, `size`) |
| `<center>`   | Center content        | CSS (`text-align:center`)            |
| `<big>`      | Larger text           | CSS (`font-size`)                    |
| `<strike>`   | Strikethrough text    | `<s>` or CSS                         |
| `<tt>`       | Monospace text        | CSS (`font-family: monospace`)       |
| `<frame>`    | Frame inside frameset | `<iframe>`                           |
| `<frameset>` | Frame-based layout    | CSS layout / `<iframe>`              |
| `<noframes>` | Fallback for frames   | Not used                             |
| `<applet>`   | Java applet           | Not supported                        |
| `<basefont>` | Base font settings    | CSS                                  |
| `<dir>`      | Directory list        | `<ul>`                               |
| `<menu>`     | Menu list             | `<ul>`                               |

## 📌 Deprecated Attributes

| Attribute | Used In         | Replacement              |
| --------- | --------------- | ------------------------ |
| `align`   | many tags       | CSS (`text-align`)       |
| `bgcolor` | tables/body     | CSS (`background-color`) |
| `border`  | tables          | CSS (`border`)           |
| `width`   | layout tables   | CSS (`width`)            |
| `height`  | layout elements | CSS (`height`)           |
| `valign`  | table cells     | CSS (`vertical-align`)   |
