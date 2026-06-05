---
title: >-
  A deep-learning-based surrogate model for thermal signature prediction in
  laser 
updated: 2026-05-24  
created: 2024-12-12  
tags:
  - deep learning
  - surrogate model
---

## A deep-learning-based surrogate model for thermal signature prediction in laser metal deposition 

date: 2026.05.23

---

## The questions this research want to answer 
1. Why we need to predict the transient thermal signature?
2. What kind of machine learning methodology is proposed to acheive that?
3. How does the research ensure that the AI generated images are physically realistic?
4. How to validate the generated images?

---
### Generative Adversarial Nets Framework (GAN)
模型包含三個要素
G : Generator
E : Encoder
D : discriminator

鑑別器(discriminator) 會把輸出的結果，反向傳播(backpropagation)給產生器(generator) ，讓generator 改變權重


> Q. 三者的關係是什麼? 

生成器 Generator 接收一個random 的 latent vector 去生成 128 x 128大小的熱影像
鑑別器 Discriminator 接收一張照片，判斷這張照片是否為 第 i 層的熱影像
enocder 負責什麼? 

**Activation function**
Generator 的 acitivation function 通常是 ReLU 或是 Tanh 
Discriminator 的 activation function 通常是 LeakyReLU 



> Q. 輸入的 latent vector 大小 size 如何決定的?
>依據訓練的資料量大小，參數的多寡來決定
> 如果latent vector 的長度太小，表示整個latent space 的自由度不足以代表整個系統的變化
> 而當決定的長度太大,又會造成
> 
> Q. 為何 G、D 的 filter 大小要不同? 影響是什麼? 
 

LMD-cGAN 模型的功能
1. 預測在零件上，下一階段的熱特徵
2. 模擬金屬零件指定層的熱特徵


#### GAN vs. cGAN
cGAN 指的是 Conditional GAN
Conditional 的輸入代表什麼? 在某個特定層的熱影像
 原本的GAN 表示成
 $\min \limits_{G}\max \limits_{D} V(D,G) = E_{x~P_{data(x)}}[log(D(x))]+E_{z~P_z(z)}[log(1-D(G(Z)))]$
 
 cGAN 則是加了 $|y_i$
 $\min \limits_{G}\max \limits_{D} V(D,G) = E_{x~P_{data(x)}}[log(D(x|y_i))]+E_{z~P_z~(z)}[log(1-D(G(Z|y_i)))]$

 LMD 製程本身具有堆疊效應( 會受上一個狀態影響)
由於需要指定特定層作為一個資料的標籤
如果是單純用GAN , 模型就不會管你是那一層的資料
反正看起來都是一片亮亮的光點

而在文末, 作者提到可以將其他的物理參數或製程參數作為訓練的輸入, 因此這個condition , 在未來研究中也可以包含其他的參數. 或是將一狗票參數轉換成一個特徵向量丟進去
 

### Neural network 的架構 

size of the input images: 128x 128 
1 channel , only x,y and the temperature 

**Discriminator** 
input : a thermal image , size : 128 x 128 
Convolution layer : stride 2 , padding : same 
activation layer : LeakyRelu , with alpha = 0.2 
filter size 5x5
output : 


**Generator**
input : random latent vectors $R^{100\times1}$
output : a thermal images , size: 128 x 128
activation function : tanh
dropout rate 0.2 
filter size  3 x 3 

> Q. Why it choose LeakyRelu as the activation function ?

> Q. Why generator and discriminator use different size filter ?
> how to decide the suitable filter size? 

then do the feature extraction to obtain the latent vector 

> Q. What is latent vector? what does it represent for? 
why it need a random not sequential number ? 

訓練方式，把完成品的歷史熱圖像餵給模型去訓練
the thermal images are categorized layer by layer. 

利用 LMD-cGAN 生成熱像圖(同軸的熱影像資訊)

熱影像圖可以做什麼用?

### How to prepare the training data? 
explained in appendix 
- 每張照片都需要標注是那一層得到的, 在訓練過程中,作為一個標籤一同輸入給模型
- 每層的訓練圖片數不必然要相同
- 需要紀錄沒有缺陷的零件的熔池影像作為資料來源(無顯著表面的缺陷)

### Future works
1. 可以加入更多的材料, 製程參數來給LMD-cGAN 模型訓練, 以抓取更多的特徵
2. 利用其他的encoder 模型(ex. variational autoencoder), 加強溫度特徵預測的效率
3. 加入除了 thermal image 以外的物理量作為訓練的輸入資料來源
4. 擴展訓練的資料集大小

----


Q. 文中的age-cGAN  跟傳統的cGAN 差別是? 

### What is [Surrogate Model 代理模型](../../../../../undefined)? 


### Surrogate model for thermal signature prediction in LMD 


> Q. in-situ predict 和 emulate 的差別?
> 先解釋兩者的流程
> **predict**
>  given thermal image at layer o , input it to encoder
> calculate the latent vector z
> specify layer t , and input the latent vector z to Generator
> generator would generate a thermal image based on your input
> **emulation**
> We don't need encoder.
> Select a random latent vector from a distribution $N(0,I)$
> when input the latent vector to generator also provide a noise to generate the thermal image at specific layer
>
> 結論：
> prediction 藉由初始的熱影像去推斷出後續不同時間位置的熱影像
> emulation 比較像是利用實際的熱影像訓練出了一個模型環境
> 可以去模擬出任何一個時間下的熱影像
> 作為FEA 的代理模型

同樣利用Fronbenius norm 去計算prediction/ emulation 的圖片與實際訓練圖片的差異

$d_{ji,l}=F_{ji,l}/\sqrt{trace(x_{il}^T*x_{il}^T)}\\$
$where\ is \\F_{ji,l}=\sqrt{trace((x_{jl}-x_{il}^T)*(x_{jl}-x_{il}^T))}$



---

## Physical-Guided image selection (PGIS)

Use exisiting physical insights to filt out  and select from the generated thermal images.
利用物理的原則，選出那些生成的照片中，能符合物理原則的。把不合理的刪去。

提到利用FEA (Finite element analysis )，同作者的前一篇著作
可以利用FEA 生成製程過程中的同軸熔池溫度 
Using [Moving heat source of 3D Goldak heat flux](../../../../../undefined) to simulate the thermal history. 



Structure : single wall for 60 layers high 


>Q. 如何將合理跟不合理進行量化? 
(Quantification of physics invalidity) 
本文的方法: 

計算 [Fronbenius 範數 (Fronbenius Norm)](../../../../../undefined)for specific layer's thermal image 

用什麼和什麼去比較
模型生成的照片和FEA 轉換的照片去比較，兩者的範數差異不可超過 $U_l$
代表模型生成的和FEA 模擬的每層的結果不能差異太大


文中提到一個定理 
>Q. Chebyshev's inequality 是什麼? 

$P(|X- \mu|\ge k\sigma)\le \Large{}\frac{1}{k^2}$
或如文中所寫
$P(|X- \mu|\le k\sigma)\ge 1-\Large{}\frac{1}{k^2}$

其中
$X是隨機變數$
$\mu$ 是這組變數的平均
$\sigma$是這組變數的標準差, 表示數據的離散程度
k是任意的大於零的常數, 代表幾個標準差

舉例:
當k =2 , 
$1-\frac{1}{k^2} = 0.75$
代表任何數據集中, 一定會有75%的數據點落在距離平均值2個標準差的範圍內

在文中, 應用作為計算PGIS 方法的閾值
定義使用者期望的抽樣效率 $C_l$, 例如 $C_l=50\%$  代表有50%的生成圖片可以被接受
接著, 計算
$\hat U_l = \overline F_{il}^T + S_l/\sqrt{1-C_l}$

where is 
$S_l = \sqrt{\sum\limits_{i=1}^{N_l}(F_{il}^T-\overline F_{il}^T)^2/(N_l-1)}$


## Ref.
- Goodfellow, I. J., Pouget-Abadie, J., Mirza, M., Xu, B., Warde-Farley, D., Ozair, S., Courville, A., & Bengio, Y. (2014). Generative Adversarial Networks (arXiv:1406.2661). arXiv. https://doi.org/10.48550/arXiv.1406.2661

- Guo, S., Guo, W., Bian, L., & Guo, Y. B. (2023). A deep-learning-based surrogate model for thermal signature prediction in laser metal deposition. IEEE Transactions on Automation Science and Engineering. https://doi.org/10.1109/tase.2022.3158204

- [NVIDIA PhysicsNeMo](https://developer.nvidia.com/physicsnemo)
	 - [PhysicsNeMo - github](https://github.com/NVIDIA/physicsnemo)
>NVIDIA PhysicsNeMo is an open-source deep-learning framework for building, training, fine-tuning, and inferring Physics AI models using state-of-the-art SciML methods for AI4Science and engineering


- [ADL4P](https://tum-pbs.github.io/ADL4P/)
Advanced Deep Learning for Physics
 Here is a free course to learn and the resources are open.


---

