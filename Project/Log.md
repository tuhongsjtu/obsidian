## 03.07
- [x] ⏫ 数值稳定有问题 ✅ 2024-03-14
![[Pasted image 20240307151530.png]]
参数：nwrap=5
max_wrap_error太大
在global update中，拒绝更新时没有回复状态

- [ ] 🔼 单独的nega测量有问题，会受到其他模块的影响


# 3.26
- [ ] ⏫ EE的scaling行为有些奇怪
- [ ] 🔼 PQMC需要数值稳定

# 无相互作用费米子的negativity
# 1. Half
![[Pasted image 20240320142354.png]]
这张图对比了benchmark（简易的python程序）、free fermion（在程序中设定$\xi=0$）、fermi liquid（$h=5.0 \ \ \xi=1.0$）在子系统尺寸为系统尺寸一半时的scaling行为，系统温度均为$T = 1.0$.
表明FL的行为与无相互作用电子是相似的，并且由于此时外场较大，在平均场下可以认为此时不存在spin和fermion之间的相互作用，在图象上FL此时应该与free fermion非常相近.

benchmark和dqmc的结果是吻合的，可以用benckmark程序来研究更大尺寸时的free fermion行为

## T=1.0
![[Pasted image 20240320143536.png]]
![[Pasted image 20240320143329.png]]
这张图表明随着系统尺寸增大，$R_n / L \propto \alpha$即$R_n \approx \alpha L$，系统中似乎没有观察到$L \log L$行为.

## T=0.5
![[Pasted image 20240320144903.png]]
![[Pasted image 20240320144910.png]]

## T=0.2
![[Pasted image 20240320144950.png]]
![[Pasted image 20240320144957.png]]



# 2. Corner
## T=0.5
![[Pasted image 20240320145743.png]]
![[Pasted image 20240320145752.png]]
## T=0.2
![[Pasted image 20240320150119.png]]
![[Pasted image 20240320150127.png]]
总体上呈现$R_n \propto \alpha L \log L$的scaling关系，但斜率在不断变小，怀疑仍为面积律.



# 相互作用费米子的negativity
大外场的情况已经在无相互作用的half部分中展示相关结果，与无相互作用费米子非常相似
在低外场情况下我们首先关注参数$h = 3.06, T_c = 0.5$
# 1. Half in Finite Temperature Critical Point
![[Pasted image 20240321105458.png]]
![[Pasted image 20240321105504.png]]
我们看到，在子系统为系统一半时，scaling行为在大尺寸下趋于平缓，$R_n \propto \alpha L$

# 2. Corner in Finite Temperature Critical Point
![[Pasted image 20240321105637.png]]
![[Pasted image 20240321105627.png]]
在1/4情况下，scaling满足$R_n \propto \alpha L \log L$

# 3. Corner in Non-Fermi Liquid Region
## 随着温度的变化
![[Pasted image 20240326152926.png]]
![[Pasted image 20240326152948.png]]
## 随着尺寸的变化
![[Pasted image 20240326153012.png]]
![[Pasted image 20240326153018.png]]
![[Pasted image 20240326153106.png]]
![[Pasted image 20240326153125.png]]
![[Pasted image 20240326153042.png]]

## 与其他相的对比
![[Pasted image 20240326154155.png]]
![[Pasted image 20240326154231.png]]

## 3.28
Entanglement entropy and the Fermi surface
这篇文章为费米面为$d-1$维的gapless系统提供了纠缠熵的scaling law公式
$$
S = \frac{L^{d-1}}{(2\pi)^{d-1}} \frac{\log L}{12} \int \int |n_x \cdot n_k| dA_x dA_k.
$$
gapped费米系统和具有更高余维的费米面仍然保持面积律

