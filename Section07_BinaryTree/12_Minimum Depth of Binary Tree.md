# Minimum Depth of Binary Tree
## Link
[Minimum Depth of Binary Tree](https://leetcode.com/problems/minimum-depth-of-binary-tree/)

## Code
```cpp
class Solution {
public:
    int minDepth(TreeNode* root) {
        return unit(root, 1);
    }

    int unit(TreeNode* node, int layer){
        int lf,rt;
        if(node){
            lf=unit(node->left,layer+1);
            rt=unit(node->right,layer+1);
            if(lf==0&&rt==0){
                return layer;
            }
            if(lf!=0&&rt!=0){
                if(lf>rt){
                    return rt;
                }

                return lf;
            }
            if(lf!=0){
                return lf;
            }
            if(rt!=0){
                return rt;
            }
            
        }
        
        return 0;
    }
};
```

## Evaluation
![img](./12_img.png)