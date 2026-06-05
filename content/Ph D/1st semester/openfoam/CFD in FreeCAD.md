---
title: CFD in FreeCAD
updated: 2025-08-02 14:00:24Z
created: 2025-01-11 13:54:30Z
latitude: 22.64839560
longitude: 120.32620850
altitude: 0.0000
tags:
  - cfd
---

# CFD in FreeCAD 

## basic 
coordinate 的對應 
```
x -> 紅色
y -> 綠色
z -> 藍色
```


## Cfdof 

- 不同區域切割的mesh 大小不同


## 設定
目前mesh 會失敗, 原因尚未查清

![dbbba8a8ec233b1588f8f64c658300e7.png](../../../../_resources/dbbba8a8ec233b1588f8f64c658300e7.png)

改成gmsh (polyhedral)就可以了

目前的設置
![0ea338eed2c0a9e7e056cdff62d2d1be.png](../../../../_resources/0ea338eed2c0a9e7e056cdff62d2d1be.png)


利用 freecad 跑完後 

開啟 paraview 
選擇檔案 pv.foam 
case type 選擇 decomposed case  


## 問題紀錄

1. Err. Openfoam fatal error: No such file: constant/trisurface/.stl

在執行CFD Solver的時候出現。run meshing 沒有問題。但要執行求解的過程，出現這個錯誤訊息。
解決: 
將前一次的增加的 求解計算砍掉，再執行就可以了


## Ref 
- https://forum.freecad.org/viewtopic.php?t=68499


## Python Script 
[PyCFD](../../../../MyNotes/3D%20printing/Ph%20D%20Research/PyCFD.md)

# 問題
- how to optimization in FreeCAD for CFD simulation ?



# Case study

## Nozzle simulation 

![a0d3238b628c04f9b316a4602778f8fc.png](../../../../_resources/a0d3238b628c04f9b316a4602778f8fc.png)

![60e9cd99b13aa137bbcf51f7fa4cc612.png](../../../../_resources/60e9cd99b13aa137bbcf51f7fa4cc612.png)

 ![5de4229dbbc41425c4f6aa6f3eba5481.png](../../../../_resources/5de4229dbbc41425c4f6aa6f3eba5481.png)

目前不知道要設定什麼邊界條件
計算的時間會這麼久嗎？ 
pressure 不太會變化, 為什麼？ 
有沒有benchmark 的example 可以做測試？ 
如何將結果轉到 transfer model 上？ 

07.26 修正
目前把邊界條件改為
U file 
![e0abc690ba5aab6bc39227855853506c.png](../../../../_resources/e0abc690ba5aab6bc39227855853506c.png)
 
P file 
 
![657a97ee468d1ea7a83457fcb0c3ea31.png](../../../../_resources/657a97ee468d1ea7a83457fcb0c3ea31.png)

收斂速度改善


## blade airfoil simulation 



- [x] part alignment 
缺點是只能用點去做對齊, 而且是直接照著點的位置去對齊位置 


## CFD Benchmark
- https://www.cfdsupport.com/case-studies/
 
