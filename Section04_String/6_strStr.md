# Strstr
## Puzzle Description
Given two strings ***needle*** and ***haystack***, return the index of the first occurrence of ***needle*** in ***haystack***, or ***-1*** if ***needle*** is not part of ***haystack***.

## Methodology
strStr is a typical KMP problem. So the core of this puzzle is understanding KMP algo. I'm sure there are many detailed KMP explaination posted online 'cause I also draw on those blogs to implement the algo given there.    

But even I have went through those blogs again and again, it's still a little bit hard for me to clearly understand the KMP algo. So my suggestion is giving yourself enough time to swallow the algo plus digesting it. Additionally, there is an obstacle when browsing solutions. Normally the index using to traverse ***needle*** which called ***j*** is equal to ***-1***. This is an optimized assignment which is not easy to think of at the beginning. I waste a lot of time trying to figure out the relations between ***j***, ***i***, ***next[]*** and the meaning of the content of ***next[]***.   

So if you want to fix this puzzle up fast as you can, you probably should assign ***j*** as 0 and ***i*** as 1, easier to think of.

## Code
```cpp
void getNext(int* next, std::string needle){
    int j=0;
    next[0]=0;
    for(int i=1;i<needle.size();i++){
        while(j>0&&needle[j]!=needle[i]){
            j=next[j-1];
        }
        if(needle[j]==needle[i]){
            j++;
        }
        next[i]=j;
    }
}

class Solution {
public:
    int strStr(std::string haystack, std::string needle) {
        std::vector<int> next(needle.size());

        if(haystack.size()==0||needle.size()==0){
            return -1;
        }

        getNext(&next[0], needle);

        int j=0;
        for(int i=0;i<haystack.size();i++){
            while(j>0&&haystack[i]!=needle[j]){
                j = next[j-1];
            }
            if(haystack[i]==needle[j]){
                j++;
            }
            if(j==needle.size()){
                return i-needle.size()+1;
            }
        }

        return -1;

    }
};

```

## Evaluation
![img](./6_strStr.png)