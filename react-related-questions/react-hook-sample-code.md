# React Hook Sample Code

## useState

useState\(\) returns an array with exactly two elements: 

\(1\) Your current state value, \(2\) A method to update your state value.

useState\(\) will replace the old state instead of merging. 

```jsx
import React, { useState } from "react";
import Person from "./Person/Person";

const App = props => {
    const [personState, setPersonState] = useState({
        person: [
            { name: "Harry", age: 24 }
        ]
    });
    
    const [otherState, setOtherState] = useState("some other value");
    
    const switchNameHandler = () => {
        setPersonState({
            person: [
                {name: "Harry Lu", age: 25}
            ]
        });
    };
    
    return (
        <div className="App">
            <button onClick={switchNameHandler}>Switch Name</button>
            <Person
                name={personState.person[0].name}
                age={personState.person[0].age}
            /> 
        </div>
    );
}

export default App;
```

## useEffect & useRef & useContext

```jsx
import React, { useEffect, useRef, useContext } from 'react';
import AuthContext from '../../context/auth-context';

const cockpit = props => {
  const toggleBtnRef = useRef(null);
  const authContext = useContext(AuthContext);

  useEffect(() => {
    // Http request...
    // same as componentDidMount and componentDidUpdate
    // setTimeout(() => {
    //   alert('Saved data to cloud!');
    // }, 1000);
    toggleBtnRef.current.click();
    return () => {
      // clean-up code here
      // same as componentWillUnmount 
    };
  }, []); // only re-run the effect if the value inside changes

  return (
    <div>
      <button ref={toggleBtnRef}>
        Toggle Persons
      </button>
      <button onClick={authContext.login}>Log in</button>
    </div>
  );
};

export default React.memo(cockpit);
```

