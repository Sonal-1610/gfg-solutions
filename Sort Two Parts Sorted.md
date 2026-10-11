## 01. Sort Two Parts Sorted

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/sort-the-half-sorted2157/1?_gl=1*54k0o1*_up*MQ..*_gs*MQ..&gclid=CjwKCAjw56zWBhB0EiwAdPOQOWJ86ye0B2pSTKvqleiOf5AUrb_1tGFrjws56JcXFmVjLXCHgGbhwBoCYQ8QAvD_BwE&gbraid=0AAAAAC9yBkBjDonsCtoMBaJHG0z3Q4EbI)

### Problem Description

**Task:** Given an integer array arr[] where the two parts around a break point are individually sorted, merge them into a single sorted array. The break point can be anywhere in the array, including at the beginning or end.Examples:Input: arr[] = [2, 3, 8, -1, 7, 10]

#### Examples

##### Example 1

- **Output:**
```text
[10, 20, 30]
```
- **Explanation:** One part is empty and the other part is whole array which is already sorted.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-10-11 22:24:52
- **Status:** Correct
- **Marks:** 2

```cpp
class Solution {
  public:
    void mergeTwoParts(vector<int>& arr) {
        // code here
        sort(arr.begin(),arr.end());
        
    }
};
```

*Generated on: 10/11/2026, 10:25:38 PM*