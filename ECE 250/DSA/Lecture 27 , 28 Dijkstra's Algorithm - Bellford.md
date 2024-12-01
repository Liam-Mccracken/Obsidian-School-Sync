## Shortest Path
- Generalized distance to weighted settings
- Digraph G = (V,E) with weight function W: E-> R (assigning real values to edges)
- Weight of path p= v1->v2->...-> vk 
![[Pasted image 20241128215901.png]]
**Shortest path = a path of the minimum weight!**
![[Pasted image 20241128215928.png]]
- **BFS is a unweighted shortest-path algorithm** don't forget that!

- **Theorem:** Subpaths of shortest paths are shortest paths 

	![[Pasted image 20241128220035.png]]
	![[Pasted image 20241128220527.png]]
	- This allows for recursion
### **4. Negative Weights and Cycles**

- **Negative Edge Weights**:
    - Allowed in graphs unless there are **negative weight cycles**.
    - **Negative Weight Cycle**: A cycle where the total weight is negative.
        - Such cycles allow paths with arbitrarily small lengths, making shortest paths undefined.
- **Shortest Path Properties**:
    - Shortest paths cannot have cycles (cyclic paths can always be reduced by removing the cycle).
    - Any shortest path in a graph has at most n−1 edges (for nnn vertices).

### **5. Shortest Path Tree**
- **Output of SSSP Algorithms**:
    - A **shortest path tree** rooted at s.
    - For each vertex v:
        - `v.parent()`: The predecessor of v in the shortest path from sss.
        - `v.d()`: The shortest path distance from s to v.
- **Vertex ADT Operations**:
    
    - `adjacent()`: Returns vertices connected to v;
    - `keyd() / setd()`: Get or set v.d(), the distance estimate.
    - `parent() / setparent()`: Get or set v’s predecessor.

### **6. Relaxation**
![[Pasted image 20241128221133.png]]

## Dijkstra's Algorithm
- **non - negative edges weights**
- Like BFS (if all weights 1 simply use BFS)
- Use Q, a priority queue ADT keyed by v.d() (BFS used FIFO queue, here we use a PQ, which is re-organized whenever some **d** decreases) where v.d() represents the distance 
- v.d() is updated through relaxation process, if v.d() is greater than the distance of u + weight then change v to be u as this is now the parent, this is why we pass u : vertex from what we're processing, v: neighboring vertex we are trying to relax, i.e **next node to explore will be that of the lowest weight from current node**

- Every exploration we update our estimates then choose next node
![[Pasted image 20241128223015.png]]
- Set all weights initially to infinity, set parent to nothing as we haven't explored anything
- For starting node s set the distance to 0 , S is the set of vertices for which the shortest path has been finalized
- Initialize a priority queue of the graph with all vertices of G, keyed by their distance, vertices with smaller v.d() values will be processed first
- While the queue is not empty 
	- Extract u, remove the vertex u with the smallest distance from Q 
	- Ensure all u.d() is the shortest distance from s to u
	- Add U to the set of vertices
- For each vertex v adjacent to u 
	- Relax the edge (u,v) ( this will find the overall shortest paths regardless)
		- Check if the shortest path to v can be improved by going through u
		- Update v.d() and v.parent() if a shorter path is found
	- Modify Q
		- After v.d() is updated, the priority queue Q is reorganized to reflect the new distance estimate for V
![[Pasted image 20241128225418.png]]
![[Pasted image 20241128225430.png]]
![[Pasted image 20241128225506.png]]
Way faster with binary heap to store logs 

___ 
## Bellman-Ford Algorithm 

### Recall:
- Shortest path of a function gives a generalized weighting
- Weight of a vertex is the summation of a vertex which come before it 
![[Pasted image 20241129195603.png]]
- The **shortest path** is a path of the minimum weight

Earlier we noted how Dijkstra's algorithm does not work when there are negative edges 
	- we can no longer be greedy any more on the assumption that the length of paths will only increase in the future, we have to consider the possibility that they wont
**Bellman-Ford Algorithm** detects negative cycles (returns false) or returns the shortest path tree

### Bellman-Ford Code
![[Pasted image 20241129195815.png]]
- For all values initially set to infinity, we have no starting set to NIL, set source distance to 0
- Relaxation begins for Vertex - 1 times
	- Update the distance d(v) if d(v) > d(u) + w(u,v)
	- The current shortest distance to v is d(v) the fistance to v via u is d(u) + w(u,v
		- If d(u) + w(u,v) is **less than** the current d(v) we update d(v) to be d(u) + w(u,v) meaning we have found a shorter path to v (look at dijkstra if confused)
		- if the condition holds update parent
- Eventually after V-1 check for negative weight cycles for each edge if v.d() > u.d() + G.w(u,v) then negative weight cycle exists and return false as the shortest path cannot be computed due to the infinitely decreasing cycle 
- Otherwise return true because we have successfully found the shortest path

## Bellman-Ford Example
![[Pasted image 20241129201845.png]]
![[Pasted image 20241129201929.png]]
![[Pasted image 20241129201937.png]]
![[Pasted image 20241129201951.png]]


## Shortest Path Of A DAG (directed acyclic graph)
- Easier to find shortest path, it is easy to find the order in which to relax the algo
- Topological sorting!
- A DAG is a direct graph with **no cycles** 
![[Pasted image 20241129202202.png]]
- Often used to indicate precedence and can be sorted using **topological sorting**

## DAG Theorem
- a direct graph G is acyclic if and only if a **DFS of G** yields **no back edges** (descendent to ancestor)
- **Recall:**
![[Pasted image 20241129202401.png]]
![[Pasted image 20241129202421.png]]

## Topological Sort
- Sorting of a direct acyclic graph (DAG)
- **linear ordering of all its vertices** such that any edge (u,v) in DAG, u appears before v in the ordering
#### Algorithm:
![[Pasted image 20241129202603.png]]
- **vertices are arranged from left to right in order of decreasing finishing time** 
![[Pasted image 20241129202729.png]]
- DFS on shirt, shirt finishing at jacket making it the first element of the linked list as it finished, we continue to add on with each finish as we move along the list
### Run time: 
- DFS: O(V+E) time
- Insert each of the V vertices to linked list which is constant linear O(1) per insertion
- Making runtime same as DFS O(V+E)
![[Pasted image 20241129203039.png]]
- uses Topological sort
- O(V+E) - only one relaxation for each edge
- V times faster than Bellman-Ford