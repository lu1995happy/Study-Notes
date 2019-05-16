# Sample Code

## Class Component - Presentational, Dumb, Stateless

```jsx
import React, { Component } from "react";

class App extends Component {
    state = {
        persons: [{name: "Harry", age: 28}]
    };
    
    render() {
        return (
            <div className="App"> 
                <h1>Hi</h1>
            </div>
        );
    }
} 

export default App;
```

## Functional Component - Containers, Smart, Stateful

```jsx
import React from "react";

const person = (props) => {
    return (
        <div>
            <p>I'm {props.name} and I am {props.age} years old!</p>
            <p>{props.children}</p> // anything between the parent's opening and closing tag
        </div>
    );
};

export default person;
```

## React Hooks - useState

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
            <button onClick={this.switchNameHandler}>Switch Name</button>
            <Person
                name={personState.person[0].name}
                age={personState.person[0].age}
            /> 
        </div>
    );
}

export default App;
```

