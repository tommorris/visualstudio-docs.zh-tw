---
title: EncUnavailableReason |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4dcf705015925145b790b14a44007fed8d8fad3b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31101767"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!` 代表其原因，**編輯後繼續**不提供。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum tagEncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
typedef enum tagEncUnavailableReason EncUnavailableReason;  
```  
  
```csharp  
public enum EncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
```  
  
#### <a name="parameters"></a>參數  
 ENCUN_NONE  
 沒有特定的理由為何無法使用 編輯後繼續。  
  
 ENCUN_INTEROP  
 編輯後繼續不是使用 InterOp 呼叫期間。  
  
 ENCUN_SQLCLR  
 編輯後繼續使用期間不會使用 Common Language Runtime (CLR) 的 SQL 程序呼叫。  
  
 ENCUN_MINIDUMP  
 編輯後繼續不提供處理小型傾印時發生。  
  
 ENCUN_EMBEDDED  
 編輯後繼續時，無法提供處理內嵌程式碼。  
  
 ENCUN_ATTACH  
 編輯後繼續 無法使用工作階段已附加到，因為未啟動的偵錯工具。  
  
 ENCUN_WIN64  
 編輯後繼續不提供處理 64 位元 Windows 程式碼時。  
  
## <a name="remarks"></a>備註  
 這個列舉型別僅供內部使用由[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]。 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)和[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)方法，以實作自訂連接埠供應商應該會一律傳回`E_NOTIMPL`。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.idl  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)