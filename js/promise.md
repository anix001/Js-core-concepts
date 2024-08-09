## Promise
 promise is a object which is used to represent the eventual completion(or failure) of an asynchronous functions and its resulting value.

A Promise is in one of these states:

1. **pending:** initial state, neither fulfilled nor rejected.
2. **fulfilled:** meaning that the operation was completed successfully.
3. **rejected:** meaning that the operation failed.

**How to create a promise in JS**
To create a promise, you need to create an instance object using the Promise constructor function.

```
const promise = new Promise((resolve, reject) => {
  // Condition to resolve or reject the promise
});
```

In promises, resolve is a function with an optional parameter representing the resolved value.
Also, reject is a function with an optional parameter representing the reason why the promise failed.

```
const promise = new Promise((resolve, reject) => {
  const num = Math.random();
  if (num >= 0.5) {
    resolve("Promise is fulfilled!");
  } else {
    reject("Promise failed!");
  }
});

function handleResolve(value) {
  console.log(value);
}

function handleReject(reason) {
  console.error(reason);
}

promise.then(handleResolve, handleReject);
```

It is possible to create an immediately resolved promise, and then attach a callback with the .then() method. You can also create an immediately rejected promise in the same way too.
```
Promise.resolve("Successful").then((result) => console.log(result));
// Successful

Promise.reject("Not successful").then((result) => console.log(result));
// Error: Uncaught (in promise)
```

The error in the rejected promise is because you need to define a separate callback to handle a rejected promise.

```
Promise.reject("Not successful").then(
  () => {
    /*Empty Callback if Promise is fulfilled*/
  },
  (reason) => console.error(reason)
);
// Not Successful
```

**How to Handle Errors in a Promise**
To handle errors in Promises, use the **.catch()** method. If anything goes wrong with any of your promises, this method can catch the reason for that error.
```
Promise.reject(new Error()).catch((reason) => console.error(reason));
// Error
```

**How to Handle Many Promises at Once**
Here are the available methods that can help us achieve this:

1. Promise.all()
2. Promise.race()
3. Promise.any()
4. Promise.allSettled()

1. **The Promise.all() method**
Promise.all() accepts an array of promises as an argument but returns a single promise as the output. The single promise it returns resolves with an array of values if all the promises in the input array are fulfilled.

```
const promise1 = Promise.resolve(`First Promise's Value`);
const promise2 = new Promise((resolve) =>
  setTimeout(resolve, 3000, `Second Promise's Value`)
);
const promise3 = new Promise((resolve) =>
  setTimeout(resolve, 2000, `Third Promise's Value`)
);


Promise.all([promise1, promise2, promise3]).then((values) => {
  values.forEach((value) => console.log(value));
});
```



2. **The Promise.race() method**
Promise.race() accepts an array of promises as an argument and returns a single promise as an output. The single promise it returns is the fastest promise to finish running—resolved or not. This means Promise.race() will return the promise with the shortest execution time in an array of promise.

```
const promise1 = Promise.resolve(`First Promise's Value`);
const promise2 = new Promise((resolve) =>
  setTimeout(resolve, 3000, `Second Promise's Value`)
);
const promise3 = new Promise((resolve) =>
  setTimeout(resolve, 2000, `Third Promise's Value`)
);


Promise.race([promise1, promise2, promise3]).then((value) => {
 console.log(value)
});
```

3. **The Promise.any() method***
Promise.any() accepts an array of Promises as an argument but returns a single Promise as the output. The single promise it returns is the first resolved promise in the input array. This method waits for any promise in the array to be resolved and would immediately return it as the output.

```
const promise1 = new Promise((resolve) =>
  setTimeout(resolve, 3000, `First Promise's Value`)
);
const promise2 = new Promise((resolve) =>
  setTimeout(resolve, 2000, `Second Promise's Value`)
);
const promise3 = Promise.reject(`Third Promise's Value`);

Promise.any([promise1, promise2, promise3]).then(val=> console.log(val));
```

If none of the promises in the array are resolved, Promise.any() returns a rejected promise. This rejected promise contains a JavaScript array of reasons, where each reason corresponds with that of a promise from the input array.

```
const promise1 = new Promise((resolve, reject) =>
  setTimeout(reject, 3000, `First rejection reason`)
);
const promise2 = new Promise((resolve, reject) =>
  setTimeout(reject, 2000, `Second rejection reason`)
);
const promise3 = Promise.reject(`Third rejection reason`);


Promise.any([promise1, promise2, promise3]).catch(({ errors }) =>
  console.log(errors));
```

4. **The Promise.allSettled() method**  [ES2020]
Promise.allSettled() accepts an array of promises as an argument and returns a single promise as the output.

The single promise it returns will always resolve or enter the state ‘fulfilled’ after all the input promises are settled. It does not care if any individual promise in the input array rejected. The array Promise.all() resolves with will contain the resolve values or rejection reasons of promises in the input array.

```
const promise1 = new Promise((resolve) =>
  setTimeout(resolve, 3000, `First Promise's Value`)
);
const promise2 = new Promise((resolve) =>
  setTimeout(resolve, 2000, `Second Promise's Value`)
);
const promise3 = Promise.reject(`Third Promise's Value`);

Promise.allSettled([promise1, promise2, promise3]).then(console.log);
```

**Output**
```
[
  { status: 'fulfilled', value: "First Promise's Value" },
  { status: 'fulfilled', value: "Second Promise's Value" },
  { status: 'rejected', reason: "Third Promise's Value" }
]
```