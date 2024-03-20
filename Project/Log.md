## 03.07
- [x] ⏫ 数值稳定有问题 ✅ 2024-03-14
![[Pasted image 20240307151530.png]]
参数：nwrap=5
max_wrap_error太大以及avg_re_logdet_log10error是无穷？

- [ ] 🔼 单独的nega测量有问题，会受到其他模块的影响

## 03.20
无相互作用电子的negativity行为
![[Pasted image 20240320142354.png]]
这张图对比了benchmark（简易的python程序）、free fermion（在程序中设定$\xi=0$）、fermi liquid（$h=5.0 \ \ \xi=1.0$）在子系统尺寸为系统尺寸一半时的scaling行为，系统温度均为$T = 1.0$.
表明FL的行为与无相互作用电子是相似的，并且由于此时外场较大，在平均场下可以认为此时不存在spin和fermion之间的相互作用，在图象上FL此时应该与free fermion非常相近.

benchmark和dqmc的结果是吻合的，可以用benckmark程序来研究更大尺寸时的free fermion行为
![[Pasted image 20240320143536.png]]
![[Pasted image 20240320143329.png]]
这张图表明随着系统尺寸增大，$R_n / L \propto \alpha$即$R_n \approx \alpha L$，系统中似乎没有观察到$L \log L$行为.
