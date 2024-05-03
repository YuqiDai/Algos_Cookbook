# Binary Tree Paths
## Link
[Binary Tree Paths](https://leetcode.com/problems/binary-tree-paths/description/)

## Code
```cpp
class Solution {
public:
    vector<string> binaryTreePaths(TreeNode* root) {
        TreeNode* tp=root;
        return core(tp);
    }

    vector<string> core(TreeNode* node){
        vector<string> lf,rt,ans;

        if(node){
            lf=core(node->left);
            rt=core(node->right);

            int slf=lf.size();
            int srt=rt.size();

            if(slf==0&&srt==0){
                ans.push_back(to_string(node->val));
                return ans;
            }

            for(int i=0;i<slf;i++){
                ans.push_back(to_string(node->val)+"->"+lf[i]);
            }
            for(int i=0;i<srt;i++){
                ans.push_back(to_string(node->val)+"->"+rt[i]);
            }
        }

        return ans;
    }
};
```

## Evaluation
![img](./16_img.png)