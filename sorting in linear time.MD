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
  
  找到最小的元素在数组中需要 n-1次比较 ： 显然  
  找到最大和最小的 需要3（n-2）/2次 ：在第一次比较中，大的value 初始化为max， 小的value初始化为min，（n = even if n odd min = max = A[0]）后续的比较中A[i]只有 大于max， 小于min，或者夹在二者之间，比较的次数分别是 1  1   ，3个数进行2次比较   3/2*n。  
  找到最小和 找到第二小，n+logn：   先用n-1次寻找到最小的，然后divide and conquer  
  
# Selection in expected linear time
randomized-select（A，p，r，i）
if p == r
    return A[p]
q = Randomized-partition（A，p，r）
k =q-p+1
if i == k return A[q]
else if i < k return Randomized-select(A,p,q-1,i)
else return  return Randomized-select(A,q+1,r,i-k)

Randomized-partition(A,p,r)
j=p+1
i=p
while j!=r
  if A[j] < A[r] j++ then swap A[j] and A[i]
  if A[j] > A[r] j++
swap A[i], A[r]

#  random-select in worst-caselinear time  
1：将N length 的array 分成 N/5 个长度为 5 的subarray  
2：find the median of each N/5 groups by first insertion sort  
3: use select recursively to find the median x of the n/5 medians found in 2  
4: partition the input array around the median-of-medians x using modified version of Partition.  

analysis: 从at least 3*[1/2*n/5] number of element > x (medians of the medians) vice versa  
T(n) = T(7/10n)+n+T(n/5)  
suppose we show that the running time is linear by substitution, for some big constant c  T(n) < cn
T(n) < c9/10n+an

### problem analysis when group divide by 7 and 3
T（n） =  T（n/3） + T(2/3n)+an  n(logn)
T（n） =  T(n/7) + T(5/7n)+an o(n) log

### 在仅仅只使用comparison去find ith smallest element in set of n element，同时你不许用额外的comparison 就可以找到 i-1th smallest and n-ith lager 
### Describe o（n） time algorithm to find  k numbers of element that closest to median of s
  因为前面提到了将group 分为 subgroup to find medians of the medians， （S - K/2S） =  roundup(x/2)*1/2*n/x

  


  
