---
title: Nurbs curve(Non-uniform rational B-spline curve)
updated: 2026-01-12  
created: 2024-12-29 
 
tags:
  - nurbs curve
---

# Nurbs curve(Non-uniform rational B-spline curve)
 

nurbs 曲線由以下四項所定義:
1. 階數(degree)
2. 控制點(control point)
3. 節點(knots)
4. 估算法則(geometric algorithm) > 這個應該是basic function 

以下分別解釋
階數 為正整數。 
一條曲線的次數(order) 等於 (階數 + 1)

> the degree, number of knots and number of control points are related by formula
> m = n + p + 1 

控制點為一狗票點。控制點的最少數量為 (階數 + 1)
控制點數目為N 
控制點所構成多邊形

![](https://upload.wikimedia.org/wikipedia/commons/thumb/8/81/NURBstatic.svg/500px-NURBstatic.svg.png)



---

## Nurbs curve 數學表示式

$
\Large{C(u) = \frac{\sum_{i=0}^n N_{i,p}(u)w_i P_i }{\sum_{i=0}^n N_{i,p}(u)w_i}}
$

其中
$P_i$  為控制點
$w_i$  為控制點的權重
$N_{i,p}$ 為一般化B-spline 的基本函數。
一個 P階的基本函數我們可以這樣描述
$
\begin{aligned}
N_{i,0}(u) &= \begin{cases} 1&\ if\ u_i\le u \lt u_{i+1} \\ 
0 &\ if\ otherwise \end{cases}\\[3mm]
N_{i,p}(u) &= \frac{u-u_i}{u_{i+p}-u_i}N_{i,p-1}(u) +  \frac{u_{i+p+1}-u}{u_{i+p+1}-u_{i+1}}N_{i+1,p-1}(u)\\
\end{aligned}
$
其中 $u_i$ 所指的構成節點的向量 
$U= \{u_0,u_1,...,u_m\}$


## Nurbs 曲線的幾何特性

1.
$C(0)=P_0,\ C(1) =P_n$


2. Nurbs curves are invariant under perspective projections
看不懂什麼意思
invariant 指的是什麼?

> Nurbs curve 涵蓋了Bézier curve 的所有特性

Nurbs curve 屬於[Bézier Curve](../../../../../../../undefined) 的一般形式。

----

## 撰寫中

- why nurbs ?
 nurbs curve 有什麼不同的特性可以取代或是比其他特性的曲線更好?

我們可以來比較nurbs curve 和 Bézier Curve 、spline 的差異

> Nurbs curve are genuine generizations of nonrational B-spline form as well as rational and nonrational Bézier Curve and surfaces
> On Nurbs: A survey -  Les Piegl 


> Bernstein 多項式是 Bézier Curve的基礎
nurbs 曲線是 B-spline 的推廣，


B-spline 是 Bézier Curve的推廣，而 Nurbs curve 是 B-spline的一般化

- 已知的特徵，如何利用nurbs 進行擬合?
given a group of points or curve , how to express them in nurbs curve form?

1. **Define the points** 點資料
   這些幾何特徵的資料，需要參考某個基準座標系，給定2D/3D的座標資料

2. **Choose representation method** 選擇表現的形式
	i. 如果想要nurbs 曲線大概接近這些點，則把這些點當作是control points

	ii. 如果想要

----

把特性一個一個寫進去

**rational function**

$C(u) = \sum_{i=0}^nP_{i}R_{i,p}(u)\\[3mm]
R_{i,p}(u)=\frac{w_i N_{i,p}(u)}{\sum_{j=0}^n w_j N_{j,p}(u)}$ 

$R_{i,p}(u)$ 稱為 有理基本函數。決定這個曲線的基本特性


決定這個曲線
--
如何去表示曲線? 
表現的形式可以是
1. 參數式
如果是平面的圖形，我們可以定義一狗票的點
$C(u) = \{ X(u),Y(u) \}$

例如: 
一個半徑為1的圓 
$Circle(\theta) = \{ sin(\theta) , cos(\theta) \}$

2. 多項式
$y(x)=a_2 x^2 + a_1 x +a_0$

變數之間的關係形成一個多項式，來表示兩個變數或多個變數之間的變化



 
### Continuity 

$C^1\, Continuity$

分成一次微分與二次微分連續
曲線對於某個點的一次微分可以代表在該點上的切線方向
因此，一次微分連續代表著這個曲線在切線方向上的變化，不會突然從一個方向跳到另外一個方向，換言之，可以代表這個曲線是否平滑。

二次微分連續。
曲線的二次為曲線的曲率，換言之，

>曲線的一次微分代表切線方線的變化連續性
> 曲線的二次微分代表曲率的連續性


## 利用Nurbs 設計曲線
1. 畫出控制多變形 (control polygon)
2. 利用內插法得到點集合(a set of points)
3. 將曲線擬合至點集合上


## 待解決疑問，
- 如何處理nurbs curve 的微分
- 可以微分幾次?
- 微分後的代表特性?

- 如果basic function 沒有symmetric 就不算nurbs curve 嗎?
- basic function should be comply to the Bernstein polynomials ? 


## 應用
- CAD 建模
  可以將任意曲線以參數形式的方式表示，並且容易調整

- 電腦動畫特效
藉由調整權重與控制點，可以做到模擬物體或人物的細微動作，例如: 臉部表情或是連續的動作變化
  
- 製造加工
機械加工控制，在複雜的路徑可以利用Nurbs curve 來取代，在保證精度的條件下減少加工時間

- 建築/產品 設計
由於其容易調整且可以參數化的特性，可以利用nurbs 曲面建構隨意的曲面特徵。


## 參考閱讀/資源
- [On Nurbs: a survey](https://ieeexplore.ieee.org/document/67702)
- [The nurbs books](https://link.springer.com/book/10.1007/978-3-642-59223-2)
- [Interactive Computer graphics - Nurbs](https://sejmou.github.io/interactive-computer-graphics/nurbs.html)
- [演算法筆記 - surface](https://web.ntnu.edu.tw/~algo/Surface.html)

- [ ] [nurbs intro](https://libnurbs.sourceforge.net/old/nurbsintro.pdf)

### 書籍推薦

**Beginner**
- 《計算機圖形學：原理與實踐》（Computer Graphics: Principles and Practice）
作者：James D. Foley, Andries van Dam, Steven K. Feiner, John F. Hughes
這本書是計算機圖形學的經典教材，其中包含了 Bézier 曲線和 Bernstein 多項式的詳細介紹。

- 《曲線與曲面數學》（Curves and Surfaces for Computer Graphics）
作者：David Salomon
這本書專注於計算機圖形學中的曲線和曲面數學，內容淺顯易懂，適合初學者。

- Wikipedia 條目：Bernstein Polynomial
Bernstein Polynomial - Wikipedia
這是一個簡潔的入門資源，涵蓋了 Bernstein 多項式的定義、性質和應用。

**Intermediate**
- 《數值分析與科學計算》（Numerical Analysis and Scientific Computing）
作者：Gene H. Golub, Charles F. Van Loan
這本書深入討論了多項式逼近和數值方法，其中包含 Bernstein 多項式的應用。

- 《計算幾何：算法與應用》（Computational Geometry: Algorithms and Applications）
作者：Mark de Berg, Otfried Cheong, Marc van Kreveld, Mark Overmars
這本書詳細介紹了計算幾何中的曲線和曲面表示，包括 Bernstein 多項式和 Bézier 曲線。

- 論文：Bernstein Polynomials and Convexity
作者：George G. Lorentz
這篇論文探討了 Bernstein 多項式與凸性之間的關係，適合對數學理論感興趣的讀者。

**Advanced**
- 《逼近理論與方法》（Approximation Theory and Methods）
作者：M. J. D. Powell
這本書是高級逼近理論的經典教材，深入討論了 Bernstein 多項式在多項式逼近中的應用。

- 論文：Bernstein Polynomials: A Centennial Retrospective
作者：R. A. DeVore, G. G. Lorentz
這篇論文回顧了 Bernstein 多項式的歷史和發展，並討論了其在現代數學中的應用。

- 《數值逼近》（Numerical Approximation）
作者：Endre Süli, David F. Mayers
這本書深入討論了多項式逼近和數值分析，其中包含 Bernstein 多項式的高級應用。