## what is node js
it is neither language nor framework. Node/Node.js  is a **runtime environment** executing js code on server side.

## How Node is a runtime on server side? What is V8?
Browsers execute js on the client side, and similarly, node js executes js on the server side.
V8 is a js engine for the js language.

## What is the difference b/w Runtime environment & Framework?
**Runtime Environment**: Primarily focuses on providing the necessary infrastructure for code execution, including services like memory management and i/o operations.

**Framework**: Primarily focuses on simplifying the development process by offering a structured set of tools, libraries, and best practices.

## What is difference bw=etween Node.js and Express?
**Node.js** is a runtime environment that allows the execution of js code server-side.
**Express.js** is a framework built on the top Node.js. It is design to simplify the process of building web applications and APIs by providing web applications and APIs by providing a set of feature like simple routing system, middleware support etc.

## What are the difference b/w Client-Side(browser) & Server-side(Node.js)?
Client-side means that the action takes place on the user's (the client's) computer. Server-side means that the action takes place on a web server.

## What are the 7 main features of node.js?
1. Single Threaded
2. Asynchronous
3. Event-Driven
4. V8 js Engline
5. Cross-Platform
6. NPM(Node Package Manager)
7. Real-Time Capabilities

## What is Single Threaded Programming?
A single-threaded language is one that can execute only one task at a time. The program will execute the tasks in sequence, and each task must complete before the next task starts.

## What is Synchronous Programming?
In a synchronous program, each task is performed one after another, and the program waits for each operation to complete before moving on to the next one.

Synchronous programming focuses on the order of execution in a sequential manner, while single-threaded programming focuses on the single thread.

## Multi therading
Multithreading is a feature in operating systems that allows a program to do several tasks at the same time. 

## What is asynchronous programming
In node js, asynchronous flow can be acheived by its single-threaded, non-blocking, and event-driven architecture.

In Node.js, if there are 4 tasks(Task1, Task2, Task3, Task 4) to be completed for an event. Then below steps will be executed:
1. First, Thread T1 will be created.
2. Thread T1 initiates Task1, but it won't wait for task 1, but it won't wait for task 1 to complete. Instead, T1 proceeds to initiate Task2, then task 3 and task 4(This is asynchronous execution allows T1 to efficiently handle multiple tasks continuously).
3. Whenever Task1 completes,an event is emitted.
4. Thread T1, being event-driven, promptly responds to this event, interrupting its current task and delivering the result of task1.


