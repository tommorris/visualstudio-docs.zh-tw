---
title: "偵錯 64 位元應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
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
helpviewer_keywords: 
  - "偵錯 [Visual Studio], 64 位元"
  - "64 位元偵錯"
ms.assetid: db648e5f-6375-4e2d-aa98-eb7261958927
caps.latest.revision: 32
caps.handback.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 偵錯 64 位元應用程式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以對本機電腦或遠端電腦上執行的 64 位元應用程式進行偵錯。  
  
 若要對遠端電腦上執行的 64 位元應用程式進行偵錯，請參閱 [遠端偵錯](../debugger/remote-debugging.md)。  
  
 若要在本機偵錯 64 位元應用程式，Visual Studio 會使用 64 位元背景工作處理序 \(msvsmon.exe\) 來執行無法在 32 位元 Visual Studio 處理序內完成的低階作業。  
  
 使用 .NET Framework 3.5 \(含\) 以前版本的 64 位元處理序不支援混合模式偵錯。  
  
## 偵錯 64 位元應用程式  
 若要嘗試偵錯 64 位元應用程式：  
  
1.  建立 Visual Studio 方案，例如 C\# 主控台應用程式。  
  
2.  使用組態管理員將組態設定為 64 位元。 如需詳細資訊，請參閱[如何：將專案設定成以平台為目標](../ide/how-to-configure-projects-to-target-platforms.md)。  
  
3.  此時會啟動 64 位元版本的遠端偵錯工具 \(msvsmon.exe\)。 只要開啟具有 64 位元組態的方案，就會執行此工具。  
  
4.  開始偵錯。 您應該會與 32 位元組態有相同的體驗。 如果您收到錯誤，請參閱下列＜疑難排解＞一節。  
  
## 64 位元偵錯疑難排解  
 您可能會看到錯誤：「64 位元偵錯作業所花的時間超出預期」。 在此情況下，Visual Studio 已傳送要求到 64 位元版本的 msvsmon.exe，但該要求的結果卻花很長的時間傳回。  
  
 此錯誤的主要原因有兩個：  
  
-   電腦上所安裝的網路安全性軟體造成網路堆疊不可靠，因此已丟棄通過 localhost 的封包。 請嘗試停用所有網路安全性軟體，看看這樣做是否可以解決問題。 如果是，請將軟體干擾 localhost 流量的情形回報給您的網路安全性軟體廠商。  
  
-   您在使用 Visual Studio 時遇到停止回應或效能問題。 如果此問題經常發生，您可以收集 Visual Studio 的傾印 \(devenv.exe\) 和背景工作處理序 \(msvsmon.exe\)，然後傳送給 Microsoft。 如需回報問題的資訊，請參閱 [如何回報在使用 Visual Studio 時發生的問題](../Topic/How%20to%20Report%20a%20Problem%20with%20Visual%20Studio.md)。  
  
## 請參閱  
 [64 位元應用程式](../Topic/64-bit%20Applications.md)   
 [為 64 位元設定程式](/visual-cpp/build/configuring-programs-for-64-bit-visual-cpp)   
 [Visual Studio IDE 64 位元支援](../ide/visual-studio-ide-64-bit-support.md)   
 [使用傾印檔案偵錯應用程式當機和停止回應的問題](../debugger/using-dump-files.md)   
 [遠端偵錯](../debugger/remote-debugging.md)