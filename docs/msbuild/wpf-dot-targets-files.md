---
title: "WPF .Targets 檔案 | Microsoft Docs"
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
- combining tasks into a .targets file to build an MSBuild project [WPF MSBuild]
- WPF .targets files [WPF MSBuild], introduction
- WPF .targets files [WPF MSBuild]
ms.assetid: e85a3ff4-dedd-4ff4-9b22-3a1e94755362
caps.latest.revision: 5
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: ec0e05758a3012c88d76f276b30b44bb3f6f2ef6
ms.lasthandoff: 02/22/2017

---
# <a name="wpf-targets-files"></a>WPF .Targets 檔案
[!INCLUDE[TLA#tla_winclient](../misc/includes/tlasharptla_winclient_md.md)] 會透過新增一組 [!INCLUDE[TLA2#tla_wpf](../msbuild/includes/tla2sharptla_wpf_md.md)] 特定的工作來延伸 [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)]，這些工作會合併到特殊的 .targets 檔案 **Microsoft.WinFX.targets** 中。 此檔案會合併一組在 [!INCLUDE[TLA#tla_winclient](../misc/includes/tlasharptla_winclient_md.md)] 中建置 [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] 專案所需的 [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] 工作。  
  
## <a name="see-also"></a>另請參閱  
 [.Targets 檔案](../msbuild/msbuild-dot-targets-files.md)   
 [MSBuild 參考](../msbuild/msbuild-reference.md)   
 [建置 WPF 應用程式 (WPF)](http://msdn.microsoft.com/Library/a58696fd-bdad-4b55-9759-136dfdf8b91c)