---
title: principle-of-isfet
comments: false
date: 2020-07-11 12:43:14
tags:device
categories:
---


# MOSFET 基本原理

- 空乏型MOSFET
1. P型基底鑲入兩塊N型區，分別為Source以及Drain以及Drain
2. 在這兩極之間以參雜成N型的通道區相連接
3. N型通道區的上層覆蓋了一層氧化層(二氧化矽(SiO2))
4. 閘極(Gate)是用金屬極片蓋在氧化層上面做成

# ISFET基本原理

- 最早由Bergveld Piet於1970年提出

    他發現將一般MOSFET 的金屬閘極去除後，再將其浸入溶液時，元件之通道電流會隨H+濃度不同而變化，稱其為離子場效電晶體(ISFET)。

- 優勢
    - 輸入阻抗高
    - 輸出阻抗低
    - 響應時間快
    - 低價位
    - 適合用於Biosensor

### 工作原理

由於pH-ISFET工作時感測膜區域直接浸泡於溶液中。與待測溶液相接觸的感測膜是離子感測元件將化學量轉換成電學量的關鍵。對溶液中離子活度的響應機制是根據吸附鍵結模型(Site-binding model)，電解質與感測膜之介面處
會會形成界面勢(Surface potential)，該界面勢隨電解質溶液的離子活度而改變，並對ISFET的通道電流起調制作用，進而引起汲源電流的變化，此即為
氫離子感測場效應電晶體的基本工作原理。

- pH-ISFET基本公式

    ![TSMC%20ISFET%20characteristics%2000b0b66a7a824eae9578a660c318437e/Untitled.png](TSMC%20ISFET%20characteristics%2000b0b66a7a824eae9578a660c318437e/Untitled.png)

- 吸附鍵結模型(Site-binding model)
    - Yates提出用於解釋pH-ISFET響應原理
    - 在感測膜表面存在著羥基(Si-OH, Al-OH, Ta-OH)
        - ISFET感測膜的種類
            - Ta2O5
            - Al3N4
            - Si3N4
    - 在感測膜浸在電解質溶液時，界面處會發生以下化學反應

    ![TSMC%20ISFET%20characteristics%2000b0b66a7a824eae9578a660c318437e/Untitled%201.png](TSMC%20ISFET%20characteristics%2000b0b66a7a824eae9578a660c318437e/Untitled%201.png)

- 總體來說就是藉由感測膜感應出一個表面電位，並藉由導線將表面電位傳至後方MOSFET的閘極端，改變起始電壓(Threshold Voltage)
- pH值愈高，VT愈大，I-V曲線將往右移動

$$Sensitivity=\frac{|△ψ0|}{|△pH|}=\frac{|△Vthreshold|}{|△pH|}=\frac{|△Vgs|}{|△pH|}$$

由上述式子可以得知，感測器的表面電位、元件起始電壓、閘極源極之間的電壓(Vgs)皆會酸鹼度改變。

如下圖所示，很多論文提到的感測度(Sensitivity)指的是Vth隨著pH的變化量

![TSMC%20ISFET%20characteristics%2000b0b66a7a824eae9578a660c318437e/Untitled%202.png](TSMC%20ISFET%20characteristics%2000b0b66a7a824eae9578a660c318437e/Untitled%202.png)

### 響應時間

如下圖所示，ISFET得感測度會隨時間變化

![TSMC%20ISFET%20characteristics%2000b0b66a7a824eae9578a660c318437e/Untitled%203.png](TSMC%20ISFET%20characteristics%2000b0b66a7a824eae9578a660c318437e/Untitled%203.png)

### 量測系統

- C-V

    目前先不討論C-V量測系統，先著重於I-V量測系統

- I-V
    - IDS-VGS

    ![TSMC%20ISFET%20characteristics%2000b0b66a7a824eae9578a660c318437e/Untitled%204.png](TSMC%20ISFET%20characteristics%2000b0b66a7a824eae9578a660c318437e/Untitled%204.png)

    下面曲線與X軸交點為Vth由圖可以得知當pH質越大，元件所需的Threshold Voltage就越大，因此VGS也更高

- IDS-VDS

    ![TSMC%20ISFET%20characteristics%2000b0b66a7a824eae9578a660c318437e/Untitled%205.png](TSMC%20ISFET%20characteristics%2000b0b66a7a824eae9578a660c318437e/Untitled%205.png)

### ISFET的缺點

- 時漂與遲滯量測系統
    - 遲滯現象

    > 所謂遲滯，指當溶液之pH 值突然改變後，又再次回至原來的pH值
    時，元件之輸出電壓會與原先pH值未改變前之輸出電壓有所不同，即量測順序為pHx→pHy→pHx→pHz→pHx的情況下，其前後兩次pHx所測量的輸出值不相同，此電壓輸出之差值即為遲滯。

    > H+和OH-離子的大小不同，H+離子擴散的速率高於OH-離子，故於酸性溶液中遲滯量較小，而鹼性溶液中遲滯量較大，造成遲滯曲線的不對稱。

    - 溫度效應

        可以分為下列幾種:

        - 參考電極之溫度效
        應

        ![TSMC%20ISFET%20characteristics%2000b0b66a7a824eae9578a660c318437e/Untitled%206.png](TSMC%20ISFET%20characteristics%2000b0b66a7a824eae9578a660c318437e/Untitled%206.png)

        - 待測液之溫度效應
        - 臨界電壓之溫度效應
        - 表面電位之溫度效應
    - 照光響應
        - 
- 酸鹼讀出電路與量測系統

### 如何判定感測器的優劣?

- 穩定性與重現性

    ![TSMC%20ISFET%20characteristics%2000b0b66a7a824eae9578a660c318437e/Untitled%207.png](TSMC%20ISFET%20characteristics%2000b0b66a7a824eae9578a660c318437e/Untitled%207.png)

- 響應時間 (R)

    ![TSMC%20ISFET%20characteristics%2000b0b66a7a824eae9578a660c318437e/Untitled%208.png](TSMC%20ISFET%20characteristics%2000b0b66a7a824eae9578a660c318437e/Untitled%208.png)

- 時漂效應

    ![TSMC%20ISFET%20characteristics%2000b0b66a7a824eae9578a660c318437e/Untitled%209.png](TSMC%20ISFET%20characteristics%2000b0b66a7a824eae9578a660c318437e/Untitled%209.png)
<!-- more -->