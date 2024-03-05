### 1. QCP

To determine the critical point, the scaling form of Ising spin suspectibility at

$$  
\chi(h, T, \mathbf{0}, 0) = L^{\gamma / \nu} f((h - h_N) L^{1/\nu}),
$$
$$
\chi(h, T, \mathbf{q}, i\omega_n) = \frac{1}{L^2} \sum_{ij} \int_0^{\beta} d\tau e^{i \omega_n \tau - i \mathbf{q}\cdot\mathbf{r}_{ij}} \langle s^z_i(\tau) s^z_j(0) \rangle.
$$and the critical exponents are given by the 2D Ising universality class

The Fermion susceptibility is defined as
$$  
\chi_F(h, T, \mathbf{q}, i\omega_n) = \frac{1}{L^2} \sum_{ij \lambda \lambda'} \int_0^{\beta} d\tau e^{i \omega_n \tau - i \mathbf{q}\cdot\mathbf{r}_{ij}} \langle \sigma^z_{i \lambda}(\tau) \sigma^z_{j \lambda'}(0) \rangle.  
$$
It has a similar scaling behavior with Ising susceptibility.

![image-20231106204405438](file:///Users/hongtu/Library/Application%20Support/typora-user-images/image-20231106204405438.png?lastModify=1705228348)

![](file:///Users/hongtu/Library/Application%20Support/typora-user-images/image-20231106204132110.png?lastModify=1705228348)

​

Finite-temperature FM-to-PM transition at T=1. (a) Ising susceptibility; (b) Data collapse result. 

​

![image-20231106204641640](file:///Users/hongtu/Library/Application%20Support/typora-user-images/image-20231106204641640.png?lastModify=1705228348)

![image-20231106204141182](file:///Users/hongtu/Library/Application%20Support/typora-user-images/image-20231106204141182.png?lastModify=1705228348)

​

Finite-temperature FM-to-PM transition at T=1. (a) Fermion susceptibility; (b) Data collapse result. 

​

![image-20231106205320415](file:///Users/hongtu/Library/Application%20Support/typora-user-images/image-20231106205320415.png?lastModify=1705228348)

![image-20231106205328445](file:///Users/hongtu/Library/Application%20Support/typora-user-images/image-20231106205328445.png?lastModify=1705228348)

​

(a) Phase Diagram. The QCP is 5.31(5) and the critical exponent is about 0.82(2); (b) Fitting result. 

​`Attention! The result of phase diagram is still concerning due to the processing method.

Due to the coupling between fermions and Ising spins, they should give out the same critical point. But in our simulation, at finite size systems, the value of the critical point is not same. This phenomenon can be explained by the drift of the critical point. According to Ref[], the standard scaling form of a observable quantity is

$$  
O(\delta, L) = L^{-\kappa / \nu} f(\delta L^{	1/\nu}, \lambda L^{-\omega}).
$$

Consider two systems with size $L$ and $rL(r \gt 1)$，by using Taylor's expansion we can get the cross point is

$$  
\begin{align}
\delta^*(L) 
=& \frac{a_0}{a_1} \frac{1 - r^{-\kappa/\nu}}{r^{(1-\kappa)/\nu-1}} L^{-1/\nu} + \frac{b_1}{a_1} \frac{1 - r^{-(\kappa/\nu+\omega)}}{r^{(1-\kappa)/\nu-1}} L^{-(1/\nu+\omega)}
\end{align}  
$$

When the observable quantity is dimensionless at the cross point, e.g. $\kappa = 0$

$$  
\delta^*(L) = q^*_c(L) - q_c \propto L^{-(1/\nu+\omega)}  
$$

The observable quantity we used is

![image-20231107104857223](file:///Users/hongtu/Library/Application%20Support/typora-user-images/image-20231107104857223.png?lastModify=1705228348)

​

The drift of Ising critical point.

​

![image-20231107104823344](file:///Users/hongtu/Library/Application%20Support/typora-user-images/image-20231107104823344.png?lastModify=1705228348)

​

The drift of Fermion critical point.

​

Pay attention that the drift result of Ising is not perfect now.

---

The following content has not been confirmed by the supervisor.

The disadvantage of the method is that we always need a size

If we consider two systems with

### 2. Quantum Critical Scaling Analysis

In QCP part we have estimate that the IQCP is about

$$  
  
$$

  

In Ref, the power in

In triangle lattice system the finite-size effects is much more serious than square lattice system, so we run the code with fixed

![image-20231108173841980](file:///Users/hongtu/Library/Application%20Support/typora-user-images/image-20231108173856805.png?lastModify=1705228348)![image-20231108173909038](file:///Users/hongtu/Library/Application%20Support/typora-user-images/image-20231108173909038.png?lastModify=1705228348)

​

Data and fitting of chi^{-1} fixed h and diffrent T

​

To determine

$$  
  
$$

  

When

![image-20231106205132372](file:///Users/hongtu/Library/Application%20Support/typora-user-images/image-20231106205132372.png?lastModify=1705228348)

​

Data and fitting with fixed T and diffrent h

​

 Attention! The results are not very accurate now. The intercept in the curve fitting is about 

To

$$  
  
$$

  

$$  
  
$$

  

$$  
  
$$

  

$$  
  
$$

  

### 3. Non-Fermi Liquid Behaviors

To detect the behavior of non-Fermi liquid, we need the wave vector close to the Fermi liquid enough, and the standard we use is

The triangle lattice has

||||||||||
|---|---|---|---|---|---|---|---|---|
||2.6656|2.66559|33|||14|-7|0.00001|
||2.7233|2.72069|24|||0|9|0.00261|

### 4. Superconductivity

### 5. Entropy

The general formula of Helmholtz free energy at a fixed temperature is

$$  
  
$$

  

and we can write the entropy as

$$  
  
$$

  

#### 5.1 High Temperature Limit

When

$$  
  
$$

  

$$  
  
$$

  

$$  
  
$$

  

For the Ising part, the dimension of the Hilbert space is

$$  
  
$$

  

$$  
  
$$

  

#### 5.2 Low Temperature

$$  
  
$$

  

The difference of entropy between two neighbor

$$  
  
$$

  

$$  
  
$$

  

![entropy](file:///Users/hongtu/Desktop/QCP_plot/entropy.png?lastModify=1705228348)

The errorbar increases as the temperature decreases because of the integral process.

#### 5.3 Pure Ising Case

$$  
  
$$

  

![image-20231205150447259](file:///Users/hongtu/Library/Application%20Support/typora-user-images/image-20231205150447259.png?lastModify=1705228348)