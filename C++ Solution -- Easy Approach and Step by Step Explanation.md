## 01. C++ Solution || Easy Approach and Step by Step Explanation

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/new-registration-system--150419/1?_gl=1*72nq8r*_up*MQ..*_gs*MQ..&gclid=CjwKCAiAtbvXBhB_EiwAjwv9JtEV_Jc0injVQpzfz_ayURVKqBgC8z7bm4xIKioYALMUC-M-uM_GmhoC4PoQAvD_BwE&gbraid=0AAAAAC9yBkBKFYy4ZGZFQuGsHlXZ8a_Y5)

### Problem Description

**Task:** Given an array of strings arr[]. The array represents first names of users, generate a unique username for each entry in the order it appears.Initially, consider all usernames present in the input array as reserved.If a username has not already been assigned to any previous user, keep it unchanged.Otherwise, append the smallest positive integer suffix that produces a username that has not been reserved or assigned to any previous user.Return the array of generated usernames.Examples:Input: arr[] = ["aba", "ab", "aba", "aba", "ab"]Output: ["aba", "ab", "aba1", "aba2", "ab1"]Explanation: The first occurrences of "aba" and "ab" are new, so they remain unchanged. The next "aba" is already used, so "aba1" is assigned. When "aba" appears again, "aba1" is already used, so "aba2" is assigned. Similarly, the second occurrence of "ab" becomes "ab1".Input: arr[] = ["a", "a", "a1", "a"]

#### Examples

##### Example 1

- **Output:**
```text
["aba1", "aba", "aba2"]
```
- **Explanation:** Initially, "aba1" and "aba" are reserved. The first occurrence of each retains its original name. For the second occurrence of "aba", "aba1" is already reserved, so "aba2" is assigned.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n * m)
- **Expected Auxiliary Space Complexity:** O(n * m)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-11-07 22:53:35
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
  public:
    vector<string> generateUsernames(vector<string> arr) {
        // code here
        unordered_map<string,int>m;
        int n = arr.size();
        vector<string>ans;
        for(int i=0;i<n;i++) m[arr[i]]=0;

        for(int i=0;i<n;i++){

            string s = arr[i];

            if(m[s]==0){
                ans.push_back(s);
                m[s]++;
            }
            else{

                while(m.count(s+to_string(m[s])))m[s]++;
                ans.push_back(s+to_string(m[s]));
                m[s]++;

            }

        }

        return ans;

    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-11-07 22:53:22
- **Status:** Correct
- **Marks:** 2

```cpp
class Solution {
  public:
    vector<string> generateUsernames(vector<string> arr) {
        // code here
        unordered_map<string,int>m;
        int n = arr.size();
        vector<string>ans;
        for(int i=0;i<n;i++) m[arr[i]]=0;

        for(int i=0;i<n;i++){

            string s = arr[i];

            if(m[s]==0){
                ans.push_back(s);
                m[s]++;
            }
            else{

                while(m.count(s+to_string(m[s])))m[s]++;
                ans.push_back(s+to_string(m[s]));
                m[s]++;

            }

        }

        return ans;

    }
};
```

*Generated on: 11/7/2026, 10:53:56 PM*