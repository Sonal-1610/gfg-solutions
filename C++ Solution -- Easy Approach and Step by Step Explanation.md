## 01. C++ Solution || Easy Approach and Step by Step Explanation

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/bbt-counter4914/1)

### Problem Description

**Task:** Given a height h, find the maximum number of distinct balanced binary trees of height exactly h.A binary tree is balanced if, for every node, the heights of its left and right subtrees differ by at most 1. A tree with a single node has height 1. An empty tree has height 0.Note: Since the answer can be very large, return it modulo 10⁹ + 7.Examples:Input: h = 1Output: 1Explanation: Only one tree of height 1 exists i.e. a single node.Input: h = 2

#### Examples

##### Example 1

- **Output:**
```text
3
```
- **Explanation:** 3 distinct balanced trees of height 2 exist.

##### Example 2

- **Input:**
```text
h = 3
```
- **Output:**
```text
15
```
- **Explanation:** 15 distinct balanced trees of height 3 exist.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(h)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-11-06 22:16:56
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
    int mod = 1e9+7;
    int findans(int h,vector<int> &dp){
        if(h == 0 || h == 1) return 1;
        if(dp[h] != -1) return dp[h];
        int ans = (1LL*2*findans(h-1,dp)%mod*1LL*findans(h-2,dp)%mod + 1LL*findans(h-1,dp)%mod*1LL*findans(h-1,dp)%mod)%mod;
        return dp[h] = ans;

    }
  public:
    int countBT(int h) {
        // code here
        vector<int> dp(h+1,-1);
        return findans(h,dp);
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-11-06 22:16:45
- **Status:** Correct
- **Marks:** 2

```cpp
class Solution {
    int mod = 1e9+7;
    int findans(int h,vector<int> &dp){
        if(h == 0 || h == 1) return 1;
        if(dp[h] != -1) return dp[h];
        int ans = (1LL*2*findans(h-1,dp)%mod*1LL*findans(h-2,dp)%mod + 1LL*findans(h-1,dp)%mod*1LL*findans(h-1,dp)%mod)%mod;
        return dp[h] = ans;

    }
  public:
    int countBT(int h) {
        // code here
        vector<int> dp(h+1,-1);
        return findans(h,dp);
    }
};
```

*Generated on: 11/6/2026, 10:18:55 PM*