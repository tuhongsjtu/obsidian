## 4.1    The homogeneity assumption
在之前的章节中连续相变附近的奇异行为由一系列临界指数$\{ \alpha, \beta, \gamma, \delta, \nu, \eta, \cdots \}$表征. 由于涨落的重要性鞍点近似预测的指数被发现不够可靠. 由于不同的热力学量是相互关联的，这些指数也并不是互相独立的. 本章的目的就是发现它们之间的关系，并且找到能够描述临界点的最少数量的独立指数. 
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

均匀性假设是指，在超出鞍点近似时，自由能（以及其他热力学量）的奇异形式保留均匀形式：
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



