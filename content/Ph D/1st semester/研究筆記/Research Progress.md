---
title: Research Progress
updated: 2026-01-12 21:24:55Z
created: 2025-08-12 21:49:44Z
latitude: 22.64839560
longitude: 120.32620850
altitude: 0.0000
---

# Research Progress 

- Openfoam Environment buildup
Install Openfoam , paraview and learning 


- PINN run a script
目標是可以針對某個著名的 CFD 的問題去處理和驗證
- [Using PINN to solve navier stoke equation](../../../../MyNotes/3D%20printing/Ph%20D%20Research/研究筆記/Using%20PINN%20to%20solve%20navier%20stoke%20equation.md)


## Workflow 
## Current progress 
1. ode fitting by pytorch 
```bash
pip install torch
pip install matplotlib
```
!!!
目前照抄範例的狀態, 後續找一個二維的微分方程做一次試試看

2. 找到別人用PINN 做 n-s equation 解析模擬的程式

目前下一步先重製他的結果

Q1. 如何把 colab 上去變成一個編輯的平台
可以呼叫檔案, 輸出檔案
跟本機相同的方式去做資料的交換和儲存
09.03 測試
可以讀取sample data 的檔案(csv) 
上傳 mat 檔案(for CFD simulation result) 
可以讀取並且輸出key，表示後續可以上傳mat file for model training 

1-1. colab 是否可以讀取雲端空間的檔案? 
可以


Q2. 看懂對方的程式
為什麼這樣寫？ 有什麼

10.19 
目前進行moving heat source 的pinn 模擬
遇到的問題是 計算出來的收斂性差
不確定是不是設定上有問題 或是 程式的架構有問題

>
> 建議:
>1. alpha 從 2調整到 10-20 這個範圍以增加 物理的 compliance
>2. 增加撒的點數以及epoch 數
>3. 增加NN的層數
>4. 


另外，目前的程式，大部分是由ai 撰寫
需要搞懂這些架構還有函數之間的關係
比較好後面做修改




## resources
 - [pytorch's tutorial](https://www.kaggle.com/discussions/getting-started/123904)
