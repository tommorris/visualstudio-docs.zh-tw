---
title: XslTransformation 工作 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9a18dff58b38dc80eade3ef030b4156b040cc8ce
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2018
ms.locfileid: "39233070"
---
# <a name="xsltransformation-task"></a>XslTransformation 工作
使用 XSLT 或已編譯的 XSLT 來轉換 XML 輸入，並輸出到輸出裝置或檔案。  
  
## <a name="parameters"></a>參數  
 下表說明 `XslTransformation` 工作的參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`OutputPaths`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定 XML 轉換的輸出檔案。|  
|`Parameters`|選擇性的 `String` 參數。<br /><br /> 指定「XSLT 輸入」文件的參數。|  
|`XmlContent`|選擇性的 `String` 參數。<br /><br /> 以字串形式指定 XML 輸入。|  
|`XmlInputPaths`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定 XML 輸入檔案。|  
|`XslCompiledDllPath`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定已編譯的 XSLT。|  
|`XslContent`|選擇性的 `String` 參數。<br /><br /> 以字串形式指定 XSLT 輸入。|  
|`XslInputPath`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定 XSLT 輸入檔案。|  
  
## <a name="remarks"></a>備註  
 除了具有表格中所列的參數之外，此工作也繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其描述，請參閱 [TaskExtension 基底類別](../msbuild/taskextension-base-class.md)。  
  
## <a name="see-also"></a>另請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)