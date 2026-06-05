---
title: Openfoam
updated: 2025-08-11 21:46:26Z
created: 2024-05-13 14:05:09Z
latitude: 25.03296940
longitude: 121.56541770
altitude: 0.0000
tags:
  - cfd
  - simulation
---

Openfoam
---

# 基本介紹
OPENFOAM (OPEN FIELD OPERATION AND MANIPULATION)

通常需要搭配著一起學習的還有後處理的 [Paraview](../../../../undefined)

## Before installation


## [Installation](../../../../MyNotes/3D%20printing/Ph%20D%20Research/openfoam/OpenFoam%20安裝.md)


## 基本設置
- [OpenFoam 檔案格式與資料夾結構](../../../../MyNotes/3D%20printing/Ph%20D%20Research/openfoam/OpenFoam%20檔案格式與資料夾結構.md)

---
## 第一次跑 tutorial 
1. 複製安裝目錄下的教學資料夾內容到，要執行的目錄下
	```bash
	$cp -r $FOAM_TUTORIALS $FOAM_RUN
	```


2. 產生網格
	```bash
	$blockMesh
	```
- 注意大小寫
- 注意有沒有錯誤訊息

3. 新增一個零件檔案，作為儲存結果的檔案
	```bash
	$touch part1.foam
	```

4. 執行計算
	```bash
	$simpleFoam
	```

5. 以paraview 打開檔案，觀察結果，進行後處理

---
2025.Jan.10 

### 跑 cavity 案例 
檔案路徑
$../openfoam/run/tutorials/incompressible/icoFoam/cavity/cavity/
1. 複製這個案例的資料夾到 run 下面

	**過程**
	 > 切網格 --> 求解 --> 後處理

2. 切網格
	blockMesh 的M 要是大寫
	```bash
	$blockMesh
	```

3. 執行求解
	```bash
	$icoFoam
	```

4. 後處理
會跳出paraview 並打開結果檔案
	```bash
	$paraFoam
	```

---

### 設定paraFoam 問題

如果paraFoam 指令打進去，出現錯誤
```bash
/OpenFOAM/OpenFOAM-v2206/bin/paraFoam: line 420: paraview: command not found
```

新增類似 paraFoam 的自定義指令

```alias paraviewWindows="touch simulation.foam && /mnt/c/Program\ Files/ParaView\ 5.9.0-Windows-Python3.8-msvc2017-64bit/bin/paraview.exe simulation.foam"
```


目前windows 的電腦
openfoam 的安裝路徑
```bash
C:\Program Files\ESI-OpenCFD\OpenFOAM\v2206\msys64\home\ofuser
```

paraview 的安裝路徑
```bash
D:\software\ParaView-5.11.0-RC1-Windows-Python3.9-msvc2017-AMD64\bin
```

只要把paraview 的路徑新增到系統環境變數中，之後在 WSL中，Terminal 輸入 paraview 就可正常開啟 paraview 軟體



---
# 參考資料
- [官網 install ](https://develop.openfoam.com/Development/openfoam/-/wikis/precompiled/debian)

- [CFD 中文網 - Openfoam 無法調用paraview](https://www.cfd-china.com/topic/1445/openfoam%E6%97%A0%E6%B3%95%E8%B0%83%E7%94%A8paraview%E7%9A%84%E8%A7%A3%E5%86%B3%E5%8A%9E%E6%B3%95)


## Learning resource 
- [OpenFOAM Wiki](https://wiki.openfoam.com/Main_Page)
- [wolfdynamics](https://www.wolfdynamics.com/index.php)
  義大利 University of Genoa 大學的教學網頁
  有分享投影片和程式的教學
  跑過一次就有一點基礎了
  但是目前看都是要錢的 ，可以看Wolf 的yt 頻道
  	- [YT- Wolfdynamics](https://www.youtube.com/@wolfdynamicsCFD)
- [CFD Forum](https://www.cfd-online.com/Forums/openfoam/)
- [CFD Direct](https://cfd.direct/)
- [CFD 中文網](https://www.cfd-china.com/topic/1445/openfoam%E6%97%A0%E6%B3%95%E8%B0%83%E7%94%A8paraview%E7%9A%84%E8%A7%A3%E5%86%B3%E5%8A%9E%E6%B3%95)

- [Holzmann CFD](https://holzmann-cfd.com/community/training-cases)


### tutorial on YT
- [Cyprien Rusu channel](https://www.youtube.com/playlist?list=PLvkU6i2iQ2fobFabvgRFeCGsHOqJ8iB5W)
- [Caesar Wiratama](https://www.youtube.com/@caesarwiratama3303/videos)
- [József Nagy](https://www.youtube.com/watch?v=mGSUIXye9j4&list=PLcOe4WUSsMkH6DLHpsYyveaqjKxnEnQqB)
- [Openfoam + FreeCAD Tutorial](https://www.youtube.com/watch?v=HrVAWJqodAM&list=PLkKD7eCr9mpxhNAJFAU9NjKrECmcVsD3D)
- [CFD Learning blog](https://jahid-hasan.com/writings/a-complete-learning-path-for-cfd/)

### 閱讀
- Computational Fluid Dynamics simulations of laser metal deposition process exploring open source software
