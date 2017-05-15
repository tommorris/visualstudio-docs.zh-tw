---
title: "SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: b3aa4966-e110-4b30-b368-1281a9740dbd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND 列舉
指出擲回的例外狀況的類型。  這個列舉是由 [IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md) 方法所使用。  
  
> [!IMPORTANT]
>  這些常數是由 PDM 11.0 和更新版本所實作。  可在 activdbg100.h 中找到。  
  
## 語法  
  
```  
typedef SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND  
```  
  
## 成員  
  
|成員|值|描述|  
|--------|-------|--------|  
|ETK\_FIRST\_CHANCE|0x00000000|此例外狀況是第一個可能發生的例外狀況。|  
|ETK\_USER\_UNHANDLED|0x00000001|使用者程式碼中未處理此例外狀況。|  
|ETK\_UNHANDLED|0x00000002|程式碼中未處理此例外狀況。|  
  
## 請參閱  
 [IActiveScriptErrorDebug110 介面](../../winscript/reference/iactivescripterrordebug110-interface.md)