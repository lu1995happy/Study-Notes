# JavaScript Coding Questions

## How to implement \[1, 2, 3\].double\(\) = \[2, 4, 6\]

```javascript
Array.prototype.double = function() {
    return this.map(val) => (val * 2);
}
```

## Given an array with integer and K, return top K largest element in the array 

## Write a function to find the most repeated number in the array 

```javascript
const findMost = (arr) => {
  if (arr.length === 0) {
    return null;
  }
  let map = {};
  for (let i = 0; i < arr.length; i++) {
    if (map[arr[i]]) {
      map[arr[i]]++;
    } else {
      map[arr[i]] = 1;
    }
  }
  let keys = Object.keys(map);
  let times = 0, mostNum = 0;
  for (let i = 0; i < keys.length; i++) {
    if (times < map[keys[i]]) {
      times = map[keys[i]];
      mostNum = keys[i];
    }
  }
  return mostNum;
} 
```

## Write a function that sum\(2\)\(3\), sum\(2, 3\) will all return 5

```javascript
// Method 1:
function sum(x, y) {
    if (y !== undefined) {
        return x + y;
    } else {
        return function(y) {
            return x + y; 
        }
    }
}

// Method 2:
function sum(x) {
    if (arguments.length === 2) {
        return arguments[0] + arguments[1];
    }  else {
        return function(y) {
            return x + y;
        }
    }
}
```

## Given "HELLO" return "H.E.L.L.O"

```javascript
const helper = str => {
    return str.split("").join(".");
}
```

## Write a function that add\(\) = 0, add\(2\)\(\) = 2, add\(2\)\(2\)\(\) = 4, add\(2\)\(3\)\(4\)\(5\)\(\) = 14

```javascript
function add(a) {
    if (a === undefined) {
        return 0;
    }
    let sum = a;
    return add2(b) {
        if (b === undefined) {
            return sum;
        } else {
            sum += b;
        }
        return add2;
    }
}
```

## Stringify the object into URL: Given an object, construct the query string of it

```javascript
// Example:
const obj = {
   name: "lynn",
   gender: "female"
}
return "?name=lynn&gender=female"
```

```javascript
const constructString = (obj) => {
  let res = "?";
  for (let key in obj) {
    res += key + "=" + obj[key] + "&";
  }
  return res.slice(0, -1);
}

// using Reduce
const helper = obj => {
  return Object.entries(obj).reduce((prev, curr) => prev 
    + curr[0] + "=" + curr[1] + "&", "?").slice(0, -1);
}
```

## Flatten Array: **Change \["a", "b", \["c", "d", \["e", "f"\]\], "g"\] to \["a", "b", "c", "d", "e", "f", "g"\]**

```javascript
const flattenArray = (arr) => {
  for (let i = 0; i < arr.length; i++) {
    if (Array.isArray(arr[i])) {
      arr = [...arr.slice(0, i), ...arr[i], ...arr.slice(i + 1)];
    }
  }
  return arr;
}

// using Reduce
const flatten = arr => {
   return arr.reduce(function (flat, toFlatten) {
       return flat.concat(Array.isArray(toFlatten) ? flatten(toFlatten) : toFlatten);
   }, []);
}
```

## **Flatten Object: Change** \[{a: 1}, {b: 2, c: 3}, {d: 4}\] to {a:1, b:2, c:3, d:4}

```javascript
const flatten = Object.assign(...arr);
```

## **Flatten Nested Object: Change {a:2, b:{c: 3}} to {a: 2, c: 3}**

```javascript
const flatten = obj => {
  const flattened = {};
  Object.keys(obj).forEach((key) => {
    if (typeof obj[key] === "object") {
      Object.assign(flattened, flatten(obj[key]));
    } else {
      flattened[key] = obj[key];
    }
  });
  return flattened;
};
```

## **Merge Two Object**

```javascript
const obj1 = {a: 1, b: 2};
const obj2 = {b: 3, c: 3};
const merge = (obj1, obj2) => {
    return Object.assign(obj2, obj1);
}
```

## **Add "age" key to each object**

```javascript
const test = [
    {name: "harry"},
    {name: "bruce"}
];

test.map(e => Object.assign(e, {age: 24}));
test.map(e => e = {...e, {age: 24}});
```

## **Given array \[4, 5, 5, 2, 6\] indicate a piece of chocolate, each element represent the sweetness\(1 - 10\) of chocolate, you want to share the chocolate with two other friends\(divide array into three subarrays\), you want to make sure that your two friends get sweetest, how to divide the array so that you can get sweetest among all those division ways \(find sweetest value among the least sweet ways\)**

```text
4 | 5 | 5  2  6   ->  4
4 | 5  5 | 2  6   ->  4
4 | 5  5  2 | 6   ->  4
4  5 | 5 | 2  6   ->  5
4  5 | 5  2 | 6   ->  6   answer: 6
4  5  5 | 2 | 6   ->  2       

// Leetcode 410   
```

## Write a function, which passing an ID would return the options for that ID

```javascript
var linkGroups = [
    {id: "sports", options: ["soccer", "basketball"]}, 
    {id: "fish", options: ["salmon", "goldfish"]}
];

const helper = id => {
    return linkGroups.filter(item => item.id === id)[0].options;
}
```

## What if there are multiple options and you want to return them in one array

```javascript
var linkGroups = [
    {id: "sports", options: ["soccer", "basketball"]}, 
    {id: "fish", options: ["salmon", "goldfish"]}, 
    {id: "fish", options: ["trout", "bass"]}
];

const helper = id => {
    return linkGroups.filter(item => item.id === id).map(item => item.options);
}
```

## Write a function, which returns all the elements are string

```javascript
const arr=["bird",1,3,{a:1},"cat","dog",56];

const helper = arr => {
    return arr.filter(item => typeof item === "string");
}
```

## Write a function, which uses IIFE to get output 0,1,2,3,4

```javascript
for (var i = 0; i < 5; i++) {
    (inner = i => {
        setTimeout(() => console.log(i))
    })(i);
}
```

## Write a function, which returns the HTML elements that background color not equal to the color

```javascript
const getHTML = () => {
    let res = "";
    let arr = document.getElementsByTagName("td");
    for (let i = 0; i < arr.length; i++) {
        if (arr[i].style.color !== arr[i].style["backgroundColor"]) {
            res += arr[i].innerHTML();
        }
    }
    return res;
}
```

## Implement the forEach function

```javascript
Array.prototype.myForEach = (callback) => {
    for (let i of this) {
        callback(i);
    }
};
```

## Implement the map function

```javascript
Array.prototype.myMap = (callback) => {
    let res = [];
    for (let i of this) {
        res.push(callback(i));
    }
    return res;
}
```

## Implement the reduce function

```javascript
const reduce = (arr, initialValue = 0, callback) => {
    let curValue = initialValue;
    for (let i of arr) {
        curValue = callback(curValue, i);
    }
    return curValue;
}
```

## Sort the String first by length, then by alphabetical order. Capitalize the first character, end with "."

```javascript
// example: "bc a bb cdf cab." =>  “A bb bc cab cdf."

const arrange = (sentence) => {
  sentence = sentence.substring(0, sentence.length - 1);
  let map = new Map();
  let arr = sentence.split(" ");
  for(let word of arr){
    let len = word.length;
    if(map.get(len) === undefined){
      map.set(len, [word]);
    } else {
      map.set(len, [...map.get(len), word]);
    }
  }
  let new_arr = [...map];
  new_arr.sort((a,b) => a[0] - b[0]);
  
  let result = "";
  new_arr[0][1][0] = new_arr[0][1][0].charAt(0).toUpperCase() + new_arr[0][1][0].slice(1);
  for(let i = 0; i < new_arr.length; i++){
    for(let j = 0; j < new_arr[i][1].length; j++){
      result += new_arr[i][1][j];
      if(new_arr.length - 1 === i && j === new_arr[i][1].length - 1){
        result += '.';
      } else {
        result += ' ';
      }
    } 
  }
  return(result);
}
```

## Write a function, which could be only called once

```javascript
const something = (function() {
    let memory = false;
    return function() {
        if (!memory) {
            memory = true;
            console.log("It works!");
        }
    };
})();
```

## **Write the class “Calc” to make below codes work: Let a = new Calc\(2\); a.add\(2\).multiple\(3\).value\(\) = 12**

```javascript
class Calc {
    constructor(value) {
        this.value = value;
    }
    
    add(value) {
        this.value += value;
        return this;
    }
    
    multiple(value) {
        this.value *= value;
        return this;
    }
    
    getValue() {
        return this.value;
    }
}
```

## Write a function, which returns false for nulls, arrays, and functions, but true for objects

```javascript
console.log((obj !== null) && (obj.constructor === Object));
```

## Create a function that, given a DOM Element on the page, will visit the element itself and _all_ of its descendents \(not just its immediate children\). For each element visited, the function should pass that element to a provided callback function.

```javascript
function Traverse(p_element,p_callback) {
   p_callback(p_element);
   var list = p_element.children;
   for (var i = 0; i < list.length; i++) {
       Traverse(list[i],p_callback);  // recursive call
   }
}
```

## **Write a function \(getEvenAndSort\), which can be called on any array, and it returns the subarray of only the even numbers, but sorted.**

```javascript
Array.prototpye.getEvenAndSort = function() {
    let arr = [...this];
    arr.sort((a, b) => a - b);
    return arr.filter(num => num % 2 === 0);
}
```

## **Create a chain of promises that will do this on each step of the chain: Step 1 - Authenticate user \(auth\(\)\), Step 2 - Get getAddress \(getAddress\(\)\), Step 3 - Edit address and edit email in parallel \(editAddress\(\), editEmail\(\)\), Step 4 – print success on the console**

```javascript
auth
    .then(() => {
        getAddress();
    })
    .then(() => {
        return Promise.all([editAddress(), editEmail()]);
    })
    .then(() => {
        console.log("success");
})
```

## Given a 7\*3 grid of characters output a decoded message. The  message for the following would be IROCKED.

```javascript
const message = [
  ['I', 'B', 'C', 'A', 'K', 'E', 'A'],
  ['D', 'R', 'F', 'C', 'A', 'E', 'A'],
  ['G', 'H', 'O', 'E', 'L', 'A', 'D']
];

const decode = message => {
  const m = message.length;
  const n = message[0].length;
  let j = 0;
  let down = -1;
  let res = [];
  for (let i = 0; i < n; i++) {
    res.push(message[j][i]);
    if (j === 0 || j === m - 1) {
      down = -down;
    }
    j += down;
  }
  return res;
};
```

## Write a function to remove the duplicate list items, when the button is clicked using jQuery

```markup
<ul>
  <li>Cats</li>
  <li>Dogs</li>
  <li>Birds</li>
  <li>Cats</li>
  <li>Bears</li>
</ul>
<button onClick="">Remove Duplicates</button>
```

```javascript
$("button").click(function() {
  const seen = {};
  $('li').each(function() {
    const txt = $(this).text();
    if (seen[txt])
      $(this).remove();
    else
      seen[txt] = true;
  });
  return false;
});

// using Pure JavaScript
document.getElementsByTagName("button")[0].addEventListener("click", () => {
  const seen = [];
  const lists = document.getElementsByTagName("li");
  for (let i = 0; i < lists.length; i++) {
    const text = lists[i].innerText;
    if (seen[text]) {
      lists[i].remove();
    } else {
      seen[text] = true;
    }
  }
  return false;
})
```

## Write a function that given a time T in seconds, convert it into a string in the format "&lt;hours&gt;h&lt;minutes&gt;m&lt;seconds&gt;s"

```javascript
const solution = T => {
    const hr = Math.floor(T/3600);
    T %= 3600;
    const min = Math.floor(T/60);
    const sec = T % 60;
    return hr + "h" + min + "m" + sec + "s";
}
```

## Write a function that given a DOM tree, returns the maximum depth of nested &lt;ul&gt;/&lt;ol&gt; lists

```javascript
const solution = () => {
    let maxDepth = 0, temp, parents;
    $("ol, ul").each(function() {
        parents = $(this).parents("ol, ul");
        temp = parents ? parents.length + 1 : 1;
        maxDepth = temp > maxDepth ? temp : maxDepth;
    });
    return maxDepth;
}
```

## Write a function that given a DOM tree representing an HTML document, returns a string containing all visible letters, read in row-major order.

```javascript

    let res = "";
    $("td").each(function() {
        if ($(this).css("color") !== $(this).css("background-color")) {
            res += $(this).html();
        }
    });
    return res;
}
```

## Implement a Class, which has add, get and delete functions

```javascript
class CountMe {
    constructor() {
        this.map = new Map();
    }
    add(str) {
        if (this.map.has(str)) {
            this.map.set(str, this.map.get(str) + 1);
        } else {
            this.map.set(str, 1);
        }
    }
    
    get(str) {
        if (this.map.has(str)) {
            return this.map.get(str);
        } else {
            return 0;
        }
    }
    
    delete(str) {
        if (this.map.has(str)) {
            this.map.set(str, this.map.get(str) - 1);
        }
    }
}
```

## Write a function that accomplish iterator function

```javascript
var myIterator = iterator("test");
myIterator.next();
myIterator.next();

function iterator(str) {
    let i = 0; 
    return {
        next: () => {
            return i < str.length ? str[i++] : "no more element";
        }
    };
};
```

## Write a function that deletes the key in the nested Object

```javascript
const deleteNode = (obj, node) => {
  helper(obj, node, obj);
  return obj;
}

const helper = (obj, node, curNode) => {
  if (!curNode.children) {
    return;
  }
  if (curNode.children.map(e => e.name).includes(node.name)) {
      curNode.children = curNode.children.filter(e => e.name !== node.name);
      return;
  }

  curNode.children.forEach(e => {
      helper(obj, node, e);
  })
}

console.log(JSON.stringify(deleteNode(obj, {name: 'bird'})));
```

## Write a function gamble\(N, K\) that N is the final gold and K is the round that he all-in

```javascript
const gamble = (N, K) => {
    let res = 0;
    while (N !== 1 && K) {
        res++;
        if (N % 2 === 0) {
            N /= 2;
            K--;
        } else {
            N--;
        }
    }
    return res + N - 1;
}
```

## Use NodeJS to write a function that send response as "Hello"

```javascript
app.get("/test", (req, res, err) => {
    if (err) {
        res.status(500).json({err});
    } else {
        res.status(200).json({message: "Hello"});
    }
});

// use the next middleware
app.get("/test", (req, res, err) => {
    req.message = "Hello";
    next();
}, (req, res, next) => {
    res.status(200).json({message: req.message});
});
```

## English number to normal number

```javascript
const wordToNumber = word => {
  if (word === "zero") {
    return 0;
  }
  const units = ["thousand", "million", "billion"];
  const nums = [
    "",
    "one",
    "two",
    "three",
    "four",
    "five",
    "six",
    "seven",
    "eight",
    "nine",
    "ten",
    "eleven",
    "twelve",
    "thirteen",
    "fourteen",
    "fifteen",
    "sixteen",
    "seventeen",
    "eighteen",
    "nineteen"
  ];
  const tens = [
    "",
    "",
    "twenty",
    "thirty",
    "forty",
    "fifty",
    "sixty",
    "seventy",
    "eighty",
    "ninety"
  ];
  const words = word.split(" ");
  let res = "";
  for (let i = words.length - 1; i >= 0; i--) {
    const curWord = words[i];
    if (curWord === "negative") {
      res = "-" + res;
      return Number.parseInt(res);
    }
    const indexOfNums = nums.indexOf(curWord);
    if (indexOfNums !== -1) {
      res = indexOfNums + res;
      if (i - 1 >= 0 && indexOfNums <= 9 && tens.indexOf(words[i - 1]) !== -1) {
        res = tens.indexOf(words[i - 1]) + res;
        i--;
      }
    } else {
      const indexOfTens = tens.indexOf(curWord);
      if (indexOfTens !== -1) {
        res = indexOfTens + "0" + res;
      } else {
        if (curWord === "hundred") {
          while (res.length % 3 !== 2) {
            res = "0" + res;
          }
        } else {
          while (res.length != (units.indexOf(curWord) + 1) * 3) {
            res = "0" + res;
          }
        }
      }
    }
  }
  return Number.parseInt(res);
};
```

## Event Capture Related Question

```markup
<ul id="list">
  <li class="item-1">Item 1</li>
  <li class="item-2">Item 2</li>
  <li class="item-3">Item 3</li>
  <li class="item-4">Item 4</li>
  <li class="item-5">Item 5</li>
</ul>
```

```javascript
document.getElementById("list").addEventListener("click", function(){
  console.log("list is clicked");
});

for (let i = 1; i <= 5; i++) {
  liDomArr = document.getElementsByClassName(`item-${i}`);
  liDomArr[0].addEventListener("click", function(event){
    if (i === 5) {
      event.stopPropagation();
    } 
    console.log(`item ${i} is clicked`);
  });
}
```

## Deep Clone Object

```javascript
JSON.parse(JSON.stringify(obj));
```

