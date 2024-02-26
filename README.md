
**Variables & Data types**


## Variables

🥑 [A variable](#a-variable) 

🥑 [A tangible real world comparison](#a-tangible-real-world-comparison)

🥑 [Variable naming](#variable-naming) 

🥑 [Constants](#constants) 
 

## Data types

🥑 [Number](#number) 

🥑 [BigInt](#bigint) 

🥑 [String](#string) 

🥑 [Boolean](#boolean) 

🥑 [The “null” value](#the-null-value)

🥑 [The “undefined” value](#the-undefined-value) 

🥑 [Objects and Symbols](#objects-and-symbols) 


*****

### _A variable_

In JavaScript applications, dealing with information is common. For instance, in an online shop, you'd store details about items and shopping carts. In a chat app, information could involve users, messages, and more. Variables come in handy to store and manage this information.

A **variable** acts like a labeled container where we can store information or data. It's a way to keep track of different things, like **values**, **users**, or any other kind of **data** in our program.

Here are some examples of declaring variables:

```javascript                                                                
// Declaring variables using var (function-scoped)
var name = "John";

// Declaring variables using let (block-scoped)
let age = 30;

// Declaring variables using const (block-scoped, constant value)
const PI = 3.14;

// Declaring multiple variables in a single statement
let firstName = "Alice",
    lastName = "Smith",
    isAdmin = false;

// Declaring variables without initializing them
let city;

// Declaring variables with destructuring assignment
let [x, y] = [10, 20];

// Declaring variables with object destructuring
let {width, height} = {width: 100, height: 200};

// Declaring variables with dynamic property names
let dynamicPropertyName = "color";
let {[dynamicPropertyName]: color} = {color: "blue"};

// Declaring variables with rest parameter syntax
let numbers = [1, 2, 3, 4, 5];
let [first, second, ...rest] = numbers;

// Declaring variables with default values
function greet(name = "Guest") {
  console.log("Hello, " + name + "!");
}
greet(); // Output: Hello, Guest!

// Declaring variables with template literals
let greeting = `Hello, ${name}!`;

// Declaring variables with shorthand property names
let age = 25;
let person = { name, age };

// Declaring variables with computed property names
let propertyName = "prop";
let obj = { [propertyName]: "value" };

// Declaring variables using the class syntax (class declarations)
class Rectangle {
  constructor(width, height) {
    this.width = width;
    this.height = height;
  }
}
```

### _A tangible real world comparison_

Think of a "variable" like a box. Each box has a name on it. Inside the box is some information. For example, if we have a variable called "message" it's like having a box labeled "message" with something like "Hello!" inside (refer to Img. 1 below).

We're free to place any value inside the box, and we're also able to alter it multiple times as needed.

When the value of a variable is changed, the previous data stored in the variable is replaced (refer to Img. 2 below).

Here's an example;

```javascript
let message;

message = 'lassie';

message = 'coder'; // value changed

alert(message); // Output will be "lassiecoder"
```

![a-tangible-real-world-comparison](https://github.com/lassiecoder/100daysofjs/assets/17312616/31054aba-bc01-456d-b098-7667bb9c8de4)

> [!WARNING] 
Declaring a variable twice causes an error, see the below example;

```javascript
let message = "lassie";

// repeated 'let' leads to an error
let message = "coder"; // SyntaxError: 'message' has already been declared
```

### _Variable naming_

JavaScript variable names have two restrictions:

1. They can only consist of letters, digits, and the symbols $ and _.
2. The first character cannot be a digit. 
```javascript
// Camel Case: lowercaseFirstLetter
let userName = "John";

// Pascal Case: UppercaseFirstLetter
let FirstName = "Jane";

// Snake Case: lowercase_with_underscores
let last_name = "Doe";

// Hungarian Notation: TypePrefixName
let strMessage = "Hello";

// Upper Case: ALL_CAPS
const MAX_VALUE = 100;

// Mixed Case: CombiningDifferentCasingStyles
let userEmailID = "john.doe@example.com";

```
In the above example;

- Camel Case: `userName` - starts with a lowercase letter and each subsequent word starts with an uppercase letter.
- Pascal Case: `FirstName` - similar to Camel Case but starts with an uppercase letter.
- Snake Case: `last_name` - words are separated by underscores and all letters are lowercase.
- Hungarian Notation: `strMessage` - includes a prefix indicating the variable's type (`str` for string).
- Upper Case: `MAX_VALUE` - all letters are uppercase, commonly used for constants.
- Mixed Case: `userEmailID` - combines different casing styles, like Camel Case and Snake Case.

> [!CAUTION]
> **Distinguishing between cases:** Variables labeled as "lassie" and "LASSIE" are treated as distinct entities.

> [!CAUTION]
> **Non-Latin characters are permitted but discouraged** - Although feasible, using non-Latin characters, such as Cyrillic or Chinese, is not > recommended. While technically allowed, adhering to an international convention of English variable names is preferable, ensuring readability > across diverse audiences.

> [!WARNING]
> **Reserved terms**
> Certain words are reserved within JavaScript and cannot be used as variable names. For instance, "let," "class," "return," and "function" are reserved terms and would prompt syntax errors if employed as variable names.

> [!WARNING]
> **Assigning without strict mode**
> Historically, variables could be created via assignment without the use of "let" or "var." While this method still functions without "use strict," it's considered poor practice and can lead to errors, especially in strict mode environments.

### _Constants_

To define a constant (unchangeable) variable, employ `const` instead of `let`:

```javascript
const userName = 'lassie';
```

Variables designated with `const` are referred to as "constants". They are immutable and cannot be reassigned. Attempting to do so will result in an error:

```javascript
const userName = 'lassie';
userName = 'coder'; // Error: Cannot reassign the constant!
```

When you have to use any variable which will remain unchanged, you can declare it with `const` 

*****

## Data types

### _Number_

The Number data type represents numeric values, both integer and floating-point numbers.

**For example:**
```javascript
let num = 42; // Integer
let pi = 3.14; // Floating-point
```
### _BigInt_

The BigInt data type represents integers of arbitrary precision.

**For example:**
```javascript
let bigIntNum = 1234567890123456789012345678901234567890n;
```

### _String_
**Definition:** The String data type represents sequences of characters enclosed in single ('') or double ("") quotes.

**For example:**
```javascript
let str = "Hello, world!";
```

### _Boolean_
**Definition:** The Boolean data type represents a logical value indicating true or false.

**For example:**
```javascript
let isTrue = true;
let isFalse = false;
```

### _The “null” value_
**Definition:** The null data type represents the intentional absence of any object value.

**For example:**
```javascript
let absentValue = null;
```

### _The “undefined” value_
**Definition:** The undefined data type represents a variable that has been declared but has not yet been assigned a value.

**For example:**
```javascript
let undefinedValue;
```

### _Objects and Symbols_
**Definition:** The Object data type represents a collection of key-value pairs where keys are strings (or symbols) and values can be any data type, including other objects.

**For example:**
```javascript
let obj = {
  name: "John",
  age: 30
};
let symbol = Symbol("description");
```

These are the main JavaScript data types along with their definitions and code examples.

***Note***

The `typeof` operator enables us to determine the type of data stored in a variable.

1. It's commonly written as `typeof x`, but `typeof(x)` is also acceptable.
2. When applied, it yields a string representation of the data type, such as `"string"`.
3. However, when used with `null`, it incorrectly returns `"object" –` despite null not being an object, this behavior is considered a language error.