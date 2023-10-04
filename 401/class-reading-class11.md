# **Reading Notes: Jupyter Lab, Numpy Tutorial, and Numpy Arrays**

---
---
---

## Why are these reading important?

```
Must of linear algebra and machine learning are based on working with arrays. And for Python that is most widely accomplished through working with numpy.
```

---

## [**What is Jupyter Lab:**](https://jupyterlab.readthedocs.io/en/stable/getting_started/overview.html)

* Prompt: What are the key features and benefits of Jupyter Lab, and how does it differ from Jupyter Notebook?

  Solution: Jupyter Lab is a lightweight online version of Jupyter Notebooks. Which can simplify our development environment.

---

## [**Numpy Tutorial:**](https://www.dataquest.io/blog/numpy-tutorial-python/)

## [**Numpy Arrays:**](https://www.tutorialspoint.com/numpy/index.htm)

* Prompt: What are the main functionalities provided by Numpy library, and how can it be usedful in Python programming, particularly for scientific computing and data manipulation tasks?

  Solution: Numpy allows us to organize large amounts of data and perform efficient operations within this data and between this datasets. This is can help our programs handle data intensive tasks while also leaveraging unique mathmatical approaches(linear algebra) which can simplify our code.

* Prompt: Explain the basic structure and properties of Numpy arrays, and provide examples of how to create, manipulate, and perform operations on them.

  Solution: You can think of arrays as nested lists. A list within a list would be a 2d array. A list within a list within a list would be a 3d array. And it can go on like this. Some of the basic operations are demonstrated below.

```python
import numpy as np

#make a 1d array with a linear range of values
arr0 = np.arange(0, 101, dtype=int) # [0,1,...100]

#reshape 
arr1 = np.reshape(arr0,[10,10]) # [[0,1..],[10,11..],...]
print(arr1.shape)               #(10,10)

#make array from existing data
arr2 = np.reshape(np.array(range(0,100)),[10,10]) # same as arr1

#make an array with placeholders
arr3 = np.zeros([10,10],dtype=int #full of zeros
arr4 = np.full([10,10],3,dtype=int) #full of 3s

#select, and slice much like with lists
print(arr1[1,:])          #[10 11 12 13 14 15 16 17 18 19]
print(arr1[:,1])          #[ 1 11 21 31 41 51 61 71 81 91]
print(arr1[9,6:8])        #[96 97]
print(arr1[arr1[:]>89])   #[90 91 92 93 94 95 96 97 98 99]
print(arr0[2:20:2])       #[ 2  4  6  8 10 12 14 16 18]

#iterate over an array in a given direction
for x in np.nditer(arr1,order="F"):
    print(x)  #0 10 20 30 40 50....

```

---

## **What I want to learn more about:**

1. What are the rules of broadcasting and how to follow them when performing operations between arrays?
1. 

---
---
---