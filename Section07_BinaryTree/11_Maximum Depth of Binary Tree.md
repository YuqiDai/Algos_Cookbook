# Maximum Depth of Binary Tree
## Link
[Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/description/)

## Code
```cpp
class Solution {
public:
    int maxDepth(TreeNode* root) {
        TreeNode* tp=root;

        return unit(tp, 1);
    }

    int unit(TreeNode* node, int layer){
        int lf,rt;

        if(node){
            lf=unit(node->left, layer+1);
            rt=unit(node->right, layer+1);

            if(lf==rt&&lf==0){
                return layer;
            }
            if(lf>rt){
                return lf;
            }
            else{
                return rt;
            }
        }
        else{
            return 0;
        }
    }
};
```

## Evaluation
![img](./11_img.png)