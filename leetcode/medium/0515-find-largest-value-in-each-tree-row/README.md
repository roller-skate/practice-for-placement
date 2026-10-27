# Find Largest Value in Each Tree Row

![Difficulty](https://img.shields.io/badge/Difficulty-Medium-yellow)

## Problem

Given the `root` of a binary tree, return  *an array of the largest value in each row*  of the tree  **(0-indexed)**.

 

 **Example 1:** 

```
Input: root = [1,3,2,5,3,null,9]
Output: [1,3,9]

```

 **Example 2:** 

```
Input: root = [1,2,3]
Output: [1,3]

```

 

 **Constraints:** 

- The number of nodes in the tree will be in the range [0, 104].
- -231 <= Node.val <= 231 - 1

## Solution

**Language:** Java  
**Runtime:** 2 ms (beats 90.64%)  
**Memory:** 46.8 MB (beats 82.13%)  
**Submitted:** 2026-10-27T09:41:11.602Z  

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
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public List<Integer> largestValues(TreeNode root) {
        if (root == null) {
            return new ArrayList<Integer>();
        }
        
        List<Integer> ans = new ArrayList<Integer>();
        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(root);
        
        while (!queue.isEmpty()) {
            int currentLength = queue.size();
            int currMax = Integer.MIN_VALUE;
            
            for (int i = 0; i < currentLength; i++) {
                TreeNode node = queue.remove();
                currMax = Math.max(currMax, node.val);
                
                if (node.left != null) {
                    queue.add(node.left);
                }
                
                if (node.right != null) {
                    queue.add(node.right);
                }
            }
            
            ans.add(currMax);
        }
        
        return ans;
    }
}
```

---

[View on LeetCode](https://leetcode.com/problems/find-largest-value-in-each-tree-row/)