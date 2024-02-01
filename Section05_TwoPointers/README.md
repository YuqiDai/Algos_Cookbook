# Section05_TwoPointers
## The necessary conditions to use TPM
* Monotonicity   
The direction of traversing is always the same.   

> Quote:   
> 如何将朴素的遍历优化成为双指针算法的遍历呢？   
优化条件->问题的答案存在单调性。(必须条件)   

>重点:
上面的例题之中，全部都提到了遍历方向自始至终不会发生改变，不会有指针的回溯。这就是结果单调性。
另一方面就是因为朴素遍历方法每次都要进行回溯，忽视了结果单调性，使得有些根本就不可能成立的数据也被遍历了一遍，这就造成了时间复杂度非常高。

> Link:<a href="https://www.acwing.com/blog/content/24845/"> 双指针算法笔记</a>

## Why TPM so fast?
* Branches cutting
> Quote   
    1. 利用问题特性，通过长短板的内移来划分剪枝边界，并在每次剪枝（短板处的指针内移一格）前，将要剪去的部分（以移动 R 为例，剪去的部分就是 [:, R]）的局部最大体积记录下来   
    2. 每次指针内移，左右指针的距离减少 1，L<R 的约束与剪枝共同作用，使得对 C(n, 2)=n(n-1)/2 种情形的分块剪枝可以在 n - 2 次循环后完成（从距离 n-1 到距离 1）   
    3. 由于问题的性质，可以直接确定局部最大体积就是 [L, R] 对应的体积（长板指针内移会导致min(长, 短)不变或减少，而距离减少，从而体积减少），从而免去对 [:, R] 的局部最大体积的搜索，将整个问题的时间复杂度降为 O(n)  
 
> 综上，双指针法能保证最大体积情况被检索到，是因为它将整个问题的搜索范围划分为 O(n) 个子范围，分别求得了每个子范围的最大值，而全局最大值一定会被局部最大值函数捕获。

Link：[为什么双指针算法可以遍历所有情况呢](https://www.zhihu.com/question/477768158/answer/2951907655)

## Puzzle list
1. [3 Sum](./3%20Sum.md)
2. [4 Sum](./4%20Sum.md)
3. [Array_remove elements](./Array_remove%20elements.md)
4. [Reverse Linked List](./Reverse%20Linked%20List.md)
5. [Reverse Words in a String](./Reverse%20Words%20in%20a%20String.md)
