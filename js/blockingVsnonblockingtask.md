## Blocking and Non-Blocking in Node

**What is Blocking?**
It refers to the blocking of further operation until the current operation finishes. Blocking methods are executed synchronously. Synchronously means that the program is executed line by line. The program waits until the called function or the operation returns.

**Example:** Following example uses the **readFileSync()** function to read files and demonstrate Blocking in Node.js

```
const fs = require('fs');

const filepath = 'text.txt';

// Reads a file in a synchronous and blocking way 
const data = fs.readFileSync(filepath, {encoding: 'utf8'});

// Prints the content of file
console.log(data);

// This section calculates the sum of numbers from 1 to 10
let sum = 0;
for(let i=1; i<=10; i++){
	sum = sum + i;
}

// Prints the sum
console.log('Sum: ', sum);
```

**What is Non-Blocking ?**
It refers to the program that does not block the execution of further operations. Non-Blocking methods are executed asynchronously. Asynchronously means that the program may not necessarily execute line by line. The program calls the function and move to the next operation and does not wait for it to return.

**Example:** Following example uses the **readFile()** function to read files and demonstrate Non-Blocking in Node

```
const fs = require('fs');

const filepath = 'text.txt';

// Reads a file in a asynchronous and non-blocking way 
fs.readFile(filepath, {encoding: 'utf8'}, (err, data) => {
	// Prints the content of file
	console.log(data);
});


// This section calculates the sum of numbers from 1 to 10
let sum = 0;
for(let i=1; i<=10; i++){
	sum = sum + i;
}

// Prints the sum
console.log('Sum: ', sum);
```
