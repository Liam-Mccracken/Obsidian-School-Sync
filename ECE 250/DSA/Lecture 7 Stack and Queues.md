# Lecture 7: Stack and Queue

## Key Concepts
- **Data Type**: Set of allowed values for a variable.
- **Data Structure**: Systematic way of organizing and accessing data.
- **Principle of Abstraction**: Focus on "what" not "how" when solving a problem.
- **Abstract Data Type (ADT)**: Set of elements with well-defined operations.

---
## Abstract Data Types (ADTs)
- Defines dataset without explaining the actual implementation
- ADTs break work into independent pieces without compromising correctness.
- Serve as specifications for algorithmic problem solutions.
- Encapsulate data structures and algorithms.
- Provide a higher-level abstraction for programming.

---
## Dictionary ADT
- A **dynamic set** with operations like:
  - `Search(S, k)`: Returns a pointer to the element where `x.key = k`. ex. phone, age etc
  - `Insert(S, x)`: Adds an element `x` to `S`.
  - `Delete(S, x)`: Removes an element `x` from `S`.
  - Additional operations:
    - `Minimum(S)`: Returns the smallest element in `S`.
    - `Maximum(S)`: Returns the largest element in `S`.
    - `Successor(S, x)`: Returns the next larger element in `S`.
    - `Predecessor(S, x)`: Returns the next smaller element in `S`.

---

## Dictionary Implementations
- Data structures that can be used to implement a dictionary include:
  - Arrays
  - Linked Lists
  - Queues
  - Stacks
  - Binary Trees
  - AVL Trees
  - B-Trees
  - Hash Tables
  - Heaps

---

## Storage Types for ADTs
- **Contiguous Storage**: Arrays, where `n` objects are stored in a single block of memory.
	- if more memory is required copying all info into new array is needed
- **Node-Based Storage**: Linked Lists, where each item stores data and a reference to the next item. 
	- stores object itself and reference to next item in c++ reference is address of the next node

---

## Linked List ADT
- **Singly Linked List**: Nodes store data and a pointer to the next node.
- Operations with time complexity:
  - `isEmpty()`: `O(1)`
  - `first()`, `last()`, `insertFirst()`, `insertLast()`: `O(1)`
  - `after(p)`, `insertAfter()`: `O(1)`
  - `before(p)`, `insertBefore()`: `O(n)`
  - `replace(p, e)`: `O(1)`
  - `remove(d)`: `O(n)`
![[Pasted image 20240922164841.png]]
### Doubly Linked List
- Each node has a next and previous pointer, allowing operations to be performed in constant time. both linked and doubly linked list have time complexity of O(n)
![[Pasted image 20240922165104.png]]
- The trailer represents the end of the linked list

---
## Stack ADT
- **Stack**: A container following the Last-In-First-Out (LIFO) principle.
	- objects can be inserted at any time, but only the last (most recently inserted) object can be removed
  - Operations:
    - `Push(S, x)`: Insert element `x` onto the stack.
    - `Pop(S)`: Remove the top element from the stack.

### Array Implementation of a Stack
- Use an array of size `N` to store stack elements.
- Keep track of the top element with an index `t` (initialized to `-1`).
- Array implementation has a runtime of O(1) as u are only ever adding one element
![[Pasted image 20240922165723.png]]
#### Pseudo Code for Stack Operations:
![[Pasted image 20240922165737.png]]
___
#### Queue ADT
- First in first out principle not last in last out
- elements can be inserted at any time but only element in the longest can be removed
- elements are inserted at the rear (enqueued) and removed from the front (dequeued)
![[Pasted image 20240922170058.png]]
![[Pasted image 20240922170142.png]]
![[Pasted image 20240922170156.png]]
- Notes: first index will always head of return , dequeue rips off the front element
- Also unlike stack queue there is a front and a back element (just remember front never moves unless item removed)
- This is treated as a circular queue which means the when we reach the end of the array instead of stopping or needing to shift elements we can wrap around to the beginning of the array
- Consider a circular queue with an array of size 5 (so N=5N = 5N=5).
![[Pasted image 20240922171112.png]]
ensures the enqueued items wrap around to the front of the array once added

___
# Example
![[Pasted image 20240922172235.png]]