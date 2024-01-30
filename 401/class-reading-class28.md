
# **Reading Notes: Django CRUD and Forms**


## Why are these reading important?

```
```


---

## [**Django Forms:**](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Forms)


---

## [**Django Templates:**](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Home_page)


---

## [**Django Views:**](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Generic_views)


---

## READING QUESTIONS:


	1. Prompt: How do Django Forms facilitate user input handling, and what are some key components of creating a form using the Django framework?

		Solution: This is were Django becomes very helpful and opinionated. Django Forms are a class that have many default attributes and methods to aid in Form operations. The key components used to implement a Form are... the data model(optional), form class (inherit from forms.Form or forms.ModelForm), form template (don't forget the csrf_token), and form view (to handle post and get requests from form), 


	2. Prompt: Explain the purpose of Django Templates in web development and describe how template inheritance can be utilized to improve code reusability and maintainability.

		Solution: Templates enable Views to present the data from the Model onto a webpage through injecting that data into the html of a Template. Inheritance removes a lot of duplication and makes maintainance easier when updates need to happen.


	3. Prompt: Describe the function of Django Views in handling HTTP requests, and outline the differences between function-based views and class-based views.
	
		Solution: Views accept an HTTP response and combine the data from specific Models and the HTML from a specific Template to generate new HTML output that can be shared in a response. 
		Function-based views perform this task as a function principle accepting HTTP requests as inputs and returning responses. Where as class-based views can inherit from other class views, create instances based on requests and provide simpler responses as function views. As a rule of thumb function views are simplier and more straightforward; where as class views are more complex but can simplify more complex objectives at least in their mantainance and reusability.

---

## **What I want to learn more about:**

	1. I am across this problem. How can you perform the same task as the following code, `removed because of error` while using the reverse function instead of url? 

		Solution: I think you need to call a model method which in turn leverages the reverse function to generate a url. 
		`<a href="{{ book.author.get_absolute_url }}">{{ book.author }}</a>`

---
---
---
