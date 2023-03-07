# Javascript Algorithms and Data Structures

## Basic JavaScript

- Eight different data types ([MDN page](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures))
	- `undefined` (singleton)
		- It is the initial value for variables that are declared but not initialized
		- If a mathematical operation is performed between `undefined` and `number`, will get `NaN` (*Not a Number*)
		- If a `string` is concatenated with `undefined`, resulting *string* = `"undefined"`
	- `null` (singleton)
	- `boolean` (`true`, `false`)
	- `string`
		- `+` concatenates
	- `symbol`
	- `bigint`
	- `number` (floating point)
		- `+` adds, `-` subtracts, `variable++;` increments by 1, `variable--;` decrements by 1
		- `*` multiplies, `/` divides, `%` calculates remainder (on integers AND floating point numbers)
	- `object`

	- JS is a **dynamic** language with **weakly typed** variables
		- Dynamic = variables can be (re-)assigned values of any type without restriction
		- Weakly typed = when an operation involves mismatched types, performs an implicit conversion instead of throwing errors

- Variables
	- Act as a label upon data?
	- Declaration
		```javascript
		var variable;  // variable can be overwritten by assignment or another `var` declaration (not `let`)
		let variable;  // variable can be overwritten by assignment, but not by `var` or `let` declarations
		const VARIABLE;  // variable is immuteable (cannot be overwritten by assignment, `var`, or `let`)
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