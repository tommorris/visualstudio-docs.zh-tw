---
title: 教學課程： 偵錯 managed 和原生程式碼 （混合模式）
description: 了解如何從使用混合的模式偵錯.NET Core 或.NET Framework 應用程式的原生 DLL 進行偵錯
ms.custom: ''
ms.date: 04/27/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
- C++
helpviewer_keywords:
- mixed mode debugging
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 1f34f6af0a98e71f5feb910f84e8d67ada051ae9
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057033"
---
# <a name="tutorial-debug-managed-and-native-code-in-visual-studio"></a>教學課程： 在 Visual Studio 中的 managed 和原生程式碼偵錯

Visual Studio 可讓您啟用多個偵錯工具類型偵錯時，這稱為混合的模式偵錯。 在本教學課程中，您可以設定在單一的偵錯工作階段中偵錯 managed 和原生程式碼的選項。 本教學課程示範如何偵錯原生程式碼，從受管理的應用程式，但您也可以進行反向，並[偵錯 managed 程式碼與原生應用程式](../debugger/how-to-debug-in-mixed-mode.md)。 偵錯工具也支援其他類型的混合的模式偵錯，例如偵錯[Python 和原生程式碼](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md)，並在應用程式類型，例如 ASP.NET 中使用指令碼偵錯工具。

在本教學課程中，您將進行下列作業：

> [!div class="checklist"]
> * 建立簡單的原生 DLL
> * 建立簡單.NET Core 或.NET Framework 的應用程式呼叫 DLL
> * 開始偵錯工具
> * 叫用受管理的應用程式的中斷點
> * 逐步執行原生程式碼

## <a name="prerequisites"></a>必要條件

* 您必須已安裝的 Visual Studio 和**使用 c + + 的桌面開發**工作負載。

    如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)頁面免費進行安裝。

    如果您需要安裝工作負載，但已擁有 Visual Studio，請在 [新增專案] 對話方塊的左窗格中，按一下 [開啟 Visual Studio 安裝程式]。 Visual Studio 安裝程式即會啟動。 選擇 [Node.js 開發] 工作負載，然後選擇 [修改]。

* 您也必須擁有  **.NET 桌面開發**工作負載或**跨平台開發的.NET Core**安裝工作負載，取決於哪些應用程式，輸入您想要建立。

## <a name="create-a-simple-native-dll"></a>建立簡單的原生 DLL

1. 在 Visual Studio 中，選擇**檔案** > **新增** > **專案**。

1. 在**新的專案**對話方塊方塊中，選擇**Visual c + +**，**一般**從 [已安裝的範本] 區段中，然後在中間窗格中選取**空專案**.

1. 在 **名稱**欄位中，輸入**混合模式-偵錯**，按一下 **確定**。

    Visual Studio 會建立空的專案，就會出現在 [方案總管] 中，在右窗格中。

1. 在 方案總管 中，以滑鼠右鍵按一下**原始程式檔**c + + 中的節點專案，，然後選擇**新增** > **新項目**，然後選取  **c + +檔案 (.cpp)**。 將檔案命名**混合 Mode.cpp**，然後選擇**新增**。

    Visual Studio 會加入新的 c + + 檔案。

1. 下列程式碼複製到*混合 Mode.cpp*:

    ```cpp
    #include "Mixed_Mode.h"
    ```
1. 在 方案總管 中，以滑鼠右鍵按一下**標頭檔**c + + 中的節點專案，，然後選擇**新增** > **新項目**，然後選取  **標頭檔 (.h)**。 將檔案命名**混合 Mode.h**，然後選擇**新增**。

    Visual Studio 會加入新的標頭檔。

1. 下列程式碼複製到*混合 Mode.h*:

    ```cpp
    #ifndef MIXED_MODE_MULTIPLY_HPP
    #define MIXED_MODE_MULTIPLY_HPP

    extern "C"
    {
        __declspec(dllexport) int __stdcall mixed_mode_multiply(int a, int b) {
            return a * b;
        }
    }
    #endif
    ```

1. 從 偵錯 工具列中，選取 **偵錯**組態和**任何 CPU**做為平台，或適用於.NET Core，選取**x64**做為平台。

    > [!NOTE]
    > 在.NET Core 上選擇  **x64**做為平台。 .NET core 一律會執行 64 位元模式中，這是必要的。

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案節點 (**混合模式-偵錯**)，然後選擇**屬性**。

1. 在 **屬性**頁面上，選擇**組態屬性** > **連結器** > **進階**，及然後在**沒有進入點**下拉式清單中，選取**NO**。 然後套用的設定。

1. 在 **屬性**頁面上，選擇**組態屬性** > **一般**，然後選取 **動態程式庫 (.dll)** 從**組態類型**欄位。 然後套用的設定。

    ![切換至原生 DLL](../debugger/media/mixed-mode-set-as-native-dll.png)

1. 以滑鼠右鍵按一下專案，然後選擇 **偵錯** > **建置**。

    未出現任何錯誤，應該可以建置專案。

## <a name="create-a-simple-net-framework-or-net-core-app-to-call-the-dll"></a>建立呼叫 DLL 的簡單.NET Framework 或.NET Core 應用程式

1. 在 Visual Studio 中，選擇**檔案** > **新增** > **專案**。

1. 選擇您的應用程式程式碼的範本。

    適用於.NET Framework 中**新的專案**對話方塊方塊中，選擇**Visual C#**， **Windows Desktop**從已安裝的範本 區段中，然後在中間窗格中選取**主控台應用程式 (.NET Framework)**。

    適用於.NET Core 中**新專案**對話方塊方塊中，選擇**Visual C#**， **.NET Core**從已安裝的範本 區段中，然後在中間窗格中選取**主控台應用程式 (.NET Core)**。

1. 在 **名稱**欄位中，輸入**Mixed_Mode_Calling_App**然後按一下**確定**。

    Visual Studio 建立主控台專案，就會出現在 [方案總管] 中，在右窗格中。

1. 在  *Program.cs*，取代為下列程式碼中的預設程式碼：

    ```csharp
    using System;
    using System.Runtime.InteropServices;

    namespace Mixed_Mode_Calling_App
    {
        public class Program
        {
            // Replace the file path shown here with the
            // file path on your computer. For .NET Core, the typical (default) path
            // for a 64-bit DLL might look like this:
            // C:\Users\username\source\repos\Mixed-Mode-Debugging\x64\Debug\Mixed-Mode-Debugging.dll
            // Here, we show a typical path for a DLL targeting the **Any CPU** option.
            [DllImport(@"C:\Users\username\source\repos\Mixed-Mode-Debugging\Debug\Mixed-Mode-Debugging.dll", EntryPoint =
            "mixed_mode_multiply", CallingConvention = CallingConvention.StdCall)]
            public static extern int Multiply(int x, int y);
            public static void Main(string[] args)
            {
                int result = Multiply(7, 7);
                Console.WriteLine("The answer is {0}", result);
                Console.ReadKey();
            }
        }
    }
    ```

## <a name="configure-mixed-mode-debugging-net-framework"></a>設定混合的模式偵錯 (.NET Framework)

1. 在 [方案總管] 中，以滑鼠右鍵按一下 managed **Mixed_Mode_Calling_App**專案，然後選擇**設定為啟始專案**。

1. 以滑鼠右鍵按一下 managed **Mixed_Mode_Calling_App**專案，，然後選擇**屬性**，然後選擇**偵錯**的左窗格中。 選取 **啟用機器碼偵錯**，然後關閉 屬性 頁面，以儲存變更。

    ![啟用混合的模式偵錯](../debugger/media/mixed-mode-enable-native-code-debugging.png)

## <a name="configure-mixed-mode-debugging-net-core"></a>設定混合的模式偵錯 （.NET Core）

在 Visual Studio 2017 的大部分版本中，您必須啟用混合的模式偵錯原生程式碼中使用.NET Core 應用程式*launchSettings.json*檔案而不是**屬性**頁面。 若要追蹤這項功能的 UI 更新，請參閱這[GitHub 問題](https://github.com/dotnet/project-system/issues/1125)。

1. 開啟*launchSettings.json*中的檔案*屬性*資料夾。 根據預設，您可以在這個位置中找到檔案。

    *C:\Users\<使用者名稱 > \source\repos\Mixed_Mode_Calling_App\Properties*

    如果檔案不存在，請開啟專案屬性 (以滑鼠右鍵按一下 [managed **Mixed_Mode_Calling_App**方案總管] 中專案，然後選取**屬性**)。 進行中的暫存變更**偵錯**索引標籤，然後建置您的專案。 還原您所做的變更。

1. 在  *lauchsettings.json*檔案中，新增下列屬性：

    ```csharp
    "nativeDebugging": true
    ```

    因此，比方說，您的檔案看起來可能如下所示：

    ```csharp
    {
      "profiles": {
        "Mixed_Mode_Calling_App": {
          "commandName": "Project",
          "nativeDebugging": true
        }
      }
    }
    ```

## <a name="set-a-breakpoint-and-start-the-debugger"></a>設定中斷點並開始偵錯工具

1. 在 C# 專案中，開啟*Program.cs*和下列程式碼中設定中斷點，在左邊界按一下：

    ```csharp
    int result = Multiply(7, 7);
    ```

    紅色圓圈會出現在左邊界來指出您已設定中斷點。

1. 按下**F5** (**偵錯** > **開始偵錯**) 啟動偵錯工具。

    偵錯工具會在您設定的中斷點上暫停。 黃色箭號表示目前已偵錯工具暫停。

## <a name="step-into-native-code"></a>逐步執行原生程式碼

1. 當受管理的應用程式暫停時，按下**F11** (**偵錯** > **逐步執行**)。

    以原生程式碼的標頭檔隨即開啟，您會看到偵錯工具暫停時，黃色箭號。

    ![逐步執行原生程式碼](../debugger/media/mixed-mode-step-into-native-code.png)

    現在，您可以執行下列動作集，並叫用中斷點並檢查變數。

1. 暫留以查看其值的變數。

1. 看看**自動變數**並**區域變數**視窗，以查看變數和其值。

    當偵錯工具暫停時，您可以使用其他偵錯工具功能這類**監看式**視窗和**呼叫堆疊**視窗。

1. 按下**F11**一次，讓偵錯工具一列。

1. 按下**Shift + F11** (**偵錯** > **跳離函式**) 若要繼續應用程式執行，然後再暫停中受管理的應用程式。

1. 按 **F5** 繼續執行應用程式。

    恭喜您！ 您已完成本教學課程，在混合的模式偵錯。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已了解如何藉由啟用混合的模式偵錯，從受管理的應用程式的原生程式碼進行偵錯。 如需其他偵錯工具功能的概觀，請參閱下列文章：

> [!div class="nextstepaction"]
> [偵錯工具簡介](../debugger/debugger-feature-tour.md)
