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
自由能中的奇点实际上可以用一个关于$t$和$h$的齐次函数来描述，如：
$$
f(t, h) = |t|^2 g_f(h / |t|^{\Delta}).
\tag{4.2}
$$
函数$g_f$只依赖于$x \equiv h / |t|^{\Delta}$的组合. 其中$\Delta$被称为*能隙指数（gap exponent）*. 通过比较上面的两个等式可以很容易地得到$g_f$的渐进行为. 如果$\lim_{x \rightarrow 0} g_f(x) \sim 1/u$则恢复$h = 0$的极限，而为了获得适当的$h$的幂，我们必须设置$\lim_{x \rightarrow \infty} g_f(x) \sim x^{4/3}/u^{1/3}$. 后者表明$f \sim |t|^2 h^{4/3} / (u^{1/3} |t|^{4\Delta/3})$. 由于$f$在$t = 0$上不具有$t$的依赖性，因此能隙指数的值为：
$$
\Delta = \frac{3}{2}.
$$
