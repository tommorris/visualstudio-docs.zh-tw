---
title: "IDebugBinder::GetFunctionObject |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugBinder::GetFunctionObject
helpviewer_keywords:
- IDebugBinder::GetFunctionObject method
ms.assetid: 8fb789df-8f30-420d-8ca5-bb496a6738f1
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 3b0ada8d907a8eb082d57e6cf11285565c8d37af
ms.lasthandoff: 02/22/2017

---
# <a name="idebugbindergetfunctionobject"></a>IDebugBinder::GetFunctionObject
這個方法會取得[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)用來建立函式參數的物件。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetFunctionObject(   
   IDebugFunctionObject **ppFunction  
);  
```  
  
```c#  
int GetFunctionObject(  
   out IDebugFunctionObject ppFunction  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppFunction`  
 [out]傳回[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)用來建立函式參數的介面。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK。否則，傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)