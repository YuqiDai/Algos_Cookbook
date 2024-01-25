# Reverse String
## Puzzle Description
Write a function that reverses a string. The input string is given as an array of characters ***s***.   

You must do this by modifying the input array *in-place* with O(1) extra memory.

## Methodology
Two pointers.

## Code
```cpp
class Solution {
public:
    void reverseString(std::vector<char>& s) {
        int len=s.size();
        int left=0,right=len-1;
        while(left<right){
            std::swap(s[left],s[right]);
            left++;
            right--;
        }
    }
};
```

## Evaluation
![img](./1_Reverse%20String.png)