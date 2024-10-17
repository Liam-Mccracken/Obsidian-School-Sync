## 1. Disk-Based Data Structures
- Traditional search trees assume datasets fit in main memory. (RAM memory)
	- data sets need to be small enough to fit into this 
- Larger datasets require secondary storage (e.g., hard disks).
- Adapt search trees for secondary storage (for larger data sets)

## 2. Principles of B-Trees
- Pointers in data structures point to disk locations. (as opposed to main memory addresses)
- If X is a pointer to an object 
	- if x is in main memory key[x] refers the the value at x
	- otherwise DiskRead(x) reads the object from the disk into main memory, and DiskWrite(x) writes it back to the memory
- Nodes are loaded into memory as needed, but all nodes stored in other memory we use key references to load the values 
	- As nodes are loaded we look for the key in that notes and only continue if it is found
	![[Pasted image 20241009095425.png]]
	
## 3. Binary-Trees vs. B-Trees (balanced tree) 
- B-trees are better suited for managing large datasets.
- The size of a B-tree node is determined by the page size, one page = one node
- Height is logarithmic based on the branching factor.
	- B-tree: logarithm of base, e.g. , 1000
	- Binary tree: logarithm of base 2 
- Allows a large number of keys and children per node.
- Binary tree nodes can have at most 2 children, **B Trees** can have more than two children a B tree of degree t can have up to 2t-1 keys in each node meaning they have have up to 2t children, which allows B-trees to keep a much flatter structure and thus better for larger data sets 

## 4. B-tree Definitions
- Node fields include `n[x]` (number of keys), `key1[x]` through `keyn[x]` (keys), and `leaf[x]` (leaf status) true if leaf node, false if internal node
	- If internal node, then c1[x],...., cn[x] : Pointer to children nodes
- All leaves have the same depth , leaf nodes have no children
- In a B-tree of a degree t:
	- Every node other than the root must have at least t-1 keys, every internal node other than the root thus has at least t children
	- every node may contain at most 2t-1 keys therefore, and internal node may have at most 2t children
	## **Children**
	- must have **at least** t children (aside from root)
	- A node can have at most 2t children
  **Number of keys in a node**
	- A node must contain at least t-1 keys (expect root)
	- At **most** a node contains 2t-1 keys
	- root  node has between 0 and 2t children (i.e between 0 and 2t-1 keys)
		- ![[Pasted image 20241017160741.png]] at most 1 more child than whats in root node as its the range of values (if greater than right most look right if less than left most look left)
## 5. Height of a B-tree
- Height `h` is bounded by the logarithm of the number of keys.
- B-trees are efficient for storage and retrieval of large datasets.
![[Pasted image 20241009103422.png]]
- T controls the density of data within the nodes, **all leaves of a B -tree are at the same level**
- B-Tree grows and shrinks from the root which is unlike Binary Search Tree. Binary Search Trees grow downward and also shrink from downward
## 6. B-tree Operations
- **Searching**: Generalized tree search, starting at the root.
	- ![[Pasted image 20241017162219.png]]
- **Creating an Empty Tree**: Initialize root node.
	- ![[Pasted image 20241017162227.png]]
- **Insertion**: Involves splitting nodes.
	- 
- **Deletion**: Complex due to rebalancing requirements.

## Rules of B - Trees
- leaves of the trees must be at the same level 
- We choose max num of keys minimum num of keys is always half of max
- once max # of keys are reached in the node we split the node 
## 7. Splitting Nodes
- Nodes split when full (2t - 1 keys).
	- ![[Pasted image 20241017162307.png]]
- Splitting creates space for new keys.
- New nodes and keys are adjusted accordingly.
- Pushed nodes are pushed into the parent until the max # of keys is present which then would mean u split the root key 
- Split parent into 2 nodes and push the parent this is why the height grows upwards (tree only gets taller when the root node is split and pushed)
![[Pasted image 20241017161516.png]]
![[Pasted image 20241017161533.png]]

## 8. Inserting Keys
- Recursively insert keys, ensuring nodes are non-full.
- Elements are always added on the leaf of the tree we continually add keys by traversing down the root until a leaf is met
- Special case: if the root is full, it splits and grows upwards the middle key in the range is pushed as the new node (still must follow BST principals)
- Insertion is O(th) CPU time and O(h) for disk I/O

## 9. Deletion
- look through tree finding for the key value once its found delete it from the tree
	- Case 1: Key in a leaf node(just talked about) simply just delete
	- Case 2: Key in node has fewer than the minimum count
		- ![[Pasted image 20241017165915.png]] ![[Pasted image 20241017170130.png]]
		- we let the key from the sibling replace the parent node and take the parent node down to the unbalanced node to ensure it still follows the minimum key count
	- Case 3: We can merge nodes back together by taking a key from the adjacent nodes as well as from the parent to make a new node
		- ![[Pasted image 20241017170157.png]]
Deletion has a run time on the CPU: of O(th) = O(tlogn)

## Key Take Aways
- A node can have at most 2t children
- must have atleast t children
- node must contain t-1 keys and at most 2t-1 keys (aside from root)
- Look at insertion and deletion cases when it comes to having to rebalance the tree


