# Overview React.js

Welcome to reactive programming! React.JS is an open-source fron-end library developed by Facebook.
It was initially made for 3 things:
 * DOM Manipulation
 * Component Management
 * State Management


## some basic concepts

 * virtual DOM
React uses virtual DOM to enhance its performance. It uses the observable to detect state and prop changes. React uses an efficient diff algorithm to compare the versions of virtual DOM. It then makes sure that batched updates are sent to the real DOM for repainting or re-rendering of the UI.

 * PROPS vs STATE
The state is a data structure that starts with a default value when a Component mounts. It may be mutated across time, mostly as a result of user events.
Props (short for properties) are a Component’s configuration. Props are how components talk to each other. They are received from above component and immutable as far as the Component receiving them is concerned.

 * React vs React Native
In Reactjs, virtual DOM is used to render browser code in Reactjs  
while in React Native, native APIs are used to render components in mobile.

## init with CRA

```sh
npx create-react-app react-boilerplate
cd react-boilerplate && npm install
```
```sh
echo "SKIP_PREFLIGHT_CHECK=true" > .env && open .env
npm start
```

# HTTP Calls using Axios

 * Using [State](https://stackblitz.com/edit/react-template-hamzeen)

 * install axios: `npm install axios`

 * import & usage:
```js
import axios from "axios";
import React from "react";

const baseURL = "https://jsonplaceholder.typicode.com/posts";

export default function App() {
  const [post, setPost] = React.useState(null);

  React.useEffect(() => {
    axios.get(`${baseURL}/1`).then((response) => {
      setPost(response.data);
    });
  }, []);

  function createPost() {
    axios
      .post(baseURL, {
        title: "Hello World!", 
        body: "This is a new post."
      })
      .then((response) => {
        setPost(response.data);
      });
  }

  if (!post) return "No post!";
  return (
    <div>
      <h1>{post.title}</h1>
      <p>{post.body}</p>
      <button onClick={createPost}>Create Post</button>
    </div>
  );
}

```


## Declartive vs Imperative Programming
They are 2 different programming paradigms. 

 * Declarative programming: aimed at final result than the process to get there. 
 * Imperative programming: it relies on statements to directly change the state  of an application. An analogy between Declarative vs Imperative programming would be like “saying a carpenter this is how I want my table to look like” vs “instructing him on each step to get your look”. In react when we declare the DOM, we never intend to directly interact/manipulate it. We just simply change the state & react processes the steps under the hood (using observers) to get there. This is one fine example of declarative programming. 


## Reactive (Rx) Programming
it works on 3 pillars:
 * Observable
 * Observers
 * Schedulars


## Quick Ref
 * JWT break down: header. payload. signature
 * SSL: prevent MITM attacks.
 * ESB: service brokering & Orchestration
 * Hoisting, Spread Operator, Event Delegation, Event Loop, Throttle/Debounce


## SOLID Principles
 * S: Single Responsibility
 * O: Open/Close Principle
 * L: Liskov Substitution
 * I: Interface Segregation
 * D: Dependency Inversion


