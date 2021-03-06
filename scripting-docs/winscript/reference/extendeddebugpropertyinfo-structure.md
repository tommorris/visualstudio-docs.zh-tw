---
title: ExtendedDebugPropertyInfo 結構 |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ExtendedDebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- ExtendedDebugPropertyInfo structure
ms.assetid: f2cf6477-454b-4d13-95da-ae4c90daa175
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee06b0ace93f068e0530a3aa62b8c28d11069f44
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641328"
---
# <a name="extendeddebugpropertyinfo-structure"></a>ExtendedDebugPropertyInfo 結構
擴充`DebugPropertyInfo`結構與其他成員，以便歸納擴充的屬性。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct ExtendedDebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   LPOLESTR  bstrName;  
   LPOLESTR  bstrType;  
   LPOLESTR  bstrValue;  
   LPOLESTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
   DWORD  nDISPID;  
   DWORD  nType;  
   VARIANT  varValue;  
   ILockBytes*  plbValue;  
   IDebugExtendedProperty*  pDebugExtProp;  
};  
```  
  
## <a name="members"></a>成員  
 `dwValidFields`  
 用來指定哪些欄位會初始化列舉的資料型別。  
  
 `bstrName`  
 在內容屬性名稱。  
  
 `bstrType`  
 屬性類型為格式化的字串。  
  
 `bstrValue`  
 格式化字串為屬性值。  
  
 `bstrFullName`  
 屬性的完整名稱。  
  
 `dwAttrib`  
 列舉，指定偵錯屬性的屬性旗標。  
  
 `pDebugProp`  
 `IDebugProperty`物件對應至這個`ExtendedDebugPropertyInfo`。  
  
 `nDISPID`  
 分派識別碼。  
  
 `nType`  
 擴充的屬性的型別。  
  
 `varValue`  
 如果可以納入 VARIANT 擴充的屬性值。  
  
 `plbValue`  
 屬性值的實際資料位元組。  
  
 `pDebugExtProp`  
 `IDebugExtendedProperty`物件對應至這個`ExtendedDebugPropertyInfo`。  
  
## <a name="see-also"></a>另請參閱  
 [DebugPropertyInfo 結構](../../winscript/reference/debugpropertyinfo-structure.md)   
 [IDebugProperty 介面](../../winscript/reference/idebugproperty-interface.md)   
 [IDebugExtendedProperty 介面](../../winscript/reference/idebugextendedproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)