
**Basics of Objects**

🥑 [Literals and properties](#literals-and-properties) 

🥑 [Square brackets](#square-brackets) 

🥑 [Property value shorthand](#property-value-shorthand) 

🥑 [Property names limitations](#property-names-limitations) 

🥑 [Property existence test, `in` operator](#property-existence-test-in-operator)

🥑 [The `for..in` loop](#the-forin-loop) 

*****

## 🍄 Objects

A JavaScript object is a data structure with key-value pairs, representing entities and holding properties to describe characteristics or behavior.

**For example:**
```javascript
let person = {
  name: "John",
  age: 30,
  gender: "male",
  isMarried: false,
  greet: function() {
    console.log("Hello, my name is " + this.name + "!");
  }
};

// Accessing object properties
console.log(person.name); // John
console.log(person.age); // 30

// Modifying object properties
person.age = 35;

// Adding a new property
person.city = "New York";

// Calling a method
person.greet(); // Hello, my name is John!
```

In the above example, the `person` object has properties like `name`, `age`, `gender`, and `isMarried`, as well as a method `greet()` that prints a greeting message using the `name` property. These properties can hold various types of data, including strings, numbers, booleans, and even functions.

### _Literals and properties_

Literals are a notation for representing values directly in the code. Object literals are a specific type of literal used to define objects with properties.

Properties are the key-value pairs that describe the characteristics or attributes of an object.

**For example:**
```javascript
// Object literal with properties
let person = {
  name: "John",    // Property: name with value "John"
  age: 30,         // Property: age with value 30
  isStudent: true  // Property: isStudent with value true
};

// Accessing object properties
console.log(person.name);      // Output: John
console.log(person.age);       // Output: 30
console.log(person.isStudent); // Output: true

// Modifying object properties
person.age = 35;               // Update the value of the age property
person.isStudent = false;      // Update the value of the isStudent property

// Adding a new property
person.city = "New York";      // Add a new property city with value "New York"

// Deleting a property
delete person.isStudent;        // Remove the isStudent property

// Using multiword property names (property name must be quoted)
let car = {
  "model name": "Toyota",       // Multiword property name
  year: 2022
};

// Trailing comma in object literal (optional but helpful for easier modifications)
let book = {
  title: "JavaScript Basics",
  author: "Jane Doe",            // Trailing comma makes it easier to add/remove properties
};
```

In the above example, `person` is an object literal with properties like `name`, `age`, and `isStudent`. We access, modify, add, and delete properties as needed. The use of a trailing comma in the object literal (`book`) makes it convenient to add or remove properties without worrying about syntax errors.

### _Square brackets_

Square brackets ([]) are used for various purposes, including creating arrays, accessing array elements, and defining computed property names in objects.

1. **Creating Arrays:** Square brackets are used to create arrays, which are ordered lists of values.

2. **Accessing Array Elements:** Square brackets are used to access elements within an array by their index. The index starts at 0 for the first element.

3. **Defining Computed Property Names in Objects:** Square brackets can be used to define object properties with dynamic or computed names.

4. **Accessing Object Properties:** Square brackets are also used to access object properties when the property name is stored in a variable.

**For example:**
```javascript
// Creating Arrays
let numbers = [1, 2, 3, 4, 5];
let fruits = ["apple", "orange", "banana"];

// Accessing Array Elements
console.log(numbers[0]); // Output: 1
console.log(fruits[2]);  // Output: banana

// Defining Computed Property Names in Objects
let propertyName = "color";
let car = {
  make: "Toyota",
  [propertyName]: "blue" // Computed property name
};

console.log(car.color); // Output: blue

// Accessing Object Properties
let propertyToAccess = "make";
console.log(car[propertyToAccess]); // Output: Toyota
```

### _Property value shorthand_

Property value shorthand enables concise creation of object literals by automatically assigning variable names as property keys.

**For example:**
```javascript
// Variables representing object properties
let name = "John";
let age = 30;
let gender = "male";

// Object creation using property value shorthand
let person = {
  name,   // Equivalent to name: name
  age,    // Equivalent to age: age
  gender  // Equivalent to gender: gender
};

console.log(person); // Output: { name: 'John', age: 30, gender: 'male' }
```

In the above example, the properties of the person object are set using property value shorthand, where variable names serve as both keys and values. JavaScript assigns the values of the variables directly to the properties with matching names.

### _Property names limitations_

Property names in objects have certain limitations and conventions to follow:

1. **Property names must be strings or symbols:**
   - **String:** Property names are usually strings. They can be any valid string, including empty strings, but they cannot be numbers.
   - **Symbol:** ES6 introduced symbols, which are unique and immutable identifiers often used as property keys in objects.

2. **Reserved words:** You cannot use reserved words (keywords) as property names.

3. **Special characters:** Property names can include special characters like spaces, dashes, and Unicode characters, but they must be enclosed in quotes.

**For example:**
```javascript
// Using reserved words as property names
let person = {
  // Syntax error: cannot use "delete" as a property name
  delete: "John",
  // Valid property name
  age: 30
};

// Using special characters in property names
let car = {
  "model-name": "Toyota",
  "year-of-manufacture": 2020
};

// Accessing properties with special characters
console.log(car["model-name"]); // Toyota
console.log(car["year-of-manufacture"]); // 2020

// Using symbols as property names
const key1 = Symbol("key1");
const key2 = Symbol("key2");

let obj = {
  [key1]: "value1",
  [key2]: "value2"
};

console.log(obj[key1]); // value1
console.log(obj[key2]); // value2
```

In the above example, The first object, `person`, tries to use the reserved word `delete` as a property name, resulting in a syntax error. The second object, `car`, showcases the use of special characters like hyphens in property names. The third object, `obj`, utilizes symbols as property names for unique and private keys.

### _Property existence test, `in` operator_

The `in` operator is used to check if a property exists in an object. It returns `true` if the specified property is found in the object, otherwise it returns `false`.

**For example:**
```javascript
let person = {
  name: "John",
  age: 30,
  gender: "male"
};

// Checking if a property exists
console.log("name" in person); // true
console.log("city" in person); // false
```

In the above example, we have an object `person` with properties like `name`, `age`, and `gender`. We use the `in` operator to check if the properties `"name"` and `"city"` exist in the person object. As a result, `"name" in person` returns `true` because the name property exists, while `"city" in person` returns `false` because the `city` property does not exist.

We can also check if a property exists in an object's prototype chain, by writing;

**For example:**
```javascript
console.log("toString" in person); // true
```

### _The `for..in` loop_

`for...in` loop in JavaScript is used to iterate over the enumerable properties of an object. It allows you to loop through all the properties of an object and perform some action for each property.

**For example:**
```javascript
let person = {
  name: "John",
  age: 30,
  city: "New York"
};

for (let key in person) {
  console.log(key + ": " + person[key]);
}
```

In the above example, the `for...in` loop iterates over each property of the `person` object. For each property, it assigns the property name to the `key` variable, and then it accesses the property value using `person[key]`. The loop prints out each property name along with its corresponding value.

**Output:**
```javascript
name: John
age: 30
city: New York
```

The `for...in` loop iterates over all enumerable properties, including inherited ones. To iterate only over an object's own properties (excluding inherited ones), you can use the `hasOwnProperty()` method within the loop.