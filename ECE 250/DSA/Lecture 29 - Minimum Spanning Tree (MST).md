### Spanning Tree
- **spanning tree** of G is a subgraph which
	- is a tree
	- contains all vertices of **G**
	![[Pasted image 20241129204236.png]]
## Minimum Spanning Trees
- Undirected, connected graph G = (V,E) , **Weight** function W:E->R (assigns cost or length or other values to edges)
- Spanning tree: tree that connects all the vertices
	- MST - tree T that connects all the vertices and minimizes the weight w(T) = sum(w(u,v))
	![[Pasted image 20241129204417.png]]
	- we have to make V-1 choices (edges of the MST) to arrive at optimization goal
	- After each choice the problem size is one vertex smaller than before
	- DP at each step wouldn't work because it consider all possible choices (edges) into to new algorithm
### Greedy Algorithms
- Path being picked is regarded as the best option based on a specific criterion without considering future consequences
- **Greedy** algorithms can be used to solve optimization problems, if:
	- there is a optimal substructure & we can prove that a greedy choice at each iteration leads to an optimal solution
![[Pasted image 20241129205342.png]]
- invariant: condition or property that **remains true** throughout the execution of an algorithm. Loop invariant is a guarantee that the set of edges A, is always a subset of some **MST**
- Eventually A contains V-1 edges and A forms a MST
![[Pasted image 20241129205519.png]]

#### **Various Definitions:**
![[Pasted image 20241129212656.png]]
- V-S means set of all vertices in V that are not in S (set subtraction) 

## Generic MST Algorithm
![[Pasted image 20241129213034.png]]
Ok.......


## Pseudocode Assumptions
![[Pasted image 20241129213144.png]]

## Prim-Jarnik Algorithm 
- **Vertex based algorithm**
- Grows one tree T, **one vertex at a time**
- A set A covering the portion of T already computed
- Label the vertices v outside of the set A with v.key()
	- this is the minimum weight of an edge connecting v to a vertex in A, v.key() = inf , if no edge exists
	![[Pasted image 20241129213820.png]]
	- we use a priority queue ADT to maintain 
	- **How We Start:**
		- start from any vertex s, add all edges from s to the priority queue, with weights as priorities, the priority queue initially holds edges connected to s, and the smallest weight edge is extracted, every iteration we extract the **smallest weight edge** adding new edge options as the verticies continue to be visited
![[Pasted image 20241129214132.png]]
![[Pasted image 20241129214140.png]]
![[Pasted image 20241129214214.png]]
___
## MST Pt 2

## Kruskal's Algorithm 
- where prim was a **vertex** based algorithm this is a edge based algorithm
- Add the edges one at a time, in increasing weight order
- The algorithm maintains A - **a forest of trees**. An edge is accepted if it connect vertices of distinct trees (the cut respects A)
- Process: 
	- look for the smallest edge and select it, continue to select these edges and a MST will form
	- We must use a disjoint-set ADT to store the edges as they are not naturally connected to each other
![[Pasted image 20241129215045.png]]
![[Pasted image 20241129215049.png]]
this will store our edges as they accumulate
![[Pasted image 20241129215127.png]]
![[Pasted image 20241129215155.png]]
- Always look for smallest edges that don't form a cycle
![[Pasted image 20241129215241.png]]
- eventually we will result in a MST 
![[Pasted image 20241129215307.png]]