# 🎯 HTML – Interview Q&A

---

## 🟢 BASIC

#### 1. What is HTML?

**Answer:** HyperText Markup Language used to structure content on the web. It provides semantic meaning to web content.

#### 2. What is a tag?

**Answer:** A markup element enclosed in angle brackets (`<>`) used to define HTML structure. Example: `<p>`, `<div>`.

#### 3. What is an element?

**Answer:** A complete HTML unit consisting of opening tag, content, and closing tag. Example: `<p>Hello</p>`.

#### 4. What is an attribute?

**Answer:** Extra information added inside a tag to modify element behavior. Example: `<img src="pic.jpg" alt="Picture">`.

#### 5. What is `<!DOCTYPE html>`?

**Answer:** Declares the document type and tells browser to use HTML5 standards mode.

#### 6. Purpose of `<html>` tag?

**Answer:** Root element that wraps the entire HTML document.

#### 7. Difference between `<head>` and `<body>`?

**Answer:** `<head>` contains metadata (title, scripts, styles), `<body>` contains visible page content.

#### 8. What are void elements?

**Answer:** Self-closing tags that don't have closing tag. Example: `<img>`, `<br>`, `<hr>`, `<input>`, `<meta>`.

#### 9. Difference between `<div>` and `<span>`?

**Answer:** `<div>` is block-level (takes full width), `<span>` is inline (flows with text).

#### 10. What are block elements?

**Answer:** Elements that take full width and start on a new line. Example: `<div>`, `<p>`, `<h1>`, `<header>`.

#### 11. What are inline elements?

**Answer:** Elements that flow within text without starting new line. Example: `<span>`, `<a>`, `<strong>`, `<em>`.

#### 12. What is `<meta charset="UTF-8">`?

**Answer:** Specifies character encoding for the document. UTF-8 supports all international characters.

---

## 🟡 INTERMEDIATE

#### 1. What is semantic HTML?

**Answer:** HTML elements that clearly describe their meaning (e.g., `<header>`, `<nav>`, `<article>`) instead of generic `<div>`.

#### 2. Why use semantic HTML?

**Answer:** Improves accessibility for screen readers, enhances SEO for search engines, and improves code readability.

#### 3. Examples of semantic tags?

**Answer:** `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, `<footer>`, `<figure>`.

#### 4. Difference between `<section>` and `<article>`?

**Answer:** `<section>` is a generic container for related content. `<article>` is self-contained content that can stand alone.

#### 5. Purpose of `<meta name="viewport">`?

**Answer:** Controls layout and scaling on mobile devices. Ensures responsive design works correctly.

#### 6. What is the `<form>` element?

**Answer:** Container for collecting user input. Data can be sent to server using GET or POST method.

#### 7. Difference between `GET` and `POST`?

**Answer:** GET appends data to URL (visible, limited), POST sends data in request body (hidden, larger data).

#### 8. What is the `<label>` element?

**Answer:** Associates text with a form input for accessibility. Clicking label focuses the input.

#### 9. Purpose of `<fieldset>` and `<legend>`?

**Answer:** `<fieldset>` groups related form fields. `<legend>` provides title for the fieldset.

#### 10. What is `<img>` `alt` attribute?

**Answer:** Alternative text describing image for accessibility. Also displays if image fails to load.

#### 11. Why is `alt` text important?

**Answer:** Required for accessibility (screen readers), SEO (image search), and user experience (slow networks).

#### 12. Difference between `<strong>` and `<b>`?

**Answer:** `<strong>` indicates importance (semantic), `<b>` is just bold styling (non-semantic).

#### 13. Difference between `<em>` and `<i>`?

**Answer:** `<em>` indicates emphasis (semantic), `<i>` is just italic styling (non-semantic).

#### 14. What is `<figure>` and `<figcaption>`?

**Answer:** `<figure>` wraps image with caption. `<figcaption>` provides descriptive text for the figure.

#### 15. Purpose of `<audio>` and `<video>` tags?

**Answer:** `<audio>` embeds sound files, `<video>` embeds video files with native browser controls.

#### 16. What is `<source>` tag?

**Answer:** Provides multiple media sources for `<audio>` and `<video>` for browser compatibility.

#### 17. What is `<meta name="description">`?

**Answer:** Provides page summary for search engines. Appears in search results below page title.

#### 18. What is `<link rel="canonical">`?

**Answer:** Specifies the preferred URL for a page to prevent duplicate content issues in SEO.

---

## 🔴 ADVANCED

#### 1. Explain HTML rendering and parsing process?

**Answer:** Browser parses HTML into DOM tree, creates CSSOM from CSS, combines into render tree, performs layout, and paints to screen.

#### 2. What is DOCTYPE and why is it important?

**Answer:** DOCTYPE declares document type and HTML version. Triggers standards mode vs quirks mode in browser rendering.

#### 3. Explain difference between standards mode and quirks mode?

**Answer:** Standards mode follows W3C standards. Quirks mode maintains backward compatibility with older browsers. DOCTYPE determines the mode.

#### 4. What is the difference between `<meta http-equiv="refresh">` and JavaScript redirect?

**Answer:** Meta refresh happens immediately on page load (server-side). JS redirect can be triggered by events and is more flexible.

#### 5. How do you implement responsive images using `srcset` and `sizes`?

**Answer:** `srcset` provides different image versions. `sizes` tells browser which version to use based on viewport. Improves performance on mobile.

#### 6. Explain lazy loading in HTML (`loading="lazy"`)?

**Answer:** Images/frames load only when near viewport. Improves page load speed and reduces bandwidth usage for below-the-fold content.

#### 7. What is the purpose of `<base>` tag?

**Answer:** Sets base URL for all relative URLs in document. Useful for single page applications or relative path resolution.

#### 8. Difference between `async` and `defer` in script tags?

**Answer:** `async` - downloads in parallel, executes immediately (order not guaranteed). `defer` - downloads in parallel, executes after HTML parsing (order preserved).

#### 9. When should you use `type="module"` in script tags?

**Answer:** Use for ES6 modules. Enables `import`/`export`, defers execution automatically, and creates separate scope for variables.

#### 10. How do you prevent clickjacking attacks using HTML?

**Answer:** Use `X-Frame-Options` header in HTTP response (not HTML directly) or `<meta http-equiv="X-UA-Compatible">` for legacy support.

#### 11. Explain Content Security Policy (CSP) implementation?

**Answer:** Use `<meta http-equiv="Content-Security-Policy">` to restrict resource loading sources. Prevents XSS and injection attacks.

#### 12. Real-life: A website loads slowly on mobile. What HTML optimizations would you apply?

**Answer:** Use lazy loading for images, responsive `srcset`, compress images, async/defer scripts, minimize CSS in head, use semantic HTML for better parsing.

#### 13. Real-life: Design an e-commerce product page with proper HTML structure?

**Answer:** Use `<header>` for nav, `<article>` for product, `<figure>` for images, `<aside>` for related products, `<footer>` for company info. Include proper `alt` text, structured data.

#### 14. Real-life (Indian context): A banking website needs high accessibility for visually impaired users. What HTML practices ensure this?

**Answer:** Use semantic tags, provide `alt` text for all images, use `<label>` for form fields, proper heading hierarchy, ARIA attributes, skip-to-content links.

#### 15. Calculation: If page has 100 images (500KB each). With lazy loading, how much data initially loads?

**Answer:** Without lazy loading = 50MB. With lazy loading = only above-the-fold images (~10-15 images = 5-7.5MB). Saves ~40-45MB on initial load.

#### 16. Calculation: HTML file is 100KB, CSS is 200KB, JS is 300KB, Images 5MB. How do you prioritize loading?

**Answer:** Load HTML first (render), defer CSS in head using media queries, defer JS with async/defer attributes, lazy load images. Critical path: HTML → CSS → visible JS → rest.

---

## 📋 Quick Reference

| Concept       | Purpose                                         |
| ------------- | ----------------------------------------------- |
| Semantic HTML | Better accessibility, SEO, code clarity         |
| Forms         | Collect user input securely                     |
| Media         | Embed images, audio, video                      |
| Meta tags     | SEO, mobile responsiveness, social sharing      |
| Accessibility | Screen readers, keyboard navigation, ARIA       |
| Performance   | Lazy loading, image optimization, async scripts |
