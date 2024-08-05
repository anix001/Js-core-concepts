## Lazy Loading
Lazy loading is a technique where you delay loading parts of your application until they are actually needed. This helps improve the initial load time of your app because it only loads the necessary parts at the beginning, and other parts are loaded on demand.

```
import React, { lazy, Suspense } from 'react';

const LazyComponent = lazy(() => import('./LazyComponent'));

function App() {
  return (
    <div>
      <h1>My App</h1>
      <Suspense fallback={<div>Loading...</div>}>
        <LazyComponent />
      </Suspense>
    </div>
  );
}

export default App;
```

## Suspense
Suspense is a component that lets you handle loading states for components that are being lazily loaded. It acts as a placeholder that can show a loading indicator or message while the actual component is being fetched and rendered.


```
import React from 'react';

function LazyComponent() {
  return (
    <div>
      <h2>I am a lazy-loaded component!</h2>
    </div>
  );
}

export default LazyComponent;
```

```
import React, { lazy, Suspense } from 'react';
import ReactDOM from 'react-dom';

const LazyComponent = lazy(() => import('./LazyComponent'));

function App() {
  return (
    <div>
      <h1>My App</h1>
      {/* Suspense component to handle loading state */}
      <Suspense fallback={<div>Loading...</div>}>
        <LazyComponent />
      </Suspense>
    </div>
  );
}

ReactDOM.render(<App />, document.getElementById('root'));

```
