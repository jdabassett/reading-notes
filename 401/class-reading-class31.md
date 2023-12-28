
# **Reading Notes: Django REST Framework & Docker**


## Why are these reading important?

```
Docker allows developers to share their creations and be confident they will have all dependencies at runtime.
```


---

## [**Beginner’s Guide to Docker:**](https://wsvincent.com/beginners-guide-to-docker/)


---

## [**Django for APIs - Library Website:**](https://djangoforapis.com/library-website-and-api/)


---

## [**Beginner’s Guide to Django REST Framework:**](https://learndjango.com/tutorials/official-django-rest-framework-tutorial-beginners)


---

## READING QUESTIONS:


	1. Prompt: What are the key components of a Docker container, and how do they help streamline the development and deployment of applications?
		
		Solution: A Docker container is made up of...
			* Dockerfile that contains all the commands/ingredients to build an image.
			* Image is a 'snapshot' of a docker container.
			* .dockerignore specifies project elements that should be left out of image.
			* docker-compose.yml are the 'instructions' on how to implement a container independently or alongside other containers.


	3. Prompt: Describe the primary steps involved in building a library website using Django, including essential components like models, views, and templates.

		Solution:
		 1. Create a traditional Django project directory.
		 2. Add a library app. Add it to the project settings.
		 3. Add routes to project url mapper.
		 4. Create library model within app.
		 5. Make migrations for new model.
		 6. Register model with admin.
		 7. Can add data to database fitting model schema either through shell or admin page.
		 8. Create ListView and connect to library model and library template.
		 9. Create library template that will display data from database.
		 10. Create url.py file in library app that extends project url mapper. Create routes that leverage ListView.

		 Tests: Don't forget to write tests to maintain this code.


	4. Prompt: Can you explain the primary differences between Django and Django REST framework?

		Solution: Django is designed to create a full stack web application where as Django REST is a framework for creating an API handling HTTP requests. Django and Django REST can be integrated into the same application but are optimized for difference purposes.

---

## **What I want to learn more about:**

	1. So much more practice on Docker. 

---
---
---
