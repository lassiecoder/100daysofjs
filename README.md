
**Optional chaining '?.'**

🥑 [The “non-existing property” problem](#the-non-existing-property-problem) 

🥑 [Optional chaining](#optional-chaining)

🥑 [Short-circuiting](#short-circuiting) 

🥑 [Other variants: ?.(), ?.[]](#other-variants)

*****

## 🍄 Optional chaining '?.'

The optional chaining `?.` provides a safe method for accessing nested object properties, even when intermediate properties may be missing.

### _The “non-existing property” problem_

When accessing nested object properties, errors can occur if intermediate properties are missing.

**For example:**
```javascript
let user = {}; // a user without "address" property
alert(user.address.street); // Error!
```

Referring to the above example, While trying to access properties like `'street'` when `'address'` doesn't exist in an object can cause errors. 

To handle such scenarios gracefully, we often resort to checking for the existence of intermediate properties before accessing nested properties;

**For example:**
```javascript
let user = {}; // user has no address
alert(user.address ? user.address.street ? user.address.street.name : null : null);
```

Now, the repeated use of the conditional operator `(?)` or `&&` operator to check for property existence results in code duplication and decreased readability.

Chaining operator introduced to address this issue.

Optional chaining, we can safely access nested properties without worrying about missing intermediate properties:

**For example:**
```javascript
let user = {}; // user has no address
alert(user.address?.street?.name); // undefined (no error)
```

### _Optional chaining_

The optional chaining operator `?.` stops property evaluation if the value before it is `undefined` or `null`, returning `undefined` in such cases.

**For example:**
```javascript
let user = {}; // user has no address
alert(user?.address?.street); // undefined (no error)
```

Optional chaining also allows accessing properties even if the parent object is null or undefined

**For example:**
```javascript
let user = null;
alert(user?.address); // undefined
alert(user?.address.street); // undefined
```

### _Short-circuiting_

Short-circuiting with optional chaining `(?.)` means that if the left part doesn't exist, the evaluation stops immediately.

**For example:**
```javascript
let user = null;
let x = 0;

user?.sayHi(x++); // Since "user" is null, the sayHi call is skipped and x remains unchanged

alert(x); // Output: 0, as the value of x is not incremented
```

In the above example, the increment operation **(x++)** is not performed because the evaluation short-circuits due to the null value of **"user"**.


### _Other variants: ?.(), ?.[]_

Another variation of optional chaining includes using **?.()** to call a function or **?.[]** to access properties using square brackets.

**For example:**
```javascript
let userAdmin = {
  admin() {
    alert("I am admin");
  }
};

let userGuest = {};

userAdmin.admin?.(); // Output: "I am admin"

userGuest.admin?.(); // No action taken as the method doesn't exist
```

In the above example, the optional chaining `?.()` ensures that if the function exists, it will be executed, but if not, the evaluation stops without causing errors.

Similarly, `?.[]` allows us to access properties using square brackets, providing safe property access even if the object doesn't exist

**For example:**
```javascript
let key = "firstName";

let user1 = {
  firstName: "John"
};

let user2 = null;

alert( user1?.[key] ); // Output: "John"
alert( user2?.[key] ); // Output: undefined
```

We can also use optional chaining with the delete operator for safe property deletion

**For example:**
```javascript
delete user?.details; // Delete user.details if user exists
```