# 1. Concepts

## 1.1. Hoisting
In JavaScript, Hoisting is the default behavior of moving all the declarations at the top of the scope before code execution. It gives the advantage no matter where functions and variables are declared, they are moved to the top of their scope regardless of whether their scope is global or local.

This is okay:
```js
a = "Volvo";
var a; // 'Volvo'
```

But not this:
```js
b = "Volvo";
let b; // Uncaught SyntaxError: Missing initializer in const declaration

c = "Volvo";
const c;
```
* Note: JavaScript in strict mode does not allow variables to be used if they are not declared. `use strict`

## 1.2. destructuring
```
const user = {name: 'bertha benz', age: 28, city: 'budapest'}
const {name, age, city} = user;
```

## 1.3. Spread operator
it presents a neat alternative to most array functions like:  
`unshift()`, `shift()`, `pop()`, `concat()`

```js
 // array with 8 objects
 const aryX = new Array(8).fill({name: 'labs'}).map((el, idx ) => 
 ({...el, combine: `name: ${el.name} id: ${idx}`, id: idx}));
```

## 1.4. Reference vs Pass by Value
all primitive types are pass by value; others are pass by reference.
```
const a = {} != const b = {};
```

## 1.5. Event Loop

## 1.6. Asynchronous JS

### Asyn/Await vs Promises
```js
var p1 = new Promise(function(resolve, reject) {
	setTimeout(function() { resolve('First!'); }, 8000);
});
var p2 = new Promise(function(resolve, reject) {
	setTimeout(function() { reject('Second!'); }, 6000);
});
Promise.all([p1, p2]).then(function(results) {
	console.log('Resolved: ', results);
}).catch(function(err) {
	console.log('Catch: ', err);
});

// From the console:
// Catch: Second!
```


## 1.8. debounce vs throttling

## 1.9. Nullish coalescing
this (??) is a logical operator that returns its right-hand side operand 
when its left-hand side operand is null or undefined.
```
const foo = null ?? 'default string';
console.log(foo); // 'default string'
const baz = 0 ?? 'default string';
console.log(baz); // 0
```

## 1.10. Event Delegation

## 1.11. Events

### onload(), onContentChecked() & $(document).ready()
The onload() event occurs when the document and all its resources are loaded.

onContentChecked() event occurs after DOM hierarchy has been fully constructed. 
This event is fired when the document has been completely loaded & parsed, 
without waiting for stylesheets, images and subframes. `$(document).ready()` 
event is jQuery equivalent to `DOMContentLoaded`

```js
$(document).ready(function() {
   console.log( "ready!" );
});
```



# 2. Design

## SOLID Principles
 * S: Single Responsibility
	* class should have only one reason to change.
 * O: Open/Close Principle
	* software entities (classes, modules, methods, etc.) should be open for extension, but closed for modification
 * L: Liskov Substitution
 * I: Interface Segregation
 * D: Dependency Inversion
	* high level modules should not depend on low level modules; both should depend on abstractions. Abstractions should not depend on details.  Details should depend upon abstractions.

## Quick Ref:
 * JWT: header. payload. signature
 * ESB: service brokering & Orchestration
 * OOP: Abstraction, Inheritance, Encapsulation, Ploymorphism
 * Angular: 2-way binding; React: 1-way binding
 * TDD: react - Jest, Mocha; Angular - jasmine
 * pre-processors: PHP, SCSS


# 3. CSS / SCSS
 * Mixin: re-use styles. ex: horizontal-list
 * Mixin: Nesting Selectors, Inheritance Selectors
 * Frameworks Bootstrap, Tailwind


# 4. Databases / Backend
 * DB Transaction: unit of work that's completed or undone as a unit.
 * Http verbs Put vs Patch


# 5. Backend
 * Microservices: arranges an app into loosely coupled services. Variant of SOA structual style.
 * Micro Front-ends: organizes an front-end into loosely coupled modules.
 * SSL: prevent MITM attacks
 * HTTPS: makes a secure connection by establshing an *encrypted link* between the browser & the server or between 2 systems.
 
 