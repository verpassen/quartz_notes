---
title: '[Openfoam - Tutorial] elbow'
updated: 2025-08-11 21:47:33Z
created: 2025-07-01 13:02:28Z
latitude: 25.03577500
longitude: 121.56345030
altitude: 0.0000
---

# [Openfoam - Tutorial] elbow

>  incompressible > icoFoam > elbow 

### 問題
2025.Jul.01
- why unit in file p  is [0 2 -2 0 0 0 0 ]
長度除以時間平方？

平常使用的壓力單位，舉例 $Pa=N/m^2 [kg*m^{-1}*s^{-2}]$
Openfoam 中使用的壓力為kinematic pressure 為
$P=\Large{\frac{P}{\rho}}$
所以單位會變成 $[m^2*s^{-2}]$
ref  [Openfoam user guide](https://www.openfoam.com/documentation/guides/latest/doc/guide-fos-field-pressure.html)

---

預設是compressible flow , 但如果是incompressible flow 是以 [kinematic pressure](https://www.openfoam.com/documentation/guides/latest/doc/guide-applications-solvers-variable-transform-kinematic-pressure.html) 去計算

$p_k = \Large{\frac{p}{\rho}} \ \small{[m^2s^{-2}]}$

原本需要去乘以流體的密度, 不過不可壓縮流的密度為常數
因此, 

- boundary file 的編號如何跟 mesh 檔案對起來？
如何知道 boundary condition 中的編號會對到mesh 的哪些節點？ 




