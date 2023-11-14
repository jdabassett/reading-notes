# **Reading Notes: Automation**

---
---
---

## Why are these reading important?

```
File operations are critical to many automation tasks!
```

---

## [**Python Regular Expressions Tutorial:**](https://www.datacamp.com/community/tutorials/python-regular-expression-tutorial)

---

## [**shutil:**](https://pymotw.com/3/shutil/)

---

## [**os:**](https://pymotw.com/3/os/)

---

## [**Automation Ideas:**](https://www.youtube.com/watch?v=qbW6FRbaSl0&t=69s)

---

## [**Automating Your Browser and Desktop Apps:**](https://www.youtube.com/watch?v=dZLyfbSQPXI)

---

## [**Watchdog:**](https://pythonhosted.org/watchdog/)

---

## READING QUESTIONS:

1. Prompt: How can you use regular expressions in Python to search for specific patterns in a string, and what is the primary module to work with them?

  Solution: You can use some of the following functions from the 're' module to find matches to regular expressions and perform operations with those matches. 'str_pattern' would be the regulare expression in the examples below and allow for proper identification of the substrings.

```python
import re
# to efficiently save str_pattern as object
obj_pattern = re.compile(str_pattern)
# return match object if pattern found at beginning
obj_pattern.match(str_variable)
# returns match object at first match
# group returns the actual string from object
obj_pattern.search(str_variable).group()
# return list of all matchs
obj_pattern.findall(str_variable)
# return iterable object of all match objects
obj_pattern.finditer(str_variable)
# replace pattern with replacement
# return new string
obj_pattern.sub(str_replace,str_variable)
# split a string at given pattern 
# return list of substrings
obj_pattern.split(str_variable)
# find start and stop index of match
# return tuple
# can also return int with .start() or .end()
obj_pattern.search(str_variable).span()

# useful flags with the above functions
# re.I #ignorecase
# re.M #multiline
# re.X #verbose
```

1. Prompt: What is the purpose of the shutil module in Python, and provide an example of a common use case for file or directory management with this module?

  Solution: To perform file operations. Below are descriptions of a few of it's functions along with there uses.

```python
import shutil
# input filenames and copies file into new file
shutil.copyfile('original.py','copy.py')
# copy file into directory
shutil.copy('original.py','directory')
# to create copy with metadata permissions
shutil.copymode('original.py','directory')

# to move a file or directory
shutil.move('file.py','../directory')

# to copy directory
shutil.copytree('../directory','../new_directory')
# to remove a directory
shutil.rmtree('../directory')

# find path to...
shutil.which('virtualenv')

# compress|archive file
shutil.make_archive(
    'example', 'gztar',
    root_dir='..',
    base_dir='shutil',
    logger=logger,)

# find how much space available
shutil.disk_usage('.')
```


1. Prompt: Compare and contrast the os and shutil modules. When would you choose to use one over the other?

  Solution: A rule of thumb is this. If it is a simple file operation, 'os' module is probably sufficient; otherwise the 'shutil' modules is built for ease of use and more complex file operations and might be the right tool for the job.

## **What I want to learn more about:**

1. How to use Watchdog. It seems really interesting and I want to test it out.

---
---
---