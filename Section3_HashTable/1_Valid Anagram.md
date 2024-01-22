# Valid Anagram
## Puzzle Description
Given two strings ***s*** and ***t***, return ***true*** if ***t*** is an anagram of ***s***, and ***false*** otherwise.

An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once

## Methodology
**Anagram**s is actually some words which contain the same amount of alphabets. The amount of letters in each type of alphabet is also equal. (i.e. "nagaram" and "anagram")
So when we compare whether two words are a pair of anagrams, we need to make sure they both fit in the conditions above.

1. Store the letters by ascent in two arraies. Compare whether the two arraies are the same.
2. Use hash table

## Code
```cpp
class Solution {
public:
    bool isAnagram(std::string s, std::string t) {
        std::multiset <char> st;
        int size_s=s.size(),si=0;
        int size_t=t.size(),ti=0;

        if(size_s!=size_t){
            return false;
        }

        while(si<size_s){
            st.insert(s[si]);
            si++;
        }

        while(ti<size_s){
            if(st.find(t[ti])!=st.end()){
                st.erase(st.find(t[ti]));
                ti++;
            }
            else{
                return false;
            }
        }

        if(st.empty()==true){
            return true;
        }
        else{
            return false;
        }

    }
};

int main()
{
    std::string s = "anagram", t = "nagaram";

    Solution ss;
    std::cout<<ss.isAnagram(s,t);

    return 0;
}
```

## Evaluation
![img](./1_Valid%20Anagram.png)