## PINN(Physics-informed Neural Network)
## Why PINN ? 
- Experimental data is expensive
- Labeling data is time-consuming 
- Incorporate governing equations directly into the loss function

  (e.g., heat conduction, Navier-Stokes for melt pool) , constraining the solution space, 

    - improving generalization with limited data,
    - enhancing prediction reliability under unseen conditions 
    (e.g., different geometries or initial thermal states) compared to purely data-driven models


> PINN doesn’t learn about the environment through explorative trial and error (as RL or GA do) but is informed directly via the governing equation in its mathematical form.


## What is the difference between PINN and other method ?

if use multi-model, what is you pipeline? how does these training data flow into the models?
how to integrate these model, sequential , parallel or hybrid ?
how the data has been shared or transfered?


- What kind of the problem is good to use PINN and been verified ?
- What is the PINN cannot do ?


Main concept is to combine real data , FEM simulation results and PINN model to construct a hybrid model to predict the process results. 



## SINDy(Sparse Identification of nonlinear dynamics )


# Literature review

Compare the performance for different configuration             
which method fits best(sequential, parallel, hybrid)? 

文中提到很多不同的文獻的研究並說明使用的情境
以下列出幾個覺得有趣可能用的上的作為紀錄

-  Jin et al.[2021] 說明 computational cost of training  their PINNs was 5-10 times higher than tranditional computational fluid dynamics(CFD). They showed that this significantly improved both the training time and accuracy of the higher Reynolds number PINN.
- Chen et al. [2021] 結合PINNs 與 稀疏回歸 （他們自己的演算法）不僅可以得到微分方程的解也可以求得對他們從data 中得到的微分方程
    They showed that their method wad able to robustly discover a variety of differential equations, including the Burgers equation, Kuramoto-Sivashinsy equation, nonlinear Schrodinger equation, Navier-Stoke equations and reaction-diffusion equation
- Champion et al.[2019] they used autoencoder to learn representation of the state. The autoencoder was trained by using a loss function which tried to reconstruct example sanpshots of the state and match the temporal deriative of the latent coordinates to a library of candidate functions via sparse regression. 有一點像SINDy （不過還沒看完過內容）
- Yang at al.[2021a] combined PINNs with Bayesian interface. This approach allow them to both solve the differential equation and provide uncertainty estimates on the solutions , while natually accounting for noisy training data. **Limitation of their approach was that the cost of HMC(Hamiltonian Monte Carlo） typically scales poorly to large dataset size and only test case with up to serveral hundreds measurements.**


We seperate the DED process into three sections. 

1. Moving heat source 

利用PINN 做 移動熱源的溫度模擬

Kalyan, Anirudh, and Sundararajan Natarajan. ‘Numerical Simulation of Transient Heat Conduction With Moving Heat Source Using Physics Informed Neural Networks’. *International Journal of Mechanical System Dynamics* 5, no. 2 (2025): 345–53. [https://doi.org/10.1002/msd2.70031](https://doi.org/10.1002/msd2.70031).

Zhu, Qiming, Zeliang Liu, and Jinhui Yan. ‘Machine Learning for Metal Additive Manufacturing: Predicting Temperature and Melt Pool Fluid Dynamics Using Physics-Informed Neural Networks’. arXiv:2008.13547. Preprint, arXiv, 16 September 2020. [https://doi.org/10.48550/arXiv.2008.13547](https://doi.org/10.48550/arXiv.2008.13547).
利用PINN 針對FEM 以及解析解結果來比較 單焊道的熔池尺寸和冷卻速率

**!!! Note: why we discuss about the coolant rate and melt pool dimensions**

- A critical in metal AM is the cooling rate, which profoundly influences dendrite arm spacing, grain structure, micro-segregation, and hot cracking. 



2. Powder flow flux 

Need the review for the two phase flow 




3. Melt pool dynamics and materials solidification 


----------
## Research Gap


1. **Process parameters optimization**
2. **Multi-physics coupling analysis** 
3. **Defects prediction and material properties evaluation**
[x] **3D Temperature field prediction in Multi-layer DED**
    a. Multi-track and multi-layer modeling 
    

How to integrate the experimental data and in-situ data ? 


<ref from other literature >

**Review of PINN development** 
Ganga, Sai, and Ziya Uddin. 2024. ‘Exploring Physics-Informed Neural Networks: From Fundamentals to Applications in Complex Systems’. arXiv:2410.00422. Preprint, arXiv, October 1. [https://doi.org/10.48550/arXiv.2410.00422](https://doi.org/10.48550/arXiv.2410.00422).


1. There is a lack of PINN studies on industrial applications, and further investigation on how well PINNs can handle complex multi-physics and multi-scale applications can be carried out.
2. The development of new and efficient optimisation methods is a promising avenue for future study.
3. A primary drawback of PINN is the need to train the neural network, which might need a notably longer duration than other widely used numerical techniques. In order to reduce training times, research into creating pre-trained models or transfer learning strategies might be explored. 


----------

Ren, Zhiyuan, Shijie Zhou, Dong Liu, and Qihe Liu. ‘Physics-Informed Neural Networks: A Review of Methodological Evolution, Theoretical Foundations, and Interdisciplinary Frontiers Toward Next-Generation Scientific Computing’. *Applied Sciences* 15, no. 14 (2025): 8092. [https://doi.org/10.3390/app15148092](https://doi.org/10.3390/app15148092).


1. Optimization instability : in high-dimensional parameter spaces (d > 104), where gradient pathology causes 58% of training failures
2. Theoretical-computational gaps 


3. Hardware-algorithm co-design limitations


----------

Peng, Shitong, Shoulan Yang, Baoyun Gao, Weiwei Liu, Fengtao Wang, and Zijue Tang. ‘Prediction of 3D Temperature Field through Single 2D Temperature Data Based on Transfer Learning-Based PINN Model in Laser-Based Directed Energy Deposition’. *Journal of Manufacturing Processes* 138 (March 2025): 140–56. [https://doi.org/10.1016/j.jmapro.2025.02.015](https://doi.org/10.1016/j.jmapro.2025.02.015).


1. the research mainly focuses on single-track single layer temperature field prediction. Future research should extend the framework to predict multi-layer temperature distributions, particularly in more complex deposition processes
2. Transfer learning phase on the target task could reduce training time by 1/5 compared to pre-training on the source task, with even higher prediction accuracy.
3. Current PINN framework is far from perfect in terms of efficiency and accuracy.
4. The accuracy and practicality of the PINN are inherently dependent on the training data

 

----------

“Frontiers | The Old and the New: Can Physics-Informed Deep-Learning Replace Traditional Linear Solvers?” Accessed October 24, 2025. [https://www.frontiersin.org/journals/big-data/articles/10.3389/fdata.2021.669097/full](https://www.frontiersin.org/journals/big-data/articles/10.3389/fdata.2021.669097/full).


> Transfer-learning is a necessary operation to make PINN competitive with other solvers used in scientific computing. 


1. PINNs in the current state cannot yet replace traditional approaches.
2. To have a small number of units at the beginning of the network and a large number of units at the end of the network is beneficial to the PINN.
    Possible hypothesis (not confirmed yet) : 
    > This observation hints that initial hidden layers might responsible for encoding the low-frequencies components (fewer points are needed to represent low-frequency signals) and the following hidden layers are responsible for representing higher-frequency components (several points are needed to represent high-frequency signals)


3. The most impactful parameter for achieving a low training error is the activation function.

 smooth functions > using Tanh as the activation function
 non-differentiable / discrete function → using sigmoid functions 
 
 

----------

  
 Li, S., Wang, G., Di, Y., Wang, L., Wang, H., & Zhou, Q. (2023). A physics-informed neural network framework to predict 3D temperature field without labeled data in process of laser metal deposition. *Engineering Applications of Artificial Intelligence*, *120*, 105908. [https://doi.org/10.1016/j.engappai.2023.105908](https://doi.org/10.1016/j.engappai.2023.105908)
 


1. large amount of labeled temperature data required lots of cost since experimental measurements and numerical simulation are time-consuming and expensive. 
2. customized loss functions could be implemented according simulation scenario. 

 
 

----------
## Integrate the Simulation and Experimental Results 


- Simulation 
    Heat convection / powder flow flux / phase change  
    → Export the results as the training data
    Features :　Thermal Field / Temp. Distribution
    
- Experiment

Experiment design and find the optimal process parameters range


    - in-situ data collection 

in this article, mentioned that 

    The advantage of this approach is that simulation or experimental data can be easily incorporated without over-constraining the model. Additionally, there is no minimum required dataset size for the model to converge.

Sharma, R., and Y. B. Guo. ‘Thermal-Mechanical Physics Informed Deep Learning For Fast Prediction of Thermal Stress Evolution in Laser Metal Deposition’. arXiv:2412.18786. Preprint, arXiv, 25 December 2024. [https://doi.org/10.48550/arXiv.2412.18786](https://doi.org/10.48550/arXiv.2412.18786).


----------
# How to verify 


## Current Benchmark 

Ref to the below literature, listing the benchmarking PDEs. 

- Burgers equation 
- Wave equation 
- Heat equation with Dirichlet boundary condition 
- Heat equation with Neumann boundary conditions 
- Advection equation 
- Reaction equation 

Wang, Yicheng, Xiaotian Han, Chia-Yuan Chang, Daochen Zha, Ulisses Braga-Neto, and Xia Hu. “Auto-PINN: Understanding and Optimizing Physics-Informed Neural Architecture.” arXiv:2205.13748. Preprint, arXiv, November 27, 2023. [https://doi.org/10.48550/arXiv.2205.13748](https://doi.org/10.48550/arXiv.2205.13748).


----------
## Process Optimization 



## Verification index
- Well roughness 
- Good material strength 
- Defection free
- Nice geometric accuracy


> A success prediction case is perfect proof without explanation


----------
## PINN Implementation 



## Governing Equations 

ref to these two literatures

Li, S., Wang, G., Di, Y., Wang, L., Wang, H., & Zhou, Q. (2023). A physics-informed neural network framework to predict 3D temperature field without labeled data in process of laser metal deposition. *Engineering Applications of Artificial Intelligence*, *120*, 105908. [https://doi.org/10.1016/j.engappai.2023.105908](https://doi.org/10.1016/j.engappai.2023.105908)

Faegh, M., Sanvelly, R. R., Arabpoor, R., Rao, P., Mukherjee, T., & Haghighi, A. (2025). Physics-Informed Neural Networks for Thermal Modeling Transferable Across Paths, Print Parameters, and Beam Profiles. *Additive Manufacturing*, 105060. [https://doi.org/10.1016/j.addma.2025.105060](https://doi.org/10.1016/j.addma.2025.105060)


There are some assumption in this. Please note! Please consider them as the future job. 
Assumptions 

    a. 
    b. 
    c. 
    d. 
    e. 


1. Heat conduction
    
    $$\frac{\partial \rho C_p T}{\partial t} = [\frac{\partial}{\partial x}(k\frac{\partial T}{\partial x})+ \frac{\partial}{\partial y}(k\frac{\partial T}{\partial y})+\frac{\partial}{\partial z}(k\frac{\partial T}{\partial z})]+ \dot{Q_{laser}}(x,t) , x\in \Omega , t \in T$$
    where is 
    $$\dot Q_{laser}(x,t) =$$
    
2. Boundary conditions 

Side 

    $$-k\frac{\partial T}{\partial \vec{n}}=q_c + q_r , x \in \partial \Omega$$
    $$q_c = h_c (T- T_a)$$
    $$q_r = \sigma \epsilon (T^4-T_a^4)$$

where h is the heat convection coefficient between air and substrate, $$T_a$$ is the ambient temperature , $$\sigma$$ is the stefan-Boltzmann constant, and $$\epsilon$$ is the heat radiation coefficient


3. Moving heat source 

$$Q(x,y,z,t)= \frac{6\sqrt{3\eta}P}{\pi \sqrt{\pi}\cdot abc} exp(-3\cdot r_0^2)$$

$$r_0^2 = \frac{(x-(vt+x_0))^2}{R^2_a}+ \frac{(y-y_0)^2}{R^2_b}+\frac{(z-z_0)^2}{R^2_c}$$


## Loss Functions 

$$L_{Total} = \lambda_{pde}L_{pde}+\lambda_{init} L_{init}+\lambda_{BC}L_{BC}$$

$$L_{pde} = \frac{1}{N_p} \sum\limits^{N_p}_{i=1} R^2_{pde}$$

$$L_{init} = \frac{1}{N_o} \sum\limits^{N_o}_{i=1} R^2_{init}$$

$$L_{BC} = \frac{1}{N_b} \sum\limits^{N_b}_{i=1} R^2_{BC}$$



----------
## Improvement for programming 
1. setup a automation working flow and checking the basic params before execute the real case 

建立一個工作流程與測試的方式，例如
可以一次測試多個不同的參數的結果(loss)，不用一個一個測試
另外是 nn 的hyper parameter 也需要這樣的流程來優化
多看幾篇nn 優化的文章再來決定，先蒐集並同時測試
再來看怎麼改善

----------
# Questions
## mesh free method ?
    因為 PINN 不需要去切網格，所以說是 Mesh free method 
    
    PINN 的方式
- DARTS(Differentable architechture search)
## real time optimization or prediction 嗎?
## experimental design 結合 pinn ?
    有。
    Xie, Jibing, Ze Chai, Luming Xu, Xukai Ren, Sheng Liu, and Xiaoqi Chen. ‘3D Temperature Field Prediction in Direct Energy Deposition of Metals Using Physics Informed Neural Network’. *The International Journal of Advanced Manufacturing Technology* 119, no. 5 (2022): 3449–68. [https://doi.org/10.1007/s00170-021-08542-w](https://doi.org/10.1007/s00170-021-08542-w). 





## 如何結FEM 的資料?

github 有人分享mat 檔案


## PINN 和Surrogate model 有明顯區別嗎? 




## PINN 模擬的挑戰
- 尺度差異很大的模擬如何進行? 
    差異大? 怎樣的差異算大? 多少的scale ratio 
- 結合多種物理量(Multi-physics) 的模擬




## How to use gekko to optimize the hyperparmeters of model  
    - [GEKKO](https://gekko.readthedocs.io/en/latest/index.html)


## 路徑規劃結合PINN application case study 

K. Ren et al., ‘Integrated Numerical Modelling and Deep Learning for Multi-Layer Cube Deposition Planning in Laser Aided Additive Manufacturing’, *Virtual and Physical Prototyping* 16, no. 3 (2021): 318–32, [https://doi.org/10.1080/17452759.2021.1922714](https://doi.org/10.1080/17452759.2021.1922714).


> employs a Temperature-Pattern Recurrent Neural Networks (TP-RNN) model to predict the temperature field after the next layer deposition for each of the candidate infill toolpaths
![](https://paper-attachments.dropboxusercontent.com/s_20D46C261DD6400212F232E6951E69BDAAA5B7DDF1B429AC4D7287D409B5638F_1762992609554_image.png)

    Chi Zhang et al., ‘Influence of Wire-Arc Additive Manufacturing Path Planning Strategy on the Residual Stress Status in One Single Buildup Layer’, *The International Journal of Advanced Manufacturing Technology* 111, no. 3 (2020): 797–806, [https://doi.org/10.1007/s00170-020-06178-w](https://doi.org/10.1007/s00170-020-06178-w).
    WAAM 的製程方式。 單層沉積，四種不同路徑模式，比較最終結果的殘留應力差異
    
![](https://paper-attachments.dropboxusercontent.com/s_20D46C261DD6400212F232E6951E69BDAAA5B7DDF1B429AC4D7287D409B5638F_1763019528161_image.png)

    
![](https://paper-attachments.dropboxusercontent.com/s_20D46C261DD6400212F232E6951E69BDAAA5B7DDF1B429AC4D7287D409B5638F_1763019552025_image.png)


利用 offset 的策略產生較少的殘留應力 (case d < case c < case b < case a)


## What is the collection points? How do i obtain for that? 
    What if the collection points are located at specific region or the functioins feature obviously exist regional extreme gradient, does that affect the accuracy of the model?  

 
 

##  what is stochastic gradient descent?



----------
## Reference resources 
[ ] [(2 条消息) 利用 PINN 解热传导方程的原理与实现 - 知乎](https://zhuanlan.zhihu.com/p/5968643396)
[ ] [(4 条消息) PINN的一些坑和经验 - 知乎](https://zhuanlan.zhihu.com/p/1963625709059675474)
[ ] [(4 条消息) 内嵌物理知识神经网络（PINN）是个坑吗？ - 知乎](https://zhuanlan.zhihu.com/p/468748367)
[ ] [GitHub - MasterMeep/Heat-Equation-PINN-prediction](https://github.com/MasterMeep/Heat-Equation-PINN-prediction)
[ ] [GitHub - J-wq/Physics-Informed-ML: The repository summarizes the work from Voigt and Moeckel about physic informed neural networks and their application to dynamic heat conduction problems in material processing.](https://github.com/J-wq/Physics-Informed-ML)
[ ] [GitHub - joon-stack/physics-informed-surrogate-modeling: Developing data-efficient (labeled data) surrogate model using physics-informed loss and data](https://github.com/joon-stack/physics-informed-surrogate-modeling)
[ ] https://github.com/ComputationalDomain/PINNs/tree/main/Cylinder-Wake
[ ] [Physics-Informed Neural Networks for Estimating Convective Heat Transfer in Jet Impingement Cooling: A Comparison with Conjugate Heat Transfer Simulations](https://arxiv.org/pdf/2507.09356)


## todo 
[x] PINN 首稿
[ ] MRO 修補的部分資料
[ ] 看兩篇先前沒看的論文


