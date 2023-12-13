
# **Reading Notes: Django Models**


## Why are these reading important?

```
Django models are the bridge between a 'backend' and the 'databases' it relys on. Understanding how to work with them will help us utilize stored data from a variaty of database types.
```


---

## [**Using Models:**](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Models)


---

## [**Django Admin:**](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Admin_site)


---

## [**Beginner’s Guide to Django - Part 1:**](https://simpleisbetterthancomplex.com/series/2017/09/04/a-complete-beginners-guide-to-django-part-1.html)


---

## [**Beginner’s Guide to Django - Part 2:**](https://simpleisbetterthancomplex.com/series/2017/09/11/a-complete-beginners-guide-to-django-part-2.html)


---

## READING QUESTIONS:

	1. Prompt: Explain the purpose and basic structure of Django models. How do they help in creating and managing database schema in a Django application?

		Solution: Models are an abstraction to interact with the underlying data within databases. Models define the schema and fields of a model and their relationship with separate models.

    Models help in the creation and maintanance of a schema through the field attributes of their classes and the parameters supplied to those fields. Additionally the model metadata can provide instructions for a models's fields should be ordered, labeled or otherwise managed.


	2. Prompt: Describe the primary features and functionality of the Django Admin interface. How can it be customized to suit the specific needs of a project?

		Solution: A big feature of the admin interface is the ability to create and manage data within each model.

    As far as how the Admin Interface can be further customized. This is what ChatGPT has taught me.
    - Site Configurations: Primarily registering and managing models.
    - Templates: Override the default admin templates.
    - Add Actions and Views: Create custom actions to perform bulk operations and create views to display additional information in a custom fashion.
    - Inline Models: Use inline models to edit related models on the same page.
    - Urls and Navigation: Customize admin navigation and override admin urls.
    - Filters and Search: Add custom filters and search methods for each model.
    - Third-Party Extensions: Employ third party extensions to enhance the admin interface.
    - Access Control: Customize access controls based on user roles and permissions.


	3. Prompt: Briefly outline the key components and workflow of a Django application, as discussed in the Beginner’s Guide to Django. How do these components interact with each other to create a functional web application?
		
    Solution: A request comes into the URL mapper, which forwards it to the correct View component. Each View will incorporate combinations of Templates and Models to generate a dynamic webpage that can be provided as a response.
---

## **What I want to learn more about:**

	1. Lots of questions about Models. Primarily how to make connects between models in a one to one, one to many, or many to many fashion?

---
---
---
