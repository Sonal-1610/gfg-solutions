## 01. Minimum Sum Subarray

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/smallest-sum-contiguous-subarray/1)

### Problem Description

**Task:** Given an array arr[], find the minimum sum of a subarray containing atleast one element in the given array.Examples:Input: arr[] = [3, -4, 2, -3, -1, 7, -5]

#### Examples

##### Example 1

- **Output:**
```text
1
```
- **Explanation:** The subarray [1] has the minimum sum, which is 1.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-10-21 22:41:34
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
  public:
    int minSubarraySum(vector<int> &arr) {
        // code here
        int n=arr.size();
        int mini=1e9;
        int sum=0;

        for(int i=0; i<n; i++){
            sum+=arr[i];
            mini=min(mini, sum);
            if(sum>0) sum=0;
        }

        return mini;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-21 22:29:22
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
  public:
    int minSubarraySum(vector<int> &arr) {
        // code here
        int n=arr.size();
        int mini=1e9;
        int sum=0;

        for(int i=0; i<n; i++){
            sum+=arr[i];
            mini=min(mini, sum);
            if(sum>0) sum=0;
        }

        return mini;
    }
};
```

*Generated on: 10/21/2026, 10:42:50 PM*