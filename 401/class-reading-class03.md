# **Reading Notes: FileIO and Exceptions**

---
---
---

## Why are these reading important?

```
Learning how to handle files is learning how to import data into our programs and export the results into a file. Seem important.
```

---

## [**Read and Write Files in Python:**](https://realpython.com/read-write-files-python/)

* Prompt: What are the different open file 'modes' to chose from and their corresponding symbols?
  * 'r' for read
  * 'w' for write
  * 'rb' for read binary
  * 'wb' for write binary
  * 'x' for create
  * 'a' for append

---

## [**Exceptions in Python:**](https://realpython.com/python-exceptions/)

* Prompt: What are the 4 parts of a try+except block?

  Solution: Try, Except, Else, and Finally.

---

## [**File Objects - Reading and Writing to Files:**](https://www.youtube.com/watch?v=Uh2ebFW8OYM)

* Prompt: What does the 'with' keyword do?

  Solution: Creates a code block that handles expections automatically and closes any openned files.

* Prompt: How to make a copy of an image?

```python
with open('image.jpg','rb') as rf:
  with open('image_copy.jpg','wb') as wf:
    for line in rf:
      wf.write(line)

```

---

## [**Reading and Writing Files in Python Quiz:**](https://realpython.com/quizzes/read-write-files-python/)

---

## [**Reading Questions:**]()

1. Prompt: What is the purpose of the 'with' statement when opening a file in Python, and how does it help manage resources while reading and writing files?

  Solution: "with" is a keyword that denotes a block of code. It is used with exception handling to simplify file management often in import and closing. It does this through automating the opening, closing and exception handling within it's code block.

1. Prompt: Explain the difference between the 'read()' and 'readline()' methods for file objects in Python. Provide examples of when to use each method.

  Solution: Read loads all of the files contents into memory; where Readline converts the file into an iterable and only loads one line at a time. Best to use Read with small files of know complexity and Readline with larger files with unknown complexity.

1. Prompt: Briefly describe the concept of exception handling in Python. How can the 'try', 'except', and 'finally' blocks be used to handle exceptions and ensure proper execution of code? Provide a simple example.

  Solution: When you want to catch a non syntax error while keeping the program running, consider using a try-except block.

```python
try:
  function_that_crashes_all_the_time()
except:
  print('Function crashed again. Blame it on the kids.')
else:
  print('What a stroke of luck!')
  dependent_function()
finally:
  print('Runs regardless.')
  cleans_up_everything()
```

---

## **What I want to learn more about:**

1. I need to learn more about how to handle exceptions.
1. I need to practice working with files in python.

---
---
---