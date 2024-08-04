
The React lifecycle consists of a series of methods that are invoked at different stages of a component's existence. These methods can be grouped into three phases:

## Mounting: When the component is being created and inserted in the DOM.
 1. constructor(): Initializes the component's state and binds event handlers.

 2. getDerivedStateFromProps(): Sync state with props when the component is created.

 3. render(): Returns the jsx that defines the component's UI.

 4. ComponentDidMount(): Invoked after the component is insertd into the DOM. Good for making network requests or initializing libraries.

 ## Updating: When a component is being re-renderd due to changes in props or state.

  1. getDerivedStateFromProps(): Syncs state with props when the component is updated.

  2. shouldComponentUpdated(): Determines if a re-render is necessary.

  3. render(); Returns the updated JSX.

  4. getSnapshotBeforeUpdarte(): Captures some information (like scroll position) before the Dom is updated.

  5. componentDidUpdate(): Invoked after the component's updates are flushed to the DOM. Good for performing DOM operations or network requests after an update.

  ## UnMounting: When a component is removed from the DOM.

  1. componentWillUnmount(): Cleanup tasks like removing event listeners or canceling network requests.