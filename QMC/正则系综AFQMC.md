## 正则系综AFQMC

[TOC]

### Background

物理方面，在Mott绝缘体等的研究中，系统的行为对于填充系数非常敏感，我们经常需要控制系统的填充为一个固定值；在冷原子和核物理等的研究中，系统也处于正则系综的范畴内。但是在一般的DQMC中，系统是在巨正则系综下工作的。为了研究这些系统的行为我们需要正则系综版本的QMC。

数值方面，在QMC中控制粒子数是通过化学势项来实现的，一般的做法是扫出一条$\langle N \rangle - \mu$的曲线，通过插值等处理手段来得到目标填充对应的化学势，但成本十分高昂，并且期望值只是一个统计量，存在涨落。为了能够严格控制模拟中的粒子数我们也需要正则系综版本的QMC。

下面我们将介绍三种正则系综版本AFQMC的实现，其中第一第二种方法并不能解决成本的问题，只能帮助我们准确的实现系综系统的模拟。第三种方法不需要化学势的控制，但是算法的实现复杂很多，也很难说成本的高低，需要通过算法复杂度进一步分析。



### Review of Grand Canonical Ensemble DQMC

一般的AFQMP框架下我们的核心是是将配分函数$Z$抽象为可以进行蒙卡抽样的辅助场形式，对此我们需要进行Trotter分解
$$
Z = \text{Tr} \left( e^{-\beta (\hat{H} - \mu \hat{N})} \right) = \text{Tr} \left( \lim_{\Delta \tau \rightarrow 0} \prod_{l=1}^{L} e^{-\Delta \tau (\hat{H} - \mu \hat{N})} \right)
$$
对于每一个虚时间切片
$$
e^{-\Delta \tau (\hat{H} - \mu \hat{N})} = e^{-\Delta \tau (\hat{K} + \hat{V})} \approx e^{-\Delta \tau \hat{K}} e^{-\Delta \tau \hat{V}}
$$
其中我们把化学式项吸收进了动能项$\hat{K}$，如果相互作用项满足
$$
e^{-\Delta \tau \hat V} = e^{-\Delta \tau \sum_{\gamma} \lambda_{\gamma} \hat{\nu}_{\gamma}^2}
$$
其中$\hat \nu_{\gamma}$是单粒子算符的线形组合，此时我们可以用HS变换
$$
e^{-\Delta \tau \lambda_{\gamma} \hat{\nu}_{\gamma}^2} = \int_{-\infty}^{\infty} d \phi \frac{e^{-\phi^2/2}}{\sqrt{2\pi}} e^{\phi \sqrt{-\Delta \tau \lambda_{\gamma}} \hat{\nu}_{\gamma}}
$$
即我们引入了辅助场$\phi$。由于在每个时间切片上我们都需要引入辅助场，最后我们的配分函数写为：
$$
\begin{aligned}
Z 
& \approx \text{Tr} \left( \prod_{l=1}^L e^{-\Delta \tau \hat{K}} 
\int_{-\infty}^{\infty} d \vec{\phi}_l p(\vec{\phi}_l) e^{\sum_{\gamma} \phi_l^{\gamma} \sqrt{-\Delta \tau \lambda_{\gamma}} \hat{\nu}_{\gamma}}
\right) \\
&= \int_{-\infty}^{\infty} d \vec{\phi}_1 p(\vec{\phi}_1) \cdots \int_{-\infty}^{\infty} d \vec{\phi}_l p(\vec{\phi}_l) \text{Tr} \left( \prod_{l=1}^L \hat{B}(\vec{\phi}_l) \right) \\
&= \int_{-\infty}^{\infty} d \vec{\phi}_1 p(\vec{\phi}_1) \cdots \int_{-\infty}^{\infty} d \vec{\phi}_l p(\vec{\phi}_l) \det \left( I + \prod_{l=1}^L \hat{B}(\vec{\phi}_l) \right) 
\end{aligned}
$$




### Approach 1	Projection Method

在AFQMC中，我们的首要任务是求出辅助场形式下的配分函数$Z = \text{Tr}[e^{-\beta (\hat{H} - \mu \hat{N})}]$，这通常是在巨正则系综下完成的。转换到正则系综，只需要去掉化学势项，并使用粒子数固定的基矢求迹即可。但是在固定粒子数的基矢下求迹要复杂很多。

粒子投影法是一种使用巨正则系综基矢求迹但又保持粒子数不变的方法，它的思想非常简单，只需要给求迹的矩阵乘上一个克罗内克delta函数$\delta_{N, \hat{N}}$即可。可以证明通过将克罗内克函数展开为傅立叶变换的形式并积分，可以得到正则系综的配分函数为
$$
Z_{\text{can}} = \text{Tr}[\delta_{\hat{N}, N} e^{-\beta \hat{H}}] = \int d\vec{\phi} p(\vec{\phi}) \frac{1}{N_s} \sum_{m=1}^{N_{s}}  e^{-i \phi_m N} \det [ 1 + e^{i\phi_m} B(\vec{\phi}) ]
$$
其中$\phi_m = 2 \pi m / N_s$。这个式子的证明很简单，
$$
Z_{\text{can}} = \text{Tr}[\delta_{\hat{N}, N} e^{-\beta \hat{H}}]
= \frac{1}{N_s} \sum_{m=1}^{N_s} e^{-i\phi_m N} \text{Tr}[e^{-i \phi_m \hat{N}} e^{-\beta \hat{H}}]
$$
剩下要做的就是和DQMC中相同的操作。

现在我们可以像巨正则系综一样进行采样，但是具有限制粒子数在预定值附近波动的化学势，所以仍然需要通过扫描化学势来确定目标粒子数。

***

Q：为什么仍然需要化学势项？

***



### Approach 2	Assaad's Approach

Assaad的做法是为哈密顿量引入长程涨落相互作用
$$
\hat{H}(\lambda) = \hat{H} + \hat{H}_{\lambda} \\
\hat{H}_{\lambda} = \lambda (\hat{N} - N_0)^2
$$
因此
$$
Z_{\text{can}}(N_0) = \lim_{\lambda \rightarrow \infty} \text{Tr} [e^{-\beta \hat{H}(\lambda)}]
$$
$\hat{H}$中隐含了$\mu \hat{N}$，这个方法仍然需要控制$\mu$在一个合理的区间内。

这个形式的好处是，它是标准的$e^{\Delta \tau \lambda \hat{A}^2}$形式，可以在辅助场框架下天然的处理
$$
e^{\Delta \tau \lambda \hat{A}^2} = \sum_{l = \pm 1, \pm 2} \gamma(l) e^{\sqrt{\Delta \tau \lambda} \eta(l) \hat{A}} + \mathcal{O}(\Delta \tau^4) \\
\gamma(\pm 1) = 1 + \sqrt6 / 3, \quad \eta(\pm 1) = \pm \sqrt{2(3-\sqrt6)} \\
\gamma(\pm 2) = 1 - \sqrt6 / 3, \quad \eta(\pm 1) = \pm \sqrt{2(3+\sqrt6)}
$$
需要注意的是粒子数是被$e^{-\lambda \beta(N-N_0)^2}$所压制，即收敛的相关参数是$\beta \lambda$而不是$\lambda$本身，所以在高温时，需要更大的$\lambda$，低温时很小的$\lambda$就可以完成任务。
$$
\chi_c = \frac{\beta}{V} (\langle \hat{N^2} \rangle - \langle \hat{N} \rangle^2 )
$$
<img src="/Users/hongtu/Library/Application Support/typora-user-images/image-20231221212747669.png" alt="image-20231221212747669" style="zoom:50%;" />

<img src="/Users/hongtu/Library/Application Support/typora-user-images/image-20231221214736903.png" alt="image-20231221214736903" style="zoom:50%;" />

此外由于加入的相互作用项$(\hat{N} - N_0)^2$是个长程相互作用，所以在大格子上单个flip的接受率会很低，为了解决这个问题使用如下的分解：
$$
e^{-\beta \hat{H}} = \prod_{\tau = 1}^{L_\tau} \left[ e^{-\Delta \tau \hat T} e^{-\Delta \tau \hat V} e^{-\frac{\Delta \tau}{n_{\lambda}} \hat{H}_{\lambda}} \cdots e^{-\frac{\Delta \tau}{n_{\lambda}} \hat{H}_{\lambda}} \right].
$$
我们将加入的额外相互作用项分成了$n_{\lambda}$份，所以在进行HS分解时，我们也需要$n_{\lambda}$个辅助场。

<img src="/Users/hongtu/Library/Application Support/typora-user-images/image-20231221213047411.png" alt="image-20231221213047411" style="zoom:50%;" />



### Approach 3	Recursive Approach

1. Partition Function

$$
Z_N = \text{Tr}_c (e^{-\beta \hat{H}})  \\
Z_N \approx \int_{-\infty}^{\infty} d\vec{\phi}_1 p(\vec{\phi}_1) \cdots \int_{-\infty}^{\infty} d\vec{\phi}_L p(\vec{\phi}_L)
\text{Tr}_c \left( \prod_l^L \hat{B}(\vec{\phi}_l) \right). \\
\prod_l^L \hat{B}(\vec{\phi}_l) = \prod_l^L e^{\Delta \tau \hat{K}/2} e^{\sum_{\gamma} \phi^{\gamma}_l \sqrt{-\Delta \tau \lambda_\gamma} \hat{V}_{\gamma}} e^{\Delta \tau \hat{K}/2} = e^{-\beta \hat{A}(\vec{\phi})}
$$

这里我们认为对于某一个场的构型，$\hat{B}$矩阵的乘积是可以对角化的，即
$$
e^{-\beta \hat{A}(\vec{\phi})} = e^{-\beta \sum_{i, j} \hat{a}^{\dagger}_i A(\vec{\phi})_{ij} \hat{a}_j} = e^{-\beta \sum_{\gamma}\hat{a}^{\dagger}_{\gamma} \tilde{\varepsilon}(\vec{\phi}) \hat{a}_{\gamma}}
$$
其中$\{\tilde{\varepsilon}_{\gamma}\}$被称作有效单粒子能谱。在这个形式下我们可以很容易求出正则系综的配分函数
$$
\begin{align}
\text{Tr}_c (e^{-\beta \hat{A}(\vec{\phi})}) 
&= \text{Tr}_c (e^{-\beta \sum_{\gamma} \hat{a}^{\dagger}_{\gamma} \tilde{\varepsilon}_{\gamma}(\vec{\phi}) \hat{a}_{\gamma}}) \\
&= \sum_{\Gamma} \langle \Gamma | e^{-\beta \sum_{\gamma} \hat{a}^{\dagger}_{\gamma} \tilde{\varepsilon}_{\gamma}(\vec{\phi}) \hat{a}_{\gamma}} | \Gamma \rangle \\
&= \sum_{\Gamma} e^{-\beta \sum_{\gamma=1}^{N_s} n_{\gamma} \tilde{\varepsilon}_{\gamma}(\vec{\phi})}
\end{align}
$$
其中$| \Gamma \rangle$是$a^{\dagger}_{\gamma}$表象下总粒子数为$N$的基矢，
$$
Z = \int d \vec{\phi} p(\vec{\phi}) \sum_{\Gamma} e^{-\beta \sum_{\gamma=1}^{N_s} n_{\gamma} \tilde{\varepsilon}_{\gamma}(\vec{\phi})}
$$
我们知道在辅助场量子蒙特卡洛模拟中我们采样的是辅助场的构型，但是在上面这个式子中，辅助场权重$\sum_{\Gamma} e^{-\beta \sum_{\gamma = 1}^{N_s} n_{\gamma} \tilde{\varepsilon}_{\gamma}(\vec{\phi})}$仍然是一个不好确定的量，下面我们将递归方法应用到求解辅助场权重中

对于$N$粒子的自由气体，我们可以把$Z_N$按照子系统配分函数$Z_{N-k}$展开
$$
Z_N = \frac{1}{N} \sum_{k=1} (\pm 1)^{k+1} z_k Z_{N-k}
$$
其中$Z_0 = 1$，对于玻色子取正号，对于费米子取负号
$$
z_k = \sum_i e^{-k \beta \varepsilon_i}
$$
下标$i$遍历所有的单粒子态，公式的证明可以参考[4]。在某个辅助场下我们已经把配分函数写成了自由粒子的形式，所以可以直接利用上面的公式得到：
$$
Z_N(\vec{\phi}) = \frac{1}{N} \sum_{k=1} (\pm 1)^{k+1} z_k(\vec{\phi}) Z_{N-k}(\vec{\phi})
$$
同样的我们有$Z_0(\vec{\phi}) = 1$和
$$
z_k(\vec{\phi}) = \sum_\gamma e^{-k\beta \tilde\varepsilon_{\gamma}(\vec{\phi})}
$$
现在我们就得到了最终的配分函数
$$
\begin{aligned}
Z_N 
& \approx \int d \vec{\phi} p(\vec{\phi}) Z_N(\vec{\phi}) \\ 
& = \int d \vec{\phi} p(\vec{\phi}) \frac{1}{N} \sum_{k=1} (\pm 1)^{k+1} z_k(\vec{\phi}) Z_{N-k}(\vec{\phi})
\end{aligned}
$$

2. Observables

在辅助场量子蒙特卡洛中，我们希望得到观测量$\langle \hat{a}^{\dagger}_i \hat{a}_j \rangle$
$$
\langle \hat{a}^{\dagger}_i \hat{a}_j \rangle = \frac{\text{Tr}_c(\hat{a}^{\dagger}_i \hat{a}_j e^{-\beta \hat{H}})}{\text{Tr}_c (e^{-\beta \hat{H}})}
$$
分母我们已经得到，现在我们要寻求一个方法计算分子，即计算
$$
\begin{aligned}
\tilde{D}_{ij} 
&= \text{Tr}_c (\hat{a}^{\dagger}_i \hat{a}_j e^{-\beta \hat{H}}) \\
& \approx \int d \vec{\phi} p(\vec{\phi}) \text{Tr}_c (\hat{a}^{\dagger}_i \hat{a}_j e^{-\beta \hat{A}(\vec{\phi})}) \\
& = \int d\vec{\phi} p(\vec{\phi}) \sum_{\Gamma} \langle \Gamma | \hat{a}^{\dagger}_i \hat{a}_j | \Gamma \rangle e^{-\beta \sum_{\gamma=1}^M n_{\gamma} \tilde{\varepsilon}(\vec{\phi})}
\end{aligned}
$$
利用表象变换我们知道
$$
\hat{a}^{\dagger}_i \hat{a}_j = \sum_{\lambda \mu} \langle \lambda | i \rangle \langle j | \mu \rangle \hat{a}^{\dagger}_{\lambda} \hat{a}_{\mu} = \sum_{\lambda \mu} U^{ij}_{\lambda \mu} \hat{a}^{\dagger}_{\lambda} \hat{a}_{\mu}
$$

$$
\begin{aligned}
\tilde{D}_{ij} (\vec{\phi})
&= \sum_{\Gamma} \sum_{\lambda \mu} U^{ij}_{\lambda \mu} \langle \Gamma | \hat{a}^{\dagger}_{\lambda} \hat{a}_{\mu} | \Gamma \rangle e^{-\beta \sum_{\gamma=1}^M n_{\gamma} \tilde{\varepsilon}(\vec{\phi})} \\
& = \sum_{\Gamma} \sum_{\lambda} U^{ij}_{\lambda \lambda} \langle \Gamma | \hat{a}^{\dagger}_{\lambda} \hat{a}_{\lambda} | \Gamma \rangle e^{-\beta \sum_{\gamma=1}^M n_{\gamma} \tilde{\varepsilon}(\vec{\phi})} \\
& = \sum_{\lambda} U^{ij}_{\lambda \lambda} \langle n_{\lambda} \rangle_N Z_N(\vec{\phi})
\end{aligned}
$$

这样我们就得到了一个理想的可以用蒙卡进行测量的可观测量形式。此外，我们也可以用递归的方法来计算
$$
\langle n_{\lambda} \rangle_N = \frac{\sum_{\Gamma} n_{\lambda} e^{-\beta \sum_{\gamma = 1}^M n_{\gamma} \tilde{\varepsilon}_{\gamma}(\vec{\phi})}}{\sum_{\Gamma} e^{-\beta \sum_{\gamma = 1}^M n_{\gamma} \tilde\varepsilon(\vec{\phi})}} = \frac{Z_{N-1}(\vec{\phi})}{Z_N(\vec{\phi})} e^{-\beta \varepsilon_{\lambda}} \langle 1 \pm \hat{n}_{\lambda} \rangle_{N-1}
$$
最终我们就得到了
$$
\langle \hat{a}^{\dagger}_{i} \hat{a}_j \rangle 
\approx \frac{\int d\vec{\phi} p(\vec{\phi}) [\sum_{\lambda} U_{\lambda \lambda}^{ij} \langle n_{\lambda} \rangle_N] Z_N(\vec{\phi})}{\int d\vec{\phi} p(\vec{\phi}) Z_N(\vec{\phi})}
$$






### References

[1] Wang Z, Assaad F F, Toldin F P. Finite-size effects in canonical and grand-canonical quantum Monte Carlo simulations for fermions[J]. Physical Review E, 2017, 96(4): 042131.

[2] Shen T, Liu Y, Yu Y, et al. Finite temperature auxiliary field quantum Monte Carlo in the canonical ensemble[J]. The Journal of Chemical Physics, 2020, 153(20).

[3] Borrmann P, Franke G. Recursion formulas for quantum statistical partition functions[J]. The Journal of chemical physics, 1993, 98(3): 2484.