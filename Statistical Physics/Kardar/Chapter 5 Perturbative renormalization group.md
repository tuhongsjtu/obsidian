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
第一项来自于指数的展开；第二项

