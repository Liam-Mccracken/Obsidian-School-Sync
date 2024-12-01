Dynamic Programming – Part A
## Algorithm Design Techniques

1. **Iterative (brute force) Algorithms**: E.g., insertion sort, selection sort.
2. **Data Structure-based Algorithms**: E.g., heap sort (uses bst) 
3. **Divide and Conquer**: E.g., merge sort, quicksort, binary search

## Divide and Conquer

- **Divide**: Split problem into sub-problems. (if input size is too large to deal with in straight forward manner)
- **Conquer**: Solve sub-problems recursively.
- **Combine**: Merge solutions of sub-problems.
Ex - Merge Sort: 
```c++
Merge-Sort(A,p,r)
	if p < r then
	q = (p+r)/2
	Merge-Sort(A,p,q)
	Merge-Sort(A,q+1,r)
	Merge(A,p,q,r)
```
![[Pasted image 20241110173810.png]]

## Fibonacci Numbers

- **Recursive Definition**: F(n)=F(n−1)+F(n−2)F(n) = F(n-1) + F(n-2)F(n)=F(n−1)+F(n−2)
	- From this we see recursive procedures are slow!
- **Recursive Algorithm**: Exponential time complexity due to overlapping sub-problems.
	- Noted here: ![[Pasted image 20241110173919.png]]
	- How many summations in fibonacci ? S(n)
		![[Pasted image 20241110174002.png]]
- **Dynamic Programming Solution**:We can calculate F(n) in linear time by remembering solutions to the solved sub-problems i.e computing the solution in a **Bottom-up** fashion
```c++
	Fibonnaci(n)
		F[0] = 0
		F[1] = 1
		for i=2 to n do
		F[i] = F[i-1] + F[i-2]
		return F[n]
```
![[Pasted image 20241110174340.png]]

## Dynamic Programming (DP)

- **History**: Invented by Richard Bellman in the 1950s for multi-stage decision processes.
- **Optimization Problems**: Choose a solution that minimizes or maximizes a value. Store solution to each subproblem in case it should reappear
	- **Solution Exhibits a Structure**
	- It consists of a string of choices that were made - what choices have to be made to arrive at an optimal solution?
	- An algorithm should compute the **optimal value** plus if needed, **an optimal solution**
## Multiply Matirices
- Two matrices, A - nxm matrix and B - mxk matrix, can be multiplied to get C with dimensions nxk using nmk scalar multiplications![[Pasted image 20241110174651.png]]
- Parenthesization matters to this question so it cannot be ignored 
## How to develop a DP (dynamic programming) Algorithm

- **Step 1:** Characterize the structure of an optimal solution
- **Step 2:** Write a recurrence for the value of an optimal solution 
	- Remember it mentions storing solutions to sub problems in case they were to reappear 
- **Step 3:** Compute the value of an optimal solution typically in a bottom-up fashion.
- **Step 4:** Construct an optimal solution from computed information

**Step 1:** Characterize the structure of an optimal solution 
![[Pasted image 20241110175320.png]]
**Step 2: Write a recurrence for the value of an optimal solution**
![[Pasted image 20241128185049.png]]
- If we were to use a simple recursive approach we would get **exponential time complexity due to the redundant calculations of overlapping terms**
![[Pasted image 20241128185332.png]]
**Step 3:** Compute the value of an optimal solution!
![[Pasted image 20241128185033.png]]
**Step 4:** Construct an optimal solution from computed info
![[Pasted image 20241128185501.png]]
- Now with this optimal solution we can see that the running time is linear and no additional space is required.
![[Pasted image 20241128185526.png]]
---
Another DP Problem
## Longest Common Subsequence (LCS)
![[Pasted image 20241128185631.png]]
![[Pasted image 20241128185637.png]]
Recall Strategy for solving: 
- **Approach**:
    1. Define optimal substructure.
    2. Use recurrence relation for LCS length.
    3. Fill table to compute LCS length.
    4. Reconstruct LCS using backtracking.
**Step 1: Optimal Substructure:**  
![[Pasted image 20241128190021.png]]
**Step 2:** Use recurrence relation for LCS length
![[Pasted image 20241128190126.png]]
**Step 3 : Computer The value Optimal Solution: (using what u just decided)**
![[Pasted image 20241128190328.png]]
**Step 4:** Construct a LCS i.e Construct Optimal Solution Based on findings
![[Pasted image 20241128190426.png]]


---

# Lecture 25: Dynamic Programming – Part C

## Developing a DP Algorithm

1. **Characterize Optimal Solution**.
2. **Define Recurrence Relation**.
3. **Compute Solution (Bottom-Up)**.
4. **Construct Solution**.

## Checkerboard (CB) Problem
- Gonna have to come back to DP problems cause erm
![[Pasted image 20241128191055.png]]
![[Pasted image 20241128191205.png]]![[Pasted image 20241128191129.png]]
![[Pasted image 20241128191153.png]]