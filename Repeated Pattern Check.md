## 01. Repeated Pattern Check

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/the-pattern-matcher/1?_gl=1*1j42j28*_up*MQ..*_gs*MQ..&gclid=Cj0KCQiAk_DXBhCoARIsAHE-omMFgvI1rJ5MkE6Gn0pn_-EkeJWNhGYpyrxG9ttwK3TSFVw33aT5hFIaAkhnEALw_wcB&gbraid=0AAAAAC9yBkAm6_u3_9ocRTCj_UGh38Ls9)

### Problem Description

**Task:** Given a string s made of two characters of 'x' and 'y'. The task is to verify whether s is made by concatenating substrings that follow the pattern x^ny^n (equal number of y's follow equal number of x's).Examples:Input: s = "xxyyxy" Output: trueExplanation: The string can be split into "xxyy" + "xy". Both substrings contain an equal number of consecutive 'x' and 'y' characters.Input: s = "xyx"Output: falseExplanation: The last 'x' cannot form a valid substring because it is not followed by a matching 'y'.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(|s|)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-17 21:50:57
- **Status:** Correct
- **Marks:** 2

```cpp
class Solution {
  public:
    bool findPattern(string& s) {
        // code here
        int cnt=0;
        int n=s.size();
        int i=0;
        while(i<n)
        {
            while(i<n && s[i]=='x')
            {
                i++;
                cnt++;
            }
            while(i<n && s[i]=='y')
            {
                i++;
                cnt--;
            }
            if(cnt<0 || cnt>0)
            {
                return false;
            }
        }
        return cnt==0?true:false;
    }
};
```

*Generated on: 11/17/2026, 9:51:18 PM*