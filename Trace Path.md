## 01. Trace Path

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/trace-path3840/1)

### Problem Description

**Task:** Given a rectangular grid with n rows and m columns, and a string s representing a sequence of movement commands. Geek can start from any cell of the grid and follows all the commands in s in the same order.The string s consists only of the characters L, R, D, and U, where:L: Move one cell left, from (i, j) to (i, j - 1).R: Move one cell right, from (i, j) to (i, j + 1).D: Move one cell up, from (i, j) to (i - 1, j).U: Move one cell down, from (i, j) to (i + 1, j).Determine whether there exists at least one starting cell such that Geek remains within the grid while following all the commands in s.Examples:Input: n = 1, m = 1, s = "R"

#### Examples

##### Example 1

- **Output:**
```text
true
```
- **Explanation:** One possible cell is (1, 3). (1, 3) - > (1, 2) - > (1, 1) - > (1, 2) - > (2, 2). Thus, there is a cell from where if Geek starts, it remains inside the grid throughout tracing the route.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(|s|)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-10-24 22:33:01
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
  public:
    bool isPossible(int n, int m, string& s) {
        // code here
        int lmn = 0  ,rmn =0 ,rmx =0 ,lmx = 0;
        int x  = 0 ,y = 0;
        for(char &ch: s){
            switch(ch){
                case 'U': x++;lmx = max(lmx , x); break;
                case 'D': x-- ; lmn = min(lmn , x);break;
                case 'L': y -- ; rmn = min(rmn , y);break;
                default: y ++; rmx = max(rmx , y);
            }
        }
        lmx -= lmn;
        rmx -= rmn;
        return lmx<n && rmx<m;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-24 22:32:41
- **Status:** Correct
- **Marks:** 2

```cpp
class Solution {
  public:
    bool isPossible(int n, int m, string& s) {
        // code here
        int lmn = 0  ,rmn =0 ,rmx =0 ,lmx = 0;
        int x  = 0 ,y = 0;
        for(char &ch: s){
            switch(ch){
                case 'U': x++;lmx = max(lmx , x); break;
                case 'D': x-- ; lmn = min(lmn , x);break;
                case 'L': y -- ; rmn = min(rmn , y);break;
                default: y ++; rmx = max(rmx , y);
            }
        }
        lmx -= lmn;
        rmx -= rmn;
        return lmx<n && rmx<m;
    }
};
```

*Generated on: 10/24/2026, 10:33:57 PM*