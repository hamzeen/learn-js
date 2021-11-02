
# State of Javascript

Javascript was developed by Brendon Eich as a browser interpreted language within 2 weeks.
Today it can run outside the browser thanks to Node.js which embraces JS anywhere and everywhere paradigm.

## Data Types
  * Undefined | Null | Boolean| String| Symbol | Number | Object


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

