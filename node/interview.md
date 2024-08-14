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

## What are Events, Event Emitter, Event Queue, Event Loop & Event Driven?
1. Event: Signals that something has happened in a program.
2. Event Emitter: Create or emit events.
3. Event Queue: Events emitted queued(stored) in event queue.
4. event Handler(Event listener): Function that responds to specific events.
5. Event Loop: The event loop picks up event from the event queue and executes them in the order they were added.
6. Event Driven Architecture: It means operations in Node are drive or based by events.


## When to use Node js?
1. Ideal for the **real-time applications** like chat applications, online gaming, and collaborative tools due to its event driven architecture.

2. Excellent for building **lightweight and scalable RESTful APIs** that handle a large number of concurrent connections.

3. Well-suited for building **microservices-based architectures**,enabling modular and scalable system.

## when not to use Node.js(disadvantage)

**CPU-Intensive Tasks**: Avoid for application that involve heavy CPU processing(image/video processing, data encryption/Decryption) as Node.js may not provide optimal performance in such scenarios because it is single threaded and for heavy computation multi-threaded is better.


## What is NPM? What is the role of node_modules folder?
1. NPM(Node Package Manager) is used to manage the **dependencies** for your node project.
2. Node_modules folder contains all the dependencies of the node project.

## What is the role of package.json file in Node?
The package.json file contains project metadata(information about the project).For example, project name, version, description, author, license, etc.


## What are Modules in Node? What is the difference between a function & module?
A module constains a **specific functionality** that can be easily resused within a Node.js application. Ideally in node.js, a js file can be treated as a module.

```typescript
//mymodule.js

function sayHello(name){
    console.log("hello" + name);
}

module.exports = sayHello;
```

A module is a broader concept that encapsulates functionality, while a function is a specific set of instructions within that module. Module can contain multiple functions and variables.

If you don't export the module, then the module function will not be available outside the module. In node.js, you can import using the require function.


## What is module wrapper function?
In Node.js each module is wrapped in a function called the **module wrapper function** before it is executed.


```typescript
//app.js
const message = 'Interview';
console.log(message);
```
```typescript
//wrapper function generated by node

function(exports, require, module, __filename, __dirname){
    const message = "Interview"
    console.log(message);
});
```

## What are the Types of modules in Node?
1. Built-in Module(Core Modules): These are already present modules in Node.js which provide essential functionalities. For exanple, fs(file system), http(HTTP server), path(Path manipulation), and uti(utilities).

2. Local Modules: These user-defined modules(js files) created by developers for specific functionalities.

3. Third-Party modules:  These are external package created by the communty and provide additional functionalities or node projects. You install third-party modules using the npm install command. For example, npm install lodash


## What are the Top 5 built in modules commonly used in node projects?
 1. fs
 2. path
 3. os
 4. events
 5. http

 ## Explain the role of s module? Name some function of it?

 ```typescript
 //fs-example.js

 //reading the contents of a file asynchronously // 2nd parameter is format of the file
 fs.readFile("fs.txt","utf-8",(err, data)=>{
    if(err) return;
    console.log("File Contents:", data);
 });

 //writing to a ile asynchronously
 const  contentToWrite = "some content";
 fs.writeFile("fs.txt", contentToWrite, "utf-8", (err)=>{
    if(err){
        return;
    }
    console.log("Write operation complete.");
 })
 ```

 fs(File System) module in Node provides a set of methods for interacting with the file system.

 **7 Main functions of fs module**:
 1. fs.readFile(): Reads the content the file specified
 2. fs.writeFile(): writes data to the specified file, creating the file if it does not exist.
 3. fs.appendFile(): Appends data tp a file. if the file does not exist, it is created.
 4. fs.unlink(): Deletes the specified file.
 5. fs.readdir(): Reads the content of a directory.
 6. fs.mkdir():  creates a new directory.
 7. fs.rmdir(): Removes the specified directory.

 ## Explain the role of path module? Name some function of it?
 path module provides utilities for joining, resolving, parsing, formatting, normalizing and manipulating paths.

 ```typescript
 //path-example.js
 const path = require('/path');

 //joining Path segments
 const fullPath =  path.join('/docs', 'file.txt');
 console.log(fullPath);
 //Output: /docs/file.txt

 //parsing path
 const parsePath = path.parse('/docs/file.txt');
 console.log(parsePath);

 /*Output:
 { roor:'/', dir:'/docs', base:'file.txt', ext:'.txt', name:'file' }

  ```

**5 main functions of path module**

```typescript

const path = require('path');

//joining path segments together
const fullPath = path.join(__dirname, 'folder', 'file.txt');

//resolving the absolute path
const absolutePath = path.resolve('folder','file.txt');

//Getting the directory name of a path
const directoryName = path.dirName('/folder/file.txt');

//Getting the file extension of a path
const fileExtension = path.extname('/folder/file.txt');

//parsing a path into an object with its components
const pathObject = path.parse('/folder/file.txt');
```

## Explain the role of OS module? Name some function of it?
The os module in node.js provide a set of methods for interacting with the operating system.

Operatinf system can be used by developers for building cross-platform applications or performing system-related tasks in Node.js applications.


```typescript
const os = require('os');

//1. get Platform Information
console.log(os.type);
//output: 'Windows_NT' or 'Linux' ....

//2. get Current user information
console.log(os.userInfo());
//output: {uid:-1, gid:-1, username:'anakl',...}

//3. gey memory information in bytes
console.log(os.totalmem()); //output:14877265920
console.log(os.freemem());//output:491570813
```

## Explain the role of events module? How to handle events in Node?
1. Event: Signals that something has happened in a program.
2. Event Emitter: Create or emit events.
3. Event Queue: Events emitted queued(stored) in event queue.
4. event Handler(Event listener): Function that responds to specific events.
5. Event Loop: The event loop picks up event from the event queue and executes them in the order they were added.
6. Event Driven Architecture: It means operations in Node are drive or based by events.

```typescript
const EventEmitter = require('event');

//create an instance if EventEitter class
const myEmitter = new EventEmitter();

//Register an event listener(eventName)
myEmitter.on('eventName', ()=>{
    console.log('Event Occurred');
});


//Emit the event
myEmitter.emit('eventName'); // we need to register the event first and then emit

//output: Event occurred
```

1. events module is used to handle events.
2. EventEmitter class of events module is used to register event listeners and emit events.
3. An event listener is a function that will be executed ehen a particular event occurs.
4. on() method is used to register event listeners.


##  What are Event Arguments?
Event arguments refer to the additional information or data that can be passed along with an emitted event.

```typescript
const EventEmitter = require('event');

//create an instance if EventEitter class
const myEmitter = new EventEmitter();

//Register an event listener(eventName)
myEmitter.on('eventName', (arg1, arg2)=>{
    console.log('Event Occurred:', arg1, arg2);
});

//Emit the event with arguments
myEmitter.emit('eventName', arg1, arg2); // we need to register the event first and then emit

//output: Event occurred: arg1 arg2
```

## What is difference between a function and an event?
A function is a reusable piece of code that performs a specific task when invoked or called.

Events repersent actions that can be observed and responded to. Events will call functions internally.

## What is the role of http module in node?
 The HTTP module can create an HTTP server that listens to serve ports and gives a response back to the client.

 ## What is the role createServer() method of http module?
 The createServer() method of the http module in Node.js ia used to create an HTTP server.

```typescript
//create-server.js

//1. import the http module
const http = require('http');

//2. cretae an Http server using the createserver method
const server = http.createServer((req, res)=>{
    //handle the http request here
    res.enf("Hello World");;
});

//3. Set port on which server will listem incoming request
const port = 3000;

//4. Start the server and listen on the specidied port
server.listen(port,()=>{
    console.log(`Server is runnig on port ${port}`);
});44

//Run command in terminal : node creataeServer.js
```
