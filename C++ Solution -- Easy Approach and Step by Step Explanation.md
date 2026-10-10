## 01. C++ Solution || Easy Approach and Step by Step Explanation

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/balancing-pan5038/1?_gl=1*my09dt*_up*MQ..*_gs*MQ..&gclid=Cj0KCQjwxKfWBhDkARIsAMKwkNZER9U2zfan8ygelDoUsd8z1NOl3GSXZ2yCofEsmHoG1d1xuzJ-xU0aAhHxEALw_wcB&gbraid=0AAAAAC9yBkC-7ZaRaHS0jNo2lLG5kmZ2E)

### Problem Description

**Task:** Given a simple weighing scale with two pans, a target weight b, and a set of weights where each weight is a distinct power of a, find if the scale can be balanced such that: b + (some powers of a) = (some other powers of a)Note: Exactly one weight is available for each power of a, so each power can be used at most once.Examples:Input: a = 4, b = 11

#### Examples

##### Example 1

- **Output:**
```text
true
```
- **Explanation:** 5 + 3 + 1 = 9. So, target = 5 can be balanced using powers of 3.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(log b)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-10-10 21:57:52
- **Status:** Correct
- **Marks:** 2

```cpp
class Solution {
public:
    bool balancePan(int a, int b) {
        if (a <= 0 or b < 0) return 0;
        if (a == 1) return 1;

        while (b) {
            int r = b % a;
            if (r == 0) b /= a;
            else if (r == 1) b = (b - 1) / a;
            else if (r == a - 1) b = (b + 1) / a;
            else return 0;
        }

        return 1;
    }
};
```

*Generated on: 10/10/2026, 9:58:13 PM*