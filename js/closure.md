## Closure
closure is a form of lexical scoping used to preserve variable from outer scope of function in the inner scope of a function.

 lexical scoping determines how variable names are resolved in nested functions: inner functions contain the scope of parent functions. Closures allow these inner functions to remember the variables from their containing (lexical) environment.

 ```
 function makeCounter() {
  let count = 0;

  return function() {
    count++;
    return count;
  };
}

const counter = makeCounter();
console.log(counter()); // 1
console.log(counter()); // 2
```