---
title: Polymer processing
updated: 2026-01-11 21:43:31Z
created: 2025-12-27 02:54:21Z
---
# Polymer processing 

## 歷程
- [[Homework_1 for Introduction to Polymer Processing | Homework1]]
- [[hw_2 momentum equation derivation in x direction f | Homwork2]]



## Polymer Final project 

### Timeline
- 期末考 : 12/26
- 期末報告 : 1/2 , 1/9
    - 報告時間5-7分鐘
	
### Tasks
- [ ] 圖面標示
- [ ] 設置模擬環境
- [ ] 調查可用的材質
- [ ] 需要比較的項目
    - [ ] 製程條件
    - [ ] 材質
    - [ ] 澆口、流道設計、水冷設計
- [ ] 結果後處理
- [ ] 報告

### 紀錄 
好用功能

1. Mesh quality
mesh tab > structure mesh > 跳轉出新的頁籤 > show solidmesh quality
點選需要計算的物件
就可以針對這個物件的網格進行分析

目前的問題: 翹曲
可能原因: 
- 壓力梯度
- 厚度差異

>零件上不同厚度區域的壓力傳遞與冷卻凝固的速率不同，造成收縮差異，常見的位置為肋板或凸台，容易產生縮痕(Sink marks)

建議改善策略
- 檢查的流程工具
Thickness -> L/t Ratio -> Gate location advisor -> Quick flow -> Standard flow
- 模具溫度(Mold temperature)
提高模具溫度
- 改善冷卻水路
不均勻的冷卻收縮可能是造成翹曲的原因，因此為避免不均勻收縮的狀況
- 保壓壓力與時間調整 (packing pressure and time)

2. 比較不同參數的方式:
對主要的資料夾按右鍵， create run wizard > number of run : 4

> 對不同run 設定不同的參數，以及參數的參數設定值
> auto generate the new run 
> computation > summit batch runs > select compared batch run > 
> move the left hand side data to right side 
> setup the task number

建議比較的模擬結果
1. 總收縮率( total shrinkage)
2. 差動收縮(differential shrinkage)
    沿著流動方向(flow)與垂直方向(traverse)的收縮差異
3. 差動冷卻(differential cooling)

使用問題
- 一次射出多個如何設定? 

---

### Takeouts
- 厚件的射出(指厚度超過5mm以上) ，常見的問題為前端的料已經冷卻，靠近進料口的部分沒辦法補料，造成明顯的sinking mark 。
並且厚度較厚的地方，容易累積熱，內部收縮後，可能造成外部的塌陷凹凸不均等現象

- 大部分的人比的如材料、進料口方向或位置
- multi stage optimization 算是不一樣的。
- 因為選擇的工件特性不同，所以卡住的問題或是影響的因子會不同。 因此，如果沒有找到正確的因子去比較，很容易比了個空虛

- 概略數字: 射出成型的零件，一平方吋約4噸的壓力
可以依據這個數字來選擇設備大小

- 最後冷卻的位置，為收縮量最大的位置
收縮量大的材質： POM , PP


## 參考閱讀
- [射出相關的部落格網站](https://kenddg.tw/)
