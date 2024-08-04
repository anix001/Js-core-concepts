## pure
 This means that if you call the function with the same arguments multiple times, it will return the same result each time.

 ```
 function add(a, b) {
  return a + b;
}

```
## impure
The output depends on the current value of the counter variable, which changes with each call.

```
let counter = 0;

function increment() {
  counter += 1;
  return counter;
}

```