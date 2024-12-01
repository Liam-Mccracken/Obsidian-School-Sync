- We want to compute a table giving the length of the shortest path between any two vertices
- We also want to get the shortest paths themselves
Idea: Call Dijkstra or Bellman-Ford |V| Times
![[Pasted image 20241129221638.png]]


## Adjacency Matrix
![[Pasted image 20241129221657.png]]
- Showing 1 if the edge connects to another vertex

![[Pasted image 20241129221918.png]]
- Same idea just with weights instead of true or false 

![[Pasted image 20241129222236.png]]
- how do we make the shortest path matrix?
![[Pasted image 20241129222255.png]]
- if intermediate jokes exist then 1 otherwise  0
![[Pasted image 20241129222456.png]]
- if intermediate nodes cost is x

### Call back to Dynamic Programming
- Floyd-Warshall is **dynamic programming** algo 
	- Recall: A dynamic programming algorithm is a computer science technique that solves problems by breaking them down into smaller subproblems and reusing solutions to overlapping subproblems
	- consider intermediate vertices of a path
	- compute and store solutions to sub-problems, combine those solutions to solve larger sub problems
	- Floyd finds the shortest path b/w **ALL PAIRS** of vertices

![[Pasted image 20241130090027.png]]
## Steps:
- Start with a degree 0 matrix this is your base weights
- Move to a degree 1 matrix meaning you see the paths from all nodes other than 1 that use 1 as intermediate values to end up at the node (as we want the shortest path from all veritces and all edges)
- We continue this process moving up the matrix for each degree and stop at degree 4 as we willi have our final answer
![[Pasted image 20241130090224.png]]
- Logic is as follows, if the distance of current pair is greater than the summation of the other two pairs then the other two pairs become your new value for the shortest path, otherwise it remains the same
![[Pasted image 20241130090409.png]]
- for each rows continually find the minimums of the intermediate vertices / paths 
- Overall this gives us a run time of O(n^3)