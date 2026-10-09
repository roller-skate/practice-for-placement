# Balanced Binary Tree

![Difficulty](https://img.shields.io/badge/Difficulty-Easy-green)

## Problem

Given a binary tree, determine if it is  **height-balanced**.

 

 **Example 1:** 

```
Input: root = [3,9,20,null,null,15,7]
Output: true

```

 **Example 2:** 

```
Input: root = [1,2,2,3,3,null,null,4,4]
Output: false

```

 **Example 3:** 

```
Input: root = []
Output: true

```

 

 **Constraints:** 

- The number of nodes in the tree is in the range [0, 5000].
- -104 <= Node.val <= 104

## Solution

**Language:** Java  
**Runtime:** 1 ms (beats 31.42%)  
**Memory:** 46.5 MB (beats 5.19%)  
**Submitted:** 2026-10-09T18:23:25.449Z  

```java
class Solution {
    public boolean isBalanced(TreeNode root) {
        int[] result = dfs(root);
        return result[0] == 1;        
    }

    private int[] dfs(TreeNode node) {
        if (node == null) return new int[]{1, 0}; // {isBalanced (1 for true, 0 for false), height}
        
        int[] left = dfs(node.left);
        int[] right = dfs(node.right);
        
        boolean isBalanced = left[0] == 1 && right[0] == 1 && Math.abs(left[1] - right[1]) <= 1;
        
        return new int[]{isBalanced ? 1 : 0, 1 + Math.max(left[1], right[1])};
    }    
}
```

---

[View on LeetCode](https://leetcode.com/problems/balanced-binary-tree/)