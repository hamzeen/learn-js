# 1. Utilities

## 1.1. isNumeric | isObjecct
```js
 // isNumeric
 function isNumeric(n) {
  return !isNaN(parseFloat(n)) && isFinite(n);
 }

 // isObject
 function isObject(obj) {
  return ( (typeof obj === "object" || typeof obj === 'function') && (obj !== null) );
 }
```


## 1.2. sum of nums: divisible by 3 & 5
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

## 1.3. get middle char(s)
```javascript
const getMiddle = (s: string): string => {
  const len = (s.length % 2 === 0) ? 2 : 1;
  return s.substr(Math.ceil(s.length/2 - 1), len);
};

export {getMiddle};
console.log("middle:: "+ extractMiddle("ABDC")); // BD
console.log("middle:: "+ extractMiddle("ABD")); // B
```

# 1.4. Average working hours per day
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

# 1.5. Find outlier
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

## 1.6. Why? 0.1 + 0.2 != 0.3
  [reason](https://javascript.plainenglish.io/why-0-1-0-2-0-3-in-javascript-d7e218224a72)


