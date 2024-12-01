## Analysis of algorithms
- Asymptotic Notations (upper, lower, tight bounds etc)
- Recurrences (all 3 methods of solving)
- Algorithm Techniques
	- Divide and conquer 
		- Merge Sort
		- Quick Sort
		- Binary Search
	- Dynamic Programming
		- Problem has recursive nature, but when you try to draw you will see some sub problems overlap with each other (solved in exponential behaviors)
		- Ex: Matrix multiplication, LCS, CheckerBoard, Floyd-Warshall (she will post sol'n to checkerboard and LCS) 
	- Greedy Algorithms 
		- Prim-Jarik, Dijikstra
	- Nothing about iterative algorithms as that was part of 250


## Toolbox for DSA
- Simple DSA and ADTS
	- Arrays, all sorts of linked list, stackas , queues, heaps
- Dictionarys
	- ... She went too fast lol

## Toolbox for Algo
- Sorting
	- Insertion, merge,quick,counting sort,radix sort, in-order traversals on unbalanced trees, priority queues

## Toolbox of algorithms
- Graphs
	- Graph traversals
		- BFS (O(V+E))
		- DFS(O(V+E))
		- Topological Sort (Based on DFS which is linear, then add to beginning of linked list)
	- MST()
		- Prim-Jarnik (Based on verticies, uses min priority queue) O(eloge)
		- Kruskal (O(eloge)), based on edges where prim is based on nodes
	- SSSP (Consider starting node and try to find shortest path from starting to every other)
		- Dijkstra (O(elogv))  -  
		- Bellman-Ford(O(V * E)) - better when we have negative edges  
	- APSP
		- Floyd-Warshall - DP approach O(VQ)

Reccurences
- T(N = aT(n/b) + cn +d  -> Geo series
- T(N) = T(n-b) + cn +d
	- Arith series

### Types of Graph exercises
- Decide what are the vertices and what are the edges
- Un-weighted graphs,
	- traverse and check(do) something
		- use DFS or BFS
	- Find shortest path
		- use BFS (unweighted) shortest is counting the edges from starting node
	- schedule or order dependent activities or processes
		- Use topological sorting
- Weighted graphs
	- Decide what are the weights (distance,gaining or losing money, time diff, waiting time for airport etc)
	- Shortest paths, shortest times (positive and negative edges)
		- Use dijkstra (positive edges)
		- Use bellman-ford (pos and negatvive)
	- Minimum (maximum) spanning tree
		- use prim-jarnik or kruskal  
	- Finding a critical path in a schedule (longest path in DAG)
		- Use topological sorting on a DAG of activities 


## preparation for the exam
- First, concentrate of lecture note
	- Lec 1 to 36 on learn
- Second, studying CLRS book whenever is needed (although u need to know the concepts)
- Third, solving exercises by yourself!!!!
	- When solving write your solutions down



## More material 
- Solved exercises in tutorials / lecture (70) 
	- Check two modules on learn "lec notes" tutorials
- PRevious 250 MT and Final Exams (60)
- Sol'N for sample questions 



## Final 
- 4- 630
- Calc allowed
- Structure 
	- Seven questions with at least two sub-problems 
	- Algorithm analysis (20 marks)
		- CLRS 2,4,5,A.1,10)
	- Hashing (5 Marks)
	- Tree and Tree Traversals (10 Marks)
		- CLRS 12,18,B.5 , Weiss 4
	- Sorting Algo, Heaps, HeapSort, Priority Queues (15 marks)
		- CLRS 6,7,8
	- Graphs (30 Marks)
		- CLRS 22,24,24,25,B.4
	- Optimization Problems (15 Marks) (DP approach)
		- CLRS 15,16
	- NP - Completeness (5 marks)
		- CLRS 34