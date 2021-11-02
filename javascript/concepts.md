
# Concepts

 * Hoisting, Event Loop

## 01. destructuring
```
const user = {name: 'bertha benz', age: 28, city: 'budapest'}
const {name, age, city} = user;
```

## 02. debounce vs throttling

## 03. Spread operator

## 04. Pass by reference vs Pass by Value
all primitive types are pass by value; others are pass by reference.
```
const a = {} != const b = {};
```

## 05. Nullish coalescing
this (??) is a logical operator that returns its right-hand side operand 
when its left-hand side operand is null or undefined.
```
const foo = null ?? 'default string';
console.log(foo); // 'default string'
const baz = 0 ?? 'default string';
console.log(baz); // 0
```

## 06. Events

### onload(), onContentChecked() & $(document).ready()
onContentChecked() event occurs after the HTML document has been loaded 
(i.e. DOM hierarchy has been fully constructed). 

The DOMContentLoaded event is fired when the document has been completely loaded and parsed, 
without waiting for stylesheets, images, and subframes.  
The onload() event occurs when the documetn and all its resources all loaded.  

$(document).ready() event is jQuery equivalent to DOMContentLoaded

```
$(document).ready(function() {
   console.log( "ready!" );
});
```

