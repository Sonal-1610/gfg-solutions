## 01. XOR of Number Range

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/find-xor-of-numbers-from-l-to-r/1?_gl=1*15q3rtj*_up*MQ..*_gs*MQ..&gclid=Cj0KCQiAtvXXBhC2ARIsAJc8SUSjlFo482oGaAyfxHCXjv8vwC3PssUQC4PgrXdIszctxfBGD0Fh1AQaAso7EALw_wcB&gbraid=0AAAAAC9yBkAie3D05eN5VDMrUYNDHy2AS)

### Problem Description

**Task:** Given two integers l and r, find the bitwise XOR of all integers in the range [l, r] (both inclusive).Examples:Input: l = 4, r = 8

#### Examples

##### Example 1

- **Output:**
```text
5
```
- **Explanation:** The XOR of all integers from 5 to 9 is (5 xor 6 xor 7 xor 8 xor 9) = 5.Constraints:1 ≤ l ≤ r ≤ 10⁹

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(1)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-18 20:50:40
- **Status:** Correct
- **Marks:** 2

```cpp
class Solution {
  public:
    int getBitCount(int n, int b){
        return floor(1LL*(n/pow(2, b+1)))*pow(2, b) + max(0.0, n - floor(1LL*(n/pow(2, b+1)))*pow(2, b+1) - pow(2, b) + 1);
    }
    int findXOR(int l, int r) {
        int b = 0;
        int _xor = 0;
        while(1<<b<=r){
            if((getBitCount(r, b) - getBitCount(l - 1, b))%2){
                _xor += 1<<b;
            }
            b += 1;
        }
        return _xor;
    }
};
```

*Generated on: 11/18/2026, 8:51:01 PM*