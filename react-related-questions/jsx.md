# JSX

## JSX

JSX is a syntax extension to JavaScript and comes with the full power of JavaScript. JSX produces React "elements". You can embed any JavaScript expression in JSX by wrapping it in curly braces. After compilation, JSX expressions become regular JavaScript objects. This means that you can use JSX inside of if statements and for loops, assign it to variables, accept it as arguments, and return it from functions.  

## Understanding JSX

```javascript
// JSX
return (
    <div className="App"> 
        <h1>React</h1>
    </div>
);

// JavaScript
return React.createElement("div", {className: "App"}, 
    React.createElement("h1", null, "React"));
```

