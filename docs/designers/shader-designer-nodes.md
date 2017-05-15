---
title: "著色器設計工具節點 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f5192fbd-c78f-40a8-a4d4-443209610268
caps.latest.revision: 6
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 6
---
# 著色器設計工具節點
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在本文中包含可以使用多個著色器設計工具的節點，來建立個圖形特效等相關資訊。  
  
## 節點和節點類型  
 著色器設計工具以圖形表示視覺效果。  這些圖表示從特別選擇的節點建置的，並以精確的方式相連，以達到所需的效果。  每個節點都代表一項資訊或一個數學函式，其間的連接代表資訊如何流經圖形產生結果。  著色器設計工具提供六個不同的節點類型：篩選器、材質著色器、參數、常數、公用程式節點和數學節點，還有數個分別屬於各類型的個別節點。  本節其他文章說明這些節點和節點型別，請參閱本文件結尾處的連結。  
  
## 節點結構  
 所有的節點都是由通用項目的組合所組成。  每個節點在其右邊至少都有一個輸出終端 \(除了代表著色器輸出的完稿色彩節點以外話。  表示計算或材質範例的節點在其左邊有輸入終端，但表示資訊的節點沒有輸入終端。  輸出終端會連接至輸入終端，將資訊從一個節點移動到另一個節點。  
  
### 輸入提升  
 由於著色器設計工具最後必須產生 HLSL 原始程式碼，使其效果可以用於遊戲或應用程式，因此 \[色器設計工具\] 節點受限於 HLSL 使用的型別提升規則。  由於圖形硬體主要在操作浮點數值，因此不同型別之間的型別提升 \(例如，從 `int` 到 `float`，或是從 `float` 到 `double`\) 並不常見。  相反地，由於圖形硬體會同時對多項資訊使用相同的作業，因此可能發生不同類型的提升，其中會延長數目較短的輸入以符合最長的輸入大小。  如何根據輸入的型別以及作業本身增加長度：  
  
-   **如果較小的型別是純量值，則：**  
  
     純量的值會複製到向量中，此向量的大小與較大的輸入相等。  例如，當運算的最大輸入是三元向量時，無論是何種運算，純量輸入 5.0 會變成向量 \(5.0, 5.0, 5.0\)。  
  
-   **如果較小的型別是向量，而且運算是乘法類運算 \(\*、\/、% 等等\)，則：**  
  
     將向量的值複製到向量開頭的項目中，此向量的大小等於較大的輸入，且結尾項目設為 1.0。  例如，當向量輸入 \(5.0, 5.0\) 乘以四元向量時，會變成向量 \(5.0, 5.0, 1.0, 1.0\)。  這可以使用乘法識別 1.0 保留輸出的第三和第四個項目。  
  
-   **如果較小的型別是向量，而且運算是加法類運算 \(\+、\- 等等\)，則：**  
  
     將向量的值複製到向量開頭的項目中，此向量的大小等於較大的輸入，且結尾項目設為 0.0。  例如，當向量輸入 \(5.0, 5.0\) 加上四元向量時，會變成向量 \(5.0, 5.0, 0.0, 0.0\)。  這可以使用加法識別 0.0 保留輸出的第三和第四個項目。  
  
## 相關主題  
  
|標題|描述|  
|--------|--------|  
|[常數節點](../designers/constant-nodes.md)|描述可在著色器計算中用來表示常值及內插補頂點狀態資訊的節點。  由於頂點狀態是內插補 \(因此不同於每個像素\)，每個像素著色器執行個體都會收到不同版本的常數。|  
|[參數節點](../designers/parameter-nodes.md)|描述可在著色器計算中用來表示相機位置、材質屬性、光源參數、時間及其他應用程式狀態資訊的節點。|  
|[紋理節點](../designers/texture-nodes.md)|描述可用來取樣各種材質類型和幾何以及透過一般方式產生或轉換材質座標的節點。|  
|[數學節點](../designers/math-nodes.md)|描述可以用來執行代數、邏輯、三角及其他直接對應至 HLSL 指令之數學運算的節點。|  
|[公用程式節點](../designers/utility-nodes.md)|描述可以用來執行一般光源計算及其他未直接對應至 HLSL 指令之一般運算的節點。|  
|[篩選節點](../designers/filter-nodes.md)|描述可以用來執行材質篩選及色彩篩選的節點。|