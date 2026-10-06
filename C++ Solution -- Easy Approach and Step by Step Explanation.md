## 01. C++ Solution || Easy Approach and Step by Step Explanation

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/longest-increasing-path-in-a-matrix/1?_gl=1*1uoii0h*_up*MQ..*_gs*MQ..&gclid=Cj0KCQjwuJLWBhD_ARIsAIBcRUyLxe5lOYdHCihFlwCz2xIgPjVupS0aVyw6w0wu8EpUYga8N0GFOUIaAlCvEALw_wcB&gbraid=0AAAAAC9yBkC6dZ9rm1drhORG61cee2iq9)

### Problem Description

**Task:** Given a matrix with n rows and m columns, find the length of the longest path such that:The path can start and end at any cell.A cell cannot be visited more than once.The values in path are strictly increasing. From each cell, you can move left, right, up, or down. Diagonal moves and moves outside the matrix are not allowed.Examples:Input: n = 3, m = 3, matrix[][] = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

#### Examples

##### Example 1

- **Output:**
```text
1
```
- **Explanation:** There can at most one vertex as all vertices are same.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n * m)
- **Expected Auxiliary Space Complexity:** O(n * m)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-10-06 21:54:47
- **Status:** Correct
- **Marks:** 8

```cpp
class Solution {
public:
    vector<vector<bool>> vis;
    vector<vector<int>> dist;
    int n, m;

    bool bounds(int i, int j) { return !(i < 0 || j < 0 || i >= n || j >= m); }

    int solve(vector<vector<int>>& matrix, int i, int j) {

        if (vis[i][j])
            return dist[i][j];

        int res = 0;

        vector<vector<int>> mv = {{1, 0}, {-1, 0}, {0, 1}, {0, -1}};

        for (auto it : mv)
            if (bounds(i + it[0], j + it[1]) && matrix[i + it[0]][j + it[1]] > matrix[i][j])
                res = max(res, solve(matrix, i + it[0], j + it[1]));

        vis[i][j] = true;
        return dist[i][j] += res;
    }

    int longIncPath(vector<vector<int>>& matrix, int n, int m) {

        this->n = n;
        this->m = m;

        vis = vector<vector<bool>>(n, vector<bool>(m, false));
        dist = vector<vector<int>>(n, vector<int>(m, 1));

        int res = 0;
        for (int i = 0; i < n; i++)
            for (int j = 0; j < m; j++)
                if (!vis[i][j])
                    res = max(res, solve(matrix, i, j));

        return res;
    }
};
```

*Generated on: 10/6/2026, 9:55:15 PM*