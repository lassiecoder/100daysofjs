
**Functions & Expressions**


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


*****

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




