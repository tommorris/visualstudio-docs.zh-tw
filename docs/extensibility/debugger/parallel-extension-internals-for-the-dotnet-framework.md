---
title: 適用於.NET Framework 進行平行擴充內部資訊 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 84b4106509f62f1929f20283bc86c7930c22d39b
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2018
ms.locfileid: "39251081"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>適用於.NET Framework 的平行擴充內部資訊
本章節描述內部型別、 方法和欄位的類別可協助您實作自訂的 parallel extensions 到.NET Framework 偵錯工具。  
  
## <a name="in-this-section"></a>本節內容  
 [Task 類別](../../extensibility/debugger/task-class-internal-members.md)  
 描述內部的資料成員的<xref:System.Threading.Tasks.Task?displayProperty=fullName>類別。  
  
 [TaskScheduler 類別](../../extensibility/debugger/taskscheduler-class-internal-members.md)  
 描述內部的資料成員的<xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>類別。  
  
 [ContingentProperties 類別](../../extensibility/debugger/contingentproperties-class-internal-members.md)  
 描述內部的資料成員的`System.Threading.Tasks.ContingentProperties`類別。  
  
 [AsyncTaskMethodBuilder 結構](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md)  
 描述的內部成員<xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>結構。  
  
 [AsyncTaskMethodBuilder\<TResult > 結構](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md)  
 描述的內部成員<xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>結構。  
  
 [AsyncVoidMethodBuilder 結構](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md)  
 描述的內部成員<xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>結構。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Visual Studio 偵錯工具擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)   
 [平行程式設計](/dotnet/standard/parallel-programming/index)