
**Handling Arrays & Array methods**

## 🍄 Handling Arrays

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

## 🍄 Array methods

🥑 [Add/remove items](#addremove-items)

🥑 [Iterate: forEach](#iterate-foreach)

🥑 [Searching in array](#searching-in-array)

🥑 [Transform an array](#transform-an-array)

🥑 [Array.isArray](#arrayisarray)

🥑 [Most methods support “thisArg”](#most-methods-support-thisarg)

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

*****

### _Add/remove items_

Arrays in JavaScript offer methods like `push`, `pop`, `shift`, `unshift`, `splice` to add or remove items from the array

**`push`:** Adds one or more elements to the end of an array and returns the new length of the array

**For example:**

```javascript
let array = [1, 2, 3];
array.push(4);
// array is now [1, 2, 3, 4]
```

**`pop`:** Removes the last element from an array and returns that element

**For example:**

```javascript
let array = [1, 2, 3];
let poppedElement = array.pop();
// poppedElement is 3, array is now [1, 2]
```

**`shift`:** Removes the first element from an array and returns that removed element. It also shifts all the subsequent elements to a lower index

**For example:**

```javascript
let array = [1, 2, 3];
let shiftedElement = array.shift();
// shiftedElement is 1, array is now [2, 3]
```

**`unshift`:** Adds one or more elements to the beginning of an array and returns the new length of the array

**For example:**

```javascript
let array = [2, 3];
array.unshift(1);
// array is now [1, 2, 3]
```

**`splice`:** Changes the contents of an array by removing or replacing existing elements and/or adding new elements in place

**For example:**

```javascript
let array = [1, 2, 3, 4, 5];
array.splice(2, 1, 'a', 'b');
// array is now [1, 2, 'a', 'b', 4, 5]
```

### _Iterate: forEach_

The forEach method iterates over each element of the array and executes a provided function for each element

**For example:**

```javascript
let arr = [1, 2, 3, 4];
arr.forEach(item => {
    console.log(item); // Prints each element of the array
});
```

### _Searching in array_

Methods like `indexOf`, `lastIndexOf`, `includes` are used to search for elements in an array

**`indexOf`:** 

- The `indexOf` method returns the first index at which a specified element can be found in the array.
- If the element is not present, it returns -1.
- Syntax: `array.indexOf(element, startIndex)`

    **For example:**

    ```javascript
    const array = [1, 2, 3, 4, 5];
    console.log(array.indexOf(3)); // Output: 2 (index of 3)
    console.log(array.indexOf(6)); // Output: -1 (not found)
    ```

**`lastIndexOf`:**

- The `lastIndexOf` method returns the last index at which a specified element can be found in the array, searching backwards from the end.
- If the element is not present, it returns -1.
- Syntax: `array.lastIndexOf(element, startIndex)`

    **For example:**

    ```javascript
    const array = [1, 2, 3, 4, 3];
    console.log(array.lastIndexOf(3)); // Output: 4 (last index of 3)
    console.log(array.lastIndexOf(6)); // Output: -1 (not found)
    ```

**`includes`:**

- The `includes` method determines whether an array includes a certain element, returning `true` or `false` as appropriate.
- Syntax: `array.includes(element, startIndex)`

    **For example:**

    ```javascript
    const array = [1, 2, 3, 4, 5];
    console.log(array.includes(3)); // Output: true (3 is present)
    console.log(array.includes(6)); // Output: false (6 is not present)
    ```

### _Transform an array_

Array methods like `map`, `filter`, `reduce`, `slice`, `concat` are used to transform arrays in various ways

**`map()`**: This method creates a new array by applying a function to each element of the original array

**For example:**

```javascript
const numbers = [1, 2, 3, 4, 5];
const doubledNumbers = numbers.map(num => num * 2);
// doubledNumbers: [2, 4, 6, 8, 10]
```

**`filter()`**: This method creates a new array with elements that pass a test specified by a provided function.

**For example:**

```javascript
const numbers = [1, 2, 3, 4, 5];
const evenNumbers = numbers.filter(num => num % 2 === 0);
// evenNumbers: [2, 4]
```

**`reduce()`**: This method applies a function against an accumulator and each element in the array (from left to right) to reduce it to a single value.

**For example:**

```javascript
const numbers = [1, 2, 3, 4, 5];
const sum = numbers.reduce((accumulator, currentValue) => accumulator + currentValue, 0);
// sum: 15
```

**`slice()`**: This method returns a shallow copy of a portion of an array into a new array object selected from start to end (end not included) where start and end represent the index of items in that array.

**For example:**

```javascript
const numbers = [1, 2, 3, 4, 5];
const slicedArray = numbers.slice(1, 4);
// slicedArray: [2, 3, 4]
```

**`concat()`**: This method is used to merge two or more arrays. This method does not change the existing arrays, but instead returns a new array.

**For example:**

```javascript
const array1 = [1, 2, 3];
const array2 = [4, 5, 6];
const mergedArray = array1.concat(array2);
// mergedArray: [1, 2, 3, 4, 5, 6]
```

### _Array.isArray_

`Array.isArray` is a static method that checks whether the passed value is an array

**For example:**

```javascript
console.log(Array.isArray([1, 2, 3]));   // Outputs: true
console.log(Array.isArray('Hello'));     // Outputs: false
```

### _Most methods support “thisArg”_

Many array methods have an optional parameter called `thisArg`, which allows you to specify the value of `this` within the callback function

**For example:**

```javascript
let arr = [1, 2, 3];
function logItem(item) {
    console.log(this.prefix + item);
}
arr.forEach(logItem, { prefix: 'Item: ' }); // Outputs: Item: 1, Item: 2, Item: 3
```
