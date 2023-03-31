# **Class12 Reading Notes:**
---
---
---
## Why are these reading important?

```
This will provide a good framework for setting up a rest api.
```

---

## [**Status Codes Based On REST Methods:**](https://www.moesif.com/blog/technical/api-design/Which-HTTP-Status-Code-To-Use-For-Every-CRUD-App/)


*  In your own words, describe what each group of status code represents:

```
  100's codes convey that a request was received and the server is working to fulfill it.

  200's codes convey that a request was received an successfully processed. 

  300's codes convey that a resource is no longer available at the provided location and the server has redirected the request to a different location for processing.

  400's codes convey an error in the request data, format, credentials, or for some other reason.

  500's codes convey server errors. It's the classic it's use not you errors.
```


* What is a status code 202?

  Conveys to client that request is valid and accepted but will take some time to process before any further responses.

* What is a status code 308?

  Conveys a permanent redirect to the right resources.

* What code would you use if an update didn't return data to a client?

  204

* What code would you use if a resource used to exist but no longer does?

  308

* What is the 'Forbidden' status code?

  403

---

## [**Build A REST API With Node.js, Express, & MongoDB - Quick - First 20 minutes:**](https://www.youtube.com/watch?v=fgTGADljAeg)

* Why do we need to pull our MongoDB database string out of our server and put it into our .env?

  For privacy so that it won't be includes in out deployment.

* What is middleware?

  For Express a HTTP request triggers the execution of a list of middleware functions. These functions will parse/handle a resquest and create a response.

* What does app.use(express.json()) do?

  'express.json()' is a middleware function that parses incoming JSON requests and puts the data into req.body.

* What does the /:id mean in a route?

  This is a placeholder for information that will add in the resolution of a request.

* What is a the difference between PUT and PATCH?

  PUT requests must contain all information for a document that will subsequently be replaced by it.

  PATCH requests can contain any portion of a full document while only updating the pertainant parts.

* How do you make a default value in a schema?

  Use the 'required' key along with a boolean of true or false within the declaration of the schema.

* What does a 500 error status code mean?

  Server encountered a condition that prevented the requests fulfillment.

* What is the difference between a status 200 and a status 201?

  200 is a general "all is okay", where as 201 is a more specific "document was successfully created".

---
---
---
## **Things I want to know more about:**

1. How to set up routers using express.router?

