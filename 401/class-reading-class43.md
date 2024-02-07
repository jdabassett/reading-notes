# **Reading Notes: Pythonisms**

---
---
---

## Why are these reading important?

```
Each of these topics will help us progress beyond a basics into the intermediate level.
```

---

## [**Dunder Methods:**](https://dbader.org/blog/python-dunder-methods)

---

## [**Iterators:**](https://dbader.org/blog/python-iterators)

---

## [**Generators:**](https://dbader.org/blog/python-generators)

---

## [**What are Generators:**](https://realpython.com/lessons/what-are-python-generators/)


---

## [**Decorators:**](https://realpython.com/primer-on-python-decorators/)


---

## **Reading Questions:**

1. Prompt: What are dunder methods in Python, and how do they allow for the customization of built-in behavior in classes? Provide an example of a common dunder method and its purpose.

  Solution: Duncer methods are private methods that enable class instances to function like other data structures. Think subscription for lists, comparable for integers, and printable in a formated fashion.

  Some examples:
  * `__init__`: for initializing class objects
  * `__str__`:  for generating a formated printable version of class instance
  * `__len__`:  for returning length
  * `__getitem__`:  making subscribable
  * `__iter__`:  returns iterable object
  * `__next__`:  defines how iteration works
  * `__eq__` or `__lt__` or `__ge__`: for comparison operations
  __

1. Prompt: Explain the concept of an iterator in Python. How do you create a custom iterator using the iter() and next() methods, and why are they important for enabling iteration in a class?

  Solution: Lots of built-in data structure are iterators. Lists, strings, sets, tuples, and dictionaries(convertible) can be iterated over. Yet to iterate over the data in a custom class instance, you will need to define how to properly tranverse the data. 

  This example is taken from ChatGPT.

```python
class MyIterator:
    def __init__(self, start, end):
        self.start = start
        self.end = end
        self.current = start

    def __iter__(self):
        return self

    def __next__(self):
        if self.current < self.end:
            result = self.current
            self.current += 1
            return result
        else:
            raise StopIteration

my_iterator = MyIterator(1, 5)

for value in my_iterator:
    print(value)
```


1. Prompt: What is a generator in Python, and how does it differ from a regular function? Illustrate your answer with an example of a generator function using the ‘yield’ keyword.

  Solution: A generator is a type of iterator that allows iteration over data without making a new space in memory for that data. In this way generators are comparably easy to work with as conventional iterators but with more memory savings. 

  This is an example from the reading contrasting iterators with generators.

```python
# traditional iterator
class BoundedRepeater:
    def __init__(self, value, max_repeats):
        self.value = value
        self.max_repeats = max_repeats
        self.count = 0

    def __iter__(self):
        return self

    def __next__(self):
        if self.count >= self.max_repeats:
            raise StopIteration
        self.count += 1
        return self.value

# a comparable generator
def bounded_repeater(value, max_repeats):
    for i in range(max_repeats):
        yield value
```



1. Prompt: Define decorators in Python and explain their primary use case. How can you create and apply a custom decorator to a function or method? Provide a simple example to demonstrate this concept.

  Solution: Decorators are a means to reduce code repeatition. If you find redundance code used in multiple functions or methods this can be removed from the function and added back in the form of a decorator function. Think of it like nesting your primary function inside of a decorator function. Only doing that nesting would also cause a  lot of needless code repetition. Defeating the point. Which is why decorators are implemented in a very simple and slightly confusing way. In the long it is simpler to declare and use.

  This is from the reading.

```python
def my_decorator(func):
    def wrapper(*args,**kwargs):
        print("Something is happening before the function is called.")
        func(*args, **kwargs)
        print("Something is happening after the function is called.")
    return wrapper

@my_decorator
def say_whee(input_string):
    print(input_string)
  
say_whee("Hello World")
```


---

## **What I want to learn more about:**

1. I am a little more comfortable with generators than iterators. Yet ultimately I don't know when I would want to use one over the other? (When there isn't a hard memory constraint.)

---
---
---