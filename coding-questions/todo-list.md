# Todo-List

## Using React Context API

{% code-tabs %}
{% code-tabs-item title="App.js" %}
```jsx
import React from 'react';
import ReactDOM from 'react-dom';
import { TodoContext } from './Todo-Context';
import Todos from './Todos';
import AddTodo from './AddTodo';
import Filter from './Filter';

class App extends React.Component {

  state = {
    todo: [],
    filter: "All"
  };

  addTodoHandler = (todo) => {
    this.setState({
      todo: [
        ...this.state.todo,
        {
          text: todo,
          completed: false
        }
      ]
    })
  }

  toggleTodoHandler = (index) => {
    this.setState({
      todo: [
        ...this.state.todo.slice(0, index),
        {
          ...this.state.todo[index],
          completed: !this.state.todo[index].completed
        },
        ...this.state.todo.slice(index + 1)
      ]
    })
  }

  setFilterHandler = (filter) => {
    this.setState({
      filter: filter
    })
  }

  render() {
    return (
      <React.Fragment>
        <TodoContext.Provider value={{ todo: this.state.todo, filter: this.state.filter }}>
          <AddTodo addTodo={this.addTodoHandler} />
          <Todos toggleTodo={this.toggleTodoHandler} />
          <Filter setFilter={this.setFilterHandler} />
        </TodoContext.Provider>
      </React.Fragment>
    );
  }
}

ReactDOM.render(<App />, document.getElementById('root'));
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="AddTodo.js" %}
```jsx
import React from "react";

class AddTodo extends React.Component {

  state = {
    value: ""
  };

  render() {
    return (
      <React.Fragment style={{display: "block"}}>
        <input value={this.state.value} onChange={(e) => this.setState({ value: e.target.value })}/>
        <button onClick={() => {
          this.props.addTodo(this.state.value);
          this.setState({ value: "" });
        }}>Add Todo</button>
      </React.Fragment>
    );
  }
}

export default AddTodo;
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="Filter.js" %}
```jsx
import React from 'react';
import { TodoContext } from './Todo-Context';

const Filter = (props) => {

  return (
    <TodoContext.Consumer>
      {({filter}) => {
        return (
          <React.Fragment>
            <span>Show:</span>
            <button onClick={() => props.setFilter("All")} disabled={filter === "All"}>All</button>
            <button onClick={() => props.setFilter("Active")} disabled={filter === "Active"}>Active</button>
            <button onClick={() => props.setFilter("Completed")} disabled={filter === "Completed"}>Completed</button>
          </React.Fragment>
        )
      }}
    </TodoContext.Consumer>
  );
}

export default Filter;
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="Todos.js" %}
```jsx
import React from 'react';
import { TodoContext } from './Todo-Context';

const Todos = (props) => {

  const filterFunc = (todo, filter) => {
    return todo.filter((todo) => {
      if (filter === "All") {
        return true;
      } else if (filter === "Active") {
        return !todo.completed;
      } else {
        return todo.completed;
      }
    })
  }

  return (
    <TodoContext.Consumer>
      {
        ({todo, filter}) => (
          <React.Fragment>
            {
              filterFunc(todo, filter).map((todo, index) => {
                return (
                  <li
                    key={index}
                    onClick={() => props.toggleTodo(index)}
                    style={{ textDecoration: todo.completed ? "line-through" : "none" }}
                  >
                    {todo.text}
                  </li>
                )
              })
            }
          </React.Fragment>
        )
      }
    </TodoContext.Consumer>
  )
}

export default Todos;
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="TodoContext.js" %}
```jsx
import React from "react";

export const TodoContext = React.createContext({
  todo: [],
  filter: "All"
});
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Using Regular React

