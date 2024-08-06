## What is an event loop in JavaScript ?
JavaScript’s event loop is the core mechanism that enables asynchronous operations. Though single-threaded, it manages tasks efficiently. Imagine it as a queue system: events like user interactions or network requests are added to the queue, and the engine processes them one by one. This allows JavaScript to handle non-blocking tasks without freezing, keeping the application responsive even while waiting for data or other operations.


## What does it mean when we say JavaScript is single-threaded?
Single-threaded means that the main thread where JavaScript code is run, runs in one line at a time manner and there is no possibility of running code in parallel.

**The event loop model in JavaScript works as follows:**

1. **Event Queue:** When asynchronous events occur, such as user interactions (e.g., click events, keyboard input), HTTP responses, timers, or ther asynchronous operations, they are placed into an event queue.

2. **Call Stack:** — The call stack is a data structure that keeps track of the currently executing code. It maintains a record of function calls and their respective contexts (local variables, parameters).
    
3. **Event Loop:** — The event loop continuously monitors the call stack and the event queue. When the call stack is empty (i.e., no code is executing), the event loop takes the first event from the event queue and pushes its corresponding callback function onto the call stack. This process is known as “popping an event off the queue.”

4. **Execution of Callbacks:** — The callback function from the event queue is executed. If the callback itself contains asynchronous code (e.g., an asynchronous API call, a setTimeout), it’s scheduled to run later, and the event loop continues to process other events.

5. **Non-blocking Behavior:** — The event loop ensures that asynchronous operations do not block the main thread, allowing other events to be processed concurrently.

6. **Completion:** - The event loop keeps running as long as there are events in the queue or pending callbacks. When the queue is empty, the event loop will eventually terminate.

**Here’s a simplified example to illustrate the event loop in JavaScript:**
```
console.log('Start');

setTimeout(() => {
  console.log('Timeout callback');
}, 2000);

console.log('End');
```

**In this example, the output will be:**
```
Start
End
Timeout callback
```
The “Start” and “End” are printed first, while the setTimeout function schedules the “Timeout callback” to be executed after a 2-second delay. The event loop enables the non-blocking behavior here, allowing the script to continue executing while waiting for the timeout to complete.
