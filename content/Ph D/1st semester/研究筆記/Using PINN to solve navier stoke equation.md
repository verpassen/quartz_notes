---
title: Using PINN to solve navier stoke equation
updated: 2025-10-13 14:52:26Z
created: 2025-09-01 14:50:06Z
---

Using PINN to solve navier stoke equation

## Ref literatures
- [NSFnets (Navier-Stokes Flow nets): Physics-informed neural networks for the incompressible Navier-Stokes equations](https://arxiv.org/pdf/2003.06496)


## 目前的問題

- Loss function 怎麼寫
Loss function 由多個元件組成。最常見的分成兩個部分，
  1. Physics-informed Loss (MSE of equation residual)
      
  2. Data Loss (MSE of prediction)


	
整個的Loss function = (Physics-informed Loss) + (Data Loss)
有些會在個別的Loss 前面乘上權重
有些boundary 和 initial condition 也會算在 loss function 裡面阿?

- boundary condition & initial condition 怎麼寫 ?

- training data 那個 github 的資料可以用?
- 其他的模擬參數設定值?


## ref 
- [CFD Python solve N-S Equation ](https://www.techchickensoup.com/cae/cfd-python-12-steps-to-navier-stokes-1/)
