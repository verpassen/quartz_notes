---
title: Research ideas
updated: 2025-10-17 03:14:03Z
created: 2025-07-11 14:12:28Z
latitude: 22.64839560
longitude: 120.32620850
altitude: 0.0000
---

# Research ideas 

1. 利用 CFD 模擬去蒐集資料, 且是符合已知物理特性的資料

註: 
CFD 其實是很多種不同架構的統稱，常見的包含
- finite difference
- fiinite volume
- finite element
- spectral methods

---

目前採用 
1. moving heat source
2. powder flux
3. direct energy deposition

seperate into 3 phase to verify the idea

所以模擬的部份分成 

- heat source conduction

目前最好取得的資料應該是ccd 的影像, 不論是一般的ccd 或是 pyrometer 

---

2. 模擬的部分，如何利用 physics-informed transfer model 去學習 CFD 的結果 

- Physics-informed transfer learning strategy to accelerate unsteady fluid flow simulations

如果利用surrogate model 去取代 原有的CFD Simulation，要說明相關的優點。比如說，原有CFD 在解決___問題的時候，花了多少的CPU Time ，但利用surrogate model 只花了多少時間等等
> ref : https://www.sciencedirect.com/science/article/abs/pii/S0950423017302711


3. scaling laws for DED
[@tsengScalingLawsNumerical2023](http://dx.doi.org/10.1016%2Fj.ijheatmasstransfer.2023.124717)

文中有談到利用無因次參數來說明整個現象，那是不是可以利用ML method 來找到相關性
 
## todo 
- [Moving heat source conduction](../../../../MyNotes/3D%20printing/Ph%20D%20Research/研究筆記/Moving%20heat%20source%20conduction%20in%20Openfoam.md)


---

## 待解決

- surrogate model 的部份 還不知道要怎麼處理
- 整個系統的架構還不清楚

-----

# 閉迴路控制

如果雷射可以用pwm 控制, 可以看成是一條隨著時間變動的曲線
然後粉末是一條, 速度也是一條
最終的目的讓輸出的溫度/ 熔池大小維持在同樣水準
其實概念是相同的
跟pwm 好像無關





