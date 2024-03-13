
**Symbol type**

🥑 [Symbols](#symbols)

🥑 [“Hidden” properties](#hidden-properties)

🥑 [Global symbols](#global-symbols)

*****

## 🍄 Symbol type

Object property keys in JavaScript can only be of two primitive types: `string` or `symbol`.

If another type, such as number, is used, it is automatically converted to a string. For example, `obj[1]` is equivalent to` obj["1"]`, and `obj[true]` is equivalent to `obj["true"]`.

### _Symbols_

Symbols in JavaScript are unique identifiers that can be created using the `Symbol()` function. They can also be given a description for debugging purposes, but this description does not affect their uniqueness.

**For example:**

```javascript
// Creating a symbol without a description
let id = Symbol();

// Creating a symbol with a description
let id = Symbol("id");
```

Symbols are guaranteed to be unique, even if they have the same description. This means that two symbols with the same description are not equal.

**For example:**

```javascript
// Create symbols with the same description
let symbol1 = Symbol("key");
let symbol2 = Symbol("key");

// Create an object with symbols as properties
let obj = {
  [symbol1]: "value1",
  [symbol2]: "value2"
};

// Accessing properties using symbols
console.log(obj[symbol1]); // Output: value1
console.log(obj[symbol2]); // Output: value2

// Check if symbols are equal
console.log(symbol1 === symbol2); // Output: false

// Get symbol description
console.log(symbol1.description); // Output: key
console.log(symbol2.description); // Output: key

// Get symbol keys of the object
console.log(Object.getOwnPropertySymbols(obj)); // Output: [ Symbol(key), Symbol(key) ]
```

In the above example;

1. Two symbols, `symbol1` and `symbol2`, with the description "key" are created
2. Despite having the same description, they are not equal symbols
3. Both symbols are used as properties in an object, `obj`
4. Both symbols are unique and result in different properties in the object
5. The symbols' descriptions are retrieved, and their equality is checked
6. The symbol keys of the object are obtained

### _“Hidden” properties_

Symbols enable the creation of "hidden" properties within an object, inaccessible to other parts of the code. For instance, consider assigning a unique identifier to a user object

**For example:**

```javascript
let user = {
  name: "John"
};

let id = Symbol("id");

user[id] = 1;

alert( user[id] ); // Accessing the data using the symbol as the key
```

Using `Symbol("id")` instead of a string like `"id"` offers benefits. It ensures safety when adding fields to objects owned by other codebases, preventing accidental access or modification.

**Symbols in an object literal**

To include a symbol as a property in an object literal, we enclose it within square brackets.

**For example:**

```javascript
let id = Symbol("id");

let user = {
  name: "John",
  [id]: 123 // not "id": 123
};
```

This syntax ensures that the value from the variable `id` is used as the key, rather than the string `"id"`.

**Symbols are skipped by for…in**

Symbols are ignored in `for...in` loops and `Object.keys()`, ensuring they remain hidden during iteration. They can still be accessed directly using square brackets.

**For example:**

```javascript
let id = Symbol("id");
let user = {
  name: "John",
  age: 30,
  [id]: 123
};

for (let key in user) alert(key); // Outputs: name, age (no symbols)

// Direct access to symbolic property
alert("Direct: " + user[id]); // Outputs: Direct: 123

// Object.assign copies both string and symbol properties
let clone = Object.assign({}, user);

alert(clone[id]); // Outputs: 123
```

Symbols are excluded from iterations to prevent unintended access, but they are copied when objects are cloned or merged using `Object.assign()`.

### _Global symbols_

Global symbols are symbols stored in a global registry, ensuring that symbols with the same description are the same entity.

To create a symbol in this registry, you can use the `Symbol.for(key)` method. If a symbol with the specified key exists, it is returned; otherwise, a new symbol is created and stored in the registry under the given key.

**For example:**

```javascript
// Access or create a symbol in the global registry
let id = Symbol.for("id"); // If the symbol doesn't exist, it's created

// Access the symbol again (potentially from another part of the code)
let idAgain = Symbol.for("id");

// The same symbol is returned from the registry
alert(id === idAgain); // true
```

**Symbol.keyFor**

`Symbol.keyFor` retrieves the name of a global symbol using the symbol itself, utilizing the global symbol registry. For non-global symbols, it returns undefined.

**For example:**

```javascript
let sym = Symbol.for("name");
let sym2 = Symbol.for("id");

alert( Symbol.keyFor(sym) ); // name
alert( Symbol.keyFor(sym2) ); // id
```

All symbols include a `description` property containing the description provided during creation.

**For example:**

```javascript
let globalSymbol = Symbol.for("name");
let localSymbol = Symbol("name");

alert( Symbol.keyFor(globalSymbol) ); // name (global symbol)
alert( Symbol.keyFor(localSymbol) ); // undefined (not global)

alert( localSymbol.description ); // name
```
