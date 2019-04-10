# React Related Questions

## How does React work

React creates a virtual DOM. When state changes in a component it firstly runs a "diffing" algorithm, which identifies what has changed in the virtual DOM. The second step is reconciliation, where it updates the DOM with the results of diff.

## What are the advantages of using React?

* It's easy to know how a component is rendered, you just need to look at the render function.
* JSX makes it easy to read the code of your components. It's also really easy to see the layout, or how components are plugged/combined with each other.
* You can render React on the server-side. This enables improves SEO and performance. 
* It's easy to test.
* You can use React with any framework \(Backbone.js, Angular.js\) as it's only a view layer. 

## React Lifecycle Methods 

* componentWillMount - this is most commonly used for app configuration in your root component. 
* componentDidMount - here you want to do all the setup you couldn't do without a DOM, and start getting all the data you need. Also if you want to set up eventListeners etc, this lifecycle hook is a good place to do that.
* componentWillReceiveProps - this lifecycle acts on particular prop changes to trigger state transitions.
* shouldComponentUpdate - if you are worried about wasted renders, shouldComponentUpdate is a great place to improve performance as it allows you to prevent a re-render. If component received new prop. shouldComponentUpdate should always return a boolean and based on what this is will determine if the component is re-rendered or not.
* componentWillUpdate - rarely used. It can be used instead of componentWillReceiveProps on a component that also has shouldComponentUpdate \(but no access to previous props\).
* componentDidUpdate - also commonly used to update the DOM in response to prop or state changes.
* componentWillUnmount - here you can cancel any outgoing network requests, or remove all eventListeners associated with the component. 

## Where in a React component should you make an AJAX request?

componentDidMount is where an AJAX request should be made in a React component. This method will be executed when the component "mounts" \(is added to the DOM\) for the first time. This method is only executed once during the component's life. Importantly, you can't guarantee the AJAX request will have resolved before the component mounts. If it doesn't, that would mean that you had be trying to setState on an unmounted component, which would not work. Making your AJAX request in componentDidMount will guarantee that there's a component to update. 

## What are controlled components

In HTML, form elements such as &lt;input&gt;, &lt;textarea&gt; and &lt;select&gt; typically maintain their own state and update it based on user input. When a user submits a form the values from the aforementioned elements are sent with the form. With React it works differently. The component containing the form will keep track of the value of the input in its state and will re-render the component each time the callback function e.g. onChange is fired as the state will be updated. An input form element whose value is controlled by React in this way is called a "controlled component".

## What are refs used for in React

Refs are created using React.createRef\(\) and attached to React elements via the ref attribute. Refs are commonly assigned to an instance property when a component is constructed so they can be referenced throughout the component. Refs provide a way to access DOM nodes or React elements created in the render method. Good examples of when to use refs are for managing focus/text selection or media playback, triggering imperative animations, or integrating with third-party DOM libraries. 

## What is a higher order component

A higher order component is a function that takes a component and returns a new component. HOC allows you to reuse code, logic and bootstrap abstraction.The most common is probably Redux's connect function. Beyond simply sharing utility libraries and simple composition, HOC is the best way to share behavior between React components. If you find yourself writing a lot of code in different places that does the same thing, you may be able to refactor that code into a reusable HOC.

## Why is it advised to pass a callback function to setState as opposed to an Object

Since this.props and this.state may be updated asynchronously, you should not rely on their values for calculating the next state.

## How would you prevent a component from rendering

Returning null from a component's render method doest not affect the firing of the component's lifecycle method.

## Why would you eject from create-react-app

Until you eject you are unable to configure web-pack or babel presets.

## What are props in React

props are properties that are passed into a child component from its parent, and are read only. 

## What is the difference between component props and state

props are read only and passed in from parent to child component. State is an internal object for a particular react component and can change, as it determines the state of the component. It's not visible to other components. 

## What is a pure component

A pure \(functional\) component in React is stateless \(like a dumb component\) and always renders the same given the same set of input props. 

## What is a pure functional component in React

A component that has no internal state of its own, nor any side effects, and thus is often written as a function as opposed to an ES6 class. 

## What is the render method for

To determine what should be rendered for a particular component. Could be a complex nested object of other child React components, or it could be as simple as a primitive JavaScript object. 

## What are PropTypes in React

They help indicate to React what data types a React component's properties are and should accept. 

## How Virtual DOM works in React

React builds up its own "virtual DOM" which is a lightweight representation of the DOM optimized for React's diffing algorithms and reconciliation process. Virtual DOM changes eventually propagate to the actual DOM at the end of the reconciliation process. 



























 




























