---
title: "Visual Studio 分析工具 API 參考 (原生) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance tools, API
- Profiler, API
ms.assetid: a0c3be92-c263-4678-9fb9-bafead3bd5f5
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
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
ms.openlocfilehash: d30482dd7f179b38babf0bdaab9cd0e38389541e
ms.lasthandoff: 02/22/2017

---
# <a name="visual-studio-profiler-api-reference-native"></a>Visual Studio 分析工具 API 參考 (原生)
Visual Studio 分析工具 API 可讓您以程式設計方式控制收集的資料量，並在分析期間插入時間戳記和設定檔標記。 若要使用原生 API，您可以在您的專案中包含 VSPerf.h 標頭檔，並加入 VSPerf.lib。  
  
> [!NOTE]
>  根據預設，VSPerf.h 和 VSPerf.lib 位於 \<磁碟機>:\Program Files\Microsoft Visual Studio 9\Team Tools\Performance Tools\PerfSDK 目錄中。  
  
## <a name="in-this-section"></a>本節內容  
 [CommentMarkAtProfile](../profiling/commentmarkatprofile.md)  
  
 [CommentMarkProfile](../profiling/commentmarkprofile.md)  
  
 [MarkProfile](../profiling/markprofile.md)  
  
 [NameProfile](../profiling/nameprofile.md)  
  
 [ResumeProfile](../profiling/resumeprofile.md)  
  
 [StartProfile](../profiling/startprofile.md)  
  
 [StopProfile](../profiling/stopprofile.md)  
  
 [SuspendProfile](../profiling/suspendprofile.md)  
  
 [PROFILE_CURRENTID](../profiling/profile-currentid.md)  
  
## <a name="see-also"></a>另請參閱  
 [程式碼剖析工具 API](../profiling/profiling-tools-apis.md)   
 [逐步解說：使用分析工具 API](../profiling/walkthrough-using-profiler-apis.md)