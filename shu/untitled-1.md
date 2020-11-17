# 0116.填充每个节点的下一个右侧节点

先序遍历，DFS

```cpp
class Solution {
public:
    Node* connect(Node* root) {
        if (root == NULL || root->left == NULL){
            return root;
        }
        root->left->next = root->right;
        if(root->next != NULL){
            root->right->next = root->next->left;
        }
        connect(root->left);
        connect(root->right);
        return root;
    }
};
```

层序遍历，BFS

但是似乎不满足题目要求，题目说常数级的额外空间

```cpp
class Solution {
public:
    Node* connect(Node* root) {
        if(root == NULL){
            return root;
        }

        queue<Node*>q;
        q.push(root);

        while(!q.empty()){
            int size = q.size();

            for(int i = 0; i < size; i++){
                Node * top = q.front();
                q.pop();

                if(i != size-1){
                    Node * next_ = q.front();
                    top->next = next_;
                }

                if(top->left != NULL){
                    q.push(top->left);
                }
                if(top->right != NULL){
                    q.push(top->right);
                }
            }
        }
        return root;
    }
};
```

