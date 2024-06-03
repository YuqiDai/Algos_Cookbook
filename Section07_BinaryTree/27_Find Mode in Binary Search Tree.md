# Find Mode in Binary Search Tree
## Link
[Find Mode in Binary Search Tree](https://leetcode.com/problems/find-mode-in-binary-search-tree/description/)

## Code
```cpp
class Solution {
public:
    vector<int> findMode(TreeNode* root) {
        int num=0;
        int size=0;
        int prev=-1;
        vector<int> ans;

        core(root, num, size, prev, ans);
        return ans;
    }

    void core(TreeNode* node, int& num, int& size, int& prev, vector<int>& ans){
        if(node==nullptr){
            return ;
        }

        core(node->left, num, size, prev, ans);
        if(ans.size()==0){
            ans.push_back(node->val);
            prev=node->val;
            num++;
            size++;
        }
        else{
            if(node->val!=prev){
                prev=node->val;
                size=1;
                if(size==num){
                    ans.push_back(prev);
                }
            }
            else{
                size++;
                if(size==num){
                    ans.push_back(prev);
                }
                if(size>num){
                    ans.clear();
                    ans.push_back(prev);
                    num=size;
                }
            }
        }

        core(node->right, num, size, prev, ans);
    }
};

```

## Evaluation
![Find Mode in Binary Search Tree](./27_img.png)