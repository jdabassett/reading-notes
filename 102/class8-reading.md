# Flashcards: Javascript Iterables

___
___
___

## **Why is this important?**
Iterables are invaluable and a great place for beginners to start!

___
___

## Flashcards

**How to use a ternary operator?**

```
//condtional ? if-true: if-false;

let status= age>=18 ? 'adult' : 'minor';
```
___

**With a for loop, print "Hello World" 5 times in the console?**

```
/*initial expression
  conditional expression
  incremental expression*/
for (let i=0; i<10; i++) {
  console.log('Hello World');
  if (i>=5){break;};}
```
___

**With a while loop, print "Hello World" 5 times in the console?**

```
/*conditional expression
let i = 0;
while (i<10){
  i++;
  console.log('Hello World');
  if (i>=5){break;};}
```

---

**How to use the delete operator/keyword?**

```
delete object.property;
delete object[propertyKey];
delete objectName[index];
```

---

**How if object has property?**

```
//use the 'in' operator/keyword
//will return boolean if property exists
//propNameOrNumber in objectName;
const rocks = ["big","small","round"]
0 in rocks;			//true
4 in rocks;			//false
'big' in rocks;		//false
'length' in rocks;	//true
```

---

**Boolean comparison of object type?**

```
//use the 'instanceof' operator/keyword
//objectName instanceof objectType;
```

___
___
___

## Things I want to know more about.

1. How to use the super function?