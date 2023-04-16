## Data Types 

 - JavaScript is a dynamically typed language, which means that variables can hold any types of values and it's types of value can be changed at runtime.
 - JavaScript is typed values not typed variables
- Types of values
	- Primitive Types
	- Object Types

## Primitive Types	

- Primitive types can store a single value and are immutable and atomic in nature.
- Primitive types are passed by value
- Types 
	- Number
	- String
	- Boolean
	- Null
	- Undefined
	- Symbol
	- Bigint
	
## Non - Primitive Types

- Non-primitive types are objects  in JavaScript.
- It is mutable and can have multiple values, properties, and methods.
- It is passed by reference.
- Types
	-   Objects are always objects
	-   Booleans can be objects (if defined with the new keyword)
	-   Numbers can be objects (if defined with the new keyword)
	-   Strings can be objects (if defined with the new keyword)
	-   Dates are always objects
	-   Maths are always objects
	-   Regular expressions are always objects
	-   Arrays are always objects
	-   Functions are always objects

## Number

- It represents numeric values, both integers and floating-point numbers.
-  The number type is a double-precision 64-bit binary format IEEE 754 value, it stores values in binary form with 64 bits. which allows for accurate representation of floating-point numbers. 


#### Example 
```javascript
let myNumber = 42;
console.log(myNumber);

let myDecimalNumber = 3.1418;
console.log(myDecimalNumber);
```
#### Output
```
42
3.1418
```

- It can stores different format of numbers

#### Example 
```javascript
let decimalNumber = 50;      // decimal
let binaryNumber = 0b1010;   // binary
let octalNumber = 0o52;      // octal
let hexNumber = 0x2a;        // hexadecimal
```

- There are three special numeric values in JavaScript: `Infinity`, `-Infinity`, and `NaN` (not a number).


### How Numbers are Stored

- JavaScript uses a 64-bit double-precision floating-point format,This means that all numeric values in JavaScript are represented as 64-bit binary values, 
- which can represent both integer and floating-point numbers.
- Let's take an example of how 10 is stored in javascript
	- Convert 10 to binary number
		> 10 = 1010
	-  Convert binary number to normalize form
		> moving the decimal point to the left until there is only one non-zero digit to the left of the 	            decimal point.
	           1010 = 1.010 * 2^3
	            here exponent is 3 significant number is 1.010
	            
	- 64 bits are divided into three parts
		- 1 bit for sign
		- 11 bit for exponent
		- 52 bit for significant
	- The exponent bits are stored using a biased exponent representation, and the bias value is added to the actual exponent before storing it in the exponent bits. 
	- The purpose of this bias value is to allow positive and negative exponents to be represented with a single sign bit.
	- The bias value is

		$$
		 bias = 2^{n-1} - 1
		$$
		- here n = 11 so bias = 1023
	- Add the bias value of 1023 to the exponent 3, giving us 1026, so convert it into binary form 10000000010.
	- For significant values take the value of significant digit after the right of point is 
	- 0100000000000000000000000000000000000000000000000000
	- so the final represention is 
	- sign exponent mantisa
	- 0 10000000100 0100000000000000000000000000000000000000000000000000

### Range of the Numbers

- `Number.MAX_VALUE`,  represents the largest positive number that can be represented in JavaScript, it can represent very large numbers with decimal places.

- `Number.MIN_VALUE`,  represents the smallest positive number that can be represented in JavaScript,  it is much closer to zero and can represent very small numbers with decimal places.

	**Note**
	> `Number.MIN_VALUE` is not the smallest possible number that can be represented in JavaScript.

	>  `-Number.MAX_VALUE`. This value represents the largest negative number that can be represented in JavaScript

- `Number.MAX_SAFE_INTEGER` and `Number.MIN_SAFE_INTEGER`. These constants represent the largest and smallest integers that can be safely represented as 64-bit floating-point numbers without losing precision due to rounding errors.
- `Number.MAX_SAFE_INTEGER`  is equal to 2^53 - 1
- `Number.MIN_SAFE_INTEGER`, is equal to -(2^53 - 1)
- `+Infinity` , the  positive number greater than `Number.MAX_VALUE`
- `-Infinity` , the  negative number smaller than `- Number.MAX_VALUE`
- `+0` , the  positive number smaller than `Number.MIN_VALUE`
- `-0` , the  negative number greater than `- Number.MIN_VALUE`
- `Number.isSafeInteger()`, this method can check the safe integer number

### NaN

- `NaN` stands for `Not a Number`. 
- It is a value that represents an unrepresentable mathematical value.
- It is not equal to any value, including itself.

```javascript
console.log(NaN);  // outputs "NaN"

console.log(NaN == NaN);  // outputs "false"

console.log(NaN + 1);  // outputs "NaN"

console.log(NaN * 5);  // outputs "NaN"
```

- `isNaN()` is a function which returns true when passed `NaN` , and returns false when passed a valid number.

```javascript
console.log(isNaN(NaN));  // outputs "true"

console.log(isNaN(5));  // outputs "false"
```

### BigInt 

- `BigInt` is a built-in object that provides a way to represent integers larger than the maximum safe integer (`Number.MAX_SAFE_INTEGER`), which is 2^53 - 1.
- It  is denoted by appending the `n` suffix to a numeric literal or call the `BigInt()` constructor:

  #### Examples
	```javascript
	const a = 125n;
	const b = BigInt(476);
	```

- `BigInt` values cannot be mixed with regular `Number` values in arithmetic operations.

	#### Examples
	```javascript
	const a = 123n;
	const b = 456;

	console.log(a + b); 
	```

	#### Output
	```javascript
	TypeError: Cannot mix BigInt and other types, use explicit conversions
	```
###  Null 

- `null` is a primitive value that represents the intentional absence of any object value. 
- It is a special value that can be assigned to a variable to indicate that the variable has no value.

#### Example
```javascript
let x = null;
console.log(x); // null
```

###  Null 

- `undefined` is a primitive value that is assigned to a variable when it has been declared but has not been assigned a value. 
- It is also used as the default return value for a function that does not explicitly return a value.

#### Example
```javascript
let variable;
console.log(variable); // undefined
```

### Boolean 

- `Boolean` is a primitive data type that represents one of two values: `true` or `false`. 
- It's used to represent logical values and is often used in conditional statements and comparisons.

#### Example
```javascript
let x = true;
let y = false;
console.log(x); // true
console.log(y); // false
```

## The typeof operator

- The `typeof` operator is used to determine the the type of a given value or expression. 
- It returns a string that represents the type of the operand.

#### Example
```javascript
typeof 56; // "number"
typeof NaN; // "number"
typeof Infinity; // "number"
typeof "Hello"; // "string"
typeof true; // "boolean"
typeof undefined; // "undefined"
typeof null; // "object"
typeof {}; // "object"
typeof []; // "object"
typeof function() {}; // "function"
typeof BigInt(42); // "bigint"
typeof Symbol("foo"); // "symbol"
```
- The `typeof` operator in JavaScript returns `"object"` when applied to `null`.
- This is considered to be a mistake in the language design, as `null` represents the intentional absence of any object value, and is not an object itself.
- The `typeof` operator in JavaScript returns `"function"` when applied to a function expression or declaration.
- Functions are a type of object in JavaScript, but have additional properties and capabilities beyond regular objects.
