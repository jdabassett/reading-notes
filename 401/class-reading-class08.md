# **Reading Notes:**

---
---
---

## Why are these reading important?

```
List comprehension can be an eliquent compact way to perform many of the operations previously reserved only for traditional for-loop. They can be sexy. 


```

---

## [**List Comprehension:**](https://www.pythonforbeginners.com/basics/list-comprehensions-in-python)

* Prompt: What is the basic syntax of Python list comprehension, and how does it differ from using a for loop to create a list? Provide an example of list comprehension thats squares the elements of a give list of integers.

  Solution: Basic list comprehension syntax is `[do_something_to(component) **for** component **in** original_list **if** adheres_to_condition(component)]`. It differs in the fact that all variables created inside the loop are confined to it's scope and cannot be reference outside or after unlike a traditional for loop.

```python
list_integers = range(1,101)
#[1, 2, 3, 4, 5, 6, 7, 8, 9, 10,...
list_integers_squared = [i**2 for i in list_integers]
#[1, 4, 9, 16, 25, 36, 49, 64, 81, 100,...
```

---

## [**Debugging with Pysnooper:**](https://www.pythonpodcast.com/pysnooper-python-debugging-episode-241/)

---

## [**Primer on Decorator:**](https://realpython.com/primer-on-python-decorators/)

* Prompt: What is a decorator in Python?

  Solution: 'A decorator is a function that takes another function and extends it's behavior without explicitly modifying it.'(directly from link)

* Prompt: Explain the concept of decorators in Python. How do they work, and what are some common use cases for them? Provide an example of a simple decorator function from the reading.

  Solution: See the solution to the last prompt. How they work is through passing an inner function into the decorator to control it's execution. Use cases for decorators are debugging, measure run time, cache results, repeat inner calls, moderate inner function calls, count declarations of inner function, and many more. 
  Below is an example of a decorator that moderates the declaration of it's inner function to 1 per second. [link](https://realpython.com/primer-on-python-decorators/#slowing-down-code)

```python
import functools
import time

def slow_down(func):
    """Sleep 1 second before calling the function"""
    @functools.wraps(func)
    def wrapper_slow_down(*args, **kwargs):
        time.sleep(1)
        return func(*args, **kwargs)
    return wrapper_slow_down

@slow_down
def countdown(from_number):
    if from_number < 1:
        print("Liftoff!")
    else:
        print(from_number)
        countdown(from_number - 1)
```

---

## **What I want to learn more about:**

1. I need to practice using Pysnooper.
1. I have avoided making decorators personally because they confuse me. I would like one simple use case that I might use consistantly.

---
---
---