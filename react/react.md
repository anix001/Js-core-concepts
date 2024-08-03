 ## State VS Props
    State is built-in react object that is used to contain data or information about the component. A component state can change over time; whenever it changes, the component re-renders.

    Props stands for properties and is used for passing data from one component to another. Data with props are passed in unidirectional flow from parent to child.

## Component
    Components are independent and reusable bits of code. They serve the same purpose as js functions, but work in isolation and retrun html.Components come in two types,
    Class componnets and functional components.

    ## class Component
       React Class Components are JavaScript classes that extend React.Component. They define the UI, manage state, and handle events within your application.
        
       ```
       import React from "react";

        class App extends React.Component {
        render() {
            return <h1>GeeksForGeeks</h1>;
        }
        }

        export default App;
        ```
        
    ## Functional Component
      Functional component is just a simple javascript function; it accepts the data in the form of props and returns the react element. (The React Element is a small piece of code representing a part of the User Interface in a React Application. Every React element is a JavaScript Object at the end. It is a plain JavaScript object that represents a virtual representation of a DOM element)

      ```
        Import React from 'react';
        import Video from "./components/Video";
        import './App.css'; 
        function App() {
        return (
            <div className="App">
            <Video />
            </div>
        );
        }
        export default App;
    ```