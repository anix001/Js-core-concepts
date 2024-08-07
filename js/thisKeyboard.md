In JavaScript, the this keyword refers to the context in which a function is executed. It points to the object that is currently calling the function.

1. **Global Context:** When used in the global scope (outside of any function or object), this refers to the global object (window in browsers, or global in Node.js).

```
console.log(this); // In a browser, this logs the window object
```

2. **Object Method:** When this is used inside a method of an object, it refers to the object itself.
```
const person = {
  name: 'Alice',
  greet: function() {
    console.log(this.name); // 'this' refers to the person object
  }
};
person.greet(); // Logs: Alice
```

3. **Constructor Functions:** When used in a constructor function (a function that creates new objects), this refers to the newly created object.
```
function Person(name) {
  this.name = name;
}

const alice = new Person('Alice');
console.log(alice.name); // Logs: Alice
```

4. **Arrow Functions:** Arrow functions do not have their own this. They inherit this from their surrounding lexical context.
```
const person = {
  name: 'Alice',
  greet: function() {
    setTimeout(() => {
      console.log(this.name); // 'this' refers to the person object
    }, 1000);
  }
};
person.greet(); // Logs: Alice after 1 second
```
