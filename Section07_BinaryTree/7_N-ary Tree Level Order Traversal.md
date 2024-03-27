# N-ary Tree Level Order Traversal
## Puzzle Description
Given an n-ary tree, return *the level order traversal of its nodes' values*.

*Nary-Tree input serialization is represented in their level order traversal, each group of children is separated by the null value*.

## Methodology
Easy

## Code
```cpp
class Solution {
public:
    vector<vector<int>> levelOrder(Node* root) {
        vector<vector<int>> ans;
        Node* tp=root;
        queue<Node*> que;
        int size;

        if(tp){
            que.push(tp);
        }

        while(!que.empty()){
            size=que.size();
            vector<int> line;
            for(int i=0;i<size;i++){
                tp=que.front();
                que.pop();

                line.push_back(tp->val);
                for(int j=0;j<tp->children.size();j++){
                    que.push(tp->children[j]);
                }
            }

            ans.push_back(line);
        }

        return ans;
    }
};
```
## Evaluation
![N-ary](./7_N-ary%20Tree%20Level%20Order%20Traversal.png)

