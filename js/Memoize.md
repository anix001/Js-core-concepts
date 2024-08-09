## What is Memoization?
Memoization is a smart way to make your functions faster by storing and reusing their past results. In JavaScript, it's like using a memory system: if a function is asked the same question again, it quickly retrieves the answer from its memory instead of recalculating it.

## Memoizing a Synchronous Function
Memoizing a synchronous function is a straightforward process. All you need to do is create a cache object and store the results of the function in it. Then, before calling the function, you can check if the cache contains the result for the given arguments. If it does, you can return the cached value. Otherwise, you can perform the computation and store the result in the cache.

**Understanding the Fibonacci Function, the most common example of memoization**
**before memoization**
```
let functionCalled = 0;
const fibonacci = (n) => {
  if (n <= 1) return 1;
  functionCalled++;
  return fibonacci(n - 1) + fibonacci(n - 2);
};

console.log(fibonacci(10)); // 89
console.log(functionCalled); // 88
```
Now, let's put this into perspective with the Fibonacci function we've created. When we call the fibonacci function with the number 10, it miraculously returns 89. However, what's really surprising is that the function was called a mere 88 times to calculate this result. This number might seem small, but here's where it gets interesting.

If we decide to challenge the Fibonacci function by calling it with the number 20, it reveals a really surprising result – 10,946! This is indeed the 20th number in the Fibonacci sequence. However, here's the catch: the function was called a whopping 10,945 times to reach this result. 

**After memoization**
To tackle this issue, we can implement memoization. Take a look at the modified code below:
```
let functionCalled = 0;
const fibonacci = (n, memo = {}) => {
  if (n in memo) return memo[n];
  if (n <= 1) return 1;
  functionCalled++;
  memo[n] = fibonacci(n - 1, memo) + fibonacci(n - 2, memo);
  return memo[n];
};

console.log(fibonacci(10)); // 89
console.log(functionCalled); // 9
```

Now, with memoization, when we call fibonacci(10), it still returns 89, but the function was only called 9 times. This is a significant improvement over the previous version, especially when dealing with larger numbers. If we call fibonacci(20), the function is called just 19 times. This is a massive improvement over the previous version, where the function was called 10,945 times.


## Memoizing an Async Function
Memoizing an asynchronous function presents unique challenges. Consider this async function simulating an API call:
```
const fakeAPICall = async (userId) => {
  return new Promise((resolve, reject) => {
    setTimeout(() => resolve({ userId, name: "John Doe" }), 100);
  });
};

Promise.all([
    fakeAPICall(1),
    fakeAPICall(1),
    fakeAPICall(1)
]).then(console.log); 
// [{userId: 1, name: 'John Doe'}, ...]
```
Although it works as intended, running this code results in three separate API calls. This is inefficient, why make three API calls when we can make just one and reuse the retrieved data?

Let's dig into a practical example to illustrate this improvement:
```
let cache = {};

const fakeAPICall = async (userId) => {
  if (userId in cache) return Promise.resolve(cache[userId]);

  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const response = { userId, name: "John Doe" };
      cache[userId] = response;
      resolve(response);
    }, 100);
  });
};

Promise.all([
    fakeAPICall(1), 
    fakeAPICall(1), 
    fakeAPICall(1)
]).then(console.log); 
// [{ userId: 1, name: 'John Doe' }, ...]
```
This seems promising; we're successfully caching the data in the global cache variable. The problem persists when we make repeated API calls with the same userId. To demonstrate this issue, let's add a console.log statement within the fakeAPICall function and observe the behavior:

```
let cache = {};

const fakeAPICall = async (userId) => {
  if (userId in cache) return Promise.resolve(cache[userId]);

  console.log("API call made");
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const response = { userId, name: "John Doe" };
      cache[userId] = response;
      resolve(response);
    }, 100);
  });
};

Promise.all([
    fakeAPICall(1), 
    fakeAPICall(1), 
    fakeAPICall(1)
]).then(console.log); 
// [{ userId: 1, name: 'John Doe' }, ...]
```
When we execute this code, we observe that "API call made" is logged three times, which is not the desired outcome. Ideally, we want to perform the API call just once and utilize the cached data for subsequent calls.

**Issue**
Before we dig into the solution, it's essential to understand why this issue arises. When we initiate three parallel API calls, the first call finds the cache empty, prompting it to make an API request to retrieve the data. Since the API call is asynchronous, it takes some time to complete. During this period, the second and third function calls are triggered. As the cache remains empty, these calls also initiate new API requests. Consequently, we witnessed "API call made" being logged three times in the console.

**THE SOLUTION**
The key to resolving this challenge lies in minimizing redundant API calls when we know that the required data is not yet available in the cache. To achieve this, we'll introduce a concept called a **"promise queue."**

**Here's how it works:**

1. When the first API call is initiated, it checks the cache. If the data is not present, the call proceeds to fetch the data as usual.

2. While the initial API call is in progress, any subsequent calls are not discarded. Instead, they are added to a queue of promises, patiently waiting for the data to become available.

3. When the first API call completes and the data is obtained, it resolves not only the original promise but also all the promises in the queue. This ensures that all subsequent calls receive the data they were waiting for.

```
let cache = {};
let promiseQueue = [];
let inProgress = false;

const fakeAPICall = async (userId) => {
  if (userId in cache) return Promise.resolve(cache[userId]);

  if (inProgress) {
    return new Promise((resolve) =>  promiseQueue.push(resolve));
  }

  console.log("API call made");
  inProgress = true;
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const response = { userId, name: "John Doe" };
      cache[userId] = response;
      resolve(response);

      // Process the promise queue
      promiseQueue.forEach((resolve) => resolve(response));

      // Reset the promise queue
      promiseQueue = [];
      inProgress = false;
    }, 100);
  });
};

Promise.all([
    fakeAPICall(1), 
    fakeAPICall(1), 
    fakeAPICall(1)
]).then(console.log); 
// [{ userId: 1, name: 'John Doe' }, ...]
```

When you run this code, you'll notice that the message "API call made" is only logged once. This is precisely the desired outcome. We've effectively minimized the API calls, executing them only once and efficiently utilizing cached data for all subsequent requests.

**Let's break down what's happening in the code for a clearer understanding:**

1. **Initial API Call:** When the first API call is made, it checks whether the cache is empty. Since it is, the API request is triggered to fetch the data. Crucially, before making the API request, we set a variable called inProgress to "true." This serves as a signal to any subsequent function calls that the API request is already in progress.

2. **Queueing Subsequent Calls:** As the second and third function calls come in, we don't reject or resolve them immediately. Instead, we return a promise for each and add the corresponding "resolve" function to a queue known as promiseQueue." This step is critical without explicitly resolving or rejecting a promise, it remains pending, and callers (in this case, the Promise.all` method) await its resolution or rejection.

3. **Resolution of Pending Promises:** Once the first API call is successfully completed and the data is retrieved, we're ready to fulfil all the promises stored in the promiseQueue. This means that all the subsequent calls, which were patiently waiting, receive the same data they were waiting for. Subsequently, we clear the promiseQueue and set the inProgress variable back to "false."
