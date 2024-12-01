----
#### **1. Graphs – Definition**

- A graph G=(V,E)G = (V, E)G=(V,E):
    - V: Set of vertices.
    - E⊆V×V:  Set of edges connecting vertices.
	- An **edge** e = (u,v) which is a pair of verticies
- Types:
    - **Directed graph**: Edges have a direction 
    - **Undirected graph**: Each edge is bidirectional we represent (u,v) ∈ E
![[Pasted image 20241128194140.png]]
---
#### **2. Applications**

Graphs are used to model:

- Electronic circuits, networks (transportation, communication).
- Relationships between people, processes, or concepts.

---
#### **3. Graph Terminology**

- **Adjacent vertices**: v is adjacent to u iff (u,v)∈E  (only if share the same edge)
- **Degree**: Number of adjacent vertices.
	![[Pasted image 20241128194525.png]]
- **Path**: Sequence of vertices where each pair is connected by an edge.
- **Simple path**: Path with no repeated vertices.
- **Cycle**: Simple path where the first and last vertices are the same.
![[Pasted image 20241128194606.png]]
- **Connected graph**: Every pair of vertices has a path connecting them.
![[Pasted image 20241128194628.png]]
- **Subgraph**: A subset of vertices and edges forming a graph.
- **Connected component**: A maximal connected subgraph.
![[Pasted image 20241128194749.png]]
- **Tree**: A connected graph with no cycles.
- **Forest**: A collection of trees.
![[Pasted image 20241128194823.png]]
---
#### **4. Data Structures for Graphs**
1. **Adjacency List**:
    - Each vertex has a list of its adjacent vertices.
    ![[Pasted image 20241128194908.png]]

2. **Adjacency Matrix**:
- Matrix M with entries for all pairs of vertices 
- M[i,j] = true - there is an edge (i,j) in the graph
- M[i,j] = false - there is no edge (i,j) in the graph
- Space = O(|V|^2)
![[Pasted image 20241128202156.png]]
## Pseudocode Assumptions
- Graph ADT with an operation
	- V(): VertexSet
![[Pasted image 20241128202414.png]] 
---
#### **5. Graph Searching Algorithms**

Systematically explore every vertex and edge of a graph. Applications include:

- Compilers, graphics, maze-solving, mapping, and networks.

---
#### **6. Breadth-First Search (BFS)**
- Traverses a **connected component** of a graph, and in doing so defines a **spanning tree** with several useful properties 
- The starting vertex S, it is assigned a distance 0
<font size= 6>Process </font size>
- In the first round, the string is unrolled the length of one edges, and all of the edges that are **only one edge away** from the anchor are visited (discovered), and assigned distances of 1
- In the second round, all the new edges that can be reached by unrolling the string 2 edges are visited and assigned a distance of 2
- **This continues until every vertex has been assigned a level**
- The label of any vertex then corresponds to the length of the shortest path (in terms of edges) from s to v
Code: 
![[Pasted image 20241128203238.png]]
- A vertex becomes **white** if its undiscovered
- A vertex is **gray** if it has been discovered but not all of its edges have been explored
- A vertex is **black** after all of its adjacent vertices have been discovered
### Run time
- given a graph G = (V,E)
	- Vertices are enqueued if their color is white
	- Assuming that en- and dequeuing takes O(1) time the total cost of this operation is O(V)
	- Adjacency list of a vertex is scanned when the vertex is dequed (and only then)
	- The sum of the lengths of all list is O(E) so O(E) time is spent on scanning them
	- Initializing the algo takes O(V)
- Making the Total run time O(V+E) (linear in the size of the adjacency list representation)
![[Pasted image 20241128204254.png]]
- Always will compute a Tree
![[Pasted image 20241128204403.png]]
- BFS is surface level u explore all 1 distance nodes then mode on DFS u go fully
- BFS uses a queue where DFS uses a stack (queue FIFO , stack LIFO)
![[Pasted image 20241128211144.png]]
____
## Depth-First-Search
- DFS in a graph G is like wandering in a labyrinth with a **string** and a **can of paint**
	- We start at vertex s, tying the end of our string to the point and painting s "visited (discovered)". Next we label s as our current vertex called u
	- Now we travel along an arbitrary edge (u,v) 
	- If edge (u,v) leads us to an already visited vertex v we return to u
	- If vertex v is unvisited, we unroll our string, move to v, paint v "visited", set v as our current vertex, and repeat 
- Eventually all incident edges on u lead to visited vertices, we then **backtrack** by unrolling our string to a previously visited vertex V. then V becomes our current vertex and we repeat the previous steps. 
![[Pasted image 20241128211844.png]]
- initialize: color all verticies white
- Visit each and every white vertex using DFS-Visit, each call to dfs-visit roots a neew tree of the depth first forest at vertex u
- When DFS returns, every vertex u is assigned
Vertex u is
- white before time u (undiscovered)
- gray b/w d[u] & f[u]  - discovered but not fully explored
- Black there after (all discovered)
	- Gray verticies form a linear chain -> corresponds to a stack of vertices that have not been exhaustively expolored

## Run time
- the loops in DFS take time O(V) each, exclusing time to execute DFS visit
	- its only invoked on white vertices, and 
	- paints the vertex gray immediately
	- ![[Pasted image 20241128212255.png]]
![[Pasted image 20241128212319.png]]
- DFS uses a stack for gray vertices and pops off the LIFO element to know what to return to when black is reached
- BFS uses queue for gray vertices and pops off FIFO element when all adjacent sides have been seen 
![[Pasted image 20241128212459.png]]

## DFS Parenthesis Theorem
![[Pasted image 20241128212540.png]]
![[Pasted image 20241128214143.png]]
![[Pasted image 20241128214150.png]]
![[Pasted image 20241128214318.png]]
- So basically if discovered alr, forward edge