---
title: "封鎖時間分析報表 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.report.blocking"
helpviewer_keywords: 
  - "並行視覺化檢視，封鎖時間分析報表"
ms.assetid: 3bc45af0-3ba6-4fa3-a336-be8e9ae95107
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# 封鎖時間分析報表
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

這些分析報表會針對每個封鎖分類 \(例如 \[I\/O\] 或 \[同步處理\]\) 特有的呼叫堆疊來提供彙總封鎖時間資料。  先佔報表會列出佔用的處理序，其佔用的目前處理序中的執行個體。  為了建置此分析報表，工具會收集造成封鎖的應用程式開發介面呼叫，並累積其在呼叫堆疊的樹狀圖中。  這些報表中所顯示的資料可能會因目前時間範圍、隱藏執行緒以及可能已套用的下列兩個篩選而有所不同：  
  
-   如果選取了 \[Just My Code\]，就只會顯示具有使用者程式碼以及使用者程式碼下一層的堆疊框架。  
  
-   如果設定了 \[減少雜訊\] 值，此報表就會略過低於指定之頻率的定序堆疊。  
  
 展開所有樹狀呼叫輸入來找出封鎖時間花費的程式碼。  若要尋找原始檔的輸入的行，請在捷徑功能表中選取 \[**檢視原始檔**\]。  若要找出呼叫這一行程式碼，請在捷徑功能表上選取 \[**檢視呼叫位置**\]。  如果只有一個呼叫位置，則按一下會連接到此呼叫位置的程式碼行，並以反白顯示。  如果有多個呼叫位置，您可以選擇輸入然後選取 \[**移至原始檔**\] 按鈕，找出呼叫位置並反白顯示對話方塊才能使用這個命令。  檢視含有最多執行個體、耗用最多時間或兩者皆有呼叫位置的原始程式碼，通常最有幫助。  
  
## 封鎖時間報表資料行  
 下表顯示每份封鎖時間報表中的資料行。  
  
|資料行名稱|說明|  
|-----------|--------|  
|名稱|每個呼叫堆疊層級的函式名稱。|  
|執行個體|可見時間週期的封鎖呼叫執行個體數目。|  
|內含封鎖時間|從呼叫堆疊樹最下層累積至此層級的所有堆疊所耗用的總封鎖時間。  這個內含數目就是此函式之獨佔封鎖時間以及其所有子節點之獨佔封鎖時間的總和。|  
|獨佔封鎖時間|此函式在呼叫堆疊的最低層級時所花的總封鎖時間。  具有高獨佔封鎖時間的唯一呼叫堆疊項目可能是需要關切的函式。|  
|API\/等候類別|只有位於呼叫堆疊最低層級的函式才會顯示。  只要辨識出封鎖呼叫的特徵標記，就會提供封鎖 API 的名稱。  如果無法辨識特徵標記，則其會提供核心回報的資訊。|  
|詳細資料|此函式的完整名稱。  這包括當函式可使用時，該函式的行數。|  
  
### 同步處理  
 同步處理報表會顯示因為同步處理而造成區段封鎖的呼叫，以及每個呼叫堆疊的彙總封鎖時間。  如需詳細資訊，請參閱[同步處理時間](../profiling/synchronization-time.md)。  
  
### 睡眠  
 睡眠報表會顯示因時間耗用在睡眠而導致封鎖的呼叫，以及每個呼叫堆疊的彙總封鎖時間。  如需詳細資訊，請參閱[睡眠時間](../profiling/sleep-time.md)。  
  
### I\/O  
 I\/O 報表會顯示因為 I\/O 而造成區段封鎖的呼叫，以及每個呼叫堆疊的彙總封鎖時間。  如需詳細資訊，請參閱[I\/O 時間 \(執行緒檢視\)](../profiling/i-o-time-threads-view.md)。  
  
### 記憶體管理  
 記憶體管理報表會顯示因為記憶體管理作業而造成區段封鎖的呼叫，以及每個呼叫堆疊的彙總封鎖時間。  如需詳細資訊，請參閱[記憶體管理時間](../profiling/memory-management-time.md)。  
  
### 先佔  
 先佔報表會列出執行個體數目優先於目前處理序的處理序。您可以展開每個處理序來檢視取代目前處理序的執行緒之特定執行緒，以及檢視先佔執行個體失敗的每個執行緒。  相對於其他報表，這份封鎖報表比較沒有需要追究管理之處，因為先佔通常是作業系統對處理序進行的強制行為，而非程式碼所造成。  如需詳細資訊，請參閱[先佔時間](../profiling/preemption-time.md)。  
  
### UI 處理  
 UI 處理報表會顯示因為 UI 處理而造成區段封鎖的呼叫，以及每個呼叫堆疊的彙總封鎖時間  如需詳細資訊，請參閱[UI 處理時間](../profiling/ui-processing-time.md)。  
  
## 請參閱  
 [執行緒檢視](../profiling/threads-view-parallel-performance.md)