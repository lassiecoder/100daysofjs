
**The "switch" statement**

A switch statement is a concise way to compare a value against multiple variants. It replaces multiple if checks and provides a more descriptive way to handle such comparisons.

*****

### _Syntax_

```javascript
switch(x) {
  case 'value1':  
    ...
    [break]

  case 'value2':  
    ...
    [break]

  default:
    ...
    [break]
}
```

Here,
1. The value of `x` is compared with each case value for strict equality.
2. If a match is found, the corresponding code block executes until a `break` statement is encountered.
3. If no match is found, the code block within the `default` case (if present) executes.

**For example:**
```javascript
let a = 2 + 2;

switch (a) {
  case 3:
    alert( 'Too small' );
    break;
  case 4:
    alert( 'Exactly!' );
    break;
  case 5:
    alert( 'Too big' );
    break;
  default:
    alert( "I don't know such values" );
}
```

In the above example, `a` is compared to each case value. Since `a` is 4, the code block associated with `case 4` executes, resulting in an alert displaying "Exactly!"
