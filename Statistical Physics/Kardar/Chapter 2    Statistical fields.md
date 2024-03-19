- [[#2.1 Introduction|2.1 Introduction]]
- [[#2.2 The Landau-Ginzburg Hamiltonian|2.2 The Landau-Ginzburg Hamiltonian]]
- [[#2.3 Saddle point approximation, and mean-field theory|2.3 Saddle point approximation, and mean-field theory]]

## 2.1 Introduction			

上一章中我们说到，临界点的热力学函数可以通过一系列临界指数$\{\alpha，\beta，\gamma，\cdots \}$进行表征. 实验上也表明了这些指数是普适的，即与所研究的材料无关，并且在某种程度上与相变的性质无关，比如$\text{CO}_2$的冷凝过程中共存边界的消失与蛋白质溶液相分离具有相同的奇异行为. 这种普适性需要解释. 
我们还注意到，响应函数的发散以及通过散射实验对涨落的直接观察表明，涨落在临界点附近具有长波关联$\xi \gg a$. 这种关联的涨落涉及许多粒子，并且本着弹性理论的启发，粗粒化的方法可能适合它们的描述. 这里我们将构建这样一个*统计场论*.

我们首先关注磁性系统，它们的对称性更加透明. 考虑像铁这样的材料，实验上观察到在居里温度$T_c$以下其具有铁磁性. 磁性的微观起源是量子力学，涉及巡游电子、自旋和相互作用等元素，可以用一个微观哈密顿量$\mathcal{H}_{\text{mic}}$描述. 原则上，系统的所有热力学性质都可以从配分函数中得到，这样的配分函数可以通过对所有自由度求和而得到
$$
Z(T) = \mathrm{tr} \left[ e^{-\beta \mathcal{H}_{\text{mic}}} \right]，\quad \text{with} \quad \beta = \frac{1}{k_B T}.
$$
实际上这个公式并不常用，因为微观哈密顿量和其自由度非常复杂，很难进行计算.

为了找出可能产生铁磁性的元素微观理论是必要的，然而考虑到存在磁行为，这样的理论不一定适用于描述热涨落导致的磁性消失. 为了解决后者，相互作用电子的量子统计理论是一个过于复杂的起点. 相反我们观察到**靠近居里点的重要自由度是自旋的长波长集体激发**（很像在低温下主导固体热容的长波长声子）. 因此，关注这些最终导致相变的波动的统计特性更有意义.
为此，我们将焦点从微观尺度转移到比晶格间距大得多但比系统尺寸小得多的中间介观尺度. 以类似于图1.1中描述的粗粒化过程的方式，我们定义磁化场$\vec{m}(\mathbf{x})$ ，它表示点$\mathbf{x}$附近的自旋的平均值. 需要强调的是，虽然$\mathbf{x}$被视为连续变量，但函数$\vec{m}(\mathbf{x})$在晶格间距量级的距离上不表现出任何变化，即其傅里叶变换仅涉及小于某个上截断$\Lambda \sim 1/a$的波矢.
![[Pasted image 20240312151849.png|650]]
从原始自由度到场$\vec{m}(\mathbf{x})$的变换是变量的变化，这种映射是不可逆的，因为在平均的过程中丧失了很多微观细节（每一个场的构型对应着许多微观构型，将这些微观构型的权重加起来即可）.  同样原则上可以通过变换由玻尔兹曼权重$e^{-\beta \mathcal{H}_{\text{mic}}}$产生的原始微观概率来得到场$\vec{m}(\mathbf{x})$的构型的相应概率.  新的配分函数可以写成
$$
Z(T) = \mathrm{tr} \left[ e^{-\beta \mathcal{H}_{\text{mic}}} \right] \equiv \int \mathcal{D} \vec{m}(\mathbf{x}) \mathcal{W} \left[ \vec{m}(\mathbf{x}) \right].
\tag{2.2}
$$
其中$\mathcal{D}\vec{m}(\mathbf{x})$表示对场所有允许的构型做积分，而每种构型的权重$\mathcal{W}(\vec{m}(\mathbf{x}))$是我们希望得到的. 
得到$\mathcal{W}(\vec{m}(\mathbf{x}))$的精确形式并不比解决整个问题容易，但实际上可以用一些唯象参数来描述它（这类似于用几个弹性模量描述固体变形的能量成本）. 在相变的背景下，朗道首先应用这种方法来描述氦中超流的出现. 实际上这种方法可以普遍的应用于经历相变的不同类型的系统，其中$\vec{m}(\mathbf{x})$描述相应的序参量场. 我们将这个问题一般化，考虑一个$d$维空间中的$n$分量场
$$
\mathbf{x} \equiv (x_1，x_2，\cdots，x_d) \in \Re^d \quad (\text{space})，\quad \vec{m} \equiv (m_1，m_2，\cdots，m_n) \in \Re^n \quad (\text{order parameter}).
$$
这个一般性的框架涵盖的具体例子包括：
$n=1$描述了气液相变、二元混合物以及单轴磁体；
$n=2$应用于超流、超导和平面磁铁；
$n = 3$对应与经典磁铁.
尽管大多数物理现象发生在三维空间（$d=3$），在平面（$d=2$）和线（$d=1$）上. 相对论场论由类似的结构描述，但是$d=4$.


## 2.2 The Landau-Ginzburg Hamiltonian

使用2.2式中的粗粒化权重，我们可以定义一个有效哈密顿量
$$
\beta \mathcal{H}[\vec{m}(\mathbf{x})] \equiv - \ln \mathcal{W}[\vec{m}(\mathbf{x})]，$$
它通过玻尔兹曼因子给出了场构型的概率. 类比上一章中的弹性理论，我们按照以下原则构造$\beta \mathcal{H}[\vec{m}(\mathbf{x})]$：

**局部性和均匀性：** 如果一个系统包含不相连的部分，整体的概率通过每一部分概率的乘积得到. (2.3)式中的哈密顿量分解为每个部分的贡献之和，转变为在连续表示下的积分
$$
\beta \mathcal{H} = \int d^d \mathbf{x} \Phi[\vec{m}(\mathbf{x})，\mathbf{x}].
$$
这里$\Phi$是能量密度，原则上它在不同位置可以具有不同的函数形式. 对于空间中均匀的材料，不同的位置$\mathbf{x}$是等价的，因此可以将$\Phi$中对于$\mathbf{x}$的依赖移除. 但当系统处于外部势或者有额外的杂质时这是不成立的. 我们对更复杂的系统感兴趣，在这些系统中，由于相互作用，系统的不同部分之间存在一些耦合，为此我们在上式中包含了场的梯度
$$
\beta \mathcal{H} = \int d^d \mathbf{x} \Phi[\vec{m}(\mathbf{x})，\nabla \vec{m}，\nabla^2 \vec{m}，\cdots].
$$
一般的非局部相互作用可以通过包括许多导数来描述，当仅包含少数导数即可获得良好的描述时，“局部”是有用的. 这是短程相互作用的情况（甚至包括气液混合物中的范德瓦尔斯相互作用），但对于长程相互作用（如库伦）失败.

**解析性和多项式展开：** 接下来将$\Phi$的函数形式写为$\vec{m}(\mathbf{x})$的幂及其梯度的展开式. 为了证明这种展开的合理性，让我们再次检查独立自由度集合（例如自旋）的简单示例. 微观层面的概率分布可能比较复杂，例如自旋可以被限制为固定大小，或者被量化为特定值. 在介观尺度上，场$\vec{m}(\mathbf{x})$是通过对许多这样的自旋进行平均而获得的. 平均过程通常会简化概率分布. 在大多数情况下，中心极限定理意味着总和的概率分布接近高斯形式.  在构建统计场论时，我们实际上正在寻找中心极限定理的概括，以描述相互作用的自由度.  关键在于，从微观尺度到介观尺度，与微观自由度相关的非解析性被洗掉，粗粒场的概率分布是通过$\vec{m}$次方的解析展开得到的.  当然，宏观尺度上存在与相变相关的非解析性.  然而，这种奇点涉及无穷大（宏观数）的自由度.  通过关注介观尺度，我们从而避免了短尺度和长尺度上可能出现的奇点！
![[Pasted image 20240312153856.png|550]]

**对称性：** 一个在平均过程中存活的元素是潜在的微观对称性.  这种对称性限制了有效哈密顿量的可能形式和展开. 比如在不存在外加磁场时，所有磁化方向都是等价的，因此$\mathcal{H}[R_n \vec{m}(\mathbf{x})] = \mathcal{H}[\vec{m}(\mathbf{x})]$，其中$R_n$是$n$维序参量空间的一个旋转.  $\vec{m}$的线性项与这个对称性是不符合的，因此展开的第一项正比于$m^2(\mathbf{x})$
$$
m^2(\mathbf{x}) \equiv \vec{m}(\mathbf{x}) \cdot \vec{m}(\mathbf{x}) \equiv \sum_i^n m_i(\mathbf{x}) m_i(\mathbf{x})，$$
其中$\{m_i\}$是矢量场的分量.  更高阶项由$4$次方$m^4(\mathbf{x})$、$6$次方$m^6(\mathbf{x})$给出.
在构造涉及矢量场梯度的项时，我们应该记住系统的空间对称性.  在*各向同性*系统中，空间中的所有方向都是等效的，我们应该使用在空间旋转下不变的导数组合.  最简单的项为：
$$
(\nabla \vec{m})^2 \equiv \sum_{i=1}^{n} \sum_{\alpha = 1}^d \partial_{\alpha} m_i \partial_{\alpha} m_i，$$
$\partial_{\alpha}$代表沿着空间的$\alpha$方向做偏导.  如果不同方向是不等价的，更多的项会包括进来.  比如在三角晶格上的二维磁铁，$\partial_1 m_i \partial_1 m_i$和$\partial_2 m_i \partial_2 m_i$的系数可以是不同的.  然而，通过适当地重新缩放坐标，梯度项可以再次更改为(2.7)的形式.  各向同性系统中的四阶梯度项是：
$$
(\nabla^2 \vec{m})^2 \equiv \sum_{i=1}^{n} \sum_{\alpha = 1}^d \sum_{\beta = 1}^d (\partial_{\alpha} \partial_{\alpha} m_i)(\partial_{\beta} \partial_{\beta} m_i)，$$
并且一个可能的四次项为：
$$
m^2 (\nabla^2 \vec{m})^2 \equiv \sum_{i=1}^{n} \sum_{j = 1}^n \sum_{\alpha = 1}^d m_i m_i \partial_{\alpha} m_j \partial_{\alpha} m_j.
$$
各向异性再次导致高阶项，通常无法通过简单的重新缩放来消除.  

我们将很快证明，为了描述磁系统，事实上大多数转变，只包含几项就足够了，从而产生所谓的*Landau-Ginzburg*哈密顿量：
$$
\beta \mathcal{H} = \beta F_0 + \int d^d \mathbf{x} \left[ \frac{t}{2} m^2(\mathbf{x}) + u m^4(\mathbf{x}) + \frac{K}{2} (\nabla m)^2 + \cdots - \vec{h} \cdot \vec{m}(\mathbf{x}) \right].
$$
在短尺度上对磁性和非磁性自由度的积分也会生成一个总体常数$F_0$.  这种对总自由能的贡献是解析的（如前所述），并且大部分会被忽略.  方程(2.8)还包括磁功$\vec{B}·\vec{m}$对哈密顿量的贡献，其中$\vec{h} \equiv \beta \vec{B}$，$\vec{B}$是磁场.  磁场还可能产生高阶项，例如$m^2 \vec{m}· \vec{h}$，与上面的项相比它们更次要一些.

**稳定性：** 由于LG哈密顿量源于一个良定义的物理问题，粗粒化的玻尔兹曼权重不能导致任何非物理的场的构型.  特别的，对于无限大的$\vec{m}$，概率不能是发散的.  这个条件表明$\vec{m}$的高阶幂的系数必须是正的.  对涉及梯度的项的符号有相关的限制，以避免振荡不稳定.  

Landau-Ginzburg哈密顿量依赖于一系列的唯象参数$\{ t，u，K，\cdots \}$，这些参数是微观相互作用以及外部参数如温度、压强的非普适函数.  必须充分理解这一点，这可能是造成混乱的根源.  虽然场的特定构型的概率由玻尔兹曼权重$\exp\{ -\beta \mathcal{H}[\vec{m}(\mathbf{x})] \}$给出，但这并不意味着指数中的所有项都与$(k_BT)^{-1}$成比例.  这种依赖性仅适用于真正的微观哈密顿量.  更准确地说，Landau-Ginzburg哈密顿量是通过对微观自由度进行积分（粗粒化）而获得的有效自由能，同时将其平均值限制为$\vec{m}(\mathbf{x})$.  正是由于执行这样的第一性原理程序的困难，我们才仅在对称性的基础上假设所产生的有效自由能的形式.  付出的代价是唯象参数对原始微观参数以及温度等外部约束具有未知的函数依赖性（因为我们必须考虑粗粒度过程中丢失的短程涨落的熵）.  对这些函数形式的约束来自对称性、解析性和稳定性，正如在构造$\Phi[\vec{m}]$的函数形式的上下文中所讨论的那样.  值得注意的是，这些介观系数将是外部参数的解析函数，例如可表示为温度$T$的幂级数.  


## 2.3 Saddle point approximation, and mean-field theory

通过仅关注粗粒化场，我们大大简化了原始问题.  现在应该从配分函数中获得各种热力学函数以及奇异行为
$$
Z = \int \mathcal{D} \vec{m}(\mathbf{x}) \exp \{ -\beta \mathcal{H}[\vec{m}(\mathbf{x})] \}，\tag{2.9}
$$
对应于之前定义的Landau-Ginzburg哈密顿量.  在实际，泛函积分是作为离散积分的极限而获得的：连续坐标$\mathbf{x} ≡ (x_1，x_2，\cdots x_d)$首先被离散化为点$\mathbf{i} ≡ (i_1，i_2，\cdots，i_d)$的格，格距为$a$；将各种导数替换为适当的差分，得到泛函积分为：
$$
\int \mathcal{D} \vec{m}(\mathbf{x}) \mathcal{F}\left[\vec{m}(\mathbf{x})，\frac{\partial \vec{m}}{\partial x_\alpha}，\cdots\right] \equiv \lim _{\mathcal{N} \rightarrow \infty} \prod_{i=1}^{\mathcal{N}} \mathrm{d} \vec{m}_i \mathcal{F}\left[\vec{m}_i，\frac{\vec{m}_{i_\alpha+1}-\vec{m}_{i_\alpha}}{a}，\cdots\right] .
$$
事实上，关于泛函积分的存在性有许多数学问题.  这些问题主要与短距离内的自由度过多有关，从而导致函数表现相当糟糕.  这些问题不需要我们关心因为我们知道这些潜在的问题有一个良定义的晶格间距，这限制和控制了短距离行为.

即使经过所有这些简化，计算式(2.9)中的 Landau-Ginzburg 配分函数仍然不容易.  下面我们进行鞍点近似，其中方程中的积分被被积函数的最大值替代，对应于场$\vec{m}(\mathbf{x})$的最可能构型.  磁体中相互作用的自然趋势是保持磁化矢量平行，因此我们期望方程中的参数$K$为正.  $\vec{m}(\mathbf{x})$的大小或方向的任何变化都会导致方程 (2.8) 中$K(\nabla \vec{m})^2$项的“能量损失”.  因此，场在其最可能的配置中是均匀的，并且将积分限制到该子空间我们得到：
$$
Z \approx Z_{\text{sp}} = e^{-\beta F_0} \int d \vec{m} \exp \left[-V \left( \frac{t}{2} m^2 + um^4 + \cdots - \vec{h} \cdot \vec{m} \right) \right]，\tag{2.10}
$$
其中$V$是系统体积.  在极限$V \rightarrow \infty$时积分被鞍点$\vec{m}$主导，相应的鞍点自由能为：
$$
\beta F_{\text{sp}} = - \ln Z_{\text{sp}} \approx \beta F_0 + V \min \{ \Psi(\vec{m}) \}_{\vec{m}}，\tag{2.11}
$$
其中
$$
\Psi(\vec{m}) \equiv \frac{t}{2} \vec{m}^2 + u(\vec{m}^2)^2 + \cdots - \vec{h} \cdot \vec{m}.
$$
最有可能的磁化强度将与外部磁场对齐，即$\vec{m}(\mathbf{x}) = \overline{m} \hat{h}$ .  为了得到具体的数值我们要得到上式的最值.
$$
\Psi'(\overline{m}) = t \overline{m} + 4u \overline{m}^3 + \cdots - h = 0.
\tag{2.13}
$$
令人惊讶的是这个简单的方程捕捉了相变的定性行为.  

虽然函数$\Psi(m)$是解析函数并且没有奇点，但鞍点自由能为方程式(2.11)很可能是非解析的.  这是因为最小化运算不是一个解析过程，并且会引入奇点，正如我们将很快演示的那样.  $V \rightarrow \infty$的热力学极限证明了方程(2.10)鞍点近似的合理性.  对于有限的$V$，积分是完美解析的. 在临界点附近，磁化强度很小，因此在$\Psi(\vec{m})$的展开中仅保留最低幂次是合理的. （我们稍后可以自洽地检查展开式中省略的项确实是小的修正）$\Psi(m)$的行为很大程度上取决于参数$t$的符号.
(1) 对于$t \gt 0$，四次项对于稳定性不是必需的，可以忽略.  (2.13)式的解是$\overline{m} = h/t$，描述了顺磁行为.  最可能的磁化是沿着磁场方向，并且在$\vec{h} \rightarrow 0$时消失.  磁化率为$\chi = 1/t$，随着$t \rightarrow 0$发散.  
![[Pasted image 20240311223154.png|660]]
(2) 对于$t \lt 0$，需要$u$为正值来保证稳定性. 函数$\Psi(m)$现在有两个局部最小值，全局最小值处自旋与磁场对其.  当$\vec{h} \rightarrow 0$时全局最小值向非零值移动，表明自发磁化.  即使在$\vec{h} = 0$时也是如此，如铁磁体.  $h = 0$时$\vec{m}$的方向由系统的历史决定，并且可以通过外部场$\vec{h}$重新调整. 
![[Pasted image 20240311224807.png|650]]
最可能磁化强度$\overline{m}(h)$的结果曲线与图1.4中的曲线非常相似.  因此，Landau-Ginzburg 配分函数的鞍点评估会导致$t>0$时产生顺磁行为，$t<0$时产生铁磁行为，相变线终止于点$t = h = 0$.
![[Pasted image 20240311224843.png|800]]

参数$(t，u，K，\cdots)$是温度的解析方程，可以在临界点$T = T_c$附近进行展开.  
$$
\left\{\begin{array}{l}
t(T，\cdots)=a_0+a_1\left(T-T_c\right)+\mathcal{O}\left(T-T_c\right)^2，\\
u(T，\cdots)=u+u_1\left(T-T_c\right)+\mathcal{O}\left(T-T_c\right)^2，\\
K(T，\cdots)=K+K_1\left(T-T_c\right)+\mathcal{O}\left(T-T_c\right)^2 .
\end{array}\right.
$$
展开系数可以看作唯象参数，可以通过与实验对比确定.  特别的，为了让图1.4和图2.3匹配，我们要求$t$是一个关于温度的单调函数并且在$T_c$时为$0$，这就要求$a_0=0$以及$a_1 = a \gt 0$.  在相变点附近的铁磁相的稳定性要求$u$和$K$是正的.  将磁体的实验相图与从鞍点获得的相图相匹配的最小条件集是
$$
t = a(T - T_c)^2 + \mathcal{O}(T-T_c)^2，\quad \text{with} \quad (a，u，K) \gt 0.
\tag{2.15}
$$

当然可以在扩展中设置附加项，例如$a$或$u$为零，并通过适当选择高阶项来保持相图和稳定性.  然而，这样的选择不是通用的，没有理由施加比实验绝对要求更多的限制.  
使用式(2.15)我们可以我们可以量化式(2.11)-(2.13)中自由能的鞍点评估所预测的奇异行为.

下面计算鞍点近似给出的临界指数.
* **磁化：** 在零场时(2.13)简化为$\partial \Psi / \partial m = t \overline{m} + 4 u \overline{m}^3 = \overline{m}(t + 4 u \overline{m}^3) = 0$，我们得到
$$
\overline{m}(h=0)= \begin{cases}0 & \text { for } t>0，\\ \sqrt{\frac{-t}{4 u}}=\sqrt{\frac{a}{4 u}}\left(T_c-T\right)^{1 / 2} & \text { for } t<0 .\end{cases}
\tag{2.16}
$$
![[Pasted image 20240312134209.png|700]]
对于$t<0$，非磁化解$\overline{m} = 0$是$\Psi(m)$的最大值，并且存在自发磁化，普适指数$\beta = 1/2$.  总振幅是非普适的并且取决于材料.  
通过(2.13)，当$t=0$时可以计算出
$$
\overline{m}(t = 0) = \left( \frac{h}{4u} \right)^{1/3}，$$
可以得到$\delta = 3$.  
* **磁化率：** 其大小$t \overline{m} + 4u \overline{m}^3 = h$的解给. 幅度的变化由*纵向磁化率*$\chi_l$控制，其倒数很容易获得为：
$$
\chi_{\ell}^{-1}=\left.\frac{\partial h}{\partial \overline{m}}\right|_{h=0}=t+12 u \overline{m}^2= \begin{cases}t & \text { for } t>0，\text { and } h=0，\\ -2 t & \text { for } t<0，\text { and } h=0 .\end{cases}
\tag{2.18}
$$
从两侧接近相变点时，零场磁化率按照$\chi_{\pm} \sim A_{\pm} |t|^{-\gamma_{\pm}}$发散且$\gamma_{+} = \gamma_{-} = 1$.  尽管振幅$A_{\pm}$是依赖于材料的，式$(2.18)$预测它们的比值$A_{+} / A_{-} = 2$是普适的.  （我们很快就会遇到横向磁化率$\chi_t$，它描述了磁化强度垂直于它的磁场的变化的响应. 当$h = 0$时，磁化相中的$\chi_t$始终为无穷）
![[Pasted image 20240312141129.png|650]]
* **热容：** $h=0$时的自由能为
$$
\beta F=\beta F_0+V \Psi(\bar{m})=\beta F_0+V \begin{cases}0 & \text { for } t>0，\\ -\frac{t^2}{16 u} & \text { for } t<0 .\end{cases}
\tag{2.19}
$$
由于$t = a(T-T_c) + \cdots$，只保留$(T-T_c)$的领头阶我们可以得到$\partial/\partial T \sim a \partial / \partial t$. 因此我们可以得到在零场时热容的行为为：
$$
C(h=0)=-T \frac{\partial^2 F}{\partial T^2} \approx-T_c a^2 \frac{\partial^2}{\partial t^2}\left(k_{\mathrm{B}} T_c \beta F\right)=C_0+V k_{\mathrm{B}} a^2 T_c^2 \times \begin{cases}0 & \text { for } t>0，\\ \frac{1}{8 u} & \text { for } t<0 .\end{cases}
$$
鞍点近似预测了一个不连续性而不是发散. 如果我们坚持使用幂律$t^{- \alpha}$来描述这个奇异性，我们只能选择$\alpha = 0$.
![[Pasted image 20240312141733.png|650]]


## 2.4    Continuous symmetry breaking and Goldstone modes

对于零外场的情况，虽然微观哈密顿量具有完全的旋转对称性，但是低温相却没有. 当 $n$ 空间中一个特定方向被选作净磁化 $\vec{M}$ 的方向时，*自发对称性破缺*就发生了，同时对应的*长程序*也建立起来，其中系统的大多数自旋沿 $\vec{M}$ 方向. 原始的对称性在全局范围内仍然存在，在某种意义上，如果所有的局域自旋同时旋转（即场变换为 $\vec{m}(\mathbf{x}) \mapsto \mathfrak{R} \vec{m}(\mathbf{x})$ )，能量不会改变. 这样的旋转将一个有序态转化为另一个等价的态. 
由于均匀的旋转不耗费能量，因此通过连续性，我们期望一个在空间中缓慢变化的旋转（即 $\vec{m}(\mathbf{x}) \mapsto \Re(\mathbf{x}) \vec{m}(\mathbf{x})$ ，其中 $\Re(\mathbf{x})$ 仅有长波长的变化）耗费很小的能量. 这样的低能激发称为 Goldstone 模式. 这样的集体模式出现在任何连续对称破缺的系统中.  ${ }^5$ 固体中的声子提供一个 Goldstone 模式熟悉的例子，此时由于晶体结构的存在，平移对称性和旋转对称性被破坏. 
${ }^5$ 打破离散对称性不会产生 Goldstone 模式，因为此时不可能产生从一个态到另一个等价态缓慢变化的变换. 

出现在不同系统中堵塞 Goldstone 模式有某些共同的特征. 下面我们探讨超流中 Goldstone 模式的起源和行为. 类似于 Bose 凝聚，超流相在单个量子基态上有着宏观量级的占据数，序参量 :
$$
\psi(\mathbf{x}) \equiv \psi_{\Re}(\mathbf{x})+\mathrm{i} \psi_{\Im}(\mathbf{x}) \equiv|\psi(\mathbf{x})| \mathrm{e}^{\mathrm{i} \theta(\mathbf{x})}
$$

可以粗略地视为在 $\mathbf{x}$ 附近真实波函数的基态分量.  ${ }^6$ 波函数的相位不是可观测量，不应该出现在物理可测概率中. 