### Bridge Link Method (not work)
用于解决在DQMC模拟中出现的无限方差问题（即使在无符号问题的系统中也会出现相应问题）
方差发散出现的原因是采样过程中**极小**权重构型的出现，换句话说，是我们的样本数不够，没有办法让原本权重很小的构型达到它应有的出现概率？
或者说方差本身可能就是发散的，虽然我们可以得到一个准确的平均值，但是过大的方差导致我们的errorbar不对

toy model的尖峰长尾分布。。。？
对样本的重新分组会降低自关联程度


### Negativity
#### Definition of Negativity
Negativity提供了一种测量纠缠的办法。子系统A的negativity定义为：
$$
\mathcal{N}(\rho) = \frac{|| \rho^{T_A} ||_1 - 1}{2}
$$
其中$T_A$代表关于A的部分转置. $||X||_1$代表$X$的trace norm或者奇异值之和，也就是$|| X ||_1 = Tr |X| = Tr \sqrt{X^{\dagger} X}$. 它的性质为：
(1) 这是一个关于$\rho$的convex function


### Free Fermion Benchmark
为了得到Renyi负性，我们需要得到密度矩阵的部分转置$\rho^{T_1^f}$
在DQMC框架下，密度矩阵部分转置的求解方法为：
$$
\rho^{T_1^f} = \sum_{\mathbf{s}} p_{\mathbf{s}} \rho_{\mathbf{s}}^{T_1^f}
$$
对于特定辅助场构型$\mathbf{s}$的密度矩阵$\rho_{\mathbf{s}}^{T_1^f}$，我们需要格林函数的部分转置$G^{T_1^f}_{\mathbf{s}}$，二者之间的关系为：
$$
\rho^{T_1^f}_{\mathbf{s}} = \det \left[ G^{T_1^f}_{\mathbf{s}} \right] \exp\left\{ - \mathbf{c}^{\dagger} \ln \left[ \left( I - G^{T_1^f}_{\mathbf{s}} \right)^{-1} G^{T_1^f}_{\mathbf{s}} \right] \mathbf{c} \right\}
$$
根据上面的式子，二阶Renyi负性的计算方法为
$$
\begin{align}
e^{-\mathcal{E}_2} 
&= \mathrm{Tr}_{\mathcal{H}} \left[ \left( \rho^{T_1^f} \right)^2 \right] \\
&= \sum_{\mathbf{s}_1 \mathbf{s}_2} p_{\mathbf{s}_1} p_{\mathbf{s}_2} \mathrm{Tr} \left[ \rho^{T_1^f}_{\mathbf{s}_1} \rho^{T_1^f}_{\mathbf{s}_2} \right] \\
&= \sum_{\mathbf{s}_1 \mathbf{s}_2} p_{\mathbf{s}_1} p_{\mathbf{s}_2} \det \left[ G^{T_1^f}_{\mathbf{s}_1} \right] \det \left[ G^{T_1^f}_{\mathbf{s}_2} \right] \\
& \quad \ \ \times \det \left[ I + \left( \left( G^{T_1^f}_{\mathbf{s_1}} \right)^{-1} - I \right) \left( \left( G^{T_1^f}_{\mathbf{s_2}} \right)^{-1} - I \right) \right] \\
&= \sum_{\mathbf{s}_1 \mathbf{s}_2} p_{\mathbf{s}_1} p_{\mathbf{s}_2} \det \left[ G^{T_1^f}_{\mathbf{s}_1} G^{T_1^f}_{\mathbf{s}_2} + \left( I - G^{T_1^f}_{\mathbf{s}_1} \right) \left( I - G^{T_1^f}_{\mathbf{s}_2} \right) \right] \\
&= \sum_{\mathbf{s}_1 \mathbf{s}_2} p_{\mathbf{s}_1} p_{\mathbf{s}_2} \det \left[ g_x(\mathbf{s}_1, \mathbf{s}_2) \right]
\end{align}
$$
当$\det g_x \ge 0$时，我们可以使用incremental算法来计算Renyi负性

### Incremental Algorithm

### Problems
dyn_tau的作用是什么？
n_rpc
由于计算n阶negativity需要n个辅助场，所以创建了n个复制
nAdim
subsystem的格点数量，按照顺序来添加进去

increm_obs_k_1.bin
数字代表了incremental中的第几块