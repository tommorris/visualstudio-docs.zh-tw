---
title: SccPopulateDirList 函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5315f3156f71310c92069ec3743232e98818b9a5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137140"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList 函式
此函式判斷哪一個目錄以及 （選擇性） 檔案會儲存在原始檔控制，指定要檢查的目錄清單。  
  
## <a name="syntax"></a>語法  
  
```cpp  
SCCRTN SccPopulateDirList(  
   LPVOID        pContext,  
   LONG          nDirs,  
   LPCSTR*       lpDirPaths,  
   POPDIRLISTFUNCpfnPopulate,  
   LPVOID        pvCallerData,  
   LONG          fOptions  
);  
```  
  
#### <a name="parameters"></a>參數  
 pContext  
 [in]原始檔控制外掛程式的內容指標。  
  
 nDirs  
 [in]中的目錄路徑的數目`lpDirPaths`陣列。  
  
 lpDirPaths  
 [in]若要檢查的目錄路徑的陣列。  
  
 pfnPopulate  
 [in]每個目錄路徑和 （選擇性） 中的檔案名稱呼叫的回呼函式`lpDirPaths`(請參閱[POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)如需詳細資訊)。  
  
 pvCallerData  
 [in]要傳遞的值保持不變，回呼函式。  
  
 fOptions  
 [in]控制如何處理目錄的值的組合 (請參閱 [PopulateDirList 旗標] 一節[特定命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md)可能的值)。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作預期會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|已成功完成作業。|  
|SCC_E_UNKNOWNERROR|發生錯誤。|  
  
## <a name="remarks"></a>備註  
 只有目錄和 （選擇性） 實際上是在原始檔控制儲存機制的檔案名稱會傳遞至回呼函式中。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [特定的命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [錯誤碼](../extensibility/error-codes.md)