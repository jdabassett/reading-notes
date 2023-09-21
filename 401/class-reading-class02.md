# **Reading Notes Class02: Testing and Modules:**

---
---
---

## Why are these reading important?

```
Testing, Recursion, and Modules oh my! Learning how to utilize testing will help us developers improve the quality of our code and reduce the headaches of developing it. Recursion is a niche superpower; when it works it can work really well. And the rest are Python specific reading covering modules, lists, and strings will help broaden our base of knowledge.
```

---

## [**In Tests We Trust - TDD with Python:**](https://code.likeagirl.io/in-tests-we-trust-tdd-with-python-af69f47e6932)

* Prompt: What does TDD stand for and describe?
  
  Solution: Test-Dependent-Development, which is a development phylosophy that programmers should be writing test before coding anything to guide their codes development.

* Prompt: What is a good naming convension for scripts and their tests?

  Solution: 'script_name.py' and 'test_script_name.py'. Also store them separately.

* Prompt: What is the general work-flow for TDD?

  Solution: Write test and make it fail. Write feature and make it pass. Refactor code until acceptable.

* Prompt: Provide an example of a unit test labeling Arrange, Act, and Assert?

```python
def test():
    #Arrange
    detector = Detector()
    #Act
    expected = detector.run(‘input’)
    #Assert
    assert expected == True
```

---

## [**If the name equals main:**](https://www.geeksforgeeks.org/what-does-the-if-__name__-__main__-do/)

* Prompt: Why utilize '__name__' dunder variable?
  
  Solution: To control what code is run from a script based how if it is run directly or imported.


---

## [**Recursion:**](https://www.geeksforgeeks.org/recursion/)

* Prompt: What are four main steps to constructing a recursive function?
  
    Solution: First, define base case. Second, define subproblem. Three, ensure base case stops recursion. Fourth, combine both.

---

## [**What on Earth is Recursion:**](https://www.youtube.com/watch?v=Mv9NEXX1VHc)

* Prompt: How to terminate a recursive function?
  
  Solution: A base case. 

---

## [**Python Modules and Packages Companion Video:**](https://realpython.com/courses/python-modules-packages/)

* Prompt: How to find all the directories the interpreter will search for a imported module in the order that they will be sured at run time.

  Solution: use sys module. Can mutate this variable!

```python
import sys
#returns list of directory paths
print(sys.path)
#mutate
sys.path.append(r'new/dir/module.py')
```

* Prompt: How to find file path of imported module?

  Solution: Use '__file__' dunder variable.

---

## [**Google for Education: Python Lists**](https://developers.google.com/edu/python/lists)

* Prompt: Can you add to a list during iteration?

    Solution: Maybe but it will/should through a warning, so don't try it.


---

## [**Google for Eduction: Python Strings**](https://developers.google.com/edu/python/strings)

* Prompt: How to pass special character through as a string?

    Solution: Use the r'special\string' syntax.


---

## [**Python Modules and Packages:**](https://realpython.com/python-modules-packages/)

* Prompt: How to access the local symbol table?

    Solution: Use Dir() function. Will return list of all names in the local symbol table.


---

## [**Pytest Documentation:**](https://docs.pytest.org/en/latest/)

---

## [**Pytest Tutorial:**](https://www.guru99.com/pytest-tutorial.html)

* Prompt: How does pytest know which files to run?
    
    Solution: By default they must either start with 'test_' or end with '_test'.

* Prompt: What are some basic pytest decorators and what do they do?

    Solution: 
    1. @pytest.mark.markName sets the mark name so unit test can be called separately
    1. @pytest.fixture sets apart a function to execute first and pass it's contents to other unit tests.
    1. @pytest.mark.parameterize allows for several inputs and outputs to be passed into a unit test.

---

## [**Reading Questions:**]()

1. What are the key principles of Test-Driven Development(TDD) in Python, and how do they contribute to the overall quality of code?

  Solution: They key to TDD is to write test before and during development to improve the quality of the code. It forces developers to think critically before coding which will eliminate more edge cases and catch more bugs before they propogate.

1. Explain the purpose of the following Python statement in a script? What are some use cases for including this conditional in your code?

```python
if __name__ == '__main__':
```

  Solution: The '__name__' dunder variable is defined by the interpreter and can be used to dictate what code is ran from a script based on if the script is ran directly or imported first.

1. Describe the concept of recursion in Python?

  Solution: Recursion is the act of 'recursively' calling a function within itself. It works well with problems that have an overlapping subproblem which when solved can layer up to solve the larger problem.

1. What is the difference between Python Modules and Packages? Explain how to create, import, and use them in your Python programs?

  Solution: A module is a singel python file that is meant to be imported rather than ran directly. A packages is a collections of modules. You can create a module by writing a simple script in python and use the '.py' tag. Use the 'from' and 'import' keywords at the top of any other script to access this module.

---

## **Things I want to know more about:**

1. I need to practice recursion with trees/graphs.
2. I have never used the Pytest module and need to fix that.

---
---
---