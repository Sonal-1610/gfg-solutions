## 01. Coils in Matrix

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/form-coils-in-a-matrix4726/1)

### Problem Description

**Task:** Given a positive integer n, consider a 4n * 4n matrix filled with integers from 1 to (4n) * (4n) in row-major order (left to right, top to bottom). Form two coils from the matrix:The first coil starts from the top-left cell (0, 0) and spirals inward.The second coil starts from the bottom-right cell (4n - 1, 4n - 1) and spirals inward in the opposite direction.Return these two coils in the same order.Examples:Input: n = 1Output: [[1, 5, 9, 13, 14, 15, 11, 7], [16, 12, 8, 4, 3, 2, 6, 10]]

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n^2)
- **Expected Auxiliary Space Complexity:** O(n^2)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-10-03 22:38:07
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
  public:
  bool isInside(int x , int y , int l , int r , int u , int d){
      return x>=u && y>=l && x<=d && y<=r; 
  }
    const int dirx[4] = {1 ,0 ,-1 , 0};
    const int diry[4] = {0  ,1 , 0 , -1};
    void process(int x , int y , int l , int r , int u , int d , int dir ,int n, vector<int>&curr){
       bool moved = false;
        while(isInside(x + dirx[dir] , y + diry[dir] , l , r , u , d)){
            moved = true;
            x+=dirx[dir];
            y += diry[dir];
            curr.push_back(x * n + y);
        }
        if(dir%2 == 0){
            l++ , r--;
        }else u++ , d--;
            if(moved)process(x , y , l , r , u , d , (dir+1)%4 , n , curr);
    }
    vector<vector<int>> formCoils(int n) {
        // code here
        int m = n* 4;
        vector<vector<int>>vec(2);
        process(-1  , 1 ,1,m , 0 , m-1 , 0 ,m, vec[0]);
        process(m , m , 1 , m , 0 , m-1 , 2 ,m, vec[1]);
        return vec;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-03 22:38:02
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
  public:
  bool isInside(int x , int y , int l , int r , int u , int d){
      return x>=u && y>=l && x<=d && y<=r; 
  }
    const int dirx[4] = {1 ,0 ,-1 , 0};
    const int diry[4] = {0  ,1 , 0 , -1};
    void process(int x , int y , int l , int r , int u , int d , int dir ,int n, vector<int>&curr){
       bool moved = false;
        while(isInside(x + dirx[dir] , y + diry[dir] , l , r , u , d)){
            moved = true;
            x+=dirx[dir];
            y += diry[dir];
            curr.push_back(x * n + y);
        }
        if(dir%2 == 0){
            l++ , r--;
        }else u++ , d--;
            if(moved)process(x , y , l , r , u , d , (dir+1)%4 , n , curr);
    }
    vector<vector<int>> formCoils(int n) {
        // code here
        int m = n* 4;
        vector<vector<int>>vec(2);
        process(-1  , 1 ,1,m , 0 , m-1 , 0 ,m, vec[0]);
        process(m , m , 1 , m , 0 , m-1 , 2 ,m, vec[1]);
        return vec;
    }
};
```

*Generated on: 10/3/2026, 10:38:23 PM*