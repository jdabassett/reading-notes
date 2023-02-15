# **Class04 Reading Notes:**
---
---
---
## Why are these reading important?

```
```

---

## [**React Docs - Forms:**](https://reactjs.org/docs/forms.html)

* What is a 'Controlled Component'?

```
A components whose value is take from state and updated in state.
```

* Should we wait to store the users responses from the form into state when they submit the for OR should we update the state with their responses as soon as they enter them? Why?

```
We should update state with each response as it is made. In this way if anything interrupts the input before submission, we can store the information locally or in a database to be auto populated when the user returns. Also, tests can be run against what is inputed to throw warnings as they are triggered rather than just at submission.
```

* How do we target what the user is entering if we have an event handler on an input field?

```
We match the key held in state with the name of the component before adding any value from the event.
```

---

## [**The Conditional (Ternary) Operator Explained:**](https://codeburst.io/javascript-the-conditional-ternary-operator-explained-cac7218beeff)

* Why would we use a ternary operator?

```
For simple conditionals a ternary will often take up less space and be easier to read. This makes them idea to fit within larger code.
```

* Rewrite the following statement using a ternary statement.

```javascript
if(x===y){
  console.log(true);
} else {
  console.log(false);
}
```

```javascript
(x===y)?console.log(true):console.log(false);
```

---

## [**React Bootstrap - Forms:**](https://react-bootstrap.github.io/forms/overview/)


## [**React Docs - conditional rendering:**](https://reactjs.org/docs/conditional-rendering.html)


---
---
---
## **Things I want to know more about:**

1. 

