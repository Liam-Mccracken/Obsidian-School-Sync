## 1. **Problem Overview**  
A phone company wants to create a caller ID system:  
- Input: A phone number  
- Output: Caller’s name  
- Constraint: Phone numbers range from 0 to \( r = 10^8 - 1 \)  
- Challenge: Implementing an efficient solution with minimal wasted space
## 2. **Suboptimal Solution**  
- Using an array indexed by the phone number (O(1) time but requires huge space)
## 3. **Symbol Table Problem**
- Operations:
  - `INSERT`
  - `DELETE`
  - `SEARCH`
## 4. **Direct Access Table**
- Setup an array `T` for distinct keys where:
  - Time complexity for operations: \( O(1) \)
  - Problem: Huge range of possible keys (e.g., 64-bit numbers)
## 5. **Hash Functions**  
- **Hashing**: Use a hash function `h(k)` to map a key \( k \) to a slot in a smaller array.  
- **Collisions**: Occur when two keys hash to the same slot.
- The hash function **reduces the search space** by mapping keys from a potentially huge domain (like all possible phone numbers or strings) into a much smaller set of hash table indices.
- **Input**: You have a large set of possible keys (like phone numbers, strings, etc.).
- **Hash Function**: The hash function h(k)) takes a key k and computes a value, usually an integer, which serves as an index in a smaller table.
    - Example: h(k)=k mod  10 h(k) = k \mod 10h(k)=kmod10, where k is a number, and the function returns the remainder of k when divided by 10, mapping the key into a range from 0 to 9.
- **Output**: The key is then stored in the hash table at the position corresponding to the hash value (output of the hash function).
![[Pasted image 20240922184528.png]]
## 6. **Collision Resolution**
- **Chaining**: Resolve collisions by setting up an array of lists (chained items sharing the same slot). Items are chained together using **linked lists**
![[Pasted image 20240922185248.png]]

### Example
Given keys: {9789,5879,5344,2699,5973,4123,3171}
Hash function: \( h(x) = x \mod 10 \)
![[Pasted image 20240922185423.png]]
- values are chained that have the same mod value allowing for efficient fast sorting
- you would enter the key value and it would then map it to whatever index returns from the formula and then you'd search through for your value
## 7. **Dictionary Operations with Chaining**
- **Search**: `CHAINED-HASH-SEARCH(T, k)` searches for an element in the list.
- **Insert**: `CHAINED-HASH-INSERT(T, x)` inserts a new item at the head of the list.
- **Delete**: `CHAINED-HASH-DELETE(T, x)` deletes an item from the list.
---
## **Analysis of Hashing**  
- we assume that each key is equally likely to be hashed into any slot of table T independent of where other keys are hashed
- given hash table **T** with **m** slots holding **n** elements the **load factor** is defined as alpha = n/m
- time to compute is h(k) theta(1) **Search time** Theta( 1 + alpha)
- search takes constant time, insertion takes O(1) worst-case time, deletion takes O(1) worst-case time
---
## **Open Addressing
- alternative method to chaining for when a key is mapped to an occupied table location unlike chaining where multiple elements are stored in linked lists at each spot, open addressing keeps all elements directly within the has table and **systematically probes** until empty slot is found
![[Pasted image 20240922192258.png]]
## Linear Probing
- if collisions occur at index *i* the algorithm checks subsequent slots in the table until it finds a spot the probe sequence is 
- **h(k,i)=(h(k)+i) mod m** (where m is the slots, i is the probe number, and h(k) is original function)
- this uses less memory than chaining as we don't to store links but slower than chaining as we might have to walk along the table for a long time, note only one value can occupy a slot
#### Sudo Code
![[Pasted image 20240922193346.png]]
## **Open Addressing Example:**
Given keys: {9789,5879,5344,2699,5973,4123,3171}  

Hash function: \( h(x) = x \mod 10 \) 
![[Pasted image 20240922193156.png]]
Values are all separately stored in the hash table
## Example 2 
![[Pasted image 20240922195027.png]]
- i is initial 0 and increases by 1 until a free value is found, come the next collision i holds the previous value it had an keeps incrementing by +1 until probes are filles ^ explanation in above picture isn't correct
___
## Double Hashing
uses two hash functions 
![[Pasted image 20240925091835.png]]
## How it works
- First hash function determines the initial probe position, while the **second hash** function determines the **step size** for subsequent probes if a collision occurs 

![[Pasted image 20240925091935.png]]
![[Pasted image 20240925093515.png]]
## Key Points
- second hash function is used to see the insertion position when a conflict occurs, **i** increments by **1** for every collision / additional probe needed
- In linear probing step size is always one leading to predictable sequences, whereas here double hashing helps determine the step size so that keys are more uniformly distributed
![[Pasted image 20240925094248.png]]
## Division Method
![[Pasted image 20240925094317.png]]
## Multiplication Method
![[Pasted image 20240925094351.png]]
- A common choice for A is taking the conjugate of the golden ratio A= $(\sqrt{5} -1)/2$
## Advantages
- works well for many types of keys
- not sensitive to patterns in the key values
- can be faster than division-based methods on some hardware

![[Pasted image 20240925094941.png]]
1. Key assumptions:
    - 7-bit binary keys are used, ranging from 0 to 127 (0 ≤ k < 128)
    - Hash table size m = 8 = 2³, so p = 3 (where 2^p = m)
    - A = .1011001 in binary, which equals 89/128 in decimal
2. The key k: k = 1101011 in binary, which is 107 in decimal
3. Multiplication process: The image shows the binary multiplication of A and k:
    
    ## .1011001 (A) 1101011 (k)
    1001010.0110011 (kA)
4. Extracting the hash value:
    - In the multiplication method, we're interested in the fractional part of kA
    - The fractional part is .0110011
    - The hash value h(k) is determined by the p most significant bits of the fractional part
    - Since p = 3, we take the 3 bits after the binary point: 011
5. Result: h(k) = 011 in binary, which equals 3 in decimal

This method effectively maps the 7-bit key to a 3-bit hash value, fitting into the hash table of size 8.
The multiplication method is designed to distribute keys uniformly across the hash table. By using a carefully chosen value for A (like 89/128 in this case) and focusing on the middle bits of the product, it aims to create a good distribution even when there are patterns in the input keys.