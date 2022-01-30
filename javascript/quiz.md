## Q1 | isObject
```js
typeof x === 'object' && x !== null
```

## Q2| filter | sort | add | concatenate
```js
 const master = [
    3,
    "we",
    -1,
    NaN,
    undefined,
    10.25,
    [],
    "are",
    "",
    40,
    0,
    "the world",
    null,
    1,
    12.75
  ];

  const cleanAry = master.filter(Boolean);
  const result = {
    sum: cleanAry.filter(a => typeof a === 'number').reduce((b,c) => b+c, 0).toFixed(2),
    product: cleanAry.filter(a => typeof a === 'number').reduce((b,c) => b*c, 1),
    sort: cleanAry.filter(a => typeof a === 'number').sort((a, b) => a - b),
    text: cleanAry.filter(a=> typeof a === 'string').join(' ')
  };
```
