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
式(3.2)表明，均匀的密度只会导致向前散射$\mathbf{q} = \mathbf{0}$，而长波长涨落可以通过在小角度或小$k$下工作来研究. 如果