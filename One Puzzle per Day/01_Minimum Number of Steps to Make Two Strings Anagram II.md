# Minimum Number of Steps to Make Two Strings Anagram II
## Puzzle Description
You are given two strings `s` and `t`. In one step, you can append **any character** to either `s` or `t`.

Return *the minimum number of steps* to make `s` and `t` ***anagrams*** of each other.

An **anagram** of a string is a string that contains the same characters with a different (or the same) ordering.

## Methodology
1. Use `+` and `-` operation to implement intersect, unite and complement operation in this type of puzzles.
2. C++ -> map, unordered_map, vector.
3. Small and sweet mindset.

## Code
```cpp
class Solution {
public:
    int minSteps(string s, string t) {
        map<char, int> maps,mapt;

        for(int i=0;i<t.length();i++){
            mapt[t[i]]++;
        }

        for(int i=0;i<s.length();i++){
            mapt[s[i]]--;
        }

        map<char,int>::iterator it;
        int notint=0,notins=0;
        for(it=mapt.begin();it!=mapt.end();it++){
            if(it->second<0){
                notint+=it->second;
            }
            else{
                notins+=it->second;
            }
        }

        return notins-notint;
    }
};
```

## Evaluation
![MNoStMTSAII](./01.png)