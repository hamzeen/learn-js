# JS CORE

# Helpers: isNumeric | isObject | array of 8
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

 // array with 8 objects
 const aryX = new Array(8).fill({name: 'labs'}).map((el, idx ) => 
 ({...el, combine: `name: ${el.name} id: ${idx}`, id: idx}));

 // ensures an array without null objs
 const ar2 = aryX.filter(Boolean).map((obj) => obj.id);

 // unique array
 let unique = [...new Set(items)];

 // pagination: pages
 Math.ceil(total_items/limit);
```

# Scope in JS
```js
// [google's scope question](https://medium.com/coderbyte/a-tricky-javascript-interview-question-asked-by-google-and-amazon-48d212890703)
// here use, let
for(var i=0;i<5;i++) {
  setTimeout(() =>{ 
    console.log("let:", i)
  }, 1000);
}

```

# Sorting

## 1. Basic
```
    return data.sort().reverse(); // for performance
    return data.sort((a, b) => b.name.localeCompare(a.name)); // for unicode
    return data.sort((a, b) => (a.name  - b.name)).reverse(); // otherwise

    // parse a string & then sort
    const str = '[{"name":"eggs","price":1},{"name":"coffee","price":9.99},{"name":"rice","price":4.04}]';
    const obj = JSON.parse(str);
    obj.sort((a, b) => a.price - b.price);

```

## 2. find missing number
```js
var a = [5], n = 5;
var missing = [];
for (var i = 1; i <= n; i++) {
  if (a.indexOf(i) == -1) {
    missing.push(i);
  }
}
console.log(missing);
```


## 2. a weird sort (www.*.no)
```js
// const sample_input =  ['world', '4', 'hello', '2', '3', '1', 'coding', 'test'];
// expected_output => ['coding', '1', 'hello', '2', '3', '4', 'test', 'world'];

function sort(sample_input) {
  const aryNums = sample_input.filter((el)=> el && parseInt(el));  
  aryNums.sort();
  
  // get the strings
  const aryStrs = sample_input.filter((el)=> el && !parseInt(el));
  aryStrs.sort();
  
  const res = [];
  let strCount = 0, intCount = 0;

  for(let i =0 ; i < sample_input.length; i++) {    
    if (parseInt(sample_input[i])) {
      res[i] = aryNums[intCount];
      intCount++;
    } else {      
      res[i] = aryStrs[strCount];
      strCount++;
    }
  }
  console.log(res);
}

```
## 3. Group & Sort
```js
var ary = [
  {
    active: false,
    year: '2023-08-20T00:00:00Z'
  }, {
    active: true,
    year: '2010-08-20T00:00:00Z'
  }
];

const inactive = ary.filter(obj => (new Date() - new Date(obj.year) > 0));
const active = ary.filter(obj => (new Date() - new Date(obj.year) <= 0));
active.sort((left, right) => {
  console.log(left.year);
  return left.year - right.year;
});

const main = { prDetails: active.concat(inactive) }
console.log('main:: ', main);
```


# Aggregation
## 01. Sum of Even Numbers
```js
const nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

const c1 = nums.filter(a => a%2 === 0).reduce((a,b) => a+b, 0);

const sumEvens = (nums) => {
  var total=0;
  for (let i of nums) { 
    if (i%2 ===0) total += i; 
  }
  return total;
}
```
## 02. sum of nums: divisible by 3 & 5
```javascript
export const solution = (number: number): number => {
  let result = 0;
  for (let i = 0; i < number; i++){
    if(i%3 === 0 || i % 5 === 0)
      result += i;
  }
  return result;
};
```
## 03. Find outlier
```javascript
export function findOutlier(integers: number[]): number {
   var evenNums = [];
   var oddNums = [];
   for (let num of integers) { 
       if ((num % 2) == 0)  {
           evenNums.push(num);
       } else {
           oddNums.push(num);
       }
   }
   var elen = evenNums.length;
   var olen = oddNums.length;

   if (elen > olen) {
       return oddNums[0];
   } else {
       return evenNums[0];
   }
}
```


# String Manip
## 01. isPalindrome
```js
const isPalindrome = (str) => 
    str.toLowerCase().split('').reverse().join('') === str.toLowerCase();
console.log(isPalindrome('rAceCar'));
```

## 02. get middle char(s)
```javascript
const getMiddle = (s: string): string => {
  const len = (s.length % 2 === 0) ? 2 : 1;
  return s.substr(Math.ceil(s.length/2 - 1), len);
};

export {getMiddle};
console.log("middle:: "+ extractMiddle("ABDC")); // BD
console.log("middle:: "+ extractMiddle("ABD")); // B
```

## 03. Title Case
```js
// https://betterprogramming.pub/common-javascript-algorithm-interview-questions-explained-68d8c4186270
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

## 04. Altered SOS Messages
A space explorer's [ship](https://www.hackerrank.com/challenges/mars-exploration/problem) crashed on Mars! They send a series of SOS messages to Earth for help.

Letters in some of the SOS messages are altered by cosmic radiation during transmission. Given the signal received by Earth as a string, s, determine how many letters of the SOS message have been changed by radiation.

[Example](https://hackerranksolution.in/marsexplorationalgo/)

s = 'SOSTOT'

```javascript
function morseCode(str) {
  const chars = str.trim().split('');
  let altered = 0;
  for (let i= 0; i < chars.length; i++) {
    if (i%3 == 1) {
      if (chars[i]!=='O') {
        altered++;
      }
    } else {
      if(chars[i] !== 'S') {
        altered++;
      }
    }    
  }
  return altered;
}

console.log('LC1:: ' + morseCode('SOSTOT')); //2
console.log('LC2:: ' + morseCode('SOSSPSSQSSOR')); //3

// Method 2
function marsExploration(s) {
  let sosCount = s.length/3;
  let original = "SOS".repeat(sosCount);
  let errorCount = 0;
  
  for(let i = 0; i < s.length; i++){
    if(s[i] != original[i]){
      errorCount++;
    }
  }
  
  return errorCount;
}
```

# Date
## 01. daysElapsed
```js
function daysElasped(start, end) {
  var diffTime = Math.abs(new Date(end) - new Date(start));
  var diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24)); 
  return diffDays;
}
```
## 02. Format Date
```js
// date fromat dd-mm-yyyy
const now = new Date();
const date = now.toISOString().split('T')[0];
const newFormat = date.split('-').reverse().join('-');
console.log(newFormat):
```
## 03. Average working hours per day
```javascript
export function averagePerDay(hours: string[]): number {
  if (typeof hours !== 'undefined' && hours.length === 0) {
    return 0;
  }
  const uniqueDays = new Set();
  let time = 0;

  for (let str of hours) {
    const parts = str.split(";");

    let date = parseInt(parts[0]) ? new Date(parseInt(parts[0])) : new Date(parts[0]);
    uniqueDays.add(date.toString());
    time = time + parseFloat(parts[1]);
  }

  // console.log("time: " + time * 60);
  // console.log("days: " + uniqueDays.size);
  let strRes = 60 * time / uniqueDays.size;
  return parseFloat(strRes.toFixed(1));
}

# testcase
const input = [ 
  "1609459200;1.5",   // 1.5 hours on 1st of January
  "2021/01/03;6",     // 6 hours on 3th of January
  "2021/01/01;1.5",   // 1.5 hours on 1st of January 
  "2021/01/01;1"      // 1 hours on 1st of January
];
const result = averagePerDay(input);
console.log("LC::" + result); // 300 (5 hours)
```



# JSON
## 01. FLATTEN
```js
const groups = [
  {
     "id": "+91611111111", 
     "seats":[{
       "section":"main hall",
       "row":"1",
       "seat":"4"
     }, {
       "section":"main hall",
       "row":"1",
       "seat":"3"
     }] 
  },
  {
     "id": "+91611111112", 
     "seats":[{
           "section":"balcony",
           "row":"1",
           "seat":"1"
       }, {
           "section":"balcony",
           "row":"1",
           "seat":"2"
       }]
  }];
const reservations = [].concat(...groups.map((ap) => ap['seats']));
```

## 02. GROUP
```js
const cars = [
   { make: 'audi', model: 'r8', year: '2012' }, 
   { make: 'audi', model: 'rs5', year: '2013' }, 
   { make: 'ford', model: 'mustang', year: '2012' }, 
   { make: 'ford', model: 'fusion', year: '2015' }, 
   { make: 'kia', model: 'optima', year: '2012' }
];

const groupByMake = (ary) => {
  return ary.reduce(function (prev, curr) {
        prev[curr.make] = prev[curr.make] || [];
        prev[curr.make].push(curr);
        return prev;
    }, Object.create(null));
}
console.log(groupByMake(cars));
```

# Dictionary / i18n

## 01. Dictionary Months
```js
// translation from keys
const monthNames = {
  '1': 'Januari', '2': 'Februari', '3': 'March',
  '4': 'April', '5': 'Mei', '6': 'Juni',
  '7': 'Juli', '8': 'Augustus', '9': 'September',
  '10': 'Oktober', '11': 'Novemebr', '12': 'December'
}
const monthName = `month translation: ${monthNames[date.getMonth() + 1]}`;
```

## 02. Templating (i18n)
```js
const interpolate = function (text, data) {
  if (!text) {
    return 'no input was provided';    
  } else {
    let template = text;

    template = template.replace(/\{\{([^}]+)\}\}/g, (match) => {
      
      match = match.slice(2, -2); // removes curly braces, either sides
      if (!data[match]) {
        return '{{' + match + '}}';
      }
      return data[match];
    });
    return template;
  }
};

var options = {	liquid: 'water', temperature: '100'};
const txtToParse = 'the {{liquid}} boils at {{temperature}} degrees celsius';
const txtResult = interpolate(txtToParse, options);
```

# Misc.
 * Why? 0.1 + 0.2 != 0.3: 
  [reason](https://javascript.plainenglish.io/why-0-1-0-2-0-3-in-javascript-d7e218224a72)
* JS performance: <https://jsperf.com/>
* beginner to intermediate [questions](https://www.edureka.co/blog/interview-questions/javascript-interview-questions/)
* comomn [mistkaes](https://www.toptal.com/nodejs/top-10-common-nodejs-developer-mistakes) by nodejs devs

