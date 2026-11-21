## 01. Smallest Subarray Sum Greater Than x

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/smallest-subarray-with-sum-greater-than-x5651/1?_gl=1*doomas*_up*MQ..*_gs*MQ..&gclid=CjwKCAiAn4XYBhA-EiwA8176Fe3vbXXJKBtxfCY6ANirLOXMJ8nMgELGEq5Yzp62tp8aeaLhUyM1NhoCfaUQAvD_BwE&gbraid=0AAAAAC9yBkDa-H57wwAHdv5_vEXuXg5nM)

### Problem Description

**Task:** Given an integer x and an array of integers, arr[]. Find the length of the smallest subarray whose sum is strictly greater than x. If no such subarray exists, return 0.Examples:Input: x = 51, arr[] = [1, 4, 45, 6, 0, 19]

#### Examples

##### Example 1

- **Output:**
```text
0
```
- **Explanation:** No subarray has a sum greater than 100. Hence, the answer is 0.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-07-11 19:48:40
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
  public:
    int smallestSubWithSum(int x, vector<int>& arr) {
        // Your code goes here
        int ans=INT_MAX;
        int n=arr.size();
        int sum=0;
        int i=0,j=0;
        while(j<n){
            sum += arr[j];
                while(sum>x){
                    ans=min(ans,j-i+1);
                    sum-=arr[i];
                    i++;
                }
        
            j++;
        }
        if(ans==INT_MAX) return 0;
        return ans;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-07-11 19:26:26
- **Status:** Correct
- **Marks:** 2

```cpp
class Solution {
  public:
    int smallestSubWithSum(int x, vector<int>& arr) {
        // Your code goes here
        int ans=INT_MAX;
        int n=arr.size();
        for(int i=0;i<n;i++){
            int sum=arr[i];
            if(sum>x) return 1;
            for(int j=i+1;j<n;j++){
                sum+=arr[j];
                if(sum>x){
                    if(ans==INT_MAX||ans>j-i+1){
                        ans=j-i+1;
                    }
                    break;
                }
            }
        }
        if(ans==INT_MAX) return 0;
        return ans;
    }
};
```

*Generated on: 11/21/2026, 10:59:46 PM*