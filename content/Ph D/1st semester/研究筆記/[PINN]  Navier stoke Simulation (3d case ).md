---
title: '[PINN]  Navier stoke Simulation (3d case ) '
updated: 2025-11-12 09:39:43Z
created: 2025-11-09 01:46:38Z
---

[PINN]  Navier stoke Simulation (3d case )


## Governing Equations 

### 1. Continuity Equation & Momentum Equations
$$
\begin{alignedat}{}
\frac{\partial u}{\partial x} + \frac{\partial v}{\partial y} =& 0 &&-(1)\\
u \frac{\partial u}{\partial x}+v\frac{\partial u}{\partial y}+w\frac{\partial u}{\partial z}=& -\frac{1}{\rho}\frac{\partial p}{\partial x}+g_x+\nu(\frac{\partial^2 u}{\partial x^2}+\frac{\partial u^2}{\partial y^2}+\frac{\partial u^2}{\partial z^2})&&-(2)\\

u \frac{\partial v}{\partial x}+v\frac{\partial v}{\partial y}+w\frac{\partial v}{\partial z}=& -\frac{1}{\rho}\frac{\partial p}{\partial y}+g_y+\nu(\frac{\partial^2 v}{\partial x^2}+\frac{\partial v^2}{\partial y^2}+\frac{\partial v^2}{\partial z^2})&&-(3)\\

u \frac{\partial w}{\partial x}+v\frac{\partial w}{\partial y}+w\frac{\partial w}{\partial z}=& -\frac{1}{\rho}\frac{\partial p}{\partial z}+g_z+\nu(\frac{\partial^2 w}{\partial x^2}+\frac{\partial w^2}{\partial y^2}+\frac{\partial w^2}{\partial z^2})&&-(4)

\end{alignedat}{}
$$

$$
\begin{alignedat}{1}
 
\end{alignedat}
$$

### 2. Boundary conditions

$$-k\frac{\partial T}{\partial \vec{n}}=q_c + q_r , x \in \partial \Omega$$

$$q_c = h_c (T- T_a) - heat\ convective\ term$$
$$q_r = \sigma \epsilon (T^4-T_a^4) - radiation\ term$$

where h is the heat convection coefficient between air and substrate, $T_a$ is the ambient temperature , $\sigma$ is the stefan-Boltzmann constant, and $\epsilon$ is the heat radiation coefficient

$$R_{BC}=k\frac{\partial T}{\partial \vec{n}}+q_c + q_r , x \in \partial \Omega$$


### 3. Moving heat source 

$$Q(x,y,z,t)= \frac{6\sqrt{3\eta}P}{\pi \sqrt{\pi}\cdot abc} exp(-3\cdot r_0^2)$$

$$r_0^2 = \frac{(x-(vt+x_0))^2}{R^2_a}+ \frac{(y-y_0)^2}{R^2_b}+\frac{(z-z_0)^2}{R^2_c}$$

### 4. Initial Condition
   make sure the ambient temperature is the same with the $T_0$
   $$R_{init} = u(x,0) - T_0$$

### 5. Loss Functions 
 
 
$$L_{Total} = \lambda_{pde}L_{pde}+\lambda_{init} L_{init}+\lambda_{BC}L_{BC}$$

$$L_{pde} = \frac{1}{N_p} \sum\limits^{N_p}_{i=1} R^2_{pde}$$

$$L_{init} = \frac{1}{N_o} \sum\limits^{N_o}_{i=1} R^2_{init}$$

$$L_{BC} = \frac{1}{N_b} \sum\limits^{N_b}_{i=1} R^2_{BC}$$

----------

 
[@xie2022](http://dx.doi.org/10.1007%2Fs00170-021-08542-w)