#### 1. Z-flux
修改内容：
添加了边角的hopping相位
将xmag从1.0修改到了2.0

令$\vec{a}$和$\vec{b}$是实空间的两个基矢，$a_1$和$b_1$是其$x$方向的分量，$a_2$和$b_2$是其$y$方向的分量
考虑两个格点$\vec{i} = (x \vec{a} + L \vec{b})$和$\vec{j} = (x' \vec{a} +  \vec{b})$，它们通过一个bond连接，下面我们要计算$c^{\dagger}_\vec{i} c_\vec{j}$和$c^{\dagger}_\vec{j} c_\vec{i}$的Peirls相位，来讨论哈密顿量在加入z-flux后保持厄米性的条件

先考虑由Landau规范$\vec{A}(\vec{r}) = -B(y, 0, 0)$导致的相位，
$$
\phi_{\vec{i} \rightarrow \vec{j}} 
= \frac{2 \pi}{\Phi_0} \int_{\vec{i}}^{\vec{j}} \vec{A}_L(\vec{l}) \cdot d \vec{l} 
= -\frac{ \pi B}{\Phi_0} (j_x - i_x)(j_y + i_y)
$$
对于处于非边界的格点，只是积分的上下限颠倒，厄米性自动保持
对于$c^{\dagger}_\vec{i} c_\vec{j}$，此时从$\vec{i}$积分到$\vec{i}' = (x' \vec{a} + (L+1) \vec{b})$，相位为
$$
\phi_1 = -\frac{ \pi B}{\Phi_0} [(x' - x) a_1 + b_1] [(x + x')a_2 + (2L+1)b_2]
$$
对于$c^{\dagger}_{\vec{j}} c_{\vec{i}}$，此时从$\vec{j}$积分到$\vec{j}' = (x \vec{a} + 0 \vec{b})$，相位为
$$
\phi_2 = -\frac{ \pi B}{\Phi_0} [(x - x') a_1 - b_1] [(x + x')a_2 + b_2]
$$

现在考虑边界条件导致的相位
根据公式
$$
c^{\dagger}_{y \vec{b} + x \vec{a}} c_{(\pm L + y') \vec{b} + x' \vec{a}} = c^{\dagger}_{y\vec{b}+x\vec{a}} c_{y'\vec{b}+x'\vec{a}} e^{i 2\pi / \Phi_0 B (\pm L)b_2 (y'b_1 + x' a_1)}  
$$
$$
\psi_ = \frac{2 \pi B}{\Phi_0} (\pm L) b_2 (y' b_1 + x' a_1)
$$
对于$c^{\dagger}_\vec{i} c_\vec{j}$，我们只需将上面公式参数设为$y=L$和$y' = 1$
$$
\psi_1 = \frac{2 \pi B}{\Phi_0} L b_2 ( b_1 + x' a_1)
$$
对于$c^{\dagger}_\vec{j} c_\vec{i}$，我们只需将上面公式参数设为$y=1$和$y' = L$，并将$x$与$x'$颠倒
$$
\psi_2 = -\frac{2 \pi B}{\Phi_0} L b_2 (L b_1 + x a_1)
$$

现在我们可以求出四个相位的和
$$
\begin{aligned}
\phi_1 + \phi_2 &= -\frac{2\pi B}{\Phi_0} L b_2 [(x' - x) a_1 + b_1] \\
\psi_1 + \psi_2 &= \frac{2\pi B}{\Phi_0}Lb_2 [(x'-x)a_1 + (1-L)b_1]
\end{aligned}
$$
我们看到两个式子中括号的第一项被消掉了，剩余的是
$$
\phi_1 + \phi_2 + \psi_1 + \psi_2 = -\frac{2\pi B}{\Phi_0}L^2 b_1 b_2
$$
在晶格平移不变性的讨论中我们知道$B$的取值为
$$
B = \frac{n \Phi_0}{L^2(a_1b_2 - a_2b_1)} 
$$
所以最后我们得到
$$
\phi_1 + \phi_2 + \psi_1 + \psi_2 
= -\frac{2\pi}{\Phi_0}  
\frac{n \Phi_0}{L^2(a_1b_2 - a_2b_1)}  
L^2 b_1 b_2
= -2 n \pi \frac{b_1 b_2}{a_1b_2 - a_2b_1}
$$

* 对于正方晶格，由于$b_1 = 0$，所以上式为$0$，即对于正方晶格，任意取值的$n$都可以保持哈密顿量的厄米性
* 对于三角晶格，$a_1 = 1$，$a_2 = 0$，$b_1 = -\frac{1}{2}$，$b_2 = \frac{\sqrt{3}}{2}$
所以上式为：
$$
\phi_1 + \phi_2 + \psi_1 + \psi_2 
= -2 n \pi \frac{b_1 b_2}{a_1b_2 - a_2b_1}
=  n \pi
$$
所以为了保持哈密顿量的厄米性，我们只可以施加$n=2, 4, ...$的磁通量

##### 是否存在$n=1$的解？
1. 令$x$方向的相位为$0$
这相当于确定
$$
AX = b
$$
是否有解. 其中
$$
A = 
\begin{bmatrix} 
1 & 1 & 0 & 0 & 0 & 0 \\ 
0 & 1 & 1 & 0 & 0 & 0 \\ 
0 & 0 & 1 & 1 & 0 & 0 \\
0 & 0 & 0 & 1 & 1 & 0 \\
0 & 0 & 0 & 0 & 1 & 1 \\
1 & 0 & 0 & 0 & 0 & 1 \\
\end{bmatrix}
$$
$$
b = 
\begin{bmatrix} 
1 \\ 
-1 \\ 
1 \\
-1 \\
1 \\
-1 \\
\end{bmatrix}
$$
通过Python我们确定了$A$是一个奇异矩阵，方程无解

2. 不限制$x$方向的相位
这相当于解方程
$$
MX = b
$$
其中
$$
M = 
\begin{bmatrix} 
I_{9 \times 9} & I_{9 \times 9} & I_{9 \times 9} \\ 
I_{9 \times 9} & A_{9 \times 9} & B_{9 \times 9} \\ 
\end{bmatrix}
$$
$$
A = 
\begin{bmatrix} 
0 & 0 & P_{3 \times 3}  \\ 
P_{3 \times 3} & 0 & 0  \\ 
0 & P_{3 \times 3} & 0  \\
\end{bmatrix}
$$
$$
P = 
\begin{bmatrix} 
0 & 1 & 0  \\ 
0 & 0 & 1  \\ 
1 & 0 & 0  \\
\end{bmatrix}
$$
以及
$$
B = 
\begin{bmatrix} 
0  & I_{3 \times 3}  \\ 
I_{6 \times 6} & 0  \\ 
\end{bmatrix}
$$
$b$矩阵与之前类似，不过是$18 \times 1$的版本
为了得到方程是否有解，我们比较$M$与$M|b$的rank，方法是求出各自的svd分解，观察非$0$的奇异值个数
```python
U1, D1, V1 = np.linalg.svd(M)
U2, D2, V2 = np.linalg.svd(M_ex)
print(D1)
print(D2)
```
结果为
```
[2.44948974e+00 2.17532775e+00 2.17532775e+00 2.17532775e+00 2.17532775e+00 2.17532775e+00 2.17532775e+00 1.73205081e+00 1.73205081e+00 1.73205081e+00 1.73205081e+00 1.12603250e+00 1.12603250e+00 1.12603250e+00 1.12603250e+00 1.12603250e+00 1.12603250e+00 1.11702546e-16] 
[4.50516633 2.44948974 2.17532775 2.17532775 2.17532775 2.17532775 2.17532775 2.12302167 1.73205081 1.73205081 1.73205081 1.47518226 1.1260325 1.1260325 1.1260325 1.1260325 1.1260325 0.14174869]
```
观察到$M$有一个非常接近$0$的奇异值，而$M|b$的奇异值均为有限值，所以$\mathrm{rank}(M) \lt \mathrm{rank}(M|b)$，方程也是无解的

#### 2. Hot Spot
在低温时
$$
G(\mathbf{k}, \frac{\beta}{2}) \approx \beta A(\mathbf{k}, \omega = 0)
$$
在hot spot附近准粒子会受到更强的散射，导致权重更低

#### 3. Eliashberg Theory
$$
-\mathrm{\Sigma}(\vec{k}_F, \nu_n) = \gamma_{\vec{k}} + (1 / Z_{\vec{k}} - 1) \nu_n + \mathcal{O}(\nu_n^2) 
$$
其中$\gamma_{\vec{k}} \ll T$是非弹性散射率. 
$\omega_n$远大于$\Sigma(\omega_n)$的要求不够满足
在三角模型中，$c_q = 1.57, a_q = 1.86$，从原本的scaling公式出发得到的$\overline{g} = (\frac{\xi}{2})^2 D_0 \approx 0.16$，也许并不满足$\overline{g} \gg \Sigma$的要求
![[Pasted image 20240117144915.png]]
用第二种形式得到的结果
![[Pasted image 20240122154553.png]]
#### 4. DC Resistivity
***
想办法用外插解决一下有限尺寸问题
在0频处是否存在一个$\delta$函数
***
费米液体理论的失效表明输运性质在QCP附近也可能发生强烈变化. 其中一个有趣的量就是直流电导率，但是使用虚时间关联函数的解析延拓来得到直流电导率很困难.
$$
\begin{aligned}
\Lambda(\omega_n) &= \int d\tau e^{i \omega_n \tau} \tilde{\Lambda}(\tau) \\
\tilde{\Lambda}_{ii}(\tau) &= \langle \mathcal{T} J_i(\tau) J_i(0) \rangle 
\end{aligned}
$$
观察$\Lambda(\omega_n)$的行为，如果在第一和第二个松原频率之间有一个突变，则$\sigma'(\omega)$有一个Drude-like的组成. $\Lambda(\omega_n)$的缓慢下降则表明了另一个广泛特征，即光学权重分布在一个与$T$相比较宽的频率范围内. 所以可以试着采用其解析延拓形式：
$$
\Lambda_{\mathrm{fit}}(\omega_n) = \sum_{j=1}^2 \frac{A_j}{\omega_n^2 + \gamma_j |\omega_n| + \Omega_j^2}
$$
我们可以得到相应的电导为
$$
\sigma'(\omega) = \sum_{j=1}^2 \frac{A_j \gamma_j}{(\Omega_j^2 - \omega^2)^2 + \gamma_j^2 \omega^2}
$$
在我们的模型中，更多取决于$0$频率，所以可以只使用一个模式.

##### “resistivity proxy” $\rho_2$
可以从虚时间数据中直接计算出来，不需要解析延拓，在合理的假设下与$\rho_{DC}$成正比. 
虚时流流关联函数与实频电导实部有以下联系：
$$
\Lambda(i \omega_n) = \int \frac{d \omega}{\pi} \frac{\omega^2 \sigma'(\omega)}{\omega^2 + \omega_n^2}
$$
$$
\tilde{\Lambda}(\tau) 
= \int \frac{d \omega}{2 \pi} \sigma'(\omega) \frac{\omega \cosh \left[ (\frac{\beta}{2} - \tau) \omega \right]}{\sinh \left( \frac{\beta \omega}{2} \right)}
$$
上面的公式对于$0 \le \tau \le \beta$有效. 

$$
m_0 \equiv \beta \tilde{\Lambda}(\tau = \frac{\beta}{2}) = \beta \int \frac{d\omega}{2\pi} \frac{\omega \sigma'(\omega)}{\sinh \left( \frac{\beta \omega}{2} \right)}
$$
$$
m_2 \equiv \beta \partial^2_{\tau} \tilde{\Lambda}(\tau = \frac{\beta}{2}) = \beta \int \frac{d\omega}{2\pi} \frac{\omega^3 \sigma'(\omega)}{\sinh \left( \frac{\beta \omega}{2} \right)}
$$
$$
\rho_2 \equiv \frac{m_2}{2\pi T m_0^2} = \left. \frac{\partial^2_\tau \tilde{\Lambda}}{2 \pi \tilde{\Lambda}^2} \right|_{\tau = \beta / 2}
$$





#### 5. QCP

##### References
[1] Shao H, Guo W, Sandvik A W. Quantum criticality with two length scales[J]. Science, 2016, 352(6282): 213-216.
[2] Qin Y Q, He Y Y, You Y Z, et al. Duality between the deconfined quantum-critical point and the bosonic topological transition[J]. Physical Review X, 2017, 7(3): 031052.

受到有限尺寸效应的影响，费米子和玻色子的cross point并不相同. 以$\beta = 1.0$为例
![[Pasted image 20240114182935.png]]
![[Pasted image 20240114182945.png]]
我们可以看到费米子受到的有限尺寸效应较为严重. 
根据Ref[1]，可观测量的标准标度形式为：
$$
O(\delta, L) = L^{-\kappa / \nu} f(\delta L^{	1/\nu}, \lambda L^{-\omega}).
$$
考虑尺寸为$L$和$rL(r\gt 1)$的两个系统，它们的交叉点为：
$$
\begin{align}
\delta^*(L) 
=& \frac{a_0}{a_1} \frac{1 - r^{-\kappa/\nu}}{r^{(1-\kappa)/\nu-1}} L^{-1/\nu} + \frac{b_1}{a_1} \frac{1 - r^{-(\kappa/\nu+\omega)}}{r^{(1-\kappa)/\nu-1}} L^{-(1/\nu+\omega)}
\end{align} 
$$
当可观测量在交叉点尺寸无关，也就是$\kappa = 0$时，我们可以得到
$$
\delta^*(L) = q^*_c(L) - q_c \propto L^{-(1/\nu+\omega)}  
$$
所以根据这个式子我们可以得到热力学极限下的相变点
![[Pasted image 20240114184118.png]]
得到热力学极限下的fermion相变点为$h_c = 4.93(9)$，与data collapse得到的Ising相变点相差不大，所以我们可以安全地使用Ising相变点数据
##### Phase Diagram
![[Pasted image 20240114190238.png]]
![[Pasted image 20240114184827.png]]
计算出相变点为$h_c = 5.31(5)$，临界指数为$\nu z = 0.86$

#### 6. Scaling
##### T-scaling
![[Pasted image 20240115115900.png]]
得到的指数为$c_t = 0.06(3)$，$a_t = 1.70(4)$

##### h-scaling
![[Pasted image 20240116145032.png]]
得到的指数为$c_h = 0.54(2)$，$a_h=1.29(1)$

##### q-scaling
![[Pasted image 20240115121603.png]]
$c_q = 1.57(1)$，$a_q = 1.86(1)$

##### Scaling All
![[Pasted image 20240118173424.png]]
#### 7. Superconductivity
##### References
电流密度算符及超导计算公式
[1] Optical and DC conductivity of the two-dimensional Hubbard model in the pseudogap regime and across the antiferromagnetic quantum critical point, including vertex corrections
[2] Insulator, metal, or superconductor: The criteria

要确定的第一件事：
$$
j^x_{i \lambda \sigma} = it e^{i\phi^{\lambda \sigma}_{i, i + \hat{x}}} c^{\dagger}_{i \lambda \sigma} c_{i + \hat{x}, \lambda \sigma} + h.c.
$$
这个式子与
$$
j^x_{i \lambda \sigma} = it\sum_{\delta} \delta_x e^{i\phi^{\lambda \sigma}_{i, i + \delta}} c^{\dagger}_{i \lambda \sigma} c_{i + \delta, \lambda \sigma}
$$
是等价的，这是由于系统的平移不变性
不加z-flux的情况下流流关联函数的结果非常糟糕
加flux
![[Pasted image 20240109144158.png]]![[Pasted image 20240109144201.png]]


#### 8. Entropy
在$L=18$中跑了20个bin，errorbar的降低效果不够好，并且entropy增大的信号变得很弱
![[Pasted image 20240117141748.png]]
![[Pasted image 20240117141658.png]]
降低errorbar要求bin的数量很大，所以降低到了$L=12$，在未加flux时观察到的是熵随着h增大，在加了flux之后在临界点观察到熵增大的信号
![[Pasted image 20240117140658.png]]
	![[Pasted image 20240117140356.png]]
![[Pasted image 20240117141137.png]]
#### 9. Negativity
n阶Renyi Negativity（负性）的定义是
$$
\mathcal{E}_n = -\frac{1}{n-1} \ln \mathrm{Tr} \left [ \left( \rho^{T_2^f} \right)^n \right]
$$
$\mathrm{Tr}  [ ( \rho^{T_2^f} )^n]$是部分转置密度矩阵（PTDM）的n阶矩，与n阶Renyi纠缠熵的关系为
$$
S_n(A_1) = -(\ln \mathrm{Tr} \rho^n_{A_1}) / (n-1)
$$
其中
$$
\rho_{A_1} = \mathrm{Tr}_{A_2} \rho
$$
可以得到在DQMC中二阶Renyi negativity的公式为

$$
\mathcal{E}_2 = 
-\ln \mathrm{Tr} \left \{
\sum_{\mathbf{s}_1 \mathbf{s}_2} P_{\mathbf{s}_1} P_{\mathbf{s}_2}
\times \det
\left[ G^{T_2^f}_{\mathbf{s}_1} G^{T_2^f}_{\mathbf{s}_2} + 
\left( I- G^{T_2^f}_{\mathbf{s}_1} \right) \left( I- G^{T_2^f}_{\mathbf{s}_2} \right)
\right]
\right \}
$$
$\mathrm{Tr} [( \rho^{T_2^f} )^n]$和$\mathrm{Tr}[\rho^n]$的ratio为：
$$
R_n = -\frac{1}{n-1} \ln \left \{  \frac{\mathrm{Tr} \left[ \left( \rho^{T_2^f} \right)^n \right]}{\mathrm{Tr} [\rho]} \right \} = \mathcal{E}_n - S^{\mathrm{th}}_n
$$
其中$S^{\mathrm{th}}_n = - (\ln \mathrm{Tr} \rho^n ) / (n-1)$是热力学Renyi熵，可以通过认为$A_2$不存在来得到，混合态纠缠的准确描述需要减去这一部分.

