
**Object manipulation: keys, values, entries**

🥑 [Object.keys, values, entries](#objectkeys-values-entries)

🥑 [Transforming objects](#transforming-objects)

*****

### _Object.keys, values, entries_

`Object.keys()`, `Object.values()`, and `Object.entries()` methods provide ways to work with objects by extracting their keys, values, and key-value pairs, respectively.

`Object.keys()`: This method returns an array containing the keys of an object.

**For example:**

```javascript
const person = {
  name: 'John',
  age: 30,
  city: 'New York'
};

const keys = Object.keys(person);
console.log(keys); // Output: ['name', 'age', 'city']
```

`Object.values()`: This method returns an array containing the values of an object.

**For example:**

```javascript
const person = {
  name: 'John',
  age: 30,
  city: 'New York'
};

const values = Object.values(person);
console.log(values); // Output: ['John', 30, 'New York']
```

`Object.entries()`: This method returns an array of arrays, where each inner array contains a key-value pair as `[key, value]`.

**For example:**

```javascript
const person = {
  name: 'John',
  age: 30,
  city: 'New York'
};

const entries = Object.entries(person);
console.log(entries); 
// Output: [['name', 'John'], ['age', 30], ['city', 'New York']]
```

The above methods are useful for iterating over object properties, performing operations on keys, values, or entries, and manipulating object data in various ways.

### _Transforming objects_

To transform objects using methods like `map`, `filter`, and others similar to arrays, we can follow the below steps:

1. Use `Object.entries(obj)` to convert the object into an array of key/value pairs.
2. Apply array methods such as `map` to transform these key/value pairs.
3. Finally, use `Object.fromEntries(array)` to convert the transformed array back into an object.

**For example:**

```javascript
let prices = {
  banana: 1,
  orange: 2,
  meat: 4,
};

let doublePrices = Object.fromEntries(
  Object.entries(prices).map(entry => [entry[0], entry[1] * 2])
);

console.log(doublePrices.meat); // Output: 8
```
