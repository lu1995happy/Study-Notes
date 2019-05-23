# React Lifecycle

## Component Lifecycle - Creation

1. constructor\(props\) - Call super\(props\), DO: set up state, DON'T: cause side-effects\(HTTP request\)
2. getDerivedStateFromProps\(props, state\) - DO: sync state, DON'T: cause side-effects
3. render\(\) - prepare & structure your JSX code
4. Render Child Components 
5. componentDidMount\(\) - DO: cause side-effects, DON'T: update state\(triggers re-render\)

```jsx
import React, { Component } from 'react';

class App extends Component {
  constructor(props) {
    super(props);
    console.log('[App.js] constructor');
    // you can also initialize the state here
  }

  state = {
    persons: [
      { id: 'a1', name: 'Harry', age: 24 }
    ]
  }

  static getDerivedStateFromPros(props, state) {
    console.log('[App.js] getDerivedStateFromProps');
    return state;
  }

  componentDidMount() {
    console.log('[App.js] componentDidMount');
  }

  shouldComponentUpdate(nextProps, nextState) {
    console.log('[App.js] shouldComponentUpdate');
    return true;
  }

  componentDidUpdate() {
    console.log('[App.js] componentDidUpdate');
  }

  render() {
    console.log('[App.js] render');

    return (
      <div className={classes.App}>
        {persons}
      </div>
    );
  }
}

export default App;
```

## Component Lifecycle - Update

1. getDerivedStateFromProps\(props, state\) - DO: sync state to props, DON'T: cause side-effects
2. shouldComponentUpdate\(nextProps, nextState\) - May cancel updating process! DO: decide whether to continue or not, DON'T: cause side-effects
3. render\(\) - prepare & structure your JSX code 
4. Update Child Component Props
5. getSnapshotBeforeUpdate\(prevProps, prevState\) - DO: last-minute DOM ops, DON'T: cause side-effects
6. componentDidUpdate\(\) - DO: cause side-effects, DON'T: update state\(triggers re-render\)

```jsx
import React, { Component } from 'react';

class Persons extends Component {
  // static getDerivedStateFromProps(props, state) {
  //   console.log('[Persons.js] getDerivedStateFromProps');
  //   return state;
  // }

  // componentWillReceiveProps(props) {
  //   console.log('[Persons.js] componentWillReceiveProps', props);
  // }

  // Optimization
  shouldComponentUpdate(nextProps, nextState) {
    console.log('[Persons.js] shouldComponentUpdate');
    if (nextProps.persons !== this.props.persons) {
      return true;
    } else {
      return false;
    }
  }

  getSnapshotBeforeUpdate(prevProps, prevState) {
    console.log('[Persons.js] getSnapshotBeforeUpdate');
    return { message: 'Snapshot!' };
  }

  // componentWillUpdate() {

  // }

  componentDidUpdate(prevProps, prevState, snapshot) {
    console.log('[Persons.js] componentDidUpdate');
    console.log(snapshot);
  }

  componentWillUnmount() {
    console.log('[Persons.js] componentWillUnmount');
  }

  render() {
    console.log('[Persons.js] rendering...');
    return this.props.persons.map((person, index) => {
      return (
        <Person 
          click={() => this.props.clicked(index)}
        />
      )
    });
  }
};
  
export default Persons;
```





