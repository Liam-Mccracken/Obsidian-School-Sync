Keep in mind that radix sort is a non-comparative integer sorting algorithm
![[Pasted image 20241110160827.png]]
![[Pasted image 20241110160858.png]]
## Run time
Given n d-digits numbers in which each digit can take on up to k possible values, Radix Sort **correctly** sorts these numbers in O(d(n+k)) time if the stable sort is uses takes O(n+k) time\

Radix sort relies on **stable sorting** for each digit to ensure that the order of the elements with the same digit value is preserved across multiple passes which is essential for it to work successfully,
**note in the example above**, when elements have the same keys the order that they are sorted in the new array remains the same 53,633,233 -> 633,233

Radix Proof
Counting sort:
	![[Pasted image 20241110162159.png]]![[Pasted image 20241110162205.png]]
	![[Pasted image 20241110162227.png]]


Another time complexity breakdown: 

Runtime for Radix Sort: O(b/r * (n+2^r))
	- Treating numbers as binary values 2^r = k which is range of numbers binary would be 2^r
	- **b**: Base we're using
	- n: num of elements
	- r: number of bits or digitals in a single pass
		1.b/r : number of passes
			- radix sort processes digits one position at a time, but here we are grouping r bits (or digits at each pass)
			- by processing r bits at a time, we reduce the number of passes for b(d) to b/r
			- for example if b=8 and r =2 we need 4 passes
		2.(n+2^r): cost per pass
			- Each pass through the array requires sorting based on r bits. This is done using stable sort(often counting) with a range of values based on r bits
			-  If we process r bits at a time there are  2^r possible values for each group of r bits
		![[Pasted image 20241110162831.png]]
**Choosing r for optimal performance**
- if r is small 2^r is small, but the number of passes increases making the algo slower
- if r is large 2^r increases, which increases the sorting cost per pass
- an optimal r balance these two. In practice, values of r that result in 2^r close to n or less often yield good performance
![[Pasted image 20241110163411.png]]![[Pasted image 20241110172656.png]]
Textbook proof showing the same thing:
![[Pasted image 20241110173520.png]]