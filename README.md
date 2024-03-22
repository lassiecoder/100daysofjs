
**Map and Set data structures**

🥑 [Map](#map)

🥑 [Iteration over Map](#iteration-over-map)

🥑 [Object.entries: Map from Object](#objectentries-map-from-object)

🥑 [Object.fromEntries: Object from Map](#objectfromentries-object-from-map)

🥑 [Set](#set)

🥑 [Iteration over Set](#iteration-over-set)

*****

### _Map_

A Map is a collection of keyed data items, similar to an Object, but with the flexibility to use keys of any type.

Key methods and properties include:

- `new Map()`: Creates a new Map object
- `map.set(key, value)`: Stores a value by its corresponding key
- `map.get(key)`: Retrieves the value associated with the provided key, returning `undefined` if the key doesn't exist
- `map.has(key)`: Checks if a key exists in the map, returning `true` or `false`
- `map.delete(key)`: Removes an element (key/value pair) from the map based on the key
- `map.clear()`: Clears all elements from the map
- `map.size`: Returns the current number of elements in the map

**For example:**

```javascript
let map = new Map();

map.set('1', 'str1');   // string key
map.set(1, 'num1');     // numeric key
map.set(true, 'bool1'); // boolean key

// Maps maintain key types, unlike regular Objects
// So '1' and 1 are considered different keys
alert(map.get(1));      // 'num1'
alert(map.get('1'));    // 'str1'

alert(map.size);        // 3
```

Map allows the use of objects as keys, providing a versatile way to store key-value pairs.

**For example:**

```javascript
let john = { name: "John" };

// Create a map to store the visit counts for each user
let visitsCountMap = new Map();

// Use the 'john' object as the key for the map
visitsCountMap.set(john, 123);

// Retrieve the visit count for 'john'
alert( visitsCountMap.get(john) ); // 123
```

Map allows object keys, unlike plain Objects, where using another object as a key leads to unexpected behavior.

**For example:**

```javascript
let john = { name: "John" };
let ben = { name: "Ben" };

let visitsCountObj = {}; // Create an object

// Attempt to use 'ben' object as a key
visitsCountObj[ben] = 234;

// Attempt to use 'john' object as a key, which replaces the previous key ('ben' object)
visitsCountObj[john] = 123;

// The value stored under the key "[object Object]" reflects the last key-value assignment
alert( visitsCountObj["[object Object]"] ); // 123
```

### _Iteration over Map_

When iterating over a Map, three methods can be used:

- `map.keys()`: Returns an iterable for keys.
- `map.values()`: Returns an iterable for values.
- `map.entries()`: Returns an iterable for entries [key, value], which is used by default in `for..of` loops.

**For example:**

```javascript
let recipeMap = new Map([
  ['cucumber', 500],
  ['tomatoes', 350],
  ['onion',    50]
]);

// Iterate over keys (vegetables)
for (let vegetable of recipeMap.keys()) {
  alert(vegetable); // cucumber, tomatoes, onion
}

// Iterate over values (amounts)
for (let amount of recipeMap.values()) {
  alert(amount); // 500, 350, 50
}

// Iterate over [key, value] entries
for (let entry of recipeMap) { // Same as recipeMap.entries()
  alert(entry); // cucumber,500 (and so on)
}
```

Additionally, Map provides a `forEach` method, similar to Arrays:

**For example:**

```javascript
// Execute the function for each (key, value) pair
recipeMap.forEach((value, key, map) => {
  alert(`${key}: ${value}`); // cucumber: 500, and so on
});
```

### _Object.entries: Map from Object_

When initializing a Map, we can provide an array containing key/value pairs, like so:

```javascript
let map = new Map([
  ['1',  'str1'],
  [1,    'num1'],
  [true, 'bool1']
]);

alert( map.get('1') ); // str1
```

If we have a plain object and want to convert it into a Map, we can utilize the built-in method `Object.entries(obj)`, which returns an array of key/value pairs formatted for use with a Map.

This is how we create a map from an object:

```javascript
let obj = {
  name: "John",
  age: 30
};

let map = new Map(Object.entries(obj));

alert( map.get('name') ); // John
```

In the above example, `Object.entries` returns an array of key/value pairs: `[ ["name","John"], ["age", 30] ]`, which is suitable for initializing a Map.

### _Object.fromEntries: Object from Map_

`Object.fromEntries` is a method that creates an object from an array of [key, value] pairs. This reverse operation of `Object.entries(obj)` is useful when we need to convert data from a Map to a plain object.

**For example:**

```javascript
let map = new Map();
map.set('banana', 1);
map.set('orange', 2);
map.set('meat', 4);

let obj = Object.fromEntries(map); // Convert Map to plain object

// obj = { banana: 1, orange: 2, meat: 4 }

alert(obj.orange); // 2
```

Using `map.entries()` returns an iterable of key/value pairs, which is precisely the format expected by `Object.fromEntries`. Hence, it efficiently converts a Map to a plain object.

### _Set_

A Set is a specialized collection type in JavaScript that stores unique values without associated keys.

- `new Set([iterable])`: Creates a new Set, optionally initializing it with values from an iterable object like an array
- `set.add(value)`: Adds a value to the Set, returning the Set itself
- `set.delete(value)`: Removes a value from the Set, returning true if the value existed before deletion, otherwise false
- `set.has(value)`: Checks if a value exists in the Set, returning true if it does, otherwise false
- `set.clear()`: Removes all values from the Set
- `set.size`: Returns the number of elements in the Set

One notable feature of **Sets** is that they only contain unique values. Repeated attempts to add the same value won't result in duplicates.

**For example:**

```javascript
// Creating a new Set
let set = new Set();

// Adding values to the Set
let john = { name: "John" };
let pete = { name: "Pete" };
let mary = { name: "Mary" };

set.add(john);
set.add(pete);
set.add(mary);

// Adding a duplicate value (john)
set.add(john);

// Checking the size of the Set (should be 3)
console.log("Size of the Set:", set.size); // Output: 3

// Checking if a value exists in the Set
console.log("Does set have John?", set.has(john)); // Output: true
console.log("Does set have Anna?", set.has({ name: "Anna" })); // Output: false

// Deleting a value from the Set
console.log("Deleting Mary:", set.delete(mary)); // Output: true
console.log("Size of the Set after deletion:", set.size); // Output: 2

// Clearing all values from the Set
set.clear();
console.log("Size of the Set after clearing:", set.size); // Output: 0
```

### _Iteration over Set_

We can iterate over a Set using either a `for..of` loop or the `forEach` method:

**For example:**

```javascript
let set = new Set(["oranges", "apples", "bananas"]);

// Using for..of loop
for (let value of set) {
  alert(value);
}

// Using forEach method
set.forEach((value, valueAgain, set) => {
  alert(value);
});
```

The `forEach` method's callback function takes three arguments: **the current value**, **a duplicate of the current value**, **and the target object**, to ensure compatibility with Map.

The same iterator methods available for Map are supported for Sets:

- `set.keys()`: Returns an iterable for values.
- `set.values()`: Same as `set.keys()`.
- `set.entries()`: Returns an iterable for `[value, value]` entries.
