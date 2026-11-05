## 01. Minimum Days

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/minimum-days--170646/1?_gl=1*166fk6g*_up*MQ..*_gs*MQ..&gclid=Cj0KCQiA77DXBhCHARIsAHf2MNpzVKO24Z7wImShWcByBSai6n7x2n1prq20e8TiiugCowknGNSuJ8IaAirvEALw_wcB&gbraid=0AAAAAC9yBkDPW11Jpy5Zo0IRmk8yWYVSE)

### Problem Description

**Task:** Given a string s of length n containing only lowercase English letters, and a permutation array p[] of length n containing integers from 0 to n - 1. On the (i + 1)th day, the character at index p[i] in the string is replaced with '?'. For example:On day 1, replace s[p[0]] with '?'.On day 2, replace s[p[1]] with '?'.On day 3, replace s[p[2]] with '?'.And so on.Find the minimum number of days required so that no two adjacent characters in s are equal, unless at least one of them is '?'.Formally, for every index i (0 <= i < n - 1), the string must satisfy: If s[i] ! = '?' and s[i+1] ! = '?', then s[i] ! = s[i+1].Examples:Input: s = "aabb", p = [2, 1, 3, 0]

#### Examples

##### Example 1

- **Output:**
```text
0 The initial string "abca" already satisfies the condition without replacing any characters.
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n) [Note: For CPP - O(1)]

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-11-05 23:21:07
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
  public:

    bool check(string &s, vector<int> &p, int mid) {

        int n = s.size();
        vector<bool> removed(n, false);

        for(int i = 0; i < mid; i++) {
            removed[p[i]] = true;
        }

        for(int i = 0; i < n-1; i++) {

            if(!removed[i] && !removed[i+1] && s[i] == s[i+1]) {
                return false;
            }
        }

        return true;
    }

    int getMinimumDays(string &s, vector<int> &p) {

        int n = s.size();
        int low = 0, high = n;
        int ans = n;

        while(low <= high) {

            int mid = low + (high-low)/2;

            if(check(s, p, mid)) {
                ans = mid;
                high = mid-1;
            }
            else {
                low = mid+1;
            }
        }

        return ans;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-11-05 23:02:09
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
  public:

    bool check(string &s, vector<int> &p, int mid) {

        int n = s.size();
        vector<bool> removed(n, false);

        for(int i = 0; i < mid; i++) {
            removed[p[i]] = true;
        }

        for(int i = 0; i < n-1; i++) {

            if(!removed[i] && !removed[i+1] && s[i] == s[i+1]) {
                return false;
            }
        }

        return true;
    }

    int getMinimumDays(string &s, vector<int> &p) {

        int n = s.size();
        int low = 0, high = n;
        int ans = n;

        while(low <= high) {

            int mid = low + (high-low)/2;

            if(check(s, p, mid)) {
                ans = mid;
                high = mid-1;
            }
            else {
                low = mid+1;
            }
        }

        return ans;
    }
};
```

*Generated on: 11/5/2026, 11:21:28 PM*