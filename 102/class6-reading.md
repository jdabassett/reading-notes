# **102 Class06 Reading Notes:**
___
___
___

## **Why is this important?**
Javascript provide the means to take our website from a static state into the real of the dynamic.

___
___

## Flashcards

**What is the difference between var, let, and const keywords?**

```javascript
var x; 	    //undefined declaration of x variable
var x=1;	//can be redeclared
x=1; 	    //or reassigned
		    //will be hoisted but be undefined

let y; 	    //undefined declaration of y variable
		    //block scoped
//let y=2; but not redeclared within same scope
y=2;	    //can be reassigned within any scope
		    //will be hoisted but through error


const z;    //undefined declaration of z variable
//same as let, but cannot redeclared or redefined
//can redefine some properties
```

___

**Within HTML file, how to link to Javascript file?**

```html
<script src='file.js'>
</script>
```

___
**How to write a if-else statement?**

```javascript
if (iceCream === "chocolate") {
  console.log("Yay, I love chocolate ice cream!");}
else if (iceCream === "vanilla"){
  console.log("I hate vanilla ice cream!");}
else {
  console.log("I don't like ice cream.");}
```
___
___
___

## Things I want to know more about.

1. How to make a function?
1. How to write an OOP program?