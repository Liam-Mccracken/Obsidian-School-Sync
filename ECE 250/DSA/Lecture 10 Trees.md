
### New Data Structure
- **Problem**: Linked lists have prohibitive linear access times.
- **Solution**: Trees offer better performance, achieving O(log N) time complexity for search, insert, and delete operations.
### Trees
- A **tree** is a collection of nodes, either empty or consisting of a root node and zero or more subtrees connected by edges.
### Tree Terminologies
- **Parent and Child**: Every node (except the root) has one parent, and nodes can have multiple children.
- **Leaves**: Nodes with no children.
- **Siblings**: Nodes sharing the same parent.
- **Path**: A sequence of nodes where each node is the parent of the next one.
- **Depth**: The length of the path from the root to a node. (equal to depth of deepest leaf)
- **Height**: The longest path from a node to a leaf. (leaves are height 0, height = height of root)
- **Length:** Number of edges on the path
![[Pasted image 20240925101035.png]]
### Example: Unix Directory
![[Pasted image 20240925101312.png]]
### Binary Trees
- A **binary tree** is a tree in which each node has at most two children.
- The depth of an average binary tree is typically smaller than the total number of nodes (N), though it can reach N-1 in the worst case.

### Binary Tree Abstract Data Type (ADT)
- **Accessor functions**:
  - `key()`: Returns the key of the node. (int - value stored in each node that determines the node position according to tree specific properties) 
  - `parent()`: Returns the parent node. 
  - `left()`: Returns the left child node.
  - `right()`: Returns the right child node.
- **Modification procedures**:
  - `setKey(k)`: Sets the key of the node.
  - `setParent(T)`: Sets the parent node.
  - `setLeft(T)`: Sets the left child node.
  - `setRight(T)`: Sets the right child node.
### Expression Trees
- **Leaves** represent operands (constants or variables).
- **Internal nodes** represent operators.
- Expression trees may not be binary if they contain non-binary operators.
![[Pasted image 20240925101557.png]]
### Tree Traversal Techniques
Tree traversal is the process of visiting **every node** in a tree. The three main types of tree traversal are:

1. **Pre-order Traversal** (Node, Left, Right) 
   - Example of a prefix expression: `++a*bc*+*defg`
   - visit root, traverse left subtree fully. traverse right subtree recursively fully

3. **Post-order Traversal** (Left, Right, Node)
   - Example of a postfix expression: `abc*+de*f+g*+`
   - traverse left tree, right, node

4. **In-order Traversal** (Left, Node, Right)
   - Example of an infix expression: `a+b*c+d*e+f*g`
   - traverse left subtree recursively in order, visit root, traverse right subtree

### References
- CLRS: Chapter 10.4 and Appendix B.5
- Weiss: Chapter 4

