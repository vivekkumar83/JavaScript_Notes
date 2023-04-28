# Type Conversion

- Type Conversion is the process of changing the type of a value from one type to another.

- There are two ways of type conversion: 

	- Explicit   conversion
	- Implicit   conversion

- Explicit Type Conversion or Type Casting is when the programmer intentionally changes the type of a value. 

> For example, using the Number() function to convert a string to a number.

- Implicit Type Conversion or Type Coercion is when JavaScript automatically converts the type of a value. 

> For example, when using the + operator with a string and a number, JavaScript will convert the number to a string and concatenate the two strings.

## Abstract Operations

- Abstract Operations are defined in the ECMAScript specification.

- It provide a standardized way to define the behavior of various functions and operators in JavaScript. 

- These operations are implemented by the JavaScript engine

> For example, ToPrimitive(), ToNumber(), ToString(), ToBoolean(), etc these are the abstract operations

## Implicit Conversion

- It is also known as coercion.

- Abstract operations are closely related to implicit coercion.

- It provides the set of rules that define how values are automatically converted from one type to another by the language itself.

- There are several operators and functions in JavaScript in which coercion is applied

## Subtraction operator (-)

- The subtraction operator (`-`) is used to subtract two values in JavaScript.
- In this operator, ToNumber() abstract operation will be applied.
- Substraction Operator - [Link](https://262.ecma-international.org/10.0/#sec-subtraction-operator-minus)
- ToNumber() - [Link](https://262.ecma-international.org/10.0/#sec-tonumber)

### Example 1
```JavaScript
console.log(10 - undefined); // NaN
console.log(10 - null); // 10
console.log(10 - true); // 9
console.log(10 - "5"); // 5
console.log(10 - "abc"); // NaN
```
>  In the above example, ToNumber() abstract operation has applied.

### Example 2
```JavaScript
let obj1 = {};

// by-default
console.log(obj1.valueOf()); // {}
console.log(obj1.toString()); // "[object Object]"

// override
let obj2 = {
  x: 20, 
  valueOf() {
    return 10;
  },
  toString() {
    return "Hi";
  }
};

console.log(obj2.valueOf()); // 10
console.log(obj2.toString()); // "Hi"
```
>  By default valueOf() function return the same object but we can override this.

>  By default toString() function returns the [object Object] which is string but we can override this.

### Example 3
```JavaScript
let obj = {}
console.log(20 - obj); //NaN

let obj1 = {x: 10};
console.log(20 - obj1);// NaN
```

>  1. In the above example, ToNumber() abstract operation has applied which leads to call further ToPrimitive() abstract operation .

ToPrimitive - [Link](https://262.ecma-international.org/10.0/#sec-toprimitive)

### Example 4
```JavaScript
let obj2 = {x: 10, valueOf() {return 90}};
console.log(100 - obj2); // 10

let obj3 = {x: 10, toString() {return "70"}};
console.log(90 - obj3); // 20

let obj4 = {x: 10, toString() {return {}}};
console.log(100 - obj4); // error
```
> In the above example, we have overriden the valueOf() and toString() function.

## Addition operator (+)

- The addition operator (`+`) can perform both addition and concatenation depending on the types of the operands.
- Addition Operator - [Link](https://262.ecma-international.org/10.0/#sec-addition-operator-plus)
- ToString() - [Link](https://262.ecma-international.org/10.0/#sec-tostring)

### Example 5
```JavaScript
let x = 10;
let y = "20";
let result = x + y;

console.log(result); // "1020"
```
>  In the above example, If one or both of the operands are strings, the operator performs string concatenation.

### Example 6
```JavaScript
let a = 5;
let b = 10;
let result = a + b;

console.log(result); // 15
```
>  In the above example, If both operands are numbers, the operator performs addition.

### Example 7
```JavaScript

let obj = {}
console.log(20 + obj); // 20[object Object]

let obj2 = {x: 10, valueOf() {return 90}};
console.log(100 + obj2); // 190

let obj3 = {x: 10, toString() {return "70"}};
console.log(90 + obj3); // 9070
```
>  In the above example, we have applied ToPrimitive() abstract operation 

## Truthy & Falsy Values

- These values are considered as falsy values `undefined`, `null`, `NaN`, `+0`, `-0`, `false`, `" "`

- All other values, including all objects (and arrays), are considered truthy.

- ToBoolean() abstract operation is used in several operators and constructs, such as the `if statement`, `while loop`, `do-while loop`, `logical operators (&&, ||, !)`, and more.

- ToBoolean() - [Link](https://262.ecma-international.org/10.0/#sec-toboolean)

### Example 8
```JavaScript
let x = 5;
console.log(!x);

let y = undefined;
console.log(!y);

let z = null;
console.log(!z);
```

## == vs === 

- `(==)`, this is Abstract Equality Comparison

- `(===)`, this is Strict Equality Comparison
- Abstract Equality Comparison - [Link](https://262.ecma-international.org/10.0/#sec-abstract-equality-comparison)
-  Strict Equality Comparison - [Link](https://262.ecma-international.org/10.0/#sec-strict-equality-comparison)

### Example 9
```JavaScript
console.log(null == undefined); // true

console.log(12 == "12"); // true

console.log(false == "0"); // true

/*

x -> boolean -> ToNumber -> false -> 0

x = 0, y = "0", x == y

y -> ToNumber -> 0

0 == 0 -> true

*/

console.log(null == false); // false

/**

* y -> is a boolean -> ToNumber -> 0

* null == 0

* false

*/

console.log("NaN" == NaN); // false

let obj = {x: 10, valueOf() {return 100;}}

console.log(99 == obj); // false

console.log(100 == obj); // true
```

### Example 10
```JavaScript
console.log(NaN === NaN); //false
console.log(0 === -0) // true

let obj1 = {x: 10};
let obj2 = {x: 10};
let obj3 = {y: 10};
console.log(obj1 === obj2); // false
console.log(obj1 === obj3); // false
console.log(obj1 === obj1); // true
console.log({x: 10} === {x: 10}); // false
```

## Corner Cases

### Example 11
```JavaScript
console.log("" + 0); // 0 -> "0"
console.log("" + (-0)); // -0 -> "0"

console.log("" + []); // [] -> ""
console.log("" + {}); // [object Object]

console.log("" + [1,2,3]); // 1,2,3

console.log("" + [null, undefined]);// ,

console.log("" + [1,2,null, 4]); // 1,2,,4
```

### Example 12
```JavaScript
console.log(0 - "010"); // -10
console.log(0 - "O10"); // NaN
console.log(0 - 010);  // -8
console.log(0 - "0xb"); // -11
console.log(0 - 0xb); // -11

console.log([] - 1); // -1
console.log([""] - 1); // -1
console.log(["0"] - 1); // -1
console.log([6] - 1); // 5
```

### Example 13
```JavaScript
let obj = {x: 10, y: 20};

console.log(`My object is ${obj}`); // My object is [object Object]
console.log("My object is "+obj); // My object is [object Object]

console.log(1 < 2 < 3);// -> (1 < 2) = true -> true < 3 -> 1 < 3 -> true
console.log(3 > 2 > 1);// -> (3 > 2) -> true -> true > 1 -> 1 > 1 -> false
```

## Explicit Conversion

- The different types of explicit conversion in JavaScript are :
    -   String conversions
    -   Numeric conversions
    -   Boolean conversions
    -   Symbol conversions

### String Conversions

### Example 14
```JavaScript
console.log(String(23));   // '23'
console.log(String(true)); // 'true'
console.log(String(32 - false));  // '32'
console.log(String(32 - true));   // '31'
```

### String comparison

-   string is greater than another, JavaScript uses the so-called “dictionary” or “lexicographical” order.
-   strings are compared letter-by-letter.

### Example 15
```JavaScript
console.log( 'Z' > 'A' ); // true
console.log( 'Glow' > 'Glee' ); // true
console.log( 'Bee' > 'Be' ); // true
```

### Numeric conversions

### Example 16
```JavaScript
// Explicit conversion into number
Number(" 12 ");  // 12
Number("-12.34");  // -12.34
Number("\n");   // 0

//null and indefined into a number
Number(null);   // 0
Number(undefined);  // NaN

// Booleans into Number
Number(true); // 1
Number(false); // 0

let age1 = "22";
age1 = +age1;
console.log(typeof(age1)); // number
```

- prompt function always return a String, it automatically converts any input by the user into a string.

### Example 17
```JavaScript
const age = Number(prompt('Age'));
console.log(age);
```

- The parseInt() and parseFloat() functions are used to convert a string to a number data type. 

- parseInt() converts the string to an integer, while parseFloat() converts the string to a floating-point number

### Example 18
```JavaScript
let str = "42";

let num1 = parseInt(str); // converts the string "42" to the number 42
console.log(num1);

let num2 = parseFloat(str); // converts the string "42" to the number 42.0
console.log(num2);
```

### Example 19
```JavaScript
let x = NaN;

console.log(x == NaN); // false

console.log(isNaN(x)); // true

console.log(isNaN("sanket"));// true - isNaN converts the input to a number

console.log(Number.isNaN("sanket")); // false - first checks type
console.log(Number.isNaN(x)); // true

if(typeof(x) == 'number' && x !== x ) {
    console.log(true); // true
}
```

### Example 20

```JavaScript
let x = -0;
console.log(x === 0); // true
console.log(Object.is(x, -0)); // true
console.log(Object.is(x, 0)); // false

console.log(Math.sign(-3)); // -1
console.log(Math.sign(2)); // 1
console.log(Math.sign(-0)); // -0
console.log(Math.sign(0));// 0

console.log(x < 0); // false
```

### Boolean Conversion

### Example 21
```JavaScript
Boolean('');   // false
Boolean(0);    // false     
Boolean(-0);   // false
Boolean(NaN);  // false
Boolean(null);  // false
Boolean(undefined);  // false
Boolean(false);   // false
```

### Boxing
