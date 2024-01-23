# Happy Number
## Puzzle Description
Write an algorithm to determine if a number n is happy.   

A happy number is a number defined by the following process:

* Starting with any positive integer, replace the number by the sum of the squares of its digits.
* Repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1.
* Those numbers for which this process ends in 1 are happy.

Return ***true*** if ***n*** is a happy number, and ***false*** if not.

## Methodology
Refer to code.

## Code
```cpp
class Solution {
public:
    bool isHappy(int n) {
        int slow=n;
        int fast=nextone(n);
        while(fast!=1&&fast!=slow){
            slow=nextone(slow);
            fast=(nextone(nextone(fast)));
        }

        return (fast==1);
    }

    int nextone(int n){
        int sum=0;
        while(n){
            sum+=(n%10)*(n%10);
            n=n/10;
        }
        std::cout<<sum<<std::endl;
        return sum;
    }
};
```

## Evaluation
![img](./4_Happy%20Number.png)