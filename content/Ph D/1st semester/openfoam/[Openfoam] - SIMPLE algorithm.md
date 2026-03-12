---
title: '[Openfoam] - SIMPLE algorithm'
updated: 2025-07-12 11:44:06Z
created: 2025-07-07 02:21:33Z
latitude: 22.64839560
longitude: 120.32620850
altitude: 0.0000
---

# [Openfoam] - SIMPLE algorithm

## Why Navier-stokes Equations difficult to solve 

### Navier-stokes Euqations(NS Equations)

- NS Equation 包含 非線性的項次
- 通常會和連續方程式一起求解
四個未知數，四組方程式
$(U_x,U_y,U_z,p)$

註: 
這邊的p 指的是kinematic pressure。 有除以密度
$p = \large{\frac{P}{\rho}}$

Momentum equations 
$U \cdot \bigtriangledown U -\bigtriangledown \cdot(\upsilon \bigtriangledown V) = - \bigtriangledown p$

註:
其他常見的還有 **PISO(Pressue-Implicit-of-split-Operations)、PIMPLE(Merged PISO-SIMPLE algorithm)**

## SIMPLE Algorithm 說明
**SIMPLE - Semi-Implicit-Method-Of-Pressure-Linked-Equations**
用於穩態分析

1. 推導關於壓力(Pressure field)的方程式
 假設一個係數矩陣 M 可以符合
$M U = -\bigtriangledown p$

$$
\begin{pmatrix} 
M_{1,1}&M_{1,2}&...&M_{1,n}\\
M_{2,1}&M_{2,2}&...&M_{2,n}\\
...&...&...&\\
M_{n,1}&M_{n,2}&...&M_{n,n}
\end{pmatrix} \begin{pmatrix} U_1\\U_2\\...\\U_n\end{pmatrix}
=\begin{pmatrix}(\frac{\partial{p}}{\partial x_1}) \\(\frac{\partial{p}}{\partial x_2}) \\ ... \\
(\frac{\partial{p}}{\partial x_n}) 
\end{pmatrix}
$$

Q. 建立M來串連U和 P兩者的關係，但是為什麼不寫
$MU=-p$ 就好，還要保留 梯度計算

2. 把矩陣M分解為 對角矩陣和非對角矩陣的組合
$M = AU - H\\
其中 矩陣A為對角矩陣，只有對角元素有值\\
方便反矩陣運算\\
H則為使上面關係式成立的對應矩陣$

Q. 矩陣拆解，不考慮SVD。同樣沒有維度限制而且好做轉換

3. 將上面的關係式代入連續方程式
$\because U=A^{-1}(H-\bigtriangledown p)\\
\therefore \bigtriangledown \cdot \textcolor{red}{A^{-1}(H-\bigtriangledown p)} =0$

	整理一下得到
$\bigtriangledown \cdot A^{-1}H= \bigtriangledown (A^{-1}\bigtriangledown p)$

這邊得到Possion equation 

Q. Possion equations 怎解 ?  這樣型式的方程式都叫possion equation? 


## 計算流程
$1.\ MU=- \bigtriangledown p\\
\Rightarrow\ M\ use\ an\ initial\ guess\ to\ get\ the\ coef.\ matrix$

$2.\ Solve\ the\ Equation\ for\ pressure\\
\bigtriangledown \cdot (A^{-1}H) = \bigtriangledown \cdot (A^{-1}\bigtriangledown p)$

$3.\ Use\ pressure\ field\ to\ correct\ the\ velocity\ field\\
U= A^{-1}H-A^{-1}\bigtriangledown p$

$4.\ back\ to\ step\ 1$

# Ref 
- [[CFD] The SIMPLE Algorithm (to solve incompressible Navier-Stokes)](https://www.youtube.com/watch?v=OOILoJ1zuiw)
- [Openfoam document](https://doc.openfoam.com/2306/tools/processing/solvers/pressure-velocity/simple/)