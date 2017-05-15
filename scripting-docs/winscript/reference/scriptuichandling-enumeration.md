---
title: "SCRIPTUICHANDLING 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 5b89c6e8-064c-406f-bb14-91c77bf42daf
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# SCRIPTUICHANDLING 列舉
表示應該處理 UI 控制項的方法。  
  
## 語法  
  
```vb  
typedef enum tagSCRIPTUICHANDLING {   
    SCRIPTUICHANDLING_ALLOW = 0,   
    SCRIPTUICHANDLING_NOUIERROR = 1,   
    SCRIPTUICHANDLING_NOUIDEFAULT = 2,   
} SCRIPTUICHANDLING;  
  
```  
  
## 列舉值  
  
|||  
|-|-|  
|SCRIPTUICHANDLING\_ALLOW|允許控制項中顯示。|  
|SCRIPTUICHANDLING\_NOUIERROR||  
|SCRIPTUICHANDLING\_NOUIDEFAULT||