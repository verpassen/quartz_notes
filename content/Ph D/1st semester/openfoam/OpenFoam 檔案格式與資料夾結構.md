---
title: OpenFoam 檔案格式與資料夾結構
updated: 2025-08-24 21:34:32Z
created: 2025-06-07 23:20:55Z
latitude: 25.03577500
longitude: 121.56345030
altitude: 0.0000
---

# OpenFoam 檔案格式與資料夾結構


## Folder 資料結構
\$HOME/Openfoam 下會有兩個資料夾

安裝的原始檔稱作
**\$WM_PROJECT_DIR**
使用者使用的資料夾變數則是
**\$WM_PROJECT_USER_DIR**

常會用到的捷徑名
$FOAM_RUN : 執行 openfoam 的工作資料夾
$FOAM_TUTORIALS : 放置 openfoam 教學文件的資料夾位置

alias 設定在 ~/.bashrc 中 
eg. 
>FOAM_RUN = /home/chang/OpenFOAM/chang-v2312/run

一般建議將要練習的資料夾整個複製到使用者資料夾下
這樣可以避免污染原本的檔案資料設定


### 資料結構

打開範例
![94f1646b3d683befc3ba2ccff4a448c3.png](../../../../_resources/94f1646b3d683befc3ba2ccff4a448c3.png)

0 資料夾： 存放初始條件和邊界條件

下圖p 為壓力, u為速度
![dc94d5d20640deb16b4138d9bc757327.png](../../../../_resources/dc94d5d20640deb16b4138d9bc757327.png)

constant 資料夾 : 存放生成的網格和物性特徵
polyMesh : 執行 blockMesh 後所生成的網格資料,存放在這
![862b3a263c82d29cad04abdcadce029d.png](../../../../_resources/862b3a263c82d29cad04abdcadce029d.png)

system 資料夾:  控制網格生成, 運行時間, 離散格式, 求解方式
![c679b5c29ce8e73c47bc78898c3ebe11.png](../../../../_resources/c679b5c29ce8e73c47bc78898c3ebe11.png)

blockMeshDict : 控制網格生成
controlDict  :  控制運行步長 和運行時間
decomposeParDict : 
fvSchemes : 離散格式設定
fvSolution : 求解器設定
PDRblockMeshDict : 

---

## Openfoam 檔案的格式

遵守c++ 的格式

> 單行comment  // 
多行 comment /*   */

### 檔頭 header 
說明目前使用的OpenFoam版本，檔案格式，以及你此時開啟的檔案是什麼(下面的例子就是 p 壓力的檔頭)
```txt
/*--------------------------------*- C++ -*----------------------------------*\
| =========                 |                                                 |
| \\      /  F ield         | OpenFOAM: The Open Source CFD Toolbox           |
|  \\    /   O peration     | Version:  v2206                                 |
|   \\  /    A nd           | Website:  www.openfoam.com                      |
|    \\/     M anipulation  |                                                 |
\*---------------------------------------------------------------------------*/
FoamFile
{
    version     2.0;
    format      ascii;
    class       volScalarField;
    object      p;
}
// * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * //
```

### 字典 dictionaries

>  < dictionary name > {
> keyword entities	
> }


### 單位  dimensional units 
在OpenFoam 檔案中會顯示像這樣
[ 0 2 -1 0 0 0 0 ]

代表的意義

|順序|性質|SI 單位|ucs 單位|
|-|-|-|-|
|1|mass|kilogram(kg)|pound-mass(lbm)|
|2|length|metre(m)|foot(ft)|
|3|time|second(s)|second(s)|
|4|temperature|Kelvin(K)|degree rankine()|
|5|quantity|kilogram-mole (kgmol)	|pound-mole (lbmol)	|
|6|current|ampera(A)|ampera(A)|
|7|luminous intensity|candela(cd)|candela(cd)|

舉幾個常見的單位


## Mesh 

mesh 也有分成不同的格式，目前還不清楚差異
說明文檔中有提到不同mesh 格式之間的轉換指令(mesh conversion)

https://www.openfoam.com/documentation/user-guide/4-mesh-generation-and-conversion/4.5-mesh-conversion

**問題:** 
- 如果用文字檔案看，分得出這個mesh是什麼格式的mesh 嗎?
怎麼分

- Mesh 會有分公英制? 或是今天單位使用的是 m , cm 的時候
  兩者會有差異嗎?
