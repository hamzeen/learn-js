
# 1. State of Javascript

Javascript was developed by Brendon Eich as a browser interpreted language within 2 weeks.
Today it can run outside the browser thanks to Node.js which embraces JS anywhere and everywhere paradigm.

 * Babel: converts ES6+ code to backward compatibale JS for legacy browsers. A transpiler (special type compiler)
 * Data Types: Undefined | Null | Boolean| String| Symbol | Number | Object
 * Scopes: `global`, `local` & `block-scope`
 * Engines: Edge - Chakra, Spider Monkey - Firefox, V8 - Chrome

# 2. Path to Nodejs

## 2.1. V8 (Lars Bak, Danish Developer)
V8 was menat to improve performance of rendering in Chrome.
The team cam up with a break through idea to convert javascript into machine code and then subsequently byte code. This was toally new got traction real fast as it drastically improved rendering speeds within Chrome.


## 2.2. NODE.js (Ryan Dahl)
the v8 engine paved the way for Node.js with v8, javascript was no longer 
a browser interpreted language it could be compiled outside.  
Node.js took advantage of this & showed that JS could now be used to build servers & 
it could be used for server side programming. Node.js promotes anywhere & everywhere paradigm for Javascript.  

Hence it enabled js to be used even for desktop applications. Ex: Electron (CodeEditor: Atom).

* Simple Server: `npx http-server -a 0.0.0.0 -p 8000`

## 2.3. Sorting inside different JS Engines
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
