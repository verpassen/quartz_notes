---
title: OpenFoam 安裝
updated: 2025-08-11 21:37:53Z
created: 2025-06-07 23:40:43Z
latitude: 25.03577500
longitude: 121.56345030
altitude: 0.0000
---

# OpenFoam 安裝

以下依據使用的作業系統分類
## 1. Linux

目前常在使用的是tutorial 的資料夾,類似工作區,但不是安裝軟體的位置(要分清楚)




## 2. Windows 

- https://develop.openfoam.com/Development/openfoam/-/wikis/precompiled/windows

第一次安裝還先去搞定windows的wsl，但不得不說，安裝與使用OpenFoam在windows比Linux 麻煩多了，容易產生奇怪的問題
但目前的安裝已經比從前一開始好很多了，直接執行安裝執行檔就可以完成。

---

##  Install Openfoam Docker

- 下載 dockerfile of openfoam 

- 建立資料夾

- build the image
$ docker image build --no-cache -t 

### 安裝設定步驟(未完成)
- Add the repository
``` {bash}
$curl https://dl.openfoam.com/add-debian-repo.sh | sudo bash
```

- Install preferred package. 
Eg.
```{bash}
$sudo apt-get install openfoam2212-default

# Use the openfoam shell session. Eg,
```{bash}
$openfoam2212
```


### 教學
- https://develop.openfoam.com/Development/openfoam/-/wikis/precompiled


### 學習資源
- [ ] [how to install](https://www.youtube.com/watch?v=CeEJS1eT9NE)
- [ ] htts://www.youtube.com/watch?v=3iZfVmFkvB8&list=PLqxhJj6bcnY9RoIgzeF6xDh5L9bbeK3BL&index=1


### 參考
- https://www.cfdsupport.com/OpenFOAM-Training-by-CFD-Support/node1.html
- https://hydro-informatics.com/get-started/install-openfoam.html
