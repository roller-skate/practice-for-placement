# Unique Binary Search Trees

![Difficulty](https://img.shields.io/badge/Difficulty-Medium-yellow)

## Problem

Given an integer `n`, return  *the number of structurally unique  **BST'** s (binary search trees) which has exactly* `n` *nodes of unique values from*  `1`  *to*  `n`.

 

Original
Java
 **Example 1:** 

```
Input: n = 3
Output: 5

```

 **Example 2:** 

```
Input: n = 1
Output: 1

```

 

 **Constraints:** 

- 1 <= n <= 19

## Solution

**Language:** Java  
**Runtime:** 0 ms (beats 100.00%)  
**Memory:** 41.9 MB (beats 51.40%)  
**Submitted:** 2026-11-16T17:59:33.952Z  

```java
class Solution {
    public int numTrees(int n) {
        int[] uniqTree = new int[n + 1];
        for (int i = 0; i <= n; i++) {
            uniqTree[i] = 1;
        }

        for (int nodes = 2; nodes <= n; nodes++) {
            int total = 0;
            for (int root = 1; root <= nodes; root++) {
                total += uniqTree[root - 1] * uniqTree[nodes - root];
            }
            uniqTree[nodes] = total;
        }

        return uniqTree[n];        
    }
}
```

---

[View on LeetCode](https://leetcode.com/problems/unique-binary-search-trees/)