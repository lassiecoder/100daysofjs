
**Code structure and Modern mode – "use strict"**

### Code structure:
🥑 [Statements](#statements) 

🥑 [Semicolons](#semicolons) 

🥑 [Comments](#comments)


### _Statements_

Statements in JavaScript are syntactic constructs and commands designed to execute actions.

```javascript
// Declaration statement
let x;

// Assignment statement
x = 5;

// Conditional statement
if (x > 0) {
  console.log("x is positive");
} else if (x === 0) {
  console.log("x is zero");
} else {
  console.log("x is negative");
}

// Loop statement
for (let i = 0; i < 5; i++) {
  console.log("Iteration " + (i + 1));
}

// Function statement
function greet(name) {
  console.log("Hello, " + name + "!");
}

// Function call statement
greet("world");
                                                                
```

In the above example:

1. Declare a variable `x` using `let`, marking the start of our memory reservation - a declaration statement.
2. Assign the value 5 to `x` (`x = 5;`), effectively filling the allocated memory space - an assignment statement.
3. Utilize an `if...else` statement to assess if `x` is greater than 0, equal to 0, or less than 0, printing different messages based on the condition.
4. Employ a `for` loop to iterate through a set of actions repeatedly, logging messages for each iteration from 0 to 4.
5. Define a function `greet` using a function statement, specifying parameters and instructions for a reusable action.
6. Invoke the `greet` function with the argument "world" to execute its defined behavior and display a greeting message.


### _Semicolons_

In most cases, you can skip using a semicolon if there's a line break.

Here's an example:

```javascript
// Semicolon omitted because of the line break
let x = 5
console.log(x) // Output: 5

// Semicolon included
let y = 10;
console.log(y); // Output: 10
```

In the first line, the semicolon is omitted after `let x = 5` because there's a line break afterward. JavaScript automatically interprets the line break as the end of the statement.

### _Comments_

As programs get more complex, it's important to add comments explaining what the code does and why. Comments can go anywhere in the script and don't impact how it runs because the computer just ignores them.

Here's a simple example:

```javascript
// This is a comment explaining the purpose of the code below

// Declare a variable to store the user's age
let age = 25;

// Check if the user is eligible for voting
if (age >= 18) {
  // If the user's age is 18 or older, log a message
  console.log("You are eligible to vote!");
} else {
  // If the user's age is less than 18, log a different message
  console.log("You are not eligible to vote yet.");
}
```

In the above example:

1. Comments are used to explain the purpose of the code and provide context.
2. The code declares a variable age to store the user's age.
3. An if statement checks if the user's age is 18 or older.
4. Depending on the age, different messages are logged to the console.



### Modern mode – "use strict"

"use strict" directive was introduced in ECMAScript 5 (ES5), which was standardized in December 2009. 

It enforces a stricter set of rules, catching common errors, restricting certain behaviors, and promoting more secure and maintainable code

Here are some important points about it;

1. Prevents silent errors by making them explicit, aiding early detection.
2. Limits global variables; undeclared variables trigger errors instead of becoming globals.
3. Removes default 'this' binding to the global object, preventing unintended modifications.
4. Disables octal syntax to prevent confusion and potential bugs.
5. Enforces stricter error handling; certain actions like deleting variables or functions throw errors.

Here's an example demonstrating the usage of "use strict";

```javascript
"use strict";
x = 10; // Throws a ReferenceError: x is not defined
console.log(x); // This line will not execute due to the error

"use strict";
x = 10; // Throws a ReferenceError: x is not defined
console.log(x); // This line will not execute due to the error

"use strict";
function logThis() {
  console.log(this);
}
logThis(); // Logs undefined instead of the global object

"use strict";
var num = 012; // Throws a SyntaxError: Octal literals are not allowed in strict mode
console.log(num); // This line will not execute due to the error

"use strict";
var x = 10;
delete x; // Throws a SyntaxError: Delete of an unqualified identifier in strict mode
console.log(x); // Output: 10
```

