
**WeakMap and WeakSet**

🥑 [WeakMap](#weakmap)

🥑 [Use case: additional data](#use-case-additional-data)

🥑 [Use case: caching](#use-case-caching)

🥑 [WeakSet](#weakset)

*****

### _WeakMap_

It stores key/value pairs where keys are weakly referenced, allowing objects as keys without preventing garbage collection if not referenced elsewhere

**For example:**

```javascript
// Creating a WeakMap
const cache = new WeakMap();

// Creating some objects
const obj1 = {};
const obj2 = {};

// Adding data to the WeakMap
cache.set(obj1, "data for obj1");
cache.set(obj2, "data for obj2");

// Retrieving data from the WeakMap
console.log(cache.get(obj1)); // "data for obj1"
console.log(cache.get(obj2)); // "data for obj2"

// Removing data from the WeakMap
cache.delete(obj1);

// Checking if an object exists in the WeakMap
console.log(cache.has(obj1)); // false
```

**WeakMap methods:**

**set(key, value):** Adds a new key/value pair to the WeakMap.
**get(key):** Retrieves the value associated with the specified key.
**has(key):** Checks if the WeakMap contains a specific key.
**delete(key):** Removes the key/value pair associated with the specified key.

**Usecase:**

```javascript
// Creating a WeakMap
const cache = new WeakMap();

// Creating some objects
const obj1 = {};
const obj2 = {};

// Adding data to the WeakMap
cache.set(obj1, "data for obj1");
cache.set(obj2, "data for obj2");

// Retrieving data from the WeakMap
console.log(cache.get(obj1)); // "data for obj1"
console.log(cache.get(obj2)); // "data for obj2"

// Checking if an object exists in the WeakMap
console.log(cache.has(obj1)); // true
console.log(cache.has(obj2)); // true

// Deleting data from the WeakMap
cache.delete(obj1);

// Checking again after deletion
console.log(cache.has(obj1)); // false
console.log(cache.has(obj2)); // true
```

### _Use case: additional data_

WeakMap efficiently associates metadata with objects, allowing garbage collection if no other references exist, optimizing memory usage

**For example:**

```javascript
// Create a WeakMap to store additional data for objects
const metadataMap = new WeakMap();

// Function to associate additional data with an object
function setMetadata(obj, metadata) {
    metadataMap.set(obj, metadata);
}

// Function to retrieve the associated metadata for an object
function getMetadata(obj) {
    return metadataMap.get(obj);
}

// Example objects
const user1 = { id: 1 };
const user2 = { id: 2 };

// Associate metadata with objects
setMetadata(user1, { name: 'John', age: 30 });
setMetadata(user2, { name: 'Alice', age: 25 });

// Retrieve metadata for objects
console.log(getMetadata(user1)); // { name: 'John', age: 30 }
console.log(getMetadata(user2)); // { name: 'Alice', age: 25 }

// Object reference removed, allowing for potential garbage collection
user1 = null;
user2 = null;
```

### _Use case: caching_

Using WeakMap for caching associates cached data with specific objects, enabling garbage collection of unreferenced objects to prevent memory leaks and ensure memory efficiency

WeakMap facilitates caching by associating cached data with input parameters, enabling efficient garbage collection of unused objects

**For example:**

```javascript
const cache = new WeakMap();

function computeExpensiveResult(input) {
    if (cache.has(input)) {
        console.log('Fetching cached result...');
        return cache.get(input);
    }

    console.log('Computing expensive result...');
    const result = /* Perform expensive computation */;
    cache.set(input, result);
    return result;
}

const inputData1 = { id: 1 };
const inputData2 = { id: 2 };

console.log(computeExpensiveResult(inputData1)); // Compute and cache result for inputData1
console.log(computeExpensiveResult(inputData1)); // Fetch cached result for inputData1
console.log(computeExpensiveResult(inputData2)); // Compute and cache result for inputData2
console.log(computeExpensiveResult(inputData2)); // Fetch cached result for inputData2
```

In the above example;

- The function `computeExpensiveResult` computes and caches results for unique input objects
- Cached results are linked to input objects via WeakMap
- Allows input objects to be garbage collected if no longer referenced elsewhere
- Ensures efficient memory usage, particularly in scenarios with potentially stale cached data

### _WeakSet_

WeakSet is a JavaScript collection for storing unique objects without preventing them from being garbage collected when not referenced

It's is handy for storing a collection of unique objects, allowing them to be garbage collected when unused

**For example:**

```javascript
// Creating a new WeakSet
const uniqueObjects = new WeakSet();

// Creating some objects
const obj1 = { name: 'Object 1' };
const obj2 = { name: 'Object 2' };
const obj3 = { name: 'Object 3' };

// Adding objects to the WeakSet
uniqueObjects.add(obj1);
uniqueObjects.add(obj2);
uniqueObjects.add(obj3);

// Adding a duplicate object (will not be added since WeakSet only stores unique objects)
uniqueObjects.add(obj1);

// Checking if objects exist in the WeakSet
console.log(uniqueObjects.has(obj1)); // true
console.log(uniqueObjects.has(obj2)); // true
console.log(uniqueObjects.has(obj3)); // true
console.log(uniqueObjects.has({ name: 'Object 1' })); // false (different object reference)

// Removing an object from the WeakSet
uniqueObjects.delete(obj1);

// Checking again after deletion
console.log(uniqueObjects.has(obj1)); // false
```

In the above example;

- We create a WeakSet named `uniqueObjects` to store unique objects
- Multiple objects are added to the WeakSet
- Verification of object existence is done using the `has` method
- Demonstration of the non-addition of duplicate objects
- Removal of an object via the `delete` method
- Verification of the absence of the deleted object in the WeakSet
