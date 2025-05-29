# CSS Interview Questions & Answers

<div align="center">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original-wordmark.svg" alt="CSS3 Logo" width="150" height="150"/>
    
  <p>A comprehensive collection of commonly asked CSS interview questions with detailed answers to help you ace your front-end developer interviews.</p>

[![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](CONTRIBUTING.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat)](http://makeapullrequest.com)

</div>

## 🚀 Introduction

This repository contains a curated list of CSS interview questions that are frequently asked in front-end developer interviews. Each question comes with a detailed explanation, code examples, and visual illustrations where applicable.

Whether you're preparing for your first front-end interview or looking to refresh your CSS knowledge, this resource aims to help you understand core CSS concepts and best practices.

## 🎯 How to Use This Repository

- Browse through the table of contents to find specific topics
- Study the explanations and examples for each question
- Practice implementing the concepts in your own code
- Contribute by adding new questions or improving existing answers

## Table of Contents

| No. | Questions                                                                                                                                                          |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1   | [What is the difference between classes and IDs in CSS?](#1-what-is-the-difference-between-classes-and-ids-in-css)                                                 |
| 2   | [What is specificity and how does it work in CSS?](#2-what-is-specificity-and-how-does-it-work-in-css)                                                             |
| 3   | [What is the Box Model in CSS?](#3-what-is-the-box-model-in-css)                                                                                                   |
| 4   | [What are pseudo-classes and pseudo-elements in CSS?](#4-what-are-pseudo-classes-and-pseudo-elements-in-css)                                                       |
| 5   | [How does position work in CSS (static, relative, absolute, fixed, sticky)?](#5-how-does-position-work-in-css)                                                     |
| 6   | [What is the difference between em, rem, %, px, and vh/vw units?](#6-what-is-the-difference-between-em-rem--px-and-vhvw-units-in-css)                              |
| 7   | [How does z-index work in CSS?](#7-how-does-z-index-work-in-css)                                                                                                   |
| 8   | [What is the difference between inline, block, and inline-block elements in CSS?](#8-what-is-the-difference-between-inline-block-and-inline-block-elements-in-css) |
| 9   | [How do CSS Grid and Flexbox differ? When should you use each?](#9-how-do-css-grid-and-flexbox-differ-when-should-you-use-each)                                    |
| 10  | [What are media queries and how do you use them?](#10-what-are-media-queries-and-how-do-you-use-them)                                                              |
| 11  | [What are the different types of CSS?](#11-what-are-the-different-types-of-css)                                                                                    |
| 12  | [How does inheritance work in CSS?](#12-how-does-inheritance-work-in-css)                                                                                          |
| 13  | [What are the different combinators in CSS?](#13-what-are-the-different-combinators-in-css)                                                                        |
| 14  | [What is the difference between visibility: hidden and display: none in CSS?](#14-what-is-the-difference-between-visibility-hidden-and-display-none-in-css)        |
| 15  | [What are CSS transitions and animations?](#15-what-are-css-transitions-and-animations)                                                                            |
| 16  | [How do you center a div horizontally and vertically?](#16-how-do-you-center-a-div-horizontally-and-vertically)                                                    |
| 17  | [What are the benefits of using CSS variables (custom properties)?](#17-what-are-the-benefits-of-using-css-variables-custom-properties)                            |
| 18  | [What are the most common browser compatibility issues in CSS?](#18-what-are-the-most-common-browser-compatibility-issues-in-css)                                  |
| 19  | [What is the difference between min-width, max-width, and width?](#19-what-is-the-difference-between-min-width-max-width-and-width)                                |
| 20  | [What is specificity hierarchy and how to override styles correctly?](#20-what-is-specificity-hierarchy-and-how-to-override-styles-correctly)                      |

---

Would you like me to begin writing detailed answers for each question as well?

## 1. What is the difference between classes and IDs in CSS?

**Classes (`.class`)** and **IDs (`#id`)** are both selectors in CSS used to apply styles to HTML elements, but they serve different purposes and have different rules.

---

#### 🔹 1. **Syntax**

- **Class:** Starts with a dot (`.`)
  ```css
  .button {
    background-color: blue;
  }
  ```
- **ID:** Starts with a hash (`#`)
  ```css
  #submit {
    background-color: green;
  }
  ```

---

#### 🔹 2. **Usage**

- **Class:** Can be reused on **multiple elements**.
  ```html
  <div class="box"></div>
  <p class="box"></p>
  ```
- **ID:** Should be **unique** per page — only **one element** should have a given ID.
  ```html
  <div id="header"></div>
  ```

---

#### 🔹 3. **Specificity**

- **IDs** have **higher specificity** than classes.

  - If both a class and ID target the same element, the ID’s styles will apply.

  ```css
  .box {
    color: red;
  }

  #box {
    color: blue;
  }
  ```

  ```html
  <div id="box" class="box">Text</div>
  <!-- Will be blue -->
  ```

---

#### 🔹 4. **JavaScript Access**

- **ID:**
  ```js
  document.getElementById("header");
  ```
- **Class:**
  ```js
  document.querySelector(".button");
  document.getElementsByClassName("button");
  ```

---

#### ✅ Summary Table

| Feature     | Class (`.class`)                             | ID (`#id`)       |
| ----------- | -------------------------------------------- | ---------------- |
| Syntax      | `.classname`                                 | `#idname`        |
| Reusability | Can be used multiple times                   | Should be unique |
| Specificity | Lower                                        | Higher           |
| JavaScript  | `getElementsByClassName`, `querySelectorAll` | `getElementById` |

---

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## 2. What is specificity and how does it work in CSS?

**Specificity** in CSS determines which styles are applied to an element when multiple conflicting rules target the same element. It is a scoring system that calculates how "specific" a selector is, and the more specific a selector, the higher its priority in applying styles.

#### 🔹 **Specificity Calculation**

Specificity is calculated based on four parts:

1. **Inline styles** (highest priority)
2. **IDs**
3. **Classes, attributes, and pseudo-classes**
4. **Elements and pseudo-elements** (lowest priority)

---

#### 🔹 **How Specificity is Measured**

Specificity is often represented as a four-part value:

- **Inline styles**: Represented by a value like `a=1`
- **ID selectors**: Represented by a value like `b=1`
- **Class selectors, pseudo-classes, and attribute selectors**: Represented by `c=1`
- **Element selectors and pseudo-elements**: Represented by `d=1`

Each part of the selector contributes to its specificity score. Here’s how it works:

| Selector Type      | Specificity Calculation |
| ------------------ | ----------------------- |
| Inline styles      | `1, 0, 0, 0`            |
| ID selector        | `0, 1, 0, 0`            |
| Class selector     | `0, 0, 1, 0`            |
| Element selector   | `0, 0, 0, 1`            |
| Multiple selectors | Sum of individual parts |

For example:

- **`#header`** has a specificity of `0, 1, 0, 0` (one ID).
- **`.nav`** has a specificity of `0, 0, 1, 0` (one class).
- **`div`** has a specificity of `0, 0, 0, 1` (one element).

---

#### 🔹 **How Does It Work?**

1. When two conflicting CSS rules apply to the same element, the browser checks their specificity.
2. The rule with the **higher specificity** wins and overrides the other.
3. If two rules have the same specificity, the rule that appears last in the stylesheet wins (this is called the **cascade**).

---

#### 🔹 **Examples**

1. **Element selector vs Class selector:**

   ```css
   p {
     color: red; /* Specificity: 0, 0, 0, 1 */
   }

   .text {
     color: blue; /* Specificity: 0, 0, 1, 0 */
   }
   ```

   Here, `.text` will apply because classes have higher specificity than element selectors.

2. **Class selector vs ID selector:**

   ```css
   .header {
     font-size: 20px; /* Specificity: 0, 0, 1, 0 */
   }

   #main-header {
     font-size: 30px; /* Specificity: 0, 1, 0, 0 */
   }
   ```

   In this case, `#main-header` will win because IDs have higher specificity than classes.

---

#### 🔹 **Important Notes**

- **Inline styles**: If an element has an inline style (e.g., `style="color: green;"`), it will override any styles in the external stylesheet because it has the highest specificity (`1, 0, 0, 0`).

  Example:

  ```html
  <div id="header" style="color: green;">Hello</div>
  ```

- **The Universal Selector (`*`)**: The universal selector (`*`) has the lowest specificity (`0, 0, 0, 0`) and is often overridden by other selectors.

  Example:

  ```css
  * {
    color: yellow;
  }

  .highlight {
    color: blue; /* This will apply because of higher specificity */
  }
  ```

---

#### ✅ **Summary Table**

| Selector Type      | Specificity Example | Specificity Value |
| ------------------ | ------------------- | ----------------- |
| Inline styles      | `<div style="...">` | `1, 0, 0, 0`      |
| ID selector        | `#header`           | `0, 1, 0, 0`      |
| Class selector     | `.nav`              | `0, 0, 1, 0`      |
| Attribute selector | `[type="text"]`     | `0, 0, 1, 0`      |
| Element selector   | `div`               | `0, 0, 0, 1`      |

---

Specificity is essential to understand in CSS to avoid unexpected results in your styling. By using it wisely, you can ensure your styles apply as intended.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## 3. What is the Box Model in CSS?

The **CSS Box Model** is the fundamental concept used to understand how elements are rendered on a web page. Every HTML element is considered a rectangular box, and the box model describes how the element’s size is calculated and how its space is occupied, including padding, borders, and margins.

---

### 🧱 **Box Model Structure**

The box model consists of the following parts (from innermost to outermost):

```
+-------------------------------+
|          Margin               |
|  +------------------------+   |
|  |        Border          |   |
|  |  +------------------+  |   |
|  |  |     Padding       |  |  |
|  |  |  +------------+   |  |  |
|  |  |  |  Content    |   |  |  |
|  |  |  +------------+   |  |  |
|  |  +------------------+  |  |
|  +------------------------+  |
+-------------------------------+
```

---

### 🔹 1. **Content**

- The actual text, image, or other content of the element.
- You can control the width and height using `width` and `height` properties.

### 🔹 2. **Padding**

- The space **between the content and the border**.
- It increases the clickable or visible area inside an element.
- Controlled using `padding`, `padding-top`, `padding-right`, etc.

### 🔹 3. **Border**

- The line surrounding the padding (and content).
- Controlled using `border`, `border-width`, `border-style`, `border-color`.

### 🔹 4. **Margin**

- The space **outside the border** that separates the element from others.
- Controlled using `margin`, `margin-top`, `margin-right`, etc.

---

### 🧮 **Box Model Calculation**

By default (`box-sizing: content-box`):

```plaintext
Element Total Width  = content width + left/right padding + left/right border + left/right margin
Element Total Height = content height + top/bottom padding + top/bottom border + top/bottom margin
```

For example:

```css
width: 200px;
padding: 10px;
border: 2px solid black;
margin: 5px;
```

Total width = 200 + 10 + 10 + 2 + 2 + 5 + 5 = **234px**

---

### 🔁 `box-sizing` Property

You can change how the box model is calculated using `box-sizing`:

- **`content-box`** (default): Width/height includes _only_ the content.
- **`border-box`**: Width/height includes _content + padding + border_.

Example:

```css
* {
  box-sizing: border-box;
}
```

This is commonly used to make layout calculations easier and more predictable.

---

### ✅ **Why It Matters**

- Understanding the box model helps prevent layout issues.
- It’s essential when positioning, aligning, or sizing elements.
- Affects responsive design, spacing, and performance.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## 4. What are Pseudo-Classes and Pseudo-Elements in CSS?

**Pseudo-classes** and **pseudo-elements** are powerful CSS features that allow you to style elements based on their state or to target parts of elements that are not explicitly in the DOM.

---

## 🔹 Pseudo-Classes

A **pseudo-class** is used to define the **special state of an element**—such as when it’s hovered, visited, or its position among siblings.

### ✅ Common Pseudo-Classes:

| Pseudo-Class     | Description                                              |
| ---------------- | -------------------------------------------------------- |
| `:hover`         | Applies styles when the user hovers over an element      |
| `:focus`         | Applies styles when the element is focused (e.g., input) |
| `:visited`       | Applies to links that have been visited                  |
| `:nth-child(n)`  | Selects the nth child of a parent                        |
| `:first-child`   | Selects the first child of a parent                      |
| `:last-child`    | Selects the last child of a parent                       |
| `:checked`       | Applies to checked checkboxes or radio buttons           |
| `:disabled`      | Applies to disabled form elements                        |
| `:not(selector)` | Selects elements that do **not** match a selector        |

### 🔍 Example:

```css
button:hover {
  background-color: blue;
  color: white;
}

li:nth-child(2) {
  color: red;
}
```

---

## 🔸 Pseudo-Elements

A **pseudo-element** allows you to **style specific parts of an element** without adding additional HTML.

### ✅ Common Pseudo-Elements:

| Pseudo-Element   | Description                                            |
| ---------------- | ------------------------------------------------------ |
| `::before`       | Inserts content before the content of the element      |
| `::after`        | Inserts content after the content of the element       |
| `::first-line`   | Targets the first line of a block of text              |
| `::first-letter` | Targets the first letter of a block of text            |
| `::selection`    | Targets the portion of an element selected by the user |
| `::placeholder`  | Styles the placeholder text in input fields            |

### 🔍 Example:

```css
p::first-line {
  font-weight: bold;
}

h1::before {
  content: "🔥 ";
}

input::placeholder {
  color: gray;
  font-style: italic;
}
```

---

## 🔑 Key Differences

| Feature | Pseudo-Class                  | Pseudo-Element                             |
| ------- | ----------------------------- | ------------------------------------------ |
| Targets | Element state or relationship | Part of an element’s content               |
| Syntax  | Uses a single colon `:`       | Uses two colons `::` (CSS3 recommendation) |
| Example | `a:hover`, `li:first-child`   | `p::first-line`, `h1::after`               |

> Note: Older browsers may still support pseudo-elements with a single colon (`:before`, `:after`), but `::` is the modern standard.

---

### 🧠 Summary

- **Pseudo-classes** = _Dynamic states_ (hover, focus, nth-child, etc.)
- **Pseudo-elements** = _Parts of elements_ (before, after, first-letter, etc.)
- Together, they make CSS much more expressive without needing extra HTML markup.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## 5. How Does `position` Work in CSS?

The `position` property in CSS defines how an element is positioned in a document. It also determines how its `top`, `right`, `bottom`, and `left` properties affect its placement.

---

### 🔹 1. `static` (Default)

- This is the **default** position for every element.
- The element is positioned according to the normal **document flow**.
- **`top`, `right`, `bottom`, `left` have no effect.**

```css
div {
  position: static;
}
```

---

### 🔹 2. `relative`

- The element is positioned **relative to its normal position**.
- Offsets with `top`, `left`, etc., will **move the element**, but **it still takes up its original space**.

```css
div {
  position: relative;
  top: 20px; /* Moves the element 20px down */
  left: 10px; /* Moves the element 10px to the right */
}
```

---

### 🔹 3. `absolute`

- The element is positioned **relative to the nearest positioned ancestor** (anything not `static`).
- If no such ancestor exists, it will be **relative to the `<html>` (viewport)**.
- It is **removed from the normal document flow** (doesn’t take up space).

```css
div {
  position: absolute;
  top: 50px;
  left: 100px;
}
```

---

### 🔹 4. `fixed`

- The element is **fixed to the viewport** and does **not move** when the page is scrolled.
- Commonly used for headers, footers, or floating buttons.

```css
div {
  position: fixed;
  bottom: 10px;
  right: 10px;
}
```

---

### 🔹 5. `sticky` (Hybrid)

- The element **behaves like `relative`** until it hits a scroll threshold, then it **sticks** like `fixed`.
- Requires a `top`, `left`, etc., to trigger the sticking.
- Must have a scrollable parent.

```css
div {
  position: sticky;
  top: 0;
}
```

---

### 🔁 Summary Table

| Value      | Relative to                             | Stays in flow?       | Scrolls with page? | Notes                                               |
| ---------- | --------------------------------------- | -------------------- | ------------------ | --------------------------------------------------- |
| `static`   | Normal flow                             | ✅ Yes               | ✅ Yes             | Default value                                       |
| `relative` | Itself (normal pos)                     | ✅ Yes               | ✅ Yes             | Moves visually, keeps space                         |
| `absolute` | Nearest positioned ancestor or viewport | ❌ No                | ❌ No              | Great for dropdowns, tooltips                       |
| `fixed`    | Viewport                                | ❌ No                | ❌ No              | Always visible; use for sticky navbars/buttons      |
| `sticky`   | Scroll container                        | ✅ Yes (until stuck) | Depends            | Good for headers that should stay visible on scroll |

---

### 📌 Visual Example

You might imagine a sticky header like this:

```css
header {
  position: sticky;
  top: 0;
  background: white;
  z-index: 100;
}
```

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## 6. What is the Difference Between `em`, `rem`, `%`, `px`, and `vh`/`vw` Units in CSS?

CSS offers multiple **unit types** for defining sizes (like font size, padding, width, etc.), and choosing the right one affects **responsiveness, maintainability, and consistency**.

---

### ✅ Absolute vs Relative Units

| Type         | Units                        | Description                         |
| ------------ | ---------------------------- | ----------------------------------- |
| **Absolute** | `px`, `pt`, `cm`, `mm`, etc. | Fixed size, doesn’t scale           |
| **Relative** | `em`, `rem`, `%`, `vh`, `vw` | Size depends on context/environment |

---

### 📏 1. `px` – Pixels (Absolute Unit)

- **Fixed unit** – does not scale with parent or root.
- Best used for **precise control** but lacks responsiveness.

```css
font-size: 16px;
```

🔸 **Pros**: Predictable  
🔸 **Cons**: Not scalable; not responsive to screen size or accessibility settings.

---

### 🔠 2. `em` – Relative to Parent Element

- 1 `em` equals the **font size of the current element's parent**.
- Multiplies if nested (can lead to unintended growth).

```css
font-size: 2em; /* 2 times the parent's font size */
```

🔸 **Common use**: Spacing, padding, font sizes.  
🔸 **Watch out**: In deeply nested elements, sizes can **compound**.

---

### 🧩 3. `rem` – Relative to Root Element (`html`)

- 1 `rem` equals the **font size of the `<html>` element**.
- Safer than `em` for consistent scaling across components.

```css
font-size: 1.5rem; /* 1.5 times the root font size */
```

🔸 **Great for**: Scalable and consistent design systems.  
🔸 **Common base**: `html { font-size: 16px; }`

---

### 📐 4. `%` – Percentage

- Depends on the **parent element’s dimension** (for width, height, font-size, etc.).

```css
width: 50%; /* Half of the parent’s width */
font-size: 120%; /* 120% of parent font size */
```

🔸 **Responsive** but relative to parent container.  
🔸 **Context-sensitive** – behaves differently based on the property.

---

### 📱 5. `vh` / `vw` – Viewport Height / Width

- `1vh` = 1% of **viewport height**, `1vw` = 1% of **viewport width**.
- Useful for full-screen layouts, responsive sections.

```css
height: 100vh; /* Full height of the screen */
width: 100vw; /* Full width of the screen */
```

🔸 **Perfect for**: Modals, full-screen sections, hero banners.  
🔸 **Watch out**: On mobile browsers, can be affected by browser UI.

---

### 🔁 Summary Table

| Unit  | Relative To             | Best Used For                | Notes                                |
| ----- | ----------------------- | ---------------------------- | ------------------------------------ |
| `px`  | Fixed size              | Precise spacing, borders     | Not responsive                       |
| `em`  | Parent’s font-size      | Component-relative sizing    | Can compound in nested elements      |
| `rem` | Root (`html`) font-size | Global consistency           | Predictable, scalable design systems |
| `%`   | Parent element          | Width, height, font scaling  | Context-dependent                    |
| `vh`  | Viewport height         | Full-height sections, modals | 100vh = full screen height           |
| `vw`  | Viewport width          | Full-width layouts           | 100vw = full screen width            |

---

### ✅ Pro Tip:

Set base font size on `html` using `px`, then use `rem` throughout for scalable, accessible UI.

```css
html {
  font-size: 16px; /* 1rem = 16px */
}
```

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## 7. How Does `z-index` Work in CSS?

The `z-index` property in CSS controls the **stacking order** of elements **along the Z-axis** (front to back). It determines which element appears **in front of** or **behind** others when they overlap.

---

### 🔢 Basic Concept

- Elements with **higher `z-index` values** are displayed **on top** of elements with lower values.
- The default value is `auto` (treated as `0` unless specified).
- **Only works on positioned elements** (`position: relative`, `absolute`, `fixed`, or `sticky`).

```css
.element1 {
  position: absolute;
  z-index: 1;
}

.element2 {
  position: absolute;
  z-index: 2; /* This will appear on top of .element1 */
}
```

---

### 🧱 Stack Context

A **stacking context** is formed when an element meets certain conditions, such as:

- It has a `position` and a `z-index` other than `auto`.
- It has `opacity < 1`, `transform`, `filter`, `perspective`, `clip-path`, etc.

**Each stacking context is independent**, so `z-index` only compares elements within the **same context**.

```css
.parent {
  position: relative;
  z-index: 10; /* Creates a stacking context */
}

.child {
  position: relative;
  z-index: 9999; /* Only highest within this parent, not the page */
}
```

---

### 🧠 z-index in Layers

Imagine layers of paper stacked on a table:

```
z-index: 3   ⬅️ Top layer
z-index: 2
z-index: 1
z-index: 0   ⬅️ Default layer
```

---

### ⚠️ Common Gotchas

- `z-index` **does not work** on statically positioned elements (`position: static`).
- Nesting a high `z-index` element inside a low `z-index` stacking context **limits visibility**.
- Overuse can cause **unexpected overlaps**—manage with minimal and meaningful values.

---

### ✅ Best Practices

- Use `z-index` sparingly and intentionally.
- Try to **keep values small** (`1`, `10`, `100`) rather than `9999`.
- Understand and isolate **stacking contexts** for complex UI.

---

### 🧪 Example

```html
<div class="box red"></div>
<div class="box blue"></div>
```

```css
.box {
  width: 100px;
  height: 100px;
  position: absolute;
}

.red {
  background: red;
  top: 0;
  left: 0;
  z-index: 1;
}

.blue {
  background: blue;
  top: 20px;
  left: 20px;
  z-index: 2; /* This will be on top */
}
```

---

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## 8. What is the Difference Between `inline`, `block`, and `inline-block` Elements in CSS?

These display values control how elements behave in the **layout flow** of a webpage. Understanding them is crucial for structuring and styling HTML effectively.

---

### 🔹 `inline`

- **Does NOT start on a new line**.
- Only takes up **as much width as necessary**.
- Cannot set `width` or `height`.
- Margins and paddings only apply **horizontally** (top/bottom may not push other content).

📌 **Examples**: `<span>`, `<a>`, `<strong>`, `<em>`

```html
<span>I am inline</span>
```

---

### 🔸 `block`

- **Starts on a new line** (takes full width by default).
- Respects `width`, `height`, `margin`, and `padding`.
- Stacks vertically.

📌 **Examples**: `<div>`, `<p>`, `<h1>` to `<h6>`, `<section>`

```html
<div>I am block</div>
```

---

### 🔹 `inline-block`

- Behaves like `inline` in that it **does not break to a new line**, but:
- **Allows setting** `width`, `height`, `padding`, and `margin`.
- Useful for styling inline elements with box-like features.

📌 **Common use case**: Buttons, navigation links.

```html
<span style="display: inline-block; width: 100px;">Styled Inline</span>
```

---

### 🧪 Visual Comparison

| Property          | `inline`        | `block`        | `inline-block`  |
| ----------------- | --------------- | -------------- | --------------- |
| Starts new line   | ❌ No           | ✅ Yes         | ❌ No           |
| Sets width/height | ❌ No           | ✅ Yes         | ✅ Yes          |
| Box model support | Partial         | Full           | Full            |
| Layout direction  | Horizontal flow | Vertical stack | Horizontal flow |

---

### ✅ Use Cases

- Use `inline` for small content inside text (e.g., `<a>`, `<strong>`).
- Use `block` for sections, layouts, and full-width content.
- Use `inline-block` when you need an inline element that behaves like a block (e.g., styled buttons).

---

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## 9. How Do CSS Grid and Flexbox Differ? When Should You Use Each?

CSS **Grid** and **Flexbox** are both powerful layout systems, but they are designed for different use cases. Understanding their differences helps you choose the right tool for structuring layouts.

---

## 🆚 Core Differences

| Feature                | **Flexbox**                         | **Grid**                                                 |
| ---------------------- | ----------------------------------- | -------------------------------------------------------- |
| Layout direction       | One-dimensional (row **or** column) | Two-dimensional (rows **and** columns)                   |
| Content vs. Container  | Content-driven layout               | Container-driven layout                                  |
| Placement control      | Auto-placement only                 | Precise placement using row/column lines                 |
| Alignment capabilities | Powerful alignment for items        | Even more control over both axes                         |
| Overlapping content    | ❌ Not supported                    | ✅ Supported using grid lines                            |
| Browser support        | Widely supported (IE11+)            | Fully supported (IE11+ partial, full in modern browsers) |

---

## 📐 Flexbox

### ✅ Use When:

- Laying out **items in a row or column**.
- You need **dynamic sizing and alignment**.
- You're building a **navbar**, **button group**, **cards**, etc.

### 🔧 Example:

```css
.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
```

---

## 🧮 CSS Grid

### ✅ Use When:

- You need to create **complex layouts** (e.g., dashboard, magazine-style).
- You want **explicit row and column control**.
- You're building **grids**, **overlapping areas**, or **page sections**.

### 🔧 Example:

```css
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 20px;
}
```

---

## 🧠 Think of It Like:

- **Flexbox** = Good for **one axis** → flexible **lines**
- **Grid** = Best for **two axes** → structured **grids**

---

## 🛠 Combined Use

You can use **Flexbox inside Grid**, or vice versa:

- Grid for the **page layout**.
- Flexbox for **individual components** inside each grid item.

---

## ✅ Summary

| Use Case                       | Use Flexbox | Use Grid |
| ------------------------------ | ----------- | -------- |
| Horizontal navigation bar      | ✅          | ❌       |
| Sidebar + Main + Footer layout | ❌          | ✅       |
| Equal-width buttons or cards   | ✅          | ✅       |
| Overlapping content sections   | ❌          | ✅       |
| Responsive auto-fitting layout | ✅          | ✅       |

---

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## 10. What Are Media Queries and How Do You Use Them?

**Media queries** are a feature in CSS that allow you to apply styles based on the **characteristics of the user's device**, such as its screen size, resolution, orientation, or color capability. They are a core part of **responsive web design**.

---

## ✅ Why Use Media Queries?

They allow your web pages to:

- **Adapt** to different screen sizes (e.g., mobile, tablet, desktop).
- Provide a **better user experience** on all devices.
- Maintain **design consistency** without needing multiple stylesheets.

---

## 🧱 Syntax

```css
@media media-type and (condition) {
  /* CSS rules here */
}
```

- `media-type`: Usually `screen`, `print`, or `all`.
- `condition`: A **media feature** like `max-width`, `min-height`, etc.

---

## 📦 Common Examples

### 🔹 Basic: Adjust layout for mobile

```css
/* Default desktop styles */
.container {
  width: 1000px;
}

/* Override for screens smaller than 768px */
@media screen and (max-width: 768px) {
  .container {
    width: 100%;
  }
}
```

### 🔹 Multiple conditions

```css
@media screen and (min-width: 600px) and (max-width: 1024px) {
  body {
    font-size: 1.2rem;
  }
}
```

### 🔹 Orientation

```css
@media (orientation: landscape) {
  .video {
    width: 80%;
  }
}
```

---

## 🎯 Common Media Features

| Feature       | Description                       | Example                 |
| ------------- | --------------------------------- | ----------------------- |
| `max-width`   | Maximum screen width              | `max-width: 768px`      |
| `min-width`   | Minimum screen width              | `min-width: 480px`      |
| `orientation` | Screen orientation                | `orientation: portrait` |
| `resolution`  | Screen resolution (for retina/HD) | `min-resolution: 2dppx` |
| `hover`       | Detect if hover capability exists | `hover: hover`          |

---

## 🧠 Best Practices

- **Mobile-first**: Write base styles for mobile, then add media queries for larger screens using `min-width`.
- Keep breakpoints based on **content needs**, not device types (avoid hardcoding "iPhone" widths).
- Combine media queries into reusable **SCSS mixins** or utility classes if you're using preprocessors.

---

## 🧪 Example Use Case

```css
/* Mobile-first styles */
.navbar {
  flex-direction: column;
}

/* Desktop styles */
@media (min-width: 768px) {
  .navbar {
    flex-direction: row;
  }
}
```

---

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## 11. What Are the Different Types of CSS?

CSS (Cascading Style Sheets) can be applied to HTML documents in **three primary ways**:

---

## 1. ✅ Inline CSS

**Definition:** CSS styles applied directly to an HTML element using the `style` attribute.

**Example:**

```html
<p style="color: blue; font-size: 16px;">This is inline CSS.</p>
```

**Use Case:**

- Useful for **quick fixes** or **dynamic styling via JavaScript**.
- Not recommended for large-scale styling.

**Pros:**

- High specificity.
- Immediate effect on the element.

**Cons:**

- Hard to maintain.
- Violates separation of concerns (structure vs. style).
- Cannot be reused.

---

## 2. 🧩 Internal CSS (Embedded)

**Definition:** CSS written inside a `<style>` tag within the `<head>` of an HTML document.

**Example:**

```html
<head>
  <style>
    p {
      color: green;
    }
  </style>
</head>
<body>
  <p>This is internal CSS.</p>
</body>
```

**Use Case:**

- Good for **single-page styling** or **testing** styles locally.

**Pros:**

- Keeps styles in one place within the HTML.
- No extra HTTP request needed.

**Cons:**

- Not reusable across multiple pages.
- Increases HTML file size.

---

## 3. 📦 External CSS

**Definition:** CSS written in a separate `.css` file and linked to the HTML document using the `<link>` tag.

**Example:**

```html
<head>
  <link rel="stylesheet" href="styles.css" />
</head>
```

**styles.css**

```css
p {
  color: red;
}
```

**Use Case:**

- Best for **large websites** with multiple pages needing consistent styling.

**Pros:**

- Promotes **code reusability and maintainability**.
- Separates content from presentation.
- Can be cached by browsers for better performance.

**Cons:**

- Requires an extra HTTP request.
- Not ideal for email templates or highly dynamic content.

---

## 🧠 Summary Table

| Type     | Location      | Reusable | Best For                    | Drawbacks                      |
| -------- | ------------- | -------- | --------------------------- | ------------------------------ |
| Inline   | In HTML tags  | ❌       | Quick fixes, dynamic styles | Hard to maintain, not reusable |
| Internal | `<style>` tag | ❌       | One-page styles             | Not reusable across pages      |
| External | Separate file | ✅       | Full site styling           | Extra HTTP request required    |

---

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## 12. How Does Inheritance Work in CSS?

**Inheritance** in CSS refers to the mechanism by which some CSS properties applied to a parent element are automatically **passed down** (inherited) by its child elements.

---

### 🔍 Key Concepts

- **Not all properties are inherited by default.**
- Inherited properties are typically related to **text and font styling**.

---

### ✅ Commonly Inherited Properties

| Category     | Examples                                                                                                         |
| ------------ | ---------------------------------------------------------------------------------------------------------------- |
| Text & Fonts | `color`, `font-family`, `font-size`, `line-height`, `letter-spacing`, `word-spacing`, `text-align`, `visibility` |

---

### ❌ Non-Inherited Properties

Most **box model, layout, and positioning** properties are **not inherited** by default.

| Examples                                                                                            |
| --------------------------------------------------------------------------------------------------- |
| `margin`, `padding`, `border`, `width`, `height`, `display`, `position`, `background`, `box-shadow` |

---

### 🔧 Controlling Inheritance

You can explicitly control inheritance using:

#### `inherit`

Forces an element to inherit the value from its parent.

```css
div {
  color: inherit;
}
```

#### `initial`

Resets the property to its default initial value.

```css
div {
  color: initial;
}
```

#### `unset`

Resets the property to:

- Inherited value if it's normally inherited
- Initial value if it's not

```css
div {
  color: unset;
}
```

---

### 🧪 Example

```html
<style>
  body {
    color: navy;
    font-family: Arial, sans-serif;
  }
  h1 {
    color: inherit;
  }
</style>

<body>
  <h1>This text will be navy and Arial.</h1>
</body>
```

In this example:

- `body` sets the color and font-family.
- `h1` inherits the color from `body` because we used `color: inherit`.

---

### 🧠 Summary

- CSS inheritance mimics real-world inheritance: child elements inherit styles from parents.
- Only certain properties (mainly text-related) are inherited by default.
- You can explicitly **control** inheritance with `inherit`, `initial`, and `unset`.

---

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## 13. What Are the Different Combinators in CSS?

**Combinators** in CSS define relationships between selectors. They allow you to apply styles to elements **based on their relationship** to other elements in the DOM tree.

There are **4 main combinators** in CSS:

---

### 1. **Descendant Combinator (`space`)**

**Syntax**: `A B`
**Selects** all elements `B` that are **descendants** (children, grandchildren, etc.) of element `A`.

```css
div p {
  color: blue;
}
```

> Selects all `<p>` elements inside any `<div>`.

---

### 2. **Child Combinator (`>`)**

**Syntax**: `A > B`
**Selects** all elements `B` that are **direct children** of element `A`.

```css
ul > li {
  list-style-type: square;
}
```

> Only styles `<li>` elements that are **immediate children** of `<ul>`.

---

### 3. **Adjacent Sibling Combinator (`+`)**

**Syntax**: `A + B`
**Selects** element `B` that is the **next sibling** of element `A`.

```css
h2 + p {
  color: green;
}
```

> Styles the **first `<p>` immediately after** an `<h2>`.

---

### 4. **General Sibling Combinator (`~`)**

**Syntax**: `A ~ B`
**Selects** all elements `B` that are **siblings** of `A` and come **after** it in the DOM.

```css
h2 ~ p {
  font-style: italic;
}
```

> Styles **all `<p>` elements after** an `<h2>` (not just the next one).

---

### ✅ Summary Table

| Combinator  | Selector Example | Description                             |
| ----------- | ---------------- | --------------------------------------- |
| ` ` (space) | `A B`            | All descendants of `A`                  |
| `>`         | `A > B`          | Direct children of `A`                  |
| `+`         | `A + B`          | First sibling `B` immediately after `A` |
| `~`         | `A ~ B`          | All siblings `B` after `A`              |

---

### 🧠 Pro Tip

Use combinators carefully to **avoid performance issues**, especially descendant selectors (`A B`) which are more **costly** for the browser to match.

---

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## 14. What is the Difference Between `visibility: hidden` and `display: none` in CSS?

Both `visibility: hidden` and `display: none` are used to **hide elements**, but they behave very differently:

---

### ✅ `visibility: hidden`

- **Hides** the element, but it **still takes up space** in the layout.
- The element becomes **invisible**, but the browser **reserves its space** on the page.

```css
.hidden {
  visibility: hidden;
}
```

#### 🔎 Example:

```html
<p>This is visible</p>
<p class="hidden">This is hidden</p>
<p>This is also visible</p>
```

> You'll see a blank space where the hidden paragraph would be.

---

### ✅ `display: none`

- Completely **removes the element** from the layout.
- The element is **not visible** and **does not take up any space**.

```css
.removed {
  display: none;
}
```

#### 🔎 Example:

```html
<p>This is visible</p>
<p class="removed">This is removed</p>
<p>This is also visible</p>
```

> There is **no space** where the removed paragraph was—it's like it doesn’t exist.

---

### 📊 Comparison Table

| Property             | Visibility | Space in Layout | Can be Interacted With |
| -------------------- | ---------- | --------------- | ---------------------- |
| `visibility: hidden` | ❌ Hidden  | ✅ Yes          | ❌ No                  |
| `display: none`      | ❌ Hidden  | ❌ No           | ❌ No                  |

---

### 🧠 Use Cases

- Use `visibility: hidden` if you want to **keep layout structure** intact.
- Use `display: none` when you want to **completely remove** the element from view and layout.

---

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## 15. What Are CSS Transitions and Animations?

CSS **transitions** and **animations** both add visual effects to elements, but they differ in how and when the effects occur.

---

## 🔄 CSS Transitions

**Transitions** allow property changes in CSS values to occur **smoothly over a duration**, rather than instantly.

### ✅ Syntax:

```css
selector {
  transition: property duration timing-function delay;
}
```

### 🧪 Example:

```css
.button {
  background-color: blue;
  transition: background-color 0.3s ease-in-out;
}

.button:hover {
  background-color: green;
}
```

> When you hover over the button, the background color gradually changes from blue to green.

### 🧠 Notes:

- Requires a **trigger** (e.g., `:hover`, `:focus`, `:checked`, or JavaScript class change).
- Best for simple interactions.

---

## 🌀 CSS Animations

**Animations** define more complex effects that can be **automated** using keyframes. They don't require user interaction to begin.

### ✅ Syntax:

```css
@keyframes slideIn {
  from {
    transform: translateX(-100%);
  }
  to {
    transform: translateX(0);
  }
}

.box {
  animation: slideIn 1s ease-in-out forwards;
}
```

### 🧠 Notes:

- Use `@keyframes` to define intermediate steps.
- Can run **automatically**, **repeat**, **pause**, or **alternate**.
- More flexible and powerful than transitions.

---

### 📊 Comparison Table

| Feature    | Transitions                          | Animations                               |
| ---------- | ------------------------------------ | ---------------------------------------- |
| Trigger    | Requires user action or class change | Can run automatically on load            |
| Keyframes  | ❌ Not required                      | ✅ Required for complex animations       |
| Complexity | Simple property changes              | Multiple steps and directions possible   |
| Looping    | ❌ No (without JavaScript)           | ✅ Yes (via `animation-iteration-count`) |

---

### 🎯 When to Use

- Use **transitions** for simple effects like hovers, toggles, or fades.
- Use **animations** for complex, looping, or staged visual effects like loaders, sliders, or moving elements.

---

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## 16. How Do You Center a `<div>` Horizontally and Vertically?

There are **several ways** to center a `<div>` horizontally and vertically depending on your layout needs and CSS method. Here's a breakdown of the **most common and reliable methods**:

---

## ✅ 1. **Flexbox (Recommended for Modern Layouts)**

```css
.parent {
  display: flex;
  justify-content: center; /* horizontal */
  align-items: center; /* vertical */
  height: 100vh; /* or any height */
}
```

```html
<div class="parent">
  <div class="child">Centered</div>
</div>
```

> **Best for:** Responsive layouts, dynamic content.

---

## ✅ 2. **Grid Layout**

```css
.parent {
  display: grid;
  place-items: center; /* shorthand for align-items and justify-items */
  height: 100vh;
}
```

```html
<div class="parent">
  <div class="child">Centered</div>
</div>
```

> **Best for:** Clean and modern centering using CSS Grid.

---

## ✅ 3. **Absolute Positioning + Transform**

```css
.parent {
  position: relative;
  height: 100vh;
}

.child {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

> **Best for:** Pixel-perfect centering when parent has a fixed size.

---

## ✅ 4. **Margin Auto (Horizontal Only)**

```css
.child {
  width: 200px;
  margin: 0 auto;
}
```

> **Note:** This only **centers horizontally**. To center vertically, you'd need other techniques.

---

## ✅ 5. **Table-Cell (Old-School)**

```css
.parent {
  display: table;
  height: 100vh;
  width: 100%;
}

.child {
  display: table-cell;
  vertical-align: middle;
  text-align: center;
}
```

> **Legacy support:** Works even in older browsers like IE8.

---

### 🧠 Summary Table

| Method               | Horizontal | Vertical | Notes                        |
| -------------------- | ---------- | -------- | ---------------------------- |
| Flexbox              | ✅         | ✅       | Modern, flexible, responsive |
| Grid                 | ✅         | ✅       | Clean syntax, powerful       |
| Absolute + Transform | ✅         | ✅       | Good for fixed-size content  |
| Margin Auto          | ✅         | ❌       | Only centers horizontally    |
| Table/Table-cell     | ✅         | ✅       | Works in legacy browsers     |

---

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## 17. What Are the Benefits of Using CSS Variables (Custom Properties)?

CSS Variables, also known as **custom properties**, are declared using the `--` syntax and accessed with the `var()` function. Example:

```css
:root {
  --main-color: #3498db;
}
.element {
  color: var(--main-color);
}
```

---

### 🌟 Benefits of Using CSS Variables

#### 1. **Reusability**

Define once, use anywhere.

```css
--primary-font: "Roboto", sans-serif;
```

You can apply the same font across components without repeating the value.

---

#### 2. **Easier Maintenance**

Update a single variable to reflect changes across the entire stylesheet.

```css
:root {
  --spacing: 1rem;
}
```

Change `--spacing` to `1.5rem` and all related paddings/margins update instantly.

---

#### 3. **Dynamic Theming**

You can change variable values at runtime using JavaScript or media queries for **dark mode**, user themes, etc.

```css
@media (prefers-color-scheme: dark) {
  :root {
    --background-color: #000;
    --text-color: #fff;
  }
}
```

---

#### 4. **Component-Level Scope**

Variables can be scoped to specific elements or components:

```css
.card {
  --card-color: #f5f5f5;
  background: var(--card-color);
}
```

This isolates styling logic within components.

---

#### 5. **Works with JavaScript**

You can read and update CSS variables dynamically via JS:

```js
document.documentElement.style.setProperty("--main-color", "#e74c3c");
```

---

#### 6. **Reduces Repetition**

You avoid repeating the same values across your CSS, making the code DRY (Don’t Repeat Yourself).

---

### 🚫 CSS Variables vs. Preprocessor Variables (like Sass)

| Feature                    | CSS Variables | Sass/LESS Variables |
| -------------------------- | ------------- | ------------------- |
| Runtime capability         | ✅ Yes        | ❌ No               |
| JavaScript interaction     | ✅ Yes        | ❌ No               |
| Media query responsiveness | ✅ Yes        | ❌ No               |
| Requires build tools       | ❌ No         | ✅ Yes              |

---

### 🧠 Summary

CSS variables provide:

- **Consistency**
- **Maintainability**
- **Flexibility**
- **Powerful dynamic theming**
- **Better developer experience**

---

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## 18. What Are the Most Common Browser Compatibility Issues in CSS?

Browser compatibility issues occur when CSS styles behave differently across browsers like Chrome, Firefox, Safari, Edge, or older versions of Internet Explorer. These inconsistencies can lead to unexpected layouts or features not working as intended.

---

### 🧩 Common CSS Compatibility Issues

#### 1. **Unsupported or Partially Supported Features**

Some CSS features are not supported by all browsers or require prefixes.

- ❌ Example: `backdrop-filter`, `scroll-behavior`, `aspect-ratio`
- ✅ Solution: Use [Can I use](https://caniuse.com/) to check support and provide fallbacks or polyfills.

```css
.element {
  backdrop-filter: blur(10px); /* Not supported in all browsers */
}
```

---

#### 2. **Vendor Prefixes**

Some CSS properties require browser-specific prefixes.

```css
.element {
  -webkit-transform: rotate(45deg); /* Chrome, Safari */
  -ms-transform: rotate(45deg); /* IE */
  transform: rotate(45deg); /* Standard */
}
```

🛠 Tools like Autoprefixer can automate this process.

---

#### 3. **Flexbox and Grid Compatibility**

- Older browsers may **misinterpret flex or grid layouts**.
- Different behaviors in IE11 for `min-height`, `flex-shrink`, etc.

✅ Solution: Use modern layout techniques with known fallbacks.

---

#### 4. **Default Styling Differences**

Each browser has different default styles for HTML elements like `<input>`, `<button>`, `<ul>`, etc.

✅ Solution: Use a **CSS reset** or **normalize.css** to reduce inconsistencies.

---

#### 5. **Box Model Differences (in older IE versions)**

IE used a different box model in older versions where `padding` and `border` affected width differently.

✅ Solution: Always set:

```css
* {
  box-sizing: border-box;
}
```

---

#### 6. **Form Element Styling**

Input types (`range`, `date`, `file`, etc.) are rendered differently across browsers and can be hard to style consistently.

✅ Solution: Apply minimal styling or use JS libraries for consistent UIs.

---

#### 7. **Z-Index Bugs in IE/Edge**

Z-index stacking context behaves unexpectedly in older IE/Edge versions when elements are not positioned correctly.

✅ Solution: Always define a `position` (relative, absolute, etc.) before applying `z-index`.

---

#### 8. **Media Queries & Viewport Units**

- `vh`, `vw` units behave inconsistently on mobile browsers.
- Media queries may not match perfectly across devices.

✅ Solution: Test on actual devices and use responsive units with caution.

---

### ✅ Tips to Avoid Compatibility Issues

- Use [Autoprefixer](https://autoprefixer.github.io/) or PostCSS.
- Check [Can I use](https://caniuse.com/) before using cutting-edge CSS.
- Use feature queries (`@supports`) to provide safe fallbacks:

```css
@supports (display: grid) {
  .container {
    display: grid;
  }
}
```

- Test on real browsers (not just Chrome).
- Use Normalize.css or CSS Reset to create a consistent baseline.

---

### 🧠 Summary

| Issue Type             | Solution                           |
| ---------------------- | ---------------------------------- |
| Unsupported Properties | Check support + provide fallback   |
| Vendor Prefixes        | Use Autoprefixer                   |
| Layout Differences     | Use standard practices (Flex/Grid) |
| Default Browser Styles | Use Normalize or Reset             |
| Form Styling           | Minimal styling or libraries       |

---

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>
