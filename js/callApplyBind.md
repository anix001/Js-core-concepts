JavaScript provides three methods for manipulating the this keyword in functions: call(), apply(), and bind(). These methods allow you to change the context of the this keyword, which can be useful for controlling the behaviour of functions. 

## call(); (Call Method)
The **call()** method allows you to call a function with a specified **this** value and arguments provided individually. The first argument to **call()** sets the **this** value for the function being called, and the remaining arguments are passed to the function as arguments.

```
function greet(name) {
  console.log(`Hello, ${name}! My name is ${this.name}.`);
}

let person = {
  name: "John"
};

greet.call(person, "Alice"); // Output: Hello, Alice! My name is John.
```

##apply(); (Apply Method)
The **apply()** method is similar to the **call()** method, but it takes **an array of arguments** instead of **individual arguments**. The first argument to **apply()** sets the **this** value for the function being called, and the second argument is an **array of arguments** to pass to the function.

```
const person = {
  fullName: function(city, country) {
    return this.firstName + " " + this.lastName + "," + city + "," + country;
  }
}

const person1 = {
  firstName:"John",
  lastName: "Doe"
}

person.fullName.apply(person1, ["Oslo", "Norway"]);
```

## bind(); (Bind Method)
The **bind()** method returns a new function with a specified **this** value and any arguments that are passed to it. The **bind()** method does not call the function immediately but instead returns a new function that can be called later.

```
const person = {
  firstName: "John",
  lastName: "Doe",
  fullName: function(city, country) {
    return this.firstName + " " + this.lastName + " from " + city + ", " + country;
  }
};

const member = {
  firstName: "Hege",
  lastName: "Nilsen",
};

// Create a bound function without pre-setting arguments
let boundFullName = person.fullName.bind(member);

console.log(boundFullName("Oslo", "Norway")); // Output: Hege Nilsen from Oslo, Norway
```