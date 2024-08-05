## Var vs Let Vs Const

**Hoisting is a JavaScript mechanism where variables and function declarations are moved to the top of their scope before code execution.**

**Scope of var**
The scope is global when a var variable is declared outside a function. This means that any variable that is declared with var outside a function block is available for use in the whole window.

var is function scoped when it is declared within a function. This means that it is available and can be accessed only within that function.

```
var tester = "hey hi";
    
    function newFunction() {
        var hello = "hello";
    }
    console.log(hello); // error: hello is not defined
```

**var variables can be re-declared and updated**
```
    var greeter = "hey hi";
    var greeter = "say Hello instead";
```

```
    var greeter = "hey hi";
    greeter = "say Hello instead";
```

**Hoisting of var**
This means that if we do this:

    console.log (greeter);
    var greeter = "say hello"

it is interpreted as this:

    var greeter;
    console.log(greeter); // greeter is undefined
    greeter = "say hello"



**Scope of let**
let is block scoped.
A block is a chunk of code bounded by {}. A block lives in curly braces. Anything within curly braces is a block.
```
let greeting = "say Hi";
   let times = 4;

   if (times > 3) {
        let hello = "say Hello instead";
        console.log(hello);// "say Hello instead"
    }
   console.log(hello) // hello is not defined
```
**let can be updated but not re-declare**
this will work:

    let greeting = "say Hi";
    greeting = "say Hello instead";

this will return an error:

    let greeting = "say Hi";
    let greeting = "say Hello instead"

**Hoisting of let**
Just like  var, let declarations are hoisted to the top. Unlike var which is initialized as undefined, the let keyword is not initialized. So if you try to use a let variable before declaration, you'll get a Reference Error.


**const declarations are block scoped**
Like let declarations, const declarations can only be accessed within the block they were declared.

**const cannot be updated or re-declared**
This means that the value of a variable declared with const remains the same within its scope. It cannot be updated or re-declared. So if we declare a variable with const, we can neither do this:

    const greeting = "say Hi";
    greeting = "say Hello instead";// error: Assignment to constant variable. 
nor this:

    const greeting = "say Hi";
    const greeting = "say Hello instead";// error

This behavior is somehow different when it comes to objects declared with const. While a const object cannot be updated, the properties of this objects can be updated. Therefore, if we declare a const object as this:

    const greeting = {
        message: "say Hi",
        times: 4
    }
while we cannot do this:

    greeting = {
        words: "Hello",
        number: "five"
    } // error:  Assignment to constant variable.
we can do this:

    greeting.message = "say Hello instead";


**Hoisting of const**
Just like let, const declarations are hoisted to the top but are not initialized.