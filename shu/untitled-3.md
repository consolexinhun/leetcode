# 0094.二叉树的中序遍历

DFS

```cpp
#include<bits/stdc++.h>
using namespace std;

struct TreeNode {
  int val;
  TreeNode *left;
  TreeNode *right;
  TreeNode() : val(0), left(nullptr), right(nullptr) {}
  TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
  TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
};

class Solution {
public:
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int> res;
        dfs(root, res);
        return res;
    }

    void dfs(TreeNode *root, vector<int> &t){
        if(root == NULL) return ;

        if(root->left != NULL){
            dfs(root->left, t);
        }
        t.push_back(root->val);

        if(root->right != NULL){
            dfs(root->right, t);
        }
    }
};
```

