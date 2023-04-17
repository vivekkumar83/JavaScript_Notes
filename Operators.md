# Operators in JavaScript

- In JavaScript, operators are symbols or keywords used to perform various operations on variables or values. 
- There are several types of operators in JavaScript
	- Arithmetic Operators
	- Assignment Operators
	- Comparison Operators
	- Logical Operators
	-  Bitwise Operators
	- Ternary Operator
	- Unary Operators

## Arithmetic Operators

```JavaScript
+  ----> Addition
-  ----> Subtraction
*  ----> Multiplication
** ----> Exponentiation (ES2016)
/  ----> Division
%  ----> Modulus (Remainder)
++ ----> Increment
-- ----> Decrement
```

#### Example
```javascript
let x = 3;
let y = 2;
let sum = x + y; // sum = 5
let difference = x - y; // difference = 1
let product = x * y; // product = 6
let quotient = x / y; // quotient = 1.5
let remainder = x % y; // remainder = 1
let expo = x ** y; // exponential = 9
```

## Assignment Operators

```JavaScript
=   ---> Assignment operator	
+=  ---> Addition assignment	
-=  ---> Subtraction Assignment	
*=  ---> Multiplication Assignment	
/=  ---> Division Assignment	
%=  ---> Remainder Assignment	
**= ---> Exponentiation Assignment
```
#### Example
```JavaScript
let x = 10;
x += 5; // x = 15
x -= 3; // x = 12
x *= 2; // x = 24
x /= 4; // x = 6
x %= 2; // x = 0
```

## Comparison Operators

```JavaScript
==	
!= 
=== 
!== 
< ----> less than
> ----> greater than	
```
#### Example
```JavaScript
let x = 10;
let y = 5;
let isGreater = x > y; // isGreater = true
let isNotEqual = x != y; // isNotEqual = true
let isEqual = x === y; // isEqual = false
let isLessOrEqual = x <= y; // isLessOrEqual = false

```

### == (Abstract Equality Comparison)

- The `==` operator performs a comparison between two values, and if the types of the values are the same, it performs a strict equality comparison using the `===` operator.

- If the types of the values being compared are not the same, the `==` operator performs type coercion before making the comparison. 

#### Example
```JavaScript
console.log(5 == "5");    // true (the string "5" is converted to the number 5)
console.log(true == 1);   // true (the boolean true is converted to the number 1)
console.log(null == undefined);  // true (both null and undefined are considered equal to themselves and each other)
```

### === (Strict Equality Comparison)

-   If the type of `x` is the same as the type of `y`, then the values of `x` and `y` are compared.

-   If the type of `x` is not the same as the type of `y`, then the comparison always returns `false`.

#### Example
```JavaScript
console.log(5 === "5");   // false (the string "5" is not the same as the number 5)
console.log(true === 1);  // false (the boolean true is not the same as the number 1)
console.log(null === undefined);  // false (null and undefined are not the same type)
```

## Logical Operators

```
&&	-----> Logical And
||  -----> Logical Or
!   -----> logical not
```

#### Example
```JavaScript
let x = 5;
let y = 10;

if (x < 10 && y > 5) {
  console.log("Both conditions are true");
}

// Output: Both conditions are true
```

#### Example
```JavaScript
let x = 5;
let y = 10;

if (x < 10 || y < 5) {
  console.log("At least one condition is true");
}
// Output: At least one condition is true
```

#### Example
```JavaScript
let x = 5;
let y = 10;

if (!(x > 10)) {
  console.log("x is not less than 10");
}
// Output: x is not less than 10
```

- In a AND operator, first operand false then return first operand, & if first operand true then return second operand.

#### Example
```JavaScript
console.log(10 > 12 && 8 > 3); // false
console.log(12 > 10 && 8 < 3); // false
console.log(12 > 10 && 8 > 3); // true
```

- In a OR operator, first operand false then return second operand, & if first operand true then return first operand.

#### Example
```JavaScript
console.log(10 > 12 || 8 > 3); // true
console.log(12 > 10 || 8 < 3); // true
console.log(12 > 10 || 8 > 3); // true
```

## Bitwise Operators
```
& -----> Bitwise AND
| -----> Bitwise OR
^ -----> Bitwise XOR
~ -----> Bitwise NOT
<< ----> Left shift
>> ----> Sign-propagating right shift
>>> ---> Zero-fill right shift
```

#### Example
```JavaScript
let x = 10;
let y = 5;

let result1 = x & y; // result1 = 0
console.log(result1);

let result2 = x | y; // result2 = 15
console.log(result2);

let result3 = x ^ y; // result3 = 15
console.log(result3);

let result4 = ~x; // result4 = -11
console.log(result4);

let result5 = x << 1; // result5 = 20
console.log(result5);

let result6 = y >> 1; // result6 = 2
console.log(result6);
```
## Ternary Operator

- The ternary operator in JavaScript is a shorthand way to write conditional statements. It is also known as the conditional operator

#### Example
```JavaScript
let x = 10;
let message = x > 5 ? "x is greater than 5" : "x is less than or equal to 5";
console.log(message); // "x is greater than 5"
```

## Unary Operators

- In JavaScript, unary operators are operators that operate on a single operand.
- There are several unary operators
	- Unary plus (+)
	- Unary minus (-)
	- Increment  operators
	- Decrement operators

## Unary Plus (+)

- The unary plus operator (+) is used to convert a value to a number data type, just like the Number() function. 
- It is called a unary operator because it operates on a single operand.
- The syntax for using the unary plus operator is simply to place a plus sign (+) in front of the value you want to convert.

#### Example
```javascript
let num1 = "5"; // a string value
let num2 = +num1; // using the unary plus operator to convert to a number

console.log(typeof num1); // output: string
console.log(typeof num2); // output: number
console.log(num2); // output: 5
```

#### Example
```javascript
let bool1 = true; // a boolean value
let num3 = +bool1; // using the unary plus operator to convert to a number

console.log(typeof bool1); // output: boolean
console.log(typeof num3); // output: number
console.log(num3); // output: 1
```
- Note that using the unary plus operator with a non-numeric string value will result in NaN

#### Example
```javascript
let str1 = "Hello"; // a non-numeric string value
let num4 = +str1; // using the unary plus operator to convert to a number

console.log(typeof str1); // output: string
console.log(typeof num4); // output: number
console.log(num4); // output: NaN
```

## Unary Minus (-)

- It first converts the operand to the number type and then negates it.
- Null and undefined will be converted to `0`.

#### Example
```javascript
let num1 = 5; 
let num2 = -num1; 
console.log(num2); // num2 is -5

let str1 = "10";
let num3 = -str1; // num3 is -10
console.log(num3);

let bool1 = true;
let num4 = -bool1; // num4 is -1
console.log(num4);

let null1 = null;
let num5 = -null1; // num5 is -0
console.log(num5);

let str3 = "abc";
let num6 = -str3; 
console.log(num6); // NaN
```

## Increment Operator (++)

- The increment operator (++) is used to increase the value by 1.
- There are two forms of the increment operator: pre-increment and post-increment.

### Post-increment 

- This operator `++` increases the value of a variable after the expression is evaluated.

#### Example
```javascript
let x = 1;
let y = x++;
console.log(x); // Output: 2
console.log(y); // Output: 1
```

### Pre - increment

- This operator `++` increases the value of a variable before the expression is evaluated.

#### Example
```javascript
let x = 5;
let y = ++x;

console.log(x); // output: 6
console.log(y); // output: 6
```

- Multiple increment operators are not possible.

#### Example
```javascript
let x = 5;
++(++x);
console.log(x); 

// SyntaxError: Invalid left-hand side expression in prefix operation
```

#### Example
```javascript
let x = 5;
(x++)++;
console.log(x); 

// SyntaxError: Invalid left-hand side expression in postfix operation
```

## Decrement Operator (- -)

- The decrement operator (- -) is used to decrease the value by 1.
- There are two forms of the decrement operator: pre-decrement and post-decrement.

### Post-decrement

- This operator `--` decreases the value of a variable after the expression is evaluated.

#### Example
```javascript
let x = 5;
let y = x--;
console.log(x); // Output: 4
console.log(y); // Output: 5
```

### Pre - decrement

- This operator `--` decreases the value of a variable before the expression is evaluated.

#### Example
```javascript
let x = 5;
let y = --x;
console.log(x); // Output: 4
console.log(y); // Output: 4
```
