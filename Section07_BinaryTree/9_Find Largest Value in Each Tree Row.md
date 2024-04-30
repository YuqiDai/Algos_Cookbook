# Find Largest Value in Each Tree Row
## 1. Link
[Find Largest Value in Each Tree Row](https://leetcode.com/problems/find-largest-value-in-each-tree-row/description/)

## 2. Code
```cpp
class Solution {
public:
    vector<int> largestValues(TreeNode* root) {
        queue<TreeNode*> que;
        vector<int> ans;
        TreeNode* tp=root;
        que.push(tp);
        int num=1;
        int ct=0;

        if(root==nullptr){
            return ans;
        }

        while(!que.empty()){
            int max=que.front()->val;
            for(int i=0;i<num;i++){
                if(que.front()->left){
                    que.push(que.front()->left);
                    ct++;
                }
                if(que.front()->right){
                    que.push(que.front()->right);
                    ct++;
                }
                if(max<que.front()->val){
                    max=que.front()->val;
                }
                que.pop();
            }
            num=ct;
            ct=0;
            ans.push_back(max);
        }

        return ans;
    }
};

```

## 3. Evaluation
![img](./9_img.png)
