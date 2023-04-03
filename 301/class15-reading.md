# **Class15 Reading Notes:**
---
---
---
## Why are these reading important?

```
After these reading you will have a better understanding of how third party authenication works over the web.
```

---

## [**What is OAuth:**](https://www.csoonline.com/article/3216404/what-is-oauth-how-the-open-authorization-framework-works.html)

* What is OAuth?

  Is an open-standard authorization protocol/framework that allows separate websites/services to safely share user credentials so that they can avoid signing into each service separately.

* Give an example of what using OAuth would look like?

  When a client asked to login there will be presented with multiple ways to show their credentials through the selection of separate services whose credentials they can easily supply. (Facebook, Twitter, Google, GitHub...)

* How does OAuth work? What are the steps that it takes to authenticate the user?

  1. Credentialed site connects to Login site on behalf of the client to verify their identity.
  1. Login site generate token and secret unique to the transaction and parties involved. Gives them to the Credentialed site.
  1. Credentialed site gives this token and secret to the client.
  1. If not already authenticated, the client can ask to be authenicated by Login site. After authentication the Login site asks for authorization for given transaction with Credentialed site.
  1. Client/software approves.
  1. Login site gives client an access token.
  1. Client gives access token to Credentialed site.
  1. Credentialed site gives access token back to the Login site as proof of authentication.
  1. Credentialed site authorizes Login sites transaction.

* What is OpenID?

  Is software then complements the implementation of OAuth by focusing on client authentication steps.

---

## [**Authorization and Authentication flows:**](https://auth0.com/docs/flows)

* What is the difference between authorization and authentication?

  Authenication is demonstrating ownership over an asset, where as authorization is the approval granted to third-parties to access that asset.

* What is Authorization Code Flow?

  Is a process of exchanging an authorization code for an access token.

* What is Authorization Code Flow with Proof Key for Code Exchange (PKCE)?

  Is is the same as Authorization Code Flow only with the additional use of a proof key for added security. Use especially for  mobile, native applications.

* What is Implicit Flow with Form Post?

  Implicit Flow is an less secure alternative to Authorization Code Flow intended for application unable to securely store client data. Implicit Flow can be used in conjunction with Form Post

* What is Client Credentials Flow?

  For machine to machine applications a server will authenicate/authorize an app rather than a user.

* What is Device Authorization Flow?

  For input constrained devices a server/database will authenicate/authorize a device rather than a user.

* What is Resource Owner Password Flow?

  Highly trusted application can use this to request client credientials through a form. (Prefer Authorization Code Flow to this.)

---

## [**Auth0 for single page apps:**](https://auth0.com/docs/libraries/auth0-react)


---
---
---
## **Things I want to know more about:**

1. I want to practice using AuthO React SDK.

