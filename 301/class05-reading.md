# **Class05 Reading Notes:**
---
---
---
## Why are these reading important?

```
This provides a blue print of how we should start constructing our React apps.
```

---

## [**React Docs - Thinking in React:**](https://reactjs.org/docs/thinking-in-react.html)

* What is the single responsibility principle and how does it apply to components?

```
The phylosophy that an object, function, or in our case a component should do only one thing. It it grows to do multiple things, then it should be broken up into subcomponents.
```

* What does it mean to build a ‘static’ version of your application?

```
State the build in react with no interactivity(without state). This way any design changes can happen before dynamic features are added.
```

* Once you have a static application, what do you need to add?

```
State. State is the means by which components are made dynamic and trigger rerender.
```

* What are the three questions you can ask to determine if something is state?

```
1. Is it passed in from a parent via props? (ie If true, probably not state.)
2. Does it remain unchanged over time? (ie If true, probably not state.)
3. Can you compute it based on any other state or props in your component? (ie If true, probably not state.)
```

* How can you identify where state needs to live?

```
1. Identify every component that renders something based on that state.
2. Find the closest common ancestor. Either that common ancestor or one above it should hold the data in their state.
3. If for whatever reason this isn't feasible, consider adding a component between the common ancestor and all the children with the sole responsibility to hold state.
```

---

## [**Higher-Order Functions:**](https://eloquentjavascript.net/05_higher_order.html#h_xxCc98lOBK)

* What is a “higher-order function”?

```
Functions that operate on other functions, either by taking them as arguments or by returning them.
```

* Explore the greaterThan function as defined in the reading. In your own words, what is line 2 of this function doing?

```
It is using an arrow function that will be nested with the greaterThan function. In this way the greaterThan function can be accept parameters that when generating new functions that can rely on those parameters.
```

* Explain how either map or reduce operates, with regards to higher-order functions.

```
Both map and reduce accept functions(often arrow function) as a parameter to accomplish their tasks.
```

---
---
---
## **Things I want to know more about:**

1. I need more practice working with higher-order functions.

