---
title: ResolveKeySource 工作 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveKeySource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveKeySource task [MSBuild]
- MSBuild, ResolveKeySource task
ms.assetid: 449f06c2-e9aa-4236-ab1e-c45c25452b2e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 548fd2182292d9e7fdeac59d09dab2977c351d0b
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2018
ms.locfileid: "39155525"
---
# <a name="resolvekeysource-task"></a>ResolveKeySource 工作
決定強式名稱金鑰來源。  
  
## <a name="task-parameters"></a>工作參數  
 下表說明 `ResolveKeySource` 工作的參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`AutoClosePasswordPromptShow`|選擇性的 `Int32` 參數。<br /><br /> 取得或設定顯示倒數計時訊息的時間 (以秒為單位)。|  
|`AutoClosePasswordPromptTimeout`|選擇性的 `Int32` 參數。<br /><br /> 取得或設定關閉密碼提示對話方塊前的等候時間，以秒為單位。|  
|`CertificateFile`|選擇性的 `String` 參數。<br /><br /> 取得或設定憑證檔案的路徑。|  
|`CertificateThumbprint`|選擇性的 `String` 參數。<br /><br /> 取得或設定憑證指模。|  
|`KeyFile`|選擇性的 `String` 參數。<br /><br /> 取得或設定金鑰檔案的路徑。|  
|`ResolvedKeyContainer`|選擇性的 `String` 輸出參數。<br /><br /> 取得或設定已解析的金鑰容器。|  
|`ResolvedKeyFile`|選擇性的 `String` 輸出參數。<br /><br /> 取得或設定已解析的金鑰檔案。|  
|`ResolvedThumbprint`|選擇性的 `String` 輸出參數。<br /><br /> 取得或設定所解析的憑證指模。|  
|`ShowImportDialogDespitePreviousFailures`|選擇性的 `Boolean` 參數。<br /><br /> 如果即使先前失敗也要顯示匯入對話方塊，則為 `true`。|  
|`SuppressAutoClosePasswordPrompt`|選擇性的 `Boolean` 參數。<br /><br /> 取得或設定布林值，指定密碼提示對話方塊是否不應該自動關閉。|  
  
## <a name="remarks"></a>備註  
 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其描述，請參閱 [TaskExtension 基底類別](../msbuild/taskextension-base-class.md)。  
  
## <a name="see-also"></a>另請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)