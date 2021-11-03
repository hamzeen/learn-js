[question](https://www.geeksforgeeks.org/check-for-balanced-parentheses-in-an-expression/)
```javascript

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


```
