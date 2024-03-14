
**Object to primitive conversion**

🥑 [Conversion rules](#conversion-rules)

🥑 [Hints](#hints)

🥑 [Symbol.toPrimitive](#symbol-toprimitive)

🥑 [toString/valueOf](#tostring-valueof)

🥑 [Further conversions](#further-conversions)

*****

### _Conversion rules_

In [**Type Conversions**](https://github.com/lassiecoder/100daysofjs/tree/interaction-and-type-conversions), we covered **numeric**, **string**, and **boolean conversions** for primitives, leaving out details for **objects**.

Now, with knowledge of **methods** and **symbols**, we can fill this gap.
Objects are always `true` in boolean contexts. Numeric conversion occurs during subtraction or mathematical operations, while string conversion typically happens when outputting objects.

We can implement custom string and numeric conversions using object methods.

### _Hints_

JavaScript use different type conversion strategies, known as **"hints"**, to handle various situations:

1. **"string"**: Used for object-to-string conversions, such as when performing operations that expect a string result, like **alerting** an object or using it as a property key in another object.

**For example:**

```javascript
alert(obj);
anotherObj[obj] = 123;
```

2. **"number"**: In the case of an object-to-number conversion, which occurs during mathematical operations:

**Explicit Conversion:** You can explicitly convert an object to a number using the `Number()` function.

**For example:**

```javascript
let num = Number(obj);
```

**Mathematical Operations:** Objects can be implicitly converted to numbers in mathematical operations, excluding the binary plus operator.

**For example:**

```javascript
let n = +obj; // Unary plus
let delta = date1 - date2;
let greater = user1 > user2;
```

3. **"default"**: it's is used in situations where the operator is unsure about the expected type
   
    For binary plus (+), which can concatenate strings or add numbers, it uses the "default" hint to convert objects.
    Similarly, comparisons using == with strings, numbers, or symbols also use the "default" hint.

**For example:**

```javascript
// Binary plus uses the "default" hint
let total = obj1 + obj2;

// Comparison with a number uses the "default" hint
if (user == 1) { ... };
```

### _Symbol.toPrimitive_

`Symbol.toPrimitive` is a built-in symbol used to define the conversion method

**For example:**

```javascript
obj[Symbol.toPrimitive] = function(hint) {
  // Conversion logic here
  // Must return a primitive value
};
```

If `Symbol.toPrimitive` method exists, it's used for all conversion hints.

**For example:**

```javascript
let user = {
  name: "John",
  money: 1000,

  [Symbol.toPrimitive](hint) {
    alert(`hint: ${hint}`);
    return hint == "string" ? `{name: "${this.name}"}` : this.money;
  }
};

// Conversions demo:
alert(user);      // hint: string -> {name: "John"}
alert(+user);     // hint: number -> 1000
alert(user + 500); // hint: default -> 1500
```

In the above example, the single `Symbol.toPrimitive` method handles all conversion cases based on the provided hint.

### _toString/valueOf_

If `Symbol.toPrimitive` is not implemented, JavaScript looks for the `toString` and `valueOf` methods as fallbacks.

`toString()` and `valueOf()` are methods used for converting objects to primitive values. These methods are invoked implicitly in various contexts to perform type conversions.

**toString():**
1. The `toString()` method returns a string representing the object
2. It's automatically called when an object is used in a string context, such as concatenation with a string or when passed to functions like `alert()`
3. If `toString()` is not overridden in the object, it returns `"[object Object]"`
 
**For example:**

```javascript
let obj = {
  name: "John",
  age: 30,
  toString() {
    return `${this.name}, ${this.age} years old`;
  }
};

console.log(obj.toString()); // Output: "John, 30 years old"
```

**valueOf():**

1. The `valueOf()` method returns the primitive value of the object.
2. It's automatically called when an object is used in a numeric context, such as arithmetic operations or comparisons
3. If `valueOf()` is not overridden, JavaScript tries to use the object's primitive value by default (e.g., number value if possible)

**For example:**

```javascript
let obj = {
  value: 42,
  valueOf() {
    return this.value;
  }
};

console.log(obj.valueOf()); // Output: 42
```

### _Further conversions_

In operations involving objects, JavaScript undergoes two conversion stages.

1. The object is converted to a primitive using predefined rules
2. If required, the resulting primitive is further converted

**For example:**

```javascript
let obj = {
  toString() {
    return "2";
  }
};

alert(obj * 2); // 4
```

In the above example, the object is first converted to the primitive value **"2"**, then the multiplication operation is performed, resulting in the numeric value **4**.

Likewise, the binary plus operator performs string concatenation.

**For example:**

```javascript
let obj = {
  toString() {
    return "2";
  }
};

alert(obj + 2); // "22"
```

In the above example, the object is converted to the string **"2"**, which is then concatenated with the string **"2"**, resulting in **"22"**.