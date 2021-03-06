---
title: 處理序發生無法復原的錯誤
ms.date: 06/22/2018
ms.topic: troubleshooting
helpviewer_keywords:
- unrecoverable error
- error, process
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: ebd530b9db139cb232f735f7d6401199cab2f6fd
ms.sourcegitcommit: e2373d40ca9829cee63519152a97172763471e21
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "36325698"
---
# <a name="visual-studio-unrecoverable-process-error"></a>Visual Studio 無法復原的程序錯誤

Visual Studio 2017 會使用多個跨處理序的程序執行所需的背景工作，例如即時的單元測試、程式碼分析器等等。 這些處理序會跨處理序執行，以保障 Visual Studio 效能優勢 (例如，在執行長時間且需要大量資源的工作時，確保 Visual Studio 得以快速回應)。 此外，由於 Visual Studio 是 32 位元處理序，跨處理序執行程序時，可讓需耗費大量記憶體的工作擁有較充沛的記憶體運作空間。

如果 *ServiceHub.RoslynCodeAnalysisService.exe* 或 *ServiceHub.RoslynCodeAnalysisService32.exe* 處理序因某個原因而結束，則會出現快顯資訊列，訊息如下：

**「很抱歉，Visual Studio 所使用的處理序發生無法復原的錯誤。建議您儲存工作，然後關閉並重新啟動 Visual Studio。」**

如果您看到此訊息，應該儲存工作，然後關閉並重新啟動 Visual Studio。

## <a name="list-of-processes"></a>處理序清單

以下是 Visual Studio 所使用之跨處理序的處理序清單。 此清單包含特定工作流程或情節中啟動的處理序；因此，在大部分情況下，它們不會全部同時執行。

- Microsoft.Alm.Shared.Remoting.RemoteContainer.dll
- Microsoft.CodeAnalysis.LiveUnitTesting.EntryPoint
- PerfWatson2.exe
- ServiceHub.Host.Node.x86.exe
- ServiceHub.IdentityHost.exe
- ServiceHub.VSDetouredHost.exe
- ServiceHub.SettingsHost.exe
- ServiceHub.Host.CLR.x86.exe
- ServiceHub.RoslynCodeAnalysisService32.exe
- ServiceHub.RoslynCodeAnalysisService.exe
- WindowsAzureGuestAgent.exe
- WindowsAzureTelemetryService.exe
- WaAppAgent.exe

如果所有這些處理序意外終止，則 Visual Studio 內的某些功能會停止運作。 針對某些處理序，遺失功能可能不重要。 針對其他處理序，則會影響 Visual Studio 的穩定性，並顯示錯誤訊息。