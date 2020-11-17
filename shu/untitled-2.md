# 0102.二叉树层序遍历

BFS

```cpp
//
// Created by Administrator on 2020/11/5.
//
#include<bits/stdc++.h>
using namespace std;

struct TreeNode {
    int val;
    TreeNode *left;
    TreeNode *right;
    TreeNode(int x) : val(x), left(NULL), right(NULL) {}
};
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        vector<vector<int>> v;
        if(root == NULL) return v;
        queue<TreeNode*> q;
        q.push(root);
        while(!q.empty()){
            int n = q.size();
            vector<int>temp;
            for(int i = 0; i < n; i++){
                TreeNode*  top = q.front();
                q.pop();
                temp.push_back(top->val);

                if(top->left != NULL){
                    q.push(top->left);
                }
                if(top->right != NULL){
                    q.push(top->right);
                }
            }
            v.push_back(temp);
        }
        return v;
    }
};
```

