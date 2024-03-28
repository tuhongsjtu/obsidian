https://www.zhihu.com/question/491853457/answer/3200852421
一维相互作用体系可以利用玻色化方法得到低能下的基本性质，但是当前文献中的高维玻色化还不是很成功
## 手性费米子
考虑无自旋二维自由费米气体，其哈密顿量是
$$
\hat{H}_0 = \sum_{\vec{k}} (\frac{k^2}{2m} - \mu) \hat{c}^{\dagger}_{\vec{k}} \hat{c}_{\vec{k}} = A \int \frac{d^2 \vec{k}}{(2\pi)^2} (\frac{\vec{k}^2}{2m} - \mu) \hat{c}^{\dagger}_{\vec{k}} \hat{c}_{\vec{k}}. 
$$
这里$A = L^2$是二维体系的面积，化学势$\mu = \frac{k^2_F}{2m}$，现在考虑到体系的旋转对称性，我们可以采用极坐标，这样$\int d^2 \vec{k} = \int_0^{2\pi} d\theta \int_0^{\infty} kdk$，哈密顿量可以改写为：
$$
\hat{H}_0 = A \int \frac{d \theta}{2\pi} \int \frac{k dk}{2\pi} \left( \frac{k^2}{2m} - \mu \right) \hat{c}^{\dagger}_{\theta, k} \hat{c}_{\theta, k}.
$$
这个形式可以解释为，对于每一个角度$\theta$我们有不同的动量$k$的模式，这些模式由$\hat{c}_{\theta, k}$描述. 
现在我们在费米面附近做低能展开，也就是$\frac{k^2}{2m} - \mu = \frac{k^2 - k_F^2}{2m} = \frac{(k+k_F)(k-k_F)}{2m}$在$k \rightarrow k_F$时可以近似为$v_F(k - k_F)$. 这里我们定义了费米速度$v_F = k_F / m$. 此时体系的哈密顿量近似为：
$$
\hat{H}_0 = A \int \frac{k_F d\theta}{2\pi} \int \frac{dk}{2\pi} v_F(k-k_F) \hat{c}^{\dagger}_{\theta, k} \hat{c}_{\theta, k}.
$$
我们也可以写出对应的离散版本：
$$
\hat{H}_0 = \sum_{\theta} \sum_k v_F(k - k_F) \hat{c}^{\dagger}_{\theta, k} \hat{c}_{\theta, k}.
$$
这里$\sum_{\theta} = Lk_F \int \frac{d\theta}{2\pi}$，$\sum_k = L \int \frac{dk}{2\pi}$. 
类似于一维时候的处理，我们定义相对于费米波矢的动量$\tilde{k} = k-k_F \in [-\Lambda, \Lambda]$，$\Lambda$是远小于$k_F$的动量截断. 为了减少记号，下面的$\tilde{k}$都简记$k$. 这样我们得到线性化近似后的模型：
$$
\hat{H}_0 = \sum_{\theta} \sum_{|k| \lt \Lambda} (v_F k) \hat{c}^{\dagger}_{\theta, k} \hat{c}_{\theta, k}.
$$
如果角度只有两个值$0$和$\pi$，上述哈密顿量就回到了一维费米子线性化后的形式.
$\hat{c}_{\theta, k}$称为***手性费米子***，以强调它的方向依赖特性.

我们知道费米面附近的低能激发主要是粒子-空穴激发，即$\hat{c}^{\dagger}_{\vec{k}+\vec{q}} c_{\vec{k}}$，其对应的能量是$\frac{(\vec{k}+\vec{q})^2}{2m} - \frac{\vec{k}^2}{2m} = \frac{\vec{k} \cdot \vec{q}}{m} + \frac{\vec{q}^2}{2m}$. 可以看到如果粒子-空穴激发对应的动量$|\vec{q}| \ll k_F$，所涉及的粒子在费米面附近$|\vec{k}| \approx k_F$，并且$\vec{q}$与$\vec{k}$方向比较一致，那么$\frac{\vec{q}^2}{2m}$项可以忽略，粒子-空穴激发能量就是线性的，即$\frac{(\vec{k}+\vec{q})^2}{2m} - \frac{\vec{k}^2}{2m} \approx \frac{\vec{k} \cdot \vec{q}}{m}$.
对于当前讨论的手性费米子，其粒子-空穴激发有两种类型，即同手性（$\theta$相同）和不同手性（$\theta$不同）. 前者相当于$\vec{q}$与$\vec{k}$方向完全相同，对应于一维时候$q \rightarrow 0$过程，可以完全按照一维玻色化的方案去做. 后者中$\vec{q}$与$\vec{k}$方向不同，涉及$\hat{c}_{\theta, k}$，$\hat{c}^{\dagger}_{\theta', |\vec{k}+\vec{q}|}$，显然没法套用一维玻色化的技术来处理，这实际上说明这种基于手性费米子的形式在玻色化后很难计入小角度散射的贡献. 这也是这种玻色化方案被大家放弃的基本原因. 


