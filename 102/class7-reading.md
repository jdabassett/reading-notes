# Flashcards: Javascript Variables and Functions

___
___
___

## **Why is this important?**
Functions are small scripts that make debugging easier. Functions get passed variables as arguments to produce their outputs. All of this makes your website better.

___
___

## Flashcards

**What are some common javascript operators?**

|Operator	|Action			|w/=             |
|:--        |:--            |:--|
|+			|add			|(x+=y)==(x=x+y)|
|-			|substract		|(x-=y)==(x=x-y)|
|*			|multiply		|(x*=y)==(x=x*y)|
|/			|divide			|(x/=y)==(x=x/y)|
|%			|remainder		|(x%=y)==(x=x%y)|
|**			|exponential	|(x**=y)==(x=x**y)|
|++		   	|increment      |   |
|--			|decrement      |   |
|=			|equal	        |   |

___

**What are some javascript comparison operators?**

|Operator		|Action|
|:--        |:--    |
|==			|equal to                   |
|===			|equal value and type   |
|!=			|not equal to               |
|!==			|not equal value or type|
|>			|greater than               |
|<			|less than                  |
|>=			|greater than or equal to   |
|<=			|less than or equal to      |
|?			|ternary operator           |

___

**What are some javascript logic and type operators?**

|Operator       |Action     |w/=        |
|:--            |:--        |:--        |
|&&             |logical and |(x&&y)==(x&&(x=y))    |        
|\|\|			|logical or		|(x\|\|y)==(x\|\|(x=y))
|!			|logical not		|   |
|typeof		|returns type       |   |
|instaneof	|returns boolean of comparison      |   |

---
**Add a function output to an HTML element?**

```
function fahrenheitToCelsius(f){
	return (5/9)*(f-32);}:
let tempConv = fahrenheitToCelsius(userTempFahr);
document.getElementByID("elementID").innerHTML 
= "The temperature is " + tempConv + " Celsius";
```

___
___
___

## Things I want to know more about.

1. Where the Javascript files are run-utilized?
1. How to write javascript in an OOP fashion.