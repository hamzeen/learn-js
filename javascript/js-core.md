# isNumeric | isObject
```js
 // isNumeric
 function isNumeric(n) {
  return !isNaN(parseFloat(n)) && isFinite(n);
 }

 // isObject
 function isObject(obj) {
  return ( (typeof obj === "object" || typeof obj === 'function') && (obj !== null) );
 }

 function isEmpty(obj){ 
  return (Object.keys(obj).length) === 0;
 }
```

# pagination: pages
```js
Math.ceil(total_items/limit);
```

# daysElapsed
```js
function daysElasped(start, end) {
  var diffTime = Math.abs(new Date(end) - new Date(start));
  var diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24)); 
  return diffDays;
}
```
