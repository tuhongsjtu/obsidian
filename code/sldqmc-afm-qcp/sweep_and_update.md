`ftdqmc_sweep_start_0b`

用于初始化数值稳定中使用的QDT矩阵、更新和测量中使用的等时格林函数

`nst`	数值稳定的次数

`llocal`	local update的开关

`logweightf_up`	费米子部分权重的对数

`grup(ndim, ndim)`	上自旋格林函数

`Ust_up(ndim, ndim, 0:nst)` `Dst_up(ndim, 0:nst)` `Vst_up(ndim, ndim, 0:nst)`	记录每次数值稳定的QDT矩阵

`logdetQst_up(nst)`	记录$\log \det Q$

`UR_up(ndim, ndim)` `DRvec_up(ndim)` `VR_up(ndim, ndim)`	设置矩阵$Q_R$ $D_R$ $T_R$

`green_equaltimebb()`	计算等时格林函数$G(\beta, \beta)$

`Bdtau1_up(ndim, ndim)`	用于计算矩阵$B(\beta, 0)$

`s_invlu_z(ndim, zmat)`	subroutine in `s_matrix.f90`	使用LU算法计算`ndim`维矩阵`zmat`的逆矩阵，并赋值给`zmat`



* line 486-510	

如果数值稳定步数大于`0`，则会初始化在数值稳定中需要使用的`grup(ndim, ndim)` 、$\tau=0$时刻的`Ust_up(:, :, 0)` `Dst_up(:, 0)` `Vst_up(:, :, 0)`设置为单位阵，将$\tau=0$时刻的`logdetQst_up(0)`设置为$0$

从$1$到$\text{nst}$，调用`ftdqmc_stablize_0b_svd(n)`，从$n$时刻的QDT矩阵得到$n+1$时刻的QDT矩阵

* line 512-529

将$Q_R$ $D_R$ $T_R$设置为$\mathrm{nst}$时刻的UDV矩阵，将`logdetQR_up`设置为$\mathrm{nst}$时刻的`logdetQst_up(nst)`，调用`green_equaltimebb`

* line 567-582

如果不需要数值稳定，且定义了`llocal`，首先将`Bdtau1_up(:, :)`和`Bdtau1_dn(:, :)`设置为单位阵，调用`Bmat_tau_R( ltrot, 1, Bdtau1_up, Bdtau1_dn )`直接更新到$\tau = \beta$时刻并为对角元加$1$计算$1+B(\beta, 0)$。调用`s_invlu_z( ndim, Bdtau1_up )`使用LU分解算法计算$G(\beta, \beta) = [1 + B(\beta, 0)]^{-1}$并赋值给`grup(:, :)`

* line 584-590

如果不需要数值稳定，也没有定义`llocal`，直接调用`Bmat_tau_R( ltrot, 1, grup, grdn)`计算$G(\beta, \beta) = 1 + B(\beta, 0)$



`ftdqmc_stablize_0b_svd(n)`

根据第$n-1$次数值稳定的QDT矩阵得到第$n$次的QDT矩阵

`Bmat_tau_R( nt1, nt2, bmat_up, bmat_dn )`	subroutine in `ftdqmc_core.f90`	B(tau1,tau2) * bmat_up make sure nt1 > nt2

`s_zgeQRPT_logdetQ(rdim, cdim, amat, qmat, rmat, jpvt, zlogdet)`	subroutine in `s_matrix.f90`	进行QR分解，计算$\log \det Q$

`s_invdiag_d_x_zr( ndim, dvec, Amat, Bmat )`	subroutine in `s_matrix.f90`	将矩阵`Amat`分解为对角元矩阵`dvec`和`Bmat`的乘积

`s_zmp(rdim,cdim,amat,jpv)`	返回`amat`$\times$`jpv`

`s_zmcpt(ndim,ndim,Btmp,jpvt)`	将`Btmp`按照列的norm进行排列，返回排列好的`Btmp`和置换矩阵`jpvt`

 `s_z_x_diag_d( ndim, Amat, dvec, Bmat )`	计算复矩阵`Amat`和实对称矩阵`dvec`的乘积并储存在`Bmat`中



line 184-188

首先令`Bdtau1_up(:, :)`为第$n-1$次数值稳定时刻的Q矩阵`Ust_up(:, :, n-1)`，使用`Bmat_tau_R( wrap_step(2,n), wrap_step(1,n), Bdtau1_up, Bdtau1_dn )`得到$B(n \times \mathrm{nwrap}, (n-1) \mathrm{nwrap}) Q$

line 190-218

如果$n=1$，也就是我们刚刚做第一次数值稳定，那么原始的QDT矩阵全是单位阵。调用`s_zgeQRPT_logdetQ(ndim, ndim, Bdtau1_up, Umat2, Vtmp, jpvt, logdetQst_up(n) )`进行QR分解并计算$\log \det Q$，调用`s_invdiag_d_x_zr( ndim, Dvec2, Vtmp, Vmat2 )`将`Vtmp2`分解为对角元矩阵`Dvec2`和`Vmat2`，调用`s_zmp(ndim,ndim,Vmat2,jpvt)`

line 220-265

如果不是，我们将读取$n-1$时刻的D矩阵`Dvec1(:) = Dst_up(:, n-1)`和V矩阵`Vmat1(:,:) = Vst_up(:,:,n-1)`。之后调用`s_z_x_diag_d(ndim,Bdtau1_up,Dvec1,Btmp)`计算矩阵乘积$B(n \times \mathrm{nwrap}, (n-1) \mathrm{nwrap}) Q_{n-1} D_{n-1}$并存放在`Btmp`中

调用`s_zmcpt(ndim,ndim,Btmp,jpvt)`，

调用`s_zgeQR_logdetQ(ndim,ndim,Btmp,Umat2,Vmat2,logdetQst_up(n))`进行QR分解并计算$\log \det Q$，调用`s_invdiag_d_x_zr( ndim, Dvec2, Vmat2, Vtmp )`将`Vmat2`分解为对角元矩阵`Dvec2`和`Vtmp`，

调用`call s_zpm(ndim,ndim,jpvt,Vmat1)`

调用`zgemm('n','n',ndim,ndim,ndim,cone,Vtmp,ndim,Vmat1,ndim,czero,Vmat2,ndim)`得到`Vmat2`$=$`Vtmp`$\times$`Vmat1`

line 286-288

将新得到的QDT矩阵`Umat2(:,:)` `Dmat2(:)` `Vmat2(:,:)`复制给`Ust_up(:, :, n)` `Dst_up(:,n)` `Vst_up(:,:,n)`



`s_zgeQRPT(rdim, cdim, amat, qmat, rmat, jpvt)`

line 1136-1146	workspace query

work的尺寸是$\max(1, \text{lwork})$，但是由于我们并不知道`lwork`应该设置为多少，所以如果传入的`lwork`为$-1$，此时我们并不会进行QR分解，而是只计算`work`的最佳尺寸，并将尺寸储存在`work`的第一个位置

* line 1148-1161	QR分解

* line 1163-1177	得到R矩阵

* line 1179-1196	得到Q矩阵的reflector并储存在`qmat`中

* line 1198-1218	首先进行workspace query，再通过`zungqr`从reflector得到Q矩阵



`s_zgeQRPT_logdetQ(rdim, cdim, amat, qmat, rmat, jpvt, zlogdet)`

计算$\log \det Q$版本的`s_zgeQRPT`





`green_equaltimebb( n, ndm, ure, dre, vre, logdetqr, gtt, logweightf, infoe )`

计算$G(\beta, \beta)=[(D^{\mathrm{max}}_{R})^{-1} (Q_R)^{-1} + D^{\mathrm{min}}_{R} T_R]^{-1} (D^{\mathrm{max}}_R)^{-1} Q^{-1}_R$，计算方法与`green_equaltime00`类似



`mmuul(a_up, a_dn, nf, ntau, nflag)`

nflag=3：左乘耦合项$\exp(-\Delta_{\tau} H_{sf})$
$$
H_{sf} = -\xi \sum_{i} \hat{s}^z_i (\hat{\sigma}^z_{i1} + \hat{\sigma}^z_{i2})
$$
耦合项是二次对角的且只依赖于自旋$\hat{s}^z_i$，所以在实际运算中，我们只需要知道两个自旋所对应的矩阵元即可。相关矩阵元储存在`xsigma_u_up(-1:1)`中

```fortran
  ! line 68-71 in salph.f90
  ! onsite
  ! spin up, positive coupling
  xsigma_u_up(-1) = dcmplx( dexp(  dtau * rxi * ( -0.5d0 ) ), 0.d0 )  ! -1.d0 is the field, 0.5 is from fermion spin s=1/2 
  xsigma_u_up( 1) = dcmplx( dexp(  dtau * rxi * (  0.5d0 ) ), 0.d0 )  !  1.d0 is the field, 0.5 is from fermion spin s=1/2
```



`Bmat_tau_RH( nt1, nt2, bmat_up, bmat_dn )`

左乘$B^{\dagger}(\tau_1, \tau_2) = \prod_{n=n_1}^{n=n_2} \exp(-\Delta_{\tau} H_f^{\dagger}) \exp(-\Delta_{\tau} H_{sf}^{\dagger})$，$n_1 \Delta_{\tau} = \tau_1$，$n_2 \Delta_{\tau} = \tau_2$，$\tau_1 \gt \tau_2$



`ftdqmc_stablize_b0_svd(n)`

定义B矩阵为n时刻的U矩阵

```fortran
      Bdtau1_up(:,:) = Ust_up(:,:,n)
      Bdtau1_dn(:,:) = Ust_dn(:,:,n)
```

调用Bmat_tau_RH( wrap_step(2,n), wrap_step(1,n), Bdtau1_up, Bdtau1_dn )，计算$B^{\dagger}(1+(n-1) n_\text{wrap}, n \times n_\text{wrap}) U$

如果此时$n \neq nst$，放在从beta更新到0的框架下，即不是第一次做数值稳定，我们将从n时刻的UDV矩阵得到n-1时刻的UDV矩阵

​		调用`s_zgeQRPT_logdetQ(ndim, ndim, Bdtau1_up, Umat2, Vtmp, jpvt,logdetQst_up(n-1))`进行QR分解，分别储存在Umat2和Vtmp中，并计算log Q储存在logdetQst_up中

​		调用`s_invdiag_d_x_zr( ndim, Dvec2, Vtmp, Vmat2 )`将Vtmp分解为对角元矩阵Dvec和Vmat2

​		调用`s_zmp`，**不知道功能是什么**

如果此时正好为nst，我们没有可调用的n+1时刻的矩阵，所以直接读取

```fortran
          Dvec1(:)   = Dst_up(:,n)
          Vmat1(:,:) = Vst_up(:,:,n)
```

​		调用`s_z_x_diag_d(ndim,Bdtau1_up,Dvec1,Btmp)`得到Bdtau1_up和Dvec1的乘积并储存在Btmp中

​		调用`s_zmcpt(ndim,ndim,Btmp,jpvt)`	**不清楚**

​		调用`s_zgeQR_logdetQ(ndim,ndim,Btmp,Umat2,Vmat2,logdetQst_up(n-1))`

​		调用`s_invdiag_d_x_zr( ndim, Dvec2, Vmat2, Vtmp )`，与之前的操作类似，将Vmat2分解为对角元矩阵Dvec和Vtmp

​		调用`s_zpm(ndim,ndim,jpvt,Vmat1)`	**也是不清楚，而且不知道为什么调用Vmat1**

​		调用`zgemm('n','n',ndim,ndim,ndim,cone,Vtmp,ndim,Vmat1,ndim,czero,Vmat2,ndim)`得到Vmat2 = Vtmp + Vmat1

将得到的n-1时刻的矩阵赋值

```fortran
      Ust_up(:,:,n-1) = Umat2(:,:)  ! note we have Umat2^+ and Vmat2^+
      Dst_up(:,n-1)   = Dvec2(:)
      Vst_up(:,:,n-1) = Vmat2(:,:)
```



`green_equaltime00( n, ndm, vle, dle, ule, logdetql, gtt, logweightf, infoe )`

调用`s_dvec_min_max(ndm, dle, dlmax, dlmin)`将对角矩阵dle分解为dlmax和dlmin
$$
G(0, 0) = \Q_L (D^{\mathrm{max}}_L)^{-1} [\Q_L (D^{\mathrm{max}}_L)^{-1} +  \mathbb{T}^{\dagger}_L D_L^{\mathrm{min}}]^{-1}
$$
计算$[\cdots]$并存放在dvvdtmp中

调用`s_inv_logdet_lu_z(ndm,dvvdtmp,zlogdet_tmp)`使用LU分解计算$[\cdots]^{-1}$以及计算$\log \det [\cdots]$

调用`s_v_invd_u( ndm, ule, dlmax, dvvdtmp, gtt )`计算$G(0, 0)$并存放在gtt中

由于费米子构型的权重为$\omega_f[\mathcal{C}] = \det(1 + B_{\boldsymbol{s}}(\beta, 0))$，格林函数的定义为$G(\tau, \tau) = [1 + B_{\boldsymbol{s}}(\tau, 0) B_{\boldsymbol{s}}(\beta, \tau)]^{-1}$，因此零时格林函数$G(0, 0) = [1 + B_{\boldsymbol{s}}(\beta, 0)]^{-1}$的行列式刚好是构型权重的倒数，可以顺势方便地计算构型权重。

```fortran
      logweightf = -logdetql + zlogdet_tmp + dcmplx(rlogdet_tmp,0.d0)
```

**$G(\beta, \beta)$应该也可以干一样的事**



`ftdqmc_sweep_start_b0`

如果数值稳定的步数nst大于0：

​		首先将$\tau = \beta$时刻的VDU矩阵（讲义中的TDQ矩阵）和logdetQst设为0，logdetQst是Q矩阵的行列式的对数，会在计算格林函数和构型权重时用到

​		从nst开始到1，调用`ftdqmc_stablize_b0_svd(n)`，根据n时刻的UDV矩阵计算n-1时刻的UDV矩阵和logdetQst

​		在$\tau=0$时刻调用`green_equaltime00( nst, ndim, VL_up, DLvec_up, UL_up, logdetQL_up, grup, logweightf_up, info )`计算构型权重和0时刻的等时格林函数，VL DL UL对应0时刻的VDU矩阵

如果数值稳定的步数为0，将不会使用QR分解等方法

​		如果定义了llocal，仍然会进行更新，使用`Bmat_tau_R( ltrot, 1, Bdtau1_up, Bdtau1_dn )`直接更新到0时刻，得到$1 + B(\beta, 0)$，使用`s_invlu_z( ndim, Bdtau1_up )`方法得到0时刻格林函数$[1 + B(\beta, 0)]^{-1}$并将其赋值给grup

**下面这里不是很理解**

​		如果没有定义llocal，则格林函数为$1 + B(\beta, 0)$



`obser_equaltime(nt)`

首先会根据$\langle c_i c^{\dagger}_j \rangle$计算$\langle c^{\dagger}_i c_j \rangle$

```fortran
    do i = 1,ndim
       xi = 1.d0
       if (orblist(i) == 2 ) xi = -1.d0
       do j = 1,ndim
          xj = 1.d0
          if (orblist(j) == 2 ) xj= -1.d0
          grdn (i,j) = dcmplx(xi*xj, 0.d0) * dconjg ( grup (i,j) )
          grdnc(i,j) = dcmplx(xi*xj, 0.d0) * dconjg ( grupc(i,j) )
       enddo
    enddo
```

**这一段没看懂**

测量总占据数zne并增加到obs_bin(1)中

```fortran
    ! zne
    zne = czero
    do i = 1, ndim
        zne = zne + grupc(i,i) + grdnc(i,i)
    end do
    obs_bin(1) = obs_bin(1) + zne
```

测量自旋平均值并增加到obs_bin(2)

测量上自旋和下自旋的占据数，作为实部和虚部增加到obs_bin(3)中

```fortran
    obs_bin(3) = obs_bin(3) + dcmplx(rne_up, rne_dn)
```

测量动能$-t \sum_{\alpha, \langle i, j \rangle} (\langle c^{\dagger}_{i \alpha} c_{j \alpha} \rangle + \langle c^{\dagger}_{j \alpha} c_{i \alpha} \rangle) = -t N_f \sum_{\langle i, j \rangle} (G^c_{ij} + G^c_{ij})$并增加到obs_bin(4)中

```fortran
    do n = 1,lq

       i1 = n
       i2 = nnlist(i1,1)
       i3 = nnlist(i1,6)
       i4 = nnlist(i1,2)

       zx = h0mat(i1,i2)
       zy = h0mat(i1,i4)
       zz = h0mat(i1,i3)
       zkint = zkint +        zx *  grupc(i1,i2) + &
                       dconjg(zx) * grupc(i2,i1)
       zkint = zkint +        zy *  grupc(i1,i4) + &
                       dconjg(zy) * grupc(i4,i1)
       zkint = zkint +        zz *  grupc(i1,i3) + &
                       dconjg(zz) * grupc(i3,i1)
```

**377行**

```fortran
        zkint = zkint + dcmplx(-4.0*rt,0.d0) * ( grupc(1,1) + grdnc(1,1) )
```

**381行**

```fortran
    obs_bin(4) = obs_bin(4) + zkint + dconjg(zkint)  ! layer 1 and layer 2
```

**layer1和layer2为什么是互为共轭的关系**

测量耦合的能量$\frac{1}{2}\xi s_i ( n_{i \uparrow} - n_{i \downarrow} )$并增加到obs_bin(5)中

测量自旋相互作用能量并增加到obs_bin(6)中

```fortran
    zejs = dcmplx( dble(ijs)*(-js), 0.d0 )
    obs_bin(6) = obs_bin(6) + zejs
```

测量外加磁场的能量并增加到obs_bin(7)中

```fortran
    obs_bin(7) = obs_bin(7) + dcmplx( -hx*ehx, 0.d0 )
```

调用tri_order_cal.f90进行序参量的测量

```fortran
    trimag(1)=trimag(1)+am
    trimag(2)=trimag(2)+am**2
    trimag(3)=trimag(3)+dble(abs(am))
    trimag(4)=trimag(4)+(am)**4
    trimag(5)=trimag(5)+(am**6)*dcos(6*theta)    
    trimag(6)=trimag(6)+am**6
```

**最后输出的时候还会对数据进行处理**

进行$\langle S(\vec{r}) S(0) \rangle$	$\langle S(\vec{r}, \tau) S(0, 0) \rangle$和背景强度的测量

```fortran
    do n = 1, ltrot
        do i = 1, lq
            isingzztau_bg(i,n) = isingzztau_bg(i,n) + dble(nsigl_u(i,n))
        end do
    end do
```



`upgradeu.f90`

```fortran
  do i4 = 1,lq
     nrflip = 1

     del44_up   =  delta_u_up( nsigl_u(i4,ntau), nrflip )
     ratioup = dcmplx(1.d0,0.d0) + del44_up * ( cone - green_up(i4,i4) )
```

**为什么ratio是这个**

```fortran
     ratiotot = (ratioup*ratiodn)*dconjg(ratioup*ratiodn) * wsxsz(id) !* deta_u( nsigl_u(i4,ntau), nrflip )
```

计算ratio的绝对值，并扔一个随机数

如果更新成功，更新构型的权重

```fortran
        weight_track = weight_track + log( ratio_re_abs )
#IFDEF SPINDOWN
          logweightf_old = logweightf_old + log( (ratioup*ratiodn)*dconjg(ratioup*ratiodn) )
#ELSE
          logweightf_old = logweightf_old + log( ratioup*dconjg(ratioup) )
#ENDIF
          logweights_old = logweights_old + log( wsxsz(id) )
```

更新格林函数，并在main_obs(1)中增加更新成功的位点数

**updateu**的细节



`ftdqmc_sweep_b0(lupdate, lmeasure_equaltime)`

把$\tau = \beta$时刻的VDU矩阵设置为单位矩阵，把logdetQst设置为0

```fortran
      nt_ob = ceiling( spring_sfmt_stream() * ltrot )
```

这一行的意思大概是，用于测量观测量的时间切片是随机扔出来的？

```fortran
          ! obser
          if( lmeasure_equaltime .and. ( abs(nt-nt_ob) .le. obs_segment_len .or. abs(nt-nt_ob) .ge. (ltrot-obs_segment_len) ) ) then
             call obser_equaltime(nt)
          end if
```

如果时间切片在nt_ob的左右obs_segment_len范围内，则会调用obser_equaltime(nt)。片段条件是为了防止扔出的时间切片过于靠近边缘导致所取样本变少，所以将超过范围的片段通过周期性边界条件进行平移

进行更新

如果定义了updateu（耦合rxi$\xi$大于0时自动开启）：

​		如果定义了lupdate（函数的内置变量，在调用函数时决定）调用`upgradeu(nt grup, grdn)`更新构型和格林函数

​		**如果定义了lupdatej**

​		如果下一步（时间n=nt-1）就要做数值稳定

```fortran
if ( (iwrap_nt(nt-1) .gt. 0 .and. nt.ne.ltrot) .or. ( nt.eq.1 .and. nst .gt. 0 ) ) then
```

​		将UR DR VR logdetQR定位n时刻的UDV的矩阵，调用`ftdqmc_stablize_b0_svd(n+1)`从n+1时刻得到n时刻的UDR矩阵

​		将UL DL VL logdetQL定位n时刻的UDV矩阵，调用`green_equaltime( n, ndim, UR_up, DRvec_up, VR_up, VL_up, DLvec_up, UL_up, logdetQR_up, logdetQL_up, grtmp, logweightf_up, info )`计算$G(\tau, \tau)$和构型权重

​		调用`s_compare_max_z( ndim, grtmp, grdn, max_wrap_error_tmp )`比较数值稳定计算出的格林函数和演化计算出的格林函数的差别

​		进行格林函数的替换

```fortran
              ! whether use the scrath grdn
              if( info .eq. 0 ) grdn(:,:) = grtmp(:,:)
```





`green_equaltime( n, ndm, ure, dre, vre, vle, dle, ule, logdetqr, logdetql, gtt, logweightf, infoe )`

计算$G(\tau, \tau)$和构型权重



`ftdqmc_sweep_0b(lupdate, lmeasure_equaltime, lmeasure_dyn )`

lupdate 决定是否更新	lmeasure_equaltime 决定是否测量等时关测量	measure_dyn决定是否进行动力学测量

设置0时刻的UDV矩阵为单位矩阵，logdetQst为0

如果定义了ltau，还会定义三个新的格林函数

```fortran
          g00up = grup
          gt0up = grup
          g0tup = grup-Imat
```

进行与`ftdqmc_sweep_b0`类似的更新与测量，区别在于这一次**先进行更新再进行测量**

下面进行数值稳定的判断。如果在本次更新（即时间切片n=nt上）需要做数值稳定，则把n时刻的VDU设置成VL DL UL logdetQL。调用`ftdqmc_stablize_0b_svd(n)`从n时刻的VDU矩阵得到n+1时刻的VDU矩阵

把n时刻的VDU矩阵设置成VR DR UR，如果没有定义ltau或者lmeasure_dyn，调用`call green_equaltime( n, ndim, UR_up, DRvec_up, VR_up, VL_up, DLvec_up, UL_up, logdetQR_up, logdetQL_up, grtmp, logweightf_up, info )`

如果这两个量定义了其中一个，则会进行动力学测量

动力学测量部分：

如果定义了DYNERROR，首先将nt2 nt1设置成nt，之后会调用Bmat_tau_R(nt1, nt2, gt0up, gt0dn)按照公式计算
$$
G(\tau, 0) = B(\tau, t) G(t, 0)
$$
​		不用担心nt2和nt1一样导致Bmat_tau_R不工作，因为Bmat_tau_R使用

```fortran
      do nt = nt2, nt1
```

​		即使是nt2与nt1一样也会进行一次循环

​		由于一开始我们将grup赋值给了gt0up，所以每次调用都会让非等时格林函数往前平移一个time slice

​		之后是调用Bmatinv_tau_L( nt1, nt2, g0tup, g0tdn)按照公式计算
$$
G(0, \tau) = G(0, t) B^{-1}(t, \tau)
$$
如果没有定义DYNERROR，则会直接调用green_tau(n, ndim, UR_up, DRvec_up, VR_up, VL_up, DLvec_up, UL_up, g00up, gt0tmp,  g0ttmp,  grtmp, info )

引用dyn.f90

`dyn.f90`

如果定义了ltau lmeasure_dyn并且没有定义lupdate	**为什么**

​		如果此时进行了数值稳定就已经有了非等时格林函数

​		如果没有，计算非等时格林函数，方法和之前相同

调用`obsert(nt,gt0up,gt0dn,g0tup,g0tdn,grup,grdn,g00up,g00dn)`





`green_tau(n, ndm, ure, dre, vre, vle, dle, ule, g00, gt0, g0t, gtt, infoe )`

这个函数看起来是按照公式直接计算格林函数$G(\tau, 0)$

**还没看**
