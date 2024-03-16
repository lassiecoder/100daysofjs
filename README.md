
**Working with Numbers**

## 🍄 Numbers

In modern JavaScript, there are two primary types of numbers:

1. **Regular numbers:** These are stored in 64-bit format IEEE-754, commonly known as "double precision floating point numbers".

2. **BigInt numbers:** These represent integers of arbitrary length. They are necessary in situations where regular integer numbers exceed the maximum safe value or fall below the minimum safe value.

🥑 [More ways to write a number](#more-ways-to-write-a-number)

🥑 [toString(base)](#tostringbase)

🥑 [Rounding](#rounding)

🥑 [Imprecise calculations](#imprecise-calculations)

🥑 [Tests: isFinite and isNaN](#tests-isfinite-and-isnan)

🥑 [parseInt and parseFloat](#parseint-and-parsefloat)

🥑 [Other math functions](#other-math-functions)

*****

## _More ways to write a number_

Here are some alternative ways to represent **numbers** in JavaScript:

1. Using underscores as separators:
   
    **For example:**
    
    ```javascript
    let billion = 1_000_000_000;
    ```

   Underscores enhance readability by separating digits, but JavaScript ignores them, making `1_000_000_000` equivalent to `1000000000`

2. Using exponential notation with the letter "e":
   
    **For example:**

    ```javascript
    let billion = 1e9; // 1 billion, equivalent to 1 and 9 zeroes
    alert(7.3e9); // 7.3 billion, same as 7300000000 or 7_300_000_000
    ```

    In the above example, `e` notation multiplies the number by 1 with the specified number of zeroes. For instance, `1e3` equals `1 * 1000`, and `1.23e6` equals `1.23 * 1000000`

3. Representing very small numbers:

    **For example:**
    ```javascript
    let microsecond = 0.000001;
    let microsecond = 1e-6; // five zeroes to the left from 1
    ```

    In the above example, negative number after "e" means division by 1 with the specified number of zeroes. For instance, `1e-3` equals `1 / 1000`, and `1.23e-6` equals `1.23 / 1000000`.

**Hex, binary and octal numbers**

Hexadecimal numbers are represented using the prefix `0x`, binary numbers with `0b`, and octal numbers with `0o`. For example:

**For example:**

```javascript
alert(0xff); // 255
alert(0b11111111); // 255 (binary)
alert(0o377); // 255 (octal)
```

These prefixes provide shorter and more convenient ways to represent numbers in their respective numeral systems.

## _toString(base)_

The method `num.toString(base)` converts the number `num` into a string representation using the specified numeral system base.

**For example:**

```javascript
let num = 255;

alert(num.toString(16)); // ff
alert(num.toString(2)); // 11111111
```

Common use-cases:

- Base 16 (hexadecimal) for colors and character encodings
- Base 2 (binary) for debugging bitwise operations
- Base 36 for representing long identifiers as shorter strings, such as in creating short URLs

## _Rounding_

Number rounding refers to the process of adjusting a numerical value to a specified precision or number of decimal places.

1. `Math.floor()` rounds positive numbers towards zero and negative numbers towards negative infinity, effectively removing any decimal part

**For example:**

```javascript
let num = 3.7;
let roundedDown = Math.floor(num); // 3
```

2. `Math.ceil()` rounds up positive numbers to the nearest integer, moving towards positive infinity, and truncates negative numbers towards zero, removing anything after the decimal point

**For example:**

```javascript
let num = 3.1;
let roundedUp = Math.ceil(num); // 4
```

3. Math.round(): This function rounds a number to the nearest integer. It rounds to the nearest whole number, with halves rounded upwards

**For example:**

```javascript
let num = 3.6;
let rounded = Math.round(num); // 4
```

4. `Math.trunc()` removes the decimal part without rounding, differing from `Math.floor()` by truncating toward zero, including with negative numbers

**For example:**

```javascript
let num = -3.9;
let truncated = Math.trunc(num); // -3
```

5. `toFixed()` This method rounds a number to a specified number of digits after the decimal point and returns a string representation of the result

**For example:**

```javascript
let num = 12.345;
let roundedStr = num.toFixed(2); // "12.35"
```

6. **Multiplication and Division:** To round a number to n decimal places, multiply by 10^n, round, then divide by 10^n

## _Imprecise calculations_

## _Tests: isFinite and isNaN_

## _parseInt and parseFloat_

## _Other math functions_

**For example:**

```javascript

```
