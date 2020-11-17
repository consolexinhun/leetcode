# 0236.二叉树最近公共祖先

树

递归

```cpp
#include<bits/stdc++.h>

struct TreeNode {
    int val;
    TreeNode *left;
    TreeNode *right;
    TreeNode(int x) : val(x), left(NULL), right(NULL) {}
};
using namespace std;
class Solution {
public:
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        if(root == NULL){
            return NULL;
        }
        if(root == p || root == q){
            return root;
        }
        TreeNode* left = lowestCommonAncestor(root->left, p, q);
        TreeNode* right = lowestCommonAncestor(root->right, p, q);
        if(left == NULL && right == NULL){
            return NULL;
        }
        else if(left != NULL && right != NULL){
            return root;
        }
        else if(left != NULL && right == NULL){
            return left;
        }
        else if(left == NULL && right != NULL){
            return right;
        }
        return root;
    }
};
int main(){
    Solution s;

    return 0;
}
```

