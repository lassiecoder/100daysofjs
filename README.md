
**Basic operators & Math**


## 🍄 Basic Operators

In JavaScript, basic operators are symbols that perform operations on operands, which can be values or variables. 

🥑 [Unary Operators](#unary-operators) 

🥑 [Binary Operators](#binary-operators) 

🥑 [Operand Operators](#operand-operators) 
 

## 🍄 Math in JS

🥑 [Addition +](#addition)

🥑 [Subtraction -](#subtraction) 

🥑 [Multiplication *](#multiplication) 

🥑 [Division /](#division) 

🥑 [Remainder %](#remainder) 

🥑 [Exponentiation **](#exponentiation)

## 🍄 [String concatenation with binary +](#string-concatenation-with-binary)

## 🍄 [Numeric conversion, unary +](#numeric-conversion-unary)

## 🍄 [Operator precedence](#operator-precedence)

## 🍄 [Assignment](#assignment)

## 🍄 [Modify-in-place](#modify-in-place)

## 🍄 [Increment/decrement](#increment-decrement)

## 🍄 [Bitwise operators](#bitwise-operators)


*****


### _Unary Operators_

Operators that operate on a single operand. These operators require only one operand to perform an operation.

 **For example:**
```javascript 
let num = 5;
num++; // Increment operator (unary)
console.log(num); // Output: 6
```

### _Binary Operators_

Operators that operate on two operands. These operators require two operands to perform an operation.

 **For example:**
```javascript 
let x = 10;
let y = 5;
let sum = x + y; // Addition operator (binary)
console.log(sum); // Output: 15
```

### _Operand Operators_

It's a term used to describe the values or variables on which operators act. Operands can be literals, variables, or expressions.

**For example:**
```javascript 
let a = 5; // '5' is an operand
let b = 3; // '3' is an operand
let result = a + b; // 'a' and 'b' are operands
console.log(result); // Output: 8
```

*****

### _Addition +_

It's the mathematical operation of combining two or more numbers to get a total.

**For example:**
```javascript 
let sum = 5 + 3; // Result: 8
```

### _Subtraction -_

It's the mathematical operation of finding the difference between two numbers.

**For example:**
```javascript 
let difference = 10 - 3; // Result: 7
```

### _Multiplication *_

It's the mathematical operation of combining two or more numbers to get a total.

**For example:**
```javascript 
let product = 4 * 2; // Result: 8
``` 

### _Division /_

It's the mathematical operation of splitting a number into equal parts.

**For example:**
```javascript 
let quotient = 12 / 4; // Result: 3
``` 

### _Remainder %_

It's the amount left over after dividing one number by another.

**For example:**
```javascript 
let remainder = 10 % 3; // Result: 1 (10 divided by 3 leaves a remainder of 1)
``` 

### _Exponentiation **_

It's the mathematical operation of raising a number to a power.

**For example:**
```javascript 
let power = 2 ** 3; // Result: 8 (2 raised to the power of 3)
``` 

## _String concatenation with binary +_

String concatenation using the binary + operator involves joining multiple strings together to create a new string.

**For example:**
```javascript 
let firstName = "lassie";
let lastName = "coder";
let fullName = firstName + " " + lastName; // Concatenating two strings with a space in between
console.log(fullName); // Output: "lassie coder"
``` 

## _Numeric conversion, unary +_

The unary plus (+) operator converts its operand into a number. If the operand is already a number, it remains unchanged. If the operand is not a number, the unary plus converts it into a number.

**For example:**
```javascript 
let x = "42"; // String containing a number
let num = +x; // Unary plus operator for numeric conversion
console.log(num); // Output: 42 (string converted to number)
``` 

It's commonly used when we need to convert strings to numbers, such as when dealing with values from HTML form fields. It's a shorter alternative to using the `Number()` function for conversion.

## _Operator precedence_

It determines the order in which operators are executed in an expression. Higher precedence operators are evaluated first. Parentheses can override precedence. Unary operators have higher precedence than corresponding binary operators.

**For example:**
```javascript 
let result = 1 + 2 * 2; // Multiplication has higher precedence than addition
console.log(result); // Output: 5
``` 

## _Assignment_

Assignment (=) is an operator with low priority (precedence 2). In expressions like x = 2 * 2 + 1, calculations are performed first, and then the result is stored in x.

**For example:**
```javascript 
let x = 2 * 2 + 1;
console.log(x); // Output: 5
``` 

**Assignment = returns a value**
 the assignment operator (=) is an operator that returns a value. When used in an expression, it assigns a value to a variable and then returns that value.

**For example:**
```javascript 
let a = 1;
let b = 2;

let c = 3 - (a = b + 1);

console.log(a); // Output: 3
console.log(c); // Output: 0
``` 

**Chaining assignments**

Chaining assignments in JavaScript allow multiple variables to be assigned the same value in a single line. The value is evaluated from right to left and then assigned to each variable.

**For example:**
```javascript 
let a, b, c;
a = b = c = 2 + 2;
console.log(a); // Output: 4
console.log(b); // Output: 4
console.log(c); // Output: 4
``` 

## _Modify-in-place_

To efficiently update a variable based on its current value, use modify-and-assign operators like `+=` and `*=`.

**For example:**
```javascript 
let n = 2;
n += 5; // n is now 7 (equivalent to n = n + 5)
n *= 2; // n is now 14 (equivalent to n = n * 2)
console.log(n); // Output: 14
``` 

These operators provide a concise way to perform arithmetic operations and assign the result back to the variable in a single step.

## _Increment/decrement_

**Increment Operator `(++)`**

The increment operator `(++)` increases the value of a variable by 1.

It can be used as a postfix operator `(e.g., x++)` where the current value of `x` is returned and then `x` is incremented, or as a prefix operator `(e.g., ++x)` where `x` is first incremented and then its new value is returned.

**For example:**
```javascript 
let x = 5;
x++; // Postfix increment
console.log(x); // Output: 6

let y = 10;
++y; // Prefix increment
console.log(y); // Output: 11
``` 

**Decrement Operator `(--)`**

The decrement operator `(--)` decreases the value of a variable by 1.

It can be used as a postfix operator `(e.g., x--)` where the current value of `x` is returned and then `x` is decremented, or as a prefix operator `(e.g., --x)` where x is first decremented and then its new value is returned.

**For example:**
```javascript 
let a = 8;
a--; // Postfix decrement
console.log(a); // Output: 7

let b = 12;
--b; // Prefix decrement
console.log(b); // Output: 11
``` 

## _Bitwise operators_

It's used to perform operations at the binary level, manipulating the individual bits of a number. There are several bitwise operators available:

**Bitwise AND (&):** Returns a 1 in each bit position where both corresponding bits are 1.

**Bitwise OR (|):** Returns a 1 in each bit position where either corresponding bit is 1.

**Bitwise XOR (^):** Returns a 1 in each bit position where only one of the corresponding bits is 1.

**Bitwise NOT (~):** Inverts the bits of its operand, changing 1s to 0s and 0s to 1s.

**Left Shift (<<):** Shifts the bits of its first operand to the left by the number of places specified by the second operand.

**Sign-propagating Right Shift (>>):** Shifts the bits of its first operand to the right by the number of places specified by the second operand. The sign bit is preserved.

**Zero-fill Right Shift (>>>):** Shifts the bits of its first operand to the right by the number of places specified by the second operand. Zeroes are shifted in from the left.

**For example:**
```javascript 
let a = 5; // Binary: 00000101
let b = 3; // Binary: 00000011

// Bitwise AND (&)
console.log(a & b); // Output: 1 (00000101 & 00000011 = 00000001)

// Bitwise OR (|)
console.log(a | b); // Output: 7 (00000101 | 00000011 = 00000111)

// Bitwise XOR (^)
console.log(a ^ b); // Output: 6 (00000101 ^ 00000011 = 00000110)

// Bitwise NOT (~)
console.log(~a); // Output: -6 (Inverts all bits: 00000101 becomes 11111010)

// Left Shift (<<)
console.log(a << 1); // Output: 10 (00000101 << 1 = 00001010)

// Right Shift (>>)
console.log(a >> 1); // Output: 2 (00000101 >> 1 = 00000010)

// Zero-fill Right Shift (>>>)
console.log(a >>> 1); // Output: 2 (00000101 >>> 1 = 00000010)
``` 
