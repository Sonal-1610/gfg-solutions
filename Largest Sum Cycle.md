## 01. Largest Sum Cycle

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/largest-sum-cycle--170645/1?_gl=1*oyq5z9*_up*MQ..*_gs*MQ..&gclid=CjwKCAiAhqHXBhAXEiwATbksU-RVGJhda8HDaw9ZdJ_ZIGRiaPN3_RWLC4Lf5dTHdbzXQFOMGtFxpxoCUp4QAvD_BwE&gbraid=0AAAAAC9yBkDTjfOsjArmSCKQr7oec2Gyv)

### Problem Description

**Task:** Given an array edge[] of size n, there are n cells numbered from 0 to n - 1. Each cell has at most one outgoing edge.For every cell i:edge[i] is the cell reached from i in one step.edge[i] = -1 means that cell i has no outgoing edge.A cycle is a sequence of cells where, by following the outgoing edges, we eventually return to the starting cell. The sum of a cycle is the sum of the indices of all cells in that cycle.Return the maximum cycle sum. If there is no cycle, return -1.Examples:Input: edge[] = [1, 2, 0, -1]Output: 3Explanation: There is only one cycle in the graph i.e. 0 - > 1 - > 2 - > 0. Sum of the cell index in that cycle = 0 + 1 + 2 = 3.Input: edge[] = [2, 0, -1, 2]Output: -1Explanation: There is no cycle in the graph. The edges are 1 - > 0 - > 2 < - 3. Hence, 2 has no outgoing edge, so no cycle exists.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-11-02 22:39:12
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
  public:
    int largestSumCycle(vector<int>& edge) {
        int n = edge.size() ;
        vector<int>visited(n,0) ;
        int ans = -1 ;
        for(int i = 0 ; i < n ; i++){
            if(visited[i]) continue ;
            vector<int>path_visited(n,0) ;
            vector<int>pre_sum(n,0) ;
            int idx = i ;
            int sum = 0 ;
            while(edge[idx] != -1 && !visited[idx]){
                visited[idx] = 1 ;
                path_visited[idx] = 1 ;
                pre_sum[idx] = sum ;
                sum += idx ;
                idx = edge[idx] ;
            }
            if(edge[idx] != -1 && path_visited[idx]){
                ans = max(ans,sum - pre_sum[idx]) ;
            }
        }
        return ans ;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-11-02 22:38:58
- **Status:** Correct
- **Marks:** 8

```cpp
class Solution {
  public:
    int largestSumCycle(vector<int>& edge) {
        int n = edge.size() ;
        vector<int>visited(n,0) ;
        int ans = -1 ;
        for(int i = 0 ; i < n ; i++){
            if(visited[i]) continue ;
            vector<int>path_visited(n,0) ;
            vector<int>pre_sum(n,0) ;
            int idx = i ;
            int sum = 0 ;
            while(edge[idx] != -1 && !visited[idx]){
                visited[idx] = 1 ;
                path_visited[idx] = 1 ;
                pre_sum[idx] = sum ;
                sum += idx ;
                idx = edge[idx] ;
            }
            if(edge[idx] != -1 && path_visited[idx]){
                ans = max(ans,sum - pre_sum[idx]) ;
            }
        }
        return ans ;
    }
};
```

*Generated on: 11/2/2026, 10:39:32 PM*