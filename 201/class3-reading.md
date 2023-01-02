# **201 Class03 Reading Notes:**
---
---
---

## [**Learn HTML:**](https://developer.mozilla.org/en-US/docs/Web/HTML)

### [**Ordered List:**](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/ol)

### [**Unordered List:**](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/ul)

* When should you use an unordered list in your HTML document?

```
When a list doesn't need a specified order and any one item could be substituted with anyother.
```

* How do you change the bullet style of unordered list items?

```HTML
<!--you can specify the bullet type with the ul tag attribute-->
<ul type = "circle | disc | square"></ul>
```

```CSS
// also all list styles can be changed in CSS with the list-style propertie
// in particular list-style-type to change the bullet style
ul, ol {
  list-sytle: type position image;
}
```

* When should you use an ordered list vs an unordered list in your HTML document?

```
Can cany item withing a list be substituted for another other? If yes, use an unordered list. If no, use an ordered list.
```

* Describe two ways you can change the numbers on list items provided by an ordered list?

```html
<!--can change these attributes-->
<ol reversed></ol> <!--reverse list-->
<ol start="2"></ol> <!--change the start-->
<ol type = "1 | A | a | I | i"></ol> <!--change kind of marker-->
```

---

## [**Learn CSS:**](https://developer.mozilla.org/en-US/docs/Learn/CSS)

### [**The Box Model:**](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/The_box_model)

* Describe the CSS properties of margin and padding as characters in a story. What is their role in a story titled: "The Box Model"?

```
There once was a grand estate in Versaille. If one were to ride by carriage into the estate they would find a large outer garden exquisitely manicured and maintained to separate the wider world from the estate itself. Then a large wall to display the grandeur and importance of it's occupants. Followed by an inner garden before you arrive at the ornate estate manor itself. 
The gardeners who tended to this estate where Hugo Margin and Phillipe Padding. They hand their hands full keeping the two gardens maintained. So much so that Hugo exclusively maintained the outer garden, leaving the inner garden to Phillipe. That is until the glorious French Revolution happened and they guilitined their estate master. 
```

* List and describe the 4 parts of an HTML elements box as referred to by the box model.

```
Margin Box: the space outside of the border; maintains space between separate elements
Border Box: the border between the margin and padding; in alternate model all dimensions apply here
Padding Box: the space between the border and contents; maintains space between border and contents
Content Box: the center of the box; in standard model all dimension apply here
```
---

## [**Learn Javascript:**](https://developer.mozilla.org/en-US/docs/Learn/JavaScript)

### [**Array:**](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/Arrays)

### [**Operators and Expressions:**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators)

### [**Conditionals:**](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/conditionals)

### [**Loops:**](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Looping_code)

* What data types can you store inside of an Array?

```
strings, numbers, objects, boolean, null, undefined, functions, arrays
All the data types I am aware of at the moment.
```

* Is the people array a valid JavaScript array? If so, how can I access the values stored? If not, why?

```javascript
const people = [['pete', 32, 'librarian', null], ['Smith', 40, 'accountant', 'fishing:hiking:rock_climbing'], ['bill', null, 'artist', null]];

//Yes the people array is a valid array.
//access the values with either brackets, or with splice.
//brackets: people[0][2]
//splice: people[2].splice(1,3)
```

* List five shorthand operators for assignment in javascript and descrive what they do.

```
shorthand: description
x += 1 : adds 1 to x, reassigns product to x
x -= 1 : subtracts 1 from x, reassigns product to x
x *= 1 : multiples x by 1, reassigns product to x
x /= 1 : dividdes x by 1, reassigns product to x
x **= 1 : raised x to the power of 1, reassigns product to x
```

* Read the code below and evaluate the last expression and explain what the result would be and why.

```javascript
// code
let a = 10;
let b = 'dog';
let c = false;
// evaluate this
(a + c) + b;
```

```
'10dog'
Because false would evaluate to 0, be added to 10; before 10 was converted to a string and concatenated with 'dog'.
```

* Describe a real world example of when a conditional statement should be used in a JavaScript program.

```
If the user is prompted to input their measurables to calculate their BMI, yet all the calculations will depend on the units associated with those measurables. A conditional statements would direct which calculation are made and what output is provided to the client based on the units.
```

* Give an example of when a Loop is useful in JavaScript.

```
Loops are useful when you are working with arrays and want to systematically access each item contained inside. With each iteration you could modify, filter, reassign, or do just about anything else.
```

---
---
---

## **Things I want to know more about:**

1. How unshift, shift, and map got their names?
1. How to use void, super, and new keywords?