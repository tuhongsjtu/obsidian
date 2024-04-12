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
$$
根据高斯权重的方差，有限尺寸系统的两点期望值可以很快得到：
$$
\langle m_{\alpha}(\mathbf{q}) m_{\beta}(\mathbf{q}') \rangle_0 = \frac{\delta_{\mathbf{q}, -\mathbf{q}'} \delta_{\alpha, \beta} V}{t + Kq^2 + Lq^4 + \cdots}.
$$
在无限尺寸的极限下，系统的谱变为连续，上式变为：
$$
\langle m_{\alpha}(\mathbf{q}) m_{\beta}(\mathbf{q}') \rangle_0 = \frac{\delta({\mathbf{q} + \mathbf{q}'}) \delta_{\alpha, \beta} V}{t + Kq^2 + Lq^4 + \cdots}.
$$
