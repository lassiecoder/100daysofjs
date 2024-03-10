
**Object methods and "this" keyword**

🥑 [Method examples](#method-examples) 

🥑 [`“this”` in methods](#this-in-methods) 

🥑 [`“this”` is not bound](#this-is-not-bound) 

🥑 [Arrow functions have no `“this”`](#arrow-functions-have-no-this)


*****

## 🍄 Object methods

Objects often represent real-world entities like users or orders. These objects can have methods, which are functions stored as properties. Methods allow objects to perform actions or operations related to their properties.

```javascript
let user = {
  name: "John",
  age: 30,
  greet: function() {
    console.log("Hello, " + this.name + "!");
  }
};

user.greet(); // Output: Hello, John!
```

### _Method examples_

To create a method in JavaScript, you can directly assign a function to an object property.

**For example:**
```javascript
let user = {
  name: "John",
  age: 30,
  sayHi() {
    alert("Hello!");
  }
};

user.sayHi(); // Output: Hello!
```

Alternatively, you can first declare a function and then assign it to the object property

**For example:**
```javascript
let user = {
  // ...
};

function sayHi() {
  alert("Hello!");
}

user.sayHi = sayHi;

user.sayHi(); // Output: Hello!
```

Both approaches achieve the same result: defining a method named `sayHi` for the `user` object.

### _`“this”` in methods_

`"this"` keyword inside an object method refers to the object itself. It allows the method to access the object's properties and methods. 

**For example:**
```javascript
let user = {
  name: "John",
  age: 30,

  sayHi() {
    alert(this.name);
  }
};

user.sayHi(); // Output: John
```

Using `"this"` ensures that the method works with the current object, even if the object is referenced by a different variable. T

### _`“this”` is not bound_

The value of the keyword `this` is determined dynamically at runtime based on how a function is called, rather than being bound to a specific object at the time of definition.

**For example:**
```javascript
function sayHi() {
  console.log(this.message);
}

let user = { message: "Hello, I'm a user" };
let admin = { message: "Greetings, I'm an admin" };

user.sayHi = sayHi;
admin.sayHi = sayHi;

// Calling the function with different contexts
user.sayHi(); // Output: Hello, I'm a user
admin.sayHi(); // Output: Greetings, I'm an admin
```

In the above example;
1. The `sayHi` function is declared without being part of any object.
2. It utilizes `this` to access properties.
3. When invoked as a method of `user` and `admin`, `this` refers to the respective objects.
4. This dynamic behavior of `this` showcases that it's not statically bound.

The above function's behavior varies based on the context in which it is called, demonstrating that `"this"` is not statically bound.

### _Arrow functions have no `“this”`_

Arrow functions do not have their own `"this"` context. Instead, they inherit the `"this"` value from the outer function.

This behavior can be useful when we want to maintain the same `"this"` context as the surrounding code.

**For example:**
```javascript
let user = {
  firstName: "Ilya",
  sayHi() {
    let arrow = () => alert(this.firstName);
    arrow();
  }
};

user.sayHi(); // Output: Ilya
```
