## Q1. What is JS? What is the role of Javascript engine?
Javascript is a programming language that is used for converting static web pages to interactive and dynamic web pages.

A Javascript engine is a program present in web browser that executes js code.

1. v8 for chrome
2. spider-monkey for firefox
3. javascript-Core for safari
4. Chakra for edge



## Variable
 Varibles are something that is used to store the data.

## Data Types
Data types are used to determine the type of variable.
1. primitive: used to hold the single data.(Number, String, Boolean, undefined , null) => Immutable
2. Non-primitive: used to hold the multiple data.(Object, Array, Function, Date, RegExp) =>Mutable

## Operator
Operators are symbols or keywords used to perform operations on operands.
1. Arithmetic Opertor: + ,-,/,*,%,**
2. Assignment Operator: =, +=,*=
3. Comparision operator: >,< ,>=,<=, ==, ===, !==
4. Logical Operator: &&, ||, !
5.String Operator: +(concat)

## Types of conditional Statement
1. If/else
2. Ternanry
3. Switch

## Selectors
Selector in js help to get Specific element from dom based on IDs, classname, tag ,etc.
Example: getElementByID, etc

## DOM
Dom reperesents the web page as tree like structure that allowa js to dynamically access and manipulate the content and structure of a web page.

## Loop
Loop is a programmin way of running a piece of code repeatedly until a certain condition met.
Types: for, while, do-while, for..of, for..in

## Functions
A function is a reusable block of code that performs a specific task.
Named Function, Anonymous function, Function Expression, Arrow Function, IIFE, Callback Function, High-order function

Arrow function is also know as fat arrow function, which is simpler and shorter way for defining functions in js.

## Arrays
Arrays is a data type that allows you to store multiple values in a single variable.

## Objects
Object is a data type that allows you to store key-value pairs.

## Scope
Scope determines where variable are defined and where they can be accessed.

## Asynchronous Programming
Asynchronous programming allows multiple tasks or operations to be initated and executed concurrently.
Asynchronous operations donot bloack the execution of code.

## Null Vs Undefined

When a varible is declared but **has not assigned a value** , is it automatocally initialized with undefined.
Undefined can be used when you don't have the value right now, but you will get it after  some logic or operation.


Null variable are intentionally assigned the null value.
Null can be use, when you are sire you donot have any value for patrticulatr variable.


## typeof Operator
typeof operator is used to determine the typeof each variable.


## type coercion
Type Coercion is the automatic conversion of values from one data type to another during certain operations or comparisions.

```typescript
let a = "42";
let b = 42;
console.log(a+b); //"4242"
``` 

Type coercion is used during **String and number concatenation**.
Type coercion is used while using **Comparision operartors**. 

## Short-circuit evaluation in js
Short circuit evaluation stops the execution as soon as the result can be determined without evaluating the remaining sub-expressions.

```typescript
let result = false && somefunction();
```

## == vs===
Losse Equality(==) operator compares two values for equality after performing type coercion.

Strict Equality(===) operator compares two values without performing type coercion.

## Spread vs Rest
The Spread operator (...) is used to expand or spread elements from an iterable(such as an array, string, or object) into individual elements.

Uses of spread operator : Copying an array, Merging arrays, passing multiple arguments to a function.


The rest operator is used in function parameters to collect all remaining arguments into an array.

```typescript
display(first, second , ...restParameters){
    console.log(first); //1
    console.log(second);//2
    console.log(restParameters); // [3,4,5]
}

display(1,2,3,4,5);
```

## indexOf
**indexOf()** method gets the index of a specified element in the array.

## find() vs filter() vs slice()
find() method get the **first element** that satisfies a condition.
filter() method get **an array of elements** that satisfies a condtion.
Slice() method geta a **subset of the array** from start inde to end(end is optional).

## Push() vs Concat()
Array methods for adding elements.

Push() will **modify the original array** itself.

```typescript
let array1 = [2,3];

array1.push(4,5);
console.log(array1); //[2,3,4,5]
```
Concat() method will create the new array and not modify the original array.

```typescript
let array2 = [1,2];
let array3 = array2.concat(7,8);
console.log(array3); //[1,2,7,8]
console.log(array2); //[1,2]
```

## Pop() vs shift()
Array methods for **removing** elements.
pop() will remove the last element of the array.
Shift() will remove the first element of  the array.

## Splice()
The splice() method is used to **add, remove, or replace** elements in an array.

```typescript
array.splice(startIndex, deleteCount, ...itemsToAdd);
```

## map() vs forEach()
Array methods for modification and iteration.

 The map() method is used when you want to modify element of an array and create a new array with the modified value.


The forEach() method is used when you want to perform some operation on each element of an array  **without creating a new array**.

## Array Destructuring
Array Destructuring allows you to extract elements from an array and assign them to individual variables in a single statement. (ES6) 

```typescript
const fruits = ['apple','banana', 'orange'];
const [a, b,c] = fruits;
```
## array-like objects
 Array like objects are objects that have indexed elements and length property, similar to array, but they may not have all the methods of arrays like push(), pop() & others.


**types of an array like objects**
1. arguments
 ```typescript
 sum (1,2,3);
 //Arguments object
 function sum(){
    console.log(arguments); // [1,2,3]
    console.log(arguemnts.length); //3
    console.log(arguments[0]); //1
 }
```
2. Strings:
 ```typescript
 //string
 const str="hello"
 console.log(str); // hello
 console.log(str.length); //5
 console.log(str[1]);//e
 ```

 3. HTML collections

 ```typescript
 //accessing html collections
 var boxes = document.getElementByClassName('box');
 //Accessing elements in HTML collection using indexes
 console.log(boxes[0]);
 //Accessing length property of html collection
 console.log(boxes.length); 
 ```

## while vs do-while
  While loop executes a block of code while a certain condition is true.

  The do-while loop is similar to  while loop, except that the block of code is **executed at least once**, even if the condition is false.

## break vs continue
The break statement is used to terminate the loop.
The continue statement is used to **skip the current iteration** of the loop and move on to the next iteration.

## for vs for..of
for loop is slightly more complex having more lines of code whereas for...of is much simpler and better for iterating arrays.

```typescript
let arrv=[1,2,3];

//for loop
for(let i=0; i<arr.lrngth; i++){
    console.log(arr[i]);
}

//for...of
for(let val of arr){
    console.log(val)
}
```

## for...of vs for...in

for...of loop is used to loop through the values of an object like arrays, strings. It allows you to access each value directly, without having to use an index.

```typescript
//for...of
for(let val of arr){
    console.log(val)
}
```

for...in loop is used to loop through the properties of an object. It allows you to iterate **over the keys of an object** and access the values associated by using keys as the index.

```typescript
const person={
    name:'Happy',
    role:'Devops'
};

for(let key in person){
    console.log(person[key]);
}
```

## named vs anonymous function

Named functions have a name identifier.

```typescript

//funtion declaration

function sum(a,b){
    return a + b;
};

console.log(add(5,3));
```

Anonymous functions **do not have a name identifier** and cannot be referenced directly by name.

```typescript

//anonymous function

console.log(function(a,b){
 return a*b;
}(4,5));
```


## High order function
A high order function:
1. Take one or more functions as arguments(callback function) OR
2. Return a function as a result

```typescript
//Take one or more functions
//as arguments

function hof(func){
    func();
}

hof(sayHello);

funcion sayHello(){
    console.log("Hello");
}

//output hello
```


## arguments vs parameters

Parameters are the placeholders defined in the function declaration.

```typescript

//a and b are parameters

function add(a, b){
    console.log(a + b)
};
```

Arguments are the actual values passed to a function when it is invoked or called.

```typescript
add(3,4);
```

## default parameters
In js, default parameters allow you to specify default values for function parameters.

```typescript
//function with default parameter value

function greet(name="Happy"){
    console.log("Hello "+ name +"!!");
}

greet();
```


## First-class function
A programming languange is said to have First-class function if function in that language are treated like other variable.

1. Assignable

```typescript
// Assgning function like a variable
const myFunction = function(){
    console.log("hello world");
};

myFunction();
```

2. Passable as Arguments

```typescript
function double(number){
    return number * 2;
}

//passing function as an argument like a variable
function performOperation(double, value){
    return double(value);
}

console.log(performOperation(double, 5)); //10
```

3. Returanable as Values
```typescript
// A function thet returns another function

function a(){
    return function(){
        console.log("a");
    }
};

const b = a();
b();
```

## Currying

Currying in js transforms a function with multiple arguments into a nested series of functions, each taking a single arguments.

```typescript

//without currying
function multiply(a,b){
    retrurn a*b;
}

//curried version 
function currying(a){
    return function(b){
        return a * b;
    }
}
const a = currying(5);
console.log(a(6));
```

## Function Expression

A function expression is a way to define a function by assigning it to a variable.

```typescript
//Anonymous Function Experssion

const add = function(a,b){
    return a + b;
};

console.log(add(5,3)); // 8

//named function expression

const add = function sum(a,b){
    return a + b;
};

console.log(add(5,3)); //8
```


## pure vs impure function

A pure function is a function that is always produce the same output for the same output.

```typescript
function add(a,b){
    return a + b;
}

add(5,3);//8

add(5,3);//8
```
An impure function, can produce diffrent outputs for the same input.

```typescript
let total = 0;
function addToTotal(val){
    total +=val;
    return total;
}

console.log(1); //1
console.log(1); //2
```

## callback function
A callback function is a function that is passed as an argument to another function.

```typescript
 function add(x,y){
    return x +y ;
 }

 function display(x, y, func){
    var result = func(x,y);
    console.log(result);
 }
 display(1,2, add);
 ```

 ## string immutability 
 String in js are considered immutable because you cannot modify the contents of an existing string directly.

 ## finally block
 Finally, block is used to execute some code irrespective of error.

 ## Throw Statement
 The throw statement stops the execution of the current function and passes the error to the catch block of calling function.

 ## Error propagation
 Error propagation refers to the process of passing or propagating an error from one part of code to another by using the throw statement with try catch.

## Array vs Objects
Array are collection of values.
Objects are collection of key-value pairs.

## deep copy vs shallow copy
Shallow copy in nested object case will modify the parent object property value, if cloned object property value is  changed. But deep copy will not modify the parent object property value.

## Set Object 
The set object is a collection of unique values,meaning that duplicate values are not allowed.

```typescript
const a= new Set();
a.add(1);
```

## Map Object
The Map object is a collection of key-value pairs where each key can be any type and each value can also b3 of any type.

```typescript
const a= new Map();
a.set('aa', );
```

## Events
Events are actions that happen in the browsers such as button click, mousemovement, or keyboard input.

## Event Object
Whenever any event is triggred, the browser automatically creates an event object and passed it as an argument to the event handler function.

The event object contains various properties and methods that provide informationa about the event, such as the type of event, the element that triggred the event, etc.

## Event Delegation
Event delegation in js is a technique where you attach a **single event handler to a parent element** to handle events on its **child elements**.

```typescript
<ul id="a">
<li>list 1</li>
<li>list 2</li>
<li>list 3</li>
</ul>

var parentList = doxument.getElementById("a");

//Attach event handler to parent element
parentList.addEventListener("click", handleItemClick);

//Event handler function
function handleItemClick(event){
    var target = event.target;
    console.log("clicked", target.textContent)
}
```

## Event Bubbling

Event bubbling is the process in js where an **event triggres on a child element propagates up the DOM tree**, triggring handlers on its parent elements.

```typescript
<div id="outer">
   <div id="inner">
     <button id="myButton">Click me</button>
   </div>
</div>

//Get the refrence of elements
var outer = document.getElementById("outer");
var inner = document.getElementById("inner");
var button = document.getElementById("myButton");

//Attach event handlers with elements
outer.addEventListerner("click", handleBubbling);
inner.addEventListerner("click", handleBubbling);
button.addEventListerner("click", handleBubbling);

function handleBubbing(event){
    console.log("Bubbling", this.id);
}
```
## Event Capturing
Event Capturing is the process in js where an event is handled starting from the highest-level ancestor(the root of the DOM tree) and **moving down to the target element**.

```typescript
<div id="outer">
   <div id="inner">
     <button id="myButton">Click me</button>
   </div>
</div>

//Get the refrence of elements
var outer = document.getElementById("outer");
var inner = document.getElementById("inner");
var button = document.getElementById("myButton");

//Attach event handlers with elements
outer.addEventListerner("click", handleBubbling, true);
inner.addEventListerner("click", handleBubbling, true);
button.addEventListerner("click", handleBubbling, true);

function handleBubbing(event){
    console.log("Bubbling", this.id);
}
```

## this keyword
 this keyword refers to the element that  the event handler is attached to.

 ```typescript
     <button id="myButton">Click me</button>
     var button = document.getElementById("myButton");
button.addEventListerner("click", handleBubbling);
function handleBubbing(event){
    console.log("Bubbling", this.id);
}
```

## Lexical Scoping
The concept of lexical scoping ensures that variables declared in an outer scope are accessible in nested functions.

```typescript
const a =()=>{
    const b = "aaa";
    func d(){
        console.log(b);
    }
    d();
}
a();
```

## Closure
A closure in js is a **combination of a function and the lexical environment**.

```typescript
function outerFunction(){
    const outerVariable = "Outer scope";

    function innerFunction(){
        console.log(outerVariable);
    }

    return innerFunction;
}

const closure = outerFunction();
```

## Acheiving asynchronous operation in js
1.  setTimeOut
2. setinterval
3. Callbacks
4. Promises
5. Async/await
6. Generators with yield
7. Event-driven programming

## setTimeout()
setTimeout() is a built-in js function that allows you to **schedule the execution of a function** after **a specified delay asynchronously**.


```typescript
console.log("start");

// anonymous function as callback
setTimeout(function(){
 console.log("I am not stopping anything");
},3000);

console.log("Not blocked");


//output
//start
//not blocked
//I am not stopping anything
```

## setInterval
setInterval() is a built-in js function that allows you to **repeatedly a function at a apecified interval asynchronously**.

```typescript
console.log("start");

// anonymous function as callback
setInterval(function(){
 console.log("I am not stopping anything");
},3000); //repeat after every 3 second

console.log("Not blocked");


//output
//start
//not blocked
//I am not stopping anything
//I am not stopping anything
.....
```

## async/await keyword
The async Keyword is used to define a function as an asynchronous function, which means the coe inside async function will not block the execution  of other code.

```typescript
function delay(ms){
 return new promise((resolve)=>
 setTimeout(()=>{
    console.log("Running");
    resolve();
 },ms)
 )
}


async function greet(){
    console.log("Starting....");

    delay(2000); //not block
    console.log("Not Blocked");

    await delay(1000); // Block the code untill complete
    console.log("Blocked");
}

greet();

//Output:
//Starting
//not blocked
//Running (after 1 sec)
//Blocked
//Running (after 2 sec)
```

## Browser APIs in js
Browser APIs(Application programming interfaces) in js are a **collection of built-in interfaces and methods** provided by web browsers.

```typescript
1. DOM API (getElementById, querySelector, createElement, appendChild, addEventistener)
2. XMLHttpRequest(XHR)(open(), send(), setRequestHeader(),onreadyStateChange state)
3. Fetch API(fetch(), then(), json(), and headers.get())
4. storage API(localStorage, sessionStorage)
5. Histpry API(pushState, replaceState, go, back)
6. GeoLocation API(getCurrentPosition, watchPosition, and clearWatch())
7. Notification API(Notification.requestPermission(), new Notification(), notification.onclick())
8. Canvas API(getContext(), fillRect(), drawImage(), beginPath())
9. Audio and video tags(HTMLMediaElement(audio and video elements), play(), pause(), currentTime(), Volume())
```

## web Storage
The Web storage is used to store data locally within browser.
Local Storage, Session Storage


## Local Storage
LocalStorage is a web storage feature provided by web browsers that allows web application to store key-value pairs of data locally on the user's device.

```typescript
//storing data in localStorage
localStorage.setItem('key', 'value');
//Retrive
const val = localStorage.getItem("key");

// remove from localStorage  single item
localStorage.removeItem("key");
//clear all
localStorage.clear();
```


## Cookies
Cookies are small piece of adata taht are stored in the user's web browser.

```typescript
document.cookie= "cookieName1=cookieValue1";
document.cookie= "cookieName2=cookieValue2";

const cookieVal = getCookie("cookieName1");

function getCookie(cookieName){
    const cookies = document.cookie.split(";");
    for(let i=0; i< cookies.length; i++){
      const cookie = cookies[i].split("=");
      if(cookie[0]=== cookieName){
        retrun cookie[1]
      }
    }
    return "";
}
```

## classes in js
Classes serve as  blueprint for creating objects and define their structire and behaviour.

```typescript
class Car {
  constructor(name, year) {
    this.name = name;
    this.year = year;
  }
}

const myCar1 = new Car("Ford", 2014);
const myCar2 = new Car("Audi", 2019);

```

## Constructor
Constructors are special methods within classes that are automatically called when an object is created of the class using the new keyword.

## eval()
eval() is a built-in function that evaluates a string as a js code and dynamicallly executes it.

```typescript
let x = 10;
let y = 20;
let code = "x + y";

let z= eval(code);
console.log(z); //30
```

## XSS(Cross-Site Scripting) attack
Xss is a security attack when a user/hacker insert some malicious script code in input fields to steal or manipulate content.

# SQL Injection attack
SQL Injection is a security attack when a user/hacker insert some malicious SQL script code in input fields to steal or manipulate content.
