---
title: TargetCLR | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dd27aadb0b4335cc122a1b45e9f37e13d9a69f4c
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34476517"
---
# <a name="targetclr"></a>TargetCLR
**TargetCLR** 選項指定當應用程式載入多個 CLR 版本時要分析的 Common Language Runtime (CLR) 版本。  
  
 根據預設，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具以應用程式載入的第一個 CLR 版本為目標。  
  
## <a name="syntax"></a>語法  
  
```cmd  
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]   
```  
  
#### <a name="parameters"></a>參數  
 `ClrVersion`  
 CLR 的版本號碼。 使用版本格式 **vN.N.NNNNN**。  
  
## <a name="required-options"></a>必要選項  
 **TargetCLR** 選項僅能與 [啟動] 或 [附加] 選項一起使用。  
  
 **Launch：** `AppName`  
 啟動指定的應用程式並開始分析。  
  
 **Attach:** `PID`  
 開始分析指定的處理序。  
  
## <a name="example"></a>範例  
 本例使用 TargetCLR 選項確定分析的 CLR 版本是 4.0.11003。  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```