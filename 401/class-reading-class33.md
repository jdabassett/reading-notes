
# **Reading Notes: Authentication & Production Server**


## Why are these reading important?

```
Client authentication is a critical first step in security our apis from bad actors and protecting our clients data.
```


---

## [**JSON Web Tokens:**](https://jwt.io/introduction/)


---

## [**DRF JWT Authentication:**](https://simpleisbetterthancomplex.com/tutorial/2018/12/19/how-to-use-jwt-authentication-with-django-rest-framework.html)


---

## [**Django Runserver Is Not Your Production Server:**](https://build.vsupalov.com/django-runserver-in-production/)


---

## [**White Noise:**](https://whitenoise.readthedocs.io/en/stable/django.html)


---

## [**JWT with DRF:**](https://www.youtube.com/watch?v=Fhcn2qx-4VQ)


---

## [**Gunicorn:**](https://gunicorn.org/)


---

## [**Django Migrations Primer:**](https://realpython.com/django-migrations-a-primer/)


---

## READING QUESTIONS:


	1. Prompt: What is the primary purpose of JSON Web Tokens (JWTs) and how do they work in terms of encoding and decoding data?

		Solution: 
			JWT can be used in web applications between client and server for authentication and/or data transfer. 

			Encoding: 
				Header contains metadata about the token such as the hashing algorithm. Payload holds the information being transfered. Signature in generated from the encoded header, payload, and a secret key to serve as a marker that the token hasn't been altered.

			Decoding: 
				Split token into header, payload, and signature parts. Verify signature with the use of the secret key. If valid, extract payload.


	2. Prompt: 
			How does JWT Authentication integrate with Django REST Framework to secure API endpoints, and what are the key components involved in this process?

			Solution: JWT serves as like a temporary username and password to authenicate client credentials before performing actions such as get, post, put, and delete. 

			The process proceeds as follows:
			1. Client makes get request with username and password to 'token' endpoint to retrieve 'access' and 'refresh' tokens.
			2. Client can use 'access' token at other endpoints as means of authentication while making requests.
			3. Once 'access' token has expired (~5min) a 'get' request can be made with the 'refresh' token to a separate endpoint to gain a new 'access' token. 
			4. Once the 'refresh' token has expired (~24hrs) the process needs to be repeated from the start.

	3. Prompt: Why is Django’s built-in runserver not suitable for production environments, and what are some alternative server options that should be considered for deploying a Django application?

			Solution: 
				Runserver was not built for or scrutinized in a production environment. It wasn't optimized for performance, it isn't kept up to date with the latest security features, and it don't have the reliability metrics to support a project in production.

				For our projects we will be using Gunicorn(green unicorn) in combination with Nginx for our projects.

---

## **What I want to learn more about:**

	1. I wonder how to customize the expiration date/time for a 'access' or 'refresh' token?

	2. I wonder what is the best way to store these token on the front end? State? Local-storage? Secure third-party service?

---
---
---
