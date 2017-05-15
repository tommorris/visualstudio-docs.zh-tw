---
title: "模組檢視 - 程式碼剖析工具：.NET 記憶體取樣資料 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "模組檢視"
ms.assetid: 9c05b51a-8382-44cf-a8f7-3fabdd2e8f1b
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 模組檢視 - 程式碼剖析工具：.NET 記憶體取樣資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用取樣方法收集之 .NET 記憶體配置資料的 \[模組\] 檢視，會透過程式碼剖析期間執行的模組將記憶體資料加以分組。  每個模組都是階層式樹狀結構的根項目。  模組的函式會列在模組節點下面。  
  
 配置記憶體之陳述式的原始程式檔行號會列於函式節點下方，而執行配置的指令位址則列於程式行節點的下方。  程式行資料和指令資料的內含值和專有值一定是相同的。  
  
|資料行|描述|  
|---------|--------|  
|**名稱**|模組、函式、行號或指令位址的名稱。|  
|**處理序 ID**|執行程式碼剖析期間的處理序 ID \(PID\)。|  
|**處理序名稱**|處理序的名稱。|  
|**模組名稱**|包含該函式的模組名稱。|  
|**模組路徑**|模組的路徑。|  
|**原始程式檔**|包含這個函式定義的原始程式檔。|  
|**函式行號**|在原始程式檔中這個函式的開頭行號。|  
|**內含配置**|-   對於函式而言，是函式已建立的物件總數。  此數目包括此函式所呼叫的被呼叫端函式中已建立的物件。<br />-   對於模組而言，是在執行程式碼剖析期間，模組中至少有一個函式正在執行時所配置的物件數目。  此數目包括模組函式呼叫的所有函式中已建立的物件。<br />-   對於程式行或指令而言，是程式行或指令已配置的物件總數。|  
|**內含配置 %**|執行程式碼剖析期間內，模組、函式、程式行或指令的內含配置佔所有已配置物件的百分比。|  
|**專有配置**|-   對於目前的函式而言，是函式在執行函式主體的程式碼時 \(也就是函式位於呼叫堆疊頂端時\) 所建立的物件數目。  此數目不包括此函式所呼叫的函式中已建立的物件。<br />-   對於模組而言，是模組中函式的專有配置總和。<br />-   對於程式行或指令而言，是此程式行或指令已建立的物件總數。|  
|**專有配置 %**|執行程式碼剖析期間內，模組、函式、程式行或指令的專有配置佔所有已配置物件的百分比。|  
|**內含位元組**|-   對於函式而言，是函式已配置的位元組數目。  此數目包括此函式所呼叫的函式中已配置的位元組。<br />-   對於模組而言，是在執行程式碼剖析期間，模組中至少有一個函式正在執行時所配置的位元組數目。  此數目包括模組函式呼叫的所有函式中已建立的物件。<br />-   對於程式行或指令而言，是程式行或指令已建立的物件總數。|  
|**內含位元組 %**|執行程式碼剖析期間內，模組、函式、程式行或指令的內含位元組佔所有已配置位元組的百分比。|  
|**專有位元組**|-   對於函式而言，是函式已配置的位元組總數。  此數目不包括此函式所呼叫的函式中已配置的位元組。<br />-   對於模組而言，是模組中函式已配置的專有位元組總和。<br />-   對於程式行或指令而言，是此程式行或指令已配置的物件總數。|  
|**專有位元組 %**|執行程式碼剖析期間內，模組、函式、程式碼或指令的專有位元組佔所有已配置位元組的百分比。|  
  
## 請參閱  
 [如何：自訂報表檢視資料行](../profiling/how-to-customize-report-view-columns.md)   
 [模組檢視 \- 檢測](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [模組檢視](../profiling/modules-view-sampling-data.md)   
 [模組檢視](../profiling/modules-view-instrumentation-data.md)