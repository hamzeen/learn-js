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



# sum of even numbers
```js
const nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
const c1 = nums.filter(a => a%2 === 0).reduce((a,b) => a+b, 0);
```

# pagination: pages
```js
Math.ceil(total_items/limit);
```

# group and sort
```js
const inactive = ary.filter(obj => (new Date() - new Date(obj.year) > 0));
const active = ary.filter(obj => (new Date() - new Date(obj.year) <= 0));
active.sort((left, right) => {
  console.log(left.year);
  return left.year - right.year;
});
```


# daysElapsed
```js
function daysElasped(start, end) {
  var diffTime = Math.abs(new Date(end) - new Date(start));
  var diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24)); 
  return diffDays;
}
```
