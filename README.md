
**Comparisons & Conditional branching: if, '?'**


## 🍄 Comparisons 

It's used to evaluate whether one value is greater than, less than, equal to, or not equal to another value

🥑 [Boolean comparison](#boolean-comparison) 

🥑 [String comparison](#string-comparison) 

🥑 [Comparison of different types](#comparison-of-different-types) 

## 🍄 Conditional branching: if, '?'

*****

### _Boolean comparison_

The result of all comparison operators in JavaScript is a boolean value:

1. `true` indicates "yes," "correct," or "the truth."
2. `false` indicates "no," "wrong," or "not the truth."

**For example:**
```javascript
console.log(5 > 2);  // true (correct)
console.log(9 == 7); // false (wrong)
console.log(2 != 1); // true (correct)
```

The result of a comparison can be stored in a variable just like any other value:

**For example:**
```javascript
let result = 8 > 3; // Store the result of the comparison
console.log(result); // true
```

### _String comparison_

It follows a lexicographical order, where strings are compared letter-by-letter as in a dictionary.

**For example:**
```javascript
alert( 'Z' > 'A' ); // true
alert( 'Glow' > 'Glee' ); // true
alert( 'Bee' > 'Be' ); // true
```

The algorithm for comparing two strings:

1. Compare the first character of both strings.
2. If the first character from the first string is greater or less than the other string's, then the first string is greater or less than the second, respectively.
3. If both strings' first characters are the same, compare the second characters the same way.
4. Repeat until the end of either string.
5. If both strings end at the same length, then they are equal. Otherwise, the longer string is greater.

### _Comparison of different types_

When comparing values of different types in JavaScript, the values are converted to numbers.

**For example:**
```javascript
alert( '2' > 1 ); // true, string '2' is converted to number 2
alert( '01' == 1 ); // true, string '01' is converted to number 1
```

Boolean values are converted to numeric values, where true becomes 1 and false becomes 0.

**For example:**
```javascript
alert( true == 1 ); // true
alert( false == 0 ); // true
```

An interesting scenario arises where:

1. Two values are equal.
2. One of them evaluates to true as a boolean, while the other evaluates to false.

**For example:**
```javascript
let a = 0;
alert( Boolean(a) ); // false

let b = "0";
alert( Boolean(b) ); // true

alert(a == b); // true!
```

This behavior might seem peculiar, but from JavaScript's perspective, it's a normal outcome. During an equality check, values undergo numeric conversion, while explicit Boolean conversion follows a different set of rules.