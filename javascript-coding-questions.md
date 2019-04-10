# JavaScript Coding Questions

## Leetcode 1: Two Sum

## Leetcode 3: Longest substring without repeating characters

## Leetcode 46: Permutations

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

## Given a LinkedList and a target value, remove the node that has the same value as the given target value 

## Write a function sum\(2\)\(3\), sum\(2, 3\) which will return 5

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

