# React

## React

React is a Javascript library for building User Interfaces.

## How does React work

React creates a virtual DOM. When state changes in a component it firstly runs a "diffing" algorithm, which identifies what has changed in the virtual DOM. The second step is reconciliation, where it updates the DOM with the results of diff.

## React Advantages

* It's easy to know how a component is rendered, you just need to look at the render function.
* JSX makes it easy to read the code of your components. It's also really easy to see the layout, or how components are plugged/combined with each other.
* You can render React on the server-side. This enables improves SEO and performance. 
* It's easy to test.
* You can use React with any framework \(Backbone.js, Angular.js\) as it's only a view layer. 

## React Lifecycle Methods 

* constructor
* componentWillMount - this is most commonly used for app configuration in your root component. 
* render
* componentDidMount - here you want to do all the setup you couldn't do without a DOM, and start getting all the data you need. Also if you want to set up eventListeners etc, this lifecycle hook is a good place to do that.
* componentWillReceiveProps - this lifecycle acts on particular prop changes to trigger state transitions.
* shouldComponentUpdate - if you are worried about wasted renders, shouldComponentUpdate is a great place to improve performance as it allows you to prevent a re-render. If component received new prop. shouldComponentUpdate should always return a boolean and based on what this is will determine if the component is re-rendered or not.
* componentWillUpdate - rarely used. It can be used instead of componentWillReceiveProps on a component that also has shouldComponentUpdate \(but no access to previous props\).
* render
* componentDidUpdate - also commonly used to update the DOM in response to prop or state changes.
* componentWillUnmount - here you can cancel any outgoing network requests, or remove all eventListeners associated with the component. 

![](../.gitbook/assets/image.png)

## React - Redux Workflow

![](../.gitbook/assets/image%20%289%29.png)

## Redux vs setState\(\)

Use Redux if your state is shared across multiple components. 

Use setState\(\) if it’s used only in a single component.

## React Component

A component is a function or a class which optionally accepts input and returns a React element.

## React Router

React Router is the standard routing library for React. React Router keeps your UI in sync with the URL. It has a simple API with powerful features like lazy code loading, dynamic route matching, and location transition handling. 

## Synthetic Event

Synthetic Event is a cross-browser wrapper around the browser's native event. It has the same interface as the browser's native event, including `stopPropagation()` and `preventDefault()`, except the events work identically across all browsers. 

## One way data binding in React vs Two way data binding in Angular

In Angular, if you change the UI element, then the corresponding model state changes as well. Additionally, if you change the model state, then the UI element changes.

In React, when the model state update, it will render the change in the UI element. However, if you change the UI element, the model state does not change. 

## Two Kinds of Applications 

| Single Page Applications | Multi Page Applications |
| :--- | :--- |
| Only ONE HTML Page, Content is \(re\)rendered on Client | Multiple HTML Pages, Content is rendered on Server. |
| Typically only ONE ReactDOM.render\(\) call | One ReactDOM.render\(\) call per "widget" |

## Server-Side Rendering - pros & cons 

advantages:

* search engines can crawl the site for better SEO
* initial loading becomes faster
* great for static sites

disadvantages:

* frequent server requests
* full page reloads, overall slow page rendering
* non-rich site interactions

## Client-Side Rendering - pros & cons

advantages:

* rich site interactions
* fast website rendering after the initial load
* great for web applications
* robust selection of JavaScript libraries

disadvantages:

* low SEO if not implemented correctly
* initial load might require more time
* in most cases, requires an external library

## Why need super\(props\)

If you don't initialize state and you don't bind methods, you don't need to implement the constructor for your React component.

The constructor for a React component is called before it is mounted. When implementing the constructor for a React.component subclass, you should call super\(props\) before any other statement. Otherwise, `this.props` will be undefined in the constructor, which can lead to bugs. 

## How to re-render out of Lifecycle

this.forceUpdate\(\)

## User Authentication Login

The React App sends the Auth to the server, and then the server sends back a Token that will be stored in the JavaScript localStorage. After that we can use the Token we received to request for protected resources from the server.

## 3 ways for Debugging React Apps

* Finding Logical Errors by using Chrome Developer Tools - Check your code inside Source
* Working with the React Developer Tools Chrome Extension 
* Using Error Boundaries \(**only use Error Boundaries for cases where you know that it might fail and you can't control that\)** 

## Error Handling Method - Error Boundary

Error boundaries are React components that catch JavaScript errors anywhere in their child component tree, log those errors, and display a fallback UI instead of the component tree that crashed. Error boundaries catch errors during rendering, in lifecycle methods, and in constructors of the whole tree below them.

A class component becomes an error boundary if it defines a new lifecycle method called `componentDidCatch(error, info)`

[**ErrorBoundary Sample Code**](sample-code.md#errorboundary)\*\*\*\*

## Composition vs inheritance in React

React has a powerful composition model, and composition is recommended instead of inheritance to reuse code between components. 

## Rendering Multiple Components

* You can build collections of elements and include them in JSX using curly braces {}.
* Using `<React.Fragment />`
* Return an array of elements using Map function and assign key to them 

## Keys

Keys help React identify which items have changed, are added, or are removed. Keys should be given to the elements inside the array to give the elements a stable identity. 

## Where in a React component should you make an AJAX request?

componentDidMount

## Controlled Component vs Uncontrolled Component

| Controlled Component | Uncontrolled Component |
| :--- | :--- |
| the value of form elements \(input, textarea, select\) is stored in react component and changed by event handler | the value of form elements is stored in DOM not in react component, we can use refs to operate the DOM element |

## Single-page Application

A single-page application is an application that loads a single HTML page and all the necessary assets \(such as JavaScript and CSS\) required for the application to run. Any interactions with the page or subsequent pages do not require a round trip to the server which means the page is not reloaded.

## Refs

Refs are created using React.createRef\(\) and attached to React elements via the ref attribute. Refs are commonly assigned to an instance property when a component is constructed so they can be referenced throughout the component. Refs provide a way to access DOM nodes or React elements created in the render method. Good examples of when to use refs are for managing focus/text selection or media playback, triggering imperative animations, or integrating with third-party DOM libraries. 

## Higher Order Component

A higher order component is a function that takes a component and returns a new component. HOC allows you to reuse code, logic and bootstrap abstraction.The most common is probably Redux's connect function. Beyond simply sharing utility libraries and simple composition, HOC is the best way to share behavior between React components. If you find yourself writing a lot of code in different places that does the same thing, you may be able to refactor that code into a reusable HOC.

[Higher Order Component Sample Code](sample-code.md#three-ways-using-higher-order-component)

## Why is it advised to pass a callback function to setState as opposed to an Object

Since this.props and this.state may be updated asynchronously, you should not rely on their values for calculating the next state.

## How would you prevent a component from rendering

* return null in the render method function
* return false in shouldComponentUpdate\(\) lifecycle method function in class based component

## How to access the underlying DOM component

When the ref attribute is used on an HTML element, the ref created in the constructor with React.createRef\(\) receives the underlying DOM element as its current property. 

## Shadow DOM

Shadow DOM provides a way to attach a hidden separated DOM to an element. It allows use to keep the markup structure, style and behavior hidden and separate from other code on the page so that different parts do not clash, and the code can be kept nice and clean.

## Why would you eject from create-react-app

Until you eject you are unable to configure web-pack or babel presets.

## Props vs State

props are properties that are passed into a child component from its parent, and are read only.  State is an internal object for a particular react component and can change, as it determines the state of the component. It's not visible to other components. 

only changes in `props` and/or `state` trigger React to re-render the components and potentially update the DOM in the browser. 

## Pure Component

A pure \(functional\) component in React is stateless \(like a dumb component\) and always renders the same given the same set of input props. 

## Pure Functional Component 

A component that has no internal state of its own, nor any side effects, and thus is often written as a function as opposed to an ES6 class. 

## Why need render method

To determine what should be rendered for a particular component. Could be a complex nested object of other child React components, or it could be as simple as a primitive JavaScript object. 

## PropTypes

They help indicate to React what data types a React component's properties are and should accept. 

[PropTypes Sample Code](sample-code.md#using-proptypes-to-check-the-input-data-types)

## How Virtual DOM works

React builds up its own "virtual DOM" which is a lightweight representation of the DOM optimized for React's diffing algorithms and reconciliation process. Virtual DOM changes eventually propagate to the actual DOM at the end of the reconciliation process. 

## Test method

Jest and Enzyme



























 





























