
**Garbage collection**

🥑 [Reachability](#reachability) 

🥑 [Two references](#two-references) 

🥑 [Interlinked objects](#interlinked-objects) 

🥑 [Unreachable island](#unreachable-island)

🥑 [Internal algorithms](#internal-algorithms) 

*****

## 🍄 Garbage collection

It's the automatic process of reclaiming memory occupied by objects that are no longer needed or reachable by the program.

### _Reachability_

Objects are considered reachable if they are directly or indirectly accessible from the global scope or through other reachable objects. If an object has no references pointing to it, it becomes unreachable and eligible for garbage collection.

**For example:**
```javascript
let obj = { value: 42 };
```
As long as `obj` is reachable, it won't be garbage collected. If we reassign `obj`, making it unreachable, it becomes eligible for garbage collection.

```javascript
obj = null; // Now the object { value: 42 } is unreachable
```

### _Two references_

 Two variables can reference the same object, preventing it from being garbage collected as long as at least one of the variables remains reachable.

 **For example:**
```javascript
let obj1 = { value: 42 };
let obj2 = obj1; // obj2 now references the same object as obj1

obj1 = null; // The object is still reachable through obj2
```

### _Interlinked objects_

Objects can reference each other, creating a cycle of references. Even if these objects are no longer reachable from the global scope, they won't be garbage collected because they are still reachable from each other.

**For example:**
```javascript
let objA = {};
let objB = {};

objA.ref = objB;
objB.ref = objA;

objA = null;
objB = null;

// Both objA and objB are unreachable from the global scope,
// but they reference each other, preventing garbage collection
```

### _Unreachable island_

If a group of objects is only reachable from within the group itself, but none of them are reachable from the global scope, they form an unreachable island and are eligible for garbage collection.

**For example:**
```javascript
function createUnreachableIsland() {
  let obj1 = {};
  let obj2 = {};
  obj1.ref = obj2;
  obj2.ref = obj1;
  return [obj1, obj2];
}

// The returned objects are unreachable after the function call
createUnreachableIsland();
```

### _Internal algorithms_

JavaScript engines use complex algorithms like **mark-and-sweep**, **reference counting**, and **generational garbage collection** to decide which objects are still in use and which ones can be cleared from memory. Knowing these inner workings can assist developers in writing code that uses memory more efficiently.

**For example:**
```javascript
// Create a function to generate objects
function generateObjects() {
  let objects = [];
  
  // Generate a large number of objects
  for (let i = 0; i < 10000; i++) {
    objects.push({ id: i });
  }
  
  return objects;
}

// Create some objects
let objects = generateObjects();

// Remove the reference to the objects
objects = null;

// Force garbage collection
if (window.gc) {
  window.gc();
}
```

In the above example;
- First, we made a function called `generateObjects()`. It made lots of objects and put them in a list.
- Then, we ran that function to make a bunch of objects, saving them in a variable called `objects`.
- After that, we got rid of the objects by setting the `objects` variable to `null`, showing we didn't need them anymore.
- Lastly, we tried to clean up by asking the computer to throw away unnecessary stuff using `window.gc()`. This might have made the computer use its built-in system to clean up unused things.