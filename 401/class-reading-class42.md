# **Reading Notes: React 4**

---
---
---

## Why are these reading important?

```
Next.js dynamic routes are more a simple and performant way to build a complex and dynamic application.
```

---

## [**Next.js - Dynamic Routes:**](https://nextjs.org/learn/basics/dynamic-routes)


---

## [**Next.js - Deployment:**](https://nextjs.org/learn/basics/deploying-nextjs-app)


---

## [**Next.js 10 is here:**](https://www.youtube.com/watch?v=JWCS5IdECVI)


---

## [**Next.js - Static File Serving:**](https://nextjs.org/docs/basic-features/static-file-serving)


---

## **Reading Questions:**

1. Prompt: Explain the concept of dynamic routes in Next.js and how they differ from static routes.

  Solution: 
  Dynamic routes, as the name entails, are generated at build time rather then hard coded in development like static routes. Often this means that a get request is made to an api at build time to gather the data for these routes before combining the data, html, and javascript to generate functional pages. Think server-side rendering before delivery

1. Prompt: Describe the process of deploying a Next.js application. What are the key steps involved, and what are some deployment platforms you can use?

  Solution: (With the aid of Chatgpt.)
  A Next.js project can be deployed to these hosting services: AWS, Firebase, GitHub Pages, Heroku, Netlify, and Vercel. The easiest and most well integrated might be Vercel since the team at Vercel also develops Next.js itself.
  The steps to deploy a project to Vercel are as follows.
  1. Push the latest updates up to your projects Github repository.
  2. Login to Vercel and establish a link between you Github account and your Vercel account.
  3. Click the path to deploy a new app, choose your project repository from the list of all your Github repositories.
  4. If you have any environmental variables you would need to add those before deployment.
  5. There might be other variables for you can tweak for more advanced projects but for basic projects that is all you need before deploying your project on vercel.


1. Prompt: How does Next.js handle static file serving? Discuss the default folder structure for storing static assets and explain how to reference them in a Next.js application.

  Solution: 
  Next.js realise on the public directory to store static files such as images, icons, fonts, and other static assets. When determining whether a static asset should be stored in the public directory ask the question, "Does this asset require any processing before it's use?" If the answer is no then it likely should be stored in the public directory. 
  You can import resources from the public directory using a relative path from the root directory such as shown below.

```html
<Image src="/public/images/your-image.png" alt="image-x" width="100px" height="100px" />
```

---

## **What I want to learn more about:**

1. Are dynamic routes a verson of server-side rendering?

---
---
---