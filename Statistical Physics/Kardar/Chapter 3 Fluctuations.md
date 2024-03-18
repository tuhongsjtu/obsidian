## 3.1    Scattering and fluctuations
除了bulk热力学实验以外，散射测量可以用于探测波长$\lambda$量级的微观涨落. 在一个典型的设置中，波矢为$\mathbf{k}_i$的束入射到样品上，并在波矢$\mathbf{k}_s = \mathbf{k}_i + \mathbf{q}$处测量散射强度. 对于弹性散射，$|\mathbf{k}_i| = |\mathbf{k}_s| \equiv k$并且$q \equiv |\mathbf{q}| = 2k \sin \theta$，其中$\theta$为入射波和散射波之间的夹角. 对于散射的标准处理从费米黄金规则开始，通常导出一个以下形式的散射振幅：
$$
A(\mathbf{q}) \propto \langle \mathbf{k}_s \otimes f | \mathcal{U} | \mathbf{k}_i \otimes i \rangle \propto \sigma(\mathbf{q}) \int d^d \mathbf{x} e^{i \mathbf{q} \cdot \mathbf{x}} \rho(\mathbf{x}).
$$
在上面的式子中$| i \rangle$和$| f \rangle$表示样品的起始和最终状态，$\mathcal{U}$是散射势，可以分解为一系列样品导致的散射元素的求和. 振幅具有描述单个元件散射的*局部*形状因子$\sigma(\mathbf{q})$. 处于我们的目的，更有趣的*全局*信息包含在$\rho(\mathbf{q})$中，即散射体$\rho(\mathbf{x})$的全局密度的傅立叶变换. 

适当的散射密度取决于探针的性质. 光散射感知实际原子密度，电子散射测量电荷密度，而中子散射通常用于探测磁化强度. 大多数此类探针实际上并不响应系统快照，而是观察构型的时间平均. 因此观察到的散射强度为：
$$
S(\mathbf{q}) \propto \langle |A(\mathbf{q})|^2 \rangle \propto \langle |\rho(\mathbf{q})|^2 \rangle . 
\tag{3.2}
$$
$\langle \bullet \rangle$表示$\bullet$的热力学平均，由于遍历性大多数时候可以用来替代时间平均值.
式(3.2)表明，均匀的密度只会导致向前散射$\mathbf{q} = \mathbf{0}$，而长波长涨落可以通过在小角度或小$k$下工作来研究. 如果散射是由磁化密度引起的，我们可以使用Landau-Ginzburg哈密顿量来计算其强度. 特定构型的概率为：
$$
\mathcal{P}[\vec{m}(\mathbf{x})] \propto \exp \left\{ -\int d^d \mathbf{x} \left[  
\frac{K}{2} (\nabla m)^2 + \frac{t}{2} m^2 + u m^4
\right] \right\}.
$$
正如之前所讨论的，最可能的构型是*均匀*的，$\vec{m}(\mathbf{x})=\overline{m} \hat{e}_1$，其中$\hat{e}_1$是一个单位矢量（当$t \gt 0$时$\overline{m}=0$，当$t \lt 0$时$\overline{m}=\sqrt{-t/4u}$）. 我们可以设置以下形式来检查这种构型附近的小涨落：
$$
\vec{m}(\mathbf{x}) = [\overline{m} + \phi_l(\mathbf{x})] \hat{e}_1 + \sum_{\alpha=2}^n \phi_{t, \alpha}(\mathbf{x}) \hat{e}_{\alpha}
\tag{3.4}
$$
其中$\phi_l$和$\phi_t$分别表示*纵向*和*横向*涨落. 后者可以沿着垂直于平均磁化强度的任何$n-1$各方向发生.
在替换掉式(3.4)后，展开到二阶的Landau-Ginzburg哈密顿量中的项为：
$$
\begin{align}
(\nabla m)^2 &= (\nabla \phi_l)^2 + (\nabla \phi_t)^2, \\
m^2 &= \overline{m}^2 + 2 \overline{m} \phi_l + \phi_l^2 + \phi_t^2, \\
m^4 &= \overline{m}^4 + 4 \overline{m}^3 \phi_l + 6 \overline{m}^2 \phi_l^2 + 2 \overline{m}^2 \phi_t^2 + \mathcal{O}(\phi_l^3, \phi_t^3),
\end{align}
$$
这导致了一个二次的能量损失
$$
\begin{align}
\beta \mathcal{H} \equiv -\ln \mathcal{P} = V \left( \frac{t}{2} \overline{m}^2 + u \overline{m}^4 \right) + \int d^d \mathbf{x} \left[ \frac{K}{2} (\nabla \phi_l)^2 + \frac{t + 12 u\overline{m}^2}{2} \phi_l^2 \right] \\
+ \int d^d \mathbf{x} \left[ \frac{K}{2} (\nabla \phi_t)^2 + \frac{t + 4u \overline{m}^2}{2} \phi_t^2 \right] + \mathcal{O}(\phi_l^3, \phi_t^3).
\end{align}
$$
对于均匀变形，纵向和横向恢复势（*restoring potentials*，类似于谐振子的弹性势能）具有由下式给出的“刚度常数”：
$$
\frac{K}{\xi_{\ell}^2} \equiv t+12 u \overline{m}^2=\left.\frac{\partial^2 \Psi(m)}{\partial \phi_{\ell}^2}\right|_{\overline{m}}= \begin{cases}t & \text { for } t>0 \\ -2 t & \text { for } t<0\end{cases}
$$
$$
\frac{K}{\xi_{t}^2} \equiv t+4 u \overline{m}^2=\left.\frac{\partial^2 \Psi(m)}{\partial \phi_{t}^2}\right|_{\overline{m}}= \begin{cases}t & \text { for } t>0 \\ 0 & \text { for } t<0\end{cases}
$$
长度尺度$\xi_{\ell}$和$\xi_{t}$的物理意义很快就会变得显而易见. 注意顺磁体的纵向分量和横向分量之间没有区别$(t \gt 0)$. 对于$t \lt 0$时的有序磁体，横向涨落没有恢复力，这对应于上一章中讨论的Goldstone模式. 

下面我们将其推至傅立叶空间中. $\phi(\mathbf{x}) = \sum_{\mathbf{q}} \phi_{\mathbf{q}} e^{i \mathbf{q} \cdot \mathbf{x}} / \sqrt{V}$，一个特定构型的概率为：
$$
\mathcal{P}[\{ \phi_{\ell, \mathbf{q}}; \phi_{t, \mathbf{q}} \}]
\propto \prod_{\mathbf{q}} \exp \left\{ -\frac{K}{2} (q^2 + \xi^{-2}_{\ell}) |\phi_{\ell, \mathbf{q}}|^2  \right\} \cdot \exp \left\{ -\frac{K}{2} (q^2 + \xi^{-2}_{t}) |\phi_{t, \mathbf{q}}|^2 \right\}.
$$
显然每个模式表现为均值为$0$的高斯型随机变量，因此两点关联函数为：
$$
\langle \phi_{\alpha, \mathbf{q}} \phi_{\beta, \mathbf{q}'} \rangle = \frac{\delta_{\alpha, \beta} \delta_{\mathbf{q}, -\mathbf{q}'}}{K(q^2 + \xi_{\alpha}^{-2})}, 
$$
其中下标指的是纵向分量或任何横向分量. 通过使用自旋极化中子源，可以调整相对方向以探测纵向或横向关联. *洛伦兹形式*$S(\mathbf{q}) \propto 1/(q^2 + \xi^{-2})$通常非常适合远离临界点的散射线xing zhua