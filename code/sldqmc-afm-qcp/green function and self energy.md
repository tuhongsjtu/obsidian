line 165 in ftdqmc_core_svd.f90

```fortran
call zgemm('n','n',ndim,ndim,ndim,cone,Vtmp,ndim,Vmat1,ndim,czero,Vmat2,ndim)  ! Vmat2 = Vtmp * Vmat1
```

zgemm是LAPACK里的一个函数，用于矩阵乘法，在这一行的意思就是把Vtmp和Vmat1相乘然后赋值给Vmat2



subroutine `ftdqmc_sweep_start_0b`

如果nst大于0

首先会将格林函数和0时刻的UDV矩阵定成单位矩阵，之后在每个需要进行数值稳定的时刻使用subroutine `ftdqmc_stablize_0b_svd`进行数值稳定，并把相应的UDV矩阵储存。然后会使用subroutine `green_equaltimebb`计算$\beta$时刻的等时格林函数

ltrot小于nwarp时，此时nst=0，如果定义了llocal（**我们还不知道这个开关的作用**）

```fortran
     if ( llocal ) then
         Bdtau1_up(:,:) = Imat(:,:)
         Bdtau1_dn(:,:) = Imat(:,:)
         call Bmat_tau_R( ltrot, 1, Bdtau1_up, Bdtau1_dn )
         do  i = 1, ndim
             Bdtau1_up(i,i) = Bdtau1_up(i,i) + cone
         end do
         call s_invlu_z( ndim, Bdtau1_up )
         grup(:,:) = Bdtau1_up
#IFDEF SPINDOWN
         do  i = 1, ndim
             Bdtau1_dn(i,i) = Bdtau1_dn(i,i) + cone
         end do
         call s_invlu_z( ndim, Bdtau1_dn )
         grdn(:,:) = Bdtau1_dn
#ENDIF
     else
         grup(:,:) = Imat(:,:)
         grdn(:,:) = Imat(:,:)
         call Bmat_tau_R( ltrot, 1, grup, grdn)
         do  i = 1, ndim
             grup(i,i) = grup(i,i) + cone
             grdn(i,i) = grdn(i,i) + cone
         end do
     end if

     END IF
```

**这一段哥们不是很懂，回头再看看，先吃饭了**



ftdqmc_stablize_0b_svd(n)

会在n-1处得到相应的UDV矩阵，然后会给n-1处的U矩阵左乘B(tau+dtau, tau)

在对新的B矩阵进行UDV分解后，得到新的n处的UDV矩阵，并赋值给UDV列表



subroutine `green_equaltimebb(nst, ndim, UR_up, DRvec_up, VR_up, grup, info)`

计算格林函数$G(\beta, \beta)$
$$
\begin{align}
G(\tau, \tau) 
&= [1 + B(\tau, 0) B(\beta, \tau)]^{-1} \\
&= [1 + Q_R D_R T_R T_L D_L Q_L]^{-1} \\
&= Q_{L}^{-1} [(Q_L Q_R)^{-1} + D^{\mathrm{max}}_R D^{\mathrm{min}}_R T_R T_L D^{\mathrm{min}}_L D^{\mathrm{max}}_L ]^{-1} Q_R^{-1} \\
&= Q_L^{-1} (D^{\mathrm{max}}_L)^{-1} [(D^{\mathrm{max}}_R)^{-1} (Q_L Q_R)^{-1} (D^{\mathrm{max}}_L)^{-1} + D^{\mathrm{min}}_R T_R T_L D^{\mathrm{min}}_L]^{-1} (D^{\mathrm{max}}_R)^{-1} Q_R^{-1}
\end{align}
$$
所以
$$
G(\beta, \beta) =  [(D^{\mathrm{max}}_R)^{-1} Q_R^{-1}  + D^{\mathrm{min}}_R T_R]^{-1} (D^{\mathrm{max}}_R)^{-1} Q_R^{-1}
$$
程序会在nst处读取UDV矩阵

将对角矩阵$D_R$分为大于1的对角矩阵$D_R^{\mathrm{max}}$和绝对值小于1的对角矩阵$D^{\mathrm{min}}_R$的乘积将在subroutine `s_dvec_min_max(ndim, dvec, dmax, dmin)`中完成

之后程序会计算乘积$(D^{\mathrm{max}}_R)^{-1} Q_R^{-1}  + D^{\mathrm{min}}_R T_R$并在subroutine ``s_invlu_z(ndm, dvvdtmp)``中使用LU分解计算其逆矩阵，最后会在subroutine `s_v_invd_u(ndim, dvvdtmp, drmax, urinv_tmp, gtt)`中计算格林函数$G(\beta, \beta)$

**info在哪里定义的？**



在ftdqmc_core_svd.f90和ftdqmc_core.f90中的module名字都是ftdqmc_core，调用的是哪一个？

以上内容是ftdqmc_core_svd.f90中的内容，下面说说ftdqmc_core.f90中的



stglobal_sl.f90 stglobal_wolff_ising.f90 stglobal_wolff.f90都有subroutine ftdqmc_calculate_weights(logweights)

这三个函数都是完全一样的，都是计算Boson部分的权重$\Delta \tau J \sum_{i,j} s_i s_j$，**这三个文件的区别是什么？**

但是调用函数时会把logweights先初始化为0，不知道有没有影响

没啥问题，另一个变量是叫logweightf



subroutine `obser_equaltime(nt)`

首先会计算$\langle c_i c^{\dagger}_j \rangle$和$\langle c_i^{\dagger} c_j \rangle$并储存在`grup`和`grupc`中
$$
\langle c_j c^{\dagger}_i \rangle + \langle c_i^{\dagger} c_j \rangle = \delta_{ij}
$$
之后计算的东西没太看懂

```fortran
    do i = 1,ndim
       xi = 1.d0
       if ( orblist(i) == 2 ) xi = -1.d0
       do j = 1,ndim
          xj = 1.d0
          if ( orblist(j) == 2 ) xj= -1.d0
          grdn (i,j) = dcmplx(xi*xj, 0.d0) * dconjg ( grup (i,j) )
          grdnc(i,j) = dcmplx(xi*xj, 0.d0) * dconjg ( grupc(i,j) )
       enddo
    enddo
```

orblist的定义为

```fortran
  do i = 1, ndim
      orblist(i) = (i-1)/lq + 1
  end do
```

按这个定义orblist似乎不太可能为2

之后在obs_bin里记录了各种测量量

obs_bin(1)记录了$\sum _i\langle c^{\dagger}_i c_i + c_i c^{\dagger}_i \rangle $的值

obs_bin(2)记录了自旋的均值$\langle s \rangle$

如果obs_bin(2)>0，obs_bin(3)记录的是`grupc(i, i)`+i`grdnc(i, i)`，否则记录的是`grdnc(i, i)`+i`grupc(i, i)`

obs_bin(4)记录的是动能，动能的计算方法是
$$
\langle T \rangle = \sum_i (h_{0})_{i, i+a_1} \langle c^{\dagger}_i c_{i+a_1} \rangle + (h_{0})_{i, i+a_2} \langle c^{\dagger}_i c_{i+a_2} \rangle + (h_{0})_{i, i+a_1+a_2} \langle c^{\dagger}_i c_{i+a_1+a_2} \rangle \\
h_0 = \sum_{\langle i, j \rangle} e^{-\frac{2\pi}{\Phi}\int_i^j A dl} c^{\dagger}_{i} c_j
$$
**代码里为什么没有乘rt？轨道在那？**

obs_bin(5)记录的是耦合的能量$-\sum_i \frac{1}{2}\xi (\langle n_{i \uparrow} \rangle - \langle n_{i \downarrow} \rangle)$

```fortran
    ! zecoup
    zecoup = czero
    do i = 1, lq
        zecoup = zecoup + ( grupc(i,i) - grdnc(i,i) ) * nsigl_u(i,nt)
    end do
    zecoup = zecoup*dcmplx(-rxi*0.5d0, 0.d0)  ! note 0.5 for fermion spin 1/2
    obs_bin(5) = obs_bin(5) + zecoup + dconjg(zecoup) ! layer 1 and layer 2
```

**为什么要取个共轭？**

obs_bin(6)记录的是Ising模型的能量$-J\sum_{i, j} s_i s_j$

obs_bin(7)记录的是外加恒场的能量，因为恒场的能量已经被转化为时间方向自旋的关联能，所以计算方法为：

```fortran
    ! ehx
    ehx = zero
    do i = 1, lq
        if ( nsigl_u(i,mod(nt,ltrot)+1) .eq. nsigl_u(i,nt) ) then
            ehx = ehx + tanhdth
        else
            ehx = ehx + cothdth
        end if
    end do
    obs_bin(7) = obs_bin(7) + dcmplx( -hx*ehx, 0.d0 )
```

如果需要，还会计算时空的自旋关联函数和**背景？**







