## 01. Sort in Specific Order

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/sort-in-specific-order2422/1?_gl=1*14ww44*_up*MQ..*_gs*MQ..&gclid=Cj0KCQiA2frXBhC_ARIsAPTFcdOfzVoB47yy24erRaeuoy4inJQFKnXBGfoGyLEF15DFlTeJLk34JPAaAg2kEALw_wcB&gbraid=0AAAAAC9yBkCDJJHniwD0wMSh8OIPPJ9ml)

### Problem Description

**Task:** Given an array arr[] of non-negative integers. Your need to sort them so that The first part of the array contains odd numbers sorted in descending order.The rest of the portion contains even numbers sorted in ascending order.Examples:Input: arr[] = [1, 2, 3, 5, 4, 7, 10]

#### Examples

##### Example 1

- **Output:**
```text
[7, 5, 3, 1, 0, 2, 4]Explanation: 7, 5, 3, 1 are odd numbers in descending order and 0, 2, 4 are even numbers in ascending order.
```
- **Explanation:** 7, 5, 3, 1 are odd numbers in descending order and 2, 4, 10 are even numbers in ascending order.Input: arr[] = [0, 4, 5, 3, 7, 2, 1]

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n log n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-11-19 21:40:02
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
  public:
    void sortIt(vector<int>& arr) {
        // code here

        int n = arr.size();
        int i = 0;
        int j = n-1;
        int count = 0;

        while (i < j) {

            if (arr[i] % 2 == 1) {
                i++;
            }
            else if (arr[j] % 2 == 0) {
                j--;
            }
            else {
                swap(arr[i], arr[j]);
                i++;
                j--;
            }
        }

        for (int i = 0; i < n; i++) {
            if (arr[i] % 2 != 0) {
                count++;
            }
        }

        sort(begin(arr), begin(arr) + count, greater<int>());
        sort(begin(arr) + count, end(arr));
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2025-12-18 21:24:43
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
  public:
    void sortIt(vector<int>& arr) {
        // code here
        vector<int> odd;
        vector<int> even;
        for(auto& it: arr){
            if(it%2==0){
                even.push_back(it);
            }
            else{
                odd.push_back(it);
            }
        }
        sort(even.begin(),even.end());
        sort(odd.begin(),odd.end());
        int k=0;
        for(int i=odd.size()-1;i>=0;i--){
            arr[k]=odd[i];
            k++;
        }
        for(int i=0;i<even.size();i++){
            arr[k]=even[i];
            k++;
        }
        
    }
};
```

*Generated on: 11/19/2026, 9:40:22 PM*