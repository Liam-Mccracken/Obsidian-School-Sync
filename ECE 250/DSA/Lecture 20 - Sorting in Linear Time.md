
---
## How Fast Can We Sort?

- **Comparison sorts** rely only on comparisons between elements.
- **Best possible runtime for comparison sorts:** O(n log n) (proved by decision tree model).
- Question: **Can we do better?**  
  - **Answer:** Not with comparison sorts. best case we've seen so far is O(nlogn)

---

## Decision Tree Model

-  num : num implies that the numbers of being compared
- Models the behavior of any comparison-based algorithm.
- **Tree nodes**: represent comparisons between two elements.
- **Paths**: represent a sequence of comparisons leading to a specific permutation.
- **Height of tree** = worst-case runtime.

### **Lower Bound Proof:**
- A tree sorting `n` elements must have at least `n!` leaves.
- Using Stirling's approximation, the minimum height is **Ω(n log n)** we can't get a better average case bound than this
![[Pasted image 20241029095528.png]]

Height: h 
- num of leaves in a complete BT: 2^H
- Num of leaves (permutation) in a DT (decision tree) : n!
	- 2^h >= n! -> h >= lg(n!) (2)
	- Stirling Theory: n! is approx (n/e)^n (1)
- h >= lg(n/e)^n = nlgn - nlge


---
## Sorting in Linear Time: Counting Sort

- **Non-comparison-based algorithm**.
- **Input:** Array `A[1 . . n]` with elements in range {1, 2, ..., k}.
- **Output:** Sorted array `B[1 . . n]`.
- **Auxiliary Storage:** Array `C[1 . . k]`.
![[Pasted image 20241029100249.png]]
### **Algorithm:**

1. **Initialize** the count array `C`.
2. **Count occurrences** of each element in `A`.
	1. Count the amount of key equal to the array position ![[Pasted image 20241029100703.png]]
	- There is 1 occurence of 1 2 of 4 etc etc
	
3. **Accumulate counts**: Add current cell to its right neighbor cell (accumulatively)![[Pasted image 20241110152438.png]]![[Pasted image 20241110152641.png]]
1. **Build the output array** - Shift array right by 1 cell 
![[Pasted image 20241110153404.png]]
---

## Example: Counting Sort

Given input `A = [4, 1, 3, 4, 3]`, the steps are:

1. **Initialize:** `C = [0, 0, 0, 0]`
2. **Counting Pass:** `C = [1, 0, 2, 2]`  
3. **Accumulate Counts:** `C = [1, 1, 3, 5]`  
4. **Build Output:** `B = [1, 3, 3, 4, 4]`

---

## Runtime Analysis

- Counting Sort has **Θ(n + k)** runtime.
  - If `k = O(n)`, the overall runtime is **Θ(n)**.
- This doesn't violate the **Ω(n log n)** bound for sorting since:
  - **Counting Sort** is **not a comparison sort**.

---

## Counting Sort is a Stable Sorting Algorithm
- It preserves the input order among equal elements 
	- meaning values with the same key appear in exactly the same order in sorted array than original
- **Stable sort**: Maintains the order of equal elements.
- Counting Sort is stable.
- **Question:** Which other algorithms are stable?

---

## Key Takeaways

- **Comparison sorts** are limited by Ω(n log n).
- **Counting Sort** achieves Θ(n) time by avoiding comparisons.
- Stability is a useful property in sorting.
- 

---
