## Immediately Invoked Function Expressions (IIFE) in JavaScript
Immediately Invoked Function Expressions (IIFE) are JavaScript functions that are executed immediately after they are defined. They are typically used to create a local scope for variables to prevent them from polluting the global scope.

```
(function() {
	// IIFE code block
	var localVar = 'This is a local variable';
	console.log(localVar); // Output: This is a local variable
})();
```