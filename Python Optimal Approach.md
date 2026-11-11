## 01. Python Optimal Approach

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/kth-distance3757/1?_gl=1*wk63f5*_up*MQ..*_gs*MQ..&gclid=Cj0KCQiAwdDXBhDuARIsAFdLukmB-Ppkak5DH0ba4xyoGwekwACAk_g06hL7SwedcDe37TwpzzMjkfMaAlL_EALw_wcB&gbraid=0AAAAAC9yBkD7aCF2B-kIwQJsylgvTJJsO)

### Problem Description

**Task:** Given an array of integers, arr[] and an integer k, check whether there exist two distinct indices i and j such that arr[i] is equal to arr[j] and the absolute difference between i and j is at most k.Examples:Input: arr[] = [1, 5, 4, 5, 1], k = 3Output: trueExplanation: The element 5 occurs at indices 1 and 3. Their distance is |3 - 1| = 2, which is less than or equal to k.Input: arr[] = [10, 2, 3, 4, 10, 5], k = 3Output: falseExplanation: The element 10 occurs at indices 0 and 4. Their distance is |4 - 0| = 4, which is greater than k. Hence, no duplicate exists within the given distance.Input: arr[] = [5, 1, 3, 2, 4], k = 3Output: falseExplanation: All elements are distinct, so no duplicate exists.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(min(n, k))

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-11-11 22:18:50
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
  public:
    bool checkWithinK(vector<int>& arr, int k) {
        // code here
        int n=arr.size();
        unordered_map<int, int>mpp;

        for(int i=0; i<n; i++){
            if(mpp.find(arr[i])!=mpp.end()){
                if(i-mpp[arr[i]]<=k) return true;
            }
            mpp[arr[i]]=i;
        }

        return false;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2024-11-02 18:47:41
- **Status:** Correct
- **Marks:** 2

```cpp
// User function template for C++

class Solution {
  public:

    bool checkDuplicatesWithinK(vector<int>& arr, int k) {
        // your code
         unordered_map<int,int>mp;
        for(int i=0;i<arr.size();i++){
            if(mp.find(arr[i])!=mp.end()){
                if(i-mp[arr[i]]<=k){
                    return true;
                }
            }
            else{
              mp[arr[i]]=i;
            }
            
        }
        return false;
    
    }
};
```

*Generated on: 11/11/2026, 10:19:13 PM*