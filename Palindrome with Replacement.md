## 01. Palindrome with Replacement

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/palindrome-with-minimum-sum--170648/1)

### Problem Description

**Task:** Given a string s consisting of lowercase English letters and the character '?',
Replace every '?' with a lowercase English letter such that the resulting string is a palindrome.
If it is possible to form a palindrome, return the minimum possible sum of the absolute ASCII differences between every pair of adjacent characters in the resulting string.
If it is not possible to form a palindrome, return -1.

#### Examples

##### Example 1

- **Input:**
```text
s = a???c??c????
```
- **Output:**
```text
4
```
- **Explanation:** One optimal palindrome is "abbbccccbbba". The sum of the absolute ASCII differences between adjacent characters is 1 + 0 + 0 + 1 + 0 + 0 + 0 + 1 + 0 + 0 + 1 = 4, which is the minimum possible.

##### Example 2

- **Input:**
```text
s = a???c??c???c
```
- **Output:**
```text
-1
```
- **Explanation:** It is not possible to replace the '?' characters to make the string a palindrome because the first and last characters are different and cannot be changed.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-10-22 22:46:51
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
public:
    int minimumSum(string& s) {
        int n = s.size();
        int k = n / 2;
        for (int i = 0; i < k; i++) {
            if ((s[i] != '?') && (s[n - 1 - i] != '?')) {
                if (s[i] != s[n - 1 - i])
                    return -1;
            } else if (s[i] != '?')
                s[n - 1 - i] = s[i];
            else if (s[n - 1 - i] != '?')
                s[i] = s[n - 1 - i];
        }

        int res = 0;
        for (int i = 1; i < k; i++) {
            if (s[i] != '?' && s[i - 1] != '?')
                res += 2 * abs(s[i] - s[i - 1]);
            else if (s[i] == '?' && s[i - 1] != '?')
                s[i] = s[i - 1];
        }

        if (n % 2 && s[k] != '?' && s[k - 1] != '?')
            res += 2 * abs(s[k] - s[k - 1]);

        return res;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-22 22:46:25
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
public:
    int minimumSum(string& s) {
        int n = s.size();
        int k = n / 2;
        for (int i = 0; i < k; i++) {
            if ((s[i] != '?') && (s[n - 1 - i] != '?')) {
                if (s[i] != s[n - 1 - i])
                    return -1;
            } else if (s[i] != '?')
                s[n - 1 - i] = s[i];
            else if (s[n - 1 - i] != '?')
                s[i] = s[n - 1 - i];
        }

        int res = 0;
        for (int i = 1; i < k; i++) {
            if (s[i] != '?' && s[i - 1] != '?')
                res += 2 * abs(s[i] - s[i - 1]);
            else if (s[i] == '?' && s[i - 1] != '?')
                s[i] = s[i - 1];
        }

        if (n % 2 && s[k] != '?' && s[k - 1] != '?')
            res += 2 * abs(s[k] - s[k - 1]);

        return res;
    }
};
```

*Generated on: 10/22/2026, 10:47:09 PM*