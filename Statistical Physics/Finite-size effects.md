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
c^{\dagger}_{\vec{i} + L \vec{a}} = e^{i (2\pi / \Phi_0) \chi_a(\vec{i})} c^{\dagger}_{\vec{i}}
$$
这样我们的哈密顿量就满足平移$L \vec{a}$不变了，同样的还可以定义沿着$L\vec{b}$的规范$\chi_b(\vec{i})$。

需要注意的是，在加了矢势之后，我们的模型已经不是一个有限尺寸的轮胎面了，而是一个无限大的平面，我们的模型只是生活在其中的很小一部分。此时为了让我们的模拟有周期性，我们引入了一个gauge强行将两个位置的产生湮灭算符联系起来，可以想象为取了这个gauge之后，两个位置的波函数相差一个相位，在无限大平面上有很多完全等价的系统块，某个块边界上的费米子hopping到另一个块上时，相当于回到自己的另一个边界但代价就是多一个相位，所以在计算边界的hopping时不仅有相应位置矢势（无限大平面）的相位，还有gauge产生的相位。

然而奇怪的是，按照我的理解，gauge是全局的，也就是说我们不能同时取两个gauge