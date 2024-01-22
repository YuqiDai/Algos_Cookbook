# Find Common Characters
## Puzzle Description
Given a string array ***words***, return an array of all characters that show up in all strings within the ***words*** (including duplicates). You may return the answer in **any order**.

## Methodology
Use hash table (an unordered_map is using there) to store the first word, then compare the hash table with the words after the first word in the string array ***words***. There we define two hash tables, the first one we have is used to store the number of letters in the first word. The second one is used to store the number of letters in the words following. Refer to code section for detail.

## Code
```cpp
class Solution {
public:
    std::vector<std::string> commonChars(std::vector<std::string>& words) {
        int len=words.size();

        std::unordered_map<char,int> umap;
        std::unordered_map<char,int> umapp;
        for(char c: words[0]){
            umap[c]++;
            umapp[c]=0;
        }

        for(int i=1;i<len;i++){
            for(char c: words[i]){
                if(umap.find(c)!=umap.end()){
                    umapp[c]++;
                }
                else{
                    umapp[c]=0;
                }
            }
            for(char j: words[0]){
                if(umap[j]>umapp[j]){
                    umap[j]=umapp[j];
                }
            }
            
            for(char c: words[0]){
                umapp[c]=0;
            }
        }

        std::vector<std::string> ans;
        for(auto const& i: umap){
            if(i.second>0){
                for(int j=0;j<i.second;j++){
                    std::string s;
                    s=i.first;
                    ans.push_back(s);
                }
            }
            
        }

        return ans;
    }
};
```

## Evaluation
![img](./2_Find%20Common%20Characters.png)