# Overview React.js

React.JS is an open-source fron-end library developed by Facebook.
It was initially made for 3 things:
 * DOM Manipulation
 * Component Management
 * State Management

## Common Hooks in React.js:
 * useState()
 * useContext)
 * useEffects() | componentDidMount, componentDidUpdate, and componentWillUnmount

## Survivial kit
* Unit tests (watch mode): npm run test:unit -- --watch | Press P
* FIX LINT: npm run lint:prettier -- --write
* Tools: JEST/ MOCHA , testing-library chrome add-on


## Techniques to improve performance
* 1.Use React.Suspense and React.Lazy for Lazy Loading Components
* 2.Use React.memo for Component Memoization
* 3.Virtualize a Large List Using react-window
* 4.Don't forget to use production build
* 5.Use React.Fragment to Avoid Adding Extra Nodes to the DOM


## React.memo
React.memo is a great way of optimizing performance as it helps cache functional components.  
In the React World, functions are the `functional components`, & arguments are `props`.

React.memo is a higher-order component and it’s similar to React.PureComponent but for using function components instead of classes. Example:

```js
import React from 'react';

const LabComponent = React.memo(props =>  {
  /* render only if the props changed */
});
```

## Virtual DOM
 * Observable: detetcts prop /state change
 * Diff Algo: compares the versions of virtual DOM then 
 * makes sure batched updates are sent to real DOM for repainting/ re-rendering the UI.

## PROPS vs STATE
The state is a data structure that starts with a default value when a Component mounts. It may be mutated across time, mostly as a result of user events.
Props (short for properties) are a Component’s configuration. Props are how components talk to each other. They are received from above component and immutable as far as the Component receiving them is concerned.

## React vs React Native
In Reactjs, virtual DOM is used to render browser code in Reactjs  
while in React Native, native APIs are used to render components in mobile.


## Declartive vs Imperative Programming
They are 2 different programming paradigms. 

 * Declarative programming: aimed at final result than the process to get there. 
 * Imperative programming: it relies on statements to directly change the state  of an application. An analogy between Declarative vs Imperative programming would be like “saying a carpenter this is how I want my table to look like” vs “instructing him on each step to get your look”. In react when we declare the DOM, we never intend to directly interact/manipulate it. We just simply change the state & react processes the steps under the hood (using observers) to get there. This is one fine example of declarative programming. 


## Reactive (Rx) Programming
it works on 3 pillars: `Observable | Observers | Schedulars`


## Quick Ref
 * For in ... (enumaerates keys)... | For of ... (values)
 * Higher-order Controlled / Uncontrolled Components
