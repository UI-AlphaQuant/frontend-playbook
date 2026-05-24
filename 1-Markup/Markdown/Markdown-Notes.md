# 👉 Markdown Reference

## 📌 Headings

```md id="h1"
# Heading 1

## Heading 2

### Heading 3

#### Heading 4

##### Heading 5

###### Heading 6
```

---

## 📌 Text Formatting

```md id="t1"
**Bold text**
_Italic text_
~~Strikethrough~~
`inline code`
**_bold italic combo_**
```

---

## 📌 Lists

### Unordered

```md id="l1"
- Item 1
- Item 2
  - Sub item
    - Nested item
```

### Ordered

```md id="l2"
1. First
2. Second
3. Third
```

### Mixed

```md id="l3"
1. Item
   - Sub item
   - Sub item
```

---

## 📌 Links & References

```md id="link1"
[Open Google](https://google.com)
```

```md id="link2"
[Open Google][1]

[1]: https://google.com
```

---

## 📌 Images

```md id="img1"
![Logo](https://dummyimage.com/200x60/00000000/2563eb.png&text=Logo)
```

```md id="img2"
[![Logo](logo.png)](https://example.com)
```

---

## 📌 Blockquote

```md id="bq1"
> This is a quote

> Parent

> > Child
```

---

## 📌 Code

````md id="code1"
```js
console.log("Hello World");
```
````

### Languages

`html` `css` `scss` `sass`
`javascript` `js` `typescript` `ts` `jsx` `tsx`

`json` `yaml` `yml` `env`
`markdown` `md` `diff` `plaintext` `text`

`bash` `sh` `sql` `php` `python` `node`

---

## 📌 Tables

```md id="tbl1"
| Name | Role      |
| ---- | --------- |
| John | Developer |
| Anna | Designer  |
```

### Table Alignment

```md id="tbl2"
| Name | Role |
| :--- | :--: |
| John | Dev  |
| Anna |  UX  |
```

Alignments

```id="tbl3"
:---   left
:---:  center
---:   right
```

---

## 📌 Utilities

```md id="util1"
---
```

```md id="util2"
- [x] Completed task
- [ ] Pending task
```

```md id="util3"
\*This will not become italic\*
```

```md id="util4"
Line one  
Line two
```

---

## 📌 Advanced (GitHub)

```md id="adv1"
Markdown is simple[^1]

[^1]: Footnote text
```

```md id="adv2"
<div align="center">
Centered content
</div>
```

```md id="adv3"
<details>
<summary>Click to expand</summary>

Hidden content

</details>
```

---

## 📌 Emoji & Auto Links

```md id="em1"
:rocket:
:warning:
:white_check_mark:
```

Example

🚀 ⚠️ ✅

```md id="em2"
https://example.com
```
