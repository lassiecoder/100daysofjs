
**Loops in JS**

Loops in JavaScript are used to execute a block of code repeatedly until a specified condition is met. 

🥑 [`for` Loop](#for-loop) 

🥑 [`while` Loop](#while-loop) 

🥑 [`do...while` Loop](#do-while-loop) 

🥑 [`for...in` Loop](#for-in-loop) 

🥑 [`for...of` Loop](#for-of-loop) 

🥑 [Nested Loop](#nested-loop) 

🥑 [`break` and `continue` Statements](#break-and-continue-statements)

*****

### _`for` loop_

Executes a block of code a specified number of times.

**For example:**
```javascript
for (let i = 0; i < 5; i++) {
    console.log(i); // Output: 0, 1, 2, 3, 4
}
```

### _`while` Loop_

Repeatedly executes a block of code while a specified condition is true.

**For example:**
```javascript
let i = 0;
while (i < 5) {
    console.log(i); // Output: 0, 1, 2, 3, 4
    i++;
}
```

### _`do...while` Loop_

Similar to while loop, but the block of code is executed at least once, even if the condition is false.

**For example:**
```javascript
let i = 0;
do {
    console.log(i); // Output: 0
    i++;
} while (i < 0);
```

### _`for...in` Loop_

Iterates over the properties of an object.

**For example:**
```javascript
const person = { name: 'John', age: 30, job: 'Developer' };
for (let key in person) {
    console.log(key, person[key]); // Output: name John, age 30, job Developer
}
```

### _`for...of` Loop_

Iterates over the values of an iterable object (arrays, strings, etc.).

**For example:**
```javascript
const colors = ['red', 'green', 'blue'];
for (let color of colors) {
    console.log(color); // Output: red, green, blue
}
```

### _Nested Loop_

Using loops within loops.

**For example:**
```javascript
for (let i = 0; i < 3; i++) {
    for (let j = 0; j < 3; j++) {
        console.log(i, j); // Output: 0 0, 0 1, 0 2, 1 0, 1 1, 1 2, 2 0, 2 1, 2 2
    }
}
```

### _`break` and `continue` Statements_

`break`: Terminates the loop.
`continue`: Skips the current iteration and moves to the next one.

**For example:**
```javascript
for (let i = 0; i < 5; i++) {
    if (i === 3) break;
    console.log(i); // Output: 0, 1, 2
}

for (let i = 0; i < 5; i++) {
    if (i === 2) continue;
    console.log(i); // Output: 0, 1, 3, 4
}
```

