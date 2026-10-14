## 01. Roll Characters of String

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/roll-the-characters-of-a-string2127/1)

### Problem Description

**Task:** Given a string s consisting of lowercase English letters and an integer array roll[], perform a sequence of roll operations on the string. For each value roll[i], increment each of the first roll[i] characters of the string by 1 in the English alphabet. After 'z', the character wraps around to 'a'.Return the final string after applying all roll operations.Note: A roll operation affects the current state of the string, including all previous modifications.Examples:Input: s = "bca", roll[] = [1, 2, 3]

#### Examples

##### Example 1

- **Output:**
```text
debbExplanation: Initially, s = "zcza". Roll first 1 character: "zcza" - > "acza" Roll first 1 character again: "acza" - > "bcza" Roll first 3 characters: "bcza" - > "cdaa" Roll first 4 characters: "cdaa" - > "debb" Therefore, the final string is "debb".
```
- **Explanation:** Initially, s = "bca" roll[0] = 1: Roll the first 1 character. "bca" - > "cca" roll[1] = 2: Roll the first 2 characters. "cca"- > "dda" roll[2] = 3: Roll the first 3 characters. "dda" - > "eeb" After applying all the roll operations, the final string is "eeb".Input: s = "zcza", roll[] = [1, 1, 3, 4]

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (3)

#### Solution 1 (C++)

- **Submitted:** 2026-10-14 23:37:41
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
  public:
    string findRollOut(string& s, vector<int>& roll) {
        // code here
        int n = s.size();
        vector<int>v(n,0);

        for(int i=0;i<roll.size();i++) v[roll[i]-1]++;

        int sum = 0;
        for(int i=n-1;i>=0;i--){

            sum = (sum+v[i])%26;
            int num = s[i]-'a';
            num = (num+sum)%26;
            s[i] = char(num+'a');
        }

        return s;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-14 23:15:56
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
  public:
    string findRollOut(string& s, vector<int>& roll) {
        // code here
        int n = s.size();
        vector<int>v(n,0);

        for(int i=0;i<roll.size();i++) v[roll[i]-1]++;

        int sum = 0;
        for(int i=n-1;i>=0;i--){

            sum = (sum+v[i])%26;
            int num = s[i]-'a';
            num = (num+sum)%26;
            s[i] = char(num+'a');
        }

        return s;
    }
};
```

#### Solution 3 (C++)

- **Submitted:** 2026-10-14 23:15:42
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
  public:
    string findRollOut(string& s, vector<int>& roll) {
        // code here
        int n = s.size();
        vector<int>v(n,0);

        for(int i=0;i<roll.size();i++) v[roll[i]-1]++;

        int sum = 0;
        for(int i=n-1;i>=0;i--){

            sum = (sum+v[i])%26;
            int num = s[i]-'a';
            num = (num+sum)%26;
            s[i] = char(num+'a');
        }

        return s;
    }
};
```

*Generated on: 10/14/2026, 11:38:05 PM*