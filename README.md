
**Manipulating Strings**

## 🍄 Manipulating Strings

JavaScript stores textual data as strings, with no distinct type for individual characters. Strings are always encoded in **UTF-16** internally, independent of the page encoding.

🥑 [Quotes](quotes)

🥑 [Special characters](#special-characters)

🥑 [String length](#string-length)

🥑 [Accessing characters](#accessing-characters)

🥑 [Strings are immutable](#strings-are-immutable)

🥑 [Changing the case](#changing-the-case)

🥑 [Searching for a substring](#searching-for-a-substring)

🥑 [Getting a substring](#getting-a-substring)

🥑 [Comparing strings](#comparing-strings)

*****

### _Quotes_

Strings can be defined using single/double quotes or using backticks. All these are equivalent in JavaScript.

1. **Single Quotes (''):**
   Strings can be enclosed within single quotes.

    **For example:**
    ```javascript
    let single = 'single-quoted';
    ```

2. **Double Quotes (""):**
   Similarly, strings can be enclosed within double quotes.
    **For example:**
    ```javascript
    let double = "double-quoted";
    ```

   Both single and double quotes are essentially the same and can be used interchangeably.

3. **Backticks (``):**
   Backticks allow us to create template literals, which are more versatile compared to single and double quotes. They enable us to embed expressions within the string using `${...}` syntax.
    **For example:**
    ```javascript
    let backticks = `backticks`;
    ```

   Additionally, backticks allow strings to span multiple lines, which is not possible with single or double quotes.
    **For example:**
    ```javascript
    let guestList = `Guests:
      * John
      * Pete
      * Mary
    `;

    console.log(guestList); // a list of guests, multiple lines
    ```

### _Special characters_

Special characters *(also known as escape character)* in strings allow for the inclusion of non-visible or hard-to-type characters, such as newline characters denoted by \n, which create line breaks

**For example:**

```javascript
let guestList = "Guests:\n * John\n * Pete\n * Mary";

alert(guestList); // Output: a multiline list of guests
```

Both single and double quotes can be used to create multiline strings with the help of newline characters

**For example:**

```javascript
let str1 = "Hello\nWorld";
let str2 = `Hello
World`;

alert(str1 == str2); // Output: true
```

### _String length_

The `length` property returns the number of characters in the string. It counts each character, including spaces and special characters, as one unit

**For example:**

```javascript
let str = "Hello\nWorld";
console.log(str.length); // Output: 11
```

### _Accessing characters_

Accessing characters in JavaScript strings is done using bracket notation with the index of the character you want to access.

**For example:**

```javascript
let str = "Hello";
console.log(str[0]); // Output: "H"
console.log(str[1]); // Output: "e"
```

You can use positive or negative indices to access characters. Positive indices start from the beginning of the string (0-based), while negative indices start from the end of the string (-1-based).

**For example:**

```javascript
let str = "Hello";
console.log(str[0]); // Output: "H"
console.log(str[-1]); // Output: undefined (negative index)
console.log(str[str.length - 1]); // Output: "o" (last character)
```



### _Strings are immutable_

Strings in JavaScript are immutable, their values cannot be changed once they are created. Attempting to modify a character within a string directly will result in an error

**For example:**

```javascript
let str = 'Hi';
str[0] = 'h'; // Error: Cannot assign to read only property
alert( str[0] ); // Output: "H" (original value remains unchanged)
```

To work around this limitation, you can create a new string with the desired modifications and assign it to the variable instead

**For example:**

```javascript
let str = 'Hi';
str = 'h' + str[1]; // Replace the string with the modified version
alert( str ); // Output: "hi"
```

### _Changing the case_

You can change the case of a string using the methods `toLowerCase()` and `toUpperCase()`

**For example:**

```javascript
alert('Interface'.toUpperCase()); // INTERFACE
alert('Interface'.toLowerCase()); // interface
```

To lowercase a single character, you can access it by index and apply `toLowerCase()`

**For example:**

```javascript
alert('Interface'[0].toLowerCase()); // 'i'
```

### _Searching for a substring_

You can search for substrings within a string using various methods.

1. **indexOf**: The `indexOf` method returns the index of the first occurrence of a specified substring within the string. If the substring is not found, it returns -1.

    **For example:**

    ```javascript
    let str = 'Hello, world!';
    console.log(str.indexOf('world')); // Output: 7
    console.log(str.indexOf('foo'));   // Output: -1
    ```

2. **includes**: The `includes` method checks whether a string contains a specified substring and returns a boolean value (true or false).

    **For example:**

    ```javascript
    let str = 'Hello, world!';
    console.log(str.includes('world')); // Output: true
    console.log(str.includes('foo'));   // Output: false
    ```

3. **startsWith**: The `startsWith` method checks whether a string starts with the specified substring and returns a boolean value.

    **For example:**

    ```javascript
    let str = 'Hello, world!';
    console.log(str.startsWith('Hello')); // Output: true
    console.log(str.startsWith('world')); // Output: false
    ```

4. **endsWith**: The `endsWith` method checks whether a string ends with the specified substring and returns a boolean value.

    **For example:**

    ```javascript
    let str = 'Hello, world!';
    console.log(str.endsWith('world!')); // Output: true
    console.log(str.endsWith('Hello')); // Output: false
    ```

### _Getting a substring_

In JavaScript, you can extract substrings from a string using several methods: `substring`, `substr`, and `slice`

1. **substring(startIndex, endIndex):** It extracts characters from a string between the `startIndex` index (inclusive) and the `endIndex` index (exclusive)

    **For example:**

    ```javascript
    const str = "Hello, world!";
    const sub1 = str.substring(7, 12); // "world"
    const sub2 = str.substring(0, 5);  // "Hello"
    ```

2. **substr(startIndex, length):** This method extracts characters from a string starting at a specified index and takes a length parameter to determine the number of characters to extract

    **For example:**

    ```javascript
    const str = "Hello, world!";
    const sub1 = str.substr(7, 5); // "world"
    const sub2 = str.substr(0, 5);  // "Hello"
    ```

3. **slice(startIndex, endIndex):** It works like `substring`, extracting a string section from `startIndex` to `endIndex` (exclusive)

    **For example:**

    ```javascript
    const str = "Hello, world!";
    const sub1 = str.slice(7, 12); // "world"
    const sub2 = str.slice(0, 5);  // "Hello"
    ```

### _Comparing strings_

You can compare strings using comparison operators like `==`, `!=`, `===`, and `!==`

These operators compare strings based on their Unicode code point values

1. **Lexicographical comparison:** It compares strings character by character, examining their Unicode code points sequentially until a difference is detected or all characters are compared

2. **Case sensitivity:** String comparison is case-sensitive, treating uppercase and lowercase characters as distinct

3. **Comparison operators** like `==` and `!=` perform type conversion before comparing values, while `===` and `!==` do not perform type conversion and strictly compare values and types

**For example:**

```javascript
console.log("apple" < "banana"); // true (lexicographical comparison)
console.log("apple" === "Apple"); // false (case-sensitive comparison)
console.log("5" == 5); // true (loose equality with type conversion)
console.log("5" === 5); // false (strict equality without type conversion)
```
