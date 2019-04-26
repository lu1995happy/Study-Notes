# Leetcode Coding Questions

## Leetcode 1: Two Sum

## Leetcode 3: Longest substring without repeating characters

## Leetcode 8: String to Integer

## Leetcode 20: Valid Parentheses

## Leetcode 33: Search In Rotated Sorted Array

## Leetcode 36: Valid Sudoku

## Leetcode 39: Combination Sum

## Leetcode 46: Permutations

```javascript
const permutation = str => {
    const res = [];
    helper(str, res, "");
    return res;
};

const helper = (str, res, cur) => {
    if (str.length === cur.length) {
        res.push(cur);
        return;
    }
    for (let i = 0; i < str.length; i++) {
        if (cur.includes(str[i])) {
            continue;   
        }  
        helper(str, res, cur + str[i]);      
    }
};
```

## **Leetcode 48: Rotate Image**

## **Leetcode 73: Set Matrix Zeros**

## **Leetcode 88: Merge Sorted Array**

```javascript
const merge = (nums1, m, nums2, n) => {
    let index = m + n - 1;
    let i = m - 1;
    let j = n - 1;
    while (i >= 0 && j >= 0) {
        if (nums1[i] > nums2[j]) {
            nums1[index--] = nums1[i--];
        } else {
            nums1[index--] = nums2[j--];
        }
    }
    while (j >= 0) {
        nums1[index--] = nums2[j--];
    }
};
```

## **Leetcode 94: Binary Tree Inorder Traversal**

## **Leetcode 102: Binary Tree Level Order Traversal**

## **Leetcode 110: Balanced Binary Tree**

## **Leetcode 111: Minimum Depth of Binary Tree**

## **Leetcode 114: Flatten Binary Tree to Linked List**

## **Leetcode 118: Pascal's Triangle**

## **Leetcode 124: Binary Tree Maximum Path Sum**

## **Leetcode 125: Valid Palindrome**

```javascript
function isPalindrome(str) {
  str = str.replace(/\W/g, '').toLowerCase();
  return (str == str.split('').reverse().join(''));
}
```

## Leetcode 144: Binary Tree Preorder Traversal 

## Leetcode 151: Reverse words in a string

## Leetcode 155: Min Stack

## Leetcode 189: Rotate Array

## Leetcode 203: Remove Linked List Elements

## Leetcode 206: Reverse Linked List

## Leetcode 237: Delete Node in a Linked List

## Leetcode 238: Product of Array Except Self

## Leetcode 239: Sliding Window Maximum

## Leetcode 242: Valid Anagram

## Leetcode 268: Missing Number

## Leetcode 283: Move Zeros

## Leetcode 287: Find the Duplicate Number

## Leetcode 300: Longest Increasing Subsequence

## Leetcode 316: Remove Duplicate Letters

## Leetcode 322: Coin Change

## Leetcode 349: Intersection of two arrays

## Leetcode 394: Decode String

