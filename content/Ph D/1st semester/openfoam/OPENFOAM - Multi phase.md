---
title: OPENFOAM - Multi phase
updated: 2025-09-08 21:50:34Z
created: 2024-05-18 08:09:45Z
latitude: 25.03296940
longitude: 121.56541770
altitude: 0.0000
tags:
  - cfd
  - openfoam
---

# OPENFOAM - Multi phase 

## 閱讀資料
- https://www.cfdyna.com/Home/of_multiPhase.html


## 目標 
- 粉末流動

## 學習建議
(Nots from ai) 
1. 基礎知識準備
- 流體力學基礎：理解流體力學的基本概念，特別是雙相流（氣固兩相流）的理論，包括連續相和分散相的相互作用、顆粒動力學等。

- 計算流體力學（CFD）基礎：學習 CFD 的基本原理，如網格生成、數值方法（有限體積法）、湍流模型等。

- OpenFOAM 基礎：熟悉 OpenFOAM 的基本架構、文件結構、求解器和工具。

2. OpenFOAM 學習路徑
- 安裝與環境設置：首先安裝 OpenFOAM，並熟悉其運行環境（Linux 系統）。

- 官方文檔與教程：OpenFOAM 官方提供了豐富的文檔和教程，建議從基礎教程開始，逐步深入。

- 基礎案例學習：從簡單的單相流案例開始，如 cavity、pitzDaily 等，熟悉 OpenFOAM 的工作流程。

- 雙相流模型學習：學習 OpenFOAM 中的雙相流模型，如 Euler-Euler 模型（如 twoPhaseEulerFoam）或 Euler-Lagrange 模型（如 DPMFoam）。

3. 粉末雙相流模擬
- 顆粒模型選擇：根據你的需求選擇合適的顆粒模型，如離散元素法（DEM）或 Lagrangian 粒子追蹤法。

- 噴嘴幾何與網格生成：使用工具（如 blockMesh、snappyHexMesh）生成噴嘴的幾何和網格，確保網格質量適合雙相流模擬。

- 邊界條件與初始條件：設置合適的邊界條件和初始條件，特別是顆粒的注入條件。

- 求解器選擇與設置：選擇適合的求解器（如 twoPhaseEulerFoam 或 DPMFoam），並根據需要調整模型參數。

4. 進階學習與優化
- 湍流模型：學習並選擇合適的湍流模型（如 k-ε、k-ω、LES 等），以捕捉噴嘴內的湍流效應。

- 並行計算：學習如何使用 OpenFOAM 的並行計算功能，以加速模擬過程。

- 後處理與可視化：使用 ParaView 或其他工具進行結果的可視化和分析。

5. 資源推薦
- 書籍：
	- "The Finite Volume Method in Computational Fluid Dynamics" by F. Moukalled et al.
	- "Computational Methods for Fluid Dynamics" by Joel H. Ferziger and Milovan Perić.

- 在線資源：
	- [OpenFOAM 官方文檔](https://www.openfoam.com/documentation/overview)
	- [CFD Online](https://www.cfd-online.com/Jobs/listjobs.php?country=United+States)
	- [Online Course: Computational Fluid Dynamics (CFD) with high-performance Python programming](https://drzgan.github.io/Python_CFD/2.1D%20linear%20convection.html)


---

## 影片
- [[16th OpenFOAM Workshop] Machine learning aided CFD with OpenFOAM and PyTorch](https://www.youtube.com/watch?v=SYqiJYMqxTU&t=1591s&ab_channel=OpenFOAMJournal)

在目前筆記不多的情況下,先放同一個地方
以下內容從影片節錄

- [Multi-scale Modelling of Multi-phase Flows](https://www.tue.nl/en/research/research-groups/multi-scale-modelling-of-multi-phase-flows)

模擬的情境
[氣體溶入液體中的模擬](https://andreweiner.github.io/reveal.js/ofw2019_sgs_modeling.html#/1)
但因為特性的關係 boundary layer 所需的grid size 和 實際的物體的scale 相差甚大

相關的關鍵字: [subgrid scale modeling](https://link.springer.com/chapter/10.1007/978-3-642-46395-2_26), boundary layer model , DMD(Dynamic mode decomposition)

同樣的問題,如何去驗證這些模擬的結果？ 

### current work flow 
1. extract data from two-phase simulation
2. porcess and visualize data(Numpy, Pandas, Matplotlib)
3. train ML models (Multilayer perceptrons implemented in PyTorch)
4. export models to [TorchScript](https://docs.pytorch.org/docs/stable/jit.html#pytorch-functions-and-modules)
5. implement BCs in OpenFoam and compile
6. load ML models and perform simulations

講者自己整理,研究過程中的幾個個人的心得要點
1. finding good features of often hard
- use physical relations / intuition
- extract as many features as possible
- use automated feature selection
- **make sure that the features are available in your target application**

2. Learning the mapping that you really need
data-driven wall function
 a. collect boundary layer data
 b. learn $\hat y^+ \approx y^+(u^+) to replace analytical function$
 c. learn $\hat \tau_w \approx \tau_w(y_p, u_p)$ (apply typical normalization)


### related resources 
- [flowTorch](https://flowmodelingcontrol.github.io/flowtorch-docs/1.0/notebooks/dmd_intro.html)
  





