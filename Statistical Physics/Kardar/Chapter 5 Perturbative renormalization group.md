## 5.1    Expectation values in the Gaussian model
我们可以按照带微扰的Gaussian模型来对待Landau-Ginzburg哈密顿量吗？特别的，对于零磁场，我们将检查
$$
\beta\mathcal{H}=\beta\mathcal{H}_0+\mathcal{U}\equiv\int\mathrm{d}^d\mathbf{x}\left[\frac t2m^2+\frac K2(\nabla m)^2+\frac L2(\nabla^2m)^2+\cdots\right]
+u\int\mathrm{d}^d\mathbf{x}m^4+\cdots.
$$
无微扰的Gaussian模型可以分解为独立的傅立叶模式：
$$
\beta\mathcal{H}_0=\frac1V\sum_\mathbf{q}\frac{t+Kq^2+Lq^4+\cdots}2|m(\mathbf{q})|^2
\equiv\int\frac{\mathrm{d}^d\mathbf{q}}{(2\pi)^d}\frac{t+Kq^2+Lq^4+\cdots}2|m(\mathbf{q})|^2.
$$
微扰相互作用会将正交的模式混合起来：
$$
\begin{aligned}
\mathcal{U}
=& u\int \mathrm{d} ^d\mathbf{x} m( \mathbf{x} ) ^4+ \cdots \\
=& u\int \mathrm{d} ^d\mathbf{x} \int \frac {\mathrm{d} ^d\mathbf{q} _1\mathrm{d} ^d\mathbf{q} _2\mathrm{d} ^d\mathbf{q} _3\mathrm{d} ^d\mathbf{q} _4}{( 2\pi) ^{4d}}\mathrm{e} ^{- \mathrm{i} \mathbf{x} \cdot ( \mathbf{q} _1+ \mathbf{q} _2+ \mathbf{q} _3+ \mathbf{q} _4) }m_\alpha( \mathbf{q} _1) m_\alpha( \mathbf{q} _2) m_\beta( \mathbf{q} _3) m_\beta( \mathbf{q} _4)  \\
&+ \cdots,
\end{aligned}
$$
其中关于$\alpha$和$\beta$的求和是隐式的.  关于$\mathbf{x}$的积分带来$\mathbf{q}_1+\mathbf{q}_2+\mathbf{q} _3+ \mathbf{q} _4= \mathbf{0}$，因此
$$
\mathcal{U}=u\int\frac{\mathbf{d}^d\mathbf{q}_1\mathbf{d}^d\mathbf{q}_2\mathbf{d}^d\mathbf{q}_3}{(2\pi)^{3d}}m_\alpha(\mathbf{q}_1)m_\alpha(\mathbf{q}_2)m_\beta(\mathbf{q}_3)m_\beta(-\mathbf{q}_1-\mathbf{q}_2-\mathbf{q}_3)+\cdots.
\tag{5.4}
$$
根据高斯权重的方差，有限尺寸系统的两点期望值可以很快得到：
$$
\langle m_{\alpha}(\mathbf{q}) m_{\beta}(\mathbf{q}') \rangle_0 = \frac{\delta_{\mathbf{q}, -\mathbf{q}'} \delta_{\alpha, \beta} V}{t + Kq^2 + Lq^4 + \cdots}.
$$
在无限尺寸的极限下，系统的谱变为连续，上式变为：
$$
\langle m_{\alpha}(\mathbf{q}) m_{\beta}(\mathbf{q}') \rangle_0 = \frac{ \delta_{\alpha, \beta} (2\pi)^d \delta({\mathbf{q} + \mathbf{q}'})}{t + Kq^2 + Lq^4 + \cdots}.
$$
下标$0$表示期望值是根据无微扰的Gaussian哈密顿量求得. 任意个$m$的乘积的期望值可以通过以下性质得到：
$$
\left \langle \exp \left[ \sum_i a_i m_i \right] \right \rangle_0 = \exp \left[ \sum_{i, j} \frac{a_i a_j}{2} \langle m_i m_j \rangle_0 \right],
$$
上式对于任意高斯分布变量的集合$\{ m_i \}$都是适用的. （这可以通过“completing the square”发现）. 将方程的两边按照$\{a_i\}$的幂展开的得到：
$$
\begin{aligned}&1+a_i\langle m_i\rangle_0+\frac{a_ia_j}{2}\langle m_im_j\rangle_0+\frac{a_ia_ja_k}{6}\langle m_im_jm_k\rangle_0+\frac{a_ia_ja_ka_l}{24}\langle m_im_jm_km_k\rangle_0+\cdots=\\&1+\frac{a_ia_j}{2}\langle m_im_j\rangle_0+\frac{a_ia_ja_ka_l}{24}\left(\langle m_im_j\rangle_0\langle m_km_l\rangle_0+\langle m_im_k\rangle_0\langle m_jm_l\rangle_0\right.\\&+\langle m_im_k\rangle_0\langle m_jm_l\rangle_0)+\cdots&\text{(5.8)}\end{aligned}
$$
对比上式中两边$\{ a_i \}$的幂可以得到：
$$
\left\langle\prod_{i=1}^\ell m_i\right\rangle_0=\begin{cases}0&\text{for }\ell\text{ odd}\\\text{sum over all pairwise contractions}&\text{for }\ell\text{ even.}&\end{cases}
$$
这个结果就是我们所熟知的Wick定理，对于四次项我们有：
$$
\langle m_i m_j m_k m_l \rangle_0 = \langle m_i m_j \rangle_0 \langle m_k m_l \rangle_0 + 
\langle m_i m_k \rangle_0 \langle m_j m_l \rangle_0 + 
\langle m_i m_l \rangle_0 \langle m_j m_k \rangle_0. 
$$


## 5.2    Expectation values in perturbation theory
在存在相互作用$\mathcal{U}$时，任意算符$\mathcal{O}$的期望值可以微扰地计算为：
$$
\begin{aligned}
\left\langle{\mathcal{O}}\right\rangle & =\frac{\int \mathcal{D}\vec{m}\mathcal{O}\mathrm{e}^{-\beta\mathcal{H}_0-\mathcal{U}}}{\int \mathcal{D}\vec{m}\mathrm{e}^{-\beta\mathcal{H}_0-\mathcal{U}}}=\frac{\int \mathcal{D}\vec{m}\mathrm{e}^{-\beta\mathcal{H}_0}\mathcal{O}[1-\mathcal{U}+\mathcal{U}^2/2-\cdots]}{\int \mathcal{D}\vec{m}\mathrm{e}^{-\beta\mathcal{H}_0}[1-\mathcal{U}+\mathcal{U}^2/2-\cdots]}  \\
&=\frac{Z_0[\langle\mathcal{O}\rangle_0-\langle\mathcal{OU}\rangle_0+\langle\mathcal{OU}^2\rangle_0/2-\cdots]}{Z_0[1-\langle\mathcal{U}\rangle_0+\langle\mathcal{U}^2\rangle_0/2-\cdots]}.
\end{aligned}
$$
通过按照$\mathcal{U}$的幂展开来反转分母可以得到：
$$
\begin{aligned}
\left\langle\mathcal{O}\right\rangle =& \left[\langle\mathcal{O}\rangle_0-\langle\mathcal{OU}\rangle_0+\frac12\langle\mathcal{OU}^2\rangle_0-\cdots\right]\left[1+\langle\mathcal{U}\rangle_0+\langle\mathcal{U}\rangle_0^2-\frac12\langle\mathcal{U}^2\rangle_0-\cdots\right]  \\
=&\langle O\rangle_0-(\langle OU\rangle_0-\langle O\rangle_0\langle U\rangle_0)+\frac12\left(\langle OU^2\rangle_0-2\langle OU\rangle_0\langle U\rangle_0\right. \\
&+2\langle\mathcal{O}\rangle_0\langle\mathcal{U}\rangle_0^2-\langle\mathcal{O}\rangle_0\langle\mathcal{U}^2\rangle_0\Big)+\cdots  \\
&\equiv\sum_{n=0}^\infty\frac{(-1)^n}{n!}\left\langle\mathcal{OU}^n\right\rangle_0^c.& \begin{pmatrix}5.11\end{pmatrix} 
\end{aligned}
$$
连接平均值（累积量）定义为无微扰期望值的组合. 它们的重要性会在图表示和之后的例子中变得很清楚.

让我们计算Landau-Ginzburg模型的两点关联函数直到参数$u$的一阶（考虑到它们预期的不相关性，我们将忽略高阶相互作用，并且仅保留最低阶高斯项）. 将(5.4)代入到(5.11)得到：
$$
\begin{aligned}
\langle m_\alpha(\mathbf{q})m_\beta(\mathbf{q}^\prime)\rangle & =\langle m_\alpha(\mathbf{q})m_\beta(\mathbf{q}')\rangle_0-u\int\frac{\mathrm{d}^d\mathbf{q}_1\mathrm{d}^d\mathbf{q}_2\mathrm{d}^d\mathbf{q}_3}{(2\pi)^{3d}}  \\
&\times[\langle m_\alpha(\mathbf{q})m_\beta(\mathbf{q}^{\prime})m_i(\mathbf{q}_1)m_i(\mathbf{q}_2)m_j(\mathbf{q}_3)m_j(-\mathbf{q}_1-\mathbf{q}_2-\mathbf{q}_3)\rangle_0 \\
&-\langle m_\alpha(\mathbf{q})m_\beta(\mathbf{q}')\rangle_0\langle m_i(\mathbf{q}_1)m_i(\mathbf{q}_2)m_j(\mathbf{q}_3)m_j(-\mathbf{q}_1-\mathbf{q}_2-\mathbf{q}_3)\rangle_0] \\
&+\mathcal{O}(u^2).& \text{(5.12)} 
\end{aligned}
$$
为了计算$\langle \mathcal{O} \mathcal{U} \rangle_0$我们需要上式中六个$m$相乘的无微扰期望值. 这可以通过使用(5.9)求所有成对收缩的总和得到，一共有15个. 其中三个收缩可以首先将$m_\alpha$和$m_\beta$配对，然后将剩余的四个$m$配对得到. 显然这些收缩与$\langle \mathcal{O} \rangle_0 \langle \mathcal{U} \rangle_0$中相应的部分消去，存活下来的只有将$\mathcal{O}$和$\mathcal{U}$连接起来的收缩项. 这种相消在所有阶都存在，所以$\langle \mathcal{O} \mathcal{U}^n \rangle^c_0$只包含所有$n+1$个算符通过收缩连接的项. $\langle \mathcal{OU} \rangle_0$剩下的12对有两类：
(1) 四个配对涉及将$m_\alpha$和$m_\beta$收缩为具有相同索引的$m$，例如：
$$
\begin{aligned}&\langle m_\alpha(\mathbf{q})m_i(\mathbf{q}_1)\rangle_0\langle m_\beta(\mathbf{q}^{\prime})m_i(\mathbf{q}_2)\rangle_0\langle m_j(\mathbf{q}_3)m_j(-\mathbf{q}_1-\mathbf{q}_2-\mathbf{q}_3)\rangle_0\\&=\frac{\delta_{\alpha i}\delta_{\beta i}\delta_{jj}\left(2\pi\right)^{3d}\delta^d\left(\mathbf{q}+\mathbf{q}_1\right)\delta^d\left(\mathbf{q}^{\prime}+\mathbf{q}_2\right)\delta^d\left(\mathbf{q}_1+\mathbf{q}_2\right)}{\left(t+Kq^2\right)\left(t+Kq^{\prime2}\right)\left(t+Kq_3^2\right)},\end{aligned}
\tag{5.13}
$$
其中我们使用了式(5.6). 在对$i$和$j$求和遍历后，并且对$\mathbf{q}_1$，$\mathbf{q}_2$以及$\mathbf{q}_3$积分后，这些项的贡献为：
$$
-4u \frac{n \delta_{\alpha \beta}(2\pi)^d \delta^d(\mathbf{q} + \mathbf{q}')}{(t + Kq^2)^2} \int \frac{d^d \mathbf{q}_3}{(2\pi)^d} \frac{1}{t + Kq_3^2}.
\tag{5.14}
$$
(2) 八对包含了$m_\alpha$，$m_\beta$和不同下标$m$的缩放：
$$
\begin{aligned}&\langle m_\alpha(\mathbf{q})m_i(\mathbf{q}_1)\rangle_0\langle m_\beta(\mathbf{q}^{\prime})m_j(\mathbf{q}_3)\rangle_0\langle m_i(\mathbf{q}_2)m_j(-\mathbf{q}_1-\mathbf{q}_2-\mathbf{q}_3)\rangle_0\\&=\frac{\delta_{\alpha i}\delta_{\beta j}\delta_{ij}(2\pi)^{3d}\delta^d(\mathbf{q}+\mathbf{q}_1)\delta^d(\mathbf{q}^{\prime}+\mathbf{q}_3)\delta^d(\mathbf{q}_1+\mathbf{q}_3)}{(t+Kq^2)(t+Kq^{\prime2})(t+Kq_2^2)}.
\end{aligned}
\tag{5.15}
$$
与上面相同的操作我们可以得到：
$$
-8u \frac{\delta_{\alpha \beta} (2\pi)^d \delta^d(\mathbf{q} + \mathbf{q}')}{(t + Kq^2)^2} \int \frac{d^d \mathbf{q}_2}{(2\pi)^d} \frac{1}{t + Kq^2_2}. \tag{5.16}
$$
将这些贡献加在一起我们可以得到：
$$
\begin{aligned}\langle m_\alpha(\mathbf{q})m_\beta(\mathbf{q}')\rangle=\frac{\delta_{\alpha\beta}(2\pi)^d\delta^d(\mathbf{q}+\mathbf{q}')}{t+Kq^2}\bigg[1-\frac{4u(n+2)}{t+Kq^2}\int\frac{\mathrm{d}^d\mathbf{k}}{(2\pi)^d}\frac{1}{t+Kk^2}+\mathcal{O}(u^2)\bigg].\end{aligned}
\tag{5.17}
$$


## 5.3    Diagrammatic representation of perturbation theory
微扰论中更高阶的计算变得更加复杂，可以引入图表示来帮助跟踪所有可能的收缩. 要计算$u$中第$p$阶的$\ell$点期望值$\langle \prod_{i=1}^{\ell} m_{\alpha_i}(\mathbf{q}_i) \rangle$，按照以下规则进行：
(1) 按照标记$(\mathbf{q}_i, \alpha_i)$画$\ell$个点，对应着需要的关联函数的坐标. 画$p$个四脚顶点，由内部动量和指数表示，例如$\{ (\mathbf{k}_1, i), (\mathbf{k}_2, i),(\mathbf{k}_3, j),(\mathbf{k}_4, j),\}$. 由于四条腿不等价，因此四脚顶点由用虚线连接的两个实心分支表示. （向高阶相互作用的延伸很简单.）
![[Pasted image 20240412173111.png]]
(2) 图中的每个点现在都对应着$m_{\alpha_i}(\mathbf{q}_i)$的一个因子，并且乘积的无微扰平均值通过Wick定理计算. 这是通过将一个点连接到另一个点的线以所有拓扑上不同的方式成对连接所有外部和内部点来实现的；参见下面的(5).
(3) 每一个这样的图的代数值通过以下规则得到：
(i) 连接一对点的线表示两点平均，即
![[Pasted image 20240412173806.png|210]]
对应于
$$
\delta_{\alpha_1 \alpha_2} (2\pi)^d \delta^d(\mathbf{q}_1 + \mathbf{q}_2)/(t + Kq_1^2)
$$
(ii) 一个顶点
![[Pasted image 20240412174024.png|210]]
代表
$$
u(2\pi)^d\delta^d(\mathbf{k}_1 + \mathbf{k}_2 + \mathbf{k}_3 + \mathbf{k}_4)
$$
（delta函数保证了动量是守恒的.）
(4) 对$4p$个内动量$\{ \mathbf{k}_i \}$积分，并且对$2p$个内指标求和，注意此时每个关闭的loop产生一个因子$\delta_{ii} = n$.
(5) 这里有一个数值因子：
$$
\frac{(-1)^p}{p!}\times\text{number of different pairings leading to the same topology.}
$$
第一项来自于指数的展开；第二项仅仅指出通过对称性相关的图给出相同的结果，并且可以计算一次。
(6) 当计算累积量时，仅需要包含完全连接的图（没有不相交的部分）. 这是一个巨大的简化. 

例如，对于传播子图
![[Pasted image 20240412174654.png|300]]
展开到二阶可以得到：
![[Pasted image 20240412174802.png|600]]

## 5.4 Susceptibility
式(5.17)中的修正项与非微扰值相似并非偶然. 这是因为两点关联函数的形式受到对称性的约束，从恒等式中可以看出
$$
\langle m_{\alpha}(\mathbf{q}) m_{\beta}(\mathbf{q}') \rangle 
= \int d^d \mathbf{x} \int d^d \mathbf{x}' e^{i\mathbf{q}\cdot \mathbf{x} + i\mathbf{q}' \cdot \mathbf{x}'} \langle m_{\alpha}(\mathbf{x}) m_{\beta}(\mathbf{x}') \rangle.
$$
实空间的两点关联函数必须满足平移对称性和旋转对称性，并且（在高温相中）$\langle m_\alpha(\mathbf{x})m_\beta(\mathbf{x}^\prime)\rangle=\delta_{\alpha\beta}\langle m_1(\mathbf{x}-\mathbf{x}^{\prime})m_1(\mathbf{0})\rangle$. 转换为质心和相对坐标，上述积分变为
$$
\begin{aligned}
&\langle m_{\alpha}(\mathbf{q})m_{\beta}(\mathbf{q}^{\prime})\rangle \\
&=\int\mathrm{d}^d\left(\frac{\mathbf{x}+\mathbf{x}'}{2}\right)\mathrm{d}^d\left(\mathbf{x}-\mathbf{x}'\right)\mathrm{e}^{i(\mathbf{q}+\mathbf{q}')\cdot(\mathbf{x}+\mathbf{x}')/2}\mathrm{e}^{i(\mathbf{x}-\mathbf{x}')\cdot(\mathbf{q}-\mathbf{q}')/2}\delta_{\alpha\beta}\langle m_1(\mathbf{x}-\mathbf{x}')\:m_1(\mathbf{0})\rangle \\
&\equiv(2\pi)^d\delta^d(\mathbf{q}+\mathbf{q}^{\prime})\delta_{\alpha\beta}S(q),& \text{(5.19)} 
\end{aligned}
$$
 其中
$$
S(q)=\langle|m_1(\mathbf{q})|^2\rangle=\int\mathrm{d}^d\mathbf{x}\mathrm{e}^{i\mathbf{q}\cdot\mathbf{x}}\langle m_1(\mathbf{x}-\mathbf{x}')\:m_1(\mathbf{0})\rangle 
\tag{5.20}
$$
是散射实验中的可观测量.
从(5.17)式中我们得到
$$
S(q) = \frac{1}{t + Kq^2} \left[ 1 - \frac{4u(n+2)}{t + Kq^2} \int \frac{\mathrm{d}^d\mathbf{k}}{(2\pi)^d} \frac{1}{t + Kk^2} + \mathcal{O}(u^2) \right].
$$
我们可以检查可观测量的倒数的展开
$$
S(q)^{-1}=t+Kq^2+4u(n+2)\int\frac{\mathrm{d}^d\mathbf{k}}{(2\pi)^d}\frac{1}{t+Kk^2}+\mathcal{O}(u^2).
$$
在高温相中，(5.20)表明在$q \rightarrow 0$极限下$S(q)$正是磁化率$\chi$. 出于这个原因$S(q)$有时被$\chi(q)$表示. 因此，磁化率的倒数为
$$
\chi^{-1}(t) = t + 4u(n+2) \int \frac{\mathrm{d}^d \mathbf{k}}{(2\pi)^d} \frac{1}{t + Kk^2} + \mathcal{O}(u^2).
$$
磁化率在$t=0$不再发散，因为
$$
\begin{aligned}
\chi^{-1}(0)& =4u(n+2)\int\frac{\mathrm{d}^{d}\mathbf{k}}{(2\pi)^{d}}\frac{1}{Kk^{2}}=\frac{4(n+2)u}{K}\frac{S_{d}}{(2\pi)^{d}}\int_{0}^{\Lambda}dkk^{d-3}  \\
&=\frac{4(n+2)u}KK_d\left(\frac{\Lambda^{d-2}}{d-2}\right)& (5.24) 
\end{aligned}
$$
是一个有限的数$(K_d \equiv S_d / (2\pi)^d)$. 这是因为在$u$存在时临界温度被降低为一个负值. 修改后的临界点是通过要求$\chi^{-1}(t_c) = 0$获得的，因此可以从方程(5.23)中得到
$$
t_c = -4u(n+2) \int \frac{\mathrm{d}^d \mathbf{k}}{(2\pi)^d} \frac{1}{t_c + K k^2} \approx 
- \frac{4u(n+2)K_d \Lambda^{d-2}}{(d-2)K} \lt 0.
$$
![[Pasted image 20240425113740.png]]
在移动的临界点，扰动的磁化率如何发散？从(5.23)中得到，
$$
\begin{aligned}
\chi^{-1}(t)-\chi^{-1}(t_{c})& =t-t_{c}+4u(n+2)\int\frac{\mathrm{d}^{d}\mathbf{k}}{(2\pi)^{d}}\left(\frac{1}{t+Kk^{2}}-\frac{1}{t_{c}+Kk^{2}}\right)  \\
&=(t-t_c)\left[1-\frac{4u(n+2)}{K^2}\int\frac{\mathrm{d}^d\mathbf{k}}{(2\pi)^d}\frac1{k^2(k^2+(t-t_c)/K)}+\mathcal{O}(u^2)\right].
\end{aligned}
$$
从第一个方程到第二个方程，我们将$t_c$的位置从一个分母更改为另一个分母（？）因为$t_c = \mathcal{O}(u)$，由于这个变化产生的修正只会出现在$\mathcal{O}(u^2)$上. 最后一个积分的维度为$\left[ k^{d-4} \right]$. 对于$d \gt 4$，它由最大动量主导，尺度为$\Lambda^{d-4}$. 对于$2 \lt d \lt 4$，积分在两个极限处收敛，因此其大小由动量标度$\xi^{-1} = \sqrt{(t - t_c) / K}$，可用于使被积函数无量纲. 因此在这些维度上
$$
\chi^{-1}(t) = (t - t_c) \left[ 1 - \frac{4u(n+2)}{K^2} c \left( \frac{K}{t -t_c} \right)^{2 - d/2} + \mathcal{O}(u^2) \right],
$$
其中$c$是个常数. 对于$d \lt 4$，阶数为$u$的修正项会在相变时发散，掩盖了非微扰$\chi$的$\gamma = 1$的奇异性. 因此，微扰级数本质上不适用于描述$d \lt 4$时的磁化率发散. 在微扰地计算其他任何量时也会得出相同的结论. 尽管我们首先将$u$视为微扰参数，但重要的是认识到它不是无量纲的；$u/K^2$有着$(\text{length})^{d-4}$的量纲. 任意量的微扰级数有形式$X(t, u) = X_0(t)[1 + f(ua^{4-d}/K^2, u\xi^{4-d} / K^2)]$，其中$f$是幂级数. 两个长度尺度$a$和$\chi$可用于构造无量纲变量. 由于$\chi$在临界点附近发散，微扰级数存在固有的故障. 有效（无量纲）微扰参数在$t_c$处发散且不小，使其成为本质上无效的展开参数.


## 5.5 Perturbative RG (first order)
最后一节演示了如何以$u$的幂微扰计算与Landau-Ginzburg哈密顿量相关的各种期望值. 然而，微扰级数在接近临界点时本质上是发散的，不能用于表征维度$d \le 4$中的临界行为. Wilson表明可以通过将重整化群和微扰结合成计算临界指数的系统方法. 因此，我们将3.7节中高斯模型的RG计算拓展到Landau-Ginzburg哈密顿量，将$\mathcal{U} = u \int d^d \mathbf{x} m^4$作为一个微扰.
(1) ***粗粒化***：这是RG中最困难的一步. 和之前一样，将涨落分为两部分，
![[Pasted image 20240428103447.png]]
在配分函数中
$$
Z=\int\mathcal{D}\tilde{\vec{m}}(\mathbf{q})\mathcal{D}\vec{\sigma}(\mathbf{q})\mathrm{exp}\left\{-\int_{0}^{\Lambda}\frac{\mathrm{d}^{d}\mathbf{q}}{(2\pi)^{d}}\left(\frac{t+Kq^{2}}{2}\right)\\\left(|\tilde{m}(\mathbf{q})|^{2}+|\sigma(\mathbf{q})|^{2}\right)-\mathcal{U}[\tilde{\vec{m}}(\mathbf{q}),\vec{\sigma}(\mathbf{q})]\right\},
$$
两个模式的集合因为算符$\mathcal{U}$被混合，将$\{ \vec{\sigma}(\mathbf{q}) \}$积分的结果可以写成
$$
\begin{aligned}\text{Z}
=&\int\mathcal{D}\tilde{\vec{m}}(\mathbf{q})\exp\left\{-\int_{0}^{\Lambda/b}\frac{\mathrm{d}^{d}\mathbf{q}}{(2\pi)^{d}}\left(\frac{t+Kq^{2}}{2}\right)|\tilde{m}(\mathbf{q})|^{2}\right\}
\\&\times\exp\left\{-\frac{nV}{2}\int_{\Lambda/b}^{\Lambda}\frac{\mathrm{d}^{d}\mathbf{q}}{(2\pi)^{d}}\ln\left(t+Kq^{2}\right)\right\}\left\langle\mathrm{e}^{-\mathcal{U}\left[\tilde{\vec{m}},{\vec{\sigma}}\right]}\right\rangle_{\sigma}\\
\equiv&\int\mathcal{D}\tilde{\vec{m}}(\mathbf{q})\mathrm{e}^{-\beta\tilde{\mathcal{H}}\left[\tilde{\vec{m}}\right]}.\end{aligned}
$$
这里定义了部分平均值
$$
\langle\mathcal{O}\rangle_\sigma\equiv\int\frac{\mathcal{D}\vec{\sigma}(\mathbf{q})}{Z_\sigma}\mathcal{O}\exp\biggl[-\int_{\Lambda/b}^\Lambda\frac{\mathrm{d}^d\mathbf{q}}{(2\pi)^d}\biggl(\frac{t+Kq^2}{2}\biggr)|\sigma(\mathbf{q})|^2\biggr],
$$
其中$Z_{\sigma}=\int \mathcal{D} \vec{\sigma}(\mathbf{q}) \exp \{ -\beta \mathcal{H}_0[\vec{\sigma}] \}$，是与短波涨落相关的高斯配分函数. 从方程(5.30)我们得到
$$
\tilde{\beta\mathcal{H}}[\tilde{\vec{m}}]=V\delta f_{b}^{0}+\int_{0}^{\Lambda/b}\frac{\mathrm{d}^{d}\mathbf{q}}{(2\pi)^{d}}\left(\frac{t+Kq^{2}}{2}\right)|\tilde{m}(\mathbf{q})|^{2}-\ln\left\langle\mathrm{e}^{-\mathcal{U}\left[\tilde{\vec{m}},\vec{\sigma}\right]}\right\rangle_{\sigma}.
$$
最终表达式可以扰动计算为：
$$
\begin{aligned}\ln\left\langle\mathrm{e}^{-\mathcal{U}}\right\rangle_{\sigma}
=&-\left\langle\mathcal{U}\right\rangle_{\sigma}+\frac{1}{2}\left(\left\langle\mathcal{U}^{2}\right\rangle_{\sigma}-\left\langle\mathcal{U}\right\rangle_{\sigma}^{2}\right)+\cdots\\
&+\frac{(-1)^{\ell}}{\ell!}\times\ell\text{th cumulant of }\mathcal{U}+\cdots\end{aligned}
$$
可以使用前面部分中设置的规则来计算累积量. 例如，在一阶时，我们需要计算
$$
\begin{gathered}
\left\langle\mathcal{U}\left[\tilde{\vec{m}},\vec{\sigma}\right]\right\rangle_{\sigma} =u\int\frac{\mathrm{d}^{d}\mathbf{q}_{1}\mathrm{d}^{d}\mathbf{q}_{2}\mathrm{d}^{d}\mathbf{q}_{3}\mathrm{d}^{d}\mathbf{q}_{4}}{\left(2\pi\right)^{4d}}(2\pi)^{d}\delta^{d}(\mathbf{q}_{1}+\mathbf{q}_{2}+\mathbf{q}_{3}+\mathbf{q}_{4}) \\
\left\langle\left[\tilde{\vec{m}}(\mathbf{q}_1)+\vec{\sigma}(\mathbf{q}_1)\right]\cdot\left[\tilde{\vec{m}}(\mathbf{q}_2)+\vec{\sigma}(\mathbf{q}_2)\right]\right\rangle  \\
\times\left.\left[\tilde{\vec{m}}(\mathbf{q}_{3})+\vec{\sigma}(\mathbf{q}_{3})\right]\cdot\left[\tilde{\vec{m}}(\mathbf{q}_{4})+\vec{\sigma}(\mathbf{q}_{4})\right]\right\rangle_{\sigma}. 
\end{gathered}
$$
以下类型的项是由于扩展乘积而产生的：
![[Pasted image 20240428105900.png]]
每行中的第二个元素是具有给定“对称性”的项数. 这些系数的总和为$2^4 = 16$. 由于平均值$\langle \mathcal{O} \rangle_\sigma$仅涉及短波长涨落，因此仅出现$\vec{\sigma}$的收缩. 由此产生的内部动量从$\Lambda/b$积分到$\Lambda$.
$[1]$没有$\vec{\sigma}$的因子因此等于$\mathcal{U}[\tilde{\vec{m}}]$. 第二项和第五项涉及奇数个$\vec{\sigma}$因此它们的平均值为$0$. $[3]$只有一种收缩，结果为
$$
\begin{align}
&-u\times2\int\frac{\mathrm{d}^d\mathbf{q}_1\cdots\mathrm{d}^d\mathbf{q}_4}{(2\pi)^{4d}}(2\pi)^d\delta^d(\mathbf{q}_1+\cdots+\mathbf{q}_4)\frac{\delta_{jj}(2\pi)^d\delta^d(\mathbf{q}_1+\mathbf{q}_2)}{t+Kq_1^2}\tilde{\vec{m}}(\mathbf{q}_3)\cdot\tilde{\vec{m}}(\mathbf{q}_4)\\
&=-2nu\int_0^{\Lambda/b}\frac{\mathrm{d}^d\mathbf{q}}{(2\pi)^d}|\tilde{m}(\mathbf{q})|^2\int_{\Lambda/b}^\Lambda\frac{\mathrm{d}^d\mathbf{k}}{(2\pi)^d}\frac1{t+Kk^2}.
\end{align}
\tag{5.36}
$$
$[4]$也只有一种收缩，但是这里没有closed loop(因子$\delta_{jj}$)因此没有因子$n$. 项$[6]$中4个$\vec{\sigma}$的各种缩放导致了许多不依赖于$\tilde{\vec{m}}$的项. 我们将这些项的总和表示为$uV\delta f_b^1$. 收集所有这些项，一阶$u$的粗粒化哈密顿量为
$$\begin{aligned}
\tilde{\beta\mathcal{H}}[\tilde{\vec{m}}]=&V\left(\delta f_{b}^{0}+u\delta f_{b}^{1}\right)+\int_{0}^{\Lambda/b}\frac{\mathrm{d}^{d}\mathbf{q}}{(2\pi)^{d}}\left(\frac{\tilde{t}+Kq^{2}}{2}\right)|\tilde{m}(\mathbf{q})|^{2}  \\
&+u\int_0^{\Lambda/b}\frac{\mathrm{d}^d\mathbf{q}_1\mathrm{d}^d\mathbf{q}_2\mathrm{d}^d\mathbf{q}_3}{(2\pi)^{3d}}\tilde{\vec{m}}(\mathbf{q}_1)\cdot\tilde{\vec{m}}(\mathbf{q}_2)\tilde{\vec{m}}(\mathbf{q}_3)\cdot\tilde{\vec{m}}(-\mathbf{q}_1-\mathbf{q}_2-\mathbf{q}_3),
\end{aligned}$$
其中
$$
\tilde{t} = t + 4u (n+2) \int_{\Lambda/b}^{\Lambda} \frac{d^d \mathbf{k}}{(2\pi)^d} \frac{1}{t+Kk^2}
$$
粗粒化哈密顿量因此可以被三个参数$\tilde{t}, \tilde{K}$和$\tilde{u}$描述. 最后两个参数是不变的，
$$
\tilde{K} = K, \text{ and } \tilde{u} = u.
$$
(2) ***重标度***：通过设置$\mathbf{q} = b^{-1} \mathbf{q}'$，以及
(3) ***重整化***：$\tilde{\vec{m}} = z \vec{m}'$得到
$$
\begin{align}
(\beta\mathcal{H})^{\prime}[m^{\prime}]=V\left(\delta f_{b}^{0}+u\delta f_{b}^{1}\right)+\int_{0}^{\Lambda}\frac{\mathrm{d}^{d}\mathbf{q}^{\prime}}{(2\pi)^{d}}b^{-d}z^{2}\left(\frac{\tilde{t}+Kb^{-2}q^{\prime2}}{2}\right)\left|m^{\prime}(\mathbf{q}^{\prime})\right|^{2}\\
+uz^{4}b^{-3d}\int_{0}^{\Lambda}\frac{\mathrm{d}^{d}\mathbf{q}^{\prime}_{1}\mathrm{d}^{d}\mathbf{q}_{2}^{\prime}\mathrm{d}^{d}\mathbf{q}_{3}^{\prime}}{(2\pi)^{3d}}\vec{m}^{\prime}(\mathbf{q}_{1}^{\prime})\cdot\vec{m}^{\prime}(\mathbf{q}_{2}^{\prime})\vec{m}^{\prime}(\mathbf{q}_{3}^{\prime})\cdot\vec{m}^{\prime}(-\mathbf{q}_{1}^{\prime}-\mathbf{q}_{2}^{\prime}-\mathbf{q}_{3}^{\prime}).
\end{align}
$$
重整化哈密顿量的特征是相互作用的三元组$(t', K', u')$，使得
$$
t' = b^{-d} z^2 \tilde{t}, \quad K' = b^{-d-2}z^2K, \quad u' = b^{-3d} z^4 u.
$$
由于在Gaussian模型中有一个固定点$t^* = u^* = 0$，使得我们设置$z = b^{1 + \frac{d}{2}}$，因此$K' = K$. 该点附近$t$和$u$的递归关系由下式给出
$$
\begin{cases}t_b'=b^2\left[t+4u(n+2)\int_{\Lambda/b}^{\Lambda}\frac{\mathrm{d}^d\mathbf{k}}{(2\pi)^d}\frac{1}{t+Kk^2}\right]\\u_b'=b^{4-d}u.\end{cases}
\tag{5.42}
$$
虽然$u$这一阶的递归关系与通过量纲分析获得的递归关系相同，但$t$的递归关系不同. 通过设置$b = e^{\ell}$将离散的递归关系转化为连续微分流量方程是常规的，因此对于一个无限小的$\delta \ell$，
$$
t_{b}^{\prime}\equiv t(b)=t(1+\delta\ell)=t+\delta\ell\frac{\mathrm{d}t}{\mathrm{d}\ell}+\mathcal{O}(\delta\ell^{2}),\quad u_{b}^{\prime}\equiv u(b)=u+\delta\ell\frac{\mathrm{d}u}{\mathrm{d}\ell}+\mathcal{O}(\delta\ell^{2}).
$$
将方程(5.42)展开到$\delta \ell$的一阶，得到
$$
\begin{cases}t+\delta\ell\frac{\mathrm dt}{\mathrm d\ell}=(1+2\delta\ell)\left(t+4u(n+2)\frac{S_d}{(2\pi)^d}\frac{1}{t+K\Lambda^2}\Lambda^d\delta\ell\right)\\u+\delta\ell\frac{\mathrm du}{\mathrm d\ell}=(1+(4-d)\delta\ell)u.\end{cases}
$$
控制$t$和$u$在重标度下演化的微分方程为
$$
\begin{cases}\frac{\mathrm dt}{\mathrm d\ell}=2t+\frac{4u(n+2)K_d\Lambda^d}{t+K\Lambda^2}\\\frac{\mathrm du}{\mathrm d\ell}=(4-d)u.\end{cases}
$$
$u$的递归关系很容易积分得到$u(\ell) = u_0 e^{(4−d) \ell} = u_0 b^{4−d}$. 递归关系可以在不动点$t^* = u^* = 0$附近通过设置$t = t^* + \delta t$和$u^* = u + \delta u$线性化，
$$
\frac{\mathrm{d}}{\mathrm{d}\ell}\begin{pmatrix}\delta t\\\delta u\end{pmatrix}=\begin{pmatrix}2&\frac{4(n+2)K_d\Lambda^{d-2}}{K}\\0&4-d\end{pmatrix}\begin{pmatrix}\delta t\\\delta u\end{pmatrix}.
$$
在递归关系的微分形式中，矩阵的特征值决定了算子的相关性. 由于上述矩阵的一侧元素为零，因此其特征值是对角元素，并且与高斯模型一样，我们可以确定$y_t = 2$，并且$y_u = 4−d$. 该阶的结果与高斯模型的量纲分析所获得的结果相同. 唯一的区别在于特征方向. 指数$y_t = 2$仍然与$u = 0$相关，而$y_u = 4 −d$实际上与方向$t =−4u(n+2)K_d \Lambda^{d−2}/K$相关. 这与从磁化率计算到$u$量级的转变温度的变化一致.
![[Pasted image 20240428122915.png]]
对于$d>4$，高斯不动点只有一个与$y_t$相关的不稳定方向. 因此它正确地描述了相变. 对于$d<4$，它有两个相关方向并且不稳定. 不幸的是，递归关系在这个阶上没有其他固定点，而且我们似乎从微扰RG中学到的东西很少. 然而，由于我们正在处理交替序列，我们可以预期下一阶的递归关系将被修改为
$$
\begin{cases}\frac{\mathrm dt}{\mathrm d\ell}=2t+\frac{4u(n+2)K_d\Lambda^d}{t+K\Lambda^2}-Au^2\\\frac{\mathrm du}{\mathrm d\ell}=(4-d)u-Bu^2,\end{cases}
$$
其中$A$和$B$是正的. 现在在$u^* = (4-d) / B$处有一个额外的固定点. 对于系统微扰理论，我们需要保持参数$u$较小. 因此，新的不动点只能在小$\epsilon = 4 − d$时系统地探索；我们被引导考虑在$d = 4$附近空间维度的扩展！对于在$\mathcal{O}(\epsilon)$处有效的计算，我们必须跟踪$u$的递归关系中的二阶项，但仅跟踪$t$的递归关系中的一阶项. 因此，无需计算上述递推关系中的$A$项. 


## 5.6 Perturbative RG (second order)
二阶$\mathcal{U}$的粗粒化哈密顿量为：
$$
\begin{aligned}\beta\tilde{\mathcal{H}}[\tilde{\vec{m}}]=&V\delta f_{b}^{0}+\int_{0}^{\Lambda/b}\frac{\mathrm{d}^{d}\mathbf{q}}{(2\pi)^{d}}\left(\frac{t+Kq^{2}}{2}\right)\\&|\tilde{m}(\mathbf{q})|^{2}+\langle\mathcal{U}\rangle_{\sigma}-\frac{1}{2}\left(\langle\mathcal{U}^{2}\rangle_{\sigma}-\langle\mathcal{U}\rangle_{\sigma}^{2}\right)+O(\mathcal{U}^{3}).\end{aligned}
$$
为了计算$(\langle \mathcal{U}^2 \rangle_{\sigma} - \langle \mathcal{U} \rangle^2_{\sigma})$，我们需要考虑将两个$\mathcal{U}$分解为$\tilde{\vec{m}}$和$\vec{\sigma}$的所有可能情况. 因为一阶微扰中计算得到每个$\mathcal{U}$可以分解为六种不同的项，所以两个$\mathcal{U}$一共有$36$种可能. 
![[Pasted image 20240429193624.png]]
在这个展开矩阵中，许多矩阵元是$0$或者可以在这个阶段忽略，这主要是出于以下原因：
(1) 所有至少包含类型$[1]$的11个项都为$0$，因为它们不能收缩为一个连通（connected）块，并且在计算累积量时连通块被抵消. 
(2) 另外12项（例如$[2] \times [3]$）涉及奇数个$\vec{\sigma}$，因此由于奇偶性（parity）为$0$
(3) 其中两项，$[2] \times [5]$和$[5] \times [2]$，包含了一个顶点，其中两个$\vec{\sigma}$收缩在一起，剩下$\tilde{\vec{m}}(\mathbf{q}^{<})$和${\vec{\sigma}}(\mathbf{q}^{>})$，由于$\delta$函数的存在，顶点要求四个脚的动量和为$0$，收缩要求其中两个$\sigma$的动量和为$0$，所以要求$\mathbf{q}^< + \mathbf{q}^> = \mathbf{0}$，这是不可能的. 
(4) 项$[3] \times [6]$和$[4] \times [6]$，及其拓扑等价项，有两个$\tilde{\vec{m}}$. 它们包含两个环积分，并且作为系数$\tilde{t}$的修正出现. 我们将用$A$ 表示它们的净效应，如前所述，不需要在这一阶精确了解$A$.
(5) 项$[5] \times [5]$也包含两个$\tilde{\vec{m}}$，然而$[2] \times [2]$包含六个$\vec{m}$. 后者很重要，因为它表明参数空间在这一阶不是封闭的. 即使最初为$0$，在RG下也会生成与$m^6$成比例的项. 事实上，出于动量守恒的考虑，当$\mathbf{q} = 0$时这两项都是$0$，因此分别对$q^2 m^2$和$q^2 m^6$做出贡献.

> [!NOTE] 
> 1. 不考虑$Au^2$的原因是我们希望保持阶数一致. 在之前的结果中我们有
> $$
> \begin{cases}\frac{\mathrm dt}{\mathrm d\ell}=2t+\frac{4u(n+2)K_d\Lambda^d}{t+K\Lambda^2}\\\frac{\mathrm du}{\mathrm d\ell}=(4-d)u.\end{cases}
> $$
> 在这个关系中，由于不动点$u$的阶数为$d = 4 = \epsilon$，所有第二个等式中所有阶数都为$\epsilon^2$，而第一个方程中仅为$\epsilon$，所以在第一个式子里不考虑$Au^2$
> 
> 2. 一切与对称性相符的项，即使一开始没有出现，在RG的过程中也有可能出现

(6) $[6] \times [6]$的贡献是常数，可以被收集为$u^2 V \delta f_b^2$.
(7) 项$[3] \times [3]$，$[3] \times [4]$，$[4] \times [3]$和$[4] \times [4]$的为$\tilde{\vec{m}}^4$贡献，比如$[3] \times [3]$的结果为：
![[Pasted image 20240429201859.png|400]]
$$
\begin{aligned}
\frac{u^{2}}{2}&\times2\times2\times2\int_{0}^{\Lambda/b}\frac{\mathrm{d}^{d}\mathbf{q}_{1}\cdots\mathrm{d}^{d}\mathbf{q}_{4}}{(2\pi)^{4d}}\int_{\Lambda/b}^{\Lambda}\frac{\mathrm{d}^{d}\mathbf{k}_{1}\mathrm{d}^{d}\mathbf{k}_{2}\mathrm{d}^{d}\mathbf{k}_{1}^{\prime}\mathrm{d}^{d}\mathbf{k}_{2}^{\prime}}{(2\pi)^{4d}} \\
&\times(2\pi)^{2d}\delta^d(\mathbf{q}_1+\mathbf{q}_2+\mathbf{k}_1+\mathbf{k}_2)\delta^d(\mathbf{k}'_1+\mathbf{k}'_2+\mathbf{q}_3+\mathbf{q}_4) \\
&\times\frac{\delta_{\alpha\alpha^{\prime}}(2\pi)^{d}\delta^{d}(\mathbf{k}_{1}+\mathbf{k}_{1}^{\prime})}{t+Kk_{1}^{2^{\prime}}}\frac{\delta_{\alpha\alpha^{\prime}}(2\pi)^{d}\delta^{d}(\mathbf{k}_{2}+\mathbf{k}_{2}^{'})}{t+Kk_{2}^{2^{\prime}}}\tilde{\vec{m}}(\mathbf{q}_{1})\cdot\tilde{\vec{m}}(\mathbf{q}_{2})\tilde{\vec{m}}(\mathbf{q}_{3})\cdot\tilde{\vec{m}}(\mathbf{q}_{4}) \\
=&4nu^{2}\int_{0}^{\Lambda/b}\frac{\mathrm{d}^{d}\mathbf{q}_{1}\cdots\mathrm{d}^{d}\mathbf{q}_{4}}{(2\pi)^{4d}}(2\pi)^{d}\delta^{d}(\mathbf{q}_{1}+\mathbf{q}_{2}+\mathbf{q}_{3}+\mathbf{q}_{4})\tilde{\vec{m}}(\mathbf{q}_{1})\cdot\tilde{\vec{m}}(\mathbf{q}_{2})\tilde{\vec{m}}(\mathbf{q}_{3})\cdot\tilde{\vec{m}}(\mathbf{q}_{4}) \\
&\times\int\frac{\mathrm{d}^{d}\mathbf{k}}{(2\pi)^{d}}\frac{1}{(t+Kk^{2})\left(t+K(\mathbf{q}_{1}+\mathbf{q}_{2}-\mathbf{k})^{2}\right)}.& (5.48) 
\end{aligned}
$$
来自项$[3] \times [4]$，$[4] \times [3]$和$[4] \times [4]$的收缩会导出相同的项，只是因子分别为$8$，$8$和$16$. 除了对$\mathbf{q}_1$和$\mathbf{q}_2$的依赖之外，最终结果的形式为$\mathcal{U}[\tilde{\vec{m}}]$. 事实上最后一个积分可以展开为：
$$
f(\mathbf{q}_1+\mathbf{q}_2)=\int\frac{\mathrm{d}^d\mathbf{k}}{(2\pi)^d}\frac{1}{(t+Kk^2)^2}\left[1-\frac{2K\mathbf{k}\cdot(\mathbf{q}_1+\mathbf{q}_2)-K(\mathbf{q}_1+\mathbf{q}_2)^2}{(t+Kk^2)}+\cdots\right].
$$
傅立叶变换回实空间后，我们发现除了$m^4$之外，还有$m^2 (\nabla m)^2$，$m^2 \nabla^2 ,^2$等等.
将这些所有贡献放在一起，$u^2$阶的粗粒化哈密顿量为
$$
\begin{aligned}
\tilde{\beta}_{\mathcal{H}} =& V\left(\delta f_{b}^{0}+u\delta f_{b}^{1}+u^{2}\delta f_{b}^{2}\right)+\int_{0}^{\Lambda/b}\frac{\mathrm{d}^{d}\mathbf{q}}{(2\pi)^{d}}|\tilde{m}(\mathbf{q})|^{2}  \\
&\left[\frac{t+Kq^2}{2}+2u(n+2)\int_{\Lambda/b}^{\Lambda}\frac{\mathrm{d}^d\mathbf{k}}{(2\pi)^d}\frac{1}{t+Kk^2}-\frac{u^2}{2}A(t,K,q^2)\right] \\
&+\int_{0}^{\Lambda/b}\frac{\mathrm{d}^{d}\mathbf{q}_{1}\mathrm{d}^{d}\mathbf{q}_{2}\mathrm{d}^{d}\mathbf{q}_{3}}{(2\pi)^{3d}}\tilde{\vec{m}}(\mathbf{q}_{1})\cdot\tilde{\vec{m}}(\mathbf{q}_{2})\tilde{\vec{m}}(\mathbf{q}_{3})\cdot\tilde{\vec{m}}(\mathbf{q}_{4})\times\left[u-\frac{u^{2}}{2}(8n+64)\right] \\
&\int_{\Lambda/b}^{\Lambda}\frac{\mathrm{d}^{d}\mathbf{k}}{(2\pi)^{d}}\frac{1}{(t+Kk^{2})^{2}}+\mathcal{O}(u^{2}q^{2})\Bigg]+\mathcal{O}(u^{2}\tilde{m}^{6}q^{2},\cdots)+\mathcal{O}(u^{3}).\quad(5.50)
\end{aligned}
$$

