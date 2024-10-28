## Characteristics of QuickSort
- **In-place sorting:** No additional arrays required, unlike merge sort. (merge makes another array to merge)
- **Average time complexity:** O(n log n) with small constant factors.
- **Worst-case time complexity:** O(n²), though this is rare.
- **Divide-and-conquer approach:**
  1. **Divide:** Partition the array around a pivot element.
  2. **Conquer:** Recursively sort the two partitions.
  3. **Combine:** Trivial since sorting happens in place.
	  1. Partitioning always selects an element as a pivot element around which to partition the subarray 

---
## Partitioning Algorithm

The partitioning function divides the array into two parts relative to a pivot, ensuring elements on the left are smaller than the pivot and those on the right are larger.
![[Pasted image 20241028160222.png]]

## Quick Sort Algorithm
![[Pasted image 20241028160334.png]] 
### How Quicksort works
- Divide and conquer algorithm 
	- Picks a pivot element from the array
	- partitions the array around the pivot so all smaller elements are on one side and all larger elements on other
	- recursively applies the same logic to the two partitions
- Given an unsorted array `[10,7,8,9,1,5]`
- Step 1: Choose a pivot
	- pick the last element as the pivot so 5
- Step 2: Partition the array
	- **Goal**: reorganize the array such that
		- elements less than or equal to pivot go left
		- elements greater than pivot go to right
- Compare `10` with pivot `5` – No swap, move to the next element.
- Compare `7` with `5` – No swap.
- Compare `8` with `5` – No swap.
- Compare `9` with `5` – No swap.
- Compare `1` with `5` – **Swap** `10` and `1`.
	- The array becomes `[1,7,8,9,10,5]`
	- Now swap the pivot 5 with the element at the "split point"
- Now we sort partitions left is 1 as its sorts , right array we repeat the same process until it is ordered we **recursively** apply the same steps to the two partitions and stop when partitions contain 0 or 1 element as theyre sorted
![[Pasted image 20241028161241.png]]

## Analysis of Quicksort
- running time depends on the distribution of the splits
- ![[Pasted image 20241028161313.png]]
- Worst case occurs when the partition only has one element 
![[Pasted image 20241028161357.png]]
