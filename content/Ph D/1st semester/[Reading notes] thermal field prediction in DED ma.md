---
title: >-
  [Reading notes] thermal field prediction in DED manufacturing process using
  Arti
updated: 2026-01-13 00:14:50Z
created: 2025-02-21 15:40:01Z
latitude: 23.47544220
longitude: 120.44683420
altitude: 0.0000
---

[Reading notes] thermal field prediction in DED manufacturing process using Artificial Neural network


利用 fem 的結果當作 ANN model 的輸入資料 

模擬過程為了更多的資料, 設定了不同的雷射功率以及不同的類神經層數

所以目前看起來只要設定好一個模擬設定的模型
修改一些參數, 輸出過程中(retrieve from the simulation) 的資料
就可以得到很多資料

然後在讓 類神經網路模型去學習接著預測


## 問題
- 沒有和實際的實驗去比對
- 沒有其他模型的參考
- 預測準確度的標準是什麼？ 都是模擬的資料, 驗證也是模擬的資料 要怎麼不準？ 
