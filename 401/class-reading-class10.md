# **Reading Notes: Stacks and Queues**

---
---
---

## Why are these reading important?

```
Stacks and queues are a useful data structure. Particularly when a program adds and removes from a list more than any other operation.
```

---

## [**Stacks and Queues:**](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-10/resources/stacks_and_queues.html)

* Prompt: What are some python methods/functions to perform basic operations with stacks and/or queues?

```python
from collections import deque
que0 = deque([1,2,3,4,5])

#enqueue
#add to left side or right side
que0.appendleft(0)        #[0,1,2,3,4,5]
que0.append(6)            #[0,1,2,3,4,5,6]

#dequeue
#remove from left or right
que0.popleft()            #0
que0.pop()                #6

#enqueue
#add multiple elements to either side
que0.extendleft([-1,0])   #[0, -1, 1, 2, 3, 4, 5]
que0.extend([6,7])        #[0, -1, 1, 2, 3, 4, 5, 6, 7]

#search for index of first occurence
#front
que0.count(2)             #1
#rear
que0.index(7)             #8

#search by index
que0[0]                   #0
que0[-1]                  #7

#change order
que0.reverse()            #[7, 6, 5, 4, 3, 2, 1, -1, 0]
que0.rotate(-2)           #[5, 4, 3, 2, 1, -1, 0, 7, 6]

#add and remove internally
que0.insert(index,object) #[5, 4, 100, 3, 2, 1, -1, 0, 7, 6]
que0.remove('value')      #[5, 4, 100, 3, 2, 1, 0, 7, 6]

#clear que
que0.clear                #[]
```

---

## **What I want to learn more about:**

1. Is there another python class that can perform at the same level at deque? (Chatgpt says to use a list or create a class that will manage a link-list for you.)

---
---
---