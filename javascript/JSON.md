# JSON

## 1. FLATTEN
```js
const groups = [
  {
     "id": "+31611111111", 
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
     "id": "+31611111112", 
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
const reservations = [].concat(...flatGroups.map((ap) => ap['seats']));
```


## 2. GROUP
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

## 3. Sum of Even Numbers
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

# 4. Sort & Group
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
