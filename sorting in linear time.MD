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
```
#radix sort

```Radix-sort(A,d)
    for i = 1 to d
      use a stable sort to sort array A on digit i
```
##what is stable sort:
  
