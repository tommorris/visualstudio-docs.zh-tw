---
title: 與 VSTU 共用 Unity 記錄回呼 | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 3bf25ed2764078f2d3e0424ab34f4e4a8e470ff5
ms.sourcegitcommit: e6ef03cc415ca67f75fd1f26e0e7b8846857166d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2018
ms.locfileid: "39310016"
---
# <a name="share-the-unity-log-callback-with-vstu"></a>與 VSTU 共用 Unity 記錄回呼
Visual Studio Tools for Unity 使用 Unity 註冊記錄回呼，以便將其主控台串流至 Visual Studio。 如果您的編輯器指令碼也使用 Unity 註冊記錄回呼，VSTU 回呼可能會與您的回呼相衝突。 若要避免這種可能性，請使用 `VisualStudioIntegration.LogCallback` 事件來與 VSTU 合作。

## <a name="demonstrates"></a>示範
 如何共用 Visual Studio Tools for Unity 所建立的 Unity 記錄回呼。

## <a name="example"></a>範例

```csharp
#if ENABLE_VSTU
using System;

using UnityEngine;
using UnityEditor;

using SyntaxTree.VisualStudio.Unity.Bridge;

[InitializeOnLoad]
public class LogCallbackHook
{
    static LogCallbackHook()
    {
        VisualStudioIntegration.LogCallback += (string condition, string trace, LogType type) =>
        {
            // place code that implements your log callback here
        };
    }
}
#endif
```

## <a name="see-also"></a>另請參閱
 [範例：產生專案檔](../cross-platform/customize-project-files-created-by-vstu.md)
