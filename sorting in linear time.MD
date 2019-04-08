# linear time sorting 从来都不可能是通过 comparison而是空间换时间的，comparison的sorting algorithme min cost o（nlogn）
  因为n个distinct element的排序有n！ 种，我们的sorting algorithm 就是寻找出特定的那个permutation.  
  在best-case 下，通过一次比较我们能每次减少当前一半的number of permutation,  
  2^h = n! = n^n  h = nlgn;  


# counting sort

``` Counting-sort(A,B,k)
let  c[0..k] be a new array
for i = 0 to k
    c[i] = 0
for j =1 to A.length
    c[A[j]] = c[A[j]]+1  // C[i] = k, 说明 A[0...A.length]中value 等于i的有k个数 
for i = 1 to k
    c[i] = c[i]+c[i-1]  // C[i]代表了A数组中value为i的数在数组中按照从小到大排列 第一个是 C[i]-c[i-1],最后一个c[i] ,
for j = A.length down to 1
    B[C[A[j]]] = A[j]         // A[j] 在c[]中最后的位置是C[A[j]]，将B[c[a[j]]]赋值 =a[j]
    C[A[j]] = C[A[j]] -1     // A[j] 在c[]中的位置 向前走一步   
    
The following solution also answers Exercise 8.2-2.  
Notice that the correctness argument in the text does not depend on the order in  
which A is processed. The algorithm is correct no matter what order is used!  
But the modified algorithm is not stable. As before, in the final for loop an element  
equal to one taken from A earlier is placed before the earlier one (i.e., at a lower  
index position) in the output arrray B. The original algorithm was stable because  
an element taken from A later started out with a lower index than one taken earlier.  
But in the modified algorithm, an element taken from A later started out with a  
higher index than one taken earlier.  


```
#radix sort

```Radix-sort(A,d)
    for i = 1 to d
      use a stable sort to sort array A on digit i
```
##what is stable sort: kind of sort that relation of each element is the same before sorting and after sorting

#medians and order statistics
  the ith order statistic of a set of n elements is the i th smallest element,the shhelection problem as follow  
  input: A set A of n distinct numbers and an integer i with 1< i < n.  
  output: ith smallest element
  
  找到最小的元素在数组中需要 n-1次比较 ，找到最大和最小的 需要3（n-2）/2次 
  找到最小和 找到第二小，n+logn

  


  
