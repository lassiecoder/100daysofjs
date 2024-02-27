
**Interaction methods: alert, prompt, confirm & Type Conversions**


## Interaction methods

🥑 [alert](#alert) 

🥑 [prompt](#prompt) 

🥑 [confirm](#confirm) 
 

## Type conversions

🥑 [String Conversion](#string-conversion) 

🥑 [Numeric Conversion](#numeric-conversion) 

🥑 [Boolean Conversion](#boolean-conversion) 

*****

### _alert_

The `alert()` method displays a message in a dialog box with an OK button, prompting the user to acknowledge the message.

**For example:**
```javascript                                               
alert("Welcome to my 100 days of JS challenge!");
```

### _prompt_

The `prompt()` method displays a dialog box with a message and an input field, allowing the user to enter data. It returns the text entered by the user, or null if the user clicks Cancel.

**For example:**
```javascript 
let name = prompt("Hello! I'm lassie. What's your name?");
console.log("Hello, " + name + "!");
```

### _confirm_

The `confirm()` method displays a dialog box with a message and OK and Cancel buttons, allowing the user to confirm or cancel an action. It returns true if the user clicks OK and false if the user clicks Cancel.

**For example:**
```javascript 
let result = confirm("Are you sure you want to delete this item?");
if (result) {
  console.log("Item deleted successfully.");
} else {
  console.log("Deletion canceled.");
}
```

We use these interaction methods in JavaScript to provide feedback to users and prompt them for input or confirmation.

*****

## Type conversions

The process of converting values from one data type to another is Type conversion.

### _String Conversion_

String conversion occurs when a value is converted to a string data type. 

**For example:**
```javascript 
let num = 42;
let str = String(num); // Explicit string conversion using String() function
console.log(typeof str); // Output: string
```

### _Numeric Conversion_

Numeric conversion occurs when a value is converted to a numeric data type. This can happen using - `Number()` or `parseInt()`

The `Number()` function converts a value to a numeric data type (integer or floating-point number).

**For example:**
```javascript 
let num1 = Number("42"); // Convert string to number
let num2 = Number("3.14"); // Convert string to number
let num3 = Number(true); // Convert boolean to number (true -> 1, false -> 0)
console.log(num1); // Output: 42
console.log(num2); // Output: 3.14
console.log(num3); // Output: 1
```

 The `parseInt()` function parses a string and returns an integer. It stops parsing when it encounters a non-digit character.

 **For example:**
```javascript 
let num1 = parseInt("42"); // Parse string to integer
let num2 = parseInt("3.14"); // Parse string to integer (decimal part is ignored)
let num3 = parseInt("42px"); // Parse string to integer (non-digit character stops parsing)
console.log(num1); // Output: 42
console.log(num2); // Output: 3
console.log(num3); // Output: 42
```

The `parseFloat()` function in JavaScript is used to parse a string and convert it to a floating-point number (a number with decimal points).

 **For example:**
```javascript 
let priceString = "Price: $24.99"; // String containing a price
let price = parseFloat(priceString); // Extract the floating-point number from the string
console.log(price); // Output: 24.99
```

### _Boolean Conversion_

Boolean conversion occurs when a value is converted to a boolean data type (`true` or `false`). This can happen implicitly in certain contexts, such as in conditional statements (`if`, `while`, etc.), or explicitly using the `Boolean()` function.

 **For example:**
```javascript 
let str = "hello";
let bool = Boolean(str); // Explicit boolean conversion using Boolean() function
console.log(bool); // Output: true (non-empty string is converted to true)
```