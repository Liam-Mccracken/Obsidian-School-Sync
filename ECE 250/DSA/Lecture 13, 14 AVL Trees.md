
## Binary Search Tree (BST)
- **Worst-case height:** O(N) (if the tree degenerates into a list).
- **Ideal height:** Θ(log N).
- **Goal:** Maintain height as O(log N) for efficiency in insertion, deletion, and searching.

---

## Balanced Tree?
- Balance suggestions:
  1. Left and right subtrees of the root have the same height.  
    **Issue:** Subtrees can still be skewed.
  2. **Every node must have left and right subtrees of the same height.**  
    **Issue:** Only complete binary trees satisfy this condition.
- **Chosen approach:** For each node, the height difference between left and right subtrees must be at most 1.

---
## AVL Tree
- **Definition:** First balanced binary search tree (named after Adelson-Velskii and Landis).
	- **AVL IS A BST** in which for every node in the tree, the height of the left and right subtrees differ **by at most** 1
- **Property:** Height difference between left and right subtrees for any node is at most 1.
  - Height of a subtree: max # of edges to a leaf.
  - Height of an empty subtree: -1.
![[Pasted image 20240927100636.png]]
- Side differs by at most 1 in height
---

## AVL Tree - Minimum Number of Nodes
- Recursive relation for minimum number of nodes \(N_h\) in AVL tree of height \(h\):  
	- Nh​=Nh−1​+Nh−2​+1 (number of nodes at height h is the sum of the minimum number of nodes at height h-1 and h-2, plus one for root node)
 
- **Key Result:** The height of an AVL tree is O(log N) , this ensures that operations like searching, inserting, and deleting in an AVL tree take O(log N) time which is very efficient compared to an unbalanced tree

---

## Insertion in AVL Tree
- Follows standard BST insertion but may cause an AVL property violation.
- only nodes that are on the path from the insertion point to the root might have their balance altered
- **Restoring Balance:** Rebalance the tree by checking nodes along the insertion path and applying rotations if needed.
![[Pasted image 20240927101600.png]]
- As we cant have a height difference greater than 1
---
## Rebalancing Cases
- Let \( \alpha \) be the node that requires rebalancing:
  1. Left subtree of left child.
  2. Right subtree of left child.
  3. Left subtree of right child.
  4. Right subtree of right child.

---
## Rotations
- **Single Rotation:** Used for cases where insertion is on the "outside" (left-left or right-right).
- **Double Rotation:** Used for cases where insertion is on the "inside" (left-right or right-left).

### Insertion Algorithm 
- insert the new key as a new leaf just as ordinary BST
- trace path from new leaf to root, for each node x encountered check if height of left(x) and right(x) differ by at most 1
	- if yes proceed to parent, otherwise perform either a single or double rotation to balance the tree
![[Pasted image 20240927102353.png]]
Case one left subtree of right child, rotate root to balance tree
![[Pasted image 20240927102501.png]]
### Case 5 Single Rotation Right right
![[Pasted image 20240927102524.png]]
![[Pasted image 20240927103013.png]]
- Just try to logically think of where the rotation would be needed



---
![[Pasted image 20240927103037.png]]
- Note this is left child of right subtree so single rotation wont wont
- Just remember **L-L or R-R = single rotation** L-R or R-L = double rotation

## Single Rotation Fails (Cases 2 & 3)
- **Problem:** Single rotation doesn’t fix AVL property when the imbalance is in an “inside” case (left-right or right-left).
- **Solution:** Double rotation is needed to fix these cases.
![[Pasted image 20240927102706.png]]
subtrees differ by more than 12

---
## AVL tree part 2

## AVL Trees
- **Definition**: A balanced Binary Search Tree (BST) where the height of left and right subtrees differs by at most 1. - 
- **Height**: - Height of a subtree: Maximum number of edges to a leaf. - Height of an empty subtree: -1.
## Rotations for Rebalancing (Recall this occurs when insertion is happening not on normal case)
- **Single Right Rotation (SRR)**: Applied when the left subtree is too high. (insertion into left left child)
	![[Pasted image 20241007193537.png]]
	- Note that now the left subtree can take on a child and still be fine
- **Single Left Rotation (SLR)**: Applied when the right subtree is too high. (insertion into right child)
	![[Pasted image 20241007202519.png]]
- **Double Left Rotation (DLR)**: Combines SLR and SRR. - occurs on insertion into right subtree of left child (needs both right and left rotation to maintain AVL)
	![[Pasted image 20241007202611.png]]
- **Double Right Rotation (DRR)**: Combines SRR and SLR. occurs on insertion into left subtree of right child 
	![[Pasted image 20241007202631.png]]
- **Rebalance Cases**: 
	- Case 1: Left subtree of the left child. 
	- Case 2: Right subtree of the left child. - Case 3: Left subtree of the right child. - Case 4: Right subtree of the right child.
Just remember:
- Left imbalance -> Right rotation
- Right imbalance -> Left rotation
- Left Tree Right Child imbalance -> left rotation, right rotation
- Right tree left child imbalance -> right rotation, left rotation
## Insertion in AVL Trees - 
**Process**: - Insert like a standard BST: O(log N). 
- Check nodes from the insertion point to the root for AVL property violations. - Rebalance if needed using rotations. 
- **Time Complexity**: O(log N) due to tree height maintenance.
	 ![[Pasted image 20241007203104.png]]
## Deletion from AVL Trees 
- **Process**: - Delete like a standard BST (deepest) node in a tree deleted is a leaf or a node with one child (can happen anywhere)
- trace path from the new least towards the root(we do this with BST deletion too) 
	- for each node x encounter check if height of left(x) and right(x) differ by 1
		- if **YES**, process to parent(x)
		- if no, perform an appropriate rotation at x
		- Continue to trace until the root is reached 
### Deletion Examples 
![[Pasted image 20241007203926.png]]
- Delete 5 have a right right child imbalance -> rotate left by 1 
![[Pasted image 20241007204007.png]]
- 20 is imbalanced again in a right right imbalance so the tree needs to be rotated left by one to balance
![[Pasted image 20241007204056.png]]![[Pasted image 20241007204928.png]]
- Left right rotation
![[Pasted image 20241007210133.png]]![[Pasted image 20241007210141.png]]
- **Rotation child of problem node first... THEN rotate root of problem node other direction and that addresses the conflicting direction switches**