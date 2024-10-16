
### List-Based Implementation
- **Unordered list**:
  - Operations (search, delete, min, max, predecessor, successor) take **O(n)** time.
- **Ordered list**:
  - Search: **O(log n)** (clearly way faster)
  - Insertion/Deletion: **O(n)**
  - Min/Max/Predecessor/Successor: **O(1)**

### Binary Search (not a tree)
- **Binary search** narrows down the search range in stages by comparing the key with the middle element.
- Key just refers to the value stored in each node that determines its position in the tree according to specific rules
- range of candidate items to be searched is halved after comparing the key with the middle element (repeatedly divides search space in half)
- Time complexity: **O(log n)** for search, but **O(n)** for insertion and deletion.
![[Pasted image 20240926145427.png]]

### Binary Search Trees (BSTs)
- A **BST** is a binary tree where:
  - Nodes in the left subtree store keys **less than or equal to the root's key.
  - Nodes in the right subtree store keys **greater than the root's key.
- Operations (search, insert, delete) in a balanced BST take **O(h)** time, where h is the height of the tree
![[Pasted image 20240926145855.png]]
### Dictionary ADT
- A **dictionary** is a dynamic set supporting operations like:
  - `Search(S, k)`, `Insert(S, x)`, `Delete(S, x)`
  - Additional operations for ordered dictionaries:
    - `Min(S)` and `Max(S)` to find the smallest/largest keys.
    - `Successor(S, x)` and `Predecessor(S, x)` to find the next larger/smaller element.

### Ordered Dictionary (proportional to height of tree)
![[Pasted image 20240926150558.png]]

### Searching in a BST
- To search for a key `k` in tree `T`:
  - If `k` is less than `T.key()`, search in the left subtree.
  - Otherwise, search in the right subtree.
- **Recursive and iterative algorithms** are both possible, with a time complexity of **O(h)**.
![[Pasted image 20240926150702.png]]
![[Pasted image 20240926150746.png]]
- Notice how based off the key value the side of the tree that is traversed is changed  
### Analysis of BST Search
- The running time for searching is **O(h)**, where `h` is the height of the tree.
- In the worst case (when the tree is unbalanced), this can be **O(n)**.
### BST Minimum and Maximum
- **Minimum**: Traverse the leftmost path from the root.
- **Maximum**: Traverse the rightmost path from the root.
- Both operations run in **O(h)** time.

### BST Successor
- To find the **successor** of a node `x` (the node with the smallest key greater than `x.key()`
  - If `x` has a right subtree, the successor is the **leftmost node** in that subtree.
  - If `x` has no right subtree, the successor is the lowest ancestor of `x` whose left child is also an ancestor of `x`.
- Successor finding takes **O(h)** time.
- if right tree is non empty 
![[Pasted image 20240926151027.png]]
![[Pasted image 20240926151437.png]]
- right subtree is empty
Biggest thing to remember with BST is right keys are greater than parent / root left trees are smaller than parent / root

### Pseudocode for BST Search and Successor
- Recursive and iterative search algorithms were presented, with clear pseudocode.
- Successor pseudocode identifies two cases (right subtree exists or doesn't) to efficiently find the next larger node.
![[Pasted image 20240926151526.png]]

---
### Part 2: 
### Overview
This lecture covers **Binary Search Trees (BSTs)**, focusing on insertion, deletion, tree traversal, and sorting, along with a discussion on balanced search trees.

### Binary Search Trees (BST)
- A **binary search tree** is a binary tree where:
  - Nodes in the left subtree have keys less than or equal to the root’s key.
  - Nodes in the right subtree have keys greater than or equal to the root’s key.
  
### BST Insertion
- Insert an element `z` (with NIL children (non existent)) into tree `T`:
  1. Search for the position where `z` belongs.
  2. Insert `z` at that position.
- Time complexity: **O(h)**, where `h` is the height of the tree.

### Insertion Pseudocode
```cpp 
// pseduo code
TreeInsert(T, z)
  y ← NIL              // Variable 'y' is used to track the parent of 'z'. Initially, it is set to NIL.
  x ← T                // Start from the root of the tree 'T' and traverse it to find the correct location for 'z'.

  while x ≠ NIL        // Continue traversing the tree until we reach a NIL position, indicating where 'z' should be inserted.
    y ← x              // Before moving down the tree, set 'y' to the current node 'x' (the parent of the node to be inserted).
    
    if z.key() < x.key()  // If the key of 'z' is less than the current node's key,
      x ← x.left()        // move to the left subtree.
    else                  // Otherwise,
      x ← x.right()       // move to the right subtree.

  z.setParent(y)        // After finding the correct position (NIL), set 'z's parent to 'y'.

  if y = NIL            // If 'y' is still NIL, it means the tree was empty, so insert 'z' as the root of the tree.
    T ← z
  else if z.key() < y.key()  // If 'z's key is smaller than its parent's key, insert 'z' as the left child of 'y'.
    y.setLeft(z)
  else                  // Otherwise, insert 'z' as the right child of 'y'.
    y.setRight(z)

```

### Printing tree traversal values
![[Pasted image 20240926152911.png]]![[Pasted image 20240926153658.png]]
- start at left most tree clear left then parent then right then root
- In an **in-order traversal** of a Binary Search Tree (BST), the goal is to visit the nodes in **ascending order** based on their keys
### BST Sorting
```cpp
TreeSort(A)
01 T ← NIL              // Step 1: Initialize the tree 'T' as empty (NIL).
02 for i ← 1 to n       // Step 2: Loop through each element in the list 'A'.
03    TreeInsert(T, BinTree(A[i]))   // Step 3: Insert each element into the BST.
04 InorderTreeWalk(T)   // Step 4: Perform an in-order traversal of the tree to print elements in sorted order.

```
![[Pasted image 20240926154203.png]]
- Since 5 is the first number it becomes the root then we build from there using the next key values
- Then we do an in-order traversal to list the elements in ascending order
![[Pasted image 20240926154536.png]]
- You only print the values at the lowest positions that makes sense I thought we were ignoring nodes

### BST Deletion
- Delete node x from a tree T
- cases: 
	- x has no children
		- if x has no children just remove x (current node)
	- x has one child
		- make x.parent() point to that child (we are deleting the current node)
		![[Pasted image 20240926154749.png]]
	- x has two children
		- find the successor (or predecessor) y - the sucessor of a node is the smallest node in its right subtree , pred is largest node in left subtree with key smaller than x
		- remove y (sucessor y is either a leaf node or has at most one child)
		- replace x with y
		- ![[Pasted image 20240926155335.png]]
		- ![[Pasted image 20240926155443.png]]

### Deletion Pseudo Code  (deletion is a little confusing)
```cpp
TreeSuccessor(x)
01 if x.right() ≠ NIL              // Step 1: If node `x` has a right child,
02    then return TreeMinimum(x.right())   // return the smallest node in the right subtree.
03 y ← x.parent()                   // Step 2: If no right child, move up to `x`'s parent.
04 while y ≠ NIL and x = y.right()  // Step 3: Traverse up until `x` is not the right child.
05    x ← y                         // Keep moving `x` up to the parent.
06    y ← y.parent()                // Move `y` up to the next ancestor.
07 return y                         // Step 4: Return the parent `y`, which is the successor.

```
![[d3.png]]- See how you shove the other node on the bottom and then delete have to go down right tree as left as possible to find successive node 