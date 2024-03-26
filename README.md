
**Destructuring assignment for efficient coding**

🥑 [Array destructuring](#array-destructuring)

🥑 [Object destructuring](#object-destructuring)

🥑 [Nested destructuring](#nested-destructuring)

🥑 [Smart function parameters](#smart-function-parameters)

*****

**Destructuring assignment** simplifies variable assignment by extracting values from arrays or objects and assigning them to variables, enhancing code readability.

### _Array destructuring_

**Array destructuring** allows you to unpack values from arrays into distinct variables using a syntax that resembles array literals.

```javascript
// Example 1: Basic array destructuring
let numbers = [1, 2, 3];
let [a, b, c] = numbers;
console.log(a); // Output: 1
console.log(b); // Output: 2
console.log(c); // Output: 3

// Example 2: Skipping elements
let [x, , z] = numbers;
console.log(x); // Output: 1
console.log(z); // Output: 3
```

### _Object destructuring_

Object destructuring enables you to extract properties from objects and assign them to variables with the same name.

**For example:**

```javascript
// Example 1: Basic object destructuring
let person = { name: 'John', age: 30 };
let { name, age } = person;
console.log(name); // Output: John
console.log(age); // Output: 30

// Example 2: Renaming variables
let { name: personName, age: personAge } = person;
console.log(personName); // Output: John
console.log(personAge); // Output: 30
```

### _Nested destructuring_

You can also destructure nested arrays and objects.

**For example:**

```javascript
// Example: Nested array destructuring
let nestedArray = [1, [2, 3], 4];
let [first, [second, third], fourth] = nestedArray;
console.log(first); // Output: 1
console.log(second); // Output: 2
console.log(third); // Output: 3
console.log(fourth); // Output: 4

// Example: Nested object destructuring
let nestedObject = { outer: { inner: 'value' } };
let { outer: { inner } } = nestedObject;
console.log(inner); // Output: value
```

### _Smart function parameters_

Destructuring can also be used in function parameters to extract values from objects directly.

**For example:**

```javascript
// Example:
function greet({ name, age }) {
  console.log(`Hello, ${name}! You are ${age} years old.`);
}

let person = { name: 'Alice', age: 25 };
greet(person); // Output: Hello, Alice! You are 25 years old.
```

*****

Destructuring assignment is a concise way to extract values from arrays or objects and assign them to variables.

For objects, the syntax is:

```javascript
let {prop: varName = defaultValue, ...rest} = object;
```

This assigns the value of the property `prop` to the variable `varName`, with an optional default value if the property doesn't exist. Any remaining properties are collected into the `rest` object.

For arrays, the syntax is:

```javascript
let [item1 = defaultValue, item2, ...rest] = array;
```

This assigns the first item to `item1`, the second to `item2`, and collects any remaining items into the `rest` array.

Nested arrays or objects can also be destructured, as long as the structure on the left matches that on the right.