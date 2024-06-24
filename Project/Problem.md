# disorder的自能确实不是单调的
![[Pasted image 20240624121937.png|600]]

# 直接扣除无disorder自能的合理性
![[Pasted image 20240624113808.png|500]]
大N理论中的热涨落贡献也来自于玻色自能中$\Omega_m = 0$的部分，所以如果0频率玻色自能不发生变化，热涨落贡献就不会变化
![[Pasted image 20240624121621.png|500]]
在加入disorder后，完整的玻色自能为
![[Pasted image 20240624114032.png|700]]
由此问题变成了，多出的项$g'^2 G(-\tau, \mathbf{r} = 0) G(\tau, \mathbf{r}=0) \delta^2(\mathbf{r})$是否会对$\Pi(\mathbf{q}, 0)$产生贡献。对这一项做傅里叶变换我们可以得到
$$
\Pi_{g'}(\mathbf{q}, i\Omega_m) = -g'^2 \sum_{\omega_n} G(\omega_n, \mathbf{r}=0) G(\omega_n + \Omega_m, \mathbf{r}=0)
$$
这个积分Sachdev已经帮我们做好了，虽然这个式子是在考虑disorder potential的情况下得到的，但是Sachdev说这个式子在只有disorder coupling的情况下是不变的？
![[Pasted image 20240624114507.png|]]
![[Pasted image 20240624114521.png|300]]
这个积分的问题是，为什么$\Gamma$在积分之后就没有了
所以如果考虑到这个形式，thermal part的确是不会发生变化的。

现在考虑quantum part，$\Sigma_g$是一个非常复杂的形式，暂时还没有让它退回到和Eliashberg完全相同的情况。Sachdev在做这一部分时，忽视了$\Pi_{g'}$的贡献，所以应该完全退回到没有$g'$的情况？没有$g'$的处理也是完全看不懂
![[Pasted image 20240624120422.png|800]]
这积分是怎么做出来的？
对于不同的T，quantum part还有不同的形式？
![[Pasted image 20240624120631.png]]
不过综合以上，尽管我们不能恢复到原来的Eliashberg理论，但至少可以通过有无disorder的差得到额外的一项$\Sigma_{g'}$

大N理论中的一些问题：
为什么$\varepsilon(k) - \mu = k_x + k_y^2$？
$\mathrm{sgn}(\omega_n - \mathrm{Im}[\Sigma(k, i\omega_n)]) = \mathrm{sgn}(\omega_n)$？
在临界区域$M^2 \sim T$？
