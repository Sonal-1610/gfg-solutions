## 01. C++ Solution || Easy Approach and Step by Step Explanation

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/pairs-violating-bst-property--212515/1)

### Problem Description

**Task:** Given root of a binary tree in which all node values are distinct, count pairs of nodes that violate any of the following Binary Search Tree (BST) properties. All values in the left subtree are strictly smaller.All values in the right subtree are strictly greater.Examples:Input: root[] = [10, 50, 40, N, N, 20, 30]Output: 5

#### Examples

##### Example 1

- **Explanation:** There are total 10 pairs (80, 30), (80, 60), (80, 50), (30, 60), (40, 70), (40, 30), (40, 50), (70, 30), (70, 60), (70, 50) which violate the BST properties.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n log n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-10-23 22:52:36
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
  public:

  int ans=0;
  vector<int>merge(vector<int>&a,vector<int>&b)
  {
      int n=a.size(),m=b.size();
      a.push_back(1e9);
      b.push_back(1e9);
      vector<int>temp;
      int i=0,j=0;
      for(int k=0;k<n+m;k++)
      {
          if(a[i]<=b[j])
          {
              temp.push_back(a[i++]);
              ans+=j;
          }
          else temp.push_back(b[j++]);

      }
      return temp;

  }
  vector<int>mergesort(vector<int>&v)
  {
      int n=v.size();
      if(n==1) return v;
      vector<int>left,right;
      for(int i=0;i<n;i++)
      {
          if(i<(n/2)) left.push_back(v[i]);
          else right.push_back(v[i]);
      }
      left=mergesort(left);
      right=mergesort(right);
      return merge(left,right);
  }
  void help(Node *root,vector<int>&temp)
  {
      if(!root) return ;
      help(root->left,temp);
      temp.push_back(root->data);
      help(root->right,temp);

  }
    int pairsViolatingBST(Node *root) {
        vector<int>temp;
        help(root,temp);
        ans=0;
        mergesort(temp);
        return ans;

    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-23 22:52:17
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
  public:

  int ans=0;
  vector<int>merge(vector<int>&a,vector<int>&b)
  {
      int n=a.size(),m=b.size();
      a.push_back(1e9);
      b.push_back(1e9);
      vector<int>temp;
      int i=0,j=0;
      for(int k=0;k<n+m;k++)
      {
          if(a[i]<=b[j])
          {
              temp.push_back(a[i++]);
              ans+=j;
          }
          else temp.push_back(b[j++]);

      }
      return temp;

  }
  vector<int>mergesort(vector<int>&v)
  {
      int n=v.size();
      if(n==1) return v;
      vector<int>left,right;
      for(int i=0;i<n;i++)
      {
          if(i<(n/2)) left.push_back(v[i]);
          else right.push_back(v[i]);
      }
      left=mergesort(left);
      right=mergesort(right);
      return merge(left,right);
  }
  void help(Node *root,vector<int>&temp)
  {
      if(!root) return ;
      help(root->left,temp);
      temp.push_back(root->data);
      help(root->right,temp);

  }
    int pairsViolatingBST(Node *root) {
        vector<int>temp;
        help(root,temp);
        ans=0;
        mergesort(temp);
        return ans;

    }
};
```

*Generated on: 10/23/2026, 10:52:45 PM*