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

| No. | Questions                                                                                                                                            |
| --- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What is the difference between classes and IDs in CSS?](#1-what-is-the-difference-between-classes-and-ids-in-css)                                   |
| 2   | [What is specificity and how does it work in CSS?](#2-what-is-specificity-and-how-does-it-work-in-css)                                               |
| 3   | [What is the Box Model in CSS?](#3-what-is-the-box-model-in-css)                                                                                     |
| 4   | [What are pseudo-classes and pseudo-elements in CSS?](#4-what-are-pseudo-classes-and-pseudo-elements-in-css)                                         |
| 5   | [How does position work in CSS (static, relative, absolute, fixed, sticky)?](#5-how-does-position-work-in-css)                                       |
| 6   | [What is the difference between em, rem, %, px, and vh/vw units?](#6-what-is-the-difference-between-em-rem-and-other-units)                          |
| 7   | [How does z-index work in CSS?](#7-how-does-z-index-work-in-css)                                                                                     |
| 8   | [What is the difference between inline, block, and inline-block elements?](#8-what-is-the-difference-between-inline-block-and-inline-block-elements) |
| 9   | [How do CSS Grid and Flexbox differ? When should you use each?](#9-how-do-css-grid-and-flexbox-differ)                                               |
| 10  | [What are media queries and how do you use them?](#10-what-are-media-queries-and-how-do-you-use-them)                                                |
| 11  | [What are the different types of CSS (inline, internal, external)?](#11-what-are-the-different-types-of-css)                                         |
| 12  | [How does inheritance work in CSS?](#12-how-does-inheritance-work-in-css)                                                                            |
| 13  | [What are the different combinators in CSS?](#13-what-are-the-different-combinators-in-css)                                                          |
| 14  | [What is the difference between visibility: hidden and display: none?](#14-what-is-the-difference-between-visibility-hidden-and-display-none)        |
| 15  | [What are CSS transitions and animations?](#15-what-are-css-transitions-and-animations)                                                              |
| 16  | [How do you center a div horizontally and vertically?](#16-how-do-you-center-a-div-horizontally-and-vertically)                                      |
| 17  | [What are the benefits of using CSS variables (custom properties)?](#17-what-are-the-benefits-of-using-css-variables)                                |
| 18  | [What are the most common browser compatibility issues in CSS?](#18-what-are-the-most-common-browser-compatibility-issues-in-css)                    |
| 19  | [What is the difference between min-width, max-width, and width?](#19-what-is-the-difference-between-min-width-max-width-and-width)                  |
| 20  | [What is specificity hierarchy and how to override styles correctly?](#20-what-is-specificity-hierarchy-and-how-to-override-styles-correctly)        |

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
