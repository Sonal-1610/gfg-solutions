## 01. Brute Approach

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/lexicographically-smallest-string--151951/1)

### Problem Description

**Task:** Given a string s, find the lexicographically smallest string after rotating the string left any number of times including 0.Example:Input: s = "abcd"Output: "abcd"Explanation: String after each rotation are "abcd", "bcda", "cdab", "dabc" and so on. Lexicographically smallest among them is "abcd".Input: s = "baca"

#### Examples

##### Example 1

- **Output:**
```text
"abac"
```
- **Explanation:** Strings after each rotation are "baca", "acab", "caba", "abac" and so on. Lexicographically smallest among them is "abac".

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-10-02 23:05:53
- **Status:** Correct
- **Marks:** 8

```cpp
class Solution {
  public:
    string lexiString(string &s) {
        string doubled = s + s;
        int n = doubled.size();
        vector<int> f(n, -1);
        int k = 0;
        for (int j = 1; j < n; j++) {
            char sj = doubled[j];
            int i = f[j - k - 1];
            while (i != -1 && sj != doubled[k + i + 1]) {
                if (sj < doubled[k + i + 1]) {
                    k = j - i - 1;
                }
                i = f[i];
            }
            if (sj != doubled[k + i + 1]) {
                if (sj < doubled[k]) {
                    k = j;
                }
                f[j - k] = -1;
            } else {
                f[j - k] = i + 1;
            }
        }
        return doubled.substr(k, s.size());
    }
};
```

*Generated on: 10/2/2026, 11:06:07 PM*