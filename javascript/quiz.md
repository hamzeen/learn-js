## Q1 | isObject
```js
typeof x === 'object' && x !== null
// warn! typeof null === 'object'
```
## Q2 | Destrcuture
```js
const user = {name: 'bertha benz', age: 28, city: 'budapest'}
const {name, age, city} = user;
```

## Q3 | Spread Operator
```js
// add new property
const data = [{id:1}, {id:3}]
    .map(el => ({ ...el, name: `name ${el.id}` }));
console.log(data);

// array with 8 objects
const aryX = new Array(8).fill({name: 'labs'}).map((el, idx ) => 
 ({...el, combine: `name: ${el.name} id: ${idx}`, id: idx}));
 
 // add at start
var fruits = ["Banana", "Orange", "Apple", "Mango"];
// fruits.unshift("Kiwi");
const fruitsNew = ['Kiwi', ...fruits];
```

## Q4 | filter | sort | add | concatenate
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
## Q4| moment js
moment demo: [codepen](https://codepen.io/hamzeen/pen/PgbzGx)

```js
var start = moment("2018-03-10", "YYYY-MM-DD");
var end = moment("2018-03-15", "YYYY-MM-DD");

// difference in number of days
var diff = moment.duration(start.diff(end)).asDays();
console.log("days:: " + Math.abs(diff));

// elapsed years
var years = moment().diff('1986-10-15', 'years');
console.log(years);
```

## Q5 | title case
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

* UI Design: `InVision`, `Figma`. Component lib: `Styleguide`, Pattern Library, `Design Systems`
* Frameworks: `Bootstrap`, `Tailwind`, Meterial Design
* Bootstrap uses `Flexbox` for its [grid](https://uxplanet.org/how-the-bootstrap-4-grid-works-a1b04703a3b7)

* 3 levels of styling: `inline`, `header` and as a `resource`. 
`CSS Specificity` is important to know when you work iwth it.

ex1: order of css definition matters!
```html
// here the lass css declaration takes precedence
.blue { background: blue; }
.red { background: red; }

// we see Hello in RED bg. The order the class ref here is no importnant.
<div class="red blue">Hello</div>
```

ex2: being more specific matters!
```html
// the first gets applied. Gets higher score in `CSS Specificity`
div.label { color: green; }
.label { color: black; }
div { color: blue; }

<div class="label">Hello</div>
```


