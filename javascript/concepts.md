
# Concepts

# destructuring
```
const user = {name: 'bertha benz', age: 28, city: 'budapest'}
const {name, age, city} = user;
```

# debounce vs throttling

# spread operator


# Pass by reference vs Pass by Value
all primitive types are pass by value; others are pass by reference.
```
const a = {} != const b = {};
```

# Nullish coalescing
this (??) is a logical operator that returns its right-hand side operand 
when its left-hand side operand is null or undefined.
```
const foo = null ?? 'default string';
console.log(foo); // 'default string'
const baz = 0 ?? 'default string';
console.log(baz); // 0
```