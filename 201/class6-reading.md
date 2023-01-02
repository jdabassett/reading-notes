# **201 Class06 Reading Notes:**
---
---
---

## [**JavaScript Oject Basics**](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Basics)

* How would you describe an object to a nontechnical friend you grew up with?

```
An object is a swiss army knife. It is one object yet can contain many values(information) and functions(tools). If we had a workshop we could design our own swiss army knives and make any combination of values and functions in our custom swiss army knives.
```

* What are some advantages to creating objects literals?

```
You can make objects that can produce strings dynamically based on the arguments provided and their properties.
```

* How do objects differ from arrays?

```
Arrays are ordered with each item accessible by index. While objects are look-up tables that are unordered were it's values can be accessed through the objects properties/keys.
```

* Give an example for when you would need to use bracket notation to access an object's property instead of dot notation.

```
When we are accessing an object's properties or functions dynamically with our own custom function. In this instance our function's arguments will be passed to the object with bracket notation.
```

* Evaluate the code below. What does the term this refer to and what is the advantage to using this?

```javascript
const dog = {
  name: 'Spot',
  age: 2,
  color: 'white with black spots',
  humanAge: function (){
    console.log(`${this.name} is ${this.age*7} in human years`);
  }
}
```

```
This keyword can be read as 'this function/class' and points to the function/class that it is called inside, allowing properties and methods to be 'assigned' using dote notation.
```

---

## [**Introduction to the DOM:**](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)

* What is the DOM?

```
Is a programming interface for web documents that represents the html so that CSS and Javascript can change it's appearance and behavior.
```

* Briefly describe the relationship between the DOM and JavaScript.

```
Document Object Model is the object representation of the HTML file and allowing Javascript to select object/elements to be manipulated in an OOP fashion.
```

---

## [**Understanding the problem domain is the hardest part of programming.**](http://simpleprogrammer.com/2013/07/15/understanding-the-problem-domain-is-the-hardest-part-of-programming)

---

## [**What's the difference between primitive values and object references in JavaScript?**](https://betterprogramming.pub/intermediate-javascript-whats-the-difference-between-primitive-values-and-object-references-e863d70677b)

---
---
---
## **Things I want to know more about:**

1. 

