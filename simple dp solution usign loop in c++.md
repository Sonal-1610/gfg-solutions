## 01. simple dp solution usign loop in c++

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/good-stones--170647/1?_gl=1*1n5hcxr*_up*MQ..*_gs*MQ..&gclid=CjwKCAjw_9bWBhBGEiwAomyTIiSgBsq9aAutTVyjVhxfseX4LMtkQbIE5DB6ab9wxDc3BXYoxi8lBxoCRtwQAvD_BwE&gbraid=0AAAAAC9yBkDg0fHBh_OjrLCDF12hEmJIn)

### Problem Description

**Task:** Given an array arr[], where arr[i] represents the exact number of steps to move from index i. An index is considered good if repeatedly following the jumps eventually takes you outside the array. Otherwise, if the jumps result in an infinite loop, the index is considered bad. A positive value indicates a move to the rightA negative value indicates a move to the left.A 0 value means no move and considered bad.Return the number of good indices.Examples:Input: [2, 3, -1, 2, -2, 4, 1]

#### Examples

##### Example 1

- **Output:**
```text
3
```
- **Explanation:** Indices 3, 5, and 6 are good because their jump sequences eventually leave the array. Indices 1, 2, and 4 form a cycle, while index 0 eventually enters this cycle through index 2. Hence, the total number of good indices is 3.

##### Example 2

- **Input:**
```text
[1, 0, -3, 0, -5, 0]
```
- **Output:**
```text
2
```
- **Explanation:** Indices 2 and 4 are good because their jumps take them outside the array. Indices 1, 3, and 5 are bad because their jumps are zero. Index 0 is also bad because it jumps to index 1, which is a dead end. Hence, the total number of good indices is 2.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-10-19 21:51:54
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
  public:
    int goodIndices(vector<int> &arr) {
        // code here
        int n=arr.size();
        vector<int>vis(n,0);
        vector<vector<int>>adj(n);
        queue<int>q;
        for(int i=0;i<n;i++){
            int dest=i+arr[i];
            if(dest<0 || dest>=n) q.push(i);
            else adj[i+arr[i]].push_back(i);

        }
        while(!q.empty()){
            int idx=q.front();
            q.pop();
            vis[idx]=1;
            for(auto it:adj[idx]){
                q.push(it);
            }
        }
        return accumulate(vis.begin(),vis.end(),0);
    }
};
```

*Generated on: 10/19/2026, 9:52:14 PM*