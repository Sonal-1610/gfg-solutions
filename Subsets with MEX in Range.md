## 01. Subsets with MEX in Range

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/crazy-subsets--131708/1?_gl=1*zsxjhn*_up*MQ..*_gs*MQ..&gclid=CjwKCAjwgJHXBhBGEiwAHohJq3ihkf7VJH9GS9VXLL2ACvNyLI6WTNi5N3h5iQgKdCADMnIUst9TlBoCVOYQAvD_BwE&gbraid=0AAAAAC9yBkBy_-PgBjANCL31Is2oE_o2O)

### Problem Description

**Task:** Given an array arr[] of integers and a range [l, r], count the number of subsets whose Minimum Excluded (MEX) value lies within the given range, inclusive.Minimum Excluded (or MEX) of a subset is the smallest non-negative integer that is not present in the subset. An empty subset has Minimum Excluded as zero. Since the answer can be very large, return the answer modulo 10⁹ + 7.Examples:Input: arr[] = [2, 0, 1, 0], l = 1, r = 2

#### Examples

##### Example 1

- **Output:**
```text
9
```
- **Explanation:** The subsets whose MEX lies in the range [1, 2] are counted as follows:MEX = 1: The subsets must contain at least one 0 and must not contain 1. These subsets are [0] (2 ways), [2, 0] (2 ways), [0, 0] (1 way), and [2, 0, 0] (1 way). Total = 6.MEX = 2: The subsets must contain both 0 and 1 but must not contain 2. These subsets are [0, 1] (2 ways) and [0, 1, 0] (1 way). Total = 3.The subsets [2, 0, 1] and [2, 0, 1, 0] have MEX = 3, which is outside the given range. Therefore, the total number of valid subsets is 6 + 3 = 9.Input: arr[] = [2, 0, 1], l = 1, r = 2Output: 3Explanation: The subsets whose MEX lies in the range [1, 2] are [0] (MEX = 1), [2, 0] (MEX = 1), and [0, 1] (MEX = 2). Hence, the answer is 3.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n + r)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-10-30 22:04:28
- **Status:** Correct
- **Marks:** 8

```cpp
class Solution {
  public:
    const int mod=1e9+7;
    long long power(int a,int b){
        if(b==1){
            return a;
        }
        if(b==0){
            return 1;
        }
        long long half=(power(a,b/2))%mod;;
        if(b%2==0){
            return (half*half)%mod;
        }
        else{
            return ((half*half)%mod*a)%mod;
        }


    }
    int cntSubsets(vector<int> &arr, int l, int r) {
        // code here
        int n=arr.size()+1;
        vector<int>freq(n,0);
        for(int i=0;i<arr.size();i++){
            freq[arr[i]]++;
        }
        vector<int>prefix(n);
        prefix[0]=freq[0];
        for(int i=1;i<n;i++){
            prefix[i]=prefix[i-1]+freq[i];
        }
        vector<long long>dp(n,-1);
        for(int i=0;i<n;i++){
            if(freq[i]==0){
                break;
            }
            dp[i]=((power(2,freq[i])-1)%mod+mod)%mod;
            long long prev=(i-1)>=0?dp[i-1]:1;
            dp[i]=(dp[i]*prev)%mod;

        }
        int count=0;
        for(int i=l;i<=r;i++){
            int prev_comb=(i-1>=0)?dp[i-1]:1;
            if(prev_comb==-1){
                break;
            }
            int total_elements=n-prefix[i]-1;
            long long comb= power(2,total_elements);
            comb=(comb*prev_comb)%mod;
            count=(count+comb)%mod;


        }
        return count;


    }
};
```

*Generated on: 10/30/2026, 10:23:34 PM*