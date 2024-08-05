## Lift State Up
Lifting state up is a pattern in React where you move the state to a common ancestor component so that multiple child components can share and manage that state.

```
import React, { useState } from 'react';
import InputComponent from './InputComponent';
import DisplayComponent from './DisplayComponent';

function App() {
  const [inputValue, setInputValue] = useState('');

  return (
    <div>
      <InputComponent inputValue={inputValue} setInputValue={setInputValue} />
      <DisplayComponent inputValue={inputValue} />
    </div>
  );
}

export default App;

```

```
import React from 'react';

function InputComponent({ inputValue, setInputValue }) {
  const handleChange = (event) => {
    setInputValue(event.target.value);
  };

  return (
    <div>
      <input type="text" value={inputValue} onChange={handleChange} />
    </div>
  );
}

export default InputComponent;

```
```
import React from 'react';

function DisplayComponent({ inputValue }) {
  return (
    <div>
      <p>{inputValue}</p>
    </div>
  );
}

export default DisplayComponent;
```