## Towers of Hanoi 
![[Pasted image 20241130090712.png]]
- We end up with a geometric series giving us a runtime of O(2^n) the run time is **exponential** rather than **polynomial** n^k, this is bad it means it would take years to actual get a solution the higher n disks we we're given
- This leads us to wonder, are such long running times linked to the size of the solution to an algorithm? The answer is **no** 

![[Pasted image 20241130090930.png]]

## Decision Problem Example
![[Pasted image 20241130091034.png]]
- **Does any MxM arrangement exist that fulfills the matching criterion?** 
	- Brute force algo would take n! time to verify where it exists assuming n = 25 it would take 490 billion years
- Recall
![[Pasted image 20241130091152.png]]![[Pasted image 20241130091215.png]]
- **Good** reasonable algorithms
	- bounded by a polynomial functions n^k 
	- **Tractable problems
- **Bad** unreasonable algorithms
	- algorithms whose running time is above n^k
	- **Intractable problems
	![[Pasted image 20241130091325.png]]

NP (non-deterministic polynomial time):
![[Pasted image 20241130091416.png]]
![[Pasted image 20241130091446.png]]
![[Pasted image 20241130091527.png]]
![[Pasted image 20241130091532.png]]
![[Pasted image 20241130091545.png]]




____

## GPT Summary
- this lecture explores how hard it is to solve problems on computers. It asks big questions like:
	- can we solve all problems efficiently 
	- if we cant can we at least verify solutions directly?

1. P and NP
	- **P (polynomial time):** problems that can be solved efficiently (in polynomial time)
		- ex: finding shortest path b/w two nodes on a map
	- **NP(non-deterministic polynomial time):** Problems where solutions can be verified efficiently, but we don't know if they can always be solved efficiently
		- Ex: Sudoku puzzles - checking if a solution is correct is fast, but finding that solution can take a while


2. **NP completeness Problems**
	- These are the **hardest problems in NP** if u can solve one NP-complete problem efficiently, you can solve all problems in NP efficiently
		- Example TSP (travelling sales person problem)

## The big question: P=NP?
- does solving a problem efficiently mean we can verify the solution efficiently?
	- If yes P = NP 
	- If no P != NP
		- No one knows this answer
### **Why is this important?**

- Knowing whether P=NP would change how we approach solving hard problems.
- If P=NP, many currently hard problems (like cracking passwords or optimizing supply chains) would suddenly become solvable efficiently.

---
### **How do we classify problems?**

- **Easy Problems (Tractable):** Solvable in polynomial time (n,n^2, n^3,n^4). These belong to P.
- **Hard Problems (Intractable):** Require exponential time (2n,n!,2^n). These are likely outside P.

---

### **Reduction and Why It’s Important**

- **Reduction** means showing that one problem can be transformed into another.
    - If you can reduce a known hard problem (like TSP) to a new problem, the new problem is also hard.
- Reductions help us prove that problems are NP-Complete.

---

### **A Simple Analogy**

Think of NP problems like puzzles:

1. **P Problems:** Puzzles you can solve and verify easily.
2. **NP Problems:** Puzzles you can verify easily but might take forever to solve.
3. **NP-Complete Problems:** The hardest puzzles in the NP group – if you solve one, you solve them all.

---

### **Real-World Impact**
- If P != NP: we'll focus on approximation or partial solutions for hard problems
- If P = NP: many breakthroughs could happen, like better AI, cryptography being broken and more

---