---
title: "IDebugProgram2::CanDetach |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgram2::CanDetach
helpviewer_keywords:
- IDebugProgram2::CanDetach
ms.assetid: dcd9ab6c-49e5-447e-aa7c-89f571f4a052
caps.latest.revision: 7
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
ms.openlocfilehash: fba40d6cb4d2e9fc3a26b6df34f5d18cdb0401b6
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprogram2candetach"></a>IDebugProgram2::CanDetach
判斷偵錯引擎 (DE) 可以中斷連結的程式。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT CanDetach(  
   void  
);  
```  
  
```c#  
int CanDetach();  
```  
  
## <a name="return-value"></a>傳回值  
 如果卸離，傳回`S_OK`; 否則傳回錯誤碼。 傳回`S_FALSE`如果 DE 無法中斷連結的程式。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)