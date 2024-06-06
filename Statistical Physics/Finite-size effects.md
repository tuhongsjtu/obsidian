# Z-flux
加了z-flux之后打破了哈密顿量的周期性边界条件。这是因为最开始的哈密顿量的边界项其实是$c^{\dagger}_{L} c_{L+1}$和$c^{\dagger}_1 c_0$（以及它们的厄米共轭），但是由于周期性边界条件我们有$c_{L} = c_0$，所以才会有轮胎面的效果。
现在在加了flux之后，每个产生湮灭算符都有了不同的相位，这时候就需要重新规定周期性边界条件。
我们希望哈密顿量满足
$$
[H, T_{L \vec{a}_1}] = [H, T_{L \vec{b}_1}] = 0,
$$
其中$T$是平移算符。在加入flux之后，每个hopping项为
$$
-t \exp\left[{i \frac{2\pi}{\Phi_0} \int_{\vec{i}}^\vec{j}} \vec{A}(\vec{l}) \cdot d \vec{l} \right] c^{\dagger}_{\vec{i}} c_{\vec{j}}
$$
当我们平移$L\vec{a}$时，发现上式变为
$$
-t \exp\left[{i \frac{2\pi}{\Phi_0} \int_{\vec{i} + L\vec{a}}^{\vec{j} + L \vec{a}}} \vec{A}(\vec{l}) \cdot d \vec{l} \right] c^{\dagger}_{\vec{i} + L \vec{a}} c_{\vec{j} + L\vec{a}}
$$
矢势和产生湮灭算符都发生了变化！但我们又想要哈密顿量相同，怎么办？我们观察到矢势部分可以写为
$$
 \int_{\vec{i} + L\vec{a}}^{\vec{j} + L \vec{a}} \vec{A}(\vec{l}) \cdot d \vec{l} = 
 \int_{\vec{i}}^{\vec{j}} \vec{A}(\vec{l} + L \vec{a}) \cdot d \vec{l}
= \int_{\vec{i}}^{\vec{j}} [\vec{A}(\vec{l}) +  \nabla \chi_a(\vec{l}) ] \cdot  d \vec{l}
$$
我们发现第一项已经变成了哈密顿量最开始的样子，下面我们就把多的梯度项扔给产生湮灭算符好了
于是我们定义
$$
c^{\dagger}_{\vec{i} + L \vec{a}} = 
$$