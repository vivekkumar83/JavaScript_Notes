## Values & Types

 - A Value is represent a piece of data in JavaScript and different representations of value is called types.
	1.  Number Types : A numerical value, such as `34`, `-6.14`, `84`
	2. Boolean Types : true and false
	3. String Types: `"name"`
	4. Undefined Types
	5. Null Types
	6. Symbol Types
	7. Object Types

## Variables	

- A variable is a container that stores a value.
- There are two types of variables exist
	- Static Type : Value of fixed type are stored in a variable of fixed type.
	- Dynamic or Weak Type: Any type of value are stored in variable.

- JavaScript supports weak or dynamic typed variable, so we don't have to declare the type of variable, It can store any type of variable.

### Variables Declare

- Variables are created by using the `let`, `const`, or `var` keywords.

#### Example 
```javascript
var userName;
let age;
```

###  Variables Initialize

- Assign the value to the variables

#### Example 
```javascript
var userName = "tenacious";
let age = 24;

console.log(userName);
console.log(age);
```

#### Output
```
tenacious
24
```

###  Variables Update

- update the assign value of the variable
- `var`  and `let` can be updated
#### Example 
```javascript
var userName = "tenacious";
console.log(userName);

userName = "developer";
console.log(userName);
```

#### Output
```
tenacious
developer
```

#### Example 
```javascript
let userName = "tenacious";
console.log(userName);

userName = "developer";
console.log(userName);
```

#### Output
```
tenacious
developer
```

###  Variables Redeclare

- `var`  can be re-declared
#### Example 
```javascript
var userName = "tenacious";
console.log(userName);

var userName = "developer";
console.log(userName);
```

#### Output
```
tenacious
developer
```

-  `let` can' be re-declared

#### Example 
```javascript
let userName = "tenacious";
console.log(userName);

let userName = "developer";
console.log(userName);
```

#### Output
```
SyntaxError: Identifier 'userName' has already been declared
```

**Note**

> `var` can be updated and re-declared

> `let` can be udated but not re-declared

### Variable using const

- It is used to declare a constant variable that cannot be reassigned.
- It must be initilized with some value
- it can't be updated or re-declared

#### Example
```javascript
const userName = "tenacious";
console.log(userName);

```

#### Output
```
tenacious
```

#### Example for update
```javascript
const userName = "tenacious";
console.log(userName);

userName = "developer";
console.log(userName);

```

#### Output
```
TypeError: Assignment to constant variable.
```

#### Example for redeclared 
```javascript
const userName = "tenacious";
console.log(userName);

const userName = "developer";
console.log(userName);

```

#### Output
```
SyntaxError: Identifier 'userName' has already been declared
```
