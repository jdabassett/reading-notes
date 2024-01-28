
# **Reading Notes: React 3**


## Why are these reading important?

```
Using context can help move data around a React application and simply the design of our project.
```


---

## [**NextJs:**](https://nextjs.org/learn/basics/getting-started)


---

## [**React Context for Beginners:**](https://www.freecodecamp.org/news/react-context-for-beginners/)


---

## [**Why I’m using Next.js in 2020:**](https://www.youtube.com/watch?v=rtgbaKBhdkk)


---

## [**Learn useContext In 13 Minutes:**](https://www.youtube.com/watch?v=5LrDIWkK_Bc)


---

## [**Next.js Examples:**](https://github.com/vercel/next.js/tree/canary/examples)


---

## READING QUESTIONS:


	1. Prompt: What is React Context, and how does it help in managing state and data sharing in a React application?

		Solution: React Context is a builtin tool for passing state down several components/levels from where the data is held in state to where it will be used. The motivation behind it's creation was to avoid passing data through down through multiple components that wouldn't use or alter it in anyway. This tedium is call 'prop drilling' and is something we should avoid in the design of our React apps and context can help with that.


	3. Prompt: Explain the useContext Hook and how it can be used to access data from a React Context within a functional component.

		Solution: The useContext hook is the downstream half of the context pipeline. With useContext we can unpack the data and functions passed down through context.(see below from ChatGPT) Once unpacked the data and functions can be used basically like any thing passed through props. Note that context is best used for data that is only rarely changed. This rule is for performance reasons to avoid excessive rerenders of all components that access context.

```python
import {useContext} from 'react';
import {MyContext} from 'App.js';

const MyComponent = () => {
  const { myValue, setMyValue } = useContext(MyContext);

  return (
    <div>
      <p>Value from Context: {myValue}</p>
      <button onClick={() => setMyValue('New Value')}>Change Value</button>
    </div>
  );
};
```


	4. Prompt: Describe the purpose of Next.js, and provide an example from the Vercel Next.js Examples reading on how it can be used to build a scalable web application.
	
		Solution:

---

## **What I want to learn more about:**

	1. I need implement context using those custom hooks. I haven't tried that yet.

---
---
---
