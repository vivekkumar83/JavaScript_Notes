## High Order Functions

- In JavaScript, functions are considered first-class citizens, meaning they can be assigned to variables, passed as arguments, and returned as values from other functions.

- High order functions are functions that can take one or more functions as arguments or return a function as a result.

- Common examples of HOFs in JavaScript include map, filter, reduce, and forEach.

### Example 1: forEach method
```JavaScript
const numbers = [1, 2, 3, 4, 5];
numbers.forEach((num) => console.log(num));

/* Output
1
2
3
4
5
*/
```

### Example 2: Custom filter function
```JavaScript
function filter(array, callback) {
  const result = [];
  for (const item of array) {
    if (callback(item)) {
      result.push(item);
    }
  }
  return result;
}
const numbers = [1, 2, 3, 4, 5];
const evenNumbers = filter(numbers, (num) => num % 2 === 0);
console.log(evenNumbers); // Output: [2, 4]
```

## Callback Functions

- A callback function is a function that is passed as an argument to another function and is invoked within that function.

- Callback functions allow for asynchronous and event-driven programming in JavaScript.

- They provide a way to execute code when a certain task or event is completed.

- Callbacks are commonly used in scenarios such as handling asynchronous operations, event handling, and functional programming.

- Callback functions can be synchronous or asynchronous, and they can be anonymous or named functions.

### Example 3 : Synchronous Callback Functions
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

### Problems with callbacks
- Inversion of control (Promises can resolve this issue)
- Callback hell -> readability problem 

## JavaScript runtime environment

![enter image description here](https://res.cloudinary.com/slawinski-dev/image/upload/v1648757381/javascript-runtime-environment.png)

- JavaScript is a single threaded synchronous language.

- One thing can be executed at a time in a specific order.

- The concept of asynchronous nature in JavaScript is crucial for handling time-consuming operations, such as network requests or file I/O, without blocking the execution of other tasks.

- Asynchronous operations allow code to continue executing without waiting for the completion of time-consuming tasks.

- JavaScript provides mechanisms, such as callbacks, Promises, and async/await, to handle asynchronous tasks.

- If everything in JavaScript that took a significant amount of time, blocked the browser, then we would have a pretty bad user experience

- This is where concurrency and the event loop comes into picture 

- The event loop is constantly checking the call stack to see if it is empty so that it can add anything into the call stack from the callback queue

### Example 5 
```JavaScript
console.log("1");
// goes on call stack and runs 1
setTimeout(() => {
  console.log("2"), 1000;
});
// gets sent to web api
// web api waits 1 sec, runs and sends to callback queue
// the javascript engine keeps going
console.log("3");
// goes on call stack and runs 3
// event loop keeps checking and see call stack is empty
// event loop sends calback queue into call stack
// 2 is now ran

// 1
// 3
// 2

// Example with 0 second timeout

console.log("1");
setTimeout(() => {
  console.log("2"), 0;
});
console.log("3");

// 1
// 3
// 2

// Still has the same output
```

### Example 6
```JavaScript
function timeConsumingByLoop() {
    console.log("loop starts");
    for(let i = 0; i < 1000000000; i++) {
        // some task
    }
    console.log("loop ends");
} 
function timeConsumingByRuntimeFeature0() {
    console.log("Starting timer");
    setTimeout(function exec() {
        console.log("Completed the timer0");
        for(let i = 0; i < 1000000000; i++) {
            // some task
        }
    }, 5000); // 5 sec timer
}
function timeConsumingByRuntimeFeature1() {
    console.log("Starting timer");
    setTimeout(function exec() {
        console.log("Completed the timer1");
        // while(true) {}
    }, 0); // 0 s timer
}
function timeConsumingByRuntimeFeature2() {
    console.log("Starting timer");
    setTimeout(function exec() {
        console.log("Completed the timer2");
    }, 200); // 200 ms timer
}
console.log("Hi");
timeConsumingByLoop();
timeConsumingByRuntimeFeature0();
timeConsumingByRuntimeFeature1();
timeConsumingByRuntimeFeature2();
timeConsumingByLoop();
console.log("By");
```
### Example 7
```JavaScript
let count = 0;
let y = setInterval(function exec() {
    count++;
    console.log(count);
    if(count > 15) {
        clearInterval(y);
    }
}, 2000);
```
