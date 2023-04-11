# Introduction of JavaScript

 - JavaScript is a high-level, dynamically-typed programming language. 
 -  JavaScript is a single threaded synchronous language. One thing can be executed at a time in a specific order.
 - It is just-in-time compiled programming language.
 - It is multi-paradigm programming language i.e supports multiple styles of programming.
	 - Procedural Programming
	 - Functional Programming
	 - Object Oriented Programming

## Statements & Expressions	

- Statement is a line of code, which include character, number, operator that performs a specific action or produces a result.

> sum = 3 + 5

- A statement can contain one or more expressions, and an expression can be part of a statement

> add = 6 + 5

- here 6 and 5 are literal value expression, add is variable expression, (+) arithmatic operator expression.

## Keywords

- Keywords are the reserved words in a programming language.
- it has a special meaning to the program.
- it can't be used as a variable name and function name

> e.g
> `var`, `let`, `const`, `if`, etc

## Semicolon

- Every Statement is terminated with a semicolon `;` 
- it's optional to use.

## Comment

- It is used for documentation purpose and avoid by compiler

- Single line comment
```javascript
// This is a single-line comment

```

- Multiple line comment	
```javascript
/*
This is a 
multi-line 
comment

*/
```

## Output

- It is the result of the program which is displayed to the user.
- In JavaScript, There are several ways to print output.
- using `console.log()`
- using `document.write()`
- using `alert()`

### Using Console.log()
- It is a method used to output data or messages to the browser console.
- The `log()` part of `console.log()` is a function call that accepts one or more arguments to be printed to the console.
- The `console.` part of `console.log()` is an object reference that provides access to the `log()` method.

#### Example 
```javascript
console.log("Hello");
console.log("Everyone");
```
#### Output
```
Hello
Everyone
```

#### Example 
```javascript
console.log("Hello", "Everyone");
```
#### Output
```
Hello  Everyone
```
###  using document.write()
- It is a method is used to write dynamic content to an HTML document.

#### Example 
```javascript
<!DOCTYPE html>
<html>
  <head>
    <title>My Webpage</title>
  </head>
  <body>
    <script>
      document.write("<h1>Hi Welcome </h1>");
    </script>
  </body>
</html>
```

###  using  alert()

- It is a method used to display output as a pop-up message.

#### Example 
```javascript
alert("Hello, world!");
```

## Input

- Using the `prompt()` method, we can take user input.
- It only takes a string as its argument.

#### Example 
```javascript
let name = prompt("What is your name?"); 
console.log("Hello, " + name + "!");
```
#### Output
```
What is your name?> robot1
Hello, robot1!
```
