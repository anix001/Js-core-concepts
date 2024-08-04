A Higher-Order Component (HOC) is a pattern in React for reusing component logic. It's a function that takes a component and returns a new component. This allows you to add additional functionality to existing components without modifying them directly.

## Why Use Higher-Order Components?
1. Code Reusability: HOCs help in reusing common logic across multiple components.
2. Separation of Concerns: They allow you to separate the concerns of different functionalities, making your code cleaner and more maintainable.
3. Composition: HOCs provide a way to compose behaviors and props into components dynamically.

## How Does a Higher-Order Component Work?
A higher-order component is essentially a function that:
1. Takes a component as an argument.
2. Returns a new component that wraps the original component.
3. The new component can add new props, state, lifecycle methods, and other logic to the wrapped component.

Step 1: Create the HOC
```
import React from 'react';

// This is the HOC
function withLoading(Component) {
  return function WithLoadingComponent({ isLoading, ...props }) {
    if (!isLoading) return <Component {...props} />;
    return <p>Loading...</p>;
  };
}

```

Step 2: Create a Regular Component
```
import React from 'react';

function DataDisplay({ data }) {
  return (
    <div>
      <h1>Data:</h1>
      <pre>{JSON.stringify(data, null, 2)}</pre>
    </div>
  );
}

export default DataDisplay;
```

Step 3: Wrap the Component with the HOC
```
import React, { useState, useEffect } from 'react';
import DataDisplay from './DataDisplay';
import withLoading from './withLoading';

const DataDisplayWithLoading = withLoading(DataDisplay);

function App() {
  const [data, setData] = useState(null);
  const [isLoading, setIsLoading] = useState(true);

  useEffect(() => {
    // Simulate an API call
    setTimeout(() => {
      setData({ name: 'John Doe', age: 25 });
      setIsLoading(false);
    }, 2000);
  }, []);

  return <DataDisplayWithLoading isLoading={isLoading} data={data} />;
}

export default App;
```