`sweep.f90`

调用`obser_init_ising`和`obser_init`来初始化各种数组

从1到nsweep进行以下操作：

​		无费米子：调用`ft_ising_sweep`进行metropolis更新。如果开启了lgeometry则调用`geometry_cluster_ising`进行geometry cluster算法更新**但是并不测量**。调用`stglobal_wolff_ising`进行wolff cluster算法更新**且测量**。

​		有费米子：

​		如果定义了lstglobal和llocal，首先调用`ftdqmc_sweep_b0`（相关问题请移步至对应的部分）计算费米子和玻色子的权重，并进行格林函数和Ising模型的metropolis更新。如果开启lgeometry则调用`geometry_cluster`计算费米子和玻色子的权重，进行格林函数和Ising模型的geometry cluster更新，调用`ftdqmc_sweep_0b(lupdate=.true., lmeasure_equaltime=.false.,lmeasure_dyn=.false.)`进行更新，并在最后调用`ftdqmc_stglobal`进行更新与测量**（大部分细节都没搞清楚）**

​		如果只定义了lstglobal，则会先根据lgeometry决定是否调用`geometry_cluster`更新，再进行ftdqmc_stglobal进行更新和测量**（从这里看llocal应该是一个控制local update的逻辑变量）**

​		如果只定义了llocal，则会先调用`ftdqmc_sweep_b0`进行更新和测量，根据lgeometry决定是否调用`geometry_cluster`，根据ltau调用`push_stage` `ftdqmc_sweep_0b` `pop_stage`，然后调用`ftdqmc_sweep_0b`进行更新和测量，但不进行动力学	**为什么是这个过程？**



如果没有费米子会调用`preq_ising`，汇总所有的数据并计算$\chi(0, 0)$和$\chi(\mathbf{q}, i\omega_n)$

如果有费米子会调用`preq`，与`preq_ising`相比**减少了对背景的扣除**





`ft_ising_sweep`

进行Metropolis算法的更新

会根据构型查询wsxsz(id)得到概率，如果随机数小于wsxsz(id)，weight_track会增加log(wsxsz(id))，accm会增加1，logweights_old会增加log(wsxsz(id))，构型发生改变

最后会在main_obs(1)增加dcmplx(accm, dble(2lq*ltrot))

文件尾include了一下stglobal_wolff_ising.f90，geometry_cluster_ising.f90



`geometry_cluster_ising(lmeas)`

进行geometry cluster算法的更新，调用`ftdqmc_calculate_weights(logweights)`计算权重赋值给logweights_new，给main_obs(5)增加dcmplx(1.d0,1.d0)这是因为cluster算法一定会更新，给main_obs(6)增加团簇的大小dcmplx(dble(nstcluster),dble(ltrot*lq))

将logweights_old更新为logweights_new，如果测量开关lmeas为True，调用obser_ising进行测量



`ftdqmc_calculate_weights(logweights)`

计算Ising部分的权重$\exp(\Delta_{\tau} J \sum_l \sum_{\langle i, j \rangle} s_{i, l} s_{j, l} + \gamma \sum_l \sum_i s_{i, l} s_{i, l+1})$并赋值给logweights



`obser_ising`

在obs_bin(1)中增加Ising模型磁化的均值dcmplx( dble(abs(orderbranch))/dble(lq*ltrot), 0.d0 )

在obs_bin(2)中增加空间方向Ising模型的能量

在obs_bin(3)中增加磁场部分的能量dcmplx( -hx*ehx/dble(lq*ltrot), 0.d0 )

调用`tri_order_cal.f90`

首先求出空间方向自旋的均值，方法是对于某一个空间格点求和时间方向并除以ltrot

之后求出各个子晶格上的均值，对于反铁磁和铁磁的不同情况求出相应的序参量

在trimag(1)中储存序参量的模长

在trimag(2)中储存序参量的平方

在trimag(3)中储存序参量的绝对值

在trimag(4)中储存序参量的4次方

在trimag(5)中储存序参量的6次方与cos(6*theta)的乘积，theta是序参量的幅角

在trimag(6)中储存序参量的6次方

**这些数据会在输出的时候进一步被处理**

计算ising模型空间方向的关联并储存在isingzz_corrlt(lq)中

计算ising模型时空方向的关联$\langle s_i(\tau) s_j(0) \rangle$，开关是**lsstau**，储存在isingzztau_corrlt(lq, ltrot)中

计算背景并储存在isingzztau_bg(lq, ltrot)中，计算方法是

```fortran
    do nt = 1, ltrot
        do i = 1, lq
            isingzztau_bg(i,nt) = isingzztau_bg(i,nt) + dble(nsigl_u(i,nt))
        end do
    end do
```



`stglobal_wolff_ising(lmeas)`

进行wolff-cluster算法更新，调用`ftdqmc_calculate_weights( logweights_new )`并赋值给logweights_old，给main_obs(3)增加dcmplx(1.d0,1.d0)，给main_obs(4)增加dcmplx(dble(nstcluster),dble(ltrot*lq))，如果lmeas=True，调用`obser_ising`进行测量



`geometry_cluster(lmeas)`

**line 189**

```fortran
logweightf_old = dble( logweightf_up + logweightf_dn )*2.d0
```

**lwrapu?**	如果rxi大于0自动开启

首先进行Ising模型的geometry cluster算法更新，之后如果存在耦合，即lwrapu为True，调用**ftdqmc_sweep_start_b0？**进行更新并得到新的费米子部分的权重logweightf_new，否则logweightf_new=logweightf_old

调用ftdqmc_calculate_weights计算Ising部分的权重并赋值给logweights_new（注意不是上面的logweightf_new）

之后会进行费米子部分权重的计算**（还没搞懂）**

如果更新成功

​		像无费米子情况一样更新weight_track和main_obs

​		如果开启了lmeas且有耦合，则调用`ftdqmc_sweep_0b(lupdate=.false., lmeasure_equaltime=lmeas, lmeasure_dyn=ltau)`（注意此时是没有更新的）

​		如果开启了lmeas但没有耦合，则调用`ftdqmc_sweep_b0(lupdate=.false., lmeasure_equaltime=lmeas)`和`ftdqmc_sweep_0b(lupdate=.false., lmeasure_equaltime=lmeas, lmeasure_dyn=ltau)`

​		**这里的逻辑没有搞清楚**

如果更新没有成功

```fortran
             ! global update is rejected
             weight_track = logweightf_old + logweights_old
             main_obs(5) = main_obs(5) + dcmplx(0.d0,1.d0)
```

​		并且会返回到原来的Ising构型和权重

```fortran
             ! global update is rejected, you need flip back the spin
             nsigl_u(:,:) = nsigl_u_old(:,:)

             logweightf_up = logwf_up_tmp
             logweightf_dn = logwf_dn_tmp
```

​		如果开启了lmeas，如果存在耦合首先调用`ftdqmc_sweep_start_b0`返回到旧的B矩阵**?**

​		如果不存在耦合，与更新成功情况相同

​		如果不测量，调用`pop_stage`将数组从tmp取回



`ftdqmc_sweep_0b(lupdate, lmeasure_equatime, lmeasure_dyn)`



`preq`

汇总各个进程的数据

susceptibility的定义为
$$
\chi(h, T, \mathbf{q}, \omega_n) = (1/L^2)  \int d\tau \sum _{i, j} e^{i\omega_n \tau - i \mathbf{q} \cdot \mathbf{r}_{ij}} \langle s^z_i(\tau) s_j(0) \rangle
$$
在进程0计算$\chi(0, 0)$和$\chi(\mathbf{q}, i\omega_n)$

进行傅里叶变换的波矢$\mathbf{q}$计算方法为：

```fortran
              qvec = dble(listk(iq,1))*b1_p + dble(listk(iq,2))*b2_p
```

b1_p(2)和b2_p(2)记录了倒格矢，lisk(lq, 2)记录了波矢的大小，单位是倒格矢

***

```fortran
!$OMP PARALLEL &
!$OMP PRIVATE ( itau, imj, zexpiwtqr )
!$OMP DO REDUCTION ( + : sq_ising_qwn_tmp )
```

这些是什么意思

***

傅里叶变换的相位由zexpiwt和zexpiqr得到

最后会把$\chi(0, 0)$和$\chi(\mathbf{q}, i\omega_n)$追加到文件isingzz_corrlt.bin和ising_zztau_corrlt.bin中

自旋的时空关联函数会追加到sstaur_corrlt.bin中

**文件的不同行是来自不同的bin吗？如果是的话，那么nobs是什么**

如果定义了lsstau0r**（这是什么）**,

汇总obs_bin的数据并追加到ener1.bin

汇总并处理trimag的数据并追加到trim.bin

trimag(1)：$\langle m \rangle$

trimag(2)：$\langle m^2 \rangle$

trimag(3)：$\beta L^2 (\langle m^2 \rangle - \langle m \rangle^2) $

trimag(4)：$\langle m^4 \rangle / \langle m^2 \rangle^2$

trimag(5)：$\langle m^6 \cos(6\theta) \rangle / \langle m^6 \rangle$

```fortran
      ! calculate trimag
      trimag(:) = trimag(:) / dble( isize * nobs )
      trimag(3) = (trimag(2)-trimag(3)**2)*dble(lq*beta)
      !trimag(3) = trimag(2) * dble(lq*beta)
      trimag(4) = trimag(4) / (trimag(2)**2)
      trimag(5) = trimag(5) / trimag(6)
```

调用mpi_barrier



`preq_ising`

与`preq`相比增加了对于背景的扣除

```fortran
          !deduct background
          mpi_r2_bg(:,:) = isingzztau_bg(:,:) / dble( isize * nobs )
          do nt = 1, ltrot
          do j = 1, lq
          do i = 1, lq
              imj = latt_imj(i,j)
              mpi_r2(imj,nt) = mpi_r2(imj,nt) - mpi_r2_bg(i,nt)*mpi_r2_bg(j,1)
          end do
          end do
          end do
```

**为什么preq不用扣除背景呢**

将结果追加到sstaur_corrlt_dbg.bin中

**为什么计算傅里叶变换时不用扣除背景的数据**



`prtau`

定义了一个接口

```fortran
  interface
     subroutine fourier_trans_tau(gr,filek)
       complex(kind=8), dimension(:,:) :: gr
       character (40) :: filek
     end subroutine fourier_trans_tau
  end interface
```

`fourier_trans_tau(gr, filek)`会对传入的数组gr(lq, ltrot)做空间上的傅里叶变换，如果定义了`ltauall`，会使用gr所有的数据进行计算，如果没有定义，则只使用gr(lq, ltrot/2)的数据，并将结果写入文件filek中。
$$
\frac{1}{L^2} \sum_{ij} gr \exp(-i \mathbf{q} \cdot \mathbf{r}) 
$$
首先会对数据进行归一，即乘上

```fortran
  znorm = cone / dcmplx( dble(nsweep), 0.d0 )
```

如果定义了`ltauall`，则会汇总所有进程的gtau_up gtau_dn chiszsz chiyjyjyaa chijyjyab chijyjyba chijyjybb并求平均。

***

```fortran
!$OMP PARALLEL &
!$OMP PRIVATE ( itau, imj, zexpiwtqr )
!$OMP DO REDUCTION ( + : chiszsz_qwn_tmp )
```

***

对chiszsz做傅里叶变换储存在chiszsz_qwn_tmp中，并最后输出到chiszsz.bin中，chiszsz本身会输出到szsztaur_corrlt.bin中。

输出chiyjyjyaa chijyjyab chijyjyba chijyjybb，文件名为x+taur_right.bin

如果没有定义，则只会汇总gtau_up(:, ltrot/2)和gtau_dn(:, ltrot/2)并调用fourier_trans_tau输出到gtau_up.bin和gtau_dn.bin中。傅里叶变换结果会输出到gtau_up_halfbeta.bin gtau_dn_halfbeta.bin

