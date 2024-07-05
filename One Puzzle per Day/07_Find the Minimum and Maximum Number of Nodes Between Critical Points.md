# Find the Minimum and Maximum Number of Nodes Between Critical Points
## Link
[Find the Minimum and Maximum Number of Nodes Between Critical Points](https://leetcode.com/problems/find-the-minimum-and-maximum-number-of-nodes-between-critical-points/)

## Code
```cpp
class Solution {
private:
    vector<int> pos;
public:
    vector<int> nodesBetweenCriticalPoints(ListNode* head) {
        ios_base::sync_with_stdio(false);
        int lf, mid, rt;
        if(((head->next->next)==nullptr)||(head->next->next->next)==nullptr){
            return {-1,-1};
        }

        int index=0;
        do{
            lf=head->val;
            mid=head->next->val;
            rt=head->next->next->val;

            if((lf<mid&&mid>rt) || (lf>mid&&mid<rt)){
                pos.push_back(index+1);
            }

            head=head->next;
            ++index;
        }while(head->next->next!=nullptr);

        if(pos.size()<2){
            return {-1, -1};
        }

        int mindis=INT_MAX, maxdis=*(pos.end()-1)-*(pos.begin());
        for(int i=0;i<pos.size()-1;++i){
            cout<<pos[i+1]<<" "<<pos[i]<<endl;
            mindis = min(mindis, pos[i+1]-pos[i]);
        }

        return {mindis, maxdis};
    }
};
```

## Evaluation
![Find the Minimum and Maximum Number of Nodes Between Critical Points](./07.PNG)