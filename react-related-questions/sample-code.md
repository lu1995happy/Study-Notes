# React Sample Code

## Class Component - Containers, Smart, Stateful

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
                // first way to pass arugments to event handlers
                <button onClick={() => this.switchNameHandler("Harry Lu")}>Switch Name</button>
                <Person 
                    name={this.state.person[0].name}
                    age={this.state.person[0].age}
                    // second way to pass augments to event handlers
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

## Functional Component - Presentational, Dumb, Stateless

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

## Three way to handle events 

* Bind this in the constructor

```jsx
constructor(props) {
    super(props);
    this.state = {};
    this.handleClick = this.handleClick.bind(this);
}
```

* Using arrow functions

```jsx
handleClick = () => {
    console.log("this is:", this);
}
```

* Using arrow functions in the callback - Since callback is created each time the button renders. If this callback is passed as a prop to lower components, those components might do an extra re-rendering, which will cause performance problems. 

```jsx
render() {
    return (
        <button onClick={(e) => this.handleClick(e)}> Click me </button>
    );
}
```

## ErrorBoundary 

```jsx
// must wrap the code you want to test using high order components 
import React, { Component } from 'react';

class ErrorBoundary extends Component {
  state = {
    hasError: false,
    errorMessage: ''
  }

  componentDidCatch = (error, info) => {
    this.setState({ hasError: true, errorMessage: error });
  }

  render() {
    if (this.state.hasError) {
      return <h1>{this.state.errorMessage}</h1>;
    } else {
      return this.props.children;
    }
  }
}

export default ErrorBoundary;
```

## Three ways using Higher Order Component

```jsx
// This one just do wrap other component
const aux = props => props.children; 

export default aux;
```

```jsx
// This one just add styling to the children component
import React from 'react';

// const withClass = props => (
//   <div className={props.classes}>
//     {props.children}
//   </div>
// );

const withClass = (WrappedComponent, className) => {
  return props => (
    <div className={className}>
        // getting the props from the child compoent
        <WrappedComponent {...props}/> 
    </div>
  );
}

export default withClass;
```

```jsx
// This is the built-in way that works same as the first one
import React, {Fragment} from 'react';

<Fragment>
    // some content
</Fragment>
```

## Using PropTypes to check the input Data types

```jsx
// Use this to check the input data types of the props
import PropTypes from 'prop-types';

Person.propTypes = {
  click: PropTypes.func,
  name: PropTypes.string,
  age: PropTypes.number,
  changed: PropTypes.func
};
```

## Better way to use setState\(\)

```jsx
// the better way to update the state when you are depending on old state
// Since setState updates the state asynchronously
this.setState((state, props) => {
    return {
        counter: state.counter + props.increment
    };
});
```

## Render Lists Conditionally

```jsx
import React, { Component } from 'react';
import Person from './Person/Person';

class App extends Component {
  state = {
    persons: [
      { id: 'a1', name: 'Harry', age: 24 },
      { id: 'a2', name: 'Sherry', age: 21 },
      { id: 'a3', name: 'Steven', age: 26 }
    ],
    otherState: 'some other value',
    showPersons: false
  }

  nameChangedHandler = (event, id) => {
    const personIndex = this.state.persons.findIndex(p => {
      return p.id === id;
    })

    const person = {
      ...this.state.persons[personIndex]
    };

    // const person = Object.assign({}, this.state.persons[personIndex]);

    person.name = event.target.value;

    const persons = [...this.state.persons];
    persons[personIndex] = person;

    this.setState({ persons: persons });
  }

  deletePersonHandler = (personIndex) => {
    // const persons = this.state.persons.slice();
    // Updating State Immutably
    const persons = [...this.state.persons];
    persons.splice(personIndex, 1);
    this.setState({ persons: persons });
  }

  togglePersonsHandler = () => {
    const doesShow = this.state.showPersons;
    this.setState({ showPersons : !doesShow});
  }

  render() {
    let persons = null;

    if (this.state.showPersons) {
      persons = (
        <div>
          {this.state.persons.map((person, index) => {
            return <Person 
              click={() => this.deletePersonHandler(index)}
              name={person.name} 
              age={person.age}
              key={person.id}
              changed={(event) => this.nameChangedHandler(event, person.id)} />
          })}
        </div>
      )
    }
    return (
      <div className="App">
        <h1>Hi, I'm a React App</h1>
        <p>This is really working!</p>
        <button 
          onClick={this.togglePersonsHandler}>Switch Name</button>
        {persons}
      </div>
    );
  }
}

export default App;
```

