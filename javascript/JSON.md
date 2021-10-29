# JSON

# sum of even numbers
```js
const nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
const c1 = nums.filter(a => a%2 === 0).reduce((a,b) => a+b, 0);
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
