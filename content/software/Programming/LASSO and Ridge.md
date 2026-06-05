---
title: 'LASSO and Ridge '
updated: 2026-04-01 14:03:29Z
created: 2024-08-19 13:25:19Z
 
tags:
  - machine learning
---

# LASSO(Least absolute shrinkage and selection operator)

## 迴歸分析是什麼? 
最常見的表示
B為我們量測觀察到的數值(矩陣)，A代表我們覺得可能有相關影響的特徵
X則是想要求得的關係

$AX=B$


## 為什麼需要正則化? 

為了防止過擬合，來給目標函數加上限制，或是在建立的過程直接忽略不重要的特徵.。也就是讓上述式子中的X盡可能的稀疏，允許為零的項存在(代表忽略那些不重要的項次)，最終的X也就代表了A特徵中，與量測的數值B相關性最高的。

正則化又會分成兩種, 一個是 L~1~ , 一個是L~2~

**L~1~ Norm Lasso**  
限制整個方程式的總特徵數，丟棄相對不重要的特徵，不進行擬合。相較比較不重要的特徵，會被給予0的係數。
關於L1
- 絕對值
- 特徵選擇
- 稀疏性


$Cost = \frac{1}{n}\sum^n_{i=1}(y_i-\bar y_i)^2+\lambda \sum^m_{i=1}|w_i|$

**L~2~ Norm Ridge Regression** 
限制公式的複雜度，給式子加上其他限制
經過$L_2$ 正規化的係數，比較不重要的項次趨近於0，但不會為零
$Cost = \frac{1}{n}\sum^n_{i=1}(y_i-\bar y_i)^2+\lambda \sum^m_{i=1}w_i^2$
關於L2
- 平方
- 穩定性
- 解決共線性(Colinearity)


其中 
m 代表特徵的數量
n 代表資料的數量
y~i~ 實際目標值
$\bar y_i$ 預測的目標值

與一般的懲罰函數(Loss function) 差別是加了一個常數的懲罰項
如果這個特徵對於結果影響不大, 則係數會趨近於0
意思是，這個增加的Loss function 會將與所求結果相關性高的特徵highlight 



### python 例
- [resource](https://www.youtube.com/watch?v=n2_1BW8dTBA&ab_channel=NathanKutz)

```python
import numpy as np 
from scipy.optimize import fmin
import matplotlib.pyplot  as plt 

# data set 
x = [0.1, 0.4, 0.7,1.2, 1.3, 1.7, 2.2, 2.8, 3.0, 4.0, 4.3, 4.4, 4.9]
y = [0.5,0.9,1.1, 1.5, 1.5,2.0,2.2,2.8,2.7,3.0,3.5,3.8,3.0]
# plot the original data set
plt.plot(x,y,'ro')

# define the optimization function 
def line_l2_fit(x0,x,y):
    e = sum((np.dot(x0[0],x) + x0[1] - y)**2)
    return e
def line_l1_fit(x0,x,y):
    e = sum(abs(np.dot(x0[0],x) + x0[1] - y))
    return e
	
# define l1 & l2 functoin
# find the coef. of regression function 
# fmin(<function name>, <init val>,<args>)
coef_l1 = fmin(line_l1_fit,[1,1],(x,y))
coef_l2 = fmin(line_l2_fit,[1,1],(x,y))

# fitting 
xs = np.linspace(0,5,100)
y1 = coef_l1[0]*xs + coef_l1[1]
y2  = coef_l2[0]*xs + coef_l2[1]

# plot the fitting line 
plt.plot(x,y,'ro')
plt.plot(xs,y1,label='l1 fitting')
plt.plot(xs,y2,'g--',label= 'l2 fitting')
plt.legend()
plt.grid()
```
![c8b1e618bbe09329d31ffb12e8c0f6b7.png](../../../../assets/c8b1e618bbe09329d31ffb12e8c0f6b7.png)

l2 的線會被離群值往下拉
因為計算的方式是求取最小**平方差**
 
---- 

# Ridge Regression 嶺回歸
又被稱為 L~2~ norm ，Tikhonov regularization

增加 regularization factor 去消除 ill- conditional 的問題
當A矩陣中存在有些特徵彼此之間高度線性相關

## 閱讀
- https://medium.com/chung-yi/ml%E5%85%A5%E9%96%80-%E4%BA%8C%E5%8D%81%E4%BA%8C-ridge-regression-f638e1887a7e
- https://zhuanlan.zhihu.com/p/132275334
- https://blog.csdn.net/qq_51320133/article/details/137395777


## Lasso vs. Ridge Regression Comparison

$Least\  Square\ Regression\\ L =||AX-B||_2$

$Ridge\ Regression \\ L=||AX-B||_2+ \alpha |||X||_2$

$Lasso \\ L=||AX-B||_2+ \lambda |||X||_1$

$Elastic\ Net \\ L=||AX-B||_2+ \lambda |||X||_1 + \alpha |||X||_2$

Elastic 就是兩個都要，綜合L1和L2的懲罰項次

## 什麼叫 convex optimization ?
convex function 像是一個碗公，只有一個最佳的解(不論是最大值或最小值)，不會出現局部最佳解，所以最佳化過程中一定會找到最佳解


## 優點 


## 缺點


sequential threshold least square 
- 如果維度大的系統, 容易無法求解或不好收斂
