# **Reading Notes: Hash Tables**

---
---
---

## Why are these reading important?

```
Hash tables are wonderful. They help solve so many problems and can really add to the efficiency of a solution.
```


## [**Describe some different hash tables and their uses?**]()

1. dict: This is the regular dictionary  that can do the basics.

```python
regular = {'a':1, 'b':2, 'c':3}
regular.get('d')  #None
regular.pop('a')  #removes and returns 1
regular.items()   #returns list of key value pairs
regular.keys()    #returns list of keys
regular.values()  #returns list of values
regular.clear()   #clears dictionary
```

---

1. OrderedDict: Stores all pairs in the order they are added.

```python
from collections import OrderedDict

ordered = OrderedDict()
ordered['a'] = 1
ordered['b'] = 2
ordered['c'] = 3
ordered.move_to_end('b')     #changes dict in place
ordered.popitem()            #removes and returns last element
ordered.popitem(last=False)  #removes and returns first element
```

---

1. defaultdict: With return default value if key doesn't exist.

```python
from collections import defaultdict

default = defaultdict(int)
default['a'] = 1
default['b']      #returns 0
default.get('b')  #returns 0
```

---

1. Counter: Will convert input into a counter dictionary.

```python
from collections import Counter

counter = Counter('apples')
counter.get('p')    #2
```

---

1. ChainMap: Allows for the effective management of multiple dictionaries as one.

```python
from collections import ChainMap

dict1 = {'a': 1, 'b': 2}
dict2 = {'c': 3, 'd': 4}
chain_map = ChainMap(dict1, dict2)
# ChainMap({'a': 1, 'b': 2}, {'c': 3, 'd': 4})
```

---

1. UserDict: Can inherit from to implement dictionary methods to an object.

```python
from collections import UserDict

class CustomDict(UserDict):
    def __init__(self, data):
        super().__init__(data)

new = CustomDict({'x': 10, 'y': 20})
# {'x': 10, 'y': 20}
```

---

## **What I want to learn more about:**

1. I need to practice with ChainMap more to get a better handle on it's utility.

---
---
---