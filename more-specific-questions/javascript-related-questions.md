# JavaScript Related Questions

## What is shallow comparison check

The shallow comparison check means that JavaScript only checks that the value's object IDs are the same, not their contents are the same. The ID here means the memory address for where JavaScript stores the information for that particular object.

## Closure

A closure is an inner function that has access to the variables in the outer \(enclosing\) function's scope chain. 

The closure has access to variables in three scopes

* variables in its own scope
* variables in the enclosing function's scope
* global variables

## Falsey values

* 0
* null
* undefined
* ""
* false
* NaN

## 4 types of scoping

* Global Scope - declared outside for any function, use it without declaring
* Function Scope - var
* Block Scope - let & const 
  * const: immutable variable, must be initialized
* Module Scope

## Create an Object in 6 different ways

* Object\(\) constructor 

```javascript
const obj = new Object(); 
```

* Object.create\(\) 
  * creates a new object extending the prototype object passed as a parameter 

```javascript
const obj = Object.create(null);
```

* Bracket's syntactic sugar
  * equals to Object.create\(null\), using a null prototype as an argument

```javascript
const obj = {};
```

* Function constructor 
  * call a function and setting this of the function to a fresh new Object, and binding the prototype of that new Object to the function's prototype

```javascript
const obj = function(name) {
    this.name = name
};        
const a = new obj("hello");
```

* Function constructor + prototype

```javascript
function myObject() {};
myObject.prototype.name = "hello";
const obj = new myObject();
```

* ES6 class syntax 

```javascript
class myObject {
    constructor(name) {
        this.name = name;
    }
}
const obj = new myObject("hello");
```

* Singleton pattern 

```javascript
 const obj = new function() {this.name = "hello"};
```

## Promise

* Promise represents the eventual completion of an async operation
* It must be in one of these states
  * pending
    * initial state, not fulfilled or rejected
  * fulfilled
    * meaning that the operation completed successfully
  * rejected
    * meaning that the operation failed
* It is guaranteed that a promise object will either succeed or fail
* promise.all 
  * returns a single promise that resolves when all of the promises in the argument have resolved or when the utterable argument contains no promises
* create Promise example

```javascript
function asyncDoubble(n) {
    return new Promise((resolve, reject) => {
        if (typeof n === "number") {
            resolve(n * 2);
        } else {
            reject(new Error (n + "is not a number!"));
        }
    });
}
asyncDouble(3).then(
    data => console.log(data);
    error => console.log(error);
);
```

## Callback Hell

Callback Hell is referred to the problems caused by asynchronous AJAX calls, which means where are multiple nested callbacks. 

### How to fix:

* keep the code shallow
* modularize
* handle every single error

## How does event loop works

The Event Loop has one simple job - to monitor the Call Stack and Callback Queue. If the Call Stack is empty, it will take the first event from the queue and will push it to the Call Stack, which effectively runs it.

## Event delegation and Event bubbling

Event delegation is a technique for listening to events where you delegate a parent element as the listener for all of the events that happen inside it.

Event bubbling is what the event itself does.

## How to stop Event bubbling and capturing during Event delegation

e.stopPropagation\(\)

## Call, Apply and Bind

Call invokes the function and allows you to pass in arguments one by one.

Apply invokes the function and allows you to pass in arguments as an array.

Bind returns a new function, allowing you to pass in a this array and any number of arguments. 

## What is the drawback of creating true private methods in JavaScript

They are very memory inefficient, as a new copy of the method would be created for each instance.

## How can you make people not change the value

Object.freeze\(\)

## Significance and benefits of using Strict Mode

Since "use strict" is a way to voluntarily enforce stricter parsing and error handling on the JavaScript code at runtime. Code errors that would otherwise have been ignored or would have failed silently will now generate errors or throw exceptions. 



