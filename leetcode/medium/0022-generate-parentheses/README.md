# Generate Parentheses

![Difficulty](https://img.shields.io/badge/Difficulty-Medium-yellow)

## Problem

Given `n` pairs of parentheses, write a function to  *generate all combinations of well-formed parentheses*.

 

 **Example 1:** 

```
Input: n = 3
Output: ["((()))","(()())","(())()","()(())","()()()"]

```

 **Example 2:** 

```
Input: n = 1
Output: ["()"]

```

 

 **Constraints:** 

- 1 <= n <= 8

## Solution

**Language:** Java  
**Runtime:** 3 ms (beats 15.26%)  
**Memory:** 44.9 MB (beats 23.77%)  
**Submitted:** 2026-10-08T17:42:22.556Z  

```java
class Solution {
    List<String> res = new ArrayList<>();

    public List<String> generateParenthesis(int n) {
        if (n-- == 1) return List.of("()");
        dfs(n, n, "(");

        return res;
    }

    private void dfs(int O, int C, String s) {
        if (O == 0 && C == 0) {
            res.add(s + ")");
            return;
        }

        if (O > 0)
            dfs(O - 1, C, s + "(");

        if (C >= O)
            dfs(O, C - 1, s + ")");
    }
}
```

---

[View on LeetCode](https://leetcode.com/problems/generate-parentheses/)