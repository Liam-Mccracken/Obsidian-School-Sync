#### **Lecture 23: Dynamic Programming – Part A**

**1. Algorithm Design Techniques**

- Techniques include iterative algorithms, algorithms using ADTs, and divide-and-conquer strategies.

**2. Divide and Conquer**
- Key steps: divide, conquer, and combine.
- Example: MergeSort.
**3. Fibonacci Numbers**
- Naive recursive solution is inefficient due to overlapping subproblems.
- Dynamic programming approach optimizes by storing results, reducing runtime from exponential to linear.

**4. History of Dynamic Programming**

- Developed in the 1950s by Richard Bellman to optimize multi-stage decision processes.
- "Programming" refers to planning, not coding.

**5. Optimization Problems**

- Focused on finding optimal solutions by solving subproblems and combining results.

**6. Multiplying Matrices (Overview)**

- Challenges of associativity in matrix multiplication and importance of optimal parenthesization.
- Example: Comparing costs of different parenthesization methods.

**Steps to Develop a DP Algorithm**

1. Characterize the structure of an optimal solution.
2. Write a recurrence relation.
3. Compute the value iteratively (bottom-up).
4. Construct the solution using stored computations.

---

#### **Lecture 24: Dynamic Programming – Part B**

**1. Multiplying Matrices (Continued)**

- Recursive and bottom-up DP approaches reduce computation time from exponential to polynomial.
- Algorithm: `Matrix-Chain-Order` to compute optimal splits and costs.

**2. Longest Common Subsequence (LCS)**

- Problem: Find the maximum-length common subsequence between two strings.
- Applications: DNA sequence analysis, spell checkers.
- Key Steps:
    - **Step 1**: Characterize optimal substructure.
    - **Step 2**: Define recurrence relation.
    - **Step 3**: Compute optimal value using bottom-up DP.
    - **Step 4**: Reconstruct the solution.

**LCS Algorithm**

- Construct a table to store intermediate results.
- Backtrack to print the LCS.

---

#### **Lecture 25: Dynamic Programming – Part C**

**1. Steps to Develop a DP Algorithm**  
Revisited the 4-step approach for DP algorithms.

**2. Checkerboard Problem**

- Goal: Move a checker from the bottom to the top of a checkerboard while maximizing rewards (p(x, y)).
- Rules:
    - Checker moves up, diagonally left, or diagonally right.
    - Rewards (p(x, y)) can be negative.
- Algorithm:
    - Solve the problem using DP to find optimal moves and maximum rewards.
    - Evaluate runtime efficiency of the solution.

---

### Markdown Usage for Obsidian

- Copy each section above into your Obsidian notes.
- Use headers (`#`) for titles and bullet points for key details.
- Adjust formatting as needed for your personal note-taking style.