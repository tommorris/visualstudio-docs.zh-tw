---
title: SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND 列舉 |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b3aa4966-e110-4b30-b368-1281a9740dbd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6fe5b308ea75956d9e5826b4daadaef3a823141f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734148"
---
# <a name="scripterrordebugexceptionthrownkind-enumeration"></a>SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND 列舉
指出擲回的例外狀況的類型。 這個列舉型別由[IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md)方法。  
  
> [!IMPORTANT]
>  這些常數是由 PDM 11.0 和更新版本所實作。 可在 activdbg100.h 中找到。  
  
## <a name="syntax"></a>語法  
  
```  
typedef SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND  
```  
  
## <a name="members"></a>成員  
  
|成員|值|描述|  
|------------|-----------|-----------------|  
|ETK_FIRST_CHANCE|0x00000000|此例外狀況是第一個可能發生的例外狀況。|  
|ETK_USER_UNHANDLED|0x00000001|使用者程式碼中未處理此例外狀況。|  
|ETK_UNHANDLED|0x00000002|程式碼中未處理此例外狀況。|  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptErrorDebug110 介面](../../winscript/reference/iactivescripterrordebug110-interface.md)