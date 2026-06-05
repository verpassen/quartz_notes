---
title: '[PINN]  DED Simulation (3D case)'
updated: 2026-02-12 15:38:05Z
created: 2025-11-06 15:10:00Z
tags:
  - pinn
---



## Governing Equations 

### 1. Heat conduction
$$\frac{\partial \rho C_p T}{\partial t} = \frac{\partial}{\partial x}(k\frac{\partial T}{\partial x}) +\frac{\partial}{\partial y}(k\frac{\partial T}{\partial y})+\frac{\partial}{\partial z}(k\frac{\partial T}{\partial z})+ \dot{Q_{laser}}(x,t) , x\in \Omega , t \in T$$

所以，整理一下

$$
\begin{alignedat}{1}
\frac{\partial  T}{\partial t} &- \alpha (\frac{\partial ^2 T}{\partial x^2}+\frac{\partial ^2 T}{\partial y^2}+\frac{\partial ^2 T}{\partial z^2})- \frac{\dot{Q_{laser}}(x,t)}{\rho C_p} = 0\\

\therefore  R_{pde} &= \frac{\partial  T}{\partial t} - \alpha (\frac{\partial ^2 T}{\partial x^2}+\frac{\partial ^2 T}{\partial y^2}+\frac{\partial ^2 T}{\partial z^2})- \frac{\dot{Q_{laser}}(x,t)}{\rho C_p}\\

\end{alignedat}
$$

或是參考[Rosenthal's analytical Solution](../../../../undefined)

### 2. Boundary conditions

$$-k\frac{\partial T}{\partial \vec{n}}=q_c + q_r , x \in \partial \Omega$$

$$q_c = h_c (T- T_a) - heat\ convective\ term$$
$$q_r = \sigma \epsilon (T^4-T_a^4) - radiation\ term$$

where h is the heat convection coefficient between air and substrate, $T_a$ is the ambient temperature , $\sigma$ is the stefan-Boltzmann constant ($5.67\times10^{-8}\ \small{} W\cdot m^{-2}\cdot K^{-4}$ ), and $\epsilon$ is the heat radiation coefficient

$$R_{BC}=k\frac{\partial T}{\partial \vec{n}}+q_c + q_r , x \in \partial \Omega$$



### 3. Moving heat source 

$$Q(x,y,z,t)= \frac{6\sqrt{3\eta}P}{\pi \sqrt{\pi}\cdot abc} exp(-3\cdot r_0^2)$$

ref [@AnalyticalSolutionsTransient](https://www.researchgate.net/publication/278651706_Analytical_Solutions_for_Transient_Temperature_of_Semi-Infinite_Body_Subjected_to_3-D_Moving_Heat_Sources)


$$
$$Q(x,y,z,t)= \frac{2\eta P}{\pi r^2 {\d}\} exp(-2\frac{(x-(x_0 +vt))^2 + (y-y_0)^2}{r^2}exp(-\frac{|z-z_0|}{d})$$
$$



ref to  
Han, X., Qian, Z., Gao, X., Li, H., Peng, Z., & Long, Y. (2025). Three-Dimensional Modeling and Analysis of Directed Energy Deposition Melt Pools Based on Physical Information Neural Networks. Applied Sciences, 15(17), 9401. https://doi.org/10.3390/app15179401



#### Ellipsoidal Heat source in semin-infinite body 
Famous math model 
- Rosenthal in 1941 
- Goldak equation in 1984
 


the heat source is combined by two semi-ellipsoidal 
![76c93ea902155a608d42668ec211ab88.png](../../../../_resources/76c93ea902155a608d42668ec211ab88.png)
1st section - front part
$Q_f(x,y,z) = \Large\frac{6\sqrt{3}r_fQ}{a_h b_h c_{hf} \pi \sqrt{\pi}}\large exp(-\frac{3x^2}{c_{hf}^2}-\frac{3y^2}{a_{h}^2}-\frac{3z^2}{b_h^2})$

2nd section - rear part 
$Q_b(x,y,z) = \Large\frac{6\sqrt{3}r_bQ}{a_h b_h c_{hb} \pi \sqrt{\pi}}\large exp(-\frac{3x^2}{c_{hb}^2}-\frac{3y^2}{a_{h}^2}-\frac{3z^2}{b_h^2})$

where is 
$a_h, b_h,c_h :\ ellipsoidal\ heat\ source\ parameters$
right hand side Q  is the heat input. In the original literature, it is under the welding scenario.($Q=\eta V I$ , voltage times current times efficiency) Therefore, we have to transfer into laser case. 

$r_f , r_b : proportion\ coefficient,\ representing\ heat\ appoirtionment\ in\ front\ and\ back\ of\ the\ heat\ source$
respectively , r~f~ + r~b~ = 2


$$r_0^2 = \frac{(x-(vt+x_0))^2}{R^2_a}+ \frac{(y-y_0)^2}{R^2_b}+\frac{(z-z_0)^2}{R^2_c}$$


### 3. Powder stream
[@tsengScalingLawsNumerical2023](http://dx.doi.org/10.1016%2Fj.ijheatmasstransfer.2023.124717)

![6045eb4020e67c3bf22617a39ebc5019.png](../../../../_resources/6045eb4020e67c3bf22617a39ebc5019.png)

$\xi = (x-H_w/tan\theta)sin\theta_n - (y-H_w)cos\theta_n$
$\eta=(x-H_w/tan\theta)cos\theta_n+(y-H_w)sin\theta_n$
$C_1=\Large\frac{2\cdot F_p /4}{v_p\pi r_p^2} \large{}exp\{-2[(\frac{z-v_{las} t}{r_p})^2+(\frac{\xi}{r_p})^2]\}$

$where\ is$
$r_p=-\eta tan\theta_d + r_0$

C1 , C2 , C3 , C4分別代表四個不同噴嘴的粉末(kg/m^3^)

$C(x,y,z) = C_1 + C_2 + C_3 + C_4$


----

### 4. Initial Condition
   make sure the ambient temperature is the same with the $T_0$
   $$R_{init} = u(x,0) - T_0$$

### 5. Loss Functions 
 
 
$$
\begin{aligned}

L_{Total} &= \lambda_{pde}L_{pde}+\lambda_{init} L_{init}+\lambda_{BC}L_{BC}\\


L_{pde} &= \frac{1}{N_p} \sum\limits^{N_p}_{i=1} R^2_{pde}\\

L_{init} &= \frac{1}{N_o} \sum\limits^{N_o}_{i=1} R^2_{init} \\
where\ is&\\ R_{init}&= \hat T_{t=t_0} - T_{ref} \\

\\

L_{BC} &= \frac{1}{N_b} \sum\limits^{N_b}_{i=1} R^2_{BC}\\
where\  &is \\R_{BC} &= \begin{cases} q(x,t)\cdot n-[h(\hat T - T_{amb})+\sigma\epsilon(\hat T^4 - T^4_{amb})]\\ q(x,t)\cdot n - [h_{force}(\hat T - T_{amb})] \end{cases}
\end{aligned}
$$

6. Change of phase
$
H(T) = \small \left. \begin{cases} 0   &  &   T<T_m \\ &|&\\ H_m & & T>T_m  \end{cases}
 \right\} 0 \; , \
f_l = \left. \begin{cases} 0 &  & T<T_s \\ \frac{T-T_s}{T_l-T_s} & | & T_l > T> T_s \\ 1  &  & T>T_l  \end{cases} \right\}
$

Considering the phase change which consume amount of the energy in the system.
$\rho(C_p + L \Large{}\frac{d f_l}{dT})\frac{\partial T}{\partial t} = \small \nabla \cdot (K\nabla T)+ \dot Q_{laser}$


----

### [DED - Material Physics Characterisitcs](../../../../undefined)
模擬中所需要用到的物理常量

## 寫錯的

- 物理常量搞錯數值. ex. Boltzmann constant
- 單位錯誤
寫pde 的時候 , 整個式子單位是  w 也就是能量
$residual = \large{} \frac{\partial T}{\partial n}- k (\frac{\partial ^2u}{\partial x^2} + \frac{\partial ^2u}{\partial y^2})$
k  代表 熱傳導速度 thermal conductivity [$W / m\cdot K$]
但這樣乘起來單位不對
應該是 $\alpha$ thermal diffusitivity [$m/s$]

----

### Reference Architecture 
![9379132c3158155d7467c6b8453ffc16.png](../../../../_resources/9379132c3158155d7467c6b8453ffc16.png)

[@hanThreeDimensionalModelingAnalysis2025](http://dx.doi.org/10.3390%2Fapp15179401)

----
## Challenges 



 ---
 
 
[@xie2022](http://dx.doi.org/10.1007%2Fs00170-021-08542-w)

[@li2023](http://dx.doi.org/10.1016%2Fj.engappai.2023.105908)

[@peng2024](http://dx.doi.org/10.1016%2Fj.addma.2024.104498)
 
Hoadley, A. F. A., and M. Rappaz. 1992. ‘A Thermal Model of Laser Cladding by Powder Injection’. Metallurgical Transactions B 23 (5): 631–42. https://doi.org/10.1007/BF02649723.

Tseng, C.-C., Wang, Y.-C., & Ho, M.-I. (2023). Scaling laws and numerical modelling of the laser direct energy deposition. International Journal of Heat and Mass Transfer, 217, 124717. https://doi.org/10.1016/j.ijheatmasstransfer.2023.124717
