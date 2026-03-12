---
title: hw#2 momentum equation derivation in x direction for fluid
updated: 2025-10-14 15:31:53Z
created: 2025-10-10 12:15:55Z
---

# hw#2 momentum equation derivation in x direction for fluid 


$dF =  m\vec{a} \small-(1)$

$\vec{V}=u\vec{i} + v\vec{j} + w\vec{k}$

$\vec{a} = \large{}\frac{d\vec{V_x}}{dt}=\frac{du}{dt}$

$m = \rho (dxdydz)$


As we know,
$\;dF = F_{body,x} + F_{surf,x}$
that  is  
$\;F_{body,x} = (\rho dx dy dz)$

$
\begin{aligned}
F_{surf,x} &= (\tau_{xx}+\frac{\partial \tau_{xx}}{\partial x}dx)dydz + (\tau_{yx}+\frac{\partial \tau_{yx}}{\partial y}dy)dxdz + (\tau_{zx}+\frac{\partial \tau_{zx}}{\partial z}dz)dxdy-\tau_{xx}dydz-\tau_{yx}dxdz-\tau_{zx}dxdy\\&= (\frac{\partial \tau_{xx}}{\partial x} + \frac{\partial \tau_{xx}}{\partial x} + \frac{\partial \tau_{xx}}{\partial x}) dx dydz
\end{aligned}
$

Substitute back to equation (1)
obtain 
$\rightarrow (\frac{\partial \tau_{xx}}{\partial x} + \frac{\partial \tau_{xx}}{\partial x} + \frac{\partial \tau_{xx}}{\partial x}) dx dydz+(\rho dxdydz) g_x = \rho(dxdydz)[\frac{\partial u}{\partial t}+u\frac{\partial u}{\partial t}+v\frac{\partial u}{\partial y}+w\frac{\partial u}{\partial z}]$

Cancel out all $(dxdydz)$ term 

$(\frac{\partial \tau_{xx}}{\partial x} + \frac{\partial \tau_{xx}}{\partial x} + \frac{\partial \tau_{xx}}{\partial x}) +\rho  g_x = \rho [\frac{\partial u}{\partial t}+u\frac{\partial u}{\partial t}+v\frac{\partial u}{\partial y}+w\frac{\partial u}{\partial z}]$

According to the Stoke's postitulates

$\tau_{xx}=-P + 2\mu\frac{\partial u}{\partial x}+\lambda (\nabla \cdot \vec{V})$

$\tau_{yx}=\mu(\frac{\partial u}{\partial y}+\frac{\partial v}{\partial x})$

$\tau_{zx}=\mu(\frac{\partial u}{\partial z}+\frac{\partial w}{\partial x})$

Substitue back to equation (2)
$
\begin{aligned}
\rightarrow &-\frac{\partial P}{\partial t} + 2\mu \frac{\partial ^2 u}{\partial x^2} + \lambda \frac{\partial}{\partial x}(\nabla \cdot \vec{V})+ \mu \frac{\partial}{\partial y}(\frac{\partial u}{\partial y}+\frac{\partial v}{\partial x})+ \mu \frac{\partial}{\partial z}(\frac{\partial u}{\partial z}+\frac{\partial w}{\partial x})\\&=\rho[\frac{\partial u}{\partial t}+u\frac{\partial u}{\partial x}+v\frac{\partial u}{\partial y}+w\frac{\partial u}{\partial z}]
\end{aligned}
$

Rewrite Left hand side

$
\begin{aligned}
\rightarrow &-\frac{\partial P}{\partial t} + 2\mu \frac{\partial ^2 u}{\partial x^2} + \lambda \frac{\partial}{\partial x}(\nabla \cdot \vec{V})+ \mu (\frac{\partial ^2u}{\partial y^2}+\frac{\partial ^2v}{\partial x\partial y})+ \mu (\frac{\partial^2 u}{\partial z^2}+\frac{\partial^2 w}{\partial x \partial z}) + \large{}\rho g_x
\\=&-\frac{\partial P}{\partial t} + \mu (\frac{\partial ^2 u}{\partial x^2} +\frac{\partial ^2 u}{\partial y^2}+\frac{\partial ^2 u}{\partial z^2}) +\mu (\frac{\partial ^2 u}{\partial x^2} +\frac{\partial ^2 v}{\partial x \partial y}+\frac{\partial ^2 w}{\partial x \partial z}) + \lambda \frac{\partial}{\partial x}(\nabla \cdot \vec{V}) + \large{}\rho g_x
\end{aligned}$

Rewrite the all equationl, and we can obtain the fluid momentum equation for the X-direction 

$
\begin{aligned}
&-\frac{\partial P}{\partial t} + \mu (\frac{\partial ^2 u}{\partial x^2} +\frac{\partial ^2 u}{\partial y^2}+\frac{\partial ^2 u}{\partial z^2}) +\mu (\frac{\partial ^2 u}{\partial x^2} +\frac{\partial ^2 v}{\partial x \partial y}+\frac{\partial ^2 w}{\partial x \partial z}) + \lambda \frac{\partial}{\partial x}(\nabla \cdot \vec{V}) + \large{} \rho g_x \\&= 
\rho(\frac{\partial u}{\partial t} + u\frac{\partial u}{\partial x}+ v\frac{\partial u}{\partial y}+ w\frac{\partial u}{\partial z})
\end{aligned}
$
 

if the fluid is incompressible flow, that is $\nabla \cdot \vec{V} = 0$
we can simplify the equation as below 

$\large{}\rho[\frac{\partial u}{\partial t}+(\vec{V}\cdot \nabla)u]= -\frac{\partial P}{\partial x} + \mu \nabla^2u + \rho g_x$