---
title: >-
  [Seminar - Sep.16] Advanced vibration analysis techniques for predictive
  maintenance 4.0 in the oil and gas industry 
updated: 2025-12-10 02:15:46Z
created: 2025-09-16 11:56:25Z
tags:
  - ph course
  - seminar
---

# Topics : Advanced vibration analysis techniques for predictive maintenance 4.0 in the oil and gas industry 

date: Sep.16 

## Background
講者Dr. Alex Ong Zhi Chao 研究領域為結構的震動分析。談到在如何利用量測到的震動信號，進行分析，進行問題診斷，並做出預先的維修處置以降低停機、生產不良品的損失甚至是更嚴重的危害。

## Methods 
主要利用加速規進行震動信號的量測，以及利用相機抓取每禎每一像素的變化，轉換成實際設備的震動資訊。後續進行時域或頻域的頻率解析。

>[!Note]
利用影像判斷品質會受相機的解析度(Resolution)與擷取頻率(Frame per second,FPS)

### Operating Deflection shape analysis (ODS) 

屬於傳統的結構震動分析方法。
利用在結構上不同的位置放置加速規，來設備在特定操作條件下的不同位置的震動大小
並將所得的震動信號利用軟體整合，將整個結構在此特定震動頻率下的模態模擬出來。
並會利用模擬軟體建置一個相同情境進行兩者的比較。

> [!Note] Faults Diagnosis
> 分成四個不同階段
> 1. Damage presence 損傷出現的辨識
> 2. Damage location 定位出損傷位置
> 3. Damage severity 損傷的嚴重程度
> 4. Remaining useful life 剩餘的可操作時間(RUL)


## Deep Generative AI based Fault diagnosis system for predictive maintenance 

講者提了許多個不同的模型並比較模型間的準確度與差異。

所面臨的問題是
- 若利用深度學習模型進行特徵的辨識與預測，需要大量的資料蒐集。

>若所提供給模型的訓練資料不平衡(unbalance) 會造成模型準確性的下降。 eg. 訓練的資料大多都是正常狀態的震動信號，辨別不出異常、損壞的信號特徵。
>而在多數的情況下，所蒐集到的也都是健康的信號居多，因此就衍伸到下個問題


- 如何生成合成資料(synthetic data) ?
	- 如何生成夠長的合成資料?
	- 如何生成不同操作條件下的合成資料?

講者利用GAN以及其變體進行研究探討比較，多個不同的方法，而這些變體是為了要解決上述的問題

其中包含
1. WGAN-GP(Enhanced wasserstein GAN with gradient panalties)
利用Gradient panalties 來提高訓練模型的穩定性，讓模型可以順利收斂並且

2. Dual Cross Frequency Attention, DCFA Blocks
目的在解決傳統的GAN 模型所生成的信號較短，可以提升模型辨識的準確性並且避免模式崩潰(mode collapes)與不同操作條件下的泛用性

3.  Sequent Information Conditional Blocks, SICBs)
利用SICBs 生成多種操作條件下的合成時間數據，增加合成數據的多樣性

  
### Simularity and Diversity 
在比較模型生成與實際量測所得信號的評估，提到兩個指標相似性(simularity) 與 多樣性(diversity) 。

> [!Note]
> 相似性為了說明合成的數據資料與真實故障數據的接近程度
> 多樣性為了說明所生成的數據涵蓋了各種不同的操作條件、故障的程度與故障模式

比較simularity 利用的指標有
- Maximum mean discrepancy (MMD)
- Pearson correlation Coefficient(PCC)
- Kullback-Leibler divergence(KLD)

比較diversity 的指標有
- Entropy

---
### Ablation study 
> 通過逐漸移除或是有系統性的測試，來對比在模型中加入不同模組/功能對於結果的影響與貢獻

講者比較的變數有:
- dataset size
- training time
- data status (healthy data / faulty data)

>[!Note]
>使用的dataset size 不一定越長越準確，但是需要有一定的數據長度
>利用健康的設備資訊做為模型輸入，訓練的效果比較好
 

### Takeaway
- 目前關於熔池影像的研究，也有使用GAN 模型方法，一個為震動信號，自己的研究為影像的信號
可以試著參考講者的方法以及評估的指標。
- 閱讀熔池影像利用GAN模型，並未注意到有提到不穩定或是模式崩塌的說明，可再進行相關的搜尋。
- 講者的方法為: healthy data + random noise -> synthetic data
  若類比到熔池影像，is it possible that (normal image + image noise) -> defect melt pool image?

