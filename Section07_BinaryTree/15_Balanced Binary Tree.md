# Balanced Binary Tree
## Link
[Balanced Binary Tree](https://leetcode.com/problems/balanced-binary-tree/description/)

## Code
```cpp
class Solution {
public:
    bool isBalanced(TreeNode* root) {
        TreeNode* tp=root;

        return (core(tp)==-1)?false:true;
    }

    int core(TreeNode* node){
        if(node){
            int lf=core(node->left);
            int rt=core(node->right);

            if(lf==-1||rt==-1){
                return -1;
            }

            if(lf>=rt){
                if(lf-rt>=2){
                    return -1;
                }
                return lf+1;
            }
            
            return ((rt-lf)>=2)?-1:rt+1;
        }

        return 0;
    }
};
```

## Evaluation
![img](./15_img.png)