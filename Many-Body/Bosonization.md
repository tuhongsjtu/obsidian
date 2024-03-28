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
