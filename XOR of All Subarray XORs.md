## 01. XOR of All Subarray XORs

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/game-of-xor1541/1)

### Problem Description

**Task:** Given an integer array arr[], find the XOR of the XOR values of all possible non-empty subarrays of the array.Examples:Input: arr[] = [1, 2, 3]

#### Examples

##### Example 1

- **Output:**
```text
2 xor[1] = 1 xor[1, 2] = 3 xor[2, 3] = 1 xor[1, 2, 3] = 0 xor[2] = 2 xor[3] = 3 Result: 1 ^ 3 ^ 1 ^ 0 ^ 2 ^ 3 = 2
```

##### Example 2

- **Input:**
```text
arr[] = [1, 2]
```
- **Output:**
```text
0 xor[1] = 1 xor[1, 2] = 3 xor[2] = 2 Result: 1 ^ 3 ^ 2 = 0
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (4)

#### Solution 1 (C++)

- **Submitted:** 2026-11-04 23:12:47
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
  public:
    int subarrayXor(vector<int>& arr) {
        // code here
        int pre = 0;
        int ans = 0;
        int n = arr.size();

        for(int i=0;i<n;i++){
            if((i+1)%2)pre^=arr[i];
            ans^=pre;
        }

        return ans;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-11-04 23:12:09
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
  public:
    int subarrayXor(vector<int>& arr) {
        // code here
        int pre = 0;
        int ans = 0;
        int n = arr.size();

        for(int i=0;i<n;i++){
            if((i+1)%2)pre^=arr[i];
            ans^=pre;
        }

        return ans;
    }
};
```

#### Solution 3 (C++)

- **Submitted:** 2026-11-04 23:11:48
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
  public:
    int subarrayXor(vector<int>& arr) {
        // code here
        int pre = 0;
        int ans = 0;
        int n = arr.size();

        for(int i=0;i<n;i++){
            if((i+1)%2)pre^=arr[i];
            ans^=pre;
        }

        return ans;
    }
};
```

#### Solution 4 (C++)

- **Submitted:** 2025-11-25 22:56:29
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
  public:
    int xorOfiFunc(int num, int cnt){
        if((cnt % 2) == 0){
            return 0;
        } else{
            return num;
        }
    }
  
    int subarrayXor(vector<int>& arr) {
        // code here
        int n = arr.size();
        int ans = 0;
        
        for(int i=0; i<n; i++){
            int cnt = (i*(n-i)) + (n-i);
            int xorOfi = xorOfiFunc(arr[i], cnt);
            ans = ans ^ xorOfi;
        }
        
        return ans;
    }


};
```

*Generated on: 11/4/2026, 11:12:59 PM*