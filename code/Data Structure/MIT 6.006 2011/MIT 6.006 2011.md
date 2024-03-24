Efficient procedures for solving large-scale problems
Scalability
Classic data structures & classical algorithms
Real implementations in Python

## Content
8 modules
Algorithmic thinking: Peak finding
Sorting & trees: Event simulation
Hashing: Genome comparison
Numerics: RSA encryption
Graphs: Rubik's cube
Shortest paths: Caltech $\rightarrow$ MIT
Dynamic programming: Image compression
Advanced topics

## Peak finding
One-dimensioned version
![[Pasted image 20240324152252.png]]
Position 2 is a peak if and only if $b \ge a$ and $b \ge c$.
Position 9 is a peak if $i \ge h$.
Problem: Find a peak if it exists.

Straightforward Algorithm: $\mathcal{O}(n)$

算法的核心：任意一个array一定存在至少一个peak
if $a[n/2 - 1] \gt a[n/2]$, then $1, 2, \cdots, n/2-1$ for a peak
else if $a[n/2] < a[n/2 + 1]$, then $n/2+1, \cdots, n$ for a peak
else $n/2$ position is a peak
complexity: $\mathcal{O}(\log(n))$


