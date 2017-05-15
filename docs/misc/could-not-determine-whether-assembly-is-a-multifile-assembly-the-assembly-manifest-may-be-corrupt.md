---
title: "無法決定 &#39;assembly&#39; 是否為多檔案組件。 組件資訊清單可能已損毀。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannotfindscatterinfo"
ms.assetid: 2d4af6ef-c2f8-4764-af8b-580d433bfbc9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 無法決定 &#39;assembly&#39; 是否為多檔案組件。 組件資訊清單可能已損毀。
專案系統無法讀取專案所參考的組件，因此專案系統無法判斷組件所參考的檔案。  
  
 **更正這個錯誤**  
  
-   重新安裝 Visual Studio \(如果組件隨附 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 或 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\)。  
  
     \-或\-  
  
-   重新安裝適當的協力廠商控制項。  
  
     此錯誤不會防止建置專案。 不過，可能會發生執行階段錯誤。  
  
## 請參閱  
 [中斷參考的疑難排解](../ide/troubleshooting-broken-references.md)   
 [NIB 如何：使用加入參考對話方塊以加入或移除參考](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/zh-tw/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)