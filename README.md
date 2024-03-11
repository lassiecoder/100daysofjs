
**Constructors and the "new" operator**

🥑 [Constructor function](#constructor-function) 

🥑 [Constructor mode test: `new.target`](#constructor-mode-test-newtarget)

🥑 [Return from constructors](#return-from-constructors) 

🥑 [Methods in constructor](#methods-in-constructor)

*****

## 🍄 Constructors and the "new" operator

Constructor functions and the `"new"` operator are commonly used to create multiple similar objects, such as users or menu items.

### _Constructor function_

1. Constructor functions start with a capital letter and are intended to be used with the "new" operator.
2. When invoked with "new", a constructor function creates a new empty object and assigns it to "this".
3. The function body then executes to modify "this" by adding properties to it.
4. Finally, the constructed object is returned.
5. This pattern enables the creation of objects with predefined properties and behaviors.

**For example:**
```javascript
function User(name) {
  this.name = name;
  this.isAdmin = false;
}

let user = new User("Jack");

console.log(user.name); // Jack
console.log(user.isAdmin); // false
```

In the above example, behind the scenes, `"new User(...)"` creates an object with properties defined in the constructor function. This allows for easy creation of new objects with similar properties and behaviors.

### _Constructor mode test: `new.target`_

`new.target` indicates if a function was called with the new keyword. If new is used, `new.target` is the function itself.

Otherwise, it's `undefined`. This property helps adjust function behavior based on how it's called.

**For example:**
```javascript
function User(name) {
  if (!new.target) {
    return new User(name);
  }
  this.name = name;
}

let john = User("John");
alert(john.name); // John
```

### _Return from constructors_

Constructors typically don't include a `return` statement.

When a `return` statement is present:
1. If it returns an object, that object is returned instead of the instance created by the constructor.
2. If it returns a primitive value, the return is ignored, and the instance created by the constructor is returned.

**For example:**
```javascript
function BigUser() {
  this.name = "John";
  return { name: "Godzilla" }; // Returns this object
}

console.log(new BigUser().name); // Output: Godzilla

function SmallUser() {
  this.name = "John";
  return; // Returns this
}

console.log(new SmallUser().name); // Output: John
```

### _Methods in constructor_

In constructor functions, we can define methods along with properties to create objects with specific behaviors.

**For example:**
```javascript
function User(name) {
  this.name = name;

  this.sayHi = function() {
    console.log("My name is: " + this.name);
  };
}

let john = new User("John");

john.sayHi(); // Output: My name is: John
```

This method enables encapsulating behavior within objects created using the constructor function.