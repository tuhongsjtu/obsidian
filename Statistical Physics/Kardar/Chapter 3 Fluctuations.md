- [[#3.1    Scattering and fluctuations|3.1    Scattering and fluctuations]]
- [[#3.2    Correlation functions and susceptibilities|3.2    Correlation functions and susceptibilities]]
- [[#3.3    Lower critical dimension|3.3    Lower critical dimension]]
- [[#3.4    Comparison to experiments|3.4    Comparison to experiments]]
- [[#3.5    Gaussian integrals|3.5    Gaussian integrals]]
- [[#3.6    Fluctuation corrections to the saddle point|3.6    Fluctuation corrections to the saddle point]]
- [[#3.7    The Ginzburg criterion|3.7    The Ginzburg criterion]]

## 3.1    Scattering and fluctuations
除了bulk热力学实验以外，散射测量可以用于探测波长$\lambda$量级的微观涨落. 在一个典型的设置中，波矢为$\mathbf{k}_i$的束入射到样品上，并在波矢$\mathbf{k}_s = \mathbf{k}_i + \mathbf{q}$处测量散射强度. 对于弹性散射，$|\mathbf{k}_i| = |\mathbf{k}_s| \equiv k$并且$q \equiv |\mathbf{q}| = 2k \sin \theta$，其中$\theta$为入射波和散射波之间的夹角. 对于散射的标准处理从费米黄金规则开始，通常导出一个以下形式的散射振幅：
$$
A(\mathbf{q}) \propto \langle \mathbf{k}_s \otimes f | \mathcal{U} | \mathbf{k}_i \otimes i \rangle \propto \sigma(\mathbf{q}) \int d^d \mathbf{x} e^{i \mathbf{q} \cdot \mathbf{x}} \rho(\mathbf{x}).
$$
在上面的式子中$| i \rangle$和$| f \rangle$表示样品的起始和最终状态，$\mathcal{U}$是散射势，可以分解为一系列样品导致的散射元素的求和. 振幅具有描述单个元件散射的*局部*形状因子$\sigma(\mathbf{q})$. 处于我们的目的，更有趣的*全局*信息包含在$\rho(\mathbf{q})$中，即散射体$\rho(\mathbf{x})$的全局密度的傅立叶变换. 

适当的散射密度取决于探针的性质. 光散射感知实际原子密度，电子散射测量电荷密度，而中子散射通常用于探测磁化强度. 大多数此类探针实际上并不响应系统快照，而是观察构型的时间平均. 因此观察到的散射强度为：
$$
S(\mathbf{q}) \propto \langle |A(\mathbf{q})|^2 \rangle \propto \langle |\rho(\mathbf{q})|^2 \rangle . 
\tag{3.2}
$$
$\langle \bullet \rangle$表示$\bullet$的热力学平均，由于遍历性大多数时候可以用来替代时间平均值.
式(3.2)表明，均匀的密度只会导致向前散射$\mathbf{q} = \mathbf{0}$，而长波长涨落可以通过在小角度或小$k$下工作来研究. 如果散射是由磁化密度引起的，我们可以使用Landau-Ginzburg哈密顿量来计算其强度. 特定构型的概率为：
$$
\mathcal{P}[\vec{m}(\mathbf{x})] \propto \exp \left\{ -\int d^d \mathbf{x} \left[  
\frac{K}{2} (\nabla m)^2 + \frac{t}{2} m^2 + u m^4
\right] \right\}.
$$
正如之前所讨论的，最可能的构型是*均匀*的，$\vec{m}(\mathbf{x})=\overline{m} \hat{e}_1$，其中$\hat{e}_1$是一个单位矢量（当$t \gt 0$时$\overline{m}=0$，当$t \lt 0$时$\overline{m}=\sqrt{-t/4u}$）. 我们可以设置以下形式来检查这种构型附近的小涨落：
$$
\vec{m}(\mathbf{x}) = [\overline{m} + \phi_l(\mathbf{x})] \hat{e}_1 + \sum_{\alpha=2}^n \phi_{t, \alpha}(\mathbf{x}) \hat{e}_{\alpha}
\tag{3.4}
$$
其中$\phi_l$和$\phi_t$分别表示*纵向*和*横向*涨落. 后者可以沿着垂直于平均磁化强度的任何$n-1$各方向发生.
在替换掉式(3.4)后，展开到二阶的Landau-Ginzburg哈密顿量中的项为：
$$
\begin{align}
(\nabla m)^2 &= (\nabla \phi_l)^2 + (\nabla \phi_t)^2, \\
m^2 &= \overline{m}^2 + 2 \overline{m} \phi_l + \phi_l^2 + \phi_t^2, \\
m^4 &= \overline{m}^4 + 4 \overline{m}^3 \phi_l + 6 \overline{m}^2 \phi_l^2 + 2 \overline{m}^2 \phi_t^2 + \mathcal{O}(\phi_l^3, \phi_t^3),
\end{align}
$$
这导致了一个二次的能量损失
$$
\begin{align}
\beta \mathcal{H} \equiv -\ln \mathcal{P} = V \left( \frac{t}{2} \overline{m}^2 + u \overline{m}^4 \right) + \int d^d \mathbf{x} \left[ \frac{K}{2} (\nabla \phi_l)^2 + \frac{t + 12 u\overline{m}^2}{2} \phi_l^2 \right] \\
+ \int d^d \mathbf{x} \left[ \frac{K}{2} (\nabla \phi_t)^2 + \frac{t + 4u \overline{m}^2}{2} \phi_t^2 \right] + \mathcal{O}(\phi_l^3, \phi_t^3).
\end{align}
$$
对于均匀变形，纵向和横向恢复势（*restoring potentials*，类似于谐振子的弹性势能）具有由下式给出的“刚度常数”：
$$
\frac{K}{\xi_{\ell}^2} \equiv t+12 u \overline{m}^2=\left.\frac{\partial^2 \Psi(m)}{\partial \phi_{\ell}^2}\right|_{\overline{m}}= \begin{cases}t & \text { for } t>0 \\ -2 t & \text { for } t<0\end{cases}
\tag{3.6}
$$
$$
\frac{K}{\xi_{t}^2} \equiv t+4 u \overline{m}^2=\left.\frac{\partial^2 \Psi(m)}{\partial \phi_{t}^2}\right|_{\overline{m}}= \begin{cases}t & \text { for } t>0 \\ 0 & \text { for } t<0\end{cases}
\tag{3.7}
$$
长度尺度$\xi_{\ell}$和$\xi_{t}$的物理意义很快就会变得显而易见. 注意顺磁体的纵向分量和横向分量之间没有区别$(t \gt 0)$，这与顺磁相中磁化是各向同性是相符的. 对于$t \lt 0$时的有序磁体，横向涨落没有恢复力，这对应于上一章中讨论的Goldstone模式. 

下面我们将其推至傅立叶空间中. $\phi(\mathbf{x}) = \sum_{\mathbf{q}} \phi_{\mathbf{q}} e^{i \mathbf{q} \cdot \mathbf{x}} / \sqrt{V}$，一个特定构型的概率为：
$$
\mathcal{P}[\{ \phi_{\ell, \mathbf{q}}; \phi_{t, \mathbf{q}} \}]
\propto \prod_{\mathbf{q}} \exp \left\{ -\frac{K}{2} (q^2 + \xi^{-2}_{\ell}) |\phi_{\ell, \mathbf{q}}|^2  \right\} \cdot \exp \left\{ -\frac{K}{2} (q^2 + \xi^{-2}_{t}) |\phi_{t, \mathbf{q}}|^2 \right\}.
$$
显然每个模式表现为均值为$0$的高斯型随机变量，因此两点关联函数为：
$$
\langle \phi_{\alpha, \mathbf{q}} \phi_{\beta, \mathbf{q}'} \rangle = \frac{\delta_{\alpha, \beta} \delta_{\mathbf{q}, -\mathbf{q}'}}{K(q^2 + \xi_{\alpha}^{-2})}, 
\tag{3.9}
$$
其中下标指的是纵向分量或任何横向分量. 通过使用自旋极化中子源，可以调整相对方向以探测纵向或横向关联. *洛伦兹形式*$S(\mathbf{q}) \propto 1/(q^2 + \xi^{-2})$通常非常适合远离临界点的散射线形状. (3.9)式表明，在有序相中，纵向散射仍然呈现洛伦兹形式（由于自发磁化，在$\mathbf{q} = \mathbf{0}$处的$\delta$函数之上），而横向散射始终以$1/q^2$增长. 同样的幂律衰减预计也会在临界点$t = 0$处成立. 实际实验拟合产生以下形式的幂律：
$$
S(\mathbf{q}, T=T_c) \propto \frac{1}{q^{2 - \eta}}
\tag{3.10}
$$
$\eta$是一个小的正值. 

![[Pasted image 20240318205144.png]]

## 3.2    Correlation functions and susceptibilities
我们还可以得到时空间的涨落. 涨落的平均值$\langle \phi_{\alpha}(\mathbf{x}) \rangle = \langle m_{\alpha}(\mathbf{x}) - \overline{m}_{\alpha} \rangle$显然是$0$，连接关联函数（connected correlation function）为：
$$
\begin{align}
G^c_{\alpha, \beta}(\mathbf{x}, \mathbf{x}')
& \equiv \langle ( m_{\alpha}(\mathbf{x}) - \overline{m}_{\alpha}) (m_{\beta}(\mathbf{x}') - \overline{m}_{\beta}) \rangle  \\
& = \langle \phi_{\alpha}(\mathbf{x}) \phi_{\beta}(\mathbf{x}') \rangle = \frac{1}{V} \sum_{\mathbf{q}, \mathbf{q}'} e^{i \mathbf{q} \cdot \mathbf{x} + i \mathbf{q}' \cdot \mathbf{x}'} \langle \phi_{\alpha, \mathbf{q}} \phi_{\beta, \mathbf{q}'} \rangle .
\end{align}
$$
使用(3.9)式我们得到
$$
G^c_{\alpha, \beta}(\mathbf{x}, \mathbf{x}') = \frac{\delta_{\alpha,\beta}}{V} \sum_{\mathbf{q}} \frac{e^{i \mathbf{q} \cdot (\mathbf{x} - \mathbf{x}')}}{K(q^2 + \xi_{\alpha}^{-2})} \equiv - \frac{\delta_{\alpha, \beta}}{K} I_d(\mathbf{x} - \mathbf{x}', \xi_{\alpha}),
\tag{3.12}
$$
在连续极限下
$$
I_d(\mathbf{x}, \xi) = - \int \frac{d^d \mathbf{q}}{(2 \pi)^d} \frac{e^{i \mathbf{q} \cdot \mathbf{x}}}{q^2 + \xi^{-2}}.
$$
或者，$I_d$是以下微分方程的解:
$$
\nabla^2 I_d(x) = \int \frac{d^d \mathbf{q}}{(2\pi)^d} \frac{q^2 e^{i \mathbf{q} \cdot \mathbf{x}}}{q^2 + \xi^{-2}} = \int \frac{d^d \mathbf{q}}{(2\pi)^d} \left[ 1 - \frac{\xi^{-2} }{q^2 + \xi^{-2}} \right] e^{i \mathbf{q} \cdot \mathbf{x}} = \delta^d(\mathbf{x}) + \frac{I_d(\mathbf{x})}{\xi^2}.
$$
这个解是球对称的，满足下面的方程：
$$
\frac{d^2 I_d}{dx^2} + \frac{d-1}{x} \frac{d I_d}{dx} = \frac{I_d}{\xi^2} + \delta^d(\mathbf{x}).
\tag{3.15}
$$
我们可以尝试使用一个在远距离指数衰减的函数作为试探解：
$$
I_d(x) \propto \frac{\exp(-x / \xi)}{x^p}.
\tag{3.16}
$$
（我们预计存在次主导幂律）于是$I_d$的导数为：
$$
\begin{align}
\frac{d I_d}{dx} &= - \left( \frac{p}{x} + \frac{1}{\xi} \right) I_d, \\
\frac{d^2 I_d}{dx^2} &= \left( \frac{p(p+1)}{x^2} + \frac{2p}{x\xi} + \frac{1}{\xi^2} \right) I_d.
\end{align}
$$
对于$x \neq 0$，(3.15)和(3.16)给出：
$$
\frac{p(p+1)}{x^2} + \frac{2p}{x\xi} + \frac{1}{\xi^2} - \frac{p(d-1)}{x^2} - \frac{(d-1)}{x\xi} = \frac{1}{\xi^2}.
\tag{3.18}
$$
选择$\xi$作为衰减长度保证了上面方程中常数项的消去. 指数$p$通过要求消去下一个最大项来确定. 对于$x \ll \xi$，$1/x^2$项是次重要的，所以我们设置$p(p+1) = p(d-1)$，得到$p = d-2$. 这是与库仑相互作用相似的指数，事实上在这个长度范围内，关联感受不到$\xi$的存在. 如下一节所示，这个极限的合适的归一化结果为：
$$
I_d(x) \simeq C_d(x)=\frac{x^{2-d}}{(2-d) S_d} \quad(x \ll \xi)
\tag{3.19}
$$
（请注意，始终可以将常数项添加到解中以满足所研究的相关函数的适当限制. ）在大距离$x \gg \xi$时，$1/(x \xi)$项主导了(3.18)，我们可以得到$p = (d - 1) / 2$. 匹配(3.19)在$x\approx \xi$的连续性可以得到可以得到
$$
I_d(x) \simeq \frac{\xi^{(3-d)/2}}{(2-d)S_d x^{(d-1)/2}} \exp(-x / \xi) \quad(x \gg \xi).
\tag{3.20}
$$
![[Pasted image 20240318221345.png]]
对于式(3.12)我们观察到横向和纵向关联表现不同. 靠近相变点时，纵向相关长度(3.6)的表现为：
$$
\xi_{\ell}= \begin{cases}t^{-1 / 2} / \sqrt{K} & \text { for } \mathrm{t}>0 \\ (-2 t)^{-1 / 2} / \sqrt{K} & \text { for } \mathrm{t}<0 .\end{cases}
$$

> [!关联长度] 
> 我们在之前的推导中有$\xi \approx t^{-gamma}$以及$\gamma = 1/2$，这可能是将$\xi_{\ell}$定义为关联长度的原因，因为它与之前的关联长度有着相同的标度行为.

奇异性可以被描述为$\xi_{\pm} \simeq \xi_0 B_{\pm} |t|^{-\nu_{\pm}}$，$\nu = 1/2$以及$B_+ / B_- = \sqrt{2}$是普适的，而$\xi_0 \propto 1/\sqrt{K}$并不是. 横场关联长度在$t \gt 0$时等于$\xi_{\ell}$，在$t \lt 0$时为无穷. 方程(3.19)表明在$T_c$处，关联按照$1/x^{d-2}$衰减. 事实上衰减指数通常用$1/x^{d-2+\eta}$来表示，其中$\eta$是和(3.10)式中相同的指数. 对连接关联函数进行积分会产生bulk磁化率. 比如纵向磁化率的发散性也可以从以下公式获得：
$$
\chi_{\ell} \propto \int \mathrm{d}^d \mathbf{x} G_{\ell}^c(\mathbf{x}) \propto \int_0^{\xi_{\ell}} \frac{\mathrm{d}^d x}{x^{d-2}} \propto \xi_{\ell}^2 \simeq A_{ \pm} t^{-1} .
$$
再次从上式中恢复通用指数和振幅. 对于$T \lt T_c$，横向关联没有上截止长度，横向磁化率的发散可以与系统尺寸$L$相关，如
$$
\chi_t \propto \int \mathrm{d}^d \mathbf{x} G_t^c(\mathbf{x}) \propto \int_0^L \frac{\mathrm{d}^d x}{x^{d-2}} \propto L^2.
$$


## 3.3    Lower critical dimension
在第二章中我们讨论了连续对称性的破缺如何伴随着低能激发（Goldstone模式）出现的. 这些模式可以被热力学涨落简单地激发，我们可以提问这种涨落对有序相的影响.

我们首先考虑超流有序相的情况，其局部序参量为$\psi(\mathbf{x})=|\psi(\mathbf{x})| e^{i \theta(\mathbf{x})}$. 假设序参量的振幅时均匀的，一个特定构型的概率为：
$$
\mathcal{P}[\theta(\mathbf{x})] \propto \exp \left[ -\frac{\overline{K}}{2} \int d^d \mathbf{x} (\nabla \theta)^2 \right].
\tag{3.24}
$$
我们抄袭第二章的处理可以将能量密度函数通过傅立叶变换转换成对动量的求和：
$$
\mathcal{P}[\theta(\mathbf{q})] \propto \exp \left[ -\frac{\overline{K}}{2} \sum_{\mathbf{q}} q^2 |\theta(\mathbf{q})|^2 \right] \propto \prod_{\mathbf{q}} p(\theta_{\mathbf{q}}).
$$
每一个$\theta_{\mathbf{q}}$都是一个均值为零的高斯分布独立变量，因此可以得到关联为：
$$
\langle \theta_{\mathbf{q}} \theta_{\mathbf{q}'} \rangle = \frac{\delta_{\mathbf{q}, -\mathbf{q}'}}{\overline{K} q^2}.
$$
同样的我们可以按照上式得到实空间中相位$\theta(\mathbf{x})$的关联. 显然由于对称性$\langle \theta(\mathbf{x}) \rangle = 0$，
$$
\langle \theta(\mathbf{x}) \theta(\mathbf{x}') \rangle = \frac{1}{V} \sum_{\mathbf{q}, \mathbf{q}'} e^{i\mathbf{q}\cdot\mathbf{x} + i\mathbf{q}'\cdot\mathbf{x}'} \langle \theta_{\mathbf{q}} \theta_{\mathbf{q}'} \rangle = \frac{1}{V} \sum_{\mathbf{q}} \frac{e^{i \mathbf{q} \cdot (\mathbf{x} - \mathbf{x}')}}{\overline{K} q^2}.
$$
在连续行极限下，我们可以将求和$\sum_{\mathbf{q}}$转化为积分$V \int d^d \mathbf{q} / (2\pi)^d$，因此我们得到：
$$
\langle \theta(\mathbf{x}) \theta(\mathbf{x'}) \rangle = \int \frac{d^d \mathbf{q}}{(2\pi)^d} \frac{e^{i \mathbf{q} \cdot (\mathbf{x} - \mathbf{x}')}}{\overline{K}q^2}
= - \frac{C_d(\mathbf{x} - \mathbf{x}')}{\overline{K}}.
$$
方程$C_d(\mathbf{x})$是d维空间在原点的单位电荷产生的库仑势，这是因为如果我们对其作用拉普拉斯算符可以得到：
$$
C_d(\mathbf{x}) = - \int \frac{d^d \mathbf{q}}{(2\pi)^d} \frac{e^{i\mathbf{q} \cdot \mathbf{x}}}{q^2}.
$$
$$
\nabla^2 C_d(\mathbf{x}) = \int \frac{d^d \mathbf{q}}{(2\pi)^d} \frac{q^2}{q^2} e^{i \mathbf{q} \cdot \mathbf{x}} = \delta^d(\mathbf{x}).
$$
我们可以通过高斯定理轻易的得到一个解：
$$
\int d^d x \nabla^2 C_d = \oint dS \cdot \nabla C_d.
$$
对于球对称的解$\nabla C_d = (dC_d / dx) \vec{x}$，上面的方程简化为：
$$
1 = S_d x^{d-1} \frac{dC_d}{dx},
$$
其中$S_d$是$d$维空间总立体角
$$
S_d = \frac{2\pi^{d/2}}{(d/2 - 1)!}
$$
因此我们可以得到：
$$
\frac{dC_d}{dx} = \frac{1}{S_d x^{d-1}} \Rightarrow C_d(x) = \frac{x^{2-d}}{(2-d) S_d} + c_0,
$$

$C_d(x)$的长距行为在$d=2$时发生巨大变化：
$$
\lim _{x \rightarrow \infty} C_d(x)= \begin{cases}c_0 & d>2 \\ \frac{x^{2-d}}{(2-d) S_d} & d<2 \\ \frac{\ln (x)}{2 \pi} & d=2 .\end{cases}
$$
积分的常数可以通过观察以下式子来得到：
$$
\langle[\theta(\mathbf{x}) - \theta(\mathbf{x}')]^2\rangle = 2 \langle \theta(\mathbf{x})^2 \rangle - 2\langle \theta(\mathbf{x}) \theta(\mathbf{x}') \rangle,
$$
当$\mathbf{x} \rightarrow \mathbf{x}'$时上式变为$0$，因此
$$
\langle [\theta(\mathbf{x}) - \theta(\mathbf{x}')]^2 \rangle = \frac{2(|\mathbf{x} - \mathbf{x}'|^{2-d} - a^{2-d})}{\overline{K}(2-d)S_d},
$$
其中$a$的量级是晶格间距.

对于$d \gt 2$，相位涨落是有限的，而对于$d \le 2$，相位涨落变得渐进大. 由于相位以$2 \pi$为界，因此这意味着相位中的长程有序被破坏（远处相位的关联涨落为无穷大，不具有长程序）. 通过检查相位涨落对两点关联函数的影响，结果更加明显.
$$
\langle \psi(\mathbf{x}) \psi^*(\mathbf{0}) \rangle = \overline{\psi}^2 \langle e^{i[\theta(\mathbf{x}) - \theta(\mathbf{0})]} \rangle.
$$
由于忽略了振幅涨落，我们实际上正在研究横向关联函数（此时的自由度只有两个，振幅与幅角，现在固定了振幅不变，因此幅角的变化此时为横向涨落）. 稍后我们将证明对于任何高斯分布变量的集合，有：
$$
\langle \exp(\alpha \theta) \rangle = \exp \left( \frac{\alpha^2}{2} \langle \theta^2 \rangle \right).
$$
现在我们先假设这个结果是理所当然的，我们可以得到：
$$
\langle \psi(\mathbf{x}) \psi^*(\mathbf{0})\rangle = \overline{\psi}^2 \exp \left[ -\frac{1}{2} \langle [ \theta(\mathbf{x}) - \theta(\mathbf{0})]^2 \rangle \right] = \overline{\psi}^2 \exp \left[ -\frac{x^{2-d} - a^{2-d}}{\overline{K}(2-d) S_d} \right],
$$
渐进的可以得到：
$$
\lim_{x \rightarrow \infty} \langle \psi(\mathbf{x}) \psi^*(\mathbf{0}) \rangle = 
\begin{cases}\overline{\psi'}^2 & d\gt2 \\ 0 & d\le2 .\end{cases}
$$

上面的例子代表了一个更普遍的结果，称为*Mermin-Wagner*定理. 该定理指出，在维度$d \le 2$的短程相互作用系统中，连续对称性不会自发破缺. 该定理的一些推论是：
(1) 必须仔细对待二维的边界维度，称为*下临界维度*. 正如我们稍后将在课程中演示的那样，尽管不存在真正的长程有序，但二维超流体实际上存在相变.
(2) 当破缺的对称性是离散的（例如$n = 1$）时，不存在Goldstone模式. 在这种情况下，长程有序可以降低至下临界尺寸$d = 1$.


## 3.4    Comparison to experiments


## 3.5    Gaussian integrals
在之前的章节中，涨落的能量损失计算到了二阶. 涨落也会改变鞍点自由能. 在计算这个修正之前，我们对计算高斯积分进行一个简短但必要的数学转换.

最简单的高斯积分包含一个变量$\phi$，
$$
\mathcal{J}_1 = \int_{-\infty}^{\infty} d \phi e^{-\frac{K}{2} \phi^2 + h\phi} = \sqrt{\frac{2 \pi}{K}} e^{\frac{h^2}{2K}}.
$$
通过上述表达式对$h$求道，包含$\phi$的幂次的积分产生了，即：
$$
\begin{align}
\frac{d}{dh}: \int_{-\infty}^{\infty} d\phi \phi e^{-\frac{K}{2}\phi^2 + h\phi} &= \sqrt{\frac{2\pi}{K}} e^{\frac{h^2}{2K}} \cdot \frac{h}{K}, \\
\frac{d^2}{dh^2}: \int_{-\infty}^{\infty} d\phi \phi^2 e^{-\frac{K}{2}\phi^2 + h\phi} &= \sqrt{\frac{2\pi}{K}} e^{\frac{h^2}{2K}} \cdot \left[ \frac{1}{K} + \frac{h^2}{K^2} \right].
\end{align}
$$
如果被积函数表示随机变量的概率密度，则上述积分意味着$\langle \phi \rangle = h/K$以及$\langle \phi^2 \rangle = h^2/K^2 + 1/K$. 相应的累积量为$\langle \phi \rangle_c = \langle \phi \rangle = h/K$以及$\langle \phi^2 \rangle_c = \langle \phi^2 \rangle - \langle \phi \rangle^2 = 1/K$. 事实上高斯分布的所有高阶累积量都为$0$，因为：
$$
\langle e^{-ik\phi} \rangle \equiv \exp \left[ \sum_{l = 1}^{\infty} \frac{(-ik)^l}{l!} \langle \phi^l \rangle_c \right] = \exp \left[ -ikh - \frac{k^2}{2K} \right].
$$

> [!Q] 
> 这里似乎应该没有$\exp$才对? 并不是，使用的是累积量，并且求和从1开始\
> 高阶累积量可以通过求导获得，而第二个等号告诉我们，二阶以上导数都是0 \
> derive？

下面我们考虑一个$N$变量的高斯积分：
$$
\mathcal{J}_N = \int_{-\infty}^{\infty} \prod_{i=1}^N d\phi_i \exp \left[ -\sum_{i, j} \frac{K_{i, j}}{2} \phi_i \phi_j + \sum_i h_i \phi_i \right].
\tag{3.43}
$$
这个积分可以通过对角化矩阵$\mathbf{K} \equiv K_{i, j}$来约化为$N$个单变量高斯积分的乘积. 因为我们只需要考虑*对称矩阵*（$K_{i, j} = K_{j, i}$），其本征值是实的，并且本征向量可以正交化. 让我们用$\vec{q}$和$K_q$分别表示$\mathbf{K}$的本征向量和本征值， 即$\mathbf{K} \vec{q} = K_{q} \vec{q}$. 向量$\{\vec{q}\}$在原来的$N$维空间中形成了一组新的坐标基矢，空间中的任意一点可以通过坐标$\{\phi_i\}$或者$\left\{ \tilde{\phi}_{q} \right\}$表示，其中$\phi_i = \sum_q \tilde{\phi}_q \vec{q}_i$. 我们现在可以将积分变量从$\{ \phi_i \}$转换为$\left\{ \tilde{\phi}_q \right\}$，与这个幺正变换相关的Jacobian是单位矩阵，所以原来的高斯积分变为：
$$
\mathcal{J}_N = \prod_{q=1}^N \int_{-\infty}^{\infty} d\tilde{\phi}_q 
\exp \left[ -\frac{K_q}{2} \tilde{\phi}_q^2 + \tilde{h}_q \tilde{\phi}_q \right]
= \prod_{q=1}^N \sqrt{\frac{2\pi}{K_q}} \exp \left[ \frac{\tilde{h}_q K_q^{-1} \tilde{h}_q}{2} \right].
$$
最终的表达式可以通过逆矩阵$\mathbf{K}^{-1}$以原始坐标表达. 由于矩阵的行列式不依赖于基矢的选取，所以$\det \mathbf{K} = \prod_q K_q$，得到
$$
\mathcal{J}_N = \sqrt{\frac{(2\pi)^N}{\det \mathbf{K}}} \exp \left[ \sum_{i, j} \frac{K^{-1}_{i, j}}{2} h_i h_j \right].
\tag{3.45}
$$
将$\left\{ \phi_i \right\}$视为高斯随机变量，其联合概率分布正比于积分(3.43)，*联合特征函数*为：
$$
\langle e^{-i \sum_j k_j \phi_j} \rangle = \exp \left[ -i \sum_{i, j} K^{-1}_{i, j} h_i h_j - \sum_{i, j} \frac{K^{-1}_{i,j}}{2} k_i k_j \right].
\tag{3.46}
$$
分布的*矩*由特征函数对$k_i$的导数获得，*累积量*由其对数的导数得到. 因此(3.46)意味着
$$
\begin{cases}
\langle \phi_i \rangle_c = \sum_{j} K^{-1}_{i, j} h_j \\
\langle \phi_i \phi_j \rangle_c = K_{i, j}^{-1}.
\end{cases}
\tag{3.47}
$$

> [!NOTE] Derive
> Contents

(3.46)的另一个有用的形式是：
$$
\langle \exp(A) \rangle = \exp \left[ \langle A \rangle_c + \frac{1}{2} \langle A^2 \rangle_c \right],
$$
其中$A = \sum_i a_i \phi_i$是高斯分布变量的任意线性组合. 在上一节中我们已经使用这个公式计算存在相位涨落时超流中序参量的关联. 

高斯*泛函积分*是上述多变量积分的极限情况. 将点$i$视为$d$维晶格的位置，并让间距为零. 在连续极限下，$\{\phi_i\}$转化为函数$\phi(\mathbf{x})$，矩阵$K_{ij}$被替换为*核函数*$K(\mathbf{x}, \mathbf{x}')$. $(3.45)$的一个自然的推广为：
$$
\begin{align}
\int_{-\infty}^{\infty} &\mathcal{D}\phi(\mathbf{x}) \exp \left[ -\int d^d\mathbf{x}  d^d \mathbf{x}' \frac{K(\mathbf{x}, \mathbf{x}')}{2} \phi(\mathbf{x}) \phi(\mathbf{x}') + \int d^d \mathbf{x} h(\mathbf{x}) \phi(\mathbf{x}) \right] \\
& \propto (\det \mathbf{K})^{-1/2} \exp \left[ \int d^d \mathbf{x} d^d \mathbf{x}' \frac{K^{-1}(\mathbf{x}, \mathbf{x}')}{2} h(\mathbf{x}) h(\mathbf{x}') \right],
\end{align}
\tag{3.49}
$$
其中逆核函数$K^{-1}(\mathbf{x}, \mathbf{x}')$满足：
$$
\int d^d \mathbf{x}' K(\mathbf{x}, \mathbf{x}') K^{-1}(\mathbf{x}', \mathbf{x}'') = \delta^d(\mathbf{x} - \mathbf{x}'').
\tag{3.50}
$$
符号$\mathcal{D}\phi(\mathbf{x})$用于代表泛函积分. 这里有一个比例常数$(2\pi)^{N/2}$被排除在(3.49)之外. 虽然$N \rightarrow \infty$的连续极限在形式上是无限的，但它不会影响通过对积分求导得到的平均值. 特别是，(3.47)推广为：
$$
\begin{cases}
\langle \phi(\mathbf{x}) \rangle_c = \int d^d \mathbf{x}' K^{-1}(\mathbf{x}, \mathbf{x}') h(\mathbf{x}') \\
\langle \phi(\mathbf{x}) \phi(\mathbf{x}') \rangle_c = K^{-1}(\mathbf{x}, \mathbf{x}').
\end{cases}
$$

在Landau-Ginzburg哈密顿量处理小涨落时，我们遇到二次型：
$$
\int d^d \mathbf{x} [ (\nabla \phi)^2 + \phi^2 / \xi^2 ] 
\equiv \int d^d\mathbf{x} d^d\mathbf{x}' \phi(\mathbf{x}') \delta^d(\mathbf{x} - \mathbf{x}') (-\nabla^2 + \xi^{-2}) \phi(\mathbf{x}),
$$
这个例子中核函数为：
$$
K(\mathbf{x}, \mathbf{x}') = K \delta^d(\mathbf{x} - \mathbf{x}') (-\nabla^2 + \xi^{-2}).
$$
按照(3.50)式逆核函数满足：
$$
K \int d^d \mathbf{x}'' \delta^d(\mathbf{x}-\mathbf{x}'')(-\nabla^2+\xi^{-2}) K^{-1}(\mathbf{x}''-\mathbf{x}') = \delta^d(\mathbf{x}'-\mathbf{x}),
$$
上式表明微分方程
$$
K(-\nabla^2 + \xi^{-2}) K^{-1}(\mathbf{x}) = \delta^d(\mathbf{x}).
$$
与等式(3.14)对比得到$K^{-1}(\mathbf{x}) = \langle \phi(\mathbf{x}) \phi(\mathbf{0}) \rangle = -I_d(\mathbf{x})/K$.


## 3.6    Fluctuation corrections to the saddle point
我们现在检查鞍点解附近的涨落如何修正自由能以及宏观性质. 从(3.5)开始，包含了小涨落的配分函数为：
$$
\begin{align}
Z \approx \exp \left[ -V \left( \frac{t}{2}\overline{m}^2 + u\overline{m}^4 \right) \right] 
& \int \mathcal{D}\phi_l(\mathbf{x}) \exp \left\{ -\frac{K}{2} \int d^d\mathbf{x} \left[ (\nabla\phi_l)^2 + \frac{\phi^2_l}{\xi^2_l} \right] \right\} \\
& \cdot \int \mathcal{D}\phi_t(\mathbf{x}) \exp \left\{ -\frac{K}{2} \int d^d\mathbf{x} \left[ (\nabla\phi_t)^2 + \frac{\phi^2_t}{\xi^2_t} \right] \right\}.
\end{align}
\tag{3.56}
$$
每个高斯核函数可以通过傅立叶变换对角化：
$$
\tilde{\phi}(\mathbf{q}) = \int d^d\mathbf{x} \exp(-i \mathbf{q}\cdot\mathbf{x}) \phi(\mathbf{x}) / \sqrt{V},
$$
相应的本征值为$K(\mathbf{q})=K(q^2+\xi^{-2})$. $\mathbf{K}$的行列式是这些本征值的乘积，因此：
$$
\ln \det \mathbf{K} = \sum_{\mathbf{q}} \ln K(\mathbf{q}) = V \int \frac{d^d \mathbf{q}}{(2\pi)^d} \ln [K(q^2 + \xi^{-2})].
$$
(3.56)式给出的自由能为：
$$
\begin{aligned}
\beta f =& -\frac{\ln Z}{V} = \frac{t \overline{m}^2}{2} + u\overline{m}^4 + \frac{1}{2} \int \frac{d^d \mathbf{q}}{(2\pi)^d} \ln[K^2(q^2 + \xi_{\ell}^{-2})] \\
&+ \frac{n-1}{2} \int \frac{d^d \mathbf{q}}{(2\pi)^d} \ln[K(q^2 + \xi_{t}^{-2})].
\end{aligned}
$$
利用相关长度对约化温度的依赖性，热容的奇异部分可得出为：
$$
C_{\text{singular}} \propto -\frac{\partial^2(\beta f)}{\partial t^2} 
= 
\begin{cases}
0 + \frac{n}{2} \int \frac{d^d \mathbf{q}}{(2\pi)^d} \frac{1}{(Kq^2 + t)^2}  &\quad \text{for } t\gt0 \\
\frac{1}{8u} + 2 \int \frac{d^d \mathbf{q}}{(2\pi)^d} \frac{1}{(Kq^2 - 2t)^2} &\quad \text{for } t\lt0. \\
\end{cases}
\tag{3.59}
$$
因此修正项正比于：
$$
C_F = \frac{1}{K^2} \int \frac{d^d \mathbf{q}}{(2\pi)^d} \frac{1}{(q^2 + \xi^{-2})^2}.
$$
这个积分的维度为$(\text{length})^{4-d}$，因此在$d=4$时性质发生变化. 当$d \gt 4$时积分在大$\mathbf{q}$发散，并且被上截断$\Lambda \simeq 1/a$主导，其中$a$是晶格间距.  当$d \lt 4$时积分在两个极限上收敛. 它可以通过将$\mathbf{q}$缩放$\xi^{-1}$来使其无量纲化，因此正比于$\xi^{4-d}$. 因此
$$
C_F \simeq \frac{1}{K^2} 
\begin{cases}
a^{4-d} \quad \text{for } d \gt 4 \\
\xi^{4-d} \quad \text{for } d \lt 4.
\end{cases}
\tag{3.61}
$$
![[Pasted image 20240325202249.png]]
在维度$d \gt 4$时，热容的涨落修正在相变的两边给背景增加了一个常数项. 然而奇点的主要形式（$C$中的不连续性）没有改变. 对于$d \lt 4$，由$\xi \propto t^{-1/2}$导致在相变处有一个发散的修正项，这比原来的不连续性更重要. 事实上，修正项对应于指数$\alpha = (4-d)/2$. 然而这只是对鞍点结果的第一次修正. $C_F$的发散仅意味着鞍点结论在维度$d \le 4$中（低于所谓的上临界维度）不再可靠. 尽管我们通过查看热容的涨落修正获得了这个维度，但在检查任何其他量（例如磁化强度或磁化率）的奇异部分时，我们也会得出相同的结论. 由涨落引起的贡献总是会修改维度$d ≤ 4$中的主要奇异行为，从而修改临界指数. 


## 3.7    The Ginzburg criterion
因此，我们确立了涨落的重要性，并将其确定为鞍点近似无法正确描述观察到的指数的可能原因. 然而，如前所述，有一些材料（例如超导体）的实验结果非常适合这种近似预测的奇异形式. 我们能否量化为什么涨落在超导体中不如在其他相变中重要？

简单来说，$\xi_0$决定了相变温度附近奇异性的发散快慢，更大的$\xi_0$会导致更快的发散以及更窄的半宽. 实验上分辨率有限，每隔一段温度才可识别一个热容大小，如果分辨率比发散的半宽大很多，奇异性可能就会被跳过.

方程$(3.61)$表明涨落修正由于关联长度的发散而变得重要. 在鞍点近似中关联长度按照$\xi \approx \xi_0 |t|^{-1/2}$发散. 其中$t = (T_c - T) / T_c$是约化温度，$\xi_0 \approx \sqrt{K}$是微观长度尺度. 原则上$\xi_0$可以通过拟合散射线形状进行实验测量. 它必须大约等于在相变时经历排序的单元的大小. 在气液相变中$\xi_0$大约为$(v_c)^{1/3}$，其中$v_c$是临界原子体积. 在超流中$\xi_0$约为热波长$\lambda(T)$. 这两个估计值都是几个原子间距$(1-10 A)$的量级. 另一方面，超导体的基本单元是库珀对. 成对的电子由于库仑斥力被迫分开，导致相对较大的间距为$\xi_0 \approx 10^3 A$. 涨落的重要性可以通过比较方程(3.59)中的两项来衡量；鞍点不连续性$\Delta C_{SP} \propto 1/u$和修正项$C_F$. 由于$K \propto \xi^2_0$，修正项与$\xi^{-d} t^{-(4-d)/2}$成比例. 因此涨落很重要的前提是：
$$
\xi^{-d} t^{\frac{4-d}{2}} \gg \Delta C_{SP} \quad \Rightarrow \quad |t| \ll t_G \simeq \frac{1}{(\xi^d_0 \Delta C_{SP})^{\frac{2}{4-d}}}.
\tag{3.62}
$$
上述要求被称为*Ginzburg准则*. 自然地，当$d<4$时，足够接近临界点时满足不等式的条件. 然而，实验的分辨率可能不够好，无法比Ginzburg约化温度$t_G$更接近. 如果是这样，则在约化温度$t>t_G$时的明显奇点可能会表现出鞍点行为. 正是这种明显的不连续性出现在方程(3.62) ，并且可用于自洽地估计$t_G$. 
显然，$\Delta C_{SP}$和$\xi_0$都可以用无量纲单位来测量；$\xi_0$以原子大小$a$为单位，$\Delta C_{SP}$以$Nk_B$为单位. 对于大多数相变来说，后者具有统一的数量级，因此$d = 3$时$t_G ≈ \xi^{−6}$. 在$\xi_0$是几个原子间距的情况下，$t_G ≈ 10^{−1}−10^{−2}$的分辨率就足够了. 然而，在$\xi_0 ≈ 10^3 a$的超导体中，需要$t_G < 10^{−18}$的分辨率才能看到任何涨落效应. 这远远超出了现有设备的能力. 较新的陶瓷高温超导体的相干长度要小得多，为$\xi_0 ≈ 10 a$，并且它们确实表现出一些涨落效应.

再次值得强调的是，可以通过检查任何其他物理量来获得类似的标准. 涨落修正在$t \ll t_G(X) \simeq A(X)  \xi_0^{-2d/4-d}$ 的量$X$的测量中变得重要. 然而，对于不同的量，系数$A(X)$可能不同（相差一个或两个数量级）. 因此，原则上可能观察到一个量的鞍点行为，然而以相同分辨率测量的另一物理量时涨落很重要. 当然，在足够高的分辨率下，涨落总是变得很重要.

迄今为止从Landau-Ginzburg方法获得的结果总结如下：
* 对于维度$d$大于上临界维度$d_u = 4$的情况，鞍点近似有效，并且临界点处的奇异行为由指数$\alpha = 0, \beta = 1/2, \gamma = 1, \nu= 1/2, \eta = 0$描述.
* 如果$d$小于下临界维度（连续对称性$d_{\ell} = 2$，离散对称性$d_{\ell} = 1$）涨落就足以破坏有序相.
* 在中间维度$d_{\ell} ≤ d ≤ d_u$中，涨落足以改变鞍点结果，但不足以完全破坏序. 不幸的是，或者幸运的是，这是我们感兴趣的$d = 3$的情况.