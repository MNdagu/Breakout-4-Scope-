### 1. What is scope in JavaScript, and why is it important?
-<span style = color:red>Scope</span> in JavaScript refers to the context in which variables and functions are accessible. It determines the visibility and lifetime of variables, which is essential for managing and organizing code, avoiding conflicts, and ensuring variables are used correctly.

<strong>Importance of scope</strong>
 1. <u>Avoids Variable Conflicts:</u>

-Scope helps prevent variables from being overwritten or conflicted, especially in larger programs with many variables.

2. <u>Encapsulation:</u>

-Scope allows functions to encapsulate variables

3. <u>Code Readability and Maintenance:</u>

-Easy to read and maintain code

4. <u>Memory Mnagement:</u>

-Variables are destroyed when they go out of scope, aiding in memory management by freeing up resources no longer needed.

### 2. Can you explain the difference between global scope and local scope?

-In <span style = color:red>global scope</span> variables and functions are declared outside any function or block and are in the global scope. They are accessible from anywhere in your code and exist for the duration of the application's runtime.

-In <span style = color:red>local scope</span> variables and functions are declared within a function or block. They are accessible only within the function or block and exist only for the duration of the function or block execution.

### 3. How does JavaScript handle scope in functions compared to block-level scope?

With <span style = color:red>block-level scope</span>, introduced in ES6,variables declared with 'let' or 'const' are confined to the block (`{}`) in which they are declared,such as 'if' statement or 'for' loop.

With <span style = color:red>function scope</span>,variables declared with 'var' inside a function are only accessible within that function.Even if you declare another variable with the same name outside the function, the inner variable takes precedence within the function.

### 4. How do var, let, and const differ in terms of scope?

Variables declare with <span style = color:red>var</span> are only accessible within the function they are declared in.The scope of a var variable is of functional or global scope.

Variables declared with <span style = color:red>let</span> and <span style = color:red>const</span> are only accessible within the curly braces {} of the block where they are declared. The scope of both a let variable and a const variable is block scope.

### 5. What are the implications of declaring a variable without any keyword (i.e., no var, let, or const)?

In JavaScript, declaring a variable without any keyword (var, let, or const) creates a <span style = color:red>global variable</span> by default.

This can have several negative implicaions:

1. <u>Global Pollution:</u>
Makes it harder to track and manage variables within the global namespace.

2. <u>Scope issues:</u>
These variables are accessible from anywhere in your code, including other functions and scripts.

3. <u>Strict Mode Errors:</u>
In strict mode,declaring a variable without a keyword throws an error.

Example:
```
name = "John"; // Declared without a keyword (becomes global)

function sayHello() {
  console.log(name); // Accesses the global variable
}

sayHello();
```

### 6. What is the scope chain, and how does JavaScript use it to resolve variable access?

The <span style = color:red>scope chain</span> in JavaScript is the mechanism that JavaScript uses to resolve variable references. When JavaScript encounters a variable name, it searches for the variable in the <span style = color:red>'current scope'</span>. If the variable is not found in the current scope, the JavaScript interpreter searches the <span style = color:red>'outer scope'</span>, and lastly if the variable is not found, the Javascript interpreter searches the <span style = color:red>'global scope'.</span>
If the variable is not found in any of the scopes, the JavaScript interpreter throws a <span style = color:red>'ReferenceError'</span> exception.

### 7. What are some differences between lexical scope and dynamic scope? Which one does JavaScript use?

Lexical(static) scope and dynamic scope are two different ways programming languages <strong>determine where to find a variable when its name is referenced in your code.</strong>

<span style = color:red>Lexical scope</span> focuses on the structure of the code to determine variable accessibility. Variables are looked up based on their location in the code where they are defined (lexicon).Decisions about variable access are made at compile time (or when the code is parsed).This approach leads to more predictable and easier to reason about code.

<span style = color:red>Dynamic scope</span> relies on the <strong>runtime call stack</strong> to determine variable accessibility.Variables are looked up based on the calling context of a function.Decisions about variable access are made at runtime.This approach can be less predictable and can lead to unexpected behavior in certain situations.

The runtime call stack is a fundamental concept in JavaScript's execution. It's a <strong>Last In, First Out (LIFO)</strong> data structure that keeps track of the function calls currently happening in your program. 

### 8. What is a closure, and how does it relate to scope in JavaScript?

In JavaScript, a <span style = color:red>closure</span> is <strong>a powerful concept that combines a function bundled together (enclosed) with references to its surrounding state</strong>, specifically the lexical environment.
Closures leverage lexical scoping to create functions that can access variables even after their enclosing function has finished executing.

Example:
```
function createGreeter(greeting) {
  // greeting is a local variable in createGreeter

  function greet(name) {
    console.log(greeting + ", " + name + "!");
  }

  return greet;  // Returning the inner function (closure)
}

const helloGreeter = createGreeter("Hello");
helloGreeter("Bob"); // Output: Hello, Bob!

const goodbyeGreeter = createGreeter("Goodbye");
goodbyeGreeter("Alice"); // Output: Goodbye, Alice!
```