# **Class09 Reading Notes:**
---
---
---
## Why are these reading important?

```
React is largely a functional programming endeavor these days. Taking a step back to see the forest for the trees will help us become better React developers.
```

---

## [**Functional Programming Concepts:**](https://medium.com/the-renaissance-developer/concepts-of-functional-programming-in-javascript-6bc84220d2aa)


* What is functional programming?

  It is a programming paradigm where programs are made with function that avoid changing global variables and mutable data.

* What is a pure function and how do we know if something is a pure function.

  First, return values must be the same for a give input. (deterministic)
  Second, there can be no side effects.

* What are the benefits of a pure function?
 
 
  First, they are predictable and thus robust, reliable, easier to understand, easier to test/debug.
  Second, since they don't take in global variables or have side-effects; they can be very fast.
  Third, they have better performance since they use less memory and are often faster.

* What is immutablility?

  The concept that given variables are unchangeable.

* What is Referential transparency?

  If a function constitantly returns the same results for the same input (First Rule of a pure function), than it is has referential transparency.

---

## [**Node JS Tutorial for Beginners #6 - Modules and require():**](https://www.youtube.com/watch?v=xHLd36QoS4k)

* What does the word 'require' do?

  It is a node.js function to load external modules.

* How do we bring another module into the file that we are working in?

```javascript
  const objectName = require('module');
```

* What do we have do to make a module available?

```javascript
  module.exports = elementToExport
```

---
---
---
## **Things I want to know more about:**

1. How to memoize a recursive function?

