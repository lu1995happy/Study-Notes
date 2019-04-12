# JavaScript Coding Questions

## Leetcode 1: Two Sum

## Leetcode 3: Longest substring without repeating characters

## Leetcode 33: Search In Rotated Sorted Array

## Leetcode 36: Valid Sudoku

## Leetcode 39: Combination Sum

## Leetcode 46: Permutations

## **Leetcode 73: Set Matrix Zeros**

## **Leetcode 94: Binary Tree Inorder Traversal**

## **Leetcode 110: Balanced Binary Tree**

## **Leetcode 125: Valid Palindrome**

## Leetcode 144: Binary Tree Preorder Traversal 

## Leetcode 151: Reverse words in a string

## Leetcode 203: Remove Linked List Elements

## Leetcode 206: Reverse Linked List

## Leetcode 268: Missing Number

## Leetcode 283: Move Zeros

## Leetcode 300: Longest Increasing Subsequence

## Leetcode 316: Remove Duplicate Letters

## How to implement \[1, 2, 3\].double\(\) = \[2, 4, 6\]

```javascript
Array.prototype.double = function() {
    return this.map(val) => (val * 2);
}
```

## Give you an array contains duplicate numbers, print out the numbers which is duplicate 

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

## Given a LinkedList and a target value, remove the node that has the same value as the given target value 

## Write a function that sum\(2\)\(3\), sum\(2, 3\) will all return 5

```javascript
function sum(a, b) {
    if (b === undefined) {
        return function(b) {
            return a + b;
        }
    } else {
        return a + b; 
    }
}
```

## Merge two sorted array

## Given "HELLO" return "H.E.L.L.O"

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

## Query string constructor: Given an object, construct the query string of it

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

