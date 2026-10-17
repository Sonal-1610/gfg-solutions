## 01. C++ Solution || Easy Approach and Step by Step Explanation

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/check-if-it-is-possible-to-convert-one-string-into-another-with-given-constraints4116/1)

### Problem Description

**Task:** Given two strings s1 and s2, consisting only of the characters 'A', 'B', and '#'. Determine whether s1 can be transformed into s2 by performing the following operations on s1:'A' can move only towards the left. 'B' can move only towards the right.Neither 'A' nor 'B' can cross each other.'#' represents an empty position through which 'A' and 'B' can move.Moving the character at index i one step to the left means swapping it with the character at index i - 1, provided i - 1 >= 0. Similarly, moving it one step to the right means swapping it with the character at index i + 1, provided i + 1 < s1.length().Return true if s1 can be transformed into s2; otherwise, return false.Examples:Input: s1 = #A#B#B#, s2 = A###B#B

#### Examples

##### Example 1

- **Output:**
```text
false
```
- **Explanation:** The character 'A' in s1 is at index 1, whereas the corresponding 'A' in s2 is at index 3. Since 'A' can move only towards the left, it cannot reach a position to the right of its current position. Therefore, s1 cannot be transformed into s2, and hence, the answer is false.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n + m)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-10-17 22:14:14
- **Status:** Correct
- **Marks:** 2

```cpp
class Solution {
  public:
    bool isItPossible(string &s1, string &s2) {
        int n = s1.size();

        if (s2.size() != n)
            return false;

        int i = 0, j = 0;

        while (i < n && j < n) {
            while (i < n && s1[i] == '#')
                i++;

            while (j < n && s2[j] == '#')
                j++;

            if (i == n || j == n)
                return i == n && j == n;

            if (s1[i] != s2[j])
                return false;

            if (s1[i] == 'A' && i < j)
                return false;

            if (s1[i] == 'B' && i > j)
                return false;

            i++;
            j++;
        }

        return true;
    }
};
```

*Generated on: 10/17/2026, 10:14:34 PM*