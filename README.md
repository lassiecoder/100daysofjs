
**Object references and copying**

🥑 [Comparison by reference](#comparison-by-reference) 

🥑 [Cloning and merging, `Object.assign`](#cloning-and-merging-objectassign) 

🥑 [Nested cloning](#nested-cloning) 

*****

## 🍄 Object references and copying

Objects are passed and assigned by reference, not by value. This means that when you work with objects, you're dealing with references to the original object, not copies.

**For example:**
```javascript
// Object reference
let originalObject = { key: 'value' };
let referenceToObject = originalObject;

// Modifying the referenced object
referenceToObject.key = 'new value';

console.log(originalObject.key); // Outputs: 'new value'
```

In the above example, modifying the `referenceToObject` also affects the `originalObject` because they reference the same underlying object.

To create an exact copy of an object, including nested objects, you need to perform a deep copy. Refer to the below example of creating a shallow copy using the spread syntax `(...)`.

**For example:**
```javascript
// Object reference
// Shallow copy using spread syntax
let originalObject = { key: 'value', nested: { innerKey: 'innerValue' } };
let copiedObject = { ...originalObject };

// Modifying the copied object
copiedObject.key = 'new value';
copiedObject.nested.innerKey = 'new inner value';

console.log(originalObject.key); // Outputs: 'value'
console.log(originalObject.nested.innerKey); // Outputs: 'new inner value'
```

In the above example, modifying the `copiedObject` does not affect the `originalObject`. However, note that this is a shallow copy, and if the object contains nested objects, they will still be shared references.

For a deep copy, you may need to use libraries like **Lodash** or implement a custom recursive function to ensure a complete copy of nested structures.

### _Comparison by reference_

It involves checking whether two variables refer to the same object in memory. When comparing objects using equality operators like `==` or `===`, JavaScript checks if the references to the objects are the same, not their contents.

**For example:**
```javascript
// Define an object
let obj1 = {
  name: "John",
  age: 30,
  address: {
    city: "New York",
    country: "USA"
  }
};

// Create a shallow copy of obj1
let obj2 = obj1;

// Create a deep copy of obj1 using the spread syntax
let obj3 = { ...obj1 };

// Modify obj1 and obj2
obj1.name = "Jane";
obj1.address.city = "Los Angeles";

// Output the original and copied objects
console.log("Original Object (obj1):", obj1);
console.log("Shallow Copy (obj2):", obj2);
console.log("Deep Copy (obj3):", obj3);

// Compare object references
console.log("obj1 === obj2:", obj1 === obj2); // true
console.log("obj1 === obj3:", obj1 === obj3); // false

// Compare object contents
console.log("obj1.address === obj2.address:", obj1.address === obj2.address); // true
console.log("obj1.address === obj3.address:", obj1.address === obj3.address); // true
```

In the above example, we have an object `obj1` with nested properties. We create a shallow copy `obj2` and a deep copy `obj3` of `obj1`. After modifying `obj1`, we observe how these changes affect `obj2` and `obj3` then compare the references of the objects as well as the references of their nested properties.

### _Cloning and merging, `Object.assign`_

`Object.assign()` method copies the values of all enumerable properties from one or more source objects to a target object, modifying the target object.

**For example:**
```javascript
// Creating a target object
let target = {};

// Creating source objects
let source1 = { name: 'John' };
let source2 = { age: 30 };

// Merging source objects into the target using Object.assign()
Object.assign(target, source1, source2);

// Output the target object
console.log(target); // { name: 'John', age: 30 }
```

In the above example, `Object.assign()` copies the properties from `source1` and `source2` into the `target` object.

If there are properties with the same name, the value from the later source object overwrites the earlier one.

**NOTE:** `Object.assign()` performs a shallow copy, meaning that nested objects are copied by reference, not cloned. If you need to perform a deep copy, you'll need to implement **custom logic** or use **third-party libraries**.

### _Nested cloning_

**Nested cloning** means making a complete copy of an object along with its nested objects. This is important when you want to change the copied object without altering the original.

**For example:**
```javascript
function deepClone(obj) {
  // Check if obj is an object
  if (typeof obj !== 'object' || obj === null) {
    return obj; // Return the primitive value
  }

  // Create an empty object/array to store the cloned properties
  const clone = Array.isArray(obj) ? [] : {};

  // Iterate over each property of the object
  for (let key in obj) {
    // Check if the property is not inherited
    if (Object.prototype.hasOwnProperty.call(obj, key)) {
      // Recursively clone nested objects
      clone[key] = deepClone(obj[key]);
    }
  }

  return clone; // Return the cloned object
}

// Example object with nested properties
const originalObj = {
  a: 1,
  b: {
    c: 2,
    d: {
      e: 3
    }
  }
};

// Deep clone the object
const clonedObj = deepClone(originalObj);

// Modify the cloned object
clonedObj.b.c = 5;

// Original object remains unchanged
console.log(originalObj); // { a: 1, b: { c: 2, d: { e: 3 } } }
console.log(clonedObj);   // { a: 1, b: { c: 5, d: { e: 3 } } }
```

In the above example, the `deepClone` function recursively iterates over each property of the object and clones nested objects as well. This ensures that the cloned object is completely independent of the original one.