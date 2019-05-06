# RESTful API Related Questions

## Can you map CRUD to http methods on a RESTful API

* Create - Post
* Read - Get
* Update - Put
* Delete - Delete

## The difference between PUT, POST and PATCH method



## NodeJS architecture 

Single Threaded Event Loop Model 

## How to do auth in NodeJS

Using Passport.js. Passport is authentication middleware for NodeJS. Passport can be easily dropped into any Express-based web applications. It's a comprehensive set of strategies supports authentication using a username and password, Facebook, Twitter. 

## MVC vs Flux

MVC works both in server and client side development. MVC architecture: the user updates the controller, the controller manipulates the model, the model updates the view, and finally the user can see the view.

Flux is used for building client-side web applications. It implements React's com-posable view components by utilizing a unidirectional data flow. 

## Throw vs Reject

Any time you are inside a promise callback, you can use `throw`. However, if you are in any other asynchronous callback, you must use `reject`. Moreover, `reject` does not terminate control flow like a `return` statement does. In contrast `throw` does terminate control flow.

## The advantages of NodeJS server

* JavaScript as the programming language
* Asynchronous events
* Real-time web apps
* NPM package manager
* Data sharing
* Event driven architecture

## AJAX

AJAX \(Asynchronous JavaScript and XML\) is to create asynchronous web applications. With AJAX, web applications can send data and retrieve from a server asynchronously in the background without the need to reload the entire page. 

The `XMLHttpReques`t API is frequently used for the asynchronous communication or these days, the `fetch` API. 

## AJAX - pros & cons

Advantages:

* Better interactivity. New content from the server can be changed dynamically without the need to reload the entire page. 
* Reduce connections to the server since scripts and stylesheets only have to be requested once. 
* State can be maintained on a page. JavaScript variables and DOM state will persist because the main container page was not reloaded.
* Basically most of the advantages of an SPA.

Disadvantages:

* Dynamic webpages are harder to bookmark.
* Does not work if JavaScript has been disabled in the browser.
* Some web-crawlers do not execute JavaScript and would not see content that has been loaded by JavaScript. 
* Basically most of the disadvantages of an SPA. 

## Cross Browser Compatibility Issues

Since difference browser may require different API for the same functionality, you can easily use if - else statement to define which API should be used in which environment. If the API is not working with that browser, it will return undefined. 

## Continuous Integration

Continuous Integration is a development practice that requires developers to integrate code into a shared repository several times a day. Each check-in is then verified by an automated build, allowing teams to detect problems early. 

## 5 ways to reduce the page loading speed

* Optimize Images
* Browser Caching 
* Compression
* Optimize Your CSS
* Keep the Scripts below the fold

## The workflow for JSON web token

![](../.gitbook/assets/image%20%284%29.png)

## How do you parse JSON in backend

use body-parser module



