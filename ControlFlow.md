## Conditional Flow:

### if statement:
```javascript
if (condition) {
  // code to be executed if condition is true
}
```
```javascript
let x = 5;
if (x > 0) {
  console.log("x is a positive number");
}
```

### if...else statement:
```javascript
if (condition) {
  // code to be executed if condition is true
} else {
  // code to be executed if condition is false
}
```
```javascript
let x = 5;
if (x > 0) {
  console.log("x is a positive number");
} else {
  console.log("x is not a positive number");
}
```
### if...else if...else statement::
```javascript
if (condition1) {
  // code to be executed if condition1 is true
} else if (condition2) {
  // code to be executed if condition2 is true
} else {
  // code to be executed if none of the conditions are true
}
```
```javascript
let x = 5;
if (x > 0) {
  console.log("x is a positive number");
} else if (x < 0) {
  console.log("x is a negative number");
} else {
  console.log("x is zero");
}
```
### Switch Case
```javascript
switch (expression) {
  case value1:
    // code to be executed if expression equals value1
    break;
  case value2:
    // code to be executed if expression equals value2
    break;
  default:
    // code to be executed if expression does not equal any of the values
}
```
```javascript
function groceryPrice(exp){
 switch (exp) {
  case 'Cookies':
    console.log('Cookies cost 100 rupees');
    break;
  case 'Milk':
    console.log('Milk cost 60 rupees');
    break;
  case 'Fruits':
    console.log('Fruits cost 300 rupees');
    break;
  case 'Corn Flakes':
    console.log('Corn Flakes cost 150 rupees');
    break;
  default:
    console.log(exp + ' is not available right now');
  }
}


groceryPrice('Cookies');
//output: Cookies cost 100 rupees

groceryPrice('Fruits');
//output: Fruits cost 300 rupees

groceryPrice('Peanut');
//output: Peanut is not available right now

```
## Loops:
### while()
```javascript
while (condition) {
  // code to be executed
}
```
```javascript
// print numbers from 1 to 10
let i = 1;
while (i <= 10) {
  console.log(i);
  i++;
}
```
### do...while()
```javascript
do {
  // code to be executed
} while
```
```javascript
// print numbers from 1 to 10
let i = 1;
do {
  console.log(i);
  i++;
} while (i <= 10);
```
### for()
```javascript
for (initialization; condition; update) {
  // code to be executed
}
```
```javascript
// print numbers from 1 to 10
for (let i = 1; i <= 10; i++) {
  console.log(i);
}
```
### For...in
* The for-in loop iterates over the enumerable properties of an object, including its prototype chain. It is commonly used to iterate over the properties of an object or to iterate over the indices of an array.
```javascript
for (variable in object) {
  // code to be executed
}
```
```javascript
const obj = { a: 1, b: 2, c: 3 };

for (let prop in obj) {
  console.log(prop); // outputs "a", "b", "c"
  console.log(obj[prop]); // outputs 1, 2, 3
}
```
### For...of
* The for-of loop is a new addition to the language as part of ECMAScript 6. It is used to iterate over the values of an iterable object such as an array, a string, or a Map.
```javascript
for (variable of iterable) {
  // code to be executed
}
```
```javascript
const arr = [1, 2, 3];

for (let value of arr) {
  console.log(value); // outputs 1, 2, 3
}
```
### For-await-of statement
* used to create loops that iterate over async and sync objects like arrays, map-sets, etc
* used only inside an async function
```javascript
for await (variable of iterable) { statement }
```
```javascript
async function main() {
    for await (const x of ['apple', 'mango']) {
        console.log(x);
    }
}
main();
```
