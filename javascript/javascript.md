# Javascript Algorithms and Data Structures

## Basic JavaScript
	Apparently, it was mostly ECMAScript 5 (ES5) features covered


- JS is a **dynamic** language with **weakly typed** variables
	- Dynamic = variables can be (re-)assigned values of any type without restriction
	- Weakly typed = when an operation involves mismatched types, performs an implicit conversion instead of throwing errors

- Data types
	- There are apparently 8: ([MDN page](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures))
		- `undefined` (singleton)
			- It is the initial value for variables that are declared but not initialized
			- If a mathematical operation is performed between `undefined` and `number`, will get `NaN` (*Not a Number*)
			- If a `string` is concatenated with `undefined`, resulting *string* = `"undefined"`
		- `null` (singleton)
		- `boolean` (`true`, `false`)
		- `string`
			- Immuteable
			- `+` concatenates
			- `+=` concatenates and re-binds to existing variable
			- Must start/end with `"` (double quote) or `'` (single)
			- Escaping with `\` (for quotes, backslash)
			- Special character codes: `\n`, `\t`, `\r`, `\b` (word boundary?), `\f` (form feed?))
			- length: `{string}.length` property
			- indexing: `{string}[{index}]` (it's 0-based!)
		- `symbol`
		- `bigint`
		- `number` (floating point)
		- `object`
			- mutable
			- "Can be thought of as a key/value storage, like a dictionary"
				- Keys = properties
				-  properties can be set with strings, or directly as names (without any quotes) if they are strings.
				- properties don't need to be strings, though (they are typecast to strings though)
				- This means that an integer (ex: 5) and a string (ex: "5") will write TO THE SAME PROPERTY
				- properties are accessed...
					- with brackets: `myobject['property']`
					- with dot: `myobject.property`
				- properties can be added (and removed?) dynamically
					- deletion: `delete myobject.property` or `delete myobject['property']`
				- `myobject.hasOwnProperty(propname)` to check for existence of a property
			- Can contain any other type of JS data structure (nested)
				- nested access: combinations of `[]` and `.` (for arrays/objects)
	- `typeof()` function returns the type of a literl/variable, *as a string*

- Variables
	- Act as a label upon data (*not sure where the similarity with Python's stops though, if ever*)
	- Declaration
		```javascript
		var variable;    // variable can be overwritten by assignment or another `var` declaration (not `let`)
		let variable;    // variable can be overwritten by assignment, but not by `var` or `let` declarations
		const VARIABLE;  // variable is immuteable (cannot be overwritten by assignment, `var`, or `let`)
		variable;		 // it be declared without any declaration keyword??
		```
		- Declared variable without initialization points to `undefined`.
		
	- Assignment
		```javascript
		variable = <<value>>;  // value can be a literal, or another variable
		```
	- Initialization (Declaration + Assignment)
		```javascript
		var variable = <<value>>;
		let variable = <<value>>;
		const VARIABLE = <<value>>;
		```
	- Variables are case-sensitive.  Recommended variable naming conventions:
		- **camelCase** for mutable values
		- **UPPER_CASE** for immutable values / constants

- Operators ([w3schools JS operators reference](https://www.w3schools.com/js/js_operators.asp))
	- Arithmetic
		- `+` adds, `-` subtracts
		- `variable++;` increments by 1, `variable--;` decrements by 1
		- `*` multiplies, `/` divides, `%` calculates remainder (on integers AND floating point numbers)
		- Compound assignment: `+=`, `-=`, `*=`, `/=`, `%=` 
	- Comparison
		- `==` and `!=` check (in)equality and attempt type conversion (normalization)
		- `===` and `!==` check "strict equality".  No type conversion, arguments must be same type/value.
		- `>`, `>=`
		- `<`, `<=`
	- Logical
		- `&&` AND
		- `||` OR
		- `!` NOT

- Arrays
	- Mutable, even with `const` declaration
	- Can contain mixed types
	- Initialization:
		```javascript
		const/let/var myArray = [];
		const/let/var myArray = ["string", integer, floatingpoint, []];
		```
	- Indexing: `myArray[idx0][idx1][...]`
	- Methods
		- `{array}.push({param1}, ...)` - adds one or more arguments to end of array
		- `{array}.pop()` - pops from end
		- `{array}.shift()` - pops from front
		- `{array}.unshift({param1}, ...)` - appends to front of array

- Functions
	- Creation:
		```javascript
		function functionName(param1, param2, ) {
			// contents
			return something; // optional; by default returns undefined
		}
		```
	- Invocation: `functionName(param1, param2)`
	- "return early pattern"

- Scope
	- Variables defined outside of a function have global scope
	- Variables defined within a function have local/function scope
		- Within a function, local variables take precedence over globals with the same name
	- Variables defined within a function without the `let` or `const` keywords have global scope

- Conditional Logic
	- `if` statement
		```javascript
		if (true_condition) {
			statement;
		} else if (true_condition) {
			statement;
		} else if {  // can have as may `else if` as desired
		
		} else {
			statement;
		}
		```
		- The braces are only required for multi-line contents!
	- `switch` statement
		- Expressions are executed from the first matched `case` value until a `break` is encountered ("fall through")
		- The variable / case comparisons are performed using strict equality (`===`)
		- Can contain strings, unlike C++!
		```javascript
		switch (variable) {
			case {one}:
				statement;
				break;
			case {two}:
				statement;
				break;
			case {three}:
			case {four}:
				statement;
				break;
		...
			default:
				statement;
				break;
		}

		```
	- Ternary operator
		```javascript
		condition ? statement_returned_if_true : statement_returned_if_false;
		```
		- They can be nested...
			```javascript
			condition1 ? cond1_true : condition2 ? cond1_false_cond2_true : cond1_false_cond2_false;
			```
			Apparently, should be formatted as follows:
			```javascript
			condition1 ? cond1_true
				: condition2 ? cond1_false_cond2_true
				: cond1_false_cond2_false
			```

- Loops
	- while
		```javascript
		while (condition) {
			statement;
			...
		}
		```
	- for
		- Declared wit hthree optional expressions separated by semicolons: `for(a; b; c)
			- `a` = initialization statement (`let i = 0`)
			- `b` = condition statemtn (`i < 5`, `i < arr.length`)
			- `c` = final expression (`i++`)
			- another way of looking at it: {[start, stop), step}

		```javascript
		for (a; b; c) {
			statement;
			...
		}
		```
	- do while (always executes once, and continues looping while condition is true)
		```javascript
		do {
			statement;
			...
		} while (condition);
		```

- Some useful functions, presented during lessons
	- `Math.random()` generates a random decimal number between [0, 1)
	- `Math.floor()` rounds down to nearest whole number
	- `parseInt({str}, radix)` turns specified string into integer of specified radix/base if possible, else `NaN`


## ES6

## Regular Expressions

## Debugging

## Basic Data Structures

## Basic Algorithm Scripting

## Object Oriented Programming

## Functional Programming

## Intermediate Algorithm Scripting



## Questions
- Does assigning one variable equal to another copy or reference the underlying data?
	- In Python: immutables copy, mutables reference.
	- In JavaScript: ???

- If a `string` is concatenated with `undefined`, resulting *string* = `"undefined"` (claim from module)

	However, I tested with below and it didn't work (I may have done something wrong):

	```javascript
	var c = "I am a";
	var d;
	var e;
	var f;

	c = c + " String!";
	e = d + " String!";

	console.log(c);
	console.log(d);
	console.log(d == "undefined");  // false
	console.log(d == f);			// true
	```