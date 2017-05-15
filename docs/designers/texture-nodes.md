---
title: "紋理節點 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b7df5ef3-dd4f-4964-9d96-34e0e180515e
caps.latest.revision: 12
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 12
---
# 紋理節點
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在著色器設計工具中，材質節點會取樣各種材質類型和幾何，並產生或轉換材質座標。  紋理提供物件的色彩和光源詳細資料。  
  
## 紋理參考節點。  
  
|節點|詳細資料|屬性|  
|--------|----------|--------|  
|**立方體地圖範例**|從指定座標的一個立方體地圖中選取一個色彩範例。<br /><br /> 您可以使用立方體地圖，為反射效果提供色彩詳細資料，或是將材質套用至與 2D 材質相比較不失真的球面物件。<br /><br /> **輸入：**<br /><br /> `UVW`: `float3`<br /> 在當做範例之材質立方體上指定位置的向量。  範例取自此向量與個向量與立方體交界處。<br /><br /> **輸出：**<br /><br /> `Output`: `float4`<br /> 色彩範例|**紋理**<br /> 與取樣器產生關聯的材質暫存器。|  
|**法線地圖範例**|從指定座標的一個 2D 一般地圖中選取一個一般範例。<br /><br /> 您可以使用標準地圖在物件的表面上模擬其他幾何詳細資料的外觀。  標準地圖包含表示單位向量而非色彩資料的封裝資料。<br /><br /> **輸入：**<br /><br /> `UV`: `float2`<br /> 這個範例中所使用的座標。<br /><br /> **輸出：**<br /><br /> `Output`: `float3`<br /> 一般範例。|**座標軸調整**<br /> 用來調整標準地圖範例之慣用手的因數。<br /><br /> **紋理**<br /> 與取樣器產生關聯的材質暫存器。|  
|**移動瀏覽 UV**|做為時間的函數，平移指定的材質座標。<br /><br /> 您可以使用這個來移動物件表面間的材質或標準地圖。<br /><br /> **輸入：**<br /><br /> `UV`: `float2`<br /> 移動的座標。<br /><br /> `Time`: `float`<br /> 時間長度以秒移動瀏覽。<br /><br /> **輸出：**<br /><br /> `Output`: `float2`<br /> 移動的座標。|\[**速度 X**\]<br /> 每秒在 x 軸間移動瀏覽的材質數目。<br /><br /> \[**速度 Y**\]<br /> 每秒在 y 軸間移動瀏覽的材質數目。|  
|**視差 UV**|將材質座標取代為高度和檢視角度的函式，即可修改材質座標。<br /><br /> 這種效果也稱為 *視差對應*，或是虛擬位移對應。  您可以用來在平面上建立深度錯覺。<br /><br /> **輸入：**<br /><br /> `UV`: `float2`<br /> 替換的座標。<br /><br /> `Height`: `float`<br /> 與 `UV` 座標相關聯的 heightmap 值。<br /><br /> **輸出：**<br /><br /> `Output`: `float2`<br /> 放錯的座標。|**深度平面**<br /> 視差效果的參考深度。  預設值為 0.5。  較小的值會提高材質，較大值則會使材質沈入表面。<br /><br /> **深度比例**<br /> 視差效果的小數位數。  這樣可以增加或減少明顯的深度。  一般值範圍從 0.02 到 0.1。|  
|**旋轉 UV**|做為時間的函數，繞著中心點旋轉指定的材質座標。<br /><br /> 您可以使用這個在物件的表面微調材質或標準地圖。<br /><br /> **輸入：**<br /><br /> `UV`: `float2`<br /> 旋轉的座標。<br /><br /> `Time`: `float`<br /> 時間長度以秒移動瀏覽。<br /><br /> **輸出：**<br /><br /> `Output`: `float2`<br /> 旋轉的座標。|**中心 X**<br /> 定義旋轉中心的 x 座標。<br /><br /> **中心 Y**<br /> 定義旋轉中心的 y 座標。<br /><br /> **速度**<br /> 材質每秒旋轉的角度 \(以弧度為單位\)。|  
|**紋理座標**|目前像素的材質座標。<br /><br /> 材質座標依是否在附近端點的材質座標之間插入而定。  您可以將這個當做材質空間中目前像素的位置。<br /><br /> **輸出：**<br /><br /> `Output`: `float2`<br /> 材質座標。|無|  
|**材質維度**|輸出第 2 材質地圖的寬度和高度。<br /><br /> 您可以使用材質會考慮紋理的寬度和高度在著色器中。<br /><br /> **輸出：**<br /><br /> `Output`: `float2`<br /> 以向量表示紋理的寬度和高度。  這個寬度 Vector 中的第一個項目中。  儲存在第二個項目中的高度。|**紋理**<br /> 與材質面向產生關聯的材質暫存器。|  
|**材質差異**|輸出差異 \(距離\) 在第 2 材質地圖的 Texel 之間。<br /><br /> 您可以使用材質差異取樣在著色器的鄰近材質值。<br /><br /> **輸出：**<br /><br /> `Output`: `float2`<br /> 差異 \(距離\) 從一個材質到下 texel \(動作對角朝正向\)，以用向量標準化材質空間。  您可以選擇忽略或負差異的 U 或 V 座標取得所有鄰居 Texel 的位置。|**紋理**<br /> 與材質差異產生關聯的材質暫存器。|  
|**材質範例**|從指定座標的一個 2D 材質地圖中選取一個色彩範例。<br /><br /> 您可以使用材質地圖，在物件的表面提供色彩詳細資料。<br /><br /> **輸入：**<br /><br /> `UV`: `float2`<br /> 這個範例中所使用的座標。<br /><br /> **輸出：**<br /><br /> `Output`: `float4`<br /> 色彩範例|**紋理**<br /> 與取樣器產生關聯的材質暫存器。|