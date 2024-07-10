# Crawler Log Folder
## Link
[Crawler Log Folder](https://leetcode.com/problems/crawler-log-folder/description/)

## Code
```cpp
class Solution {
public:
    int minOperations(vector<string>& logs) {
        stack<string> stk;

        for(int i=0;i<logs.size();++i){
            if(logs[i]=="../"){
                if(stk.size()==0){
                    continue;
                }
                stk.pop();
            }
            else if(logs[i]=="./"){
                continue;
            }
            else{
                stk.push(logs[i]);
            }
        }

        return stk.size();
    }
};
```

## Evaluation
![Crawler Log Folder](./12.PNG)