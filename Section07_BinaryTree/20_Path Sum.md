# Path Sum
## Link
[Path Sum](https://leetcode.com/problems/path-sum/description/)

## Code
```cpp
class Solution {
public:
    bool hasPathSum(TreeNode* root, int targetSum) {
        vector<int> ans;

        if(root){
            ans=core(root);
            vector<int>::iterator it;
            for(it=ans.begin();it!=ans.end();it++){
                if(*it==targetSum){
                    return true;
                }
            }
        }

        return false;
    }

    vector<int> core(TreeNode* node){
        vector<int> lf,rt;
        vector<int> ans;

        if(node==nullptr){
            return ans;
        }

        if(node->left==nullptr&&node->right==nullptr){
            ans.push_back(node->val);
            return ans;
        }

        lf=core(node->left);
        rt=core(node->right);

        for(int i=0;i<lf.size();i++){
            ans.push_back(lf[i]+node->val);
        }
        for(int i=0;i<rt.size();i++){
            ans.push_back(rt[i]+node->val);
        }

        return ans;
    }
};
```

## Evaluation
![img](./20_img.PNG)