# **Class03 Reading Notes:**
---
---
---
## Why are these reading important?

```
Working with lists and the spread operator will help translate state within React to make new elements and start the cycle between intitial and rerender.
```

---

## [**React Docs - lists and keys:**](https://reactjs.org/docs/lists-and-keys.html)

* What does .map() return?

```
A new array with each array item having passed through the function utilized by map.
```

* If I want to loop through an array and display each value in JSX, how do I do that in React?

```
Apply the map function to the array passing each array item as arguments to initialize a React component. Add this array of elements into the render method to be displayed.
```

* Each list item needs a unique ___.

```
key
```

* What is the purpose of a key?

```
To provide a unique identification to aid React in identify what elements have changed and need to be removed or rerendered.
```

---

## [**The Spread Operator:**](https://medium.com/coding-at-dawn/how-to-use-the-spread-operator-in-javascript-b9e4a8b06fab)

* What is the spread operator?

```
Syntax that expands an iterable object into a list of arguments.
```

* List 4 things that the spread operator can do.

```
Expanding: Expanding objects and lists into their items which can be passed to functions.
Combining: Pairs of objects or lists.
Adding: Items to an iterable.
Updating: With the addition it can be used to update items within an iterable.
```

* Give an example of using the spread operator to combine two arrays.

``` javascript
let array0 = [1,2,3,4,5];
let array1 = [6,7,8,9,10];
let array3 = [...array0,...array1];
// [1,2,3,4,5,6,7,8,9,10]
```

* Give an example of using the spread operator to add a new item to an array.

``` javascript
let num0 = 0;
let array0 = [1,2,3,4,5];
let array1 = [num0,...array0];
// [0,1,2,3,4,5]
```

* Give an example to using the spread operator to combine two objects into one.

``` javascript
let obj0 = {key1:'value1'};
let obj1 = {key2:'value2'};
let obj2 = {...obj0,...obj1,key3:'value3'};
// {key1:'value1',key2:'value2',key3:'value3'}
```

---

## [**How to Pass Functions Between Components:**](https://www.youtube.com/watch?v=c05OL7XbwXU)

* In the video, what is the first step that developer does to pass functions between components?

```
They create function within the element that holds the state thay will be changed/updated.
```

* In your own words, what does the increment function do?

```
When the click event occurs at the child element, the event is passed up the the parent element and the function is called to change the state by a set increment.
```

* How can you pass a method from a parent component into a child component?

```
As an attribute. This attribute will eventually be given to the event handler on a subsequent child element to be passed up when the event is triggered.
```

* How does the child component invoke a method that was passed to it from a parent component?

```
When the event is triggered in the child element.
```

---

## [**React Tutorial through 'Declaring a Winner':**](https://reactjs.org/tutorial/tutorial.html)

---

## [**React Docs - Lifting State Up:**](https://reactjs.org/docs/lifting-state-up.html)

---
---
---
## **Things I want to know more about:**

1. Why use [] to change a value of a key when using the spread operator to update an object?

``` javascript
(prevObject)=>({...prevObject,[key]:!prevObject.key})
```

