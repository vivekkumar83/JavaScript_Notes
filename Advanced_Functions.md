# Advanced Functions

- Functions have properties & methods just like other objects so it is also called first class object.
- Functions are the callable object.
- Function Statements is also known as function declaration.

```JavaScript
a();  // a called
function a() {
	console.log("a called");
}
a();   // a called
```
> Function declaration is Hoisted, so It calls the functions before declaration.

## Function Expression

- Function expressions in JavaScript provide a way to define functions as expressions and assign them to variables.

- These are the Function Expressions

```JavaScript
let f = function gun() { // named function expression
    // some impl
}

let a = function() { // anonymous function expression
    // okk some more impl
}

(function x() {
    // can you stop it ?
}) // function expression

(function (){
    // i am done
})
```

- Function expressions can be anonymous or named. Anonymous function expressions are functions without a name, while named function expressions have a name.

```JavaScript
let x = function () {
    console.log('HI');
}
console.log(x); // [Function: x]

x(); // HI
```

- In JavaScript, function expressions are not hoisted like function declarations.
- The variable `add` is hoisted, but it's initially assigned the value `undefined`.

```JavaScript
console.log(add(2, 3)); // Error: add is not a function

var add = function(a, b) {
  return a + b;
};

```

### Scope of Function Expression

```JavaScript
var b = function xyz() {  
	console.log("b called");  // b called
	console.log(xyz);         // Function:xyz
}
b();   
xyz(); // we can not access xyz as global scope 
because it is created in local scope
```

### Use Case of Named Function Expression
- Named Function Expression gets higher priority then anonymous function expression

- `Code readability:` Giving meaningful names to functions improves code readability and makes it easier for other developers to understand the purpose and functionality of the code

```JavaScript
const calculateArea = function rectangleArea(length, width) {
  return length * width;
}

console.log(calculateArea(3,5)); //15
```

- `Recursive functions:` By giving the function a name, it can reference itself, allowing the recursive logic to work correctly. This makes it easier to implement algorithms like calculating factorial or traversing tree structures.

```JavaScript
const factorial = function factorial(n) {
  if (n <= 1) {
    return 1;
  }
  return n * factorial(n - 1);
};
console.log(factorial(5)); // Output: 120
```

- `Function References within their own scope:` Named function expressions allow the function to refer to itself within its own scope. This can be useful in situations where the function needs to call itself or manipulate its own definition within its body.

```JavaScript
const performOperation = function operation() {
  // ... do some operations
  if (condition) {
    operation(); // self-reference within the function
  }
};
```

- `Debugging and stack traces:` When an error occurs and a stack trace is generated, having named function expressions provides more informative and readable information. Instead of seeing an anonymous function in the stack trace, the named function expression's name is displayed, making it easier to identify the function and its location in the code.

## Use Case of Function Expression

### IIFE - IMMEDIATELY INVOKED FUNCTION EXPRESSION
-   A JavaScript immediately invoked function expression is a function defined as an expression and executed immediately after creation.

-   When you define a function, the JavaScript engine adds the function to the global object.

-   if you declare a variable outside of a function using the var keyword, the JavaScript engine also adds the variable to the global object

-   If you have many global variables and functions, the JavaScript engine will only release the memory allocated for them until the global object loses its scopes.

-   It creates a private scope for variables and functions, preventing global scope pollution and naming conflicts.

- It can also be referred to as a Self-Executing Anonymous Function.

```JavaScript
(function(name) {
	var greet = "How are you?";
  console.log("Hello, " + name + ", "+greet);
})("vivek"); // Hello, vivek, How are you?

// Error: name is not defined
console.log(name); 
```

### Passing Functions as Arguments

- Function expression can  be treated as values and used to be passed as arguments to other functions

```JavaScript
// Example of passing a function as an argument
function sayHello() {
  console.log('Hello!');
}

function greet(fn) {
  fn(); // Invoking the passed function
}

greet(sayHello); // Output: Hello!
```

-   The most common use case of passing functions as arguments is to use them as **callback functions**.

-   Callback functions are functions that are passed as arguments to other functions and executed later.

```JavaScript
// Example: Using a callback function
function calculate(a, b, operation) {
  var result = operation(a, b);
  console.log('Result:', result);
}

function add(a, b) {
  return a + b;
}

calculate(5, 3, add); // Output: Result: 8
```

-   Functions that accept other functions as arguments are called **higher-order functions**.

-   Higher-order functions provide a powerful abstraction mechanism and enable code reuse.

```JavaScript
// Example: Higher-order function using a callback
function doTwice(fn, value) {
  fn(value);
  fn(value);
}

function greet(name) {
  console.log('Hello, ' + name + '!');
}

doTwice(greet, 'John');
// Output:
// Hello, John!
// Hello, John!
```
### Corner Cases 

```JavaScript
// Example: Anonymous function as an argument
function doSomething(callback) {
  callback();
}

doSomething(function() {
  console.log('Anonymous function called.');
}); // Output: Anonymous function called.
```
```JavaScript
// Example: Function expression as an argument
function performOperation(operation) {
  var result = operation(5, 3);
  console.log('Result:', result);
}

performOperation(function(a, b) {
  return a * b;
}); // Output: Result: 15

```

### Function returning Function

- Functions can return other functions as values.
- This concept of returning functions allows for the creation of higher-order functions

```JavaScript
function myFunc(){
    function hello(){
        return "hello world"
    }
    return hello;
}

const ans = myFunc();
console.log(ans()); // hello world
```

```JavaScript
// Example: Returning an anonymous function
function createMultiplier(factor) {
  return function(number) {
    return number * factor;
  };
}

var multiplyByTwo = createMultiplier(2);
console.log(multiplyByTwo(5)); // Output: 10
```

-   Returning a function creates a closure, which preserves the variables of the outer function even after it has finished executing.

-   The returned function has access to the variables in its lexical scope, providing encapsulation and privacy.

```JavaScript
// Example: Closure and lexical scope
function outer() {
  var outerVariable = 'I am from outer function';

  return function inner() {
    console.log(outerVariable);
  };
}

var innerFunction = outer();
console.log(innerFunction); // [Function: inner]
innerFunction(); // Output: I am from outer function
```

- The ability of function to be used as values and can be passed these as an arguments to another function and can be returned from the function is this ability is known as first class function

- First class function is also known as first class citizen

## Arrow Functions

-   Arrow functions are defined using a shorter syntax using the `=>` arrow operator.

-   They can have either a single expression or a block of statements as their body.

- Arrow functions are commonly used for anonymous functions and as callbacks.

```JavaScript
// Example of arrow function syntax
const greet = () => {
  console.log('Hello!');
};

greet(); // Output: Hello!
```

- If the function body consists of a single expression, the curly braces `{}` and the `return` keyword can be omitted.

```JavaScript
// Example: Single-expression arrow function
const add = (a, b) => a + b;

console.log(add(2, 3)); // Output: 5
```

-  Arrow functions do not have their own `arguments` object.

-  If you need to access the arguments passed to an arrow function, you can use the rest parameters syntax (`...args`) or pass arguments explicitly.

```JavaScript
// Example: Accessing arguments in an arrow function
const sum = (...args) => {
  return args.reduce((total, num) => total + num, 0);
};

console.log(sum(1, 2, 3, 4)); // Output: 10
```

-  Arrow functions do not have their own `this` value. Instead, they inherit the `this` value from the enclosing context.

-  This behavior is called lexical `this` binding, and it avoids the need for explicit `this` binding using `bind`, `call`, or `apply`.

```JavaScript
// Example: Lexical `this` binding in arrow functions
const person = {
  name: 'John',
  greet: function() {
    setTimeout(() => {
      console.log('Hello, ' + this.name + '!');
    }, 1000);
  }
};

person.greet(); // Output: Hello, John!
```

### Use Cases of Arrow Functions

- Arrow functions are commonly used for short, concise functions, especially as callbacks and for array methods like `map`, `filter`, and `reduce`.

- DOM-level methods like setTimeout, setInterval, addEventListener are great applications of the Arrow functions.

- They cannot be used as constructors with the `new` keyword, and they lack their own

```JavaScript
// Example: Using arrow functions as callbacks
const numbers = [1, 2, 3, 4, 5];

const doubled = numbers.map(num => num * 2);
console.log(doubled); // Output: [2, 4, 6, 8, 10]

const evenNumbers = numbers.filter(num => num % 2 === 0);
console.log(evenNumbers); // Output: [2, 4]
```

### Use Cases Summary

- Function Declaration: Use when you need a named function that can be accessed throughout your code or when you want to define reusable code blocks.
- Function Expression: Use when you need to assign a function to a variable or pass it as an argument to another function.
- Arrow Function: Use when you want a concise syntax for anonymous functions or callbacks, especially when working with array methods like `map`, `filter`, and `reduce`.

## Pass-by-value or Pass-by-reference

- In JavaScript, the concepts of pass-by-value and pass-by-reference determine how values are passed and assigned to variables or passed as arguments to functions.

- In pass-by-value, the actual value of a variable is passed and copied into a new variable.

- When a primitive data type (e.g., number, string, boolean) is passed, a new copy of the value is created, and any modifications to the new variable do not affect the original value.

- The original variable and the copied variable are independent of each other.

```JavaScript
var num1 = 60;
var num2 = 60;
console.log(num1 === num2); // true
```

-   In pass-by-reference, a reference to the original object is passed and assigned to a new variable.

-   When an object (including arrays and functions) is passed, the new variable points to the same object in memory. Modifying the new variable also modifies the original object.

```JavaScript
let obj = { name: 'John' };

function changeName(o) {
  o.name = 'Jane';
}

changeName(obj);
console.log(obj.name); // Output: Jane (modified)
```
