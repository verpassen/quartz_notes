---
title: Physics-Informed neural networks (PINN)
updated: 2025-11-26 00:31:16Z
created: 2025-07-10 01:55:00Z
latitude: 25.03296940
longitude: 121.56541770
altitude: 0.0000
tags:
  - machine learning
---

# Physics-Informed neural networks (PINN)

## Why PINN? 
一般來說，對於Neural network 只要能夠給夠大的資料集，都可以訓練出逼近於資料背後的現象，但是如果這些資料有問題，或是這結果可能根本就不符合某些物理原則，同樣是 garbage in garbage out. 


使用模擬，可以得到整個情境全局的高精度解析資料，但如果要了解較長一段時間的變化，所需消耗的計算資源就很龐大。

利用實驗量測相關的特徵物理資訊，可以長時間蒐集資料，但所通常為空間中某幾個位置的資訊，若要完整獲取整個空間與時間的資訊，同樣需要消耗大量的資源。

利用PINN 我們可以利用在訓練模型過程中，導入某些特定領域的物理原則，依據當下你要解決的問題domain，熱、聲音、電磁等等。好處在於PINN可以利用相對較稀疏的資料，建立同樣可靠的模型。

Ref to the below literature, listing the benchmarking PDEs. 
- Burgers equation 
- Wave equation 
- Heat equation with Dirichlet boundary condition 
- Heat equation with Neumann boundary conditions 
- Advection equation 
- Reaction equation
  
[@wangAutoPINNUnderstandingOptimizing2023](http://dx.doi.org/10.48550%2FarXiv.2205.13748)

---
## Literature Review 

1. [Neural algorithm for solving differential equations](https://doi.org/10.1016/0021-9991(90)90007-N)
2.  [Thermal-Mechanical Physics Informed Deep Learning For Fast Prediction of Thermal Stress Evolution in Laser Metal Deposition](https://doi.org/10.48550/arXiv.2412.18786)
3. [A physics-informed neural network framework to predict 3D temperature field without labeled data in process of laser metal deposition](https://doi.org/10.1016/j.engappai.2023.105908)
4. [Machine learning for metal additive manufacturing: Predicting temperature and melt pool fluid dynamics using physics-informed neural networks](https://doi.org/10.48550/arXiv.2008.13547)
5. [Physics-Informed Online Learning for Temperature Prediction in Metal AM](https://doi.org/10.3390/ma17133306)
6. [Advances in physics-informed neural networks for solving complex partial differential equations and their engineering applications: A systematic review](https://linkinghub.elsevier.com/retrieve/pii/S0952197625020524)
7. [Physics Informed Deep Learning (Part I): Data-driven Solutions of Nonlinear Partial Differential Equations](http://arxiv.org/abs/1711.10561)
8. [Physics Informed Deep Learning (Part II): Data-driven Discovery of Nonlinear Partial Differential Equations](http://arxiv.org/abs/1711.10566)

---

 - 目前文獻使用的PINN 有哪些變體
 - 應用於DED 的有哪些?
	 - 分別怎麼去應用
	 - 輸入和輸出分別是?
	 - 它們的差別是什麼?
- 文獻中列出的Future work 有哪些


## Research Gap 
- Multi-physics coupling analysis
- Integration of the experimental data and in-situ  data
- Multi-track and multi layer modeling
- error accumulation and robustness

===
原生的PINN 在使用上所遇到的一些困難包含: 
- Multi-physics
- stiff partial differential equations
會遇到的狀況是 收斂性不佳以及準確性不夠好的問題


所提出的可以對應的建議包含: 
- domain decomposition
- adaptively weighting each loss term
- improve the architecture to manage interpolation and extrapolation
- embedding input coordinate features


ref to [Intech open]

===


### What problems you want to solve 

- how to build a digital twin of the current system by PINN
- review the current literature
- explain the research gap
- what is the research target
- what is the innovation of your research method / approach?
  


## Related notes
- [Reading notes Physics-informed learning of governing equations from scarce dat](../../../../undefined)
- https://laserbeamfoam.com/
針對PBF製程開發的Openfoam 套件還有整理的 solver 
  - [laser beam foam github](https://github.com/laserbeamfoam/laserbeamfoam.github.io)
若是針對laser beam 的焊接可以參考[這邊](https://laserbeamfoam.com/solvers/Associated_Projects/beamWeldFoam/beamWeldFoam.html)

## Github
- [physics-informed-surrogate-modeling](https://github.com/joon-stack/physics-informed-surrogate-modeling)
- [Transfer learning PINN](https://github.com/shi-tong/Transfer-learning-based-PINN/tree/main)
- [Heat-Transfer-in-Advanced-Manufacturing-using-PINN](https://github.com/doomsday4/Heat-Transfer-in-Advanced-Manufacturing-using-PINN)
- [cladplus](https://github.com/openlmd/cladplus)



- [Laser beam foam](https://github.com/laserbeamfoam/LaserbeamFoam)
- [PINN](https://github.com/ComputationalDomain/PINNs)
這裡有open 的data,也可以參考[這裡](https://github.com/Shengfeng233/PINN-for-NS-equation?tab=readme-ov-file)

### Python modules
- [PINA](https://mathlab.github.io/PINA/_tutorial.html)
- [PBDL](https://www.physicsbaseddeeplearning.org/overview.html)

![f61781df7fff168642617f8a2a1b8004.png](../../../../_resources/f61781df7fff168642617f8a2a1b8004.png)


---
### Variation of the PINN 
We can assembly or integrate different algorithm and combine the different model to build a new model to simulate / solve the real world physics problems. 

Here are some variation of the PINN 
- FBPINNs , Finite basis Physics-informed Neural networks
a general domain decomposition for solving a large scale and multi-scale problem relating to differential equations.
- DAE-PINN
- mnPINN
- [Delta-PINNs](https://arxiv.org/abs/2209.03984)
- [Fourier Neural Operator (FNO)](../../../../MyNotes/3D%20printing/Ph%20D%20Research/研究筆記/Fourier%20Neural%20Operator%20%28FNO%29.md)




----
 ## Learning sources 

### Websites
- https://databookuw.com/
有很多data-driven method 的教學影片和資料。
書需要買，資料和 test code 免費提供

- [PINN 作者的Github](https://github.com/maziarraissi/PINNs)
- [PINN for N-S Equation](https://github.com/Shengfeng233/PINN-for-NS-equation)
一個新加坡的學生的 repository

### video 
- [Physics Informed Machine Learning: High Level Overview of AI and ML in Science and Engineering](https://www.youtube.com/watch?v=JoFW2uSd3Uo&list=PLMrJAkhIeNNQ0BaKuBKY43k4xMo6NSbBa&ab_channel=SteveBrunton)
 
 ---
 
## **Work Flow**
## 1. decide on problem 定義問題
我們要模擬的問題是什麼?
輸入和輸出各是什麼? 我們想知道什麼和什麼之間的關係?

## 2. curate data 規劃資料
需要什麼樣的資料來餵給模型? 需要監控、紀錄什麼類型的資訊?
照片、聲音等等

### 會遇到的問題
1. 資料量
> how much data is enough to model ?

data augmentation 
對原始資料進行 transformation (角度轉換/ 放大/縮小)
但本質現象不變，以獲取更多資料作為訓練資料

2. 結果受限於訓練資料
模型中得到的最佳解通常都是由在訓練資料中，去找出來的，所以，如果今天需要解決的是一個優化的設計問題，我們應該如何從現有過去的成果中，找出更好的解?
(beyond your training data)

> We  need to generalize our model to design space

3. 有些極端事件很難有資料可以提供做為訓練
極端事件，例如海嘯或是大地震，這種發生機率較低的事件，就不容易有很多的資料可提供模型來訓練，也因此不容易去做預測

4. 隱藏的變數
事實上，我們並沒辦法得到 系統 / 現象 中每個重要的變數/參數，重點在於如何建立模型來還原與解釋現象背後的原因。

5.  模型也要有不確定性
> it is better to provide some uncertainty to the digital twin.

可以接受模型所提供的預測結果有個範圍，而非只是一個數值，而這個範圍，我們可以需要知道其上下限，對於訓練者而言可以根據這個不確定性的範圍大小，再給予模型相對應的資料進行模型的強化。

6. Coordinate is matter
Suitable coordinate made the equation describing the phenomenon more simple.

---

## 3. decide an architecture 規劃一個架構
選擇一個 模型的架構 , eg. RNN, Autoencoder, SINDy ,...etc

Q. 你要怎麼知道這個模型架構適合你目前要解的問題? 
當然我們都可以選擇模型來建立，來預測。不過模型只是依據你所提供的數據資料，進行計算，然後給出結果，但對於是否Make sense 或是 有代表的意義，還是需要由人去思考判斷。

因此，應該如何根據所研究的問題領域選擇適合的模型架構作為基礎是很重要的。

註: 在選擇某種架構，且將某個物理原則嵌入時，會有所謂的 **inductive bias 歸納偏見**的問題

## 4. craft a loss function 建立一個損失函數
如何修正你的模型，模型輸出怎樣的結果對你來說算好?
過去的neural network 是利用預測值與實際值得差異來表示損失函數, 例如

$\sum\limits_{data}||\hat{u}(x_j)-u(x_j)||^2_2$


而pinn 以這個基礎,再往前踏一步
以預測出來的這些結果,去計算它們的微分,(對某個變數)偏微分，並增加額外的損失函數,使這些微分的數值彼此間需要滿足某些已知的物理原則(eg. 動能守恆, 連續方程式)，使得pinn可以達到即使為稀疏的資料仍有相對較好的預測表現

## 6. employ optimization 選擇一個最佳化演算法
利用一個演算法來使得這個模型，改變相關的參數，並使得 loss function 最小化

而其中PINN 可以在每個階段都去嵌入，你所面對問題的相關physics equations / theory 

 

----

### PINN 求解 PDE 
![f968ce325e43a907e7b92178c64cb522.png](../../../../_resources/f968ce325e43a907e7b92178c64cb522.png)

參考流程: 
1. 建立一個 Neural network
2. 利用 **邊界條件 和 初始條件**建立訓練資料
3. 計算 損失函數(loss function)。 損失函數的來源包含 boundary condition 、neural network 和 initial conditions
4. 持續訓練 PINN ，使 loss function 最小


目前先在線上用colab 測試
有一些 經典的ODE 或 PDE 可以作為benchmark 

ODE 例如: damped oscillation motion , 
PDE 例如: Berg's equation , Possion Equation 

### Verification Questions 
- Berg's Equation 
$$
berg's\ equation\ with\ viscous\ form \\[3mm]
\begin{aligned}
u_t + uu_{x} &= \nu u_{xx}\\[3mm]
u(0,t) &= 0 \\[2mm]
u(1,t) &= 0 \\[2mm]
u(x,0) &= sin(2\pi x)
\end{aligned}
$$

- 2D Poisson's equation 

Possion Equation is not a time-dependent problem. 
$\nabla \phi = f(x,y)$ 


#### Network:
 - input : x,y 
 - output : u

$\nabla^2 \phi = -2\pi^2 sin(\pi x)sin(\pi y)$



```python

```




- Navier-stokes equation 


 
---

### Reading articles
- [ ] https://maziarraissi.github.io/PINNs/
- [ ]  https://colab.research.google.com/github/Frenz86/DeepLearning/blob/main/python/PINN/PINN_physicNN.ipynb
- [ ] [Physics Informed Neural Networks (PINNs): An Intuitive Guide](https://medium.com/@theo.wolf/physics-informed-neural-networks-a-simple-tutorial-with-pytorch-f28a890b874a)
- [ ] [Physics-informed Neural Networks: a simple tutorial with PyTorch](https://towardsdatascience.com/physics-informed-neural-networks-pinns-an-intuitive-guide-fff138069563/) 
- [ ] [Ben Moseley's blog](https://benmoseley.blog/my-research/so-what-is-a-physics-informed-neural-network/)
- [ ] [Intech open - Physics-Informed Neural Network: Principles and applications](https://www.intechopen.com/chapters/1191254)

預計完成: 
- [x] 將網路影片看完，並作筆記
- [x] 找一個資料進行實作
	- [x] 如果資料不足的情況下，去做 fitting 會出現的狀況
	    來說明 PINN 的效益。 可以在資料相對稀疏的條件下，仍然有精確的預測結果
		* [ ] [Example 1](https://github.com/TheodoreWolf/pinns)

- [ ] 把這個練習改到DED 上面


2025.Aug.24 目前把網路上的範例弄到 Colab 上面
還沒整理好

- https://www.youtube.com/watch?v=9-CvXh0Fibw&ab_channel=machinedecision

 

### 問題

 - Grey box model 和 PINN 的差別是什麼?
 ref. [Literature Review and Prospects for Grey-Box Models and PINN in Powertrain Technology](http://dx.doi.org/10.13140/RG.2.2.34632.64008)

- autograd的 形式或數量有沒有限制? 可以選擇的 candidate operator 有哪些

- 有人做real time 嗎?
- 做 experimental design 結合 pinn ?
  Yes,
  [@xie3DTemperatureField2022](http://dx.doi.org/10.1007%2Fs00170-021-08542-w)
  
- 如何結合FEM 的資料?
- 路徑規劃結合PINN 

- 有人進行延伸的變體包含
太多了，如果一個一個探討，做不完，除非是要做Review 的文章
 
結合正逆向的  forward / reverse 

[利用 PINN 去線上 識別 與控制 未知 PDE](https://arxiv.org/html/2408.03456v1)
 
---
利用 deep learning 求解 pde 的問題
https://zhuanlan.zhihu.com/p/578796228




 



  $L_T = \lambda_G L_G + \lambda_{BC} L_{BC} +\lambda_{IC} L_{IC}$