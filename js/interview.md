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