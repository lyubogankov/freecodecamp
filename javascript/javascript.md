# Javascript Algorithms and Data Structures

## Basic Javascript / ES6

- JS is a **dynamic** language with **weakly typed** variables
	- Dynamic = variables can be (re-)assigned values of any type without restriction
	- Weakly typed = when an operation involves mismatched types, performs an implicit conversion instead of throwing errors

### Data types
There are apparently 8: ([MDN page](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures))
	
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
	- Template literals ([MDN docs: template literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals))
		- Can interpolate, though note the enclosing '`' backticks
			```javascript
			`string text ${expression} string text`
			```
		- Can also enclose multi-line strings, still with the single backticks

- `symbol`
- `bigint`
- `number` (floating point)

- `object`
	- Mutable
	- Declaration:
		```javascript
		const myobj = {
			property1 : value1,
			"property2" : value2,
			...
		};

		// shorthand in ES6 when instantiating from variables
		const [property1, property2] = [value1, value2];
		const myobj = {property1, property2};  // myobj = {'property1':value1, 'property2':value2}
		```
	- > Can be thought of as a key/value storage, like a dictionary
		- Keys = properties
		-  properties can be set with strings, or directly as names (without any quotes) if they are strings.
		- properties don't need to be strings, though (they are typecast to strings though)
			- This means that an integer (ex: 5) and a string (ex: "5") will write TO THE SAME PROPERTY
		- Properties are accessed...
			- with brackets: `myobject['property']`
			- with dot: `myobject.property`
			- (ES6) with *destructuring assignment*
				```javascript
				const user = { name: 'John Doe', age: 34 };

				// instead of...
				const name = user.name;
				const age = user.age;

				// Using destructuring
				// Left-hand-side variable names must match object properties!
				// Not required to extract all parameters.
				const { name, age } = user;

				// It can be nested, too:
				const user = {
					johnDoe: { 
						age: 34,
						email: 'johnDoe@freeCodeCamp.com'
					}
				};
				const { johnDoe: { age, email }} = user;
				const { johnDoe: { age: userAge, email: userEmail }} = user;
				```
		- properties can be added dynamically
			- creation: `myobject.newproperty = value` or `myobject['newproperty'] = value`
			- deletion: `delete myobject.property` or `delete myobject['property']`
		- `myobject.hasOwnProperty(propname)` to check for existence of a property
	- Can contain any other type of JS data structure (nested)
		- nested access: combinations of `[]` and `.` (for arrays/objects)

Note: `typeof()` function returns the type of a literal/variable, *as a string*, not an class-object like Python.

### Variables
- Act as a label upon data (*not sure where the similarity with Python's stops though, if ever*)
- Declaration
	```javascript
	var variable;            // can be overwritten by assignment or another `var` declaration (not `let`)
	let variable;            // can be overwritten by assignment, but not by `var` or `let` declarations
	const VARIABLE = value;  // is immuteable (cannot be overwritten by assignment, `var`, or `let`)
	variable;		         // can be declared without any declaration keyword??
	
	// ES6: destructuring assignment (like Python's iterable unpacking)
	// Can be nested to combine object/array unpacking

	// Objects: by name
	// I took more notes on this above, under "Data types -> object"
	var/let/const {a, b, ...} = object       // variable & object property names must match!
	var/let/const {a: x, b: y, ...} = object // names of tags must match; variables get new names

	// Arrays: by position
	var/let/const [a, b] = [1, 2, 3, 4, 5, 6];      	// a=1, b=2
	var/let/const [a, b,,, c] = [1, 2, 3, 4, 5, 6]; 	// a=1, b=2, c=5
	var/let/const [a, b, ...arr] = [1, 2, 3, 4, 5, 7];	// a=1, b=2, arr=[3, 4, 5, 7]
	```
	- Declared variable without initialization points to `undefined`.
	- `const` keyword means the variable cannot point to a new object.  However, if it points to a mutable object, the object can still be mutated.
		- `Object.freeze(obj)` will make the object immutable, though!
			- "Any attempt at changing the object will be rejected, with an error thrown if the script is running in [strict mode](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode)"
	- Using destructuring assignment, can imitate a Python feature I like.
		```Python
		x, y = 1, 2               # Python
		```
		```javascript
		let {x, y} = {x:1, y:2}; // Javascript, with object
		let [x, y] = [1, 2];     // Javascript, with array   (cleaner, imo)
		// variable value swap:
		[x, y] = [y, x];         // This is the Python ex that comes to mind!
		```
	
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

### Operators ([w3schools JS operators reference](https://www.w3schools.com/js/js_operators.asp))
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

### Arrays
- 0-indexed
- Mutable, even with `const` declaration
- Can contain mixed types
	- There is a separate object called a [typed array (MDN Docs)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Typed_arrays)
- Initialization:
	```javascript
	const/let/var myArray = [];
	const/let/var myArray = ["string", integer, floatingpoint, []];
	```
- Indexing: `myArray[idx0][idx1][...]`
- Methods (they also have properties, both are documented on [MDN Docs page](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array))
	- `{array}.push({param1}, ...)` - adds one or more arguments to end of array
	- `{array}.pop()` - pops from end
	- `{array}.shift()` - pops from front
	- `{array}.unshift({param1}, ...)` - appends to front of array
	- `{arr1}.concat({arr2})` - concatenates elements of arr2 onto arr1's end
	- `{array}.slice(start=0, end=array.length)` - creates a shallow copy into a new array object containing elements [start, end)
	- `{array}.map({function})` - apply the function to each element in the array and return a new array

### Functions
- Creation:
	```javascript
	function functionName(param1, param2, ) {
		// contents
		return something; // optional; by default returns undefined
	}
	```
	- In ES6, there's a shorter syntax when creating a function within an object?
		```javascript
		// instead of
		const myobj = { myfunc: function() { return 'wassup'; } };
		// we can do
		const myobj = { myfunc() { return 'wassup'; } };
		```
- Invocation: `functionName(param1, param2)`
- Default parameters:
	```javascript
	function functionName(param1=default1) { ... }
	```
- Variable number of arguments (in ES6): *rest* parameter.  Arguments stored in an array.
	```javascript
	function howMany(...args) {
		return args.length + " arguments";
	}
	```

- Using destructuring assignment, can unpack an object:
	```javascript
	// destructuring
	const profileUpdate = (profileData) => {
		const { name, age, nationality, location } = profileData;
		...
	}
	// destructuring directly in function signature
	const profileUpdate = ({ name, age, nationality, location }) => { ... }
	```

- Every function has a hidden `this` parameter.  Its value is determined by how the function is called (*runtime binding*) ([MDN docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this#function_context))
	> In typical function calls, `this` is implicitly passed like a parameter through the function's prefix (the part before the dot)
	
	> For a typical function, the value of this is the object that the function is accessed on. In other words, if the function call is in the form obj.f(), then this refers to obj.
	```javascript
	function getThis() {
		return this;
	}

	const obj1 = { name: "obj1" };
	const obj2 = { name: "obj2" };

	obj1.getThis = getThis;
	obj2.getThis = getThis;

	console.log(obj1.getThis()); // { name: 'obj1', getThis: [Function: getThis] }
	console.log(obj2.getThis()); // { name: 'obj2', getThis: [Function: getThis] }
	```

- Every function is a `Function` object, and has properties and methods ([MDN docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function))
	- `Function.prototype.apply()` - can set a function's `this` parameter as well as arguments, provided with an array.  For a function `fn`: `fn.apply(this, args)`.  Both `this` and `args` can be `null`!
	- `Function.prototype.bind()` is like Python's `functools.partial` / `functools.partialmethod`.  Can also set the `this` parameter.

- *spread operator* is like Python's iterable unpacking: for an array (*or "other expression"?*) `arr`, "spread" using `...arr`
	```javascript
	const arr = [6, 89, 3, 45]          // want to find max
	let m = Math.max(6, 89, 3, 45)      // could hardcode
	let m = Math.max.apply(null, args)  // could use Function.prototype.apply
	let m = Math.max(...args)			// could use spread operator!
	```

#### Anonymous functions
- Verbose syntax:
	```javascript
	const myFunc = function() {
		const myVar = "value";
		return myVar;
	}
	```
- "Arrow function" syntax
	```javascript
	const myFunc = () => {
		const myVar = "value";
		return myVar;
	}
	```
- "Arrow function" syntax without a function body (only return value)
	```javascript
	const myFunc = () => "value";                              // return with no args
	const doubler = (item) => item * 2;                        // can take arg(s)!
	const doubler = item => item * 2;                          // 1 argument = special, can omit parens
	const multiplier = (item, multi) => item * multi;		   // 2+ require parens
	const greeting = (name = "Anonymous") => "Hello " + name;  // with default argument parameter

	(arg) => arg * 2; // anonymous function; if passing directly to another function no need to name
	```


### Scope
- Variables defined outside of a function have global scope
- Variables defined within a function have local/function scope
	- Within a function, local variables take precedence over globals with the same name
- Variables defined within a function without the `let` or `const` keywords have global scope
- `this` keyword behaves differently in different contexts: global, class, and function ([MDN docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this))


### Conditional Logic
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


### Loops
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
		- `b` = condition statement (`i < 5`, `i < arr.length`)
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


### Regular Expressions (regex)

### Debugging

### Misc
- Some useful functions, presented during lessons
	- `Math.random()` generates a random decimal number between [0, 1)
	- `Math.floor()` rounds down to nearest whole number
	- `parseInt({str}, radix)` turns specified string into integer of specified radix/base if possible, else `NaN`


- "strict mode"
	- Can be applied to entire scripts, or individual functions by writing `"use strict";` within the desired scope.



## Basic Algorithm Scripting module

## Intermediate Algorithm Scripting module

## Object Oriented Programming (material from ES6 & dedicated modules)

- Naming convention for classes (in ES6 only?): **UpperCamelCase**

- Defining a class (copied straight the [freeCodeCamp module](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/use-class-syntax-to-define-a-constructor-function))
	> In ES5, an object can be created by defining a constructor function and using the new keyword to instantiate the object.

	> In ES6, a class declaration has a constructor method that is invoked with the new keyword. If the constructor method is not explicitly defined, then it is implicitly defined with no arguments.

	```javascript
	// Explicit constructor
	class SpaceShuttle {
		constructor(targetPlanet) {
			this.targetPlanet = targetPlanet;
		}
		takeOff() {
			console.log("To " + this.targetPlanet + "!");
		}
	}

	// Implicit constructor 
	class Rocket {
		launch() {
			console.log("To the moon!");
		}
	}

	const zeus = new SpaceShuttle('Jupiter');
	zeus.takeOff();  // prints To Jupiter! in console

	const atlas = new Rocket();
	atlas.launch();  // prints To the moon! in console
	```

## Functional Programming module

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