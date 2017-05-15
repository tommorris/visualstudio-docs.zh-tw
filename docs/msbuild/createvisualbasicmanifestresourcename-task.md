---
title: "CreateVisualBasicManifestResourceName 工作 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CreateVisualBasicManifestResourceName task
- CreateVisualBasicManifestResourceName task [MSBuild]
ms.assetid: 251c47b9-de32-414b-a138-bf45290af12e
caps.latest.revision: 8
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 5edc245c56e198b974f9f406c42a4e0340f266d8
ms.lasthandoff: 02/22/2017

---
# <a name="createvisualbasicmanifestresourcename-task"></a>CreateVisualBasicManifestResourceName 工作
從指定的 .resx 檔案名稱或其他資源，建立 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 樣式的資訊清單名稱。  
  
## <a name="parameters"></a>參數  
 下表描述 [CreateVisualBasicManifestResourceName 工作](../msbuild/createvisualbasicmanifestresourcename-task.md)的參數。  
  
|參數|說明|  
|---------------|-----------------|  
|`ManifestResourceNames`|<xref:Microsoft.Build.Framework.ITaskItem> `[]` 輸出唯讀參數。<br /><br /> 產生的資訊清單名稱。|  
|`ResourceFiles`|必要的 `String` 參數。<br /><br /> 建立 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 資訊清單名稱的來源資源檔名稱。|  
|`RootNamespace`|選擇性的 `String` 參數。<br /><br /> 資源檔的根命名空間，通常取自專案檔。 可以是 `null`。|  
|`PrependCultureAsDirectory`|選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，就會在資訊清單資源名稱正前方加入文化特性名稱做為目錄名稱。 預設值為 `true`。|  
|`ResourceFilesWithManifestResourceNames`|選擇性的 `String` 唯讀輸出參數。<br /><br /> 傳回現在包含資訊清單資源名稱的資源檔名稱。|  
  
## <a name="remarks"></a>備註  
 [CreateVisualBasicManifestResourceName 工作](../msbuild/createvisualbasicmanifestresourcename-task.md)會決定要指派給指定的 .resx 或其他資源檔的適當資訊清單資源名稱。 此工作會為資源檔提供邏輯名稱，然後將它附加到輸出參數做為中繼資料。  
  
 除了上面所列的參數，此工作會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別的參數，而其本身是繼承自 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其說明，請參閱 [TaskExtension 基底類別](../msbuild/taskextension-base-class.md)。  
  
## <a name="see-also"></a>另請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)