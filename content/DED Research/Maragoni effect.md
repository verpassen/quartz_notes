---
title: Maragoni effect
updated: 2026-01-18 00:46:49Z
created: 2023-11-19 02:15:13Z
latitude: 22.64839560
longitude: 120.32620850
altitude: 0.0000
tags:
  - fluid dynamics
  - surface tension
---

# Maragoni effect 馬倫哥尼效應

# 現象說明
>The Marangoni effect is the mass transfer along an interface between two fluids due to the surface tension gradient (which fluid from areas with low surface tension is transferred to areas with higher surface tension).
> 由於溫度梯度的關係，造成區域表面張力的差異，而形成一個流動傳導的驅力。
> DED 中的溫度梯度，則是由於移動的熱源與冷卻速率造成的。


源自熔池表面極高的溫度梯度，導致熔池的表面張力分布不均勻，驅使熔池內部的液態金屬產生流動，亦稱為馬蘭戈尼對流(Marangoni Convection)。

**表面張力高**  - 限制流體的流動，產生淚滴、水珠狀的特徵
**表面張力低** - 熔池的流動性較佳，改善材料填充孔洞或間隙的能力，較能得到一個均勻分布的涂覆表面


## 說明
表面張力的溫度梯度若為正，表示表面張力隨著溫度越高越大。
表面張力的溫度梯度若為負，表示表面張力隨著溫度越高越小。
<img src='https://amarineblog.files.wordpress.com/2021/06/marangoni-effect-in-welding-gtaw.png' width=80%>

**對於大部分鋼材，表面張力的溫度係數是負的。**

>當材料中添加硫、氧這些表面活性元素，則會讓表面張力隨著溫度上升而增加。

如果硫含量小於30 ppm ，dγ / dT < 0，溶池易向外擴散，形成較低穿透深度的溶池形狀。
如果硫含量大於60 ppm ，dγ / dT > 0，溶池易向內集中，形成較深的穿透深度的溶池。(但也容易使得空氣不易逸散，而形成porosity)

熔池中心的溫度往往是最高的位置，且表面張力隨著溫度而下降，因此中心的表面張力相較於兩旁來的小，形成由熔池中心向外流動的驅力，形成寬而淺的焊道。而添加了表面活性，則形成相反特性的焊道，形成由外相中心流動的熔池，容易形成窄且深的焊道。

$\begin{aligned}
M_a &= \frac{d\gamma}{dT} \frac{dT}{dx} \frac{L^2}{\eta \alpha} \\[5mm]
其中\\ & \gamma 為表面張力 \\[3mm]
& \frac{dT}{dx} 為溫度梯度\\[3mm]
& \alpha 溫度傳導係數 \\[3mm]
& L 為特徵長度 \\[3mm]
& \eta 為溶池的黏滯性
\end{aligned}$


![schematic of Marangoni effect.JPG](../../../../assets/schematic%20of%20Marangoni%20effect.JPG)


### 實際案例 

- 酒杯的眼淚 wine tear


# 參考
- [What is Marangoni effect in GTAW welding](https://amarineblog.com/2021/06/28/what-is-marangoni-effect-in-gtaw-welding/)
- [State of the Art in Directed Energy Deposition: From Additive Manufacturing to Materials Design](10.3390/coatings9070418) 
