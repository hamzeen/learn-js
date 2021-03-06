# asynchronous javascript

## Callbacks
As it grows, it is difficult to read, debug and maintain, it leads to callback hell.

## Promises



## Async Await

* async/await is syntactic sugar around promises & 
provides a way to handle the asynchronous tasks in a synchronous manner. 
* async functions can contain zero or more await expressions. 
* Await expressions make promise-returning functions behave as though they're synchronous.

* async/await has 4 simple rules:

    * A function handling an asynchronous task must be marked using the async keyword.
    * await promise operator pauses the function execution until promise is either resolved successfully or rejected.
    * If promise resolves successfully, the await operator returns the resolved value: const resolvedValue = await promise. Otherwise, you can catch a rejected promise inside try/catch.
    * An async function always returns a promise, which gives the ability to nest async functions.

## the famous timeout trivia
```js
for(var i = 0; i < 5; i++) {
  setTimeout(() => { 
    console.log("var:", i)
  }, i * 1000);
} // 5 times 5 is printed

for(let i = 0; i < 5; i++) {
  setTimeout(() => { 
    console.log("var:", i)
  }, i * 1000);
} // prints from 0 to 4 in 5 secs.

OR...
for(var i = 0; i < 5; i++) { 
  function closure(i) {
    setTimeout(() => { 
      console.log("var:", i)
    }, i * 1000);
  }
  closure(i);
} // prints from 0 to 4 in 5 secs.
```
