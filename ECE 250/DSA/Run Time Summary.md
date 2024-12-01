**Quicksort** - Worst case run time : O(n^2)

**Comparison** sorting best possible run time : O(n log n)

**Counting sort**: has O(n + k) run time
- n num of elements in input array
- k is the range of input values, specifically diff between max and min

**Radix Sort:** O(d x (n+b)) Time complexity
- d is # of digits in largest num
- n is num of elements
- b is the base (10 for dec)
![[Pasted image 20241110140414.png]]
**BFS:** O(V + E) where v is vertex's and E is edges
DFS: O(V + E)

![[Pasted image 20241128225506.png]]![[Pasted image 20241129201951.png]]
# Topological Sort Run time
- DFS : O(V + E) time
- Insert each of the | V | vertices to front of linked list which is constant O(1) per insert
- Making it the same as DFS O(V+E)
![[Pasted image 20241129214224.png]]
![[Pasted image 20241129215309.png]]
![[Pasted image 20241129223022.png]]

- Floyd Warshall: Has a runtime of O(n^3)
- 