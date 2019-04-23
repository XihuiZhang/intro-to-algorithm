# problem
  find the kth smallest nubmber in array using o(n) time

# main idea
  just select one element from array not to sort,decreasing the number of comparision  
  using random()  select a element to be boundary of subarray whose value less than && subarray of value bigger  
  and random-partition to construct that, we only go on  recurrsively this step on less or big array where kth number in
  using i j as index for less and big area,   
  
  constrcuting area by comparing  A[j] with A[e],if A[j] > A[j] j++ incresing the area of big than A[e]   
  else swap A[i+1] and A[j] to incresing area of less  
  scan over swap A[i+1] and A[e] ,      | less   |A[p] | big |   comparing p and k to  
  return  randomselect(A,b,p,k) k > p    
          randomselect(A,P,e,k-p) k < p  
          A[p]  (p == k)  
# pseducode
```
  partition(A,b,e)
    x = A[e]
    i = b-1
    for j = b to e-1
        if A[j] <= x
           swap(A,i+1,j)
           i = i + 1
    swap(A,i+1,e)
    return i+1
  
  random-partition(A,b,e,k)
   p = random(b,e)
   swap(A[e],A[p])
   return partition(A,b,e)
 
  randomselect(A,b,e,k)
    i = random-partition(A,b,e,k);
    if i == k return A[k]
    if( i > k) randomselect(A,b,i,k);
               randomselect(A,i,e,k-i);
    
 ```   
# correctness of idea
  time  of algorithm can be represent as T(n) = T(n/k)+T(n)      
  i = random()    
  1/k =(number of  element > A[k])/(whole element number)  or (number of  element < A[k])/(whole element number)
  we can divide whole array into n/5 nubmers array whose length is 5, select median of those array to constrcut a median array  
  select median of median array and prove these is   
  at least 3/10n > median of median, 3/10n < median of median  
  T(n) = T(n/5)+T(7/10*n)+n ------>o(n)
  
# c++code
```

```
  
  
  
