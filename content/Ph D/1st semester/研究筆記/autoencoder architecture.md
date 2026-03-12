---
title: autoencoder architecture
updated: 2025-10-19 02:58:51Z
created: 2025-09-10 13:32:17Z
completed?: no
---

## autoencoder architecture 

- [ ] 利用 autoencoder 去處理 影像
	pytorch 或是 keras 處理同軸和側掛的影像
 
    先用keras + tensorflow (公司電腦)


紀錄Melt pool 影像，要訓練有幾個問題:
- 影像需要前處理嗎?
- 影像會與時間有關，如何將這個資訊整合進去
- 影像會和參數有關，如何將這個資訊整合進去

用 [ViT](https://github.com/google-research/vision_transformer) 或 ViT-G試試看

註: ViT 是google 團隊發表，利用Transformer 架構進行圖片的分類

[參考影片1 - Vision Transformer Quick Guide - Theory and Code in (almost) 15 min](https://www.youtube.com/watch?v=j3VNqtJUoz0)
[Self Attention Operation](../../../../undefined){#multi-head-attention}

ViT 的流程
1. 把圖片轉換成序列化的資訊(split image)
   這個過程稱為 patching
   將輸入圖片切割成數個指定大小的圖片，

2. 

3. linear projection


----

## Questions 

- CLS Tokens 
	- it is a dummy input representing as a positional embedding.
	 - learnable variables. 

- colab 上傳照片，隔天再打開，卻消失了，是不是表示需要把檔案/dataset 儲存在另外一個空間
  再讓模型去讀取?
  
  ![檔案消失](../../../../_resources/d4617f3f08510280d616cfd1cc96f0e4.png)


---
- [參考](https://medium.com/@andy6804tw/%E8%AB%96%E6%96%87%E5%B0%8E%E8%AE%80-vision-transformer-vit-%E9%99%84%E7%A8%8B%E5%BC%8F%E7%A2%BC%E5%AF%A6%E4%BD%9C-379306ea2fb)



---

### 影像前處理: 
- spatter reduction
>A stacked convolutional denoising autoencoder (SCDAE) is commonly used to utilize this latent representation to reduce undesired noises from an image[ref 1]


- melt pool orientation identification

> . Yang et al. [ref 2] utilized the Canny edge algorithm to identify the melt pool’s shape and orientation from the MPM images


不過這個原文的方法，需要手動去設定 threshold ，而在 [ref 3.] 利用CNN 自動去抓取熔池的特徵，並計算  傾斜角度 $\theta$




## PINN 

- [ ] 完成一篇讀書心得
- [ ] 投影片 - Background and application




## REF 
[ref 1] Vincent P, Larochelle H, Lajoie I, Bengio Y, Manzagol P-A, Bottou L. Stacked denoising autoencoders: Learning useful representations in a deep network with a local denoising criterion. J Mach Learn Res 2010;11(12).

 [ref 2] Yang Z, Lu Y, Yeung H, Krishnamurty S. Investigation of deep learning for real-time melt pool classification in additive manufacturing. In: 2019 IEEE 15th international conference on automation science and engineering. CASE, IEEE; 2019, p. 640–7.

[ref 3]Kim, Jaehyuk, Zhuo Yang, Hyunwoong Ko, Hyunbo Cho和Yan Lu. 2023年. 《Deep Learning-Based Data Registration of Melt-Pool-Monitoring Images for Laser Powder Bed Fusion Additive Manufacturing》. Journal of Manufacturing Systems 68 (六月): 117–29. https://doi.org/10.1016/j.jmsy.2023.03.006.
