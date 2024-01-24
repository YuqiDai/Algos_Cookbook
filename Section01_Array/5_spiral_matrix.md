# Spiral Matrix
## Puzzle Description
Given a positive integer ***n***, generate an ***n x n*** ***matrix*** filled with elements from ***1*** to $n^2$ in spiral order.   
Refer to [Spiral Matrix](https://leetcode.com/problems/spiral-matrix-ii/description/)
## Methodology
The most difficult part of this puzzle is boundary checking. We have two main loops which are nested. The boundary of the outer loop is ***value<=$n*n$***, the boundary of the inner loop will be shown below.

## Code
```c++
int main(){
    int n=3;
    std::vector<std::vector<int>> v(n, std::vector<int>(n,0));
    v[0][0]=1;
    int i=0,j=0;
    int value=2;

    /* Function */
    
    while(value<=n*n){
        while(j<n-1&&v[i][j+1]==0){
            j+=1;
            v[i][j]=value++;
            std::cout<<"->"<<"v["<<i<<"]"<<"["<<j<<"]"<<v[i][j]<<std::endl;
        }
        while(i<n-1&&v[i+1][j]==0){
            i+=1;
            v[i][j]=value++;
            std::cout<<"down"<<"v["<<i<<"]"<<"["<<j<<"]"<<v[i][j]<<std::endl;
        }
        while(j>0&&v[i][j-1]==0){
            j-=1;
            v[i][j]=value++;
            std::cout<<"<-"<<"v["<<i<<"]"<<"["<<j<<"]"<<v[i][j]<<std::endl;
        }
        while(i>0&&v[i-1][j]==0){
            i-=1;
            v[i][j]=value++;
            std::cout<<"up"<<"v["<<i<<"]"<<"["<<j<<"]"<<v[i][j]<<std::endl;
        }
    }

    for(int i=0;i<n;i++){
        for(int j=0;j<n;j++){
            std::cout<<v[i][j]<<' ';
        }
        std::cout<<std::endl;
    }

    return 0;
}
```
## Evaluation
![img](./5_spiral_matrix.png)
