# JavaScript Related Questions

## What is shallow comparison check

The shallow comparison check means that JavaScript only checks that the value's object IDs are the same, not their contents are the same. The ID here means the memory address for where JavaScript stores the information for that particular object.

## Closure

A closure is an inner function that has access to the variables in the outer \(enclosing\) function's scope chain.  Closure is a function that returns a function. It gives the access to an outer function's scope from an inner function. To use the closure, simply define a function inside another function and return it or pass it to another function. 

The closure has access to variables in three scopes

* variables in its own scope
* variables in the enclosing function's scope
* global variables

## How `this` works in JavaScript

The value of `this` depends on how the function is called. 

The following rules are applied:

* If the `new` keyword is used when calling the function, `this` inside the function is a brand new object.
* If `apply`, `call` or `bind` are used to call/create a function, `this` inside the function is the object that is passed in as the argument. 
* If a function is called as a method, such as `obj.method()`, `this` here is the object that the function is a property of. 
* If a function is invoked as a free function invocation. meaning it was invoked without any of the conditions present above, `this` is the global object. In a browser, it is the `window` object. If in strict mode \(`"use strict"`\), `this` will be `undefined` instead of the global object. 
* If multiple of the above rules apply, the rule that is higher wins and will set the `this` value.
* If the function is an ES6 arrow function, it ignores all the rules above and receives the `this` value of its surrounding scope at the time it is created. 

## Falsey values

* 0
* null
* undefined
* ""
* false
* NaN

## 4 types of scoping

* Global Scope - declared outside for any function, use it without declaring
* Function Scope - `var`
* Block Scope - `let & const` 
  * `const`: immutable variable, must be initialized
* Module Scope

## Prototypal Inheritance

All JavaScript objects have a prototype property, that is a reference to another object. When a property is accessed on an object and if the property is not found on that object, the JavaScript engine looks at the object's prototype, and the prototype's prototype and so on, until it finds the property defined on one of the prototypes or until it reaches the end of the prototype chain. This behavior simulates classical inheritance, but it is really more of delegation than inheritance. 

## The difference between `null` and `undefined`

A variable that is `undefined` is a a variable that has been declared, but not assigned a value. It is of type `undefined`. 

A variable that is `null` will have been explicitly assigned to the `null` value. It represents no value and is different from `undefined` in the sense that it has been explicitly assigned. It is of type `object`. 

`undefined == null // true`

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

## Event delegation

Event delegation is a technique involving adding event listeners to a parent element instead of adding them to the descendant elements. The listener will fire whenever the event is triggered on the descendant elements due to event bubbling up the DOM. 

The benefits of this technique are:

* Memory footprint goes down because only one single handler is needed on the parent element, rather than having to attach event handlers on each descendant.
* There is no need to unbind the handler from elements that are removed and to bind the event for new elements. 

## Event delegation and Event bubbling

Event delegation is a technique for listening to events where you delegate a parent element as the listener for all of the events that happen inside it.

Event bubbling is what the event itself does.

## How to stop Event bubbling and capturing during Event delegation

e.stopPropagation\(\)

## Lexical Scope

Lexical scope, also known as static scope, is a convention that sets the scope of a variable so that it may only be called from within the block of code in which it is defined. The scope is determined when the code is compiled. 

## Bind

The `bind` method creates a new function that, when called, has its `this` keyword set to the provided value, with a given sequence of arguments preceding any provided when the new function is called. 

## The difference for `call` and `apply`

Both are used to invoke functions and the first parameter will be used as the value of `this` within the function. However, `call` takes in comma-separated arguments as the next arguments while `apply` takes in an array of arguments as the next argument. 

## The difference for `map` and `forEach`

`forEach`: parameter is a function, apply the function to each item. It modifies the original array. 

`map`: apply the function to all elements,  function has two parameters, first is value, second is index. It returns a new array, the original array is not modified. 

## What are the pros and cons of using Promises instead of Callbacks

## What is the drawback of creating true private methods in JavaScript

They are very memory inefficient, as a new copy of the method would be created for each instance.

## How can you make people not change the value

Object.freeze\(\)

## Significance and benefits of using Strict Mode

Since "use strict" is a way to voluntarily enforce stricter parsing and error handling on the JavaScript code at runtime. Code errors that would otherwise have been ignored or would have failed silently will now generate errors or throw exceptions. 



