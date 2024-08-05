Prototypal inheritance is a way for objects in JavaScript to share properties and methods. Instead of classes and instances, JavaScript uses prototypes.

 ## Basic Concepts
**Object Prototype:**

Every JavaScript object has a prototype.
A prototype is also an object.
An object inherits properties and methods from its prototype.

**Prototype Chain:**

If an object doesn't have a property or method, JavaScript looks for it in the object's prototype.
This continues up the chain until it finds the property/method or reaches the end of the chain (usually Object.prototype).

## Example
Let's use an example to explain how prototypal inheritance works:

**Step 1: Create a Prototype Object**
```
const animal = {
  eats: true,
  walk() {
    console.log('Animal walks');
  }
};
```
animal is an object with a property eats and a method walk.

**Step 2: Create Another Object Inheriting from the Prototype**
```
const dog = Object.create(animal);
dog.barks = true;
```
dog is an object created with animal as its prototype.
dog now has access to animal's properties and methods.
dog also has its own property barks.

**Step 3: Access Inherited Properties and Methods**
```
console.log(dog.eats); // true (inherited from animal)
dog.walk(); // "Animal walks" (method inherited from animal)
console.log(dog.barks); // true (own property)
```
dog can access eats and walk from animal.
dog also has its own property barks.


## Constructor Functions and prototype
You can also use constructor functions and the prototype property to set up inheritance.

**Step 1: Constructor Function**
```
function Animal() {
  this.eats = true;
}

Animal.prototype.walk = function() {
  console.log('Animal walks');
};
```

**Step 2: Create an Instance**
```
const dog = new Animal();
dog.barks = true;
```

**Step 3: Access Inherited Properties and Methods**
```
console.log(dog.eats); // true (own property)
dog.walk(); // "Animal walks" (method from prototype)
console.log(dog.barks); // true (own property)
```

## __proto__
__proto__ is a property in JavaScript that points to the prototype of an object. It's a way to access the prototype from which the object inherits properties and methods.