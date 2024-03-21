
**Exploring Iterables**

## 🍄 Array methods

🥑 [Symbol.iterator](#symboliterator)

🥑 [String is iterable](#string-is-iterable)

🥑 [Calling an iterator explicitly](#calling-an-iterator-explicitly)

🥑 [Iterables and array-likes](#iterables-and-array-likes)

🥑 [Array.from](#Array.from)


*****

### _Symbol.iterator_

JavaScript arrays are iterable, meaning they have a built-in `Symbol.iterator` method that allows them to be iterated over using loops or other constructs

**For example:**

```javascript
const array = [1, 2, 3];
const iterator = array[Symbol.iterator]();
console.log(iterator.next()); // { value: 1, done: false }
console.log(iterator.next()); // { value: 2, done: false }
console.log(iterator.next()); // { value: 3, done: false }
console.log(iterator.next()); // { value: undefined, done: true }
```

### _String is iterable_

Strings in JavaScript are also iterable, meaning they can be looped over character by character using the `Symbol.iterator` method

**For example:**

```javascript
const str = 'hello';
for (let char of str) {
  console.log(char);
}
// Output: h, e, l, l, o
```

### _Calling an iterator explicitly_

You can manually call the `Symbol.iterator` method of an iterable object to obtain an iterator, which can then be used to iterate over the elements

**For example:**

```javascript
const array = [1, 2, 3];
const iterator = array[Symbol.iterator]();
console.log(iterator.next()); // { value: 1, done: false }
```

### _Iterables and array-likes_

In JavaScript, iterables are objects that implement the `Symbol.iterator` method, allowing them to be iterated over

Array-like objects are objects that have indices and a length property but may not have the built-in methods of arrays like `forEach` or `map`

**For example:**

```javascript
// Array-like object
const arrayLike = { 0: 'a', 1: 'b', 2: 'c', length: 3 };
// Iterating over array-like object
for (let item of arrayLike) {
  console.log(item);
}
// Output: a, b, c
```

### _Array.from_

The `Array.from` method creates a new, shallow-copied Array instance from an array-like or iterable object

**For example:**

```javascript
const arrayLike = { 0: 'a', 1: 'b', 2: 'c', length: 3 };
const newArray = Array.from(arrayLike);
console.log(newArray); // Output: ['a', 'b', 'c']
```
