# Same Tree
## Link
[Same Tree](https://leetcode.com/problems/same-tree/description/)

## Code
```cpp
class Solution {
public:
    bool isSameTree(TreeNode* p, TreeNode* q) {
        return core(p, q);
    }

    bool core(TreeNode* p, TreeNode* q){

        if(p==nullptr&&q==nullptr){
            return true;
        }
        if(p==nullptr||q==nullptr){
            return false;
        }
        if(p->val!=q->val){
            return false;
        }

        return core(p->left,q->left)&&(p->right,q->right);
    }
};
```

## Evaluation
![img](./17_img.png)