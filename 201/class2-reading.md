# **Class02 Reading Notes:**
---
---
---

## [**Introduction to HTML:**](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML)
---

## [**HTML Text Fundamentals:**](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/HTML_text_fundamentals)
---

## [**HTML Advanced Text Formatting:**](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting)

* Why is it important to use semantic elements in our HTML?

```
It provides meaning to our content. This will help other developers that need to understand our code and improve a webpages SEO score.
```

* How many levels of headings are there in HTML?

```html
<!--6 levels of heading-->
<h1></h1>
<h2></h2>
<h3></h3>
<h4></h4>
<h5></h5>
<h6></h6>
```

* What are some uses for the sup and sub elements

```html
<sub>Are used to make subtext.</sub>
<sup>Are used to make supertext.</sup>
```

* When using the abbr element, what attribute must be added to provide the full expansion of term?

```html
<p>The abbr element is to be used with abbreviations or acronyms and contain a title to label all subsiquent abbreviations of the same. <abbr title="Hypertext Markup Language">HTML</abbr></p>
```

---
---
## [**How CSS is Structure:**](https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps/How_CSS_is_structured)

* What are ways to apply CSS to our HTML?

```HTML
<!--1. Inline-->
<p style="color:white">Text</p>
<!--2. Internal-->
<style>
  p {color:white;}
</style>
<!--3. External-->
<link rel="stylesheet" href="styles.css"/>
```

* Why should we avoid using inline styles?

```
1. It is the hardest to maintain.
2. Second it mixes CSS with HTML and makes both harder to read and interpret.
```

* Review this block of code and answer the following.

```css
h2 {
  color: black;
  padding: 5px;
}
```

* What is representing the selector?

```CSS
h2 {}
```

* Which components are the CSS declarations?

```
color:black;
padding:5px;
```

* Which components are considered properties?

```CSS
color
padding
```

---
---
## [**Javascript:Basics**](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/JavaScript_basics)

* What data type is a sequence of text enclosed in single quote marks?

```javascript
//a string
let obj0 = "string";
```

* List 4 types of Javascript Operators?

```
addition: +
subtraction: -
multiple: *
divide: /
```

* Describe a real world problem you could solve with a function?

```javascript
//convert fahrenheit to celsius
function fahrToCelsius(tempInFahrenheit) {
  let num = (5/9)*(tempInFahrenheit-32);
  return num;
}
```

## [**Making Decisions In Your Code:**](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/conditionals)

* An if statement checks a __ and if it evaluates to ___, then the code block will execute.

```
1. conditional statement
2. true
```

* What is the use of an else if?

```
Allows for the use of additional conditional statements in determining what code to run.
```

* List 3 different types of comparison operators?

```
strict equality and inequality: === and !==

non-strict equality and inequality: == and !=

greater and less-than: < and >
```

* What is the difference between the logical operator && and ||?

```
If the conditional statements on either side of && evaluate to true the entire conditional will evaluate to true.

In the same situation for || only one conditional need evaluate to true for the same to happen.
```
---
---
## [**GitHub:**](https://chris.beams.io/posts/git-commit/)

---
---
---
## **Things I want to know more about:**

* How to work with event handlers in Javascript?

