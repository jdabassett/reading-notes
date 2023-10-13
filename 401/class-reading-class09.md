# **Reading Notes:**

---
---
---

## Why are these reading important?

```
```

---

## [**How to Build a Bot and Automate your Everyday Work:**](https://www.freecodecamp.org/news/building-bots/)

* Prompt: Describe the types of automation in Python to automate everyday tasks. What are some possible applications of this knowledge in the real-world context?

  Solution: I asked ChatGPT what the unique types of automation Python can perform. Here they are a few with my short summary.

  * Web Scraping: Automate the extraction of date from websites.
  * GUI Automation: Automate the interactions with a graphical user interface(GUI).
  * Test Processing: Automate tasks related to test processing and analysis
  * Data Extraction, Transformation, and Loading: Automate these tasks.
  * Image Processing: Automate image analysis, video analysis, and object detection.
  * Network Automation: Automate tasks related to network provisioning, configuration, and monitoring.
  * Task Scheduling: Automate creating of recurring tasks.
  * Social Media Automation: Automate and fabricate user actions of social media.
  * Machine Learning and AI: Automate predictive modeling, recommendation systems, and natural language understanding.
  * Internet of Things: Automation with LoT devices.
  * Robotics: Automate repetitive and rule based tasks.

---

## [**Monkey Patching in Python:**](https://medium.com/@bits_code/https-medium-com-bits-code-monkey-patching-in-python-9a28dc0cbe4f)

* Prompt: What is monkey patching in Python? Discuss its benefits and potential risks. Provide an example where monkey patching can be beneficial.

  Solution: A monkey patch is substitute a function, module, class, instance or some other component within a script at runtime. This is can be benefitial for testing as it removes standard behavior into something that is recordable/observable. Here are three examples taken from the reading. Note that you want to remove the patch before closing the script.

```python
# modify module functions
import builtins
original_print = print
def custom_print(*args,**kwargs):
    original_print("boogers",args,kwargs)
builtins.print = custom_print
print("Hello World") #boogers ('Hello World',) {}
builtins.print = original_print
```

```python
# modify class attributes
# will modify for all class instances
class Power():
  def get(self, a, b):
    return a ** b
def mock_power(self, a, b):
  return "mock power"
Power().get(2, 4)			#16
Power.get = mock_power
Power().get(2, 4)	 		#'mock power'
```

```python
# modify instance attributes
# will modify only one class instance
import types
power0 = Power()
power0.get = types.MethodType(mock_power,power0)
power0.get()				#'mock power'
```


---

## [**How to Test Printed Output in Python with Pytest adn its Capsys:**](https://pavolkutaj.medium.com/how-to-test-printed-output-in-python-with-pytest-and-its-capsys-fixture-161010cfc5ad)

* Prompt: How can you use Pytest and its Capsys fixture to test printed output in Python? Can you describe a situation where this technique would be particularly useful?

  Solution: You can use Capsys to capture the stdout from a script, ie all the text from print statements. Then use this captured text to compare against the expected output of script. This would be useful when debugging a complex script with lots of outputs. An example might be a program that performs lots of API requests to then process and analyse the results. This program could contain lots of print statements along the way that could be captured with Capsys and allow for easier debugging when something breaks.

---

## **What I want to learn more about:**

1. I need to practice automation. ChatGPT reference two interesting modules I would like to look into; Pyautogui for process automation and OpenCV for image processing.

---
---
---