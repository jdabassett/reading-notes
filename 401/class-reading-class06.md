# **Reading Notes: Random Module, Test Coverage, and Risk Analysis**

---
---
---

## Why are these reading important?

```
The random module is very helpful and will safe us a lot of time writing functions to generate random data. Risk analysis and test coverage are important but nuanced topics that need to be taken with a grain of salt. A grain that you can read more about below!
```

---

## [**How to use Random Module:**](https://www.pythonforbeginners.com/random/how-to-use-the-random-module-in-python)

* Prompt: How can the random module be utilized in Python to generate random numbers or make selections from a list, and what are some common functions available within the module?

```python
#return a random element in range inclusive
random.randint(a,b) #a<=N<=b
#select a random element from list
random.choice(seq)
#select a random element from a weighted list
random.choices(population, weights=None, *, cum_weights=None, k=1)
#shuffle a sequest in place
random.shuffle(list0)
#generate a random float number 0<=N<1
random.random()
```

---

## [**What is Risk Analysis:**](https://www.edureka.co/blog/risk-analysis-in-software-testing/)

* Prompt: In the context of software development, what is risk analysis, and what are the key steps involved in conducting a risk analysis for a software project?

  Solution: It is the identification of points of failure and prioritizing them for testing. Key steps involve searching for risks, analyzing their potential impact, and measuring the risks if possible.
---

## [**Test Coverage:**](https://martinfowler.com/bliki/TestCoverage.html)

* Prompt: What is test coverage and why is it an important (or potentially misleading) metric in software testing?

  Solution: Test coverage is a measure of how much code has been passed through at least one test. It is important to use test coverage as a means of identifying untested code rather than a measure of quality since even at a high rate of coverage the most crucial sections may fall through the cracks.

---

## [**Big O Notation:**](https://www.youtube.com/watch?v=v4cd1O4zkGw)

* Prompt: What is Big O notation, and how is it used to describe the performance of an algorithm? Give an example of an everyday task (not software related) that demonstrates O(N) time complexity.

  Solution: Big O complexity is an approximation of the growth in time and or space needed to solve a problem as the amount of data increases. An example of O(N) might be folding laundry.

---

## [**Python Random:**](https://docs.python.org/3/library/random.html)

* Prompt: How to shuffle a deck of cards?

```python
random.shuffle(deck)
```

---

## [**What is Dependency Injection:**](https://www.freecodecamp.org/news/a-quick-intro-to-dependency-injection-what-it-is-and-when-to-use-it-7578c84fa88f/)

* Prompt: What is a pythonic way to perform dependency injection with classes?

  Solution: Hold a component at initialization and call it when necessary.

```python
class Class():
  def__init__(self):
    self.function=function
  def dependency_injection(self,parameters):
    self.function(parameters)
```

---

## **What I want to learn more about:**

1. I need to branch out and use more functions from the random module.

---
---
---