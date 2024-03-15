#### References
[1] 卢欣｜Note(2)---LFLT中的格林函数与准粒子谱[[https://zhuanlan.zhihu.com/p/372538817]]


![[Pasted image 20231225162159.png|500]]

对于费米液体，由于粒子之间存在相互作用，从而需要引入自能项描述相互作用进行修正，其格林函数和谱函数为
$$
G(\mathbf{k}, \omega) = \frac{1}{\omega - \varepsilon(\mathbf{k}) - \Sigma(\mathbf{k}, \omega) + i0^+}
$$
$$
A(\mathbf{k}, \omega) 
= - \frac{1}{\pi} \mathrm{Im} G(\mathbf{k}, \omega) 
= - \frac{1}{\pi} \frac{\mathrm{Im}\Sigma(\mathbf{k}, \omega)}{(\omega - \varepsilon(\mathbf{k}) - \mathrm{Re}\Sigma(\mathbf{k}, \omega))^2 + (\mathrm{Im} \Sigma(\mathbf{k}, \omega))^2}
$$
由于$A(\mathcal{k}, \omega) \ge 0$，因此$\mathrm{Im} \Sigma(\mathbf{k}, \omega) \le 0$，谱函数是一个Lorentz型曲线，半高宽正比于自能虚部. 虚部越趋近于$0$，准粒子寿命将无限长.

![[Pasted image 20231225165102.png|500]]
当$\mathrm{Im} \Sigma(\mathbf{k}, \omega) \rightarrow 0^-$时，
$$
A(\mathbf{k}, \omega)
= \delta(\omega - \varepsilon(\mathbf{k}) - \mathrm{Re} \Sigma(\mathbf{k}, \omega)) 
= \left| 1 - \frac{\partial \Sigma(\mathbf{k}, \omega)}{\partial \omega} \right|^{-1}_{\omega = E_k} \delta(\omega - E(\mathbf{k}))
$$
式中$E(\mathbf{k}) = \varepsilon(\mathbf{k}) - \mathrm{Re} \Sigma(\mathbf{k}, \omega)$，其中用到了公式$\delta(f(x)) = \frac{\delta(x - x_0)}{f'(x_0)}$，当$f(x) = 0$时有$x = x_0$. 我们定义谱权重为（==这与虚时的准粒子权重似乎有些不同==）：
$$
Z_{\mathbf{k}} = \left| 1 - \frac{\partial \Sigma(\mathbf{k}, \omega)}{\partial \omega} \right|^{-1}_{\omega = E_k}
$$
可以看出当自能部分$\Sigma (\mathbf{k}, \omega) = 0$时$Z_{\mathbf{k}} = 1$（==为什么不是自能实部为$0$==，是因为此时自能虚部已经趋于$0$所以自能等于自能实部吗，准粒子权重只定义在虚部趋于$0$时吗），这是自由粒子的情况. 
但是当自能虚部趋于$0$时，费米液体体系仍有一个类似于自由粒子体系的$\delta$峰，只是没有自由粒子体系的半高宽窄，我们称其为相干部分. 当$\mathrm{Im} \Sigma$为有限值时，谱函数包含两部分：相干和非相干部分
$$
A(\mathbf{k}, \omega) = A_{Coherent}(\mathbf{k}, \omega) + A_{Incoherent}(\mathbf{k}, \omega)
$$
相干部分满足$A_{Coherent} (\mathbf{k}, \omega) = Z_{\mathbf{k}} \delta(\omega - E(\mathbf{k}))$，是一个具有一定高斯展宽的$\delta$函数，对其积分有
$$
\int A_{Coherent} d\omega = Z_{\mathbf{k}}
$$
因而对相干部分进行积分等于准粒子的权重，非零的谱权重代表了具有良好定义的准粒子. 非相干部分代表了高阶的激发，比如多粒子的散射过程等等，考虑到谱权重的归一化，所以
$$
\int A_{Incoherent}(\mathbf{k}, \omega) d\omega = 1 - Z_{\mathbf{k}}
$$
类似于自由粒子，我们可以得到动量空间的分布==?==
$$
n_{\mathbf{k} \sigma} = \int A(\mathbf{k}, \omega) f(\omega) d\omega = Z_{\mathbf{k}} \theta(\varepsilon_{F} - E_k) + \phi(\mathbf{k})
$$
可以看到准粒子权重会在费米面附近制造一个突变. 
![[Pasted image 20231225172958.png]]
因此一个体系能否用费米液体理论描述的关键是判断费米面附近的准粒子谱权重是否为$0$. 