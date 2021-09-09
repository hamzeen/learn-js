
# State of Javascript





## pagination: total number of pages

```javascript
Math.ceil(total_items/limit);

// 50 items / 10 per page = 5 pages
// 55 items / 10 per page = 6 pages
```

## Title Case [blog post](https://betterprogramming.pub/common-javascript-algorithm-interview-questions-explained-68d8c4186270)
```
function upperCaseFirst(inputStr) {
    var valueOfFirstChar = inputStr.charCodeAt(0);

    var upperCaseLetter = String.fromCharCode(valueOfFirstChar - 32);
    var restOfString = inputStr.slice(1);
    return upperCaseLetter + restOfString;
 }

 function titleCase(inputStr) {
  return inputStr.split(' ').map(w => upperCaseFirst(w)).join(' ');
 }
 console.log(titleCase('i am a way shorter implementation'));
```


## Sorting inside different JS Engines
* `arrays.sort` in v8 engine uses Quick Sort but Insertion Sort for an arrays with 10 or less items. [ref](https://blog.shovonhasan.com/time-space-complexity-of-array-sort-in-v8/); Firefox uses merge sort.
```js
function QuickSort(a, from, to) {
    var third_index = 0;
    while (true) {
      // Insertion sort is faster for short arrays.
      if (to - from <= 10) {
        InsertionSort(a, from, to);
        return;
    } 
    ...
```


# trivia/tools
* The data types supported by JavaScript are:
  * Undefined | Null | Boolean| String| Symbol | Number | Object
* JS performance: <https://jsperf.com/>
* beginner to intermediate [questions](https://www.edureka.co/blog/interview-questions/javascript-interview-questions/)
* comomn [mistkaes](https://www.toptal.com/nodejs/top-10-common-nodejs-developer-mistakes) by nodejs devs
* Variable Scopes in JS: [google's scope question](https://medium.com/coderbyte/a-tricky-javascript-interview-question-asked-by-google-and-amazon-48d212890703)

