---
title: '[Seminar Dec. 02] Exploring Quantum Intelligent Robotics '
updated: 2026-01-01 00:49:14Z
created: 2025-12-02 15:02:40Z
---

Seminar Dec. 02 
N18141024
張耿賓

# Exploring Quantum Intelligent Robotics 
主題: Exploring Quantum Intelligent Robotics 
講者: Dr. Tien-Fu Lu 

講者一開始先介紹了他所來自的學院，University of Adelaide。很風趣地介紹了當地的特色，學校的地理位置

## Background 
講者首先說明當下關於機器學習的相關的挑戰，以下幾點條列
1. 資料模型隨著資料越來越龐大
2. 取樣資料處理的效率低下
3. 高維度問題的取樣資訊以及樣本缺乏
高維的狀態空間需要更多的訓練資料，也需要更多的計算時間與資源。
這些問題在遷移學習(環境條件不同)或是訓練樣本不足的情況下更明顯。
5. 最佳化的挑戰
傳統的強化學習(Reinforced Learning) 容易在過程中陷入局部的最佳解(Local optimal)，而不是全域的最佳解，因此會有所謂的Barren Plateau problem，使得深度學習的成果難以穩定收斂。

也因此，所相對應的需求包含
- 越來越大的算力需求
- 更大的資料中心

隨機而生的是整合量子計算的機器學習架構(Quantum Integrated Architecture,QIA) : 整合了量子演算法(Quantum algorithm) 以及傳統機器學習演算法。

對於量子整合計算的架構中，並非使用較多的量子比特就能有更佳的效率，過程中講者以一個倒單擺例子說明，選擇適合當下問題複雜度的模型，才能得到更有效率的結果。


## Technology 
對於量子計算的能力應用，講者雖有提到幾個限制，但其優異的計算能力(Exponetial computational power)，也讓IBM，Google 已投入這場算力競賽之中。
優勢包含
- 對於解決複雜問題
- 強化機械學習與最佳化
- 處理複雜資料的效率

### 量子計算的基本概念
- 量子比特 (Qubits) : 量子資訊的基本單位，可處於疊加態。
- Bloch sphere: 用於視覺化單個量子比特狀態的幾何表示。
- 量子變分電路(Variance Quantum Circuit,VQC) : 構成量子強化學習的基礎，用於編碼和處理狀態，是量子與經典算法結合的橋樑。
- 哈達瑪門 (Hadamard Gate) : 用於將量子比特置於疊加態的量子門

研究的三個基本元素
1. Quatum algorithm - Variational Quantum Circuit
2. Intelligence - Machine learning - reinforcment learning
3. Robotics - Cart-pole , Inverted pendulum 

### (Quantum Integrated Architecture = quantum algorithm + Classic ML)的挑戰
- 在最佳化過程中探索(Exploration)與開發(Exploitation)的權衡
在最佳化算法中，需要決定是否繼續在全局範圍中繼續擴大搜索範圍已找到更佳的解，或是在局部範圍中，精細畫條件，繼續搜尋更優解。

- 資料在量子電腦與傳統的電腦設備之間轉換也會出現延遲與硬體上的限制問題。

- 對於複雜系統需要去分析，所需的量子線路的級別(circuit scale)需要多少也需要去評估適當的等級
  
### 混合式的模型應用
- 利用 量子變分電路(Variance Quantum Circuit,VQC) 結合經典的神經網路的混和架構

![8f5515bb095cc3f54b208e967b7d13fa.png](../../../../../_resources/8f5515bb095cc3f54b208e967b7d13fa.png)

- 從環境輸入的觀察資訊，例如圖像，聲音等，是需要經過編碼的過程，才能進到模型中進行處理計算的
  
- 講者利用CartePole / 倒單擺 (inverted pendulum) 作為試驗的問題情境，試著利用量子的混和模型進行學習與控制。而結果展現比經典強化學習收斂速度更快的並且有更高穩定性

## 未來的挑戰
### - 實現更複雜的量子變分電路(QVC)
若能建立更複雜的QVC 架構，就能對更高自由度的複雜系統進行預測, 控制

### - 物理系統的控制
即使可以提前將模型的訓練好，但將數位雙生或模型的參數應用於實際的真實場景，模型還是需要調整與適應
(講者以駭客任務的一段影片進行闡述)

### - 優化架構設計
需要更多的研究來探討運用量子與經典的機器學習模型的組合，來達到更佳的運算效率與模型的性能。

#### - 克服硬體的限制
由於目前全球可用的量子電腦計算屬於稀缺資源，再者目前發展的量子電腦還須克服速度、錯誤率上的限制，才能達到更廣闊的應用面


## 延伸閱讀
- https://hackmd.io/@sqcs
- [IBM Quantum machine learning](https://quantum.cloud.ibm.com/learning/en/courses/quantum-machine-learning/introduction)