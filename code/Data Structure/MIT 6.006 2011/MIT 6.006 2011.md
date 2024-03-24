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
$$
\begin{aligned}
T(n) &= T(n/2) + \theta(1) \\
T(1) &= \theta(1) \quad ? \\
T(n) &= \theta(1) + \cdots + \theta(1) =\theta(\log_2 n)
\end{aligned}
$$

2D version
![[Pasted image 20240324162903.png]]
a is a 2D peak if and only if $a \ge b; a\ge d; a\ge c; a\ge e$

Greedy Ascent Algotithm
![[Pasted image 20240324163334.png]]
选择起始格点，朝着一个方向不断前进直到数字不再变大或者到达边界，之后换一个方向重复上述过程，直到四个方向都遍历完毕即可找到peak
complexity: $\mathcal{O}(nm)$

