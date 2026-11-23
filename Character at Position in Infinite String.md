## 01. Character at Position in Infinite String

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/the-infinite-string1049/1?_gl=1*1v0regb*_up*MQ..*_gs*MQ..&gclid=CjwKCAiA5Y_YBhBbEiwAK5Dl7YNbtWZT0mZq9R4X5a-7Vau3Thh_Q5omXxqlfJr6jIerpbGvbzsjRhoCTnEQAvD_BwE&gbraid=0AAAAAC9yBkB23gk9tffS83e-CZIarmyz7)

### Problem Description

**Task:** Given a string s and an integer pos, an infinite string is constructed by repeatedly applying the following operation. In the i-th step, append i consecutive $ characters, followed by the reverse of the current string, to the current string.Formally, if the current string is s, update it as:s = s + ('$' repeated i times) + reverse(s)The initial string is the given s, and the process continues indefinitely. Find and return the character at the pos(1-based indexing) in the resulting infinite string.Examples:Input: s = "12345", pos = 3

#### Examples

##### Example 1

- **Output:**
```text
3
```
- **Explanation:** In "12345...", the character at pos 3 is 3.

##### Example 2

- **Input:**
```text
s = "12345", pos = 10
```
- **Output:**
```text
2
```
- **Explanation:** In "12345$54321...", the character at pos 10 is 2.

##### Example 3

- **Input:**
```text
s = "abc", pos = 7
```
- **Output:**
```text
a
```
- **Explanation:** In "abc$cba...", the character at pos 7 is a.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(log (pos))
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-23 22:51:56
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
    char f(int i, int pos, string &s, vector<int> &vec) {
        if(i == 0) return s[pos - 1];
        // cout << i << " " << pos << endl;
        if(pos <= vec[i - 1]) return f(i - 1, pos, s, vec);
        if(pos <= vec[i - 1] + i) return '$';
        return f(i - 1, vec[i] - pos + 1, s, vec);
    }
  public:
    char posInfinite(string &s, int pos) {
        // code here
        int n = s.length();
        vector<int> vec;
        vec.push_back(n);
        for(int i = 1; vec.back() <= pos; i++) vec.push_back(vec.back() * 2 + i);
        return f(vec.size() - 1, pos, s, vec);
    }
};
```

*Generated on: 11/23/2026, 10:52:17 PM*