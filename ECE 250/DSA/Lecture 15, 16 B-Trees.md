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
- Nodes are loaded into memory as needed, but all nodes stored in other memory we use key references to load the values as need
	![[Pasted image 20241009095425.png]]
	
## 3. Binary-Trees vs. B-Trees
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
	- root  node has between 0 and 2t children (i.e between 0 and 2t-1 keys)

## 5. Height of a B-tree
- Height `h` is bounded by the logarithm of the number of keys.
- B-trees are efficient for storage and retrieval of large datasets.
![[Pasted image 20241009103422.png]]
- T controls the density of data within the nodes, all leaves of a B -tree are at the same level
- B-Tree grows and shrinks from the root which is unlike Binary Search Tree. Binary Search Trees grow downward and also shrink from downward
## 6. B-tree Operations
- **Searching**: Generalized tree search, starting at the root.
	- 
- **Creating an Empty Tree**: Initialize root node.
- **Insertion**: Involves splitting nodes.
- **Deletion**: Complex due to rebalancing requirements.

## 7. Splitting Nodes
- Nodes split when full (2t - 1 keys).
- Splitting creates space for new keys.
- New nodes and keys are adjusted accordingly.

## 8. Inserting Keys
- Recursively insert keys, ensuring nodes are non-full.
- Special case: if the root is full, it splits and grows upwards.
- Insertion is O(th) CPU time and O(h) for disk I/O.

---
# Part 2 


## 1. B-tree Operations (Continued)
- **Searching**: Locate a key starting from the root, traversing downwards.
- **Insertion**: Recursive insertion into non-full nodes.

## 2. Deleting Keys
- Deletion has three scenarios:
  - **Case 1**: Key in a leaf node—delete directly.
  - **Case 2**: Key in an internal node—replace with a predecessor or successor.
  - **Case 3**: Key suspected to be in a lower-level node—descend to the appropriate node.
- Before descending, ensure the node has at least `t` keys.

## 3. Deleting Keys - Distribution
- Distribute keys if a sibling has `t` keys.
- Adjust keys between nodes to maintain balance.
- Consider which nodes are loaded from disk for efficiency.

## 4. Deleting Keys - Merging
- Merge nodes when siblings have `t - 1` keys.
- Reduces tree height when necessary.
- Maintains the tree’s balanced nature.

## 5. Deletion: Running Time
- Most deletions occur at the leaf level.
- O(h) disk operations and O(th) CPU time.

## 6. Two-Pass Operations
- Practical implementations use two passes (down and up).
- **Down**: Locate the node for deletion or insertion.
- **Up**: Split, merge, or distribute as necessary.
- Use a buffer to minimize re-reading nodes.

## 7. Other Access Methods
- **B+-trees**: Data keys stored only in leaves, commonly used in databases.
- Non-leaf nodes store pointers to sub-trees and key ranges.
