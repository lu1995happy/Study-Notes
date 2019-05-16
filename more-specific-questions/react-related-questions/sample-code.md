# Sample Code

## Class Component - Presentational, Dumb, Stateless

```jsx
import React, { Component } from "react";
import Person from "./Person/Person";

class App extends Component {
    state = {
        person: [
            {name: "Harry", age: 24}
        ]
    };
    
    switchNameHandler = (newName) => {
        this.setState({
            person: [
                {name: newName, age: 24}
            ]
        });
    };
    
    nameChangedHandler = (event) => {
        this.setState({
            person: [
                {name: event.target.value, age: 24}
            ]
        });
    };
    
    render() {
        return (
            <div className="App"> 
                <button onClick={() => this.switchNameHandler("Harry Lu")}>Switch Name</button>
                <Person 
                    name={this.state.person[0].name}
                    age={this.state.person[0].age}
                    click={this.switchNameHandler.bind(this, "Harry!!!")}
                    changed={this.nameChangedHandler}
                > My Hobbies: Sing, Dance, Rap, Basketball
                </Person>
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
            <p> onClick={props.click} I'm {props.name} and I am {props.age} years old!</p>
            <p>{props.children}</p> // anything between the parent's opening and closing tag
            <input type="text" onChange={props.changed} value={props.name} /> // two way data binding 
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

