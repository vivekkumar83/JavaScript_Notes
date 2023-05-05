# JavaScript Hoisting

- Hoisting is a JavaScript mechanism by which variable and function declarations are moved to the top of their scope before the code is executed.

- This means that you can use a variable or function before it's actually declared in your code.

- However, only variable and function declarations are hoisted, not their values.

- Function expressions and arrow functions behave like variables, so they are hoisted but not initialized to a value.

## Hoisting with var keyword & Function

- When you declare a variable using the `var` keyword, it is hoisted and initialized to `undefined`. 

- Functions are fully hoisted, which means you can use a function before it's declared in your code.

#### Example 1
```JavaScript
greet(); // Output: "Hello, world!"
console.log(num); // Undefined

var num = 12;

function greet() {
  console.log("Hello, world!");
}
```

## Hoisting with let and const keywords

- When you declare a variable using the `let` or `const` keyword, it is hoisted but not initialized. This means that you can't access it.

#### Example 2
```JavaScript
greet(); // Output: "Hello, world!"
console.log(num); // ReferenceError: Cannot access 'num' before initialization

let num = 12;

function greet() {
  console.log("Hello, world!");
}
```

- When you declare a `let` and `const` variable, it creates a "temporal dead zone" where the variable exists but cannot be accessed until it is initialized.

- Attempting to access a `let`  and `const` variable in the temporal dead zone will result in a reference error.

- The time period between when a variable is declared with `let` or `const` and the point at which it is initialized with a value is called TDZ

#### Example 3
```JavaScript
console.log(num); // undefined
 
//  time between this is temporal dead zone

let num = 12; // 
```

# Window & this

- The window object is a global object in JavaScript, which is created along with the global execution context.

- Whenever any JavaScript code is run, a global object and a global execution context are created, and a this keyword is also created, which points to the window object by default.

- The window object contains all the variables and functions that are created in the global scope of a JavaScript program, and they can be accessed using the window.variable or this.variable syntax.

#### Example 4
```JavaScript
var num1 = 10;

function add(num1) {
	var num2 = 20
	var result = num1 + num2;
	return result;
}

console.log(add(num1)); // 30
```
- For example, if you define a variable a in the global scope using the var keyword, it will be attached to the window object, and you can access it using either window.num1 or this.num1 or num1 (by default it is assumed to be window.num1).

-  However, if you define a variable num2 inside a function, it will not be attached to the window object and cannot be accessed using the window or this keyword.

- The this keyword refers to the object that the function belongs to or the object that is currently being operated on. It can have different values depending on the context in which it is used.

- When used inside a function that is a method of an object, the this keyword refers to the object itself. For example, in the following code, this keyword inside the method greet() refers to the object person

#### Example 5
```JavaScript
var person = {
  name: "John",
  greet: function() {
    console.log("Hello, my name is " + this.name);
  }
};

person.greet(); // output: "Hello, my name is John"
```

# JavaScript Scopes

- One of the most fundamental paradigms of nearly all programming languages is the ability to store values in variables, and later retrieve or modify those values.
- The scope is the current context of execution in which variable and functions are "visible" or can be referenced.
- Scopes can also be layered in a hierarchy, so that child scopes have access to parent scopes, but not vice versa.
- JavaScript has the following kinds of scopes:
	* Global Scope
	* Module scope
	* Function Scope
	* Block Scope
	* Lexical Scope

### Global Scope:
* Global scope means that parameters and variables are visible in, all other scopes.
```javascript
var global_var = 1;

function prints()
{
    console.log(global_var); //output: 1
}
console.log(global_var); //output: 1
```
### Function Scope:
* Function scope means that parameters and variables defined in a function are visible everywhere within the function, but are not visible outside of the function.
```javascript
function prints()
{
    var local_var = 2;// a local variable with value 2
    console.log(local_var);
    //the local_var can be used anywhere inside this function
}
console.log(local_variable);//this line will result in ReferenceError, as local_variable is not visible in this line
```
### Module scope:
* In modules, a variable declared outside any function is hidden and not available to other modules unless it is explicitly exported.
* Exporting makes a function or object available to other modules
```javascript
function prints()
{
    var local_var = 2;// a local variable with value 2
    console.log(local_var);
    //the local_var can be used anywhere inside this function
}
console.log(local_variable);//this line will result in ReferenceError, as local_variable is not visible in this line
```
### Block Scope
* The scope created with a pair of curly braces.
* Block scope means that parameters and variables defined in a block and visible within the block.
```javascript
{
	 this is block
}
```
* let and const declarations are blocks scope, but not var declarations.
``` javascript
{
  var a = 10;
  let b = 50;
  const c = 30;
  console.log(a); // 10 
  console.log(b); // 50
  console.log(c); // 30
}
console.log(c); // Uncaught ReferenceError: c is not defined

// Block  --> b : undefined (hoisted in block)
// Block  --> c : undefined (hoisted in block)
// Global --> a : undefined (hoisted in global)

```
### var
* The var statement declares a function-scoped or globally-scoped variable, optionally initializing it to a value.
```javascript
var x = 1;

if (x === 1) {
  var x = 2;

  console.log(x);
  // Expected output: 2
}

console.log(x);
// Expected output: 2
```
* var declarations, wherever they occur, are processed before any code is executed. This is called hoisting
* The scope of a variable declared with var is its current execution context and closures thereof, which is either the enclosing function and functions        	 declared within it, or, for variables declared outside any function, global.
* Duplicate variable declarations using var will not trigger an error, even in strict mode, and the variable will not lose its value, unless another             assignment is performed.
```javascript
"use strict";
function foo() {
  var x = 1;
  function bar() {
    var y = 2;
    console.log(x); // 1 (function `bar` closes over `x`)
    console.log(y); // 2 (`y` is in scope)
  }
  bar();
  console.log(x); // 1 (`x` is in scope)
  console.log(y); // ReferenceError, `y` is scoped to `bar`
}

foo();
```
* In the global context, a variable declared using var is added as a non-configurable property of the global object
### let
* The let declaration declares a block-scoped local variable, optionally initializing it to a value.
```javascript
let x = 1;

if (x === 1) {
  let x = 2;

  console.log(x);
  // Expected output: 2
}

console.log(x);
// Expected output: 1
```
* let allows you to declare variables that are limited to the scope of a block statement, or expression on which it is used.
* Redeclaring the same variable within the same function or block scope raises a SyntaxError.
```javascript
if (x) {
  let foo;
  let foo; // SyntaxError thrown.
}
```
* You may encounter errors in switch statements because there is only one block.
```javascript
let x = 1;
switch (x) {
  case 0:
    let foo;
    break;

  case 1:
    let foo; // SyntaxError for redeclaration.
    break;
}
```
* A block nested inside a case clause will create a new block scoped lexical environment, avoiding the redeclaration errors shown above.
```javascript
let x = 1;

switch (x) {
  case 0: {
    let foo;
    break;
  }
  case 1: {
    let foo;
    break;
  }
}
```
* the let does not create properties of the window object when declared globally
### const
* The const declaration creates block-scoped constants, much like variables declared using the let keyword.
* The value of a constant can't be changed through reassignment, and it can't be redeclared.
* if a constant is an object or array its properties or items can be updated or removed.
```javascript
const number = 42;

try {
  number = 99;
} catch (err) {
  console.log(err);
  // Expected output: TypeError: invalid assignment to const `number'
  // (Note: the exact output may be browser-dependent)
}

console.log(number);
// Expected output: 42
```
* This declaration creates a constant whose scope can be either global or local to the block in which it is declared. 
* Global constants do not become properties of the window object, unlike var variables.
* An initializer for a constant is required. You must specify its value in the same declaration.
* let & const can not access outside of the block
``` javascript
var a = 100;  // global
let b = 50;   // script
const c = 40; // script
{
	var a = 10; // global but updated 
	let b = 20; // block 
	const c = 30; // block
	console.log(a);  // 10
	console.log(b);  // 20
	console.log(c);  // 30
}
console.log(a);  // 10
console.log(b);  // 50
console.log(c);  // 40
```
### Shadowing
* we can not shadowing a let variable using var, we can shadowing only let inside block
``` javascript
let a = 20;
{
    var a = 20;
    console.log(a);
}
console.log(a); 
//  Uncaught SyntaxError: Identifier 'a' has already been declared
```
``` javascript
let a = 20;
function x() {
	var a = 20;
        console.log(a);
}
console.log(a);
// 20
```
* this can be done, because var is functionl block so it's boundry is function 
* but in the above case, it is on the block level scope, so can't shadowing  
``` javascript 
var a = 20;
{
	let a = 20;
  console.log(a); // 20
}
console.log(a); // 20
```
* this is also true because var is in global scope.

* block scope follows lexical scope
``` javascript 
const a = 20;
{
	const b = 100;
	{
		const c = 200;
		console.log(a);
	}
}
```

# Difference Between 'var' and 'let':
* The main difference between var and let is that the scope of the variable that is defined by let is limited to the block in which it is declared, whereas the variable declared using var has the global scope, i.e., can be used throughout the code.
* If we declare a variable using var outside of any block (i.e., in the global scope), then the variable gets added to the window object, whereas variables declared with let will never get added to it.
* We cannot declare the same variable multiple times if one of them is declared using let, whereas we can declare the same variable any number of times using var.
* Variable hoisting can be done using var, but hoisting cannot be done using let.
* Once a variable is declared or initialized, we can change its value anytime and anywhere within its scope. 

## Lexical Enviroment

-   Scope means where you can access a specific variable or a function in code

-   Scope is directly dependent on the lexical enviroment

-   wherever a execution context is created, a lexical enviroment is also created

-   lexical enviroment is the local memory along with the lexical enviroment of it's parent

-   lexical means inhirachical or sequence

-   whenever a execution context is created, you also get refrence to the lexical enviroment of it's parent

``` javascript 
var b = 10;
function a() {
	c();
	function c() {
		console.log(b);
	}
}
a();
```
 
```
Global ----> a:f(a)
             b: 10
	  
a ---------> local 
               c: f(c)
	       this: window
	       Global
	       
c ---------> local 
               this: window
	         closure(a)
	         Global
	       
	       
// this keyword is used in local because it's in lexical enviroment
```

-   scope chain is process of finding value in lexical enviroment

``` javascript 
var x = 1;
a();  // 10
b();  // 100
console.log(x);  // 1

function a() {
	var x = 10;
	console.log(x); // find x in the local enviroment
}

function b() {
	var x = 100;
	console.log(x)
}
```

### AutoGlobal Variable

- In JavaScript, if a variable is declared without the `var`, `let`, or `const` keyword inside a function or a block, it becomes an auto global variable, which means it is automatically added to the global scope during the execution phase.

``` javascript 
function greeting() {
  greet = "hello"; // This is an auto global variable
	console.log(greet);
}

greeting();

console.log(greet); // "hello"
```

- To avoid the creation of auto global variables, it is important to always use the `var`, `let`, or `const` keyword to declare variables, and to use strict mode by adding the `"use strict";` directive at the beginning of the script or function.

``` javascript 
"use strict";

function greeting() {
  greet = "hello"; 
	console.log(greet); // Error
}

greeting();

console.log(greet); 
```

### Lexical Scope and Dynamic Scope

- In lexical scope, the scope of a variable is determined based on the location of the variable declaration in the code. The scope of a variable is fixed at the time of its creation, and it remains the same throughout the execution of the program, regardless of how or where the function is called.

- In dynamic scope, the scope of a variable is determined based on the call stack of the program at runtime. The scope of a variable can change depending on how and where the function is called.

- JavaScript uses lexical scope, also known as static scope.

``` javascript 
var x = 10;

function outer() {
  var y = 20;
  
  function inner() {
    console.log(x); // Output: 10
    console.log(y); // Output: 20
  }
  
  inner();
}

outer();

```

``` javascript 
var teacher = "Sanket"; 
function ask(question) { 
	console.log(teacher, question); 
}

function fun() { 
	var teacher = "Pulkit"; 
	ask("why?");
}
fun();
```

### Corner Cases

``` javascript 
console.log("hi");   // hi

console.lo("hello"); // Error

console.log("bye");
```
- In the above example, there is no error in the parsing phase because `console.` object is created, so fist line print `hi` but in the execution phase there is no `.lo` function exist so it prints error.

``` javascript 
console.log("hi"); // error

console..log("hello"); //error

console.log("bye");
```
- In the above example, there is error in the parsing phase because `console..` object is not created, so in the fist line it throws error.

``` javascript 
console.log("hi"); // hi

console.log("hello"); //  hello

console.log(10..toString()); // 10
```
- In the above example, 10 is primitive so `..` do auto boxing which creates object which is fine. we can also write like this  `console.log((10).toString());`  

``` javascript 
{
    function fun() {
        return "123";
    }
}

console.log(fun);
```
- In the above example, fun is created inside the block but it get acces to the global scope

``` javascript 
"use strict";
{
    function fun() {
        return "123";
    }
    console.log(fun); // [fun]
}

console.log(fun); // error
``` 
- In the above example, fun is created inside the block in the strict mode so we can't get access this in the global scope but it get acces to the block scope

### use case of var
``` javascript 
// we can access both var & let inside thew if block
function fun(x) {
    let i; // var i
    if(x %2 == 0) {
        i = 0;
    } else {
        i = 1;
    }
}

// but we can also write in this better way 

function gun(x) {
    if(x %2 == 0) {
        var i = 0;
    } else {
        var i = 1;
    }
    console.log(i);
}

gun(10);
``` 
### use case of let
```JavaScript
// if you used var inside the for loop then 
// it can be access out side of the for loop that's not good
function fun() {
    for(let i = 0; i < 10; i++) {
        // do something
    }
    console.log(i);
}

function process(x, y) {
    if(x > y) {
        // var temp = x;
        let temp = x;
        x = y;
        y = temp;
    }
    return y - x;
}

fun();
```
