# Ransom Note
## Puzzle Description
Given two strings ***ransomNote*** and ***magazine***, return ***true*** if ***ransomNote*** can be constructed by using the letters from ***magazine*** and ***false*** otherwise.

Each letter in ***magazine*** can only be used once in ***ransomNote***.

## Methodology
Use hashtable (i.e. unordered_map) to store the letters in ***magazine*** and the number of same letters by constructing a map shaped like ***unordered_map<char, int> mp***.

## Code
```cpp
class Solution {
public:
    bool canConstruct(std::string ransomNote, std::string magazine) {
        std::unordered_map<char,int> table;
        for(char a: magazine){
            table[a]++;
        }

        for(char b: ransomNote){
            if(table[b]>0){
                table[b]--;
            }
            else{
                return false;
            }
        }

        return true;
    }
};
```

## Evaluation
![img](./6_Ransom%20Note.png)