# **Reading Notes: Serverless, Vercel, venv and API requests**

---
---
---

## Why are these reading important?

```
These readings will help us as python developers understand the serves that process our http requests and how we make those requests.
```

---

## [**What is Serverless Computing:**](https://www.ibm.com/cloud/learn/serverless)

---

## [**Creation of Virtual Environments:**](https://docs.python.org/3/library/venv.html)

---

## [**Vercel- Get Started:**](https://vercel.com/docs/get-started)

---

## [**http.server:**](https://pymotw.com/3/http.server/index.html)

---

## [**Requests){:target=”_blank”}:**](https://requests.readthedocs.io/en/latest/)

---

## [**Python and APIs:**](https://realpython.com/python-api/)

---

## [**What is Serverless?**](https://www.youtube.com/watch?v=vxJobGtqKVM)

---

## [**Serverless Functions:**](https://vercel.com/docs/concepts/functions/serverless-functions)

---

## [**Effective Python Environment:**](https://realpython.com/effective-python-environment/)

---

## READING QUESTIONS:

1. Prompt: What are the key characteristics of serverless computing, and how does it differ from traditional server-based architectures?

  Solution: Serverless computing removes server management from the developer and provides computation as a service. It means that developers don't need to become experts in creating and maintaining servers. For smaller applications it is also can be much cheaper than the upfront costs of creating a dedicated server.

1. Prompt: How can one get started with Vercel, and what are the main steps involved in deploying a serverless function using Vercel?

  Solution: Make a Vercel account, connect it to your github, select a respository, and deploy.

1. Prompt: What are APIs, and how can they be utilized in Python applications to access and manipulate data from external sources?

  Solution: API are interfaces to gain information, add to records, update records, and delete records in an external resource. They can be accessed from our python scripts through the functionality provided from the requests library. (see below)

1. Prompt: What is the Requests library in Python, and how can it be used to interact with APIs by sending HTTP requests? Can you provide an example of a basic GET request using the Requests library?

  Solution: Requests is a class that can provide a tremendous amount of functionality. Such as formating a request with custom attributes, making requests, providing lots of information about the response, and formating the response. See below.

```python
#import request library
import requests
# make custom headers and parameters
headers = {"query-type": "query"}
query_params = {"api_key": api_key}
# to make request
res = requests.get("url", headers=headers, params=query_params)
# to check status code
res.status_code
# find reason for failure
res.reason
# access contents
res.text
# access header attributes and values
res.request.headers.get('Content-Type")
# review request method
res.request.method
# review request url
res.request.url
# convert contents into usable format
res.json()
```

## **What I want to learn more about:**

1. How to work with Vercel!

---
---
---