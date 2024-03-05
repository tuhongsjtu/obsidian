pure state: $\rho = | \psi \rangle \langle \psi |$
mixed state: $\rho_{mix} = \sum_i p_i | \psi_i \rangle \langle \psi_i |$

#### Properties of Pure State
1. 
$\rho^2 = | \psi \rangle \langle \psi | \psi \rangle \langle \psi | = \rho$
2. Trace of density matrix of pure state equals $1$.
$\mathrm{Tr}(\rho) = \sum_i \langle i | \rho | j \rangle = \sum_i \langle i | \psi \rangle \langle \psi | i \rangle = \sum_i \langle \psi | i \rangle \langle i  | \psi \rangle = 1$
3. From 1 and 2: The trace of any power of the density matrix is equal to 1
$\mathrm{Tr} (\rho^n) = 1$
4. Hermitian
$\rho^{\dagger} = \rho$
5. semi-positive
$\langle \phi | \rho | \phi \rangle = |\langle \phi | \psi \rangle|^2 \ge 0$

#### Properties of Mixed State
1. $\rho^2_{mix} \neq \rho_{mix}$
2. $\mathrm{Tr}(\rho_{mix}) = 1$
3. $\mathrm{Tr} (\rho_{mix}) < 1$
4. Hermitian and semi-positive

#### Composite Syste
For a composite system, the Hamiltonian is $H_{AB} = H_A \otimes H_B$, and the corresponding density matrix is 
$$
\rho_{AB} = \rho_A \otimes \rho_B
$$
which means that
$$
(| \psi \rangle \langle \psi |) \otimes (| \phi \rangle \langle \phi |)
= 
(| \psi \rangle \otimes | \phi \rangle) (\langle \psi | \otimes \langle \phi |)
$$
***
Condition of formula
$$
(AB) \otimes (CD)
= 
(A \otimes C) (B \otimes D)
$$
?
***

Another operation is so called partial trace, which is defined as:
$$
\begin{align}
\rho_{A} = \mathrm{Tr}_B(\rho_{AB}) \\
\rho_{B} = \mathrm{Tr}_A(\rho_{AB}) \\
\end{align}
$$
Partial trace and Kronecker product are inverse operator of each other.