
# **Reading Notes: React 2**


## Why are these reading important?

```
This reading will help us review and remember what we have learned so that we can build confident that we are following best practices.
```


---

## [**React - Conditional Rendering:**](https://reactjs.org/docs/conditional-rendering.html)


---

## [**React - Lists & Keys:**](https://reactjs.org/docs/lists-and-keys.html)


---

## [**React - Forms:**](https://reactjs.org/docs/forms.html)


---

## [**React - Lifting State:**](https://reactjs.org/docs/lifting-state-up.html)


---

## [**React - Composition vs Inheritance:**](https://reactjs.org/docs/composition-vs-inheritance.html)


---

## [**Thinking in React:**](https://reactjs.org/docs/thinking-in-react.html)


---

## [**React - Comprehensive Guide:**](https://tylermcginnis.com/reactjs-tutorial-a-comprehensive-guide-to-building-apps-with-react/)


---

## [**Heroicons:**](https://heroicons.com/)


---

## READING QUESTIONS:


	1. Prompt: How does lifting state up in a React application help with managing data flow and what are the benefits of using this approach?

		Solution: It simplies data management as there is a single data source. This has the benefit of consolidating potential bugs and eliminating redundant data handling/management. Can be more performant as it can reduce rerenders. Also simplifies development either as code expands or contracts.


	2. Prompt: Explain the concept of conditional rendering in React and provide an example of how to implement it in a component.

		Solution: Conditional rendering is the practice of rendering components based on criteria of data supplied to the component themselves or a data for a separate component/purpose. My favorite examples from the first reading in the first link is as follows.

```Javascript
// conditional return
function Greeting(props) {
  if (props.isLoggedIn) {
    return Null;
  }
  return <GuestGreeting />;
};

// conditional variable assignment
function Greeting(props) {
    let button;
    if (props.isLoggedIn) {
      button = <LogoutButton/>;
    } else {
      button = <LoginButton/>;
    };
    return (
			<>{button}</>
    );
};

// conditional logic operator
function Greeting(props) {
    return (
			<>{props.isLoggedIn && <Button/>}</>
    );
};

//  conditional ternary
function Greeting(props) {
    return (
			<>{props.isLoggedIn ? <Button1/>: <Button2/>}</Button2>
    );
};
```


	3. Prompt: What are the main principles behind “Thinking in React” and how do they guide the process of designing and building a React application?

		Solution: These steps taken in the proper order will enable better design of React applications as many truths/simplification will become self evident as each facet is encountered in it's turn.

		1. Divide the wireframe into components based on their role. You can define what should be a component and what type by asking questions like these. Is this component presenting a type of data? Are they accepting data? How are they grouped?
		2. Build a static version of your design. This will help put off a lot of complexity and allow for ideas to percolate in.
		3. Define the minimum dataset that will enable your application. No sense building in redundancy, simply as much as possible.
		4. Establish that data/state in a component that can easily share it with all others that need it.
		5. Enable interaction between children components and state.

---

## **What I want to learn more about:**

	1. I want to practice more with passing components as props. I have never done this before and wonder what the benefit might be?

---
---
---
