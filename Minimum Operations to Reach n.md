## 01. Minimum Operations to Reach n

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/find-optimum-operation4504/1?_gl=1*cf5bth*_up*MQ..*_gs*MQ..&gclid=CjwKCAjwoaLWBhAWEiwAnyituy6BIRPSzVSbPzuxODzdArhLU3u-1MdxqeT852bNC4fLpedF8ti4thoC1WQQAvD_BwE&gbraid=0AAAAAC9yBkCrlNFOQX2kNdaJgEblruCgj)

### Problem Description

**Task:** Given a number n. Find the minimum number of operations required to reach n starting from 0. You have two operations available:Double the number Add one to the numberExamples:Input: n = 8

#### Examples

##### Example 1

- **Output:**
```text
4
```
- **Explanation:** 0 + 1 = 1 -- > 1 + 1 = 2 -- > 2 * 2 = 4 -- > 4 * 2 = 8.

##### Example 2

- **Input:**
```text
n = 7
```
- **Output:**
```text
5
```
- **Explanation:** 0 + 1 = 1 -- > 1 + 1 = 2 -- > 1 + 2 = 3 -- > 3 * 2 = 6 -- > 6 + 1 = 7.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(log n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-10-09 22:44:10
- **Status:** Correct
- **Marks:** 2

```cpp
class Solution {
  public:

    int minOperation(int n) {
        // code here
        if(n==0) return 0;
        int ope;
        if(n%2==0){ ope=minOperation(n/2) + 1;}
        else { ope= minOperation(n-1)+1;}
        return ope;
    }
};
```

*Generated on: 10/9/2026, 10:44:31 PM*