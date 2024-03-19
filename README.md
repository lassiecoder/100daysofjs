
**Handling Arrays & Array methods**

🥑 [Declaration](#declaration)

🥑 [Get last elements with “at”](#get-last-elements-with-at)

🥑 [Methods pop/push, shift/unshift](#methods-pop-push-shift-unshift)

🥑 [Internals](#internals)

🥑 [Performance](#performance)

🥑 [Loops](#loops)

🥑 [A word about “length”](#a-word-about-length)

🥑 [new Array()](#new-array)

🥑 [Multidimensional arrays](#multidimensional-arrays)

🥑 [toString](#tostring)

🥑 [Don’t compare arrays with ==](#dont-compare-arrays-with==)

*****

### _Declaration_

Variables in JavaScript can be declared using the `var`, `let`, or `const` keywords.

**For example:**

```javascript
let x = 10;
```

### _Get last elements with “at”_

JavaScript arrays can be accessed using index notation. To get the last element, you can use negative indices.

**For example:**

```javascript
let arr = [1, 2, 3, 4, 5];
let lastElement = arr[arr.length - 1];
```

### _Methods pop/push, shift/unshift_

Arrays in JavaScript have built-in methods like push, pop, shift, and unshift for adding/removing elements from the beginning or end of an array.

**For example:**

```javascript
let arr = [1, 2, 3];
arr.push(4); // [1, 2, 3, 4]
arr.pop();   // [1, 2, 3]
arr.unshift(0); // [0, 1, 2, 3]
arr.shift();    // [1, 2, 3]
```

### _Internals_

JavaScript handles arrays dynamically, resizing them as needed. Internally, arrays are implemented using objects with numeric keys.

**For example:**

```javascript

```

### _Performance_

JavaScript arrays offer good performance for most operations. However, performance can degrade with large arrays or frequent manipulations.

**For example:**

```javascript

```

### _Loops_

You can iterate over arrays using loops like `for`, `forEach`, `for...of`, or `map`.

**For example:**

```javascript
let arr = [1, 2, 3];
for (let i = 0; i < arr.length; i++) {
    console.log(arr[i]);
}
```

### _A word about “length”_

The length property of an array returns the number of elements in the array.

**For example:**

```javascript
let arr = [1, 2, 3];
console.log(arr.length); // Output: 3
```

### _new Array()_

You can create arrays using the Array constructor.

**For example:**

```javascript
let arr = new Array(3); // Creates an array with length 3
```

### _Multidimensional arrays_

JavaScript supports multidimensional arrays using nested arrays.

**For example:**

```javascript
let arr = [[1, 2], [3, 4]];
```

### _toString_

The `toString` method converts an array to a comma-separated string.

**For example:**

```javascript
let arr = [1, 2, 3];
console.log(arr.toString()); // Output: "1,2,3"
```

### _Don’t compare arrays with ==_

Use caution when comparing arrays with == as it checks for reference equality, not deep equality. Use methods like isEqual from libraries like Lodash for deep comparisons.

**For example:**

```javascript
let arr1 = [1, 2, 3];
let arr2 = [1, 2, 3];
console.log(arr1 == arr2); // Output: false
```

