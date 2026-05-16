---
title: Overfitting & udnerfitting
updated: 2026-04-02 05:01:41Z
created: 2024-11-09 14:07:18Z
latitude: 22.55197590
longitude: 120.54875970
altitude: 0.0000
tags:
  - machine learning
  - overfitting
  - regularization
---

# Overfitting & udnerfitting

---
> Model's capacity is its ability to fit a wide variety of functions

對於模型的假設架構，會影響到所謂的Hypothesis space 
例如，將迴歸函數從線性改為高次多項式，可以增加hypothesis ，同時可以讓模型對數據有更高的capacity 

意思是指增加模型的參數數量囉? 
對，
you can increase the depth and the width of the neural network or change the connection and architecture to improve the effeciency for specific task 

---

首先需要提到 bias 和 variance 
利用資料訓練模型, 會討論到幾個問題
這個模型的預測與實際的結果差距如何？ 這個模型所預測的結果是否有很大的變動性？

![da0c7768362ba58828c90b3600c137f3.png](../../../../assets/da0c7768362ba58828c90b3600c137f3.png)

類似精度與準度的概念

從下圖可以看到,模型複雜度與偏誤的關係
當模型被簡化太多, 所得到的模型並不能很貼切的去描述實際的現象
我們稱為**underfitting** 
> high bias and low vairance

從模型所得到的結果是相對誤差較大的情況
但是, 當我們利用了過多的參數用來描述這個模型,
會造成**overfitting** 
> low bias and high variance

也就是過度貼近當下的這個資料
可能造成幾個問題

## 可能的問題
- **模型的遷移性不佳**
你用這個資料集訓練起來很準, 換了個資料後,就不準了
- **容易被noise 影響**
模型過於貼近訓練資料, 有些資料可能只是雜訊或是干擾,都被納入的情況,就可能在其他的情境下出現錯誤分類或是偏差的情況

下圖表示 bias-vairance tradoff
![3ece86b7215304e256478ac0b5e66397.png](../../../../assets/3ece86b7215304e256478ac0b5e66397.png)

bias 和 variance 的關係是反向的. 當其中一者增加, 另外一方則會相對的減少
所以找到一個適合的模型複雜度(或是剛剛好數量的參數來表達模型)是有其必要性


## 如何避免
1. 
因此,通常在進行訓練模型時的手法,都會將原本的資料集以8/2的比例去分配
區分成訓練集與驗證集
作為判斷模型是否有overfitting 或是 underfitting 的情況

2.  [交叉驗證 Cross Validation](../../../../../undefined)

3. 
正規化 regularization 
用來懲罰過度複雜的模型, 在標準的線性迴歸後面增加懲罰項次與係數
分成 
1. Lasso regularization : L~1~ regularization 
2. Ridge regularization : L~2~ regularization
3. Elastic net regularization : L~1~ and L~2~ regularization 

可以參考這篇
[[LASSO and Ridge]]


# Ref 
- [model selection and overfitting](https://www.nature.com/articles/nmeth.3968.pdf)
- [geek for geek - regularization in machine learning](https://www.geeksforgeeks.org/regularization-in-machine-learning/)