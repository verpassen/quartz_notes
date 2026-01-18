# DED - Multi-materials deposition paper survey 


## 高熵合金(High engtropy alloys, HEAs)

通常是由五種或五種以上等量或相對比例金屬形成的新型[合金](https://zh.wikipedia.org/wiki/%E5%90%88%E9%87%91)。名為「高熵合金」是因為當混合物中存在大量元素混合時的熵增加實質上更高，並且比例更接近相等。

國內最為知名的為清華大學 材料系的葉蔚均教授

https://www.dropbox.com/scl/fi/yeliomloi41xjmlv7daqx/Nature.pdf?rlkey=ibmvrkfx7lkovw4sjzrdsbk9l&dl=0



## What is the characteristics of HEAs ? 
- High-entropy effect
- Severe lattice distortion effect 
- Sluggish diffusion effect
- Cocktail effect 


![](https://paper-attachments.dropboxusercontent.com/s_F4AEF7376EB1C333C18B7E5A2BBB8D98A12F814EE2484B0866717F42CF6336E3_1768099829161_image.png)



## Why Nuclear fusion need HEAs ? 

先要了解的一些名詞

- Helium-ion bombardment 
- Neutron-induced transmutation 



1. Radiation-Induced Segregation
    輻射會造成合金中的某些特定元素朝向或是遠離晶界，容易造成材料的**晶間破裂(intergranular cracking)**
2. Helium "Fuzz" & Blistering
    



## DED  HEAs Application literatures

目前市場上利用DED 進行開發的產品為韓國 InssTek 的[Mx Labs](https://www.insstek.com/products/mx-lab/)
過去它們有的[實績](https://www.insstek.com/download/MX-Lab%20Brochure_2023.pdf)



## Current Requirement from Customer 


1. W(75%) Re(25%) 
2. W(86%) V(3%) Ti(11%)
3.  W(70%) Cr(20%) Ti(10%)
> Notes: the ratio based on **atomic weight**


%at ratio 的計算方式
ex. 
atomic weight of Fe is 56 
atomic weight of C is 12 
avogadro’s number 6.022 x $$10^{23}$$

carbon 有 7 g , iron 有 93 g 
計算如下
$$Carbon = 7 \times 6.022 \times 10^{23} / 12 = 3.513 x 10^{23}$$
$$Iron = 93 \times 6.022 \times 10^{23} = 10.00 \times 10^{23}$$
因此
%at of C $$= 3.513 \times 10^{23} / ((3.513+10)\times 10^{23}) = 26\%$$
%at of Fe = $$93 \times 10^{23} / ((3.513 + 10)\times 10^{23}) = 74\%$$
 

    # measure_atomic_ratio.py
    no_of_element = int(input('Please input the number of the elements you want to mix: '))
    
    element_group = {}
    
    # 1. Collect Atomic Weights
    for i in range(no_of_element):
        weight = float(input(f'Please input the atomic weight of element {i}: '))
        element_group[f'elem_{i}_atomic_weight'] = weight
    
    # 2. Collect Ratios
    print('\nPlease input the atomic ratio of each element using commas to separate.')
    print('Example: 75,10,15')
    ratio_input = input('Input here: ')
    ratios = [float(r) for r in ratio_input.split(',')]
    
    # Store ratios in the dictionary
    for i in range(no_of_element):
        element_group[f'elem_{i}_ratio'] = ratios[i]
    
    ## ---- Calculation Logic ---- ##
    
    # Fixed mass for element 0
    m0 = 10.0
    element_group['elem_0_mass'] = m0
    
    # Variables for element 0 to use in the loop
    r0 = element_group['elem_0_ratio']
    a0 = element_group['elem_0_atomic_weight']
    
    print("\n--- Calculation Results ---")
    print(f"{'Element':<12} | {'Ratio':<10} | {'At. Weight':<12} | {'Mass (g)':<10}")
    print("-" * 55)
    
    # Calculate mass for every element (including element 0)
    for i in range(no_of_element):
        ri = element_group[f'elem_{i}_ratio']
        ai = element_group[f'elem_{i}_atomic_weight']
        
        # Formula: m_i = m0 * (ri / r0) * (ai / a0)
        mi = m0 * (ri / r0) * (ai / a0)
        
        element_group[f'elem_{i}_mass'] = mi
        
        # Display formatted results
        print(f"Element {i:<4} | {ri:<10.2f} | {ai:<12.3f} | {mi:<10.4f}")
    
    ## ---- Optional: Full dictionary export ---- ##
    # print("\nRaw Data:", element_group)
----------

目前問題在於

- 廠內粉桶僅兩組
- 如何確保與控制粉末混和比例
    - 目前供粉機屬於預混還是在雷射頭上方才混和?
        即使是雷射頭上方才混和，也不能確保隨著時間變化的混和穩定性
- 取得粉末材料 (詢問中佑)

what are the challenges of mixing and solidification with these materials? 


1. W-Re alloy 鎢錸合金(Tungsten-rhenium alloys)

Tungsten , atomic number 74 ,  atomic weight 183.84
Rhenium , atomic number 75 , atomic weight 186.207

> 依據 %at 推算，若 Tungsten 10g ，則 Rhenium 需 3.3763 g ，達 (75 - 25 at%)

固溶強化型合金，錸的比例可以分成 3、5、10、25、26以上
這次的需求屬於高錸比例的合金
Re 的添加比例，會改變材料的韌脆性轉換溫度( ductile-brittle transition temperature)，如下圖。
在添加2 - 7 % 的Re 便可以明顯地觀察到曲線的變化。
 

| Rhenium content at. % | Transition temperature , K |
| --------------------- | -------------------------- |
| 0                     | 530                        |
| 1.0                   | 530                        |
| 2.0                   | 430                        |
| 7.0                   | 450                        |
| 25.0                  | 350                        |

 
 
可能的問題

- cracking 

因為 tungsten 和 rhenium 的熔點都很高， 而DED 製程的 cooling rate 極高 (10^4 ~ 10^6) ，很容易造成熱裂。 會需要預熱。(ai : 600 - 1000°C) → hard to achieve

![](https://paper-attachments.dropboxusercontent.com/s_F4AEF7376EB1C333C18B7E5A2BBB8D98A12F814EE2484B0866717F42CF6336E3_1768523611360_image.png)




2. W(86%) V(3%) Ti(11%) (Tungsten - Vanadium - Titanium)

Vanadium，atomic number 23, atomic weight 50.9415
Titanium，atomic number 22, atomic weight 47.867 
可能的問題

- element  volatilization  

因為tungsten 和 Cr 的熔點差異很大，因此可能造成在沉積tungsten 造成其他元素的揮發，改變了最終成品的元素比例。



3. W(70%) Cr(20%) Ti(10%) ( Tungsten - Chromium - Titanium )

Chromium , atomic number 24 , atomic weight 51.996 


**Ref** 
[1] Xiao, S., Ma, Y., Tian, L., Li, M., Qi, C., & Wang, B. (2020). Decrease of blistering on Helium irradiated tungsten surface via transversal release of helium from the grooved surfaces. *Nuclear Materials and Energy*, *23*, 100746. [https://doi.org/10.1016/j.nme.2020.100746](https://doi.org/10.1016/j.nme.2020.100746)
[2] [高熵合金 - 維基百科，自由的百科全書](https://zh.wikipedia.org/zh-tw/%E9%AB%98%E7%86%B5%E5%90%88%E9%87%91)
[3] *Compositional Effects of Additively Manufactured Refractory High-Entropy Alloys under High-Energy Helium Irradiation—PMC*. (n.d.). Retrieved 10 January 2026, from [https://pmc.ncbi.nlm.nih.gov/articles/PMC9228246/](https://pmc.ncbi.nlm.nih.gov/articles/PMC9228246/)
[4] V, B., & M, A. X. (2024). Development of high entropy alloys (HEAs): Current trends. *Heliyon*, *10*(7). [https://doi.org/10.1016/j.heliyon.2024.e26464](https://doi.org/10.1016/j.heliyon.2024.e26464)
[5] Kumar, A., Singh, A., & Suhane, A. (2022). Mechanically alloyed high entropy alloys: Existing challenges and opportunities. *Journal of Materials Research and Technology*, *17*, 2431–2456. [https://doi.org/10.1016/j.jmrt.2022.01.141](https://doi.org/10.1016/j.jmrt.2022.01.141)
[6] Que, Z., Li, X., Zhang, L., Mei, E., Guo, C., Sun, H., Liu, J., Qin, M., Chen, G., & Qu, X. (2025). Preparation and properties of tungsten-rhenium alloys resistant to ultra-high temperatures. *International Journal of Refractory Metals and Hard Materials*, *127*, 106975. [https://doi.org/10.1016/j.ijrmhm.2024.106975](https://doi.org/10.1016/j.ijrmhm.2024.106975)
[7] Gilbert, M., & Sublet, J.-C. (2011). Neutron-induced transmutation effects in W and W-alloys in a fusion environment. *Nuclear Fusion*, *51*, 043005. [https://doi.org/10.1088/0029-5515/51/4/043005](https://doi.org/10.1088/0029-5515/51/4/043005)
[8] Gilbert, M. (2010). *Transmutation and He Production in W and W-alloys*. [https://www.semanticscholar.org/paper/Transmutation-and-He-Production-in-W-and-W-alloys-Gilbert/966b8ab53c92a5a521e25474c1df7da3139e8823](https://www.semanticscholar.org/paper/Transmutation-and-He-Production-in-W-and-W-alloys-Gilbert/966b8ab53c92a5a521e25474c1df7da3139e8823)
[9] [Glossary - at% and wt%](https://www.southampton.ac.uk/~pasr1/g7.htm)








