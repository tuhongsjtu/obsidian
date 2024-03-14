##### `ftdqmc_intial.f90`

subroutine `ftdqmc_initial`

* line 15-21	根据时间设置伪随机数种子
* line 23-62    打印文件头、开始时间、并行进程数（如果有）

subroutine `ftdqmc_initial_print`

在$0$进程打印：

* line 73-110	打印文件`ftdqmc.in`的输入参数以及根据输入参数（如果没有将使用程序默认参数）设置的逻辑变量

* line 112-119  根据数组`wrap_step(nst, 2)`打印进行数值稳定的开始和结束时间切片
* line 121-128  根据数组`list(lq, 2)`打印晶格的坐标
* line 130-139  根据数组`distance(lq)`、`distance_len(lq)`和`imjdeg(lq)`打印不同格点到原点的距离以及相同距离的个数
* line 141-149  根据数组

* line 151-153  如果使用棋盘分解（即定义了BREAKUP_T），调用`print_sbondfam`输出每个家族的键的个数与位置



##### `blockc.f90`

定义和初始化模拟中常用的全局变量

* line 2-156        定义模拟中需要的变量，方便其他模块的调用

subroutine `make_tables`

* line 168-169	定义需要传入的模型参数model_para和控制参数ctrl_para的列表
* line 171-214    定义程序的默认参数并使用
* line 216-226    查找是否有文件名为`ftdqmc.in`的文件，如果有，从中读取参数并赋给`model_para`和`ctrl_para`，从而覆盖原有的默认参数
* line 229-256    将参数通过`mpi_bcast`传递给各进程
* line 259-261    `shiftx`和`shifty`是动量转移在k空间基矢的投影，将其转化为实空间基矢的投影`flux_x`和`flux_y`
* line 263-272    根据传入的参数调整需要使用的内部参数。如果费米子和玻色子的耦合强度`rxi`大于$0$，将`lwrapu`和`lupdateu`调为True；如果Hubbard模型的在位相互作用`rj`大于$0$，将`lwrapj`调为True；如果`nsw_stglobal`比$0$大（程序内默认的值是$-1$）并且开启了`lupdateu`，将`lstglobal`调为True；如果`llocal`为假但是`lstglobal`为真，将`nsw_stglobal`设为$1$
* line 273-323    设置delay update需要的block数量`nublock`、数值稳定的次数`nst`、记录数值稳定发生和结束的时间切片数组`wrap_step(2, nst)`以及记录数值稳定发生的时间切片数组`iwrap_nt(nst)`；设置观测量的bin的数量`nmeas_bin`和用于追踪权重变化的`weight_track`
* line 325-331    设置实空间的基矢`a1_p(2)`、`a2_p(2)`和k空间的基矢`b_1(2)`、`b2_p(2)`
* line 333-399    allocate arrays

subroutine `deallocate_tables`



##### `sli.f90`

设置和晶格、k空间有关的数组，所有大于格点尺寸或为负的值均通过函数`npbc`进行平移

`list(lq:2)`	记录格点的坐标，单位是实空间基矢`a1_p(2)`与`a2_p(2)`

`invlist(l, l)`	格点编号的数组。每一个格点的坐标对应`invlist`的行列，`invlist`的值为该格点的坐标，也可用于编号距离。例：`invlist(1, 1)`的值为$1$，所以编号$1$可以用于表示坐标为$(1, 1)$的格点，也可用于表示距离为$\boldsymbol{a}_1 + \boldsymbol{a}_2$

`orblist(ndim)`	

`nnlist(lq, 8)`	$0$记录格点的编号，$1-6$记录三角格点的$6$个近邻，$7-8$记录正方晶格的剩余两个次近邻

`list_plaq(lq, 5)`	

`latt_imj(lq, lq)`	记录任意两个格点之间的距离。行列分别代表两个格点的**编号**，记录的值为两个格点间的距离

`listk(lq, 2)`	记录用于傅里叶变换的波矢$k$，单位是$\boldsymbol{b}_1$和$\boldsymbol{b}_2$
$$
k_1 = 
\left \{
\begin{matrix}
-\frac{L}{2}, 1 - \frac{L}{2} , ..., \frac{L}{2} - 1, \ \ L \text{  is  even};  \\
-\frac{L-1}{2},  - \frac{L-3}{2} , ..., \frac{L-1}{2} , \ \ L \text{  is  odd}.
\end{matrix}
\right.  \\

k_2 = 
\left \{
\begin{matrix}
-\frac{L}{2}, 1 - \frac{L}{2} , ..., \frac{L}{2} - 1, \ \ L \text{  is  even};  \\
-\frac{L-1}{2},  - \frac{L-3}{2} , ..., \frac{L-1}{2} , \ \ L \text{  is  odd}.
\end{matrix}
\right.
$$
`wn(-nuse:nuse)`	记录用于傅立叶变换的频率$\omega_n$，范围是$-\frac{2\pi}{\beta} \text{nuse}, -\frac{2\pi}{\beta} (\text{nuse}-1), ..., \frac{2\pi}{\beta} \text{nuse}$

```fortran
! line 355-357 in blockc.f90
    do i = -nuse, nuse
        wn(i) = 2.d0*dble(i)*pi/beta
```

`zexpiwt(0:ltrot-1, 0:nuse)`	记录用于傅里叶变换的相位$\exp(i \omega_n \tau)$，实际使用的$\omega_n$范围是$0, \frac{2\pi}{\beta}, \cdots, \frac{2\pi}{\beta} \text{nuse}$，$\tau$的范围是$0, \Delta_\tau, \cdots, (\text{ltrot} - 1) \Delta_{\tau}$

`zexpiqr(lq, lq)`	记录用于傅里叶变换的相位$\exp(i \mathbf{q} \cdot \mathbf{r})$，实际使用的时候如果需要$\exp(-i \mathbf{q} \cdot \mathbf{r})$会选择除以数组的元素，$\mathbf{q}$的取值来自于`listk(lq, 2)`，$\mathbf{r}$的取值是所有格点，来自于`1ist(lq, 2)`。第一个维度即行下标代表$\mathbf{r}_{ij}$，另一个维度即列下标代表使用的波矢$\mathbf{q}$，在定义时$\mathbf{r}_{ij}$只包括了格点所在的离散值

subroutine `sli`

* line 14-73		设置与实空间相关的数组`list(lq, 2)`、`invlist(l, l)`、`orblist(ndim)`、`nnlist(lq, 8)`、`list_plaq(lq, 5)`、`latt_imj(lq, lq)`
* line 75-115      设置与傅立叶变换有关的数组`listk(lq, 2)`、`zexpiwt()`、`zexpiqr()`
* line 108-158    设置与距离有关的数组



##### `sbondfam.f90`





##### `salph.f90`

设置有关权重和更新概率计算的数组
$$
H_{sf} = -\xi \sum_i \hat{s}^z_i ( \hat{\sigma}^z_{i1} + \hat{\sigma}^z_{i2} )  \\
\hat{\sigma}^z_{i1} = \frac{1}{2} (\hat{n}_{i\uparrow1} - \hat{n}_{i\downarrow1}) \\
-\Delta_{\tau} H_{sf} = \boldsymbol{c}^{\dagger} D \boldsymbol{c}
$$
耦合项自动满足二次型，并且矩阵$D$是对角的，所以只需要设置矩阵元即可

`xsigp2(-1:1)`	

`xsigm2(-1:1)`	

`dellp2(-1:1, 1)`	

`dellm2(-1:1, 1)`

`xsigma_u_up2(-1:1)`	矩阵元$\exp(\Delta_\tau \xi \hat{s}^z_i)$，$-1$对应自旋向下，$1$对应自旋向上

`xsigma_u_dn2(-1:1)`

`delta_u_up2(-1:1)`	自旋翻转时的变化。$(-1, 1)$对应自旋从下翻转到上的变化$\exp(-\Delta_\tau \xi) / \exp(\Delta_\tau \xi) - 1$，$(1, 1)$对应从上翻转到下的变化$\exp(\Delta_\tau \xi) / \exp(-\Delta_\tau \xi) - 1$

`delta_u_dn2(-1:1)`

`dth`	`tanhdth`	`cothdth`	`gamma_s`

`wsxsz(512)`

`wjs(32)`

`lstglobal`

`lgeometry`

`stbonds_neib(2, 8, lq, ltrot)`

`ratio_nn_st(8)`

subroutine `salph`

* line 16-38		计算并在$0$进程打印与耦合相关的矩阵`xsigp2(-1:1)`、`xsigm2(-1:1)`、`dellp2(-1:1, 2)`、`dellm2(-1:1, 2)`
* line 44-66
* line 83-159      设置`wsxsz(512)`和`wjs(32)`
* line 162-203    如果定义了`lstglobal`和`lgeometry`，设置`stbonds_neib(2, 8, lq, ltrot)`和`ratio_nn_st(8)`，并在$0$进程打印
* line 205-233    在geometry cluster算法中需要使用中心反演对称性，如果定义了`lgeometry`，设置在中心反演对称性下键的映射`sys_map_bond(8)`，并在$0$进程打印

function `gssb(s1, s2, ralpha)`

如果s1等于s2则赋值给`gssb`$\cosh(\text{ralpha})$，否则复制给`gssb`$\sinh(\text{ralpha})$



##### `inconfc.f90`

subroutine `inconfc`

在$0$进程初始化Ising构型，并通过mpi分发给其他进程



##### `thop_mag.f90`





##### `sthop.f90`

在DQMC中，Hubbard模型的动能项为：
$$
H_f = -t \sum_{\langle ij \rangle \lambda \sigma} \hat{c}^{\dagger}_{i \lambda \sigma} \hat{c}_{j \lambda \sigma} + \mathrm{H.c.} = \boldsymbol{c}^{\dagger} T \boldsymbol{c}
$$
如果考虑z-flux或者扭曲边界条件（twisted boundary condition，TBC），需要对hopping参数$t$进行修正
$$
H_f(L) = - \sum_{\langle i, j \rangle \lambda \sigma} t \exp\left[i \frac{2\pi}{\Phi_0} \int_{i}^j \vec{A}_L(\vec{l}) \cdot d \vec{l} \right] \hat{c}^{\dagger}_{i \lambda \sigma} \hat{c}_{j \lambda \sigma} + \mathrm{H.c.}
$$
该子程序的目的就是用于计算矩阵$T$，以及对角化$T$之后得到$\exp(-\Delta_{\tau} T)$，相位的添加需要调用`thop_mag.f90`

`sldqmc_afm_qcp`提供了三种计算方法，棋盘分解（需开启BREAKUP_T）、直接计算以及快速傅里叶变换（需开启FFT），快速傅里叶变换单独放在文件`seth.f90`中

`lfnum(9)`	记录每个family中键的个数

`lbondf(2, lq/3, 9)`	记录每个family的每个键的开始和终止位置

`zthp`	function in `thop_mag.f90`，用于给矩阵元增加来自矢势的相位

`rt`	hopping强度$t$的值

`s_eig_he(ldim, ndim, amat, eval, evec)`	subroutine in `s_matrix.f90`	计算amat的本征值和本征向量存放在`eval`和`evec`中

`urt(2,2,max(lq/3,1),9)`	用于储存每一个family每一个键所对应的hopping矩阵$\exp(-\Delta_{\tau} H_f)$

`urtm1(2,2,max(lq/3,1),9)`	用于储存每一个family每一个键所对应的hopping矩阵$\exp(\Delta_{\tau} H_f)$

`wc(2)` `hlp1(2, 2)`	用于暂时储存`hlp2(2, 2)`的本征值和本征向量

`h0mat`	完整的hopping矩阵，在棋盘分解中会用于计算本征值，在直接计算中会用于输出

`hmat`	完整的hopping矩阵，在直接计算中用于计算本征值和本征向量

`heig` `hvec`	用于暂时储存`hmat`或`h0mat`的本征值和本征向量

`en_free`	$\sum_{n} E_n$，$E_n \le 0$

`h0mat_dn`
`urt_dn`
`urtm1_dn`



subroutine `sthop`

* line 8-97	棋盘分解方法，需开启BREAKUP_T

对于每一个family的每一个键，根据其所属family判断键的开始和结束位置，计算相位与矩阵元，存放在`h0mat`的相应位置，暂时将其和共轭存放在`hlp(2, 2)`的$(1, 2)$和$(2, 1)$

增加来自化学势的部分，由于每个位置要计算$6$次，所以只需要给对角元相应位置减去$\mu/6$

调用`s_eig_he(2,2,hlp2,wc,hlp1)`计算矩阵`hlp2(2, 2)`的本征值和本征向量，分别存放在`wc`和`hlp1(2, 2)`中。计算$\exp(-\Delta_{\tau} H_f)$和$\exp(\Delta_\tau H_f)$的矩阵元存放在`urt(2,2,max(lq/3,1),9)`和`urtm1(2,2,max(lq/3,1),9)`中

调用`s_eig_he(ndim,ndim,h0mat,heig,hvec)`计算完整hopping矩阵的本征值并输出

* line 99-201

如果没有定义`BREAKUP_T`，则会直接计算整个矩阵，计算方法与上面类似

之后会继续计算$\exp(-\Delta_\tau \mathrm{h0mat})$和$\exp(\Delta_\tau \mathrm{h0mat})$并储存在`urt`和`urtm1`中，此时`utr`的维度也会相应的变化，并计算`en_free`



subroutine `set_hopdelta`



##### `seth.f90`

与`sthop`中直接计算hopping矩阵的部分完全相同



##### `setfft.f90`

使用快速傅里叶算法（FFT）计算hopping矩阵的本征值

`h0k(lq)`	记录hopping矩阵的本征值

`exph0k(lq)`	记录$\exp(-\Delta_{\tau} \text{h0k})$

subroutine `setfft`

* line 20-59	使用`seth`计算hopping矩阵，使用FFT算法计算hopping矩阵本征值并储存在`h0k(lq)`中，计算$\exp(-\Delta_{\tau} \text{h0k})$储存在`exph0k(lq)`中。
* line 66-84    输出本征值信息，计算`en_free`





