### connectivity of graph
 ```
 >Depth-first-search()
   -initialize every visited[v] = false  
   -for any v,if not visited[v]
          explore(G,v) 
````
```          
>explore(G,V)    //explore every thing reachble form V  
  -visited[v] = true  
  -for every (v,w) if not visited[w]:explore(G,w)  
```
