```javascript

var ary = [
  {
    active: false,
    year: '2023-08-20T00:00:00Z'
  }, {
    active: true,
    year: '2010-08-20T00:00:00Z'
  }, {
    active: false,
    year: '2025-08-20T00:00:00Z'
  }, {
    active: true,
    year: '2020-08-20T00:00:00Z'
  }, {
    active: true,
    year: '2029-08-20T00:00:00Z'
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
