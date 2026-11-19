# Count Complete Tree Nodes

![Difficulty](https://img.shields.io/badge/Difficulty-Medium-yellow)

## Problem

Given the `root` of a  **complete**  binary tree, return the number of the nodes in the tree.

According to  **Wikipedia**, every level, except possibly the last, is completely filled in a complete binary tree, and all nodes in the last level are as far left as possible. It can have between `1` and `2h` nodes inclusive at the last level `h`.

Design an algorithm that runs in less than `O(n)` time complexity.

 

 **Example 1:** 

```
Input: root = [1,2,3,4,5,6]
Output: 6

```

 **Example 2:** 

```
Input: root = []
Output: 0

```

 **Example 3:** 

```
Input: root = [1]
Output: 1

```

 

 **Constraints:** 

- The number of nodes in the tree is in the range [0, 5 * 104].
- 0 <= Node.val <= 5 * 104
- The tree is guaranteed to be complete.

## Solution

**Language:** Java  
**Runtime:** 0 ms (beats 100.00%)  
**Memory:** 48.9 MB (beats 73.03%)  
**Submitted:** 2026-11-19T03:59:25.382Z  

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left;
 *         this.right;
 *     }
 * }
 */
class Solution {
    int height(TreeNode root){
        return root == null ?-1 : 1+ height(root.left);
    }
    public int countNodes(TreeNode root) {
        int nodes =0, h = height(root);
        while (root != null){
            if(height(root.right)== h-1){
                nodes += 1 <<h;
                root = root.right;
            } else {
                nodes += 1 << h-1;
                root = root.left;
            }
            h--;
        }
        return nodes;
    }
}
```

---

[View on LeetCode](https://leetcode.com/problems/count-complete-tree-nodes/)