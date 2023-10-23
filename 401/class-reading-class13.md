# **Reading Notes: Linear Regression**

---
---
---

## Why are these reading important?

```
Linear regression is one of the most basic methods in data analysis. If you want to understand anything in data analysis, linear regression is a great place to start.
```

---

## [**How to Run Linear Regression in Python:**](https://www.activestate.com/resources/quick-reads/how-to-run-linear-regressions-in-python-scikit-learn/)

---

## [**Linear Regression in Python:**](https://realpython.com/linear-regression-in-python/)

---

## [**Introduction to Simple Linear Regression:**](https://www.youtube.com/watch?v=KsVBBJRb9TE)

---

## [**Train and Test Splits:**](https://towardsdatascience.com/train-test-split-and-cross-validation-in-python-80b61beca4b6)

---

## [**What is Linear Regression:**](https://www.statisticssolutions.com/what-is-linear-regression/)

---

## **Reading Questions:**

1. Prompt: Can you explain the basic concept of linear regression and its purpose in the context of machine learning and data analysis?

  Solution: Linear regression is a basic data analysis technique to fit a linear prediction model onto two sets of variables to see if there is a linear relationship between them. There are standards to measure the quality of the fit (r^2, Coefficient of Determination) and standards to define the relationship as positively correlated or negatively correlated (correlation).

1. Prompt: Describe the process of implementing a linear regression model using Python’s Scikit Learn library, including the necessary steps and functions.

```
# example taken from 'How to Run Linear Regression in Python'

# import numpy, pyplot, and LinearRegression tools
import numpy as np
from sklearn.linear_model import LinearRegression

# create random dependent and independent data in arrays
rnstate = np.random.RandomState(1)
x = 10 * rnstate.rand(50)
y = 2 * x - 5 + rnstate.randn(50)

# create model
model = LinearRegression(fit_intercept=True)

# train on new data
model.fit(x[:, np.newaxis], y)

# generate training data
xfit = np.linspace(0, 10, 1000)

# make predictions based on training data
yfit = model.predict(xfit[:, np.newaxis])
```

1. Prompt: What is the purpose of splitting the dataset into train and test sets, and how does this contribute to the evaluation of a machine learning model’s performance?

  Solution: The purpose is to hold data in reserve for testing. The thinking is that is you only evaluate your model on the same data that it was trained on then it to increase it's score the model will invariably become 'overfit' meaning that it excels at predictions for the current dataset but will struggle with 'fresh' data.

---

## **What I want to learn more about:**

1. Practice, practice, practice. I am opening up Kaggle right now to set a few reps in.

---
---
---