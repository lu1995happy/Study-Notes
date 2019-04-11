# JavaScript Coding Questions

## Leetcode 1: Two Sum

## Leetcode 3: Longest substring without repeating characters

## Leetcode 39: Combination Sum

## Leetcode 46: Permutations

## Leetcode 151: Reverse words in a string

## Leetcode 268: Missing Number

## Leetcode 283: Move Zeros

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

