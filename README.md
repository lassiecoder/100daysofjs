
**Logical operators & Nullish coalescing '??'**


## 🍄 Logical operators

Logical operators in JavaScript are used to perform logical operations on boolean values. 

🥑 [`||` (OR)](#or) 

🥑 [OR `"||"` finds the first truthy value](#finds-the-first-truthy-value) 

🥑 [`&&` (AND)](#&&-and) 

🥑 [AND `“&&”` finds the first falsy value](#and-“&&”-finds-the-first-falsy-value) 

🥑 [`!` (NOT)](#not) 

## 🍄 Nullish coalescing '??'

The nullish coalescing operator `??` is a recent addition to JavaScript. It returns the first defined value of two expressions.

🥑 [Comparison with `"||"`](#comparison-with) 

🥑 [Precedence](#precedence) 

*****

### _|| (OR)_

The logical OR operator `||` returns true if at least one of the operands is truthy.

**For example:**
```javascript
let result = true || false; // true
```

### _OR `||` finds the first truthy value_

The `||` operator returns the first truthy operand it encounters, or the last operand if all are falsy.

**For example:**
```javascript
let result = null || undefined || 0 || 'hello'; // 'hello'
```

### _&& (AND)_

The logical AND operator `&&` returns true only if both operands are truthy.

**For example:**
```javascript
let result = true && false; // false
```

### _AND “&&” finds the first falsy value_

The `&&` operator returns the first falsy operand it encounters, or the last operand if all are truthy.

**For example:**
```javascript
let result = 'hello' && 0 && false; // 0
```

### _! (NOT)_

The logical NOT operator `!` returns the opposite boolean value of its operand.

**For example:**
```javascript
let result = !true; // false
```

## 🍄 Nullish coalescing '??'

It's used to provide a default value when the first value is null or undefined.

**For example:**
```javascript
let user;

alert(user ?? "Anonymous"); // "Anonymous" (user is undefined)

let user = "John";

alert(user ?? "Anonymous"); // "John" (user is defined)
```

It can also be used with a sequence of expressions to select the first defined value from a list.

**For example:**
```javascript
let firstName = null;
let lastName = null;
let nickName = "Supercoder";

alert(firstName ?? lastName ?? nickName ?? "Anonymous"); // "Supercoder"
```

The nullish coalescing operator is a concise way to handle default values in JavaScript, especially when dealing with potentially null or undefined variables.

### _Comparison with ||_

In JavaScript, the OR operator `(||)` can be used similarly to the nullish coalescing operator `(??)`. 

**For example:**

```javascript
let firstName = null;
let lastName = null;
let nickName = "Supercoder";

// Using OR operator to show the first truthy value
alert(firstName || lastName || nickName || "Anonymous"); // Output: Supercoder
```

The key difference between them is that:

- || returns the first truthy value.
- ?? returns the first defined value.

In practice, `||` treats `false`, `0`, an empty string `""` and `null/undefined` as falsy values, returning the second argument if any of these is encountered. However, `??` only returns the second argument if the first one is null or undefined.

**For example:**

```javascript
let height = 0;

alert(height || 100); // Output: 100
alert(height ?? 100); // Output: 0
```

### _Precedence_

The `??` operator in JavaScript has the same precedence as the `||` operator, both equal to 3. This means they are evaluated before `=` and `?`, but after most other operations like `+` and `*`.

**For example:**

```javascript
let height = 0;

alert(height || 100); // Output: 100
alert(height ?? 100); // Output: 0
```

If parentheses are omitted, the higher precedence of `*` could lead to incorrect results:

**For example:**

```javascript
// Without parentheses (not recommended)
let area = height ?? 100 * width ?? 50;

// Works this way (not what we want)
let area = height ?? (100 * width) ?? 50;
```

When using `??` with && or `||`, explicit parentheses are required to avoid syntax errors:

**For example:**

```javascript
// Syntax error without explicit parentheses
let x = 1 && 2 ?? 3;

// Use explicit parentheses to work around it
let x = (1 && 2) ?? 3;

alert(x); // Output: 2
```

This limitation was introduced to prevent programming mistakes when transitioning from `||` to `??`.