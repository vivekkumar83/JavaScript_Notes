## Javascript Engine

- The JavaScript engine is a program that executes JavaScript code. It is responsible for parsing, compiling, and executing the code.
- JavaScript engine mainly consist of : 
	- The Parser
	- The Compiler

- The parser is responsible for reading the code and converting it into an Abstract Syntax Tree (AST). 

- The AST is a tree-like structure that represents the structure of the code. The parser checks the syntax of the code to ensure that it is valid JavaScript code.

- The engine then compiles the AST into bytecode.

- The bytecode is then executed by the engine's interpreter.

- As the interpreter executes the code, it identifies "hot" functions, which are functions that are called frequently or take a long time to execute.

- The engine then optimizes these hot functions by compiling them into machine code using JIT compilation. The optimized machine code is then cached so that it can be reused later.

- The engine continues to execute the code, using the optimized machine code for the hot functions and the interpreter for the rest of the code.

- JIT compilation compiling the JavaScript code into machine code just before it is executed. The compiled code is then cached so that it can be reused later. This caching allows the engine to avoid recompiling the same code multiple times, resulting in faster execution times.

## Call Stack

- The call stack is a data structure used by the JavaScript engine to manage function calls. It is a stack data structure, which means that the last function that was called is the first function that will be executed.

- The call stack is determines the order in which functions are executed.

- All the execution context is managed by the call stack.

- An execution context is a concept in JavaScript that refers to the environment in which a piece of code is executed. Every time JavaScript code is run, it runs in a new execution context.

- There are 2 types of execution context in JavaScript, Global or Function.

-  There are 2 stages as well to each context, the parsing and executing phase.

- 1 stage(parsing phase) is the memory creation phase,inside this variable & function in key-value pair exist.

- 2 stage is the execution pahse, thread of execution start from here, one line at a time

## Memory Heap

- The memory heap is a place to store and write information so that we can use our memory appropriately. It is a place to allocate, use, and remove memory as needed.

- JavaScript is a garbage collected language.

- If you allocate memory inside of a function, JavaScript will automatically remove it from the memory heap when the function is done being called.

- JavaScript completes garbage collection with a mark and sweep method.

## How JavaScript Code is Executed

#### Example 1
```JavaScript
var n = 2;
function square(num) {
	var ans = num * num;
	return ans;
}
var square2 = square(n);
console.log(square2)     // 4
var square4 = square(4);
console.log(square4);    // 16
```

-   When a JavaScript program is executed, a Global Execution Context (GEC) is created first, which represents the global scope of the program.

-   The GEC contains all the global variables and functions declared in the program, including the `n` variable and the `square` function in this example.

-   As the program execution proceeds, the JavaScript engine keeps track of the current execution context by maintaining a Call Stack.

-   Whenever a new function is invoked, a new Function Execution Context (FEC) is created and pushed onto the top of the call stack.

-   In this example, when the `square` function is called with the argument `n`, a new FEC is created with its own local memory space to store the `num` and `ans` variables.

-   The `square` function is executed within this FEC, and when it finishes executing, the FEC is popped off from the top of the call stack.

-   The returned value from the function is stored in the `square2` variable, which is in the GEC.

-   Similarly, when the `square` function is called again with the argument `4`, another FEC is created and pushed onto the top of the call stack.

-   The `square` function is executed within this FEC, and when it finishes executing, the FEC is popped off from the top of the call stack.

-   The returned value from the function is stored in the `square4` variable, which is in the GEC.

-   Finally, when the program execution is complete, the GEC is also popped off from the top of the call stack and the program terminates.
