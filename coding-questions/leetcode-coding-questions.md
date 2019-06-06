# Leetcode Coding

## Leetcode 1: Two Sum

```javascript
const twoSum = (nums, target) => {
    let map = new Map();
    let res = [];
    for (let i = 0; i < nums.length; i++) {
        if (map.has(target - nums[i])) {
            res[0] = i;
            res[1] = map.get(target - nums[i]);
            return res;
        } else {
            map.set(nums[i], i);
        }
    }
    return res;
}
```

## Leetcode 3: Longest substring without repeating characters

```javascript
const lengthOfLongestSubstring = (s) => {
    if (s.length === 0) {
        return 0;
    }
    let res = 0;
    let map = new Map();
    for (let i = 0, j = 0; i < s.length; i++) {
        if (map.has(s[i])) {
            j = Math.max(j, map.get(s[i]) + 1);
        }
        map.set(s[i], i);
        res = Math.max(res, i - j + 1);
    }
    return res;
}
```

## Leetcode 6: ZigZag Conversion

## Leetcode 15: 3Sum

## Leetcode 20: Valid Parentheses

```javascript
const isValid = (s) => {
    if (s.length % 2 !== 0) {
        return false;
    }
    let stack = [];
    for (let i = 0; i < s.length; i++) {
        if (s[i] === "(") {
            stack.push(")");
        } else if (s[i] === "[") {
            stack.push("]");
        } else if (s[i] === "{") {
            stack.push("}");
        } else if (stack.length === 0 || stack.pop() !== s[i]) {
            return false;
        }
    }
    return stack.length === 0;
}
```

## Leetcode 33: Search In Rotated Sorted Array

```javascript
const search = (nums, target) => {
    let low = 0, high = nums.length - 1;
    while (low < high) {
        let mid = Number.parseInt((low + high) / 2);
        if (nums[mid] === target) {
            return mid;
        }
        if (nums[low] <= nums[mid]) {
            if (target >= nums[low] && target < nums[mid]) {
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        } else {
            if (target > nums[mid] && target <= nums[high]) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }
    }
    return nums[low] === target ? low : -1;
}
```

## Leetcode 36: Valid Sudoku

## Leetcode 39: Combination Sum

```javascript
const combinationSum = (candidates, target) => {
    const backtrack = (nums, remain, res, list, start) => {
        if (remain < 0) {
            return res;
        }
        if (remain === 0) {
            res.push(list.slice());
            return res;
        }
        for (let i = start; i < nums.length; i++) {
            list.push(nums[i]);
            backtrack(nums, remain - nums[i], res, list, i);
            list.pop();
        }
        return res;
    }
    return backtrack(candidates, target, [], [], 0);
}
```

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

## **Leetcode 53: Maximum Subarray**

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

```javascript
function TreeNode(val) {
    this.val = val;
    this.left = this.right = null;
}

// Binary Tree In-order Traversal: (left, root, right)

// BFS
const inorderTraversal = (root) => {
  const res = [], stack = [];
  while (root || stack.length) {
    if (root) {
      stack.push(root);
      root = root.left;
    } else {
      root = stack.pop();
      res.push(root.val);
      root = root.right;
    }
  }
  return res;
}

// DFS
const inorderTraversal = (root) => {
    const res = [];
    dfs(root, res);
    return res;
}

const dfs = (root, res) => {
    if (!root) {
        return;
    }
    dfs(root.left, res);
    res.push(root.val);
    dfs(root.right, res);
}
```

## **Leetcode 100: Same Tree**

## **Leetcode 102: Binary Tree Level Order Traversal**

```javascript
// BFS
const levelorderTraversal = (root) => {
    const queue = [], res = [];
    if (!root) {
        return res;
    }
    queue.push(root);
    while (queue.length) {
        const temp = [];
        const size = queue.length; 
        for (let i = 0; i < size; i++) {
            const node = queue.shift();
            temp.push(node.val);
            if (node.left) {
                queue.push(node.left);
            }
            if (node.right) {
                queue.push(node.right);
            }
        }
        res.push(temp);
    }
    return res;
}

// DFS
const levelorderTraversal = (root) => {
  const res = [];
  dfs(res, root, 0);
  return res;
}

const dfs = (res, root, height) => {
  if (!root) {
    return;
  }
  if (height >= res.length) {
    res.push([]);
  }
  res[height].push(root.val);
  dfs(res, root.left, height + 1);
  dfs(res, root.right, height + 1);
}
```

## **Leetcode 110: Balanced Binary Tree**

## **Leetcode 111: Minimum Depth of Binary Tree**

## **Leetcode 114: Flatten Binary Tree to Linked List**

## **Leetcode 118: Pascal's Triangle**

## **Leetcode 121: Best Time to Buy and Sell Stock**

## **Leetcode 124: Binary Tree Maximum Path Sum**

## **Leetcode 125: Valid Palindrome**

```javascript
function isPalindrome(str) {
  str = str.replace(/\W/g, '').toLowerCase();
  return (str == str.split('').reverse().join(''));
}
```

## Leetcode 139: Work Break

## Leetcode 144: Binary Tree Preorder Traversal 

```javascript
// Binary Tree Pre-order Traversal: (root, left, right)

// BFS
const preorderTraversal = (root) => {
  const res = [], stack = [];
  while (root || stack.length) {
    if (root) {
      res.push(root.val);
      stack.push(root);
      root = root.left;
    } else {
      root = stack.pop();
      root = root.right;
    }
  }
  return res;
}

// DFS 
const preorderTraversal = (root) => {
    const res = [];
    dfs(root, res);
    return res;
}

const dfs = (root, res) => {
    if (!root) {
        return;
    }
    res.push(root.val);
    dfs(root.left, res);
    dfs(root.right, res);
}
```

## Leetcode 145: Binary Tree Postorder Traversal

```javascript
// Binary Tree Post-order Traversal: (left, right, root)

// BFS
const postorderTraversal = (root) => {
  const stack = [], res = [];
  while (root || stack.length) {
    if (root) {
      stack.push(root);
      res.unshift(root.val);
      root = root.right;
    } else {
      root = stack.pop();
      root = root.left;
    }
  }
  return res;
}

// DFS
const postorderTraversal = (root) => {
    const res = [];
    dfs(root, res);
    return res;
}

const dfs = (root, res) => {
    if (!root) {
        return;
    }
    dfs(root.left, res);
    dfs(root.right, res);
    res.push(root.val);
}
```

## Leetcode 148: Sort List

## Leetcode 151: Reverse words in a string

## Leetcode 155: Min Stack

## Leetcode 189: Rotate Array

## Leetcode 198: House Robber

## Leetcode 203: Remove Linked List Elements

## Leetcode 206: Reverse Linked List

## Leetcode 207: Course Schedule

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

## Leetcode 412: Fizz Buzz

```javascript
const fizzBuzz = (n) => {
    const res = [];
    for (let i = 1; i <= n; i++) {
        if (i % 3 === 0 && i % 5 === 0) {
            res.push("FizzBuzz");
        } else if (i % 3 === 0) {
            res.push("Fizz");
        } else if (i % 5 === 0) {
            res.push("Buzz");
        } else {
            res.push(i.toString());
        }
    }
    return res;
}
```

## Leetcode 680: Valid Palindrome II

## Leetcode 695: Max Area of Island

## Leetcode 805: Split Array With Same Average

