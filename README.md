
**Functions & Function Expressions**


## 🍄 Functions 

Functions in JavaScript are reusable blocks of code that perform a specific task. They allow you to group code into logical units, making your code more organized and easier to manage.

🥑 [Function Declaration](#function-declaration)

🥑 [Local variables](#local-variables)

🥑 [Outer variables](#outer-variables)

🥑 [Parameters](#parameters)

🥑 [Default values](#default-values)

🥑 [Returning a value](#returning-a-value)

🥑 [Naming a function](#naming-a-function)

🥑 [Functions == Comments](#functions-comments)

## 🍄 Function Expresions

Functions expressions allow you to define a function as part of an expression, rather than as a standalone statement.

🥑 [Function is a value](#function-is-a-value)

🥑 [Callback functions](#callback-functions)

🥑 [Function Declaration and Function Expression](#function-declaration-and-function-expression)

*****

## 🍄 Functions 

### _Function Declaration_

It includes the `function` keyword, followed by the function's name, optional parameters within parentheses, and the function's body enclosed in curly braces.

**Syntax:**
```javascript
function functionName(parameter1, parameter2, ...) {
  // function body
}
```

**For example:**
```javascript
// Function declaration
function greet(name) {
  console.log('Hello, ' + name + '!');
}

// Calling the function
greet('John'); // Output: Hello, John!
```

### _Local variables_

Variables declared within a function are local to that function and can only be accessed within its scope.

**For example:**
```javascript
function greet(name) {
  let message = 'Hello, ' + name + '!';
  console.log(message);
}

greet('John'); // Output: Hello, John!
console.log(message); // Error: message is not defined
```

### _Outer variables_

Functions can access variables declared outside of them. These variables are called outer variables.

**For example:**
```javascript
let greeting = 'Hello';

function greet(name) {
  console.log(greeting + ', ' + name + '!');
}

greet('John'); // Output: Hello, John!
```

### _Parameters_

Parameters are placeholders for values that are passed into a function when it is called. They allow functions to accept input and perform operations on it.


**For example:**
```javascript
function add(a, b) {
  return a + b;
}

let sum = add(3, 5); // sum is 8
```

### _Default values_

You can assign default values to function parameters. If a parameter is not provided when the function is called, it will use the default value.

**For example:**
```javascript
function greet(name = 'Guest') {
  console.log('Hello, ' + name + '!');
}

greet(); // Output: Hello, Guest!
greet('John'); // Output: Hello, John!
```

### _Returning a value_

Functions can return a value using the `return` statement. This allows the function to produce output that can be used elsewhere in your code.

**For example:**
```javascript
function multiply(a, b) {
  return a * b;
}

let result = multiply(3, 5); // result is 15
```

### _Naming a function_

Function names should be descriptive and indicative of their purpose. This makes your code more readable and easier to understand.

**For example:**
```javascript
function calculateArea(radius) {
  return Math.PI * radius ** 2;
}
```

### _Functions == Comments_

Well-named functions can often replace comments, providing clear and self-documenting code.

**For example:**
```javascript
// Function to calculate the area of a circle
function calculateArea(radius) {
  return Math.PI * radius ** 2;
}
```

In the above example, the function name `calculateArea` conveys the purpose of the code better than the comment. Functions with descriptive names make the code more readable and maintainable.

## 🍄 Function Expressions

### _Function is a value_

In JavaScript, functions are treated as values. This means they can be assigned to variables, passed as arguments, and returned from other functions just like any other data type.

**For example:**
```javascript
function sayHi() {
  alert("Hello");
}

let func = sayHi; // Assigning the function to a variable

func(); // Outputs: Hello
sayHi(); // Outputs: Hello
```

In the above example;

1. The function `sayHi` is declared and defined.
2. The function is assigned to the variable `func`.
3. Both `func` and `sayHi` can be called to execute the function and output "Hello".

This behavior illustrates that functions are indeed values in JavaScript. They can be stored in variables, passed around, and called just like any other value. 

### _Callback functions_

Callback functions are functions that are passed as arguments to other functions and are expected to be called back later if necessary. 

**For example:**
```javascript
function ask(question, yes, no) {
  if (confirm(question)) {
    yes();
  } else {
    no();
  }
}

function showOk() {
  alert("You agreed.");
}

function showCancel() {
  alert("You canceled the execution.");
}

ask("Do you agree?", showOk, showCancel);
```

In the above example, The function `ask` asks the question and depending on the user's response, `yes()` or `no()`.

 `showOk` and `showCancel` are callback functions. They are passed as arguments to the `ask` function and will be called back depending on the user's response.

We can also use function expressions to define callback functions inline:

**For example:**
```javascript
ask(
  "Do you agree?",
  function() { alert("You agreed."); },
  function() { alert("You canceled the execution."); }
);
```

Anonymous function expressions are used directly inside the `ask` function call. They serve the same purpose as named functions but are declared inline and are not accessible outside of the `ask` function.

### _Function Declaration and Function Expression_

***Function Declaration*** and ***Function Expression*** are two ways to define functions in JavaScript, each with its own syntax and behavior.

***<ins>Function Declaration</ins>:***

***Syntax:*** Declared as a separate statement in the main code flow using the function keyword.

***Hoisted:*** Function declarations are hoisted, meaning they are moved to the top of their scope during compilation and can be called before they are defined.

**For example:**
```javascript
function greet() {
  console.log('Hello!');
}
greet(); // Output: Hello!
```

***<ins>Function Expression</ins>:***

***Syntax:*** Created inside an expression or another syntax construct by assigning it to a variable.

***Not Hoisted:*** Function expressions are not hoisted, meaning they cannot be called before they are defined in the code.

**For example:**
```javascript
let greet = function() {
  console.log('Hello!');
};
greet(); // Output: Hello!
```

Let's talk about differences!

***Hoisting:*** Function declarations are hoisted, function expressions are not.

***Accessibility:*** Function declarations are accessible throughout their scope, while function expressions are only accessible through the variable they are assigned to.

**For example:**
```javascript
greet(); // Works fine with function declaration
function greet() {
  console.log('Hello!');
}

greet(); // Throws an error with function expression
let greet = function() {
  console.log('Hello!');
};
```

***Use Cases:***

Function declarations are useful for creating named functions that are accessible throughout the scope.
Function expressions are useful for creating functions dynamically or passing them as arguments to other functions.

Keep coding and stay curious! 🌸 🎯 💁🏻‍♀️