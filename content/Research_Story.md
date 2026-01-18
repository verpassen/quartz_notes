# Research Story

> as the Seminar slides concepts 
# Problem you want to solve


## 1. Process optimization
    - Target 
    > Adjust the process parameters real-time
    >  adjust the parameters as Laser Power, feed rate and height (standoff distance)
## 2. Predict the process  parameters in advance
## 3. Predict the performance in advance
    - Response of prediction 
        - Roughness
        - Temperature
        - stress(option)
        - phase or defects (option)


- Building a digital twin of process(metal additive manufacturing)

What is the challenge? 
Why choose thermal signature ? 
What is the correlation between temperature and the mechanical properties ? 
.


----------
# Background


## DED Introduction 



## What’s the challenge we have ?
1. DED 


2. Machine learning on Additive manufacturing 
## Current challenges for SciML
    1. 由多個方程式才能得到結果 > 計算成本高
    如果問題維度越大越複雜,需要的計算成本就越高。
    本身問題的相關變數多,彼此互相耦合，模型本身需要掌控的控制參數也多等等
    PINNs often contain millions of free parameters and it is unclear how best to optimise them. Indeed, in contrast to traditional numerical methods, their theoretical convergence properties are not well understood.


    ps. 第九個書籤紀錄多個文獻關於PINN 收斂性的研究


    2. Ill-posedness
    Give b not sufficient to uniquely determine a
    通常還要再給定額外的限制條件
    Stiff partial differential equations 
    會遇到的狀況是收斂性不佳以及準確性不夠好?
    目前準確性大約幾%? 
     ref to <[Intech open](https://www.intechopen.com/chapters/1191254)>


    3. Surffering from noise
    真實世界的資料往往夾帶著實際的訊息與雜訊
    如何將這些雜訊清理或是模型可以更強健不受這些雜訊的影響


    > Is the PINN can extract any equations from real world data?
    > Forward and inversion question applied pinn is there any difference


## Challenges of PINNs: 

Haghighat, E., Raissi, M., Moure, A., Gomez, H., & Juanes, R. (2021). A physics-informed deep learning framework for inversion and surrogate modeling in solid mechanics. *Computer Methods in Applied Mechanics and Engineering*, *379*, 113741. [https://doi.org/10.1016/j.cma.2021.113741](https://doi.org/10.1016/j.cma.2021.113741)


1. Generalization ability
2. Training efficiency 
3. Optimization limits
4. Accuracy 



# What is your approach ? 

What is the limit using the Finite element method / Computational Fluid dynamics?
Require vast computational resources 

 

## Why Machine learning in additive manufacturing ? 

Problem domain 

- defects detection 
- Process optimization and monitoring, property & Quality prediction
- Regression 
- Classification
![](https://paper-attachments.dropboxusercontent.com/s_20D46C261DD6400212F232E6951E69BDAAA5B7DDF1B429AC4D7287D409B5638F_1761522463578_image.png)


Herzog, T., M. Brandt, A. Trinchi, A. Sola, and A. Molotnikov. ‘Process Monitoring and Machine Learning for Defect Detection in Laser-Based Metal Additive Manufacturing’. *Journal of Intelligent Manufacturing* 35, no. 4 (2024): 1407–37. [https://doi.org/10.1007/s10845-023-02119-y](https://doi.org/10.1007/s10845-023-02119-y).


----------
## Machine learning models
- LMD-cGAN
- PINN
- SINDy
- Surrogate model 


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





