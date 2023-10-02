# **Reading Notes: Scope, Big O, and Rolling Dice Examples**

---
---
---

## Why are these reading important?

```
Knowing when and where you can access the elements you create or the tools you needs is criticial to software development and understanding scope will help with this. Also it never hurts to understand Big O notation for a different perspective. Very helpful.
```

---

## [**Python Scope:**](https://realpython.com/python-scope-legb-rule/)

* Prompt: Explain the concept of variable scope in Python and describe the difference between local and global scope. Provide an example illustrating the usage of both.

  * Solution: 
    Scope refers to the storage and access of variables, parameter, classes, function, and more. If a function is declared within the global scope it can be accessed by any other element globally. The same is true for a local scope. 

    Think of scope like segments of a factory. Maybe the entire factory is under the Builtin scope. A segment like the paint shop might be under a Global scope, containing all tools applicable to the paint process(Global to paint). There as someone's office within the paint shop might be their own Enclosed(Functional) scope and the candy drawer within their desk would be a smaller Local scope. Each of the smaller scopes can have access to elements declared in a larger scope(my phone can call headquarters) but not the other way around (stay out of my candy drawer).

* Prompt: How do the global and nonlocal keywords work in Python, and in what situations might you use them?

  * Solution: The global keyword can initialize a locally declared variable within the global scope instead of locally. Nonlocal does something similar but only in nested function. Either way you want to avoid using them. They can make your code unnecessarily complex and buggy.

---

## [**Big O notation is simpler than you think:**]()

* Prompt: In your own words, describe the purpose and importance of Big O notation in the context of algorithm analysis.

  * Solution: Big O notation is the means developers use to estimate the increase in work, time, and/or memory utilized by an algorithm as the input data increases in size or complexity.

---

## [**Rolling Dice Examples:**]()

* Prompt: Based on the Rolling Dice Example, explain how you would simulate a dice roll using Python. Describe how you would use code to calculate the probability of rolling a specific number (e.g. the probability of rolling a 6) over a large number of trials?

  * Solution: You could use the random module and make a function to simulate the single roll of a die. Then you could simulate the roll of that die multiple times and use the results to find the proportion of of received one result from a six sided die over that number of rolls. See below.

```python
import random
def roll_dice() -> int:
    return random.randint(1,6)

def roll_amount(number: int,value: int) -> float:
    if number <= 0 or value < 1 or value > 6:
        return 0

    int_count = 0
    int_iter = 0
    while int_iter < number:
        int_dice = roll_dice()
        if int_dice == value:
            int_count += 1
        int_iter += 1

    return round(int_count / number,4)

print("What proportion of times can you roll any one number from a 6 sided die.")
print("10 rolls:",roll_amount(10,1))
print("100 rolls:",roll_amount(100,1))
print("1,000 rolls:",roll_amount(1000,1))
print("10,000 rolls:",roll_amount(10000,1))
print("100,000 rolls:",roll_amount(100000,1))
print("1,000,000 rolls:",roll_amount(1000000,1))
print("10,000,000 rolls:",roll_amount(10000000,1))

#What proportion of times can you roll any one number from a 6 sided die.
#10 rolls: 0.2
#100 rolls: 0.18
#1,000 rolls: 0.174
#10,000 rolls: 0.1676
#100,000 rolls: 0.1663
#1,000,000 rolls: 0.1665
#10,000,000 rolls: 0.1667
```

---

## **What I want to learn more about:**

1. I wonder what a good use case of the Global keyword might be?

---
---
---