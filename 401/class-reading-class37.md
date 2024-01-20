
# **Reading Notes: React 1**


## Why are these reading important?

```
Because we are full-stack web developers and there is no hotter framework for the front of our project than REACT!
```


---

## [**ES6 Syntax and Feature Overview:**](https://www.taniarascia.com/es6-syntax-and-feature-overview/)


---

## [**React - Hello World:**](https://reactjs.org/docs/hello-world.html)


---

## [**React - JSX:**](https://reactjs.org/docs/introducing-jsx.html)


---

## [**React - Rendering Elements:**](https://reactjs.org/docs/rendering-elements.html)


---

## [**React - Components & Props:**](https://reactjs.org/docs/components-and-props.html)


---

## [**React - State & Lifecycle:**](https://reactjs.org/docs/state-and-lifecycle.html)


---

## [**React - Handling Events:**](https://reactjs.org/docs/handling-events.html)


---

## [**Utility First CSS:**](https://tailwindcss.com/docs/utility-first)


---

## [**Tailwind in a few min minutes:**](https://www.youtube.com/watch?v=pB1oed_10IA)


---

## [**Learn Next.js:**](https://nextjs.org/learn/basics/create-nextjs-app)


---

## [**Why to use Next.js:**](https://www.youtube.com/watch?v=rtgbaKBhdkk)


---

## READING QUESTIONS:


	1. Prompt: In the context of ES6 Syntax and Feature Overview, what are three key features introduced in ES6 that improve upon the previous version of JavaScript, and briefly explain their benefits?

		Solution: 
		1.1. The introduction of the let and const keywords for variable declaration. The allow for additional features that contrast well with the var keyword.
| keyword | scope    | hoisting | reassignable | redeclarable |
|---------|----------|----------|--------------|--------------|
| var     | function | yes      | yes          | yes          |
| let     | block    | no       | yes          | no           |
| const   | block    | no       | no           | no           |

		1.2. Loop iteration is much easier.

```javascript
// ES5
for (var i = 0; i < arr.length; i++) {
  console.log(arr[i])
}

// ES6
for (let i of arr) {
  console.log(i)
}
```

		1.3. You don't need to use prototype to add methods to a constructor function.

```javascript
// ES5
function Func(a, b) {
  this.a = a
  this.b = b
}

Func.prototype.getSum = function () {
  return this.a + this.b
}

var x = new Func(3, 4)

// ES6
class Func {
  constructor(a, b) {
    this.a = a
    this.b = b
  }

  getSum() {
    return this.a + this.b
  }
}

let x = new Func(3, 4)
```

		1.4. Inheritance is a lot more straight-forward.

```javascript
// ES5
function Inheritance(a, b, c) {
  Func.call(this, a, b)

  this.c = c
}

Inheritance.prototype = Object.create(Func.prototype)
Inheritance.prototype.getProduct = function () {
  return this.a * this.b * this.c
}

var y = new Inheritance(3, 4, 5)

// ES6
class Inheritance extends Func {
  constructor(a, b, c) {
    super(a, b)

    this.c = c
  }

  getProduct() {
    return this.a * this.b * this.c
  }
}

let y = new Inheritance(3, 4, 5)
```



	2. Prompt: After reading “Tailwind in 15 minutes,” can you describe the purpose of utility classes in Tailwind CSS and provide an example of how to use them to style an HTML element?

		Solution: Utility classes provide a low-level way to apply styling directly to HTML elements, without the need for writing custom CSS. (The following example is takend from the Utility-First CSS link above.)
	
```html
<!-- without Tailwind -->
<div class="chat-notification">
  <div class="chat-notification-logo-wrapper">
    <img class="chat-notification-logo" src="/img/logo.svg" alt="ChitChat Logo">
  </div>
  <div class="chat-notification-content">
    <h4 class="chat-notification-title">ChitChat</h4>
    <p class="chat-notification-message">You have a new message!</p>
  </div>
</div>

<style>
  .chat-notification {
    display: flex;
    max-width: 24rem;
    margin: 0 auto;
    padding: 1.5rem;
    border-radius: 0.5rem;
    background-color: #fff;
    box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
  }
  .chat-notification-logo-wrapper {
    flex-shrink: 0;
  }
  .chat-notification-logo {
    height: 3rem;
    width: 3rem;
  }
  .chat-notification-content {
    margin-left: 1.5rem;
    padding-top: 0.25rem;
  }
  .chat-notification-title {
    color: #1a202c;
    font-size: 1.25rem;
    line-height: 1.25;
  }
  .chat-notification-message {
    color: #718096;
    font-size: 1rem;
    line-height: 1.5;
  }
</style>

<!-- with Tailwind -->
<div class="p-6 max-w-sm mx-auto bg-white rounded-xl shadow-lg flex items-center space-x-4">
  <div class="shrink-0">
    <img class="h-12 w-12" src="/img/logo.svg" alt="ChitChat Logo">
  </div>
  <div>
    <div class="text-xl font-medium text-black">ChitChat</div>
    <p class="text-slate-500">You have a new message!</p>
  </div>
</div>
```


	3. Prompt: Based on “Why to use Next.js,” explain the main advantages of using Next.js for web development, and provide a brief comparison between traditional client-side rendering and Next.js’s server-side rendering approach.
		
		Solution: The Next.js framework enables developers to perform.. (Results taken from ChatGPT and rewritten.)
		3.1. Serve-Side Rendering for more involved dynamic content.
		3.2. Client-Side Rendering for simpler less dynamic content.
		3.3. Code Splitting to make the web app more efficient and performant.
		3.4. Built-in Routing to simply its implementation.
		3.5. API Routes to simplify the building of serverless functions.
		3.6. Static Site Generation that can be pre-rendered at build time.
		3.7. Great tools for TypeScript integration.
		3.8. Data fetching methods.
		3.9. Lots of plugins and features.

		Client-Side Render(CSR): The server sends some HTML and Javascript for the client's browser to run and render. Benefits are the shifting of work and cost the the client. Downside is the speed can be reduced as download and execution are bundled.

		Next.js Server-Side Render(SSR): The server sends fully rendered HTML reducing the amount of JavaScript the client must execute. Benefits are that the experience can be must faster, especially for very complex and dynamic applications. Downside the server capacity must increase; along with the additional computational costs that do with that.

---

## **What I want to learn more about:**

	1. So much to practice and lots of rust to kick off. I am interested most in practicing with Tailwind.

---
---
---
