---
title: "偵錯準備：Windows Form 應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "偵錯 [C#], Windows 應用程式"
  - "偵錯 [J#], Windows 應用程式"
  - "偵錯 [Visual Basic], Windows 應用程式"
  - "偵錯 [Visual Studio], Windows 應用程式"
  - "偵錯 Windows 應用程式"
  - "Windows 應用程式, 偵錯"
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 偵錯準備：Windows Form 應用程式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Windows Form 專案範本會建立 Windows Form 應用程式。  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中可以直接偵錯這種類型的應用程式。  如需詳細資訊，請參閱[Creating a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
 當您以專案範本建立 Windows Form 專案時，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會自動建立偵錯和發行組態所需要的設定。  若有需要，您可以變更這些設定。  這些設定可以在 \[**\<專案名稱\> 屬性頁**\] 對話方塊 \(在 Visual Basic 中為 \[**我的專案**\]\) 中進行變更。  
  
 如需詳細資訊，請參閱 [建議的屬性設定](../debugger/managed-debugging-recommended-property-settings.md)。  
  
 下表顯示一個額外的建議屬性設定。  
  
### 偵錯索引標籤的組態屬性  
  
|**屬性名稱**|**設定**|  
|--------------|------------|  
|**起始動作**|-   通常會設定為 \[**起始專案**\]。  如果您啟動偵錯 \(通常是偵錯 DLL\) 時想要啟動另外一個可執行檔，請設定為 \[**起始外部程式**\]。|  
  
 您可以從 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 內部偵錯 Windows Form 應用程式，或附加至正在執行的應用程式進行偵錯。  如需附加的詳細資訊，請參閱[附加至執行中處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。  
  
### 若要偵錯 C\#、F\# 或 Visual Basic Windows Form 應用程式  
  
1.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中開啟專案。  
  
2.  建立需要的中斷點。  
  
     因為 Windows Form 應用程式是事件驅動的，您的中斷點會進入事件處理常式程式碼中，或事件處理常式程式碼所呼叫的方法中。  通常放置中斷點的事件包括：  
  
    1.  與控制項相關的事件，例如點選、輸入等等。  
  
    2.  與啟動和關閉應用程式有關的事件，例如載入、啟動等等。  
  
    3.  焦點和驗證事件。  
  
     如需詳細資訊，請參閱 [在 Windows Form 中建立事件處理常式](../Topic/Creating%20Event%20Handlers%20in%20Windows%20Forms.md)。  
  
3.  按一下 \[**偵錯**\] 功能表上的 \[**啟動**\]。  
  
4.  使用[偵錯工具基礎](../debugger/debugger-basics.md)中所探討的技巧進行偵錯。  
  
## 請參閱  
 [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)   
 [C\#、F\# 和 Visual Basic 專案類型](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [如何：設定偵錯和發行組態](../debugger/how-to-set-debug-and-release-configurations.md)   
 [C\# 偵錯組態的專案設定](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic 偵錯組態的專案設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [附加至執行中處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Windows Form](../Topic/Windows%20Forms.md)