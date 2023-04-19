# Functions in JavaScript

- DRY stands for `Don't Repeat Yourself`
- The DRY concept is all about avoiding code duplication and redundancy in your codebase.
- Functions are an essential building block for creating reusable code and reducing redundancy in your codebase.
-  A function can be defined once and used multiple times throughout your program.

## Function Declaration 

- It is used to define a named function.
- It is also known as Function Statement.
- camelCase naming is used for Function Declaration 

**Syntax**
```JavaScript
function functionName(parameter1, parameter2) {
  // function body
  return value;
}
```

- For executing the function, we call the function i.e  invoking it to execute the code within its body

**Syntax**
```JavaScript
functionName(argument1, argument2);
```

#### Example1
```JavaScript
function greet(name) {
  console.log(`Hello, ${name}!`);
}

greet("John");

// Output : Hello, John!
```

#### Example2
```JavaScript
function addNumbers(num1, num2) {
  return num1 + num2;
}

console.log(addNumbers(20, 10));

// Output : 30
```

### Return Keyword 

- The `return` keyword is used to end the execution of a function and optionally return a value to the caller.
- The return statement is used to explicitly return a value from a function to the caller. If you don't explicitly return anything from a function, it will automatically return undefined.
- console.log() is a built-in function in JavaScript that logs a value to the console, but it also returns undefined by default.

#### Example3
```JavaScript
function greet(name) {
  console.log(`Hello, ${name}!`);
}

let result = greet("John"); // Hello, John!

console.log(result); // undefined
```
- In the above program, by-defult `undefined` is returned, which is stored in result.
 
#### Example4
```JavaScript
function addNumbers(num1, num2) {
  return num1 + num2;
}

let result = addNumbers(20, 10);

console.log(result); // 30
```
- In the above program, return keyword returns the value to the caller which is stored in result.
 
## Parameters & Arguments

- Parameters are the variables defined in a function declaration.
- Arguments are the values passed to a function when it is called.
- Define any number of parameters for a function by separating them with commas in the function definition.

#### Example4
```JavaScript
function addNumbers(num1, num2, num3) {
  return num1 + num2 + num3;
}

let result = addNumbers(20, 10, 20);

console.log(result); // 50
```

> In the above program, num1,num2, and num3 are the parameters and 20, 10 and 20 are the arguments

- if the arguments are less than the parameters, the remaining parameters will be assigned the value `undefined`.

#### Example 5
```JavaScript
function addNumbers(num1, num2, num3) {
  return num1 + num2 + num3;
}

let result = addNumbers(20, 10);

console.log(result); // NaN
```

- if the arguments are greater than the parameters, then the extra arguments are ignored

#### Example 6
```JavaScript
function addNumbers(num1, num2, num3) {
  return num1 + num2 + num3;
}

let result = addNumbers(20, 10, 20, 10);

console.log(result); // 50
```

### Default Parameters

- Default parameters in JavaScript allow you to specify a default value for a parameter if no argument is passed to the function or if the argument is `undefined`.

#### Example 7
```JavaScript
function greet(name = "friend") {
  console.log(`Hello, ${name}!`);
}

greet(); // output: "Hello, friend!"
greet("Alice"); // output: "Hello, Alice!"
```

#### Example 8
```JavaScript
function greet(name = "friend", greeting = `Hello, ${name}!`) {
  console.log(greeting);
}

greet(); // output: "Hello, friend!"
greet("Alice"); // output: "Hello, Alice!"
greet("Bob", "Hi there!"); // output: "Hi there!"
```

###  Rest Parameters(...)

- Rest parameters in JavaScript allow to pass an arbitrary number of arguments to a function as an array.
- It returns the array of element

#### Example 9
```JavaScript
function sum(x,y,...numbers) {
  let total = 0;
  for (let number of numbers) {
    total += number;
  }

	console.log(numbers); // [6,7,8]
    return total+x+y;
}

console.log(sum(4, 5, 6, 7, 8)); // output: 30
```
