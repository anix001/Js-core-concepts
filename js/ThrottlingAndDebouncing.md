Throttling and debouncing are techniques used to control how often a function is executed, especially when it's tied to events that can fire very frequently, like scrolling, resizing, or typing.

## Throttling:
Throttling ensures that a function is called at most once every X milliseconds, no matter how many times the event occurs. 

## Debouning:
Debouncing ensures that a function is only called after a certain amount of time has passed without the event firing again. If the event keeps happening, the timer resets.

Imagine you're texting a friend and you don't want to interrupt them with multiple notifications. You decide to wait until they're done typing for 3 seconds before you send your reply. If they keep typing, you keep waiting.


**Throttling Example:**
Imagine you have a button that logs a message to the console every time it's clicked. Without throttling, if someone clicks the button rapidly, the message will log each time they click. With throttling, you can make it so that the message is logged only once every 2 seconds, no matter how many times the button is clicked.
```
function logMessage() {
  console.log("Button clicked!");
}

function throttle(func, delay) {
  let lastCall = 0;
  return function() {
    const now = new Date().getTime();
    if (now - lastCall >= delay) {
      lastCall = now;
      func();
    }
  };
}

const throttledLogMessage = throttle(logMessage, 2000);

document.getElementById("myButton").addEventListener("click", throttledLogMessage);
```

**Debouncing Example:**
Imagine you have a search input field that triggers a search function every time a user types. Without debouncing, the search function would run for every keystroke, which can be inefficient. With debouncing, the search function only runs after the user stops typing for, say, 500 milliseconds.

```
function searchQuery() {
  console.log("Search triggered!");
}

function debounce(func, delay) {
  let debounceTimer;
  return function() {
    clearTimeout(debounceTimer);
    debounceTimer = setTimeout(() => {
      func();
    }, delay);
  };
}

const debouncedSearchQuery = debounce(searchQuery, 500);

document.getElementById("searchInput").addEventListener("input", debouncedSearchQuery);
```



