

`mmuur.f90`

in a, out exp(V(S)) * a

`xsigma_u_up`定义在salph.f90中

```fortran
  ! onsite
  ! spin up, positive coupling
  xsigma_u_up(-1) = dcmplx( dexp(  dtau * rxi * ( -0.5d0 ) ), 0.d0 )  ! -1.d0 is the field, 0.5 is from fermion spin s=1/2 
  xsigma_u_up( 1) = dcmplx( dexp(  dtau * rxi * (  0.5d0 ) ), 0.d0 )  !  1.d0 is the field, 0.5 is from fermion spin s=1/2
  ! spin down, negative coupling
  xsigma_u_dn(-1) = dcmplx( dexp( -dtau * rxi * ( -0.5d0 ) ), 0.d0 )  ! -1.d0 is the field, 0.5 is from fermion spin s=1/2
  xsigma_u_dn( 1) = dcmplx( dexp( -dtau * rxi * (  0.5d0 ) ), 0.d0 )  !  1.d0 is the field, 0.5 is from fermion spin s=1/2
```

可以看到这个数组是用于计算**耦合？**的

如果rxi不为0，则会调用mmuur第一部分，对a_up和a_dn左乘xsigma_u_up和xsigma_u_dn

**如果rj不为0**



`ltau`	在`prtau.f90`中控制着格林函数的输出

`nsigl_u(lq, ltrot)`

Ising模型的自旋

`nsigl_k(lq, 2, ltrot)`

看起来是辅助场的自旋，**第二个维度代表什么？**

`nsigl_j(lq, 2, ltrot)`



listk(lq, 2)

记录用于傅里叶变换的波矢$k$，单位是$b_1$和$b_2$
$$
k_1 = 
\left \{
\begin{matrix}
-\frac{L}{2}, 1 - \frac{L}{2} , ..., \frac{L}{2} - 1, \ \ L \text{  is  even};  \\
-\frac{L-1}{2},  - \frac{L-3}{2} , ..., \frac{L-1}{2} , \ \ L \text{  is  even}.
\end{matrix}
\right.  \\

k_2 = 
\left \{
\begin{matrix}
-\frac{L}{2}, 1 - \frac{L}{2} , ..., \frac{L}{2} - 1, \ \ L \text{  is  even};  \\
-\frac{L-1}{2},  - \frac{L-3}{2} , ..., \frac{L-1}{2} , \ \ L \text{  is  even}.
\end{matrix}
\right.
$$


zexpiwt(0:ltrot-1, 0:nuse)、zexpiqr(lq, lq)

记录用于傅里叶变换的相位$\exp(i \omega_n \tau)$和$\exp(i \mathbf{q} \cdot \mathbf{r})$，实际使用的时候如果需要$\exp(-i \mathbf{q} \cdot \mathbf{r})$会选择除以数组的元素

注意$\exp(i\omega_n \tau)$的时间定义是$0\sim ltrot-1$，所以之后调用的时候可能会因为时间范围的不同使用zexpiwt(i, n-1)

```fortran
  ! line 93-98 in sli.f90
  ! set zexpiwt, zexpiqr
  do n = 0, nuse
      do i = 0, ltrot-1
          zexpiwt(i,n) = exp( dcmplx( 0.d0, wn(n)*dble(i)*dtau ) )
      end do
  end do

  do iq = 1, lq
      qvec = dble(listk(iq,1))*b1_p + dble(listk(iq,2))*b2_p
      do i = 1, lq
          ri = dble(list(i,1))*a1_p + dble(list(i,2))*a2_p
          zexpiqr(i,iq) = exp( dcmplx( 0.d0,  qvec(1)*ri(1) + qvec(2)*ri(2) ) )
      end do
  end do
```

wn(-nuse:nuse)是使用的频率

```fortran
    ! line 356-358 in blockc.f90
    do i = -nuse, nuse
        wn(i) = 2.d0*dble(i)*pi/beta
    end do
```

**所以**

zexpiqr(lq, lq)的第一个维度即行下表代表$\mathbf{r}_{ij}$，另一个维度即列下标代表使用的波矢$\mathbf{q}$，在定义时$\mathbf{r}_{ij}$只包括了格点所在的离散值
