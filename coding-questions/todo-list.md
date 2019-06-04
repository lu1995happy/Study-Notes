---
description: 'Write TodoList in 3 ways: React, React Hooks, React Context API'
---

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

## Using React Hooks

{% code-tabs %}
{% code-tabs-item title="App.js" %}
```jsx
import React, { useState } from 'react';
import ReactDOM from 'react-dom';
import AddTodo from "./AddTodo";
import Filter from "./Filter";
import Todo from "./Todo";

const App = () => {

  const [todoState, setTodos] = useState({ todos: [] });
  const [filterState, setFilter] = useState({ filter: "All" });

  const addTodo = (todo) => {
    setTodos({
      todos: [
        ...todoState.todos,
        {text: todo, completed: false}
      ]
    });
  }

  const toggleTodoHandler = (index) => {
    setTodos({
      todos: [
        ...todoState.todos.slice(0, index),
        {
          ...todoState.todos[index],
          completed: !todoState.todos[index].completed
        },
        ...todoState.todos.slice(index + 1)
      ]
    })
  }

  const setFilterHandler = (filter) => {
    setFilter({
      filter: filter
    })
  }

  return (
    <React.Fragment>
      <AddTodo addTodo={addTodo}/>
      <Todo todoList={todoState.todos} toggleTodo={toggleTodoHandler} currentFilter={filterState.filter}/>
      <Filter currentFilter={filterState.filter} setFilter={setFilterHandler}/>
    </React.Fragment>
  );
}

ReactDOM.render(<App />, document.getElementById('root'));
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="AddTodo.js" %}
```jsx
import React, { useState } from "react";

const AddTodo = (props) => {
  
  const [state, setState] = useState({ value: "" });

  const onChangeHandler = (e) => {
    setState({ value: e.target.value })
  };

  const onClickHandler = () => {
    props.addTodo(state.value);
    setState({ value: "" });
  };

  return (
    <div>
      <input type="text" value={state.value} onChange={onChangeHandler} />
      <button onClick={onClickHandler}> Add Todo </button>
    </div>
  );
}

export default AddTodo;
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="Filter.js" %}
```jsx
import React from "react";

const Filter = (props) => {
  
  const showAllHandler = () => {
    props.setFilter("All");
  }

  const showActiveHandler = () => {
    props.setFilter("Active");
  }

  const showCompletedHandler = () => {
    props.setFilter("Completed");
  }

  return (
    <React.Fragment>
      <span>Show:</span>
      <button onClick={showAllHandler} disabled={props.currentFilter === "All"}>All</button>
      <button onClick={showActiveHandler} disabled={props.currentFilter === "Active"}>Active</button>
      <button onClick={showCompletedHandler} disabled={props.currentFilter === "Completed"}>Completed</button>
    </React.Fragment>
  );
}

export default Filter;
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="Todo.js" %}
```jsx
import React from "react";

const Todo = (props) => {

  const TodoList = props.todoList.filter((todo) => {
    if (props.currentFilter === "All") {
      return true;
    } else if (props.currentFilter === "Active") {
      return !todo.completed;
    } else {
      return todo.completed;
    }
  })

  return(
    <React.Fragment>
      {TodoList.map((todo, index) => {
        return (<li 
          key={index} 
          onClick={() => props.toggleTodo(index)} 
          style={{textDecoration: todo.completed ? "line-through" : "none"}}
        >
          {todo.text}
        </li>
      )}
    )}
    </React.Fragment>
  );
}

export default Todo;
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Using Regular React

{% code-tabs %}
{% code-tabs-item title="App.js" %}
```jsx
import React, { Component } from 'react';
import ReactDOM from 'react-dom';
import AddTodo from "./AddTodo";
import Filter from "./Filter";
import Todo from "./Todo";

class App extends Component {

  state = {
    todos: [],
    filter: "All"
  }

  addTodo = (todo) => {
    this.setState({
      todos: [
        ...this.state.todos,
        {text: todo, completed: false}
      ]
    });
  }

  toggleTodoHandler = (index) => {
    this.setState({
      todos: [
        ...this.state.todos.slice(0, index),
        {
          ...this.state.todos[index],
          completed: !this.state.todos[index].completed
        },
        ...this.state.todos.slice(index + 1)
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
        <AddTodo addTodo={this.addTodo}/>
        <Todo todoList={this.state.todos} toggleTodo={this.toggleTodoHandler} currentFilter={this.state.filter}/>
        <Filter currentFilter={this.state.filter} setFilter={this.setFilterHandler}/>
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
import React, { Component } from "react";

class AddTodo extends Component {
  
  state = { value: "" };

  onChangeHandler = (e) => {
    this.setState({ value: e.target.value })
  };

  onClickHandler = () => {
    this.props.addTodo(this.state.value);
    this.setState({ value: "" });
  };

  render() {
    return (
      <div>
        <input type="text" value={this.state.value} onChange={this.onChangeHandler} />
        <button onClick={this.onClickHandler}> Add Todo </button>
      </div>
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
import React from "react";

const Filter = (props) => {
  
  const showAllHandler = () => {
    props.setFilter("All");
  }

  const showActiveHandler = () => {
    props.setFilter("Active");
  }

  const showCompletedHandler = () => {
    props.setFilter("Completed");
  }

  return (
    <React.Fragment>
      <span>Show:</span>
      <button onClick={showAllHandler} disabled={props.currentFilter === "All"}>All</button>
      <button onClick={showActiveHandler} disabled={props.currentFilter === "Active"}>Active</button>
      <button onClick={showCompletedHandler} disabled={props.currentFilter === "Completed"}>Completed</button>
    </React.Fragment>
  );
}

export default Filter;
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="Todo.js" %}
```jsx
import React from "react";

const Todo = (props) => {

  const TodoList = props.todoList.filter((todo) => {
    if (props.currentFilter === "All") {
      return true;
    } else if (props.currentFilter === "Active") {
      return !todo.completed;
    } else {
      return todo.completed;
    }
  })

  return(
    <React.Fragment>
      {TodoList.map((todo, index) => {
        return (<li 
          key={index} 
          onClick={() => props.toggleTodo(index)} 
          style={{textDecoration: todo.completed ? "line-through" : "none"}}
        >
          {todo.text}
        </li>
      )}
    )}
    </React.Fragment>
  );
}

export default Todo;
```
{% endcode-tabs-item %}
{% endcode-tabs %}

