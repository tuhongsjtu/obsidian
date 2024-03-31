## 4.1    The homogeneity assumption
在之前的章节中连续相变附近的奇异行为由一系列临界指数$\{ \alpha, \beta, \gamma, \delta, \nu, \eta, \cdots \}$表征. 由于涨落的重要性鞍点近似预测的指数被发现不够可靠. 由于不同的热力学量是相互关联的，这些指数也并不是互相独立的. 本章的目的就是发现它们之间的关系，并且找到能够描述临界点的最少数量的独立指数. 

![[Pasted image 20240330154254.png]]

非解析结构是一条$t \lt 0, h = 0$并且的终止于$t = h = 0$的共存线. 不同的指数描述热力学量$Q(t, h)$在此点附近的主导奇异行为. 正则系综的基本量是自由能，在鞍点近似中为：
$$
f(t, h) = \min \left[ \frac{t}{2}m^2 + um^4 - h.m \right]_m = 
\begin{cases}
-\frac{1}{16} \frac{t^2}{u} \quad &\text{for } h = 0, \ \ t \lt 0 \\
-\frac{3}{4^{4/3}} \frac{h^{4/3}}{u^{1/3}} \quad &\text{for } h \neq 0, \ \ t = 0.
\end{cases}
\tag{4.1}
$$
自由能中的奇异性实际上可以用一个关于$t$和$h$的齐次函数来描述，如：
$$
f(t, h) = |t|^2 g_f(h / |t|^{\Delta}).
\tag{4.2}
$$
> [!NOTE] Concept
> 一般的，如果对于任何标度因子$b$，
> $$
> f(b^{p_1}x_1, b^{p_2}x_2, \cdots) = b^{p_f} f(x_1, x_2, \cdots),
> $$
> 我们称函数$f(x_1, x_2, \cdots)$是齐次的.
> 通过正确选择$b$，可以删除其中一个参数，从而得到本节中使用的缩放形式.

函数$g_f$只依赖于$x \equiv h / |t|^{\Delta}$的组合. 其中$\Delta$被称为*能隙指数（gap exponent）*. 通过比较上面的两个等式可以很容易地得到$g_f$的渐进行为. 如果$\lim_{x \rightarrow 0} g_f(x) \sim 1/u$则恢复$h = 0$的极限，而为了获得适当的$h$的幂，我们必须设置$\lim_{x \rightarrow \infty} g_f(x) \sim x^{4/3}/u^{1/3}$. 后者表明$f \sim |t|^2 h^{4/3} / (u^{1/3} |t|^{4\Delta/3})$. 由于$f$在$t = 0$上不具有$t$的依赖性，因此能隙指数的值为：
$$
\Delta = \frac{3}{2}.
$$

同质性假设是指，在超出鞍点近似时，自由能（以及其他热力学量）的奇异形式保留均匀形式：
$$
f_{\text{sing}}(t, h) = |t|^{2-\alpha} g_f(h / |t|^{\Delta}).
$$
实际的指数$\alpha$和$\Delta$依赖于考虑的相变点. 关于$t$的依赖性根据$h=0$时热容的奇异性产生. 能量的奇异部分由以下产生（对于$t \gt 0$）：
$$
\begin{aligned}
E_{\text{sing}} & \sim \frac{\partial f}{\partial t} \sim (2 - \alpha) |t|^{1 - \alpha} g_f(h / |t|^{\Delta}) - \Delta h|t|^{1-\alpha-\Delta}g'_f(h/|t|^{\Delta}) \\
& \sim |t|^{1-\alpha} \left[ (2 - \alpha) (h / |t|^{\Delta}) - \frac{\Delta h}{|t|^{\Delta}} g'_f(h/|t|^{\Delta}) \right] \equiv |t|^{1-\alpha} g_E(h/|t|^{\Delta}).
\end{aligned}
$$
因此，一个齐次函数的导数是另一个齐次函数. 类似地，二阶导数采用以下形式（同样对于 $t>0$）：
$$
C_{\text{sing}} \sim -\frac{\partial^2 f}{\partial t^2} \sim |t|^{-\alpha} g_C(h/|t|^{\Delta}),
$$
重新产生了当$h \rightarrow 0$时的标度$C_{sing} \sim |t|^{-\alpha}$.

看起来我们可以自由地假设一个更一般的形式：
$$
C_{\pm}(t, h) = |t|^{-\alpha_{\pm}} g_\pm (h / |t|^{\Delta_{\pm}}),
\tag{4.7}
$$
对于$t$的正负我们有不同的函数和指数并且它们在$t=0$时匹配. 然而，因为除了$h=0$和$t \lt 0$的共存线自由能在任何地方都是解析的，所以这种可能被排除了. 考虑一个在$t=0$和有限$h$的点，按照假设，方程$C$在这点的附近是完美解析的，展开为泰勒级数可以得到：
$$
C(t \ll h^{\Delta}) = \mathcal{A}(h) + t\mathcal{B}(h) + \mathcal{O}(t^2).
\tag{4.8}
$$
进一步，相同的展开可以从$C_+$和$C_-$得到，但是(4.7)导出的展开为：
$$
C_{\pm} = |t|^{-|\alpha_{\pm}|} \left[ A_{\pm}\left( \frac{h}{|t|^{\Delta_{\pm}}} \right)^{p_{\pm}} + B_{\pm}\left( \frac{h}{|t|^{\Delta_{\pm}}} \right)^{q_{\pm}} + \cdots \right],
$$
其中$\{ p_{\pm}, q_{\pm} \}$是$g_{\pm}$对于大参数渐进展开式的主导幂，$\{A_{\pm}, B_{\pm}\}$是相应的prefactors. 将泰勒展开与(4.8)式做对比要求$p_{\pm} \Delta_{\pm} = -\alpha_{\pm}$以及$q_{\pm} \Delta_{\pm} = - (1 + \alpha_{\pm})$，得到：
$$
C_{\pm}(t \ll h^{\Delta}) = A_{\pm} h^{-\alpha_{\pm} / \Delta_{\pm}} + B_{\pm} h^{-(1 + \alpha_{\pm}) / \Delta_{\pm}} |t| + \cdots
\tag{4.10}
$$
$t = 0$的连续性要求$\alpha_+ / \Delta_+ = \alpha_- / \Delta_-$以及$( 1+\alpha_+) / \Delta_+ = (1 + \alpha_-) / \Delta_-$，这表明
$$
\begin{cases}
\alpha_+ = \alpha_- \equiv \alpha \\
\Delta_+ = \Delta_- \equiv \Delta.
\end{cases}
$$
尽管在假定的缩放形式中使用$|t|$，我们仍然可以通过适当选择参数来确保函数在$t = 0$时对于有限$h$的解析性，例如通过设置$B_− =−B_+$来匹配等式(4.10)和解析形式(4.8). 确定了这个结果后，我们以后在用$|t|$替换标度方程中的$t$时可能会有些粗心. 当然，这些论点适用于任何物理量$Q(t, h)$.

从(4.4)的自由能出发，我们可以计算其他感兴趣的物理量的奇异部分：
* *磁化强度*通过以下得到：
$$
m(t, h) \sim \frac{\partial f}{\partial h} \sim |t|^{2-\alpha-\Delta} g_m(h/|t|^{\Delta}).
$$
在极限$x \rightarrow 0$时$g_m(x)$是一个常数，并且
$$
m(t, h=0) \sim |t|^{2-\alpha-\Delta}, \quad \Rightarrow \quad \beta = 2 - \alpha - \Delta.
$$
另一方面，如果$x \rightarrow \infty$，$g_m(x) \sim x^p$，且
$$
m(t = 0, h) \sim |t|^{2 - \alpha - \Delta} \left( \frac{h}{|t|^{\Delta}} \right)^p.
$$
因为这个极限不依赖于$t$，我们有$p\Delta = 2 - \alpha - \Delta$. 因此
$$
m(t, h=0) \sim h^{(2 - \alpha - \Delta) / \Delta} \quad \Rightarrow \quad \delta = \Delta / (2-\alpha-\Delta) = \Delta / \beta.
$$
* 类似的，磁化率的计算方法为：
$$
\begin{aligned}
\chi(t, h) \sim \frac{\partial m}{\partial h} \sim |t|^{2-\alpha-2\Delta} g_{\chi}(h/|t|^{\Delta}) 
& \Rightarrow \chi(t, h=0) \sim |t|^{2-\alpha-2\Delta} \\
& \Rightarrow \gamma = 2\Delta - 2 + \alpha.
\end{aligned}
$$
因此，同质性假设的结果是：
(1) 所有临界量$Q(t,h)$的奇异部分都是齐次的，在转变上方和下方具有相同的指数.
(2) 由于通过热力学导数相互联系，所有这些量都会出现相同的能隙指数$\Delta$.
(3) 所有（bulk）临界指数只能从*两个*独立的指数获得，例如$\alpha$和$\Delta$.
(4) 由于上述原因，存在许多指数恒等式. 例如，等式 (4.13)、(4.15) 和 (4.16) 意味着：
$$
\alpha + 2\beta + \gamma = \alpha + 2(2-\alpha - \Delta) + (2\Delta - 2 + \alpha) = 2 \quad (\text{Rushbrooke's identity}),
$$
$$
\delta - 1 = \frac{\Delta}{2-\alpha-\Delta} - 1 = \frac{2\Delta - 2 + \alpha}{2 - \alpha - \Delta} = \frac{\gamma}{\beta} \quad (\text{Widom's identity}).
$$
这些恒等式可以根据下面临界指数表进行检查. 前三行基于$d = 3$时的多项理论估计；最后一行来自$d = 2$的精确解. 指数恒等式与这些值以及所有可靠的实验数据完全一致.

![[Pasted image 20240330154153.png]]

## 4.2    Divergence of the correlation length
同质性假设与自由能和从中导出的物理量有关. 但并未讨论关联函数的行为. 临界点的一个重要属性是关联长度的发散，它导致响应函数发散，并且可以从发散响应函数中推导出来. 为了获得涉及关联长度发散指数$\nu$的恒等式，我们用以下两个条件替换自由能的同质性假设：
(1) 关联长度$\xi$是一个齐次函数，
$$
\xi(t, h) \sim |t|^{-\nu} g(h / |t|^{\Delta}).
$$
对于$t = 0$，$\xi$按照$h^{-\nu_h}$发散，其中$\nu_h = \nu / \Delta$.
(2) 靠近相变时，关联长度$\xi$是系统最重要的长度并且*仅*对热力学量的奇异贡献负责.
![[Pasted image 20240330190735.png]]
第二个条件决定了自由能的奇异部分. 因为$\ln Z(t, h)$是*广延量*并且*无量纲*，它必须有以下形式：
$$
\ln Z = \left( \frac{L}{\xi} \right)^d \times g_s + \cdots + \left( \frac{L}{a} \right)^d \times g_a,
\tag{4.19}
$$
其中$g_s$和$g_a$是关于无量纲参数的非奇异函数. （$a$是一个合适的微观长度.）自由能主要的奇异部分来自于第一项，表现为：
$$
f_{\text{sing}}(t, h) \sim \frac{\ln Z}{L^d} \sim \xi^{-d} \sim |t|^{d\nu} g_f(h/|t|^{\Delta}).
$$
上述结果的一个解释是将系统划分为关联长度大小的单元，每一个单元被认为是一个独立的随机变量，给临界自由能贡献一个常数因子. 单元的数量按照$(L / \xi)^d$增长，因此导出了(4.19).

上述假设的结果是：
(1) $f_{\text{sing}}(t, h)$的同质性自然而然地显现出来.
(2) 我们得到了额外的指数关系
$$
2 - \alpha = d \nu \quad (\text{Joshephson's identity}).
$$
从广义同质性假设获得的恒等式涉及空间维度$d$，被称为*超尺度关系*（*hyperscaling relations*）. $\alpha$和$\nu$之间的关系与上表中的指数一致. 然而，这与$d \gt 4$时的鞍点值$\alpha = 0$以及$\nu = 1/2$不符合. 因此，任何临界行为理论都必须解释这种关系在低维情况下的有效性，以及$d>4$时的失效. 

## 4.3    Critical correlation functions and self-similarity
迄今为止尚未得到解释的一个指数是$\eta$，它描述了关联函数在临界点的衰减. 恰好在临界点，相关长度是无限的，并且没有其他长度尺度（样本大小除外）来切断关联函数的衰减. 因此，所有关联都会随着分离的幂而衰减. 
正如前一章所讨论的，磁化强度相关性的下降为：
$$
G_{m, m}^c(\mathbf{x}) \equiv \langle m(\mathbf{x}) m(\mathbf{0}) \rangle - \langle m \rangle^2 \sim 1 / |\mathbf{x}|^{d - 2 + \eta}.
$$
相似的，我们也可以定义一个指数$\eta'$来描述能量-能量关联函数的衰减：
$$
G_{E, E}^c(\mathbf{x}) = \langle \mathcal{H}(\mathbf{x}) \mathcal{H}(\mathbf{0}) \rangle - \langle \mathcal{H} \rangle^2 \sim 1/|\mathbf{x}|^{d-2+\eta'}.
$$
远离临界点，幂律在距离$|\mathbf{x}| \gg \xi$处被截断. 由于响应函数可以通过积分连接关联函数得到，因此还有额外的指数恒等式，例如$(\text{Fisher's identity})$：
$$
\chi \sim \int d^d \mathbf{x} G_{mm}^c(\mathbf{x}) \sim \int^{\xi} \frac{d^d x}{|x|^{d-2+\eta}} \sim \xi^{2-\eta} \sim |t|^{-\nu(2-\eta)} \quad \Rightarrow \quad \gamma = (2 - \eta)\nu.
$$
相似的，对于热容：
$$
C \sim \int d^d \mathbf{x} G_{EE}^c(\mathbf{x}) \sim \int^{\xi} \frac{d^d x}{|x|^{d-2+\eta'}} \sim \xi^{2-\eta'} \sim |t|^{-\nu(2-\eta')} \quad \Rightarrow \quad \alpha = (2 - \eta')\nu.
$$
和以前一样，两个独立的指数足以描述所有奇异的关键行为. 

这些标度思想的一个重要结果是临界系统具有额外的*膨胀对称性*(*dilation symmetry*). 在标度变化下，临界关联函数表现为：
$$
G_{\text{critical}}(\lambda \mathbf{x}) = \lambda^p G_{\text{critical}}(\mathbf{x}).
$$
这表明了一种*标度不变性*或者*自相似性*：如果临界系统的快照被放大了一个因子$\lambda$，除了对比度的变化（乘$\lambda^p$），生成的快照在统计上与原始快照相似. 这种统计上的自相似性是*分形几何*的标志. 正如Mandelbrot所讨论的，许多自然存在的形式（云、海岸线、河流盆地等）都表现出这种行.  Landau-Ginzburg 概率是基于*局部*对称性（例如旋转不变性）构建的. 如果我们可以将dilation symmetry的要求添加到约束列表中，则所得概率确实可以描述临界点. 不幸的是，不可能直接看出这样的要求如何限制有效哈密顿量. 一个值得注意的例外是$d = 2$，其中膨胀对称性意味着共形不变性，并且可以通过构建共形不变理论来获得大量信息. 相反，我们将规定一种不太直接的途径来跟踪dilation operation对有效能量的影响：*重整化群*过程.

## 4.4    The renormalization group (conceptual)
标度理论在正确预测各种指数恒等式方面的成功有力地支持了这样的假设：接近临界点时相关长度$\xi$是唯一重要的长度标度，并且微观长度标度是无关紧要的. 临界行为主要由在尺度$\xi$上自相似的涨落支配. 当然，自相似性只是统计性的，因为磁化构型是用权重$W[\vec{m}(\mathbf{x})] \propto \exp \{ − \beta \mathcal{H}[\vec{m}(\mathbf{x})] \}$生成的. Kadanoff建议利用涨落的自相似性，逐步消除长度尺度$x \ll \xi$上的相关自由度，直到只剩下尺度$\xi$上相对简单、不相关的自由度. 这是通过称为重正化群 (RG) 的过程来实现的，其概念基础是本节中概述的三个步骤. 

(1) ***粗粒化(Coarse grain)：*** 对于系统中$\vec{m}(\mathbf{x})$的允许变化，存在隐含的短距离长度截止标度$a$. 这是自旋模型中的晶格常数，或者Landau-Ginzburg哈密顿量中潜在的粗粒化尺度. 在系统的数字图片中，$a$对应于像素大小. RG的第一步是通过将该最小比例更改为$ba(b \gt 1)$来降低分辨率. *粗粒化的*磁化强度为：
$$
m_i = \frac{1}{b^d} \int_{\text{Cell centered at }\mathbf{x}} d^d \mathbf{x}' m_i(\mathbf{x}').
$$
(2) ***重新标度(Rescale)：*** 由于分辨率的变化，粗粒化的“图片”比原始图片更有颗粒感. $a$的原始分辨率可以通过将所有长度尺度减少$b$倍来恢复，即通过设置：
$$
\mathbf{x}_{\text{new}} = \frac{\mathbf{x}_{\text{old}}}{b}.
$$
(3) ***重整化(Renormalize)：*** 重新标度的磁化强度分布中的涨落变化通常与原始不同，即图片之间的对比度存在差异. 这可以通过定义*重正化*磁化强度来引入对比度的变化$\zeta$来弥补：
$$
\vec{m}_{\text{new}}(\mathbf{x}_{\text{new}}) = \frac{1}{\zeta b^d} \int_{\text{Cell centered at }b\mathbf{x}_{\text{new}}} d^d \mathbf{x}' \vec{m}(\mathbf{x}').
\tag{4.29}
$$
通过这些步骤，每个构型$\vec{m}_{\text{old}}(\mathbf{x})$产生一个新的重整化构型$\vec{m}_{\text{new}}(\mathbf{x})$. 方程(4.29)可以认为是从一组随机变量到另一个的映射，可以用于构造概率分布，或者权重$W_b[\vec{m}_{\text{new}(\mathbf{x})}] = \exp\{  -\beta \mathcal{H}_b[\vec{m}_{\text{new}}(\mathbf{x})]  \}$. Kadanoff的见解是，由于长度尺度小于$\xi$，重整化构型在统计上与原始构型相似，因此它们可能是按照也接近原始构型的哈密顿量$\beta \mathcal{H}_b$分布. 特别的，原始哈密顿量通过调节两个参数$t$和$h$到$0$来达到临界：在这一点原始构型与重新标度的系统是统计相似的. 因此临界哈密顿量在重新标度和重整化下应该是不变的. 在最初的问题中，我们远离了有限$t$和$h$的临界性. Kadanoff假设相应的重整化哈密顿量类似地由非零$t_{\text{new}}$和/或$h_{\text{new}}$描述.

接近临界的原始哈密顿量和重正化哈密顿量的接近度由两个参数$t$和$h$描述的假设大大简化了分析. RG变换对构型概率的影响现在通过两个参数映射$t_{\text{new}} \equiv t_b(t_{\text{old}, h_{\text{old}}})$和$h_{\text{new}} \equiv h_b(t_{\text{old}}, h_{\text{old}})$来描述. 下一步要注意的是，由于变换仅涉及最短长度尺度的变化，因此它不会导致任何奇点. 重整化参数必须是原始参数的解析函数，因此可扩展为
***
如何理解“变换仅涉及最短长度尺度的变化，因此它不会导致任何奇点”
***
$$
\begin{cases}
t_b(t, h) = A(b)t + B(b)h + \cdots \\
h_b(t, h) = C(b)t + D(b)h + \cdots
\end{cases}
$$
注意在上面的泰勒展开中没有常数项. 这表明如果$\beta \mathcal{H}$在临界点$(t = h = 0)$，$\beta \mathcal{H}_b$也在临界点，并且$(t_{\text{new}} = h_{\text{new}} = 0)$. 进一步，由于旋转对称性，在组合变换$(m(x) \rightarrow -m(x), h \rightarrow -h, t \rightarrow t)$下，构型的权重不变. 由于RG保留了这种对称性，因此上述表达式中的系数$B$和$C$必须为零，这导致了进一步的简化：
$$
\begin{cases}
t_b(t, h) = A(b)t + \cdots \\
h_b(t, h) = D(b)h + \cdots
\end{cases}
$$
剩余的系数$A(b)$和$D(b)$取决于（任意）缩放因子$b$，并且对于$b=1$有$A(1) = D(1) = 1$. 由于上述变换可以按顺序进行，并且$b_1$和$b_2$重新缩放的净效果是$b_1b_2$的尺度变化，因此RG过程有时被称为*半群*。