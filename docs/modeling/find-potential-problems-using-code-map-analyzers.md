---
title: "使用 Code Map 分析器尋找潛在問題 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
f1_keywords: 
  - "vs.progression.codemapanalyzers"
helpviewer_keywords: 
  - "程式碼分析，相依性圖形"
  - "相依性圖形，分析程式碼"
  - "圖形文件，分析"
ms.assetid: 9dd799a7-f7eb-42ff-8612-b19dde7ff4eb
caps.latest.revision: 11
author: "alexhomer1"
ms.author: "ahomer"
manager: "douge"
caps.handback.revision: 11
---
# 使用 Code Map 分析器尋找潛在問題
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 Code Map 上執行分析器，以協助您識別可能過度複雜或需要改進的程式碼。 例如，您可以使用這些分析器：  
  
|**尋找具有下列項目的程式碼：**|**檢查這些區域，以查看是否**|  
|-----------------------|----------------------|  
|迴圈或循環相依性|您可以將其簡化，並考慮是否可以中斷這些循環。|  
|太多相依性|相依性正在執行太多函式，或者將決定變更這些區域的影響。 格式正確的 Code Map 會顯示最少的相依性。 若要讓程式碼更容易維護、變更、測試和重複使用，請考慮是否重構這些區域，以便能更清楚地加以定義，或考慮是否合併執行類似功能的程式碼。|  
|沒有任何相依性|它們是必要的，或者您是否應移除此程式碼。|  
  
## 分析 Code Map  
  
1.  在對應工具列上選擇 \[配置\]、\[分析器\] 以及您想要執行的分析器：  
  
    |**分析器**|**若要識別具有下列項目的節點：**|  
    |-------------|------------------------|  
    |**循環參考分析器**|對彼此具有循環的相依性。 **Note:**  當您展開群組時，\[泛型\] 群組中的循環相依性不會顯示在對應上。|  
    |**尋找中樞分析器**|為前 25% 的高度連接節點<br /><br /> **隱藏對應上的所有其他節點**<br /><br /> -   開啟對應的捷徑功能表，依序選擇 \[進階\]、\[選取\] 和 \[隱藏未選取\]。<br />     對應會隱藏未選取的節點，且分析器將識別作為中樞的新節點。|  
    |**未參考的節點分析器**|不具有來自其他任何節點的參考。 **Caution:**  在假設此程式碼未經使用之前，請驗證每個案例。 在程式碼中，找不到像是 XAML 相依性和執行階段相依性這樣的靜態特定相依性。|  
  
 在您套用之後，Code Map 分析器將繼續執行。 如果您變更對應，所套用的任何分析器將自動重新處理已更新的對應。 若要停止執行分析器，在對應工具列上選擇 \[配置\]，然後選擇\[分析器\]。 關閉所選的分析器。  
  
> [!TIP]
>  如果您的對應非常大，執行分析器可能會造成記憶體不足的例外狀況。 如果發生這種情況，請編輯對應以減少其範圍，或產生較小的對應，然後執行分析器。  
  
## 請參閱  
 [對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)   
 [使用 Code Map 偵錯您的應用程式](../modeling/use-code-maps-to-debug-your-applications.md)   
 [進行偵錯時對應呼叫堆疊上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)