## Landau费米液体的精髓
==电子-电子相互作用的唯一效果时改变电子的质量，对物理可观测量给出小的修正并导致无碰撞的零声波==
![[Pasted image 20231224181041.png|500]]

![[Pasted image 20231224181843.png|500]]

## 费米液体能够工作的原因
1. 长程Coulomb相互作用的屏蔽
一般的长程相互作用会导致系统出现奇异性，屏蔽效应使得奇异性大为减弱.
2. 电子费米面的存在
费米面的存在限制了实际参与相互作用电子的数目，并使得相互作用过程变得简单且稳定

## 费米液体的基本假设
1. 绝热性
2. 一对一，即准粒子的存在

## 费米液体理论的失效
1. 量子临界系统
2. 量子规范场出现
3. 强磁场下，即分数量子霍尔效应
这里的量子临界系统指的是费米气体与处于临界状态的序参量场的耦合系统，例如在铁基超导和重费米子金属中观察到的金属性反铁磁量子临界行为就一般理解为费米气体与临界反铁磁序参量场耦合的产物. 临界状态的序参量场会受到费米气体电子空穴对激发影响表现Landau阻尼，而Landau阻尼反作用与费米子导致准粒子行为偏离费米液体.

## 费米液体基态
根据绝热性，费米液体的能谱与无相互作用电子气一致，为费米球分布，所以基态波函数为：
$$
| \Psi_{FL} \rangle = \prod_{k \le k_F, \sigma = \uparrow, \downarrow} | \tilde{n}_{k \sigma} \rangle
$$
这里相互作用费米子的分布函数是$\tilde{n}_{k \sigma} =\theta (k_F - |\vec{k}|)$，与无相互作用电子气一致。对于各向同性的系统，它们也具有相同的费米波矢$k_F$.

## 费米液体的激发：准粒子与准空穴
1. 自由电子气的激发
对于自由电子气，在其费米球态添加一个动量为$k_0$自旋为$\sigma_0$的粒子，体系的波函数为：
$$
| \Psi^{k_0, \sigma_0}_0 \rangle = | k_0, \sigma_0 \rangle \prod_{k \le k_F, \sigma = \uparrow, \downarrow} | n_{k \sigma} \rangle
$$
激发能为$\epsilon_{k_0} = \frac{k_0^2}{2m} - E_F \gt 0$. 同理也可以定义空穴态，即在费米球态中移除一个动量为$k_0$自旋为$\sigma_0$的粒子：
$$
| \Psi^{k_0, \sigma_0}_0 \rangle = \prod_{k \le k_F, \sigma = \uparrow, \downarrow, k \neq k_0, \sigma \neq \sigma_0} | n_{k \sigma} \rangle
$$
上面的激发被称为单粒子激发，同时具有双粒子激发模式如粒子-空穴激发，也就是在费米球内移除一个动量为$k$的粒子并在球外产生一个动量为$k+q$的粒子.

2. 费米液体的激发
根据费米液体一一对应的原则，无相互作用情况下的激发会演化到相互作用情况下的对应物，所以费米气体中的粒子，空穴态激发对应费米液体中的准粒子和准空穴态激发：
$$
| \Psi^{k_0, \sigma_0} \rangle_0 = | n_{k_0, \sigma_0} \rangle \prod_{k \le k_F, \sigma = \uparrow, \downarrow} | n_{k \sigma} \rangle \Rightarrow | \Psi^{k_0, \sigma_0}_{FL} \rangle =  | \tilde{n}_{k_0, \sigma_0} \rangle \prod_{k \le k_F, \sigma = \uparrow, \downarrow} | \tilde{n}_{k \sigma} \rangle
$$
$$
| \Psi^{-k_0, -\sigma_0} \rangle_0 = \prod_{k \le k_F, \sigma = \uparrow, \downarrow, k \neq k_0, \sigma \neq \sigma_0} | n_{k \sigma} \rangle \Rightarrow | \Psi^{-k_0, -\sigma_0}_{FL} \rangle =  \prod_{k \le k_F, \sigma = \uparrow, \downarrow, k \neq k_0, \sigma \neq \sigma_0} | \tilde{n}_{k \sigma} \rangle
$$
这里定义的准粒子/空穴激发实际上指的是费米子分布函数$\tilde{n}_{k \sigma}$相对于基态分布$n^0_{k \sigma}$（==这是哪个基态？==）的偏离，记为$\delta n_{k \sigma} = \tilde{n}_{k \sigma} - n^0_{k \sigma}$. 因此费米液体在基态时不存在准粒子，只有在被激发后才出现准粒子. 在下面的讨论中我们用$n_{k\sigma}$代替$\tilde{n}_{k \sigma}$以简化符号.

现在我们定义单个准粒子的能量，也就是相对于完全填满的费米球基态的激发能：
$$
E^0_{k_0, \sigma_0} = E_{k_0, \sigma_0} - E_0
$$
为了讨论粒子数可变的情况可以定义准粒子能量为：
$$
\varepsilon^0_{k_0, \sigma_0} = E^0_{k_0, \sigma_0} - \mu
$$
这样费米面上的准粒子能量为$0$，费米面以上的准粒子能量为正，费米面下的准空穴态能量为负.

## Landau能量泛函
当系统处于有限温度或者受到外场的影响时会有多个准粒子激发，此时系统的能量应该是准粒子分布函数的泛函$\mathcal{E} = \mathcal{E}(\{n_{k \sigma}\})$.
能量泛函应该是关于分布函数的复杂函数，但是在低温下分布函数对于基态分布$n_{k \sigma}^0$的偏离并不大，因此我们可以将其作为泰勒展开的出发点，物理上相当于是考虑准粒子数量不太多的情况，
$$
\begin{aligned}
\mathcal{E} (\{ n_{k \sigma} \}) 
= & \mathcal{E} (\{ n^0_{k \sigma} \}) + \sum_{k \sigma} (n_{k \sigma} - n^0_{k \sigma}) \frac{\partial \mathcal{E} (\{ n_{k \sigma} \})}{\partial n_{k \sigma}} |_{n_{k\sigma} = n^0_{k\sigma}} \\
& + \frac{1}{2} \sum_{k \sigma, k' \sigma'} (n_{k \sigma} - n^0_{k \sigma}) (n_{k' \sigma'} - n^0_{k' \sigma'}) \frac{\partial \mathcal{E} (\{ n_{k \sigma} \})}{\partial n_{k \sigma} \partial n_{k' \sigma'}} |_{n_{k\sigma} = n^0_{k\sigma}, n_{k' \sigma'} = n^0_{k'\sigma'}} + \cdots
\end{aligned}
$$
第一项表示基态能量，$\frac{\partial \mathcal{E} (\{ n_{k \sigma} \})}{\partial n_{k \sigma}} |_{n_{k\sigma} = n^0_{k\sigma}}$表示的是仅有动量为$k$，自旋为$\sigma$的费米子数目相对于基态分布有变化时，系统能量的变化率，即单个准粒子的能量$\varepsilon^0_{k \sigma}$. 我们定义$f_{k \sigma, k' \sigma'} = \frac{\partial \mathcal{E} (\{ n_{k \sigma} \})}{\partial n_{k \sigma} \partial n_{k' \sigma'}} |_{n_{k\sigma} = n^0_{k\sigma}, n_{k' \sigma'} = n^0_{k'\sigma'}}$为Landau相互作用函数，表示只有两个准粒子$k \sigma$和$k' \sigma'$存在时的相互作用强度. 最终我们得到Landau能量泛函表示为：
$$
\mathcal{E}(\{ n_{k \sigma} \}) = E_0 + \sum_{k \sigma} \varepsilon^0_{k \sigma} \delta n_{k \sigma} + \frac{1}{2} \sum_{k \sigma, k' \sigma'} f_{k \sigma, k' \sigma'} \delta n_{k \sigma} \delta n_{k' \sigma'} + \cdots
$$
现在的问题是上面的各个参数我们仍然未知.
现在考虑准粒子独立存在时的能量$\varepsilon^0_{k \sigma}$，把它在费米面附近展开：
$$
\varepsilon^0_{k \sigma} = \varepsilon^0_{k_F \sigma} + \frac{\partial \varepsilon^0_{k \sigma}}{ \partial k }|_{k = k_F} (k - k_F) + \cdots \approx v_F^*(k - k_F)
$$
这里定义了准粒子的有效费米速度$v^*_F$：
$$
\begin{aligned}
v_F^* = \frac{\partial \varepsilon^0_{kF}}{\partial k} | _{k = k_F} 
\end{aligned}
$$
并且我们还可以定义相应的有效质量$m^*$：
$$
m^* = \frac{k_F}{v^*_F}
$$
如果我们计算准粒子在费米面上的态密度时，可以发现
$$
N^*(0) 
= 2 \int \frac{4 \pi^2 k^2 dk}{(2 \pi)^3} \delta(\varepsilon^0_k) 
= \int \frac{k^2 dk}{\pi^2} \delta(v_F^*(k-k_F)) = \frac{k_F^2 / v_F^*}{\pi^2} = \frac{m^* k_F}{\pi^2} \propto m^*
$$
态密度正比于准粒子的有效质量，表明==越大的有效质量导致越大的态密度==. 同时$N^*(0) = \frac{m^*}{m} N(0)$.
接下来我们考虑有多个准粒子存在时对单个准粒子能量的修正，即我们考虑Landau能量泛函对占据数的一阶导数：
$$
\frac{\partial \mathcal{E}}{\partial n_{k \sigma}} 
= \frac{\partial \mathcal{E}}{\partial (\delta n_{k \sigma})}
\equiv \varepsilon_{k \sigma}
\equiv \varepsilon^0_{k \sigma} + \sum_{k' \sigma'} f_{k \sigma, k' \sigma'} \delta n_{k \sigma, k' \sigma'}
$$
当只有一个准粒子时$\varepsilon_{k \sigma} = \varepsilon^0_{k \sigma}$，有两个准粒子时$\varepsilon_{k \sigma} = \varepsilon^0_{k \sigma} + f_{k \sigma, k' \sigma'} \delta n_{k' \sigma'}$. 可以看到==Landau相互作用函数改变了产生一个准粒子所需要的能量==.

## 费米液体的热力学性质
* 自由能与熵
要讨论系统的热力学行为，我们首先需要知道系统自由能的形式，而通过Landau能量泛函已经得到了能量的表达式，还需要热力学熵的形式. 由于热力学熵仅依赖于能谱结构而不依赖于能谱的细节，所以==无相互作用系统的熵和相互作用系统的熵完全相同==. 因此费米液体的熵为
$$
\mathcal{S} = -\sum_{k \sigma} [n_{k \sigma} \ln n_{k \sigma} + (1 - n_{k \sigma}) \ln (1 - n_{k \sigma})]
$$
由此可以得到费米液体的自由能为：
$$
\begin{aligned}
\mathcal{F} = \mathcal{E} - T\mathcal{S} 
&= E_0 + \sum_{k \sigma} \varepsilon^0_{k \sigma} \delta n_{k \sigma} + \frac{1}{2} \sum_{k \sigma, k' \sigma'} f_{k \sigma, k' \sigma'} \delta n_{k \sigma} \delta n_{k' \sigma'} + \cdots \\
&+ T \sum_{k \sigma} [n_{k \sigma} \ln n_{k \sigma} + (1 - n_{k \sigma}) \ln (1 - n_{k \sigma})]
\end{aligned}
$$
按照这个式子，在==零温时费米液体只有一种构型，熵应为$0$，这与我们在模拟中得到的结果一致==
在热平衡下$n_{k \sigma}$应使自由能取极小值，这导致
$$
\overline{\delta} \mathcal{F} 
= 0
= \sum_{k \sigma} \left[ \varepsilon^0_{k \sigma} + \sum_{k' \sigma'} f_{k \sigma, k' \sigma'} \delta n_{k' \sigma'} \right] \overline{\delta} n_{k \sigma} + T \sum_{k \sigma} \ln \frac{n_{k \sigma}}{1 - n_{k \sigma}} \overline{\delta} n_{k \sigma} 
= \sum_{k \sigma} \left[ \varepsilon_{k \sigma} + T \frac{n_{k \sigma}}{1 - n_{k \sigma}} \right] \overline{\delta} n_{k \sigma}
$$
这样就可以得到费米子占据数分布的形式，即标准费米分布
$$
n_{k \sigma} = \frac{1}{e^{\varepsilon_{k \sigma} / T} + 1} = f_F(\varepsilon_{k \sigma})
$$
准粒子的分布函数为：
$$
\delta n_{k \sigma} = n_{k \sigma} - n^0_{k \sigma} = f_F(\varepsilon_{k \sigma}) - \theta(k_F - |\vec{k}|)
$$
但是由于准粒子能量为$\varepsilon_{k \sigma} = \varepsilon^0_{k \sigma} + f_{k \sigma, k' \sigma'} \delta n_{k' \sigma'}$，是一个关于其他准粒子分布的复杂函数，所以实际计算时需要迭代计算直到收敛.

* 低温热容
在低温时准粒子数较少，系统的能量主要由单粒子部分提供
$$
\mathcal{E} \approx E_0 + \sum_{k \sigma} \varepsilon^0_{k \sigma} \delta n_{k \sigma} = E_0 + \sum_{k \sigma} \varepsilon^0_{k \sigma} (n_{k \sigma} - n^0_{k \sigma})
$$
热容由能量对温度的一阶导数给出
$$
C_v = \frac{\partial \mathcal{E}}{\partial T} = \sum_{k \sigma} \varepsilon^0_{k \sigma} \frac{\partial n_{k \sigma}}{\partial T}
$$
同时分布函数已经给出
$$
n_{k \sigma} = \frac{1}{e^{\varepsilon_{k \sigma} / T} + 1} \approx \frac{1}{e^{\varepsilon^0_{k \sigma} / T} + 1}
$$
容易得到热容为：
$$
C_v \approx \sum_{k \sigma} \varepsilon^0_{k \sigma} \frac{\partial f_F(\varepsilon^0_{k \sigma})}{\partial T}
= \int d\varepsilon N^*(\varepsilon) \varepsilon \frac{\partial f_F(\varepsilon)}{\partial T} 
\approx N^*(0) \frac{\pi^2}{3} T
\equiv \gamma^* T
$$
这与Sommerfeld电子气理论的结果时相似的，此外有
$$
\frac{\gamma^*}{\gamma} = \frac{N^*(0)}{N(0)} = \frac{m^*}{m} = \frac{v_F}{v_F^*}
$$
也就是说费米液体相对于费米气体的有效质量增强正比于费米面态密度的比率.

## Landau参数
Landau相互作用函数可以分为自旋无关与自旋依赖两部分
$$
f_{k \sigma, k' \sigma'} = f_{k, k'}^s + f^a_{k, k'} \sigma \sigma'
$$
当准粒子在==费米面附近==时，相互作用函数只与准粒子的费米动量有关，并且对于各向同性的系统，只有费米动量的相对角度是重要的. 同时为了得到无维度的形式，可以给相互作用函数乘上费米面上的准粒子态密度$N^*(0)$
$$
f^{s/a}_{k, k'} \approx f^{s/a}(\cos \theta), \quad \cos \theta = \frac{\vec{k}_F \cdot \vec{k}_F'}{k_F^2}
$$
$$
F^{s/a}(\cos \theta) = N^*(0) f^{s/a}(\cos \theta)
$$
所谓Landau参数，即是$F^{s/a}$按照Legendre多项式展开的系数$F_l^{s/a}$
$$
F^{s/a}(\cos \theta) = N^*(0) f^{s/a}(\cos \theta)
$$
$$
F^{s/a}(\cos \theta) = \sum_{l = 0}^{\infty} ( 2l + 1 ) F^{s/a}_{l} P_l(\cos \theta)
$$
$$
F_l^{s/a} = \frac{1}{2} \int_{-1}^1 dx F^{s/a}(x) P_l(x)
$$
实际上我们会看到只需要很少几个Landau参数就可以表征一般费米液体的可观测量
![[Pasted image 20231224175549.png|500]]

## 费米液体的集体模式
经典系统的动力学或输运性质：Boltzman微分-积分方程
对于相互作用系统形式更为复杂，严格的理论处理仅能对少数系统进行。因此实际上在处理金属在内的许多量子体系输运性质时我们都采用所谓半经典处理，也就是直接采用Boltzman方程的形式，然后考虑粒子的统计性质，即让粒子分布函数在平衡时等于玻色或者费米分布，在碰撞项的处理中往往采用费米黄金规则以估计粒子分布函数由于粒子发生散射导致的变化。

我们考虑粒子的分布函数$n_{k \sigma}$，我们知道平衡时费米液体中的粒子分布函数是标准的费米分布. 当给系统添加随着时间和空间变化的电磁场时，（或者认为系统温度分布不均）分布函数也会显示对于空间$x$和时间$t$的依赖，此时分布函数$n_{k \sigma}$也对时间空间有依赖. 因此我们可以写成$n_{k \sigma} = n_{k \sigma}(x, t)$.

现在我们考虑分布函数的变化，即分布函数$n_{k \sigma}$的全导数
$$
\frac{D n_{k \sigma}(x, t)}{D t} = \frac{\partial n_{k \sigma}}{\partial t} + \frac{\partial n_{k \sigma}}{\partial x} \cdot \frac{\partial x}{\partial t} + \frac{\partial n_{k \sigma}}{\partial k} \cdot \frac{\partial k}{\partial t} = \frac{\partial n_{k \sigma}}{\partial t} + \dot{x} \cdot \nabla_x n_{k \sigma} + \dot{k} \cdot \nabla_k n_{k \sigma}
$$
另一方面，粒子之间的相互作用，或者说碰撞会使得$k$态的粒子转化为其他态的粒子，这样自然会使得$k$态粒子的分布函数发生变化，我们把这种由于碰撞导致的分布函数变化称为碰撞项，记为$I[\{n_{k \sigma}\}]$，代表单位时间内由于碰撞导致的分布函数变化，当不存在碰撞时为$0$. 最后我们得到半经典的Boltzman方程为
$$
\frac{D n_{k \sigma}(x, t)}{D t} =  \frac{\partial n_{k \sigma}}{\partial t} + \dot{x} \cdot \nabla_x n_{k \sigma} + \dot{k} \cdot \nabla_k n_{k \sigma} = I[\{n_{k\sigma}\}]
$$
由于无法同时确定动量和位置，所以上述方程中的分布函数只能看作是粒子所对应的波包的分布函数（==？==），这实际上要求波包在实空间扩展的范围远大于原胞，换句话说，对晶格中的电子来说，当其平均自由程远大于晶格尺度时，Boltzman方程描述才是有效的.

## 碰撞项
碰撞项来自两部分：$k$态的粒子经过碰撞转化为$k'$态的粒子，以及相反的过程
$$
I[\{n_{k \sigma}\}] = -\frac{1}{V} \sum_{k' \sigma'}(W_{k \sigma, k' \sigma'} n_{k \sigma} (1 - n_{k' \sigma'}) - W_{k' \sigma', k \sigma} n_{k \sigma} (1 - n_{k \sigma}))
$$
$W_{k \sigma, k' \sigma'}$时单位时间从$k \sigma$态到$k' \sigma'$的跃迁概率，通常用Fermi黄金规则进行近似估计.
在最简单的弛豫时间金丝峡，碰撞项可以用弛豫时间代替
$$
I[\{n_{k \sigma}\}] = - \frac{n_{k \sigma} - n^0_{k \sigma}}{\tau_k}
$$
这里$n^0_{k \sigma}$是平衡时的分布，$\tau_k$时弛豫时间或者粒子的寿命. 金属中的平均自由程$l$就等于费米面上电子的平均弛豫时间和费米速度的乘积，即$l=v_F \tau_F$. 事实上如果忽略Boltzman方程中的位置和时间依赖，就有
$$
\begin{aligned}
 \frac{\partial n_{k \sigma}}{\partial t} &= - \frac{n_{k \sigma} - n^0_{k \sigma}}{\tau_k} \\
 n_{k \sigma} &= n^0_{k \sigma} + \delta n_{k \sigma} \\
 \partial_t n_{k \sigma} &= - \delta n_{k \sigma} / \tau_k \\
 \delta n_{k \sigma}(t) &= \delta n_{k \sigma}(0) e^{-t / \tau_k}
\end{aligned}
$$
即在没有外场的情况下，相对平衡分布的偏离会以指数形式衰减. 

## 杂质散射
对于简单的稀薄杂质散射，根据费米黄金规则可知$W_{k, k'} = \frac{2 \pi}{\hbar} n_i |\langle k'|U| k \rangle |^2 \delta(\epsilon_k - \epsilon_{k'})$，这里$n_i$是杂质密度，$U$是杂质势.
* 由于$\delta$函数的存在，杂质散射是弹性散射，不会改变动量大小，只改变动量能量.
* 杂质散射并不依赖于粒子分布函数，这实际上是我们假定粒子之间彼此独立. 对于电子-电子相互作用或者电子-声子相互作用，杂质散射会显著依赖于粒子的部分函数
* $W_{k, k'} = W_{k', k}$是细致平衡条件的体现，也就是说微观上粒子在不同态之间的往复跃迁是可逆的.
所以杂质散射的碰撞项可以简化为
$$
I[\{ n_{k \sigma} \}] = - \frac{1}{V} \sum_{k' \sigma'} W_{k, k'} (n_{k \sigma} - n_{k' \sigma'})
$$

## 无碰撞Boltzman方程与零声
