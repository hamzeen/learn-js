
# 01. isPalindrome
```js
const isPalindrome = (str) => 
    str.toLowerCase().split('').reverse().join('') === str.toLowerCase();
console.log(isPalindrome('rAceCar'));
```

# 02. Title Case
```js
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
 
# 03. Month i18n
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
# 03. Date Formatting
```js
// date fromat dd-mm-yyyy
const now = new Date();
const date = now.toISOString().split('T')[0];
const newFormat = date.split('-').reverse().join('-');
console.log(newFormat):
```

# 04. The Weird Sort (Norway)
```js
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
// const sample_input =  ['world', '4', 'hello', '2', '3', '1', 'coding', 'test'];
// expected_output => ['coding', '1', 'hello', '2', '3', '4', 'test', 'world'];

```

# 05. Altered SOS Messages
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

```

# 06. AMAZON Balanced Parantheses
[problem statement](https://www.geeksforgeeks.org/check-for-balanced-parentheses-in-an-expression/)
```js

// Function to check if brackets are balanced
function areBracketsBalanced(expr) {
	
	// ArrayDeque is faster than using Stack class
	let stack = [];
	for(let i = 0; i < expr.length; i++) {
		let x = expr[i];
		if (x == '(' || x == '[' || x == '{') {
			
			// Push the element in the stack
			stack.push(x);
			continue;
		}

		if (stack.length == 0) // If current character is not opening
			return false;
			
		let check;
		switch (x) {
		case ')':
			check = stack.pop();
			if (check == '{' || check == '[')
				return false;
			break;

		case '}':
			check = stack.pop();
			if (check == '(' || check == '[')
				return false;
			break;

		case ']':
			check = stack.pop();
			if (check == '(' || check == '{')
				return false;
			break;
		}
	}

	// Check Empty Stack
	return (stack.length == 0);
}

// TEST
areBracketsBalanced("([{}])");

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

# 08. Templating
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
