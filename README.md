
**Understanding Data types and Methods of primitives**

## 🍄 Understanding Data types

🥑 [Primitive Data Types](#primitive-data-types)

🥑 [Composite Data Types](#composite-data-types)

## 🍄 Methods of primitives
 
🥑 [A primitive as an object](#a-primitive-as-an-object)

*****

## _Understanding Data types_

In JavaScript, there are several data types that variables can hold. Here's a brief explanation of each:

### _Primitive Data Types_

1. **Number**: Represents numeric data, including integers and floating-point numbers.
2. **String**: Represents textual data, enclosed in single `('')` or double `("")` quotes.
3. **Boolean**: Represents a logical value, either `true` or `false`.
4. **Undefined**: Represents a variable that has been declared but has not been assigned a value yet.
5. **Null**: Represents the intentional absence of any object value.
6. **Symbol**: Represents a unique and immutable value that may be used as the key of an object property.

### _Composite Data Types_

1. **Object**: Represents a collection of key-value pairs, where values can be of any data type (including other objects).

## _Methods of primitives_

JavaScript allows treating primitives _(like strings, numbers, etc)_ as objects, providing methods to call on them.

A primitive is a value of a primitive type, which includes `string`, `number`, `bigint`, `boolean`, `symbol`, `null`, and `undefined`. On the other hand, an object is capable of storing multiple values as properties and can be created using curly braces `{}`. Additionally, functions in JavaScript are also considered objects.

Objects in JavaScript allow us to store functions as properties

**For example:**

```javascript
let john = {
  name: "John",
  sayHi: function() {
    alert("Hi buddy!");
  }
};

john.sayHi(); // Hi buddy!
```

Built-in objects like **Date**, **Error**, and **HTML elements** already exist, each with their own properties and methods.

### _A primitive as an object_

In JavaScript, although primitives are intended to be lightweight and fast, there's a need to access methods and properties on them like objects. To address this, the language employs a solution where a special "object wrapper" is created temporarily to provide the additional functionality required, and then it is discarded.

Each primitive type in JavaScript, including `String`, `Number`, `Boolean`, `Symbol`, and `BigInt`, has its own corresponding **"object wrapper"** that provides different sets of methods. For example, the string method `toUpperCase()` is used to capitalize a string, as mentioned below:

```javascript
let str = "Hello";

alert( str.toUpperCase() ); // HELLO
```

Referring to the above example; 

When calling `str.toUpperCase()`, here's what happens:

1. Since `str` is a primitive, a special object is temporarily created with access to methods like `toUpperCase()`.
2. The `toUpperCase()` method executes and generates a new string, which is then displayed by the `alert`.
3. After the method call, the special object is discarded, leaving the original primitive `str` unaffected.

Numbers also have their own methods. For example, `toFixed(n)` rounds the number to the specified precision:

**For example:**

```javascript
let n = 1.23456;

alert( n.toFixed(2) ); // 1.23
```
