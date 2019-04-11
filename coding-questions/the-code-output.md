# The Code Output

## How many times is the string "Hello" printed

```javascript
var x = 10;
if ((null) || (console.log("Hello")) || x > 5) {
    console.log("Hello");
}

// answer: 2
```

## What is the output of this code snippet

```javascript
function makeMultiplier(multiplier) {
  var myFunFunc = function (x) {
    return multiplier * x;
  };
  
  return myFunFunc;
}

var operation = makeMultiplier(10);
console.log(operation(10));

// answer: 100
```

## What is the output of this code snippet

```javascript
// funcObject - object instantiation & this tests
let Circle = function (radius) {
    this.radius = radius;

    this.getArea = function() {
        return Math.PI*Math.pow(this.radius, 2);
    }
}
// Note: new in call
let myCircleNew = new Circle(5);  // area - 78.5 for radius 5
console.log("myCircleNew...  logs");
console.log(myCircleNew.getArea());

// Note:  no new in call
let myCircleDirectCall = Circle(10); // area - 314.16 for radius 10
console.log("myCircleDirectCall...  logs");
console.log(myCircleDirectCall.getArea());

// answer: myCircleNew.getArea() returns 78.5;  
// myCircleDirectCall.getArea() fails with error
```

## What is the output of this code 

```javascript
var counter = 0;
var myArray = ["Yaakov", 2, {handle: "yaakovchaikin"}];
for (var i = 0; i < myArray.length; i++) {
  counter++;
}
console.log(counter);

// answer: 3
```

## What is the output of this code snippet

```javascript
// objLiteral and closures

let myLiteralObj = {
    age: 20,
    setAge: (newAge) => {
        this.age = newAge; //this指的是window，57
    },
    getAge: () => this.age, //this指的是window，57
    getSeniorStatusThroDirectAccess:  function() {
        if (this.age>55)    // Note direct attribute access，this指的是myLiteralObj，20
            return "Senior";
        else
            return("Not Senior")
    },
    getSeniorStatusThroGettor:  function() {
        if (this.getAge()>55)      // Note access via Gettor，57
            return "Senior";
        else
            return("Not Senior")
    },
}
myLiteralObj.setAge(57);
console.log("DirectAccess: " +
        myLiteralObj.getSeniorStatusThroDirectAccess());
console.log("Through gettor: " +
        myLiteralObj.getSeniorStatusThroGettor());
        
// answer: Output is “DirectAccess: Not Senior”  
// followed by “Through gettor: Senior”
```

## Immediately Invoked Function Execution: Given this code

```javascript
(function(window) {

  var obj = {};
  
  obj.dreamOn = function () {
    console.log("I want to see the global scope! Let me out!");
  };
  
  window.doer = obj;
  
 });
 
doer.dreamOn();

// answer: The attempted Immediately Invoked Function Execution (IIFE) is not being 
// invoked and passed in the window object. It's missing '(window)' Line 11 
// right before the semicolon.
```

## DOM manipulation: What will be the difference in the output between the 2 JavaScript code snippets

```javascript
<input id="name" type="text" value="Hi">

console.log(document.getElementById("name").value + " Hello world!");

console.log(document.querySelector("#name").value + " Hello world!");

// answer: no difference
```

## Events: What will the code snippet below do

```markup
...
<head>
<script>
document.addEventListener("DOMContentLoaded", function(event) {
  console.log("Yey!");
});
</script>
</head>
<body>
...
<h1>Hello!</h1>
</body>
</html>

// answer: It will output Yey! when the web page is loaded, but before 
// external resources like images are downloaded to ≠ user's machine.
```
