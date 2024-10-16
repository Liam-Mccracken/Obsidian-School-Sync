 - Monday tutorial will cover project details 
- review big o notation 

f(n) shows running time for algorithm 
finding n value such that cg(n) is always true 
writing basic notes here and will come back and expand 
everything is log base 2 because of binay numbers 2,4,8,16,32 bit etc...

![[Pasted image 20240908202327.png]]
![[Pasted image 20240908202409.png]]
![[Pasted image 20240908202423.png]]![[Pasted image 20240908202434.png]]


<font size = 8>Asymptotic Notations </font>

- Big O is the upper bound of a function
- Big Omega is the lower bound of a function
- Theta notation is a tight bound (average bound), 

Recalling running time hierarchy 

1<log(n) < sqrt(n) < n < nlog(n) < n^2 < n3 < .... n^n

<font size = 7> Big O Notation (O) </font> 
- Big O notation describes worst case scenario, its the upper bound running time complexity of an algorithm  
- ![[Pasted image 20240908204338.png]]

<font size = 7> Big Omega Notation (O) </font> 
- Describes the best case scenario where the function f(n) >= c g(n)
-![[Pasted image 20240908204639.png]]
- **The value that satisfies this function will always result in a line lower than the og function as its supposed to be the fastest possible run time**
-can be any number


<font size = 7> Big Theta Notation (O) </font> 
- Describes the average case scenario it represents the most realistic time complexity of an algorithm, usually used when best case and worst case is the same 
- there is also an infinite number of answers for this
![[Pasted image 20240908205149.png]]
