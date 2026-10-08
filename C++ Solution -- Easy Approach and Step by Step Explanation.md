## 01. C++ Solution || Easy Approach and Step by Step Explanation

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/maximum-frequency-1662528911/1?_gl=1*v10f9i*_up*MQ..*_gs*MQ..&gclid=CjwKCAjw_pzWBhAkEiwAwDCi1YgF5dIT91ehvCkL8cQ9iBdt34b_hAxh82dF5XW1pKT8FIaieumYhRoCsIkQAvD_BwE&gbraid=0AAAAAC9yBkCjJUfAX7UiE3m8TxD1DCtCh)

### Problem Description

**Task:** Given an integer array arr[]. In one operation, you can choose an index and increment its value by 1.Find the maximum possible frequency of any element after performing at most k operations.Examples:Input: arr[] = [2, 2, 4], k = 4

#### Examples

##### Example 1

- **Output:**
```text
3
```
- **Explanation:** Apply two increment operations on index 0 and two operations on index 1 to make arr[] = [4, 4, 4]. Frequency of 4 is 3.

##### Example 2

- **Input:**
```text
arr[] = [7, 7, 7, 7], k = 5
```
- **Output:**
```text
4
```
- **Explanation:** The frequency of 7 is already 4, so no operations are needed.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n log n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-10-08 22:58:20
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
  public:
    int maxFrequency(vector<int>& arr, int k) {
        // code here
        int n=arr.size();
        sort(arr.begin(),arr.end());
        vector<long long >prefix(n);
        prefix[0]=arr[0];
        for(int i=1;i<n;i++){
            prefix[i]=arr[i]+prefix[i-1];


        }
        int maxi=0;
        for(int i=0;i<n;i++){
            if(i-1>=0 && arr[i]==arr[i-1]){
                continue;

            }
            int index=lower_bound(arr.begin(),arr.end(),arr[i]+1)-arr.begin();
            int l=0;
            int r=index-1;
            while(l<=r){
                int mid=l+(r-l)/2;
                int sum=prefix[index-1]-((mid-1)>=0?prefix[mid-1]:0);
                int size=(index-mid)*arr[i];
                int total=size-sum;
                if(total<=k){
                    maxi=max(maxi,index-mid);
                    r=mid-1;
                }
                else{
                    l=mid+1;
                }

            }


        }
        return maxi;
    }
}; // simple binary search and prefix sum
```

*Generated on: 10/8/2026, 10:59:11 PM*