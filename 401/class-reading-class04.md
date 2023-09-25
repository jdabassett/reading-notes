# **Reading Notes: Classes, Recursion, and Pytest Fixtures**

---
---
---

## Why are these reading important?

```
Most high end programing uses classes so embrace them. Recursion has a small niche but when it fits the bill it works extremely well. And getting comfortable with Pytest Fixtures will keep you from writing redundant code in your tests.
```

---

## [**Classes and Objects:**](https://www.learnpython.org/en/Classes_and_Objects)

* Prompt: What is the difference between class and instance variables?
  
  Solution: Class variables are shared between all classes of the same type, were as instance variables can be unique to each instance of a class.

---

## [**Thinking Recursively:**](https://realpython.com/python-thinking-recursively/)

* Prompt: What does the lru_cache decorator do?
  
  Solution: When calling function recursively it will hash the parameter and check the cache if a solution has already been calculated, if true it will return the answer saving time and resources.

---

## [**Pytest Fixtures and Coverage:**](https://www.linuxjournal.com/content/python-testing-pytest-fixtures-and-coverage)

* Prompt: When should you use pytest's fixures feature?
  
  Solution: When you want to set a variable/resource that can be used by all tests within a module. This avoids having to set the variable/resource for each test individually.

---

## [**Pytest Fixtures:**](https://docs.pytest.org/en/latest/fixture.html)

* Prompt: 
  
  Solution: 

---


## [**Reading Questions:**]()

1. Prompt: What are the key differences between classes and objects in Python, and how are they used to create and manage instances of a class?
  
  Solution: Classes are blueprints for individual objects. Think of classes as a blueprint or framework with attributes and methods that are shared by all objects of that class. Where as objects can have there own unique attributes.

1. Prompt: Explain the concept of recursion and provide an example of how it can be used to solve a problem in Python. What are some best practices to follow when implementing a recursive function?
  
  Solution: Recursion is problem solving method best employed with modular problems that can be solved in pieces that aggregate to a cummulative solution. 
  
  An example could be counting down from 10. The base case would be reaching zero. Incrementing down by one when calling the same function. 
  
  Best practices are to always start with the base case that will stop the recursion. Next would be to break a problem down into it's sub problem and solve that before calling the function again.

1. Prompt: What is the purpose of pytest fixtures and code coverage in testing Python code? Explain how they can be used together to improve the quality and maintainability of a project.
  
  Solution: Pytest fixtures allows to the setting of 'global variables' to that all tests can use them without needing to create them individually. Code coverage is a measure of how much cumulative 'code' is being tested when pytest is called.

  Using fixtures ahears to the dry principle and will keep you from repeating code. And code coverage will help you track just how much you are testing as you develop.


---

## **What I want to learn more about:**

1. I need more practice with pytest fixtures!
1. I am progressing in recursion, but need a lot more work to move beyond simple problems.

---
---
---