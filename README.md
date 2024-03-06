
**Arrow Functions**

It provides a concise syntax for creating functions in JavaScript, written using the `=>` syntax and are especially useful for short, non-method functions.

It looks like this: `(arguments) => expression`.

It creates a function that accepts arguments and evaluates the expression, returning the result.

**For example:**
```javascript
// Arrow function
let multiply = (a, b) => a * b;

console.log(multiply(4, 5)); // Output: 20

// Arrow function with single parameter
let square = x => x * x;

console.log(square(3)); // Output: 9

// Arrow function with no parameters
let greet = () => console.log("Hello!");

greet(); // Output: Hello!
```

### _Multiline arrow functions_

A multiline arrow function in JavaScript allows for the execution of multiple expressions or statements. Unlike single-line arrow functions, multiline arrow functions are enclosed within curly braces `{}`, and if a return value is desired, an explicit `return` statement is required.

**For example:**
```javascript
const sumOfSquaredEvenNumbers = (arr) => {
  // Filter even numbers
  const evenNumbers = arr.filter(num => num % 2 === 0);
  
  // Square each number
  const squaredNumbers = evenNumbers.map(num => num ** 2);
  
  // Sum the squared values
  const sum = squaredNumbers.reduce((total, num) => total + num, 0);
  
  return sum;
};

const numbers = [1, 2, 3, 4, 5, 6];
console.log(sumOfSquaredEvenNumbers(numbers)); // Output: 56 (2^2 + 4^2 + 6^2 = 4 + 16 + 36 = 56)
```

In the above example, the arrow function `sumOfSquaredEvenNumbers` takes an array of numbers `arr` as input. It first filters out the even numbers, then squares each even number, and finally sums up the squared values using the `reduce` method.