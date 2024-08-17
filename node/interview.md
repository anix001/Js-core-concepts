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
 The createServer() method of the http module in Node.js is used to create an HTTP server.

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


# Chapter-2

## What are the advantage of using Express.js with Node.js?

1. **Simplified Web Development**: Express.js  provides a lightweight framework that simplifies the process of building web applications in Node.js.

2.**Middleware Support**: Easy integration of middleware functions into applications's request-response cycle.

3. **Flexible Routing System**: Defining routes for  handling different Http methods(GET, POST, PUT, DELETE, etc.)and URL patterns is easy.

4. **Template Engine Integration**: Express.js supports various template engines making it easy to generate dyanamic HTML content on the server side.

## How to create an HTTP server using Express.js?

```typescript
const express = require('express');

const app = express(); //create an express app

const port = 3000;

app.listen(port,()=>{
    console.log(`Server is started in port ${port}`);
});
```

## What is Middleware in Express.js and When to use them?
A middleware in Express.js is a function that handles HTTP requests, performs operations, and passes control to next middleware.

## How do you implement middlware in Express.js?
```typescript
const express  = require("express");
const app = express();

//define middleware
const myMiddleware = (req, res, next)=>{
    //middleware logic goes here
    res.send("Interview Happy");
    next();//calls the next middleware function(callback function)
};

//use middleware globally for all routes
app.use(middleware); //Use app.use() to mount myMiddleware glbally, meaning it will be executing for every incoming request to the application.
const port = 3000;

app.listen(port,()=>{
    console.log(`Server is started in port ${port}`);
});
```


## What is the purpose of the app.use() function in Express.js?
The app.use() method is used to **execute(mount) middleware** functions globally.

## What is the purpose of the next parameter in express.js?
The next parameter is a callback function which is used to **pass control to the next middleware function** in the stack.

## How to use middleware globally in a specific route?
Use **app.use('/specificRoute', mymiddleware)** to use middleware globally for a specific route in express.js .

## What is Request pipeline in Express?
The request pipeline in Express.js  is a series of middleware functions that handle incoming HTTP requests and pass control to the next function.

# chapter- Types of middleware

## What are the types of middleware's in express.js?
1. Application-Level middleware
2. Router-level middleware
3. Error -handling middleware
4. Built-in middleware
5. third-party middleware

## What is the difference b/w application-level & route-level middleware?
Application-level middleware applies globally to all incming requests in the entire Express.js application.

Route-level middleware applies only to specific routes, not for all incoming requests.

## What is error handling middleware and how to implement it?
Error handling middleware in express.js is a special kind of middleware used to manage errors hapening while handling incoming requests.

To implement error handling in Express, define middleware with four parameters(err, req, res, next). Here the additional **error object parameter** will be used for error handling.

```typescript
const express = require("express");
const app = express();

//middleware generating error
app.use((req, res, next)=>{
    //simulate an error
    next(new Error("An error Occurred"));
});

//Error handling middleware
app.use((err, req, res, next)=>{
    console.log(err.stack);
    res.send(500).send("something went wrong !!");
});

const port = 3000;

app.listen(port,()=>{
    console.log(`Server is started in port ${port}`);
});
```

## If you have 5 middlewares then in which middleware you will do the error handling?
In case of multiple middleware, error-handling middleware should be defined at last(after all other middleware's) because when an error occurs, express.js will search for the next error-handling middleware skipping any regukar middeware or route handlers.

## What is built in middleware? How top server static files from Express.js?

 ```typescript
 
const express = require("express");
const app = express();

//server static files from the 'public' directory
app.use(express.static("public"));

//other routes and middleware can be defined here

//start the server
const port = 3000;

app.listen(port,()=>{
    console.log(`Server is started in port ${port}`);
});
```

Built-in  middleware's are built in functions inside Express framework which provides common functionalities.

**express.static()**  middleware is used for serving static files.

## What are third-party middlewares? Give some exmple
helmet, compression, etc.

Third-party middleware in Express.js are modules developed by third-party developers.


## What are the advantages of using middleware in express.js?


1. **Modularity**: Middleware allows you to modularize you application's functionality into **small, self-contained units**. each middleware functions can handle a specific task or concern, such as logging, authentication, or error handling.

2. **Reusability**: Middlewares can be reused at **multiple places and thet makes application code easier to maintain.

3. **Improved Request Handling**: Middleware functions have access to both request(req) and respose(res) objects which enables you to perform **validations on request** or modify the response before sending it back to the client.

4. **Flexible Control Flow**: Middleware functions can be applied globally to all routes or selectively to apecific routes, allowing you to control the flow of request processing in your application.

5. **Third-party middleware's**: Express.js offers a wide range of third-party middleware packages that provide additional functionality. for ex: cors, etc.


## What is Routing in Express.js?
Routing is the process of directing incoming HTTP requests to the appropriate handler function based on the request's method (GET, POST) and the URL path.

## What is the difference b/w middleware & routing in express?
**Middleware**
1. Middleware re functions.
2. Middleware functions can access  the request and response object, then they can:
a. Perform some actions(logic like authorization).
b. End the request-response cycle
c. Call the next middleware function


**Routing**
1. Routing is a process.
2.  Routing is the process of directing incoming HTTP requests to the appropriate handler functions(GET, PUT, POST/DELETE).

## How to implement routing? How do you define routes in Express.js?
To implement routing first define routes. In Express.js, routes are defined using the **app.MMETHOD() Functions** (Where METHOD is the HTTP request method(eg. GET, POST, PUT, DELETE) and app is an instance of the express application.)

## How to handle Routing in Express.js real applications?
1. import express
2. set middleware
3. import controller
4. define routes for different endpoints
5. start the server


## What are Route Handlers?
Route handler is the second agument passed to app.get() or app.post().

route handler function is used to process the request and generate a response.

```typescript

app.post("/login",(req, res)=>{
   //handle logic here
})
```
Here **(req, res)** is the route handlers.

## What are Route paramters in express.js?
Route parameters in Express.js allow you to capture dynamica values from the URL paths.
Route parameters can be accessed by using **req.params** object.

```typescript
 app.get("/user/:userId", (req, res)=>{
   //access the value
   const userId = req. params.userId;
   res.send(userId);
 });
 ```
 here **:userId** is Router parameters.


 ## What are Router object & Router methods and how to implement them?
 The rouer object is a mini version of an express application which is used for **handling routes.** Router methods are functions provided by Router object to defeine routes for different HTTP methods(GET, POST, DELETE, etc...).

```typescript
 //implement router method
 const express = require("express");
 const router = express.Router();

 router.get("/",(req, res)=>{});

 module.exports = router
 ```

 ```typescript
 //use router method
 const router = require('./router');

 app.use('/', router);

 ```

 ## What are the types of Router methods?

 1. router.get(path, callback) 
 2. router.post(path, callback)
 3. router.put(path, callback)
 4. router.delete(path, callback)

 ## What is the difference between app.get() and router.get() method?
 **app.get()**
 1. The app.get() method  is used to define routes **directly on the application object**.
 2. Routes defined using app.get() are automatically mounted on the root path(/).
 3. Routes defined using app.get() are not modular and cannot reused in other applications.

 **router.get()**

1. The router.get() method is used to define routes on a router object.
2. Routes defined using router.get() are not automatically mounted; they must be explicitly mounted **using app.use()**
3. Routes defined using router.get() are modular and can be **reused in other application** by exporting the router object.

## What is express.Router() in Express.js?
express.Router() is a class in Express.js that returns a new router object.

## Share a real application use of Routing?
Routing is used for **authenticating** requests based on the token available in request header.

```typescript
const express = require("express");
const app = express();
const router = express.Router();

//route-level middleware for authentication
const authenticate = (req, res, next)=>{
    if(req.headers.authorization){
        next();
    }else{
        res.status(401).send('unauthorize');
    }
};

router.get('/protected', authenticate, (req, res)=>{
    res.send('This is a protected route');
});

```

## What is Route Chaining in express.js?

Route chaining is a process defining **multiple route handlers** for a single route.

```typescript
const express = require("express");
const app = express();

fucntion middleware1(req, res, next){
  console.log("Middleware 1");
  next();
}

fucntion middleware2(req, res, next){
  console.log("Middleware 2");
  next();
}

//Route chainaing
app.get("/route", middleware1, middleware2 , (req, res)=>{
    console.log("ROute handlers");
    res.send("Route chaining example");
});

app.listen(3000, ()=>{
 console.log(`server is running`)
});
```

## What is Route Nesting in Express.js?
Route nesting organize routes hierarchically by grouping related routes under a common URL prefix. This allows you to create more modular ans structured routes, making you codebase easier to manage and maintain.

example:
**Route 1**
www.example.com/users
www.example.com/users/profile

**Route **
www.example.com/product
www.example.com/product/feature


## How to implement route nesting inExpress.js?
```typescript
//userRouter.js
const express = require("express");
const userRouter = express.Router();

//Route 1: www.example.com/users
userRouter.get("/", (req, res)=>{
 res.send("Users Home page");
});

//Route 2: www.example.com/users/profile
userRouter.get("/profile",(req, res)=>{
    res.send("User Profile page");
});

module.exports = usersRouter;
```

```typescript
//productsRouter.js
const express = require("express");
const productsRouter = express.Router();

//Router 1: www.example.com/products
//Router 2: www.example.com/products/features
//Router 3: www.example.com/products/ratings

module.exports = productsRouter;
```

```typescript
//app.js
const express = require("express");
const app = express();

//Import routers
const userRouter = require("./usersRouter");
const productsRouter = require("./productsRouter");

//Mount routers
app.use("/users", userRouter);
app.use("/products", productsRouter);

//Start the server
app.listen(3000, ()=>{
    console.log("Server is running on port 3000");
});
```

# Chapter- Express -Template Engines

## What are Template Engines in Express.js?
Template engines are libraries that enable developers to **generate dynamic HTML content** by combining static HTML templates with data.

## name some Template Engines libraries?
1. EJS(Embedded Javascript)
2. Handlebars
3. Pug (formerly jade)
4. Mustache
5. Nunjucks

## How to implement EJS templating engine in a express.js application?
1. npm install ejs
2. create a folder named views and create index.ejs

```typescript
<!--index.ejs-->
<html lang="en">
    <head>
      <title>EJS Example</title>
    </head>
    <body>
    <h1> <%= title%></h1>
    <p>Static HTML Template</p>
    </body>
</html>
```

```typescript
//server.js
const express = require("express");
const app = express();
const path = require('path');

//Set the view engine to EJS
app.set("view engine", 'ejs');

//set the views directory
app.set('views', path.joins(__dirname, 'views'));

// Route to render the index.ejs template
app.get('/', (req, res)=>{
    res.render('index', { title: 'Node.js with EJS'});
});

app.listen(3000, ()=>{
 console.log(`server is running`)
});
```


## How to implement  EJS templating engine in a Express.js application?
1. install EJS: npm install ejs.
2. create html template file index.ejs
3. create server file and set the view engine to EJS.
4. specify the views directory
5. Render EJS templates **using res.render() method**


## What is REST & RESTFUL API?
REST(Representational State Transfer) is an **architectural style** for designing networked applicatons(REST is a set of guidelines for creating API's).

RESTFUL API is a service which follow REST principles/guidelines.

## What are HTTP Request and Response structures in UI and REST API?
An HTTP(Hypertext Transfer protocol) request is a message sent by a client(such as a web browser or a mobile app) to a server, requsting a particular action or resource.
It contains HTTP Action(GET, POST,....), URL, Request Body, Request Header.

An HTTP response is a message sent by a server back to the client in response to an HTTP requet.It includes status code, content type, content.

## What are Top 5 RESt guidelines and the advantages of them?
1. **Separation of client and server**: The implementation of the client and the server must  be done independtly.
  **Advantage**: Independece allows easier maintenance, scalability, and evolution

2. Stateless: The server will not store anything above the latest HTTP request the client made.
**Advanatge**: It will treat every erquest as new request. It simplifies server implementation as it is not overoading it.

3. Uniform interface: Identofy theresource by URL(e.g, www.abc.com/api/question)
**Advantage**: Standardized URLs, making it easy to understand and use the API.

4. Cacheable:The API response should be cachable toimprove the peformance.
**Advantage**: Caching API responses improves performance by reducing the need for repeated requests to the server.

5. Layered system (mvc): The system should follow layered pattern.
**Advantage**: A layered system, such as MVC pattern, promotes modular design and seperation of concerns.

## What is the difference b/w REST API and SOAP API?

**REST**
1. REST is an architectural style.
2. Uses HTTP or HTTPS.
3. Uses lightweight formats like JSON, XML.
4. Statless
5. Relies on HTTP status codes.
6. Generally lightweight and faster.

**SOAP API**
1. SOAP (Simple Object Access Protocol) is a protocol.
2. Can  use various protocols(HTTP, SMTP.etc).
3. Typically uses XML.
4. Can be stateful or stateless.
5. Defines its own fault mechanism.
6. Can be slower due to XML processing.


## What are HTTP verbs and HTTP methods? v.imp
Http methods also known as HTTP verbs, are a set of actions that can take on a resource.

GET, POST, PUT, DELETE, PATCH


## What are GET,POST, PUT & DELETE HTTP methods?
1. **GET**: Retrive data from a specified resource.
2. **POST**: Submit data to be processed.
3. **PUT**: Update a resource or create a new rsource if it does not exist.
4. **DELETE**: Request removal of a resource.


## What is the difference between PUT & PATCH methods?
Both PUT and PATCH methods are used to  update a resource by replacing the resource with new data provide in the request.

In put request, the client sends the full updated resource in the requestbody, replacing the existing resource on the server.

In a PATCH request, the client sends specific change or instruction for modifying resource, updating only certain fields without resending the entire resource. 

## Explain the concept of Idempotence in RESTful APIs.
Idempotence meaning performing an operation multiple times should have the same outcome as performing it once.

**Idempotent Methods**
1. GET
2. PUT
3. DELETE

**Non-Idempotent Methods**
1. POST

## What are the role of satus codes in RestFul APIs?
Status codes are used to convey the results of a client's request.

**1xx(info)**
1. 100:Continue

**2XX(Success)**
1. 200: OK
2. 201: Created
3. 202: Accepted
4. 204: No content

**3xx(resirection)**
1. 300: Multiple Choices

**4xx(Client Error)**
1. 400:Bad Reuest
2. 401: unauthorized
3. 403: Forbidden
4. 404: Not Found

**5XX(Server Error)**
1. 500: Internal Server Error
2. 501:Not Implemented
3. 502: Bad Gateway
4. 503: Service unavailable

## What is CORS in Restful APIs?
CORS(Cross-Origin Resource sharing) is a security feature implemente in web browser that  restrict web pages or script from making requests to a different domain than the one that served the web page.

## How to remove CORS restrictions Restful APIs?

```typescript
const express = require('expresss');
const cores = require('cors');

const app = express();
//Enable CORS Middleare for all routes
app.use(cors());

//Optionally , configure CORS to allow requests from specific origins
app.use(cors({
    origin:'http://example.com'
}));
```

## What are Serialization & Deserialization?
Serilization is the process of **converting an object** into a format that can be stores, transmitted, or reconstructed later.


Deserializable is the process of converting serialized data, such as binary/XML/json data, back into an object.

**types of searialization**
1. Binary serialization
2. XML Serialization
3. JSON Serialization


## How to Serialize & Deserialize in Node js?
Serialize a js object into Json Format using JSON format using **JSON.stringify()**.

```typescript
//serialization (to JSON)
const obj = { name: "Happy", age:39};

const jsonStr = JSON.stringify(obj);
```

Deserialize a JSON String into a Javascript object using  **JSON.parse()** .

```typescript
const hspnStr2 = '{"name":"Happy", "age":39}';

const obj =JSON.parse(jsonStr2);
```

## Explain the concept of versioning in RESTful APIs. 
versioning in RESTful  APIs refres to the practice of **maintining multiple versions of an API to support backward compatibility.

```typescript
https://api.example.com/v1/resource
https://api.example.com/v2/resource
https://api.example.com/v3/resource
```

## What is an API document? What are the popular documentation formats?
An API document describe the functionality, features, and usage of REST API.

**REST API DOCUMNEtation formats**
1. Swagger(OpenAPI)
2. API Blueprint 
3. RAML

## What is the tyical structure od a REST API project in Node?
1. node_modules: Directory where npm packages are installed.
2. src: SOurce code directory
a. controllers: contains files responsible for handling business logic
b. routes: Defines API routes
c. utils: Contains reusable functions used across the project.
d. models: defines data models.
e.app.js: initializes and configure the express app. conatains routes, middleware, and other configurations.

3. .gitignore: A file that specifies files and directories to be  ignored by version control(e.g: node_modules, *.log)

4. package.json: the file that contains metadata abaout the project and its dependencies.

 ## What are Authentication and Authorization?
 Authentication is the process of verifying the identity of a user by validating thei credentials such as username and password.

 Authorization is the process of allowing an authenticated user access to resources. Authentication is always preceds to Authorization.

 **types of authentication**
 1. Basic(Username and Password) authentication
 2. API Key Authentication
 3. Token based Authentication(JWT)
 4. Multi-factor Authentication(MFA)
 5. Certificate-based Authentication

## What is Basic Authentication?
In basic  authentication, the user passes their  credentials on a post request. At  the Node Rest API end, credentials are verifies, and response is sent back.


## What is the role of hashing and salt in securing password?
Hashing is a process of converting a password into a fixed size string of characters using a mathematical algorithm.

## How can we create Hash Password in Node.js?
```typescript
const crypto = require("crypto");

// Define  a funcrion to hash and salt a password
function hashAnd SaltPassword(password){
     //1.  Generate a random salt
    const salt = crypto.randomBytes(16).toString("hex");

    //2. Create a hash object using SHA-256
    const hash = crypto .createHash("sha256");
    
    //3. Update the hash object with the salt and password
    hash.update(salt + password);

    //4. Get the hashed data in a hexadecimal string
    cinst hexHash = hash.digest("hex")

    //5. return the salt and hashed password as a string

    retun  salt + "." + hexHash;

}
```

## What is API Key Authentication?
In API Key authentication, the API owner will share an API key with thw users and this key will  authenticate the user of that API. The disadvantage of it is, API Keys can be shared or stolen threfore it may not be suitable for all scenarios.


## What are the parts of JWT token?
 1. HEader: contains info about type of token
 2. payload: contains CLAIMS
 3. Signature: is a string that is used to ensure the INtEGRITY of the token and verify that it has not been tampered with.

 ## How can you debug Node.js application?
 **Debugging technique in Node.js**
 1. console.log()
 2. debugger statement
 3. Node.js inspector
 4. vs code debugger
 5. chrome devtools

 ## Error-First Callback in Node.js

Error-First Callback in Node.js is a function which either returns an error object or any successful data returned by the function.

1. The first argument in the function is reserved for the error object. If any error has occurred during the execution of the function, it will be returned by the first argument
.
2. The second argument of the callback function is reserved for any successful data returned by the function. If no error occurred then the error object will be set to null.

```typescript
const fs = require("fs");

// This file does not exists
const file = "file.txt";

// Error first callback
// function with two
// arguments error and data
const ErrorFirstCallback = (err, data) => {
if (err) {
	return console.log(err);
}
console.log("Function successfully executed");
};

// function execution
// This will return
// error because file do
// not exist
fs.readFile(file, ErrorFirstCallback);
```