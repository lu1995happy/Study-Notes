# Redux Related Questions

## How does Redux work

## Redux

The basic idea of redux is that the entire application state is kept in a single store. The store is simply a JavaScript object. The only way to change the state is by firing actions from your application and then writing reducers for these actions that modify the state. The entire state transition is kept inside reducers and should not have any side-effects. 

## Shallow Equality Check vs Deep Equality Check in Redux

Shallow equality checking \(or reference equality\) simply checks that two different variables reference the same object; in contrast, deep equality checking \(or value equality\) must check every value of two object's properties.  

A shallow equality check is therefore as simple and as fast as `a === b`, whereas a deep equality check involves a recursive traversal through the properties of two objects, comparing the value of each property at each step.

It's for this improvement in performance that Redux uses shallow equality checking. 

## What is the point of Redux

Application state management that is easy to reason about, maintain and manage in an asynchronous web application environment. 

## What are the 3 fundamental principles of Redux

* Single source of truth - the state of your whole application is stored in an object tree within a single store.
* State is read-only - the only way to change the state is to emit an action, an object describing what happened.
* changes are made with pure functions - to specify how the state tree is transformed by actions, you write pure reducers. 

## Why Redux is immutable

State is read-only. The only way to change the state is to emit an action, an object describing what happened. Inside a Redux application there is one particular function that takes the previous state and the action being dispatched, and returns the next state of the whole application. Reducer is the function knowing how to return a new state based on the action it receives. 

## Why state is immutable in Redux

Redux's use of shallow equality checking requires immutability if any connected components are to be update correctly. Immutability can bring increased performance to your app, and leads to simpler programming and debugging, as data that never changes is easier to reason about than data that is free to be changed arbitrarily throughout your app. In particular, immutability in the context of a Web app enables sophisticated change detection techniques to be implemented simply and cheaply, ensuring the computationally expensive progress of updating the DOM occurs only when it absolutely has to. 

## What is a store in Redux

The store is a JavaScript object that holds application state. Along with this it also has the following responsibilities:

* Allows access to state via getState\(\)
* Allows state to be updated via dispatch\(action\)
* Registers listeners via subscribe\(listener\)
* Handles unregistering of listeners via the function returned by subscribe\(listener\)

## What is an action in Redux

Actions are plain JavaScript objects. They must have a type indicating the type of action being performed. In essence, actions are payload of information that send data from your application to your store. 

## What is a reducer in Redux

A reducer is simply a pure function that takes the previous state and an action, and returns the next state. 

## What is Redux Thunk used for 

Redux thunk is a middleware that allows you to write action creators that return a function instead of an action. The thunk can then be used to delay the dispatch of an action if a certain condition is met. This allows you to handle the asynchronous dispatching of actions. This also allows you to dispatch multiple actions. 

## What are typical middleware choices for handling asynchronous calls in Redux

Redux Thunk, Redux Promise, Redux Saga

## What is mapStateToProps and mapDispatchToProps

Functions typically seen in Redux applications that provide functions to Redux on how to map state / dispatch function to a set of props. 

































