# Reverse Words in a String
## Puzzle Description
Given an input string ***s***, reverse the order of the **words**.

A **word** is defined as a sequence of non-space characters. The **words** in ***s*** will be separated by at least one space.

Return *a string of the words in reverse order concatenated by a single space*.

**Note** that ***s*** may contain leading or trailing spaces or multiple spaces between two words. The returned string should only have a single space separating the words. Do not include any extra spaces.

## Methodology
This puzzle has appeared before in the fourth section. At that time, the first step I clear the blank space before the first letter and after the last letter; Then I use extra space to store the words; At the end, I string all words together.   

But this time, I haven't use extra space. So the methodology is like: Step one, reverse the whole string; Step two, clear the blank space before the first letter and after the last letter; Step three, reverse the single words in the after-processed string.

For the detail, refer to my code.


## Code
```cpp
void rvsStr(std::string& s,int left, int right){
    while(left<right){
        std::swap(s[left++],s[right--]);
    }
}

void rmBlank(std::string& s){
    int len=s.size();
    int slow=0;
    for(int i=0;i<len;i++){
        if(s[i]!=' '){
            while(i<len&&slow<len&&s[i]!=' '){
                s[slow++]=s[i++];
            }
            if(slow<len){
                s[slow++]=' ';
            }
        }
    }
    while(s[slow-1]==' '){
        slow--;
    }

    s.resize(slow);

}

class Solution {
public:
    std::string reverseWords(std::string s) {
        std::string tp=s;
        rvsStr(tp, 0, tp.size()-1);
        rmBlank(tp);
        int fast=0,slow=0;
        while(fast<=tp.size()){
            if(tp[fast]!=' '&&fast<tp.size()){
                fast++;
                continue;
            }
            rvsStr(tp, slow, fast-1);
            fast++;
            slow=fast;
        }

        return tp;
    }
};

```

## Evaluation
![img](./Reverse%20Words%20in%20a%20String.png)