---
title: Openfoam 問題
updated: 2025-08-11 11:46:47Z
created: 2025-06-04 14:00:55Z
latitude: 25.03296940
longitude: 121.56541770
altitude: 0.0000
---

# Openfoam 問題

 - How to combine Openfoam with PyTorch?

- what is cfd-dem ?
	- why we need it
- what is vod-dem ?
	- why we need them.
 
- 全解析cfd-dem
一般要求網格達到顆粒大小的1/10才有辦法準確與收斂
但因為計算量大,適合用於研究

- 半解析cfd-dem
拖曳力模型 , 熱傳導模型
精度尚可, 但效率高, 用於工業模擬
網格大小約為顆粒大小的3倍

## concepts 
openfoam 模擬case 0 資料夾中的 p 指的都是 ${p}/{\rho}$
並不是指 壓力 p 

---

## Software 

- $FOAM_RUN  reset directory
修改 ~/.bashrc
在文件末端增加
```bash
FOAM_RUN=[PATH YOU WANT TO ASSIGN]
```
修改後再執行 
```bash
$ source ~/.bashrc 
```


看完影片後忘記自己是怎麼安裝在linux pc 上
youtube 影片提到 
openfoam 是一組工具,不要看成是單一有使用者介面的軟體

src : 包含了 library 
utility : 包含了 很多應用的小工具 
solvers : 可以用到的求解器
 



