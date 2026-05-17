---
title: 'Pooling rule '
updated: 2026-04-03 00:07:36Z
created: 2025-01-31 08:36:20Z
latitude: 22.64839560
longitude: 120.32620850
altitude: 0.0000
---

# Pooling rule 


### 用途 
>減少實驗規劃中的變數數量


### 原則1. 
去除掉$F_{stat} \le 1$ 的變數
由於$F_{stat}=\Large{}\frac{MS_{factor}}{MS_{error}}$
而當$F_{stat} \le 1$，代表 $MS_{factor}$ < $MS_{error}$

=> 沒辦法解釋的影響大於由因子帶來的影響。

註: MS : Mean square 均方值

### 原則2. 
去除掉 Sum of square 數值最小的一半因子(對於表現比較不顯著的因子)
如果原本有16個實驗因子，那就去掉前8個較小的因子


接著，重新進行變異數分析
找出表現影響顯著的因子


## 參考資料
- https://www.youtube.com/watch?v=Gk3eFQzXbZ0