## Q1 | isObject
```js
typeof x === 'object' && x !== null
// warn! typeof null === 'object'
```

## Q2 | filter | sort | add | concatenate
```js
 const master = [
    3,"we",-1,NaN,undefined,
    10.25,[],"are","",40,0,
    "the world",null,1,12.75
  ];

 const cleanAry = master.filter(Boolean);
 const result = {
    sum: cleanAry.filter(a => typeof a === 'number').reduce((b,c) => b+c, 0).toFixed(2),
    product: cleanAry.filter(a => typeof a === 'number').reduce((b,c) => b*c, 1),
    sort: cleanAry.filter(a => typeof a === 'number').sort((a, b) => a - b),
    text: cleanAry.filter(a=> typeof a === 'string').join(' ')
 };
//  {"sum":"66.00","product":-15682.5,"sort":[-1,1,3,10.25,12.75,40],"text":"we are the world"}
  
```
## Q3 | title case
```js
function titleCase(inputStr) {
  return inputStr
     .split(' ')
     .map(w => w.charAt(0).toUpperCase()+w.slice(1))
     .join(' ');
}
const str = 'we are the world';
titleCase(str);
```


# CSS


* Frameworks: `Bootstrap`, `Tailwind`, Meterial Design
* UI Design: `InVision`, `Figma`

* Bootstrap uses `FlexGrid` to build its [grid](https://uxplanet.org/how-the-bootstrap-4-grid-works-a1b04703a3b7)

* 3 levels of styling: `inline`, `header` and as a `resource`. 
`CSS Specificity` is important to know when you work iwth it.

ex1:
```html
// here the lass css declaration takes precedence
.blue { background: blue; }
.red { background: red; }

// we see Hello in red bg. The order the class ref here is no importnant.
<div class="red blue">Hello</div>
```

ex2:
```html
// the first gets applied. Gets higher score in `CSS Specificity`
div.label { color: green; }
.label { color: black; }
div { color: blue; }

<div class="label">Hello</div>
```


