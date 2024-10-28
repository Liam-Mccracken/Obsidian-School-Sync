## Sorting Algorithms Overview
- **Insertion Sort**: Worst-case time: Θ(n²)
- **Merge Sort**: Worst-case time: Θ(n log n), with additional memory Θ(n)
- **Selection Sort**: Optimizing selection via data structures can reduce time complexity to O(n log n).

---

## Binary Heaps
- **Binary Heap Properties**:
  - A nearly complete binary tree where **all levels except the last are filled.**
  - Max-Heap Property: **Key at the root is greater or equal to its children.** (there is no strict ordering between siblings, this is the key property)
  - Subtrees are also binary heaps.

- **Attributes of a Heap**:
  - `length[A]`: Total elements in the array.
  - `heap-size[A]`: Number of elements in the heap.
![[Pasted image 20241028101728.png]]
### Parent-Child Relationship (where i is key)
- A binary heap can be stored in an array where the root node is at index 1, each child position is determined by the relationship below. 
- A[Parent(i)] >= A[i]
- **Parent**: `⎣i/2⎦`  
- **Left Child**: `2i`  
- **Right Child**: `2i + 1`
- describes how the elements are seen within the array 

---

## Heapify Operation
- **Purpose**: Ensures the Max-Heap property by moving elements down if the root is smaller than its children. (used to fix violations)
- **Running Time**: 
  - Recursive calls on subtrees of size 2n/3.
  - T(n) <= T(2n/3) + O(1) -> T(n) = O(logn)
  - Worst-case time: O(log n).
```
HEAPIFY(A,i)
1. Left & Right subtrees of i are heaps (satisfies root property)
2. Makes subtree rooted at i a heap
3. l <- leaf(i) -> l = 2i
4. r <- right(i) -> r=2i+1
5. if l<= n and A[l] > A[i]
	1. then largest <- l
	2. else largest <- i
6. if r<=n and A[r] > A[lagest]
	1. then largest <- r
if largest != i 
	then exchange A[i] <-> A[largest]
		HEAPIFY(A, largest)
```
## Example of heapify :
![[Pasted image 20241028104641.png]]
- we recursively work our way down the tree ensuring every nodes follows heapify and if it doesnt we switch the nodes so they do
 
---

## Building a Heap
- Converts an array into a valid heap.
- **Leaves**: Elements from A[⎣n/2⎦ + 1 ... n] are already individual heaps.
- **Time Complexity**:
  - Initial analysis: O(n log n).
  - Optimized analysis: O(n) using properties of smaller heaps.
![[Pasted image 20241028105147.png]]
- We work our way down the list and recursively call heapify to resort the tree elements to not violate the heap properties
- Running time:
	- n calls to heapify = n O(logn) = O(nlgn) (only if operations are independent of each other one for each element)
	- Time to build heapify is O(n) - this is because build head optimizes this by starting from the bottom instead of top and only performing action on necessary parts of the tree
		- Even though heapify calls can take O(logn) time the majority of the work is done on smaller subtrees leading to an overall linear time complexity 
---

## Summary of Key Takeaways
- **Heapify** is key to maintaining the heap structure.
- **Building a Heap** can be achieved efficiently in O(n) time.
- **RUNNING TIME IS O(logn)**
- Binary heaps support logarithmic time operations, useful for priority queues and sorting (e.g., Heapsort).
- Main point of heapify is root node must be greater than or equal to that of the children so we recursively call heapify to reorder elements as we work down so this property isn't violated.

---
## Lecture 18 - Building a heap analysis & Priority queues
![[Pasted image 20241028110826.png]]
![[Pasted image 20241028111632.png]]
- we know build heap takes O(n) build time then heapify on each element i.e the sorting takes **O(nlgn)**  runtime

## Heap Sort
- Recall heaps are stored as arrays not as pointer based binary trees, heap structure maps directly into array where left child = 2i right child is 2i+1.
- 1. Building the heaps
	- Heap sort begins by building a max-head for ascending order from the unsorted array. This step ensures that the largest element is at the root(first index of the array) 
- 2. Extracting the maximum element 
	- once the max-heap is built, the largest element(root) is swapped with the last element of the array
	- the size of the heap is reduced by one, and the new root( the swapped element) is heapified to restore the max-heap property
3. Placing elements in sorted order
	- This process (swapping root with the last element of heapifying) continues until the heap size becomes 1 
	- At each step the largest remaining element moves to its correct position in the sorted array 
Example: 
Unsorted array `[4,10,3,5,1]` 
Step 1: Build the max heap
       10
       /  \
      5    3
     / \
    4   1
![[Pasted image 20241028112751.png]]
- This process is repeated until the entire array is sorted 
- Final sorted array: [1,3,5,10]

Conclusion:
- Heap sort reorganizes the orignal array in place using heap operations
- after each extraction, the largest element is placed at the end of the array, and the heap is restored for the remaining elements
- once all elements are extracted the array becomes fully sorted
-![[Pasted image 20241028112934.png]]


## What is a Priority Queue?

A **Priority Queue** is an **abstract data type (ADT)** that operates similarly to a regular queue but with an added concept of **priority**. Each element in a priority queue is associated with a **priority value**, and elements are **removed based on their priority** rather than their insertion order.

---

### **How a Priority Queue Works**
- In a **Max-Priority Queue**, the element with the **highest priority** is dequeued first.
- In a **Min-Priority Queue**, the element with the **lowest priority** is dequeued first.
- A **binary heap** (Max-Heap or Min-Heap) is often used to efficiently implement a priority queue.

---

### **Operations on a Priority Queue**
1. **Insert(S, x)**:  
   - Inserts an element `x` into the set `S`.
   - **Time complexity**: O(log n) (for heap-based implementation).

2. **Maximum(S)** / **Minimum(S)**:  
   - Returns the element with the **highest** (or lowest) priority without removing it.
   - **Time complexity**: O(1).

3. **Extract-Max(S)** / **Extract-Min(S)**:  
   - Removes and returns the element with the **highest** (or lowest) priority.
   - **Time complexity**: O(log n) (Heapify is required to restore the heap property).

---
### Extract Max
- Removal of max takes constant time on top of the normal heapify operation so O(lgn) as that is the heapify run time
- ![[Pasted image 20241028113555.png]]

### Insertion 
- Insertion of a new element
	- we enlarge the priority queue and propage the new element from last place "up" the PQ
	- tree is of heigh lg n, running time: O(lgn)
	Ex: 
	![[Pasted image 20241028113709.png]]
	- Shows the process of inserting an element into a Max-Priority queue, implemented as a max-heap
	- 15 is inserted at next available position being the child of 7, we then work our way up performing heapify operations meaning 15 switches with 7 then with 14 as a result of the heapify operations then is inserted where 14 was and ensures that the heap conditions are maintained
	- This takes O(logn) time because the new element might need to be bubbled up through the height of the tree, which is logn, 
	
### **Summary**
This example demonstrates how a **Max-Priority Queue** maintains the **Max-Heap property** when a new element is inserted. The key steps are:

1. **Insert** the element at the next available position.
2. **Bubble it up** by swapping with parents until the Max-Heap property is restored.

This operation ensures that **future extractions** (like `Extract-Max`) still return the largest element efficiently from the root.