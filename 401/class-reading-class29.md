
# **Reading Notes: Django Custom User**


## Why are these reading important?

```
Handling user credientials and validation is essential to building more complex and interesting applications. 
```


---

## [**Django Custum User Model:**](https://learndjango.com/tutorials/django-custom-user-model)


---

## [**DjangoX:**](https://github.com/wsvincent/djangox)


---

## [**Creating a Custom User Moel:**](https://www.youtube.com/watch?v=eCeRC7E8Z7Y&t=59s)


---

## [**Abstract User, User Profile and Signals in Django:**](https://www.youtube.com/watch?v=EudKs1HPUfE)


---

## [**Substituting a custom User model:**](https://docs.djangoproject.com/en/3.0/topics/auth/customizing/#auth-custom-user)


---

## READING QUESTIONS:


	1. Prompt: What are the key benefits of using a Django Custom User Model, and how does it differ from the default Django User Model?

		Solution: Created a Custom User Model allows your project the ability of hold additional fields per user, improved security by adding to base features, and allow for more developer choices and control.


	2. Prompt: Explain the process of creating and implementing a Custom User Model in Django, including the necessary changes to settings.py and the required model fields.

		Solution: Summary taken from the first link.
		1. Install basic Django project, create app, and activate local environment.
		2. Inside `app/models.py` create CustomUser class that inherits from django.contrib.auth.models.AbstractUser. Specify user in project settings under variable name `AUTH_USER_MODEL`.
		3. Create form classes that will be used to take user input at user creation (CustomUserCreationForm) or updates (CustomUserChangeForm). 
		4. Create user admin class that incorporates classes from steps 2 and 3. Register this class with and CustomUser class with admin.
		5. Create templates, urls, and views as we have seen previously.
		6. Of note, add `LOGIN_REDIRECT_URL` and `LOGOUT_REDIRECT_URL` to the projects settings.

	3. Prompt: What is DjangoX and how does it complement or extend the functionality of Django? Provide an example use case for incorporating DjangoX in a project.

		Solution: DjangoX is a Django project template that offers a predefined project structure to build from. A use case would be for when starting a new project and wanted to have many of the basic features work from the start.

---

## **What I want to learn more about:**

	1. DjangoX.
	1. UserManager.

---
---
---
