#quicksort 快排使用的策略和mergesort一同为 divide-and-conquer  
  
## strategy  
    **divide  ：** 将A[p..r]分为 A[p..q-1] A[q] A[q+1..r] 要求A[p..q-1] 上的所有数 <A[q]<A[q+1..r]  
    **conquer ：** 将俩个subarray A[P..q-1] A[q+1..r]进行quicksort  
    **combine ：** subarrays are already sorted，no need to combine  

##  pseudocode
```  quicksort(A,p,r)
  {
    if(p<r)
      q = partition(A,p,r);
      quicksort(A,p,q-1);
      quicksort(A,q+1,r);
  }
    partition(A,p,r)
     x =A[r]
     i = p-1
     for j=p to r-1
        if A[j] < x
          i=i+1
          exchange A[i] with A[j]
     exchange A[i+1]with A[r]
     return i+1
```  
## correctness of quicksort  
 **initializaion**  ：在第一次迭代的过程中，i = p-1 and j = p,没有值 lie both between p and i ，i+1 and j-1，trivially satisfied  
   
 **Maintenance **  ： while j < r 为了保持数组中 A[p..i] < A[r] && A[j..r-1] > A[r]     
----------------------A[j+1] > A[r]:j = j+1         
----------------------A[J+1] < A[r]： swap A[i+1] and A[j+1] and i++ j++    
 **Termination **  : at j == r,swap A[i+1] and A[R]
    
## performance of quicksort  
**worst-case partition** T(n) = T(n-1)+O(n); o(n^2) 
**best-case** T(n) = 2T(n/2)+o(n) o(nlogn)
** any split of constant prokportionality yields arecursion tree of depth (lgn) ,where cost at  each level is o(n)  n
***T(n) = T(an)+T((1-a)n)+O(n)  0<a<1; if a > 1-a, time cose of quicksort is o(logn/loga)***


```
  tail-recursive-quicksort(A,p,r) //尾递归quicksort
    while p < r                     
      q = partition(A,p,r)            //找到分界点
      tail-recursive-quicksort(A,p,q-1)  //尾递归左边
      p = q+1                           //尾递归递归右边
      
      a:describe a scenario in which tail-recursive-quicksort stacj depth is o(n) on n-element input array
      b:modify the code for tail-recursive-quicksort for o(logn) depth
```    
```尾递归：若函数在尾位置调用自身（或是一个尾调用本身的其他函数等等），则称这种情况为尾递归。
    尾递归也是递归的一种特殊情形。尾递归是一种特殊的尾调用，即在尾部直接调用自身的递归函数。
    对尾递归的优化也是关注尾调用的主要原因。
    尾调用不一定是递归调用，但是尾递归特别有用，也比较容易实现。
    特点：尾递归在普通尾调用的基础上，多出了2个特征：
    
    10. 在尾部调用的是函数自身 (Self-called)；
    2. 可通过优化，使得计算仅占用常量栈空间 (Stack Space)。
```
