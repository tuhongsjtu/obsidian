#### Green's function and energy gap
https://simonverret.github.io/2018/11/15/visual-greens-functions.html

对于自由电子，能量为
$$
\varepsilon(\mathbf{k}) = \frac{\hbar^2 \mathbf{k}^2}{2m}
$$
其格林函数为
$$
G(\mathbf{k}, \omega) = \frac{1}{\omega + i\eta - \varepsilon(\mathbf{k})}
$$$\omega = \epsilon / \hbar$，当取$\hbar = 1$时$\omega = \varepsilon$
![[Pasted image 20231227200845.png|500]]
从这张图中我们可以看到能量与$-\mathrm{Im}G$等价性，$-\mathrm{Im} G$只在曲线关系上不为$0$，系统的能谱也是如此，这也是为什么$\mathrm{Im} G$叫做谱权重.  This actually highlights a more general fact: all the main features of the Green’s function happen at the energies of the system.

回到我们的例子中

![[Pasted image 20231227202011.png|500]]

“在量子临界点($h = h_c$)上和顺磁相($h >h_c$)里，格林函数的虚部$−\mathrm{Im}(G)$都随着松原频率的降低而增大，没有看到任何打开能隙的信号(至少在我们能达到的最低的松原频率$ω ∼ πT$).”
此时这句话就不难理解了，因为格林函数只会在系统有能量分布的地方不为$0$，所以如果存在能隙，应该存在一段格林函数为$0$的区间

##### $i \eta$
https://simonverret.github.io/img/greenEta.gif
在实际中$\eta$的值并不是为$0$的，通过上面链接中的动图我们可以发现$\eta$的作用是改变格林函数能量的展宽. 如果$\eta$为$0$，实部会是一个关于$1/\epsilon$的发散项，虚部会是一个$\delta$函数，从
$$
\lim_{\eta \rightarrow 0} \frac{1}{z + i \eta} \rightarrow \mathcal{P} \frac{1}{z} - i\pi \delta(z)
$$
得到的. 此外能量的展宽对应着更短的寿命. 实际上$\eta$可以被解释为人工散射率，相应的寿命为
$$
\tau = \frac{\hbar}{2 \eta}
$$

##### energy gap
我们考虑一个最简单的二能级哈密顿量
$$
H = 
\begin{bmatrix}
\varepsilon_1 & \Delta \\
\Delta & \varepsilon_2
\end{bmatrix}
$$
现在我们令$\varepsilon_1(k) = k$以及$\varepsilon_2(k) = -k$，它们本身是没有能隙的. 我们知道如果$\Delta$非$0$，它会在能谱上打开一个gap.
由于格林函数为
$$
G(\epsilon) = [\epsilon + i \eta + H]^{-1}
$$
所以如果我们在所有$k$上观察格林函数的矩阵元随着$\Delta$的变化，我们会发现：
* $G$的实部在本征值的位置发散，这通常用另一句话表述：$G$的极点是系统的激发
- Second, the Green’s function has zeros at the position of the crossing levels. That is: Re𝐺11(𝑘,𝜖)ReG11(k,ϵ) (top left colorplot) has zeros (white line) following 𝜀2(𝑘)=−𝑘ε2(k)=−k, whereas Re𝐺22(𝑘,𝜖)ReG22(k,ϵ) has zeros following 𝜀1(𝑘)=𝑘ε1(k)=k.
* $-\mathrm{Im} G$只有在本征值处不为$0$，此外，当gap不为$0$时，$-\mathrm{Im} G$的振幅作为$k$的函数变化，相对大小由本征向量决定
***
Proof: relation between the spectral weight and the eigenvectors
$$
H = U^{\dagger} E U
$$
$$
-\mathrm{Im} G(\epsilon) = - \mathrm{Im} \left\{ U^{\dagger} [(\epsilon + i\eta) - E]^{-1} U \right\}
$$
$$
-\mathrm{Im} G_{ij}(\epsilon) = - \mathrm{Im} \left\{ \sum_n U_{ni}^{*} \frac{1}{\epsilon + i\eta - E_n} U_{nj} \right\}
$$
对于对角元我们可以得到
$$
-\mathrm{Im} G_{ii}(\epsilon) = \sum_n |U_{ni}|^2 \frac{\eta}{(\epsilon -E_n)^2 + \eta^2} = \sum_n |U_{ni}|^2 \pi \delta(\epsilon - E_n)
$$
***
最后，使用格林函数的虚部我们还可以得到态密度
$$
N^{\pm}(\epsilon) = \int dk \left[- \frac{1}{\pi} \mathrm{Im} \left\{ [\epsilon + i \eta - E^{\pm}(k)]^{-1} \right\} \right]
$$

superconductivity and energy gap