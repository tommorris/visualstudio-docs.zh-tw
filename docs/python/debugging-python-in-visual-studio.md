---
title: 對 Python 程式碼進行偵錯
description: 在 Visual Studio 中針對 Python 程式碼的偵錯功能逐步解說，其中包括設定中斷點、逐步執行、檢查值、查看例外狀況，以及在互動式視窗中偵錯。
ms.date: 08/14/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 6766e5e498b631ea4e95a535d65ebf09ff973b59
ms.sourcegitcommit: 4c60bcfa2281bcc1a28def6a8e02433d2c905be6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42627037"
---
# <a name="debug-your-python-code"></a>偵錯您的 Python 程式碼

Visual Studio 提供全面的 Python 偵錯體驗，包括附加至執行中處理序、在 [監看式] 和 [即時運算] 視窗中評估運算式、檢查區域變數、中斷點、逐步執行/跳離/不進入陳述式及**設定下一個陳述式**等。

另請參閱下列案例特定的偵錯文章︰

- [Linux 遠端偵錯](debugging-python-code-on-remote-linux-machines.md)
- [Azure 遠端偵錯](debugging-remote-python-code-on-azure.md)
- [混合模式 Python/C++ 偵錯](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- [混合模式偵錯的符號](debugging-symbols-for-mixed-mode-c-cpp-python.md)

|   |   |
|---|---|
| ![影片的電影攝影機圖示](../install/media/video-icon.png "觀看影片") | [觀看示範 Python 偵錯的影片 (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Debugging-Python-Ep5dp5LWE_3805918567) \(英文\) (3 分 32 秒)。|

<a name="debugging-without-a-project"></a>

> [!Tip]
> Visual Studio 中的 Python 支援在不使用檔案的情況下進行偵錯。 在開啟獨立 Python 檔案的情況下，以滑鼠右鍵按一下編輯器，並選取 [啟動並偵錯]，Visual Studio 就會在不使用引數的情況下，以全域預設環境啟動指令碼 (請參閱 [Python 環境](managing-python-environments-in-visual-studio.md))。 但之後您就有完整的偵錯支援。
>
> 若要控制環境和引數，請建立程式碼的專案，這可以透過[從現有 Python 程式碼](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files)專案範本輕鬆地完成。

<a name="debugging-with-a-project"></a>

## <a name="basic-debugging"></a>基本偵錯

基本偵錯工作流程包含設定中斷點、逐步執行程式碼、檢查值和處理例外狀況，如下列各節所述。

您可以透過 [偵錯] > [開始偵錯] 命令、工具列上的 [開始] 按鈕或 **F5** 鍵開始偵錯工作階段。 這些動作會使用專案的使用中環境，以及已在 [專案屬性] 中指定的任何命令列引數或搜尋路徑 (請參閱[專案偵錯選項](#project-debugging-options))，來啟動您專案的啟動檔案 (在 [方案總管] 中以粗體顯示)。 **Visual Studio 2017 15.6 版**及更新版本會在您沒有啟動檔案集的情況下警示您；較舊的版本可能會在 Python 解譯器執行的情況下開啟輸出視窗，或是該輸出視窗可能會短暫出現並消失。 無論情況為何，請以滑鼠右鍵按一下適當的檔案，然後選取 [設定為啟動檔案]。

> [!Note]
> 偵錯工具一律會以專案的使用中 Python 環境啟動。 若要變更環境，請將其他環境設為使用中，如[針對專案選取 Python 環境](selecting-a-python-environment-for-a-project.md)所述。

### <a name="breakpoints"></a>中斷點

中斷點會在標示的點停止執行程式碼，讓您可以檢查程式狀態。 在程式碼編輯器的左邊界中按一下，或以滑鼠右鍵按一下程式碼行並選取 [中斷點] > [插入中斷點] 以設定中斷點。 具有中斷點的每一行會顯示一個紅點。

![Visual Studio 中的中斷點](media/debugging-breakpoints.png)

按一下紅點或以滑鼠右鍵按一下程式碼行，選取 [中斷點] > [刪除中斷點] 以移除中斷點。 您也可以使用 [中斷點] > [停用中斷點] 命令來停用而不移除它。

> [!Note]
> Python 中的一些中斷點可能會令已使用其他程式設計語言的開發人員感到意外。 在 Python 中，整個檔案就是可執行程式碼，因此 Python 會在載入檔案來處理任何最上層類別或函式定義時執行檔案。 如果已設定中斷點，您可以透過類別宣告發現偵錯工具中斷方式。 這種行為正確，不過有時會很令人意外。

您可以自訂觸發中斷點的條件，例如僅在變數設為特定值或值範圍時中斷。 若要設定條件，以滑鼠右鍵按一下中斷點的紅點，選取 [條件 (Condition)]，然後使用 Python 程式碼建立運算式。 如需 Visual Studio 中這項功能的完整詳細資訊，請參閱[中斷點條件](../debugger/using-breakpoints.md#breakpoint-conditions)。

設定條件時，您也可以設定 [動作 (Action)] 並建立要記錄至輸出視窗的訊息，或選擇自動繼續執行。 記錄訊息會建立所謂的「追蹤點」，而不直接將記錄碼新增到您的應用程式︰

![建立具有中斷點的追蹤點](media/debugging-tracepoint.png)

### <a name="step-through-code"></a>逐步執行程式碼

一旦停在中斷點，在再度中斷之前，您可以使用各種方式逐步執行程式碼或執行程式碼區塊。 在許多地方都可使用下列命令，包括最上層的偵錯工具列、[偵錯] 功能表、程式碼編輯器中的滑鼠右鍵操作功能表，以及透過鍵盤快速鍵 (然而並非所有地方都提供所有命令)：

| 功能 | 按鍵輸入 | 描述 |
| --- | --- | --- |
| **Continue** | **F5** | 執行程式碼，直到下一個中斷點為止。 |
| **逐步執行** | **F11** | 執行下一個陳述式並停止。 如果下一個陳述式是函式的呼叫，偵錯工具會停在所呼叫函式的第一行。 |
| **不進入函式** | **F10** | 執行下一個陳述式，包括呼叫函式 (執行其所有程式碼) 和套用任何傳回值。 不進入函式可讓您輕鬆略過不需偵錯的函式。 |
| **跳離函式** | **Shift**+**F11** | 執行程式碼直到目前的函式結束，然後逐步執行呼叫的陳述式。  當您不需要對目前函式的其餘部分進行偵錯時，此命令非常有用。 |
| **執行至游標處** | **Ctrl**+**F10** | 執行程式碼直到編輯器中插入點 (Caret) 的位置。 此命令可讓您輕鬆略過不需偵錯的程式碼區段。 |
| **設定下一個陳述式** | **Ctrl**+**Shift**+**F10** | 將程式碼中目前的執行點變更為插入點 (Caret) 的位置。 此命令可讓您略過特定的程式碼區段而不執行，例如當您知道程式碼有錯誤或是會產生不想要的副作用時。 |
| **顯示下一個陳述式** | **Alt**+**Num** **&#42;**| 返回下一個將執行的陳述式。 如果您在程式碼中四處尋找卻不記得偵錯工具停止的位置時，此命令很有用。 |

### <a name="inspect-and-modify-values"></a>檢查和修改值

在偵錯工具中停止時，您可以檢查和修改變數的值。 您也可以使用 [監看式] 視窗來監視個別的變數及自訂運算式 (如需一般詳細資訊，請參閱[檢查變數](../debugger/getting-started-with-the-debugger.md#inspect-variables-with-the-autos-and-locals-windows))。

若要使用 **DataTips** 檢視值，只要將滑鼠游標停在編輯器中任一變數的上方。 您可以按一下值來變更它︰

![偵錯工具中的 DataTips](media/debugging-quick-tips.png)

[自動變數] 視窗 ([偵錯] > [視窗] > [自動變數]) 包含與目前的陳述式相關的變數和運算式。 您可以在值資料行中按兩下或選取並按 **F2** 來編輯值：

![偵錯工具中的 [自動變數 (Autos)] 視窗](media/debugging-autos-window.png)

[區域變數] 視窗 ([偵錯] > [視窗] > [區域變數]) 會顯示目前範圍中可再次編輯的所有變數：

![偵錯工具中的 [區域變數 (Locals)] 視窗](media/debugging-locals-window.png)

如需使用 [自動變數] 和 [區域變數] 的詳細資訊，請參閱[在自動變數和區域變數視窗中檢查變數](../debugger/autos-and-locals-windows.md)。

[監看式] 視窗 ([偵錯] > [視窗] > [監看式] > [監看式 1-4]) 可讓您輸入任意 Python 運算式並檢視結果。 運算式會針對每個步驟重新評估︰

![偵錯工具中的 [監看式 (Watch)] 視窗](media/debugging-watch-window.png)

如需使用 [監看式] 的詳細資訊，請參閱[使用監看式及快速監看式視窗在變數設定監看式](../debugger/watch-and-quickwatch-windows.md)。

檢查字串值時 (針對此目的，`str`、`unicode`、`bytes` 和 `bytearray` 全都視為字串)，在值的右邊會出現放大鏡圖示。 按一下圖示，會在快顯對話方塊中顯示不具引號的字串值，其換行和多行式格式非常適合長字串。 此外，選取圖示上的下拉箭號可讓您選取純文字、HTML、XML 和 JSON 視覺效果︰

![字串視覺化工具](media/debugging-string-visualizers.png)

HTML、XML 和 JSON 視覺效果會出現在不同的快顯視窗中，其中的語法會反白顯示，並含有樹狀檢視。

### <a name="exceptions"></a>例外狀況

如果對程式進行偵錯時發生錯誤，但您沒有例外狀況處理常式可以處理它，偵錯工具會在例外狀況的位置中斷︰

![例外狀況快顯](media/debugging-exception-popup.png)

此時，您可以檢查程式狀態，包括呼叫堆疊。 不過，如果您嘗試逐步執行程式碼，將會繼續擲回例外狀況，直到已處理或您的程式結束為止。

[偵錯] > [視窗] > [例外狀況設定] 功能表命令會顯示一個視窗，您可以在其中展開 [Python 例外狀況]：

![例外狀況視窗](media/debugging-exception-settings.png)

每個例外狀況的核取方塊控制當此例外狀況引發時，是否*一律*中斷偵錯工具。 當您想更頻繁地針對特定例外狀況中斷時，請核取此方塊。

根據預設，在原始程式碼中找不到例外狀況處理常式時，大部分的例外狀況都會中斷偵錯工具。 若要變更此行為，請以滑鼠右鍵按一下任何例外狀況，並修改 [當使用者程式碼中未處理時繼續] 選項。 當您想減少針對例外狀況中斷的頻率時，請清除此方塊。

若要設定未顯示在此清單中的例外狀況，請按一下 [新增 (Add)] 按鈕將其加入。 名稱必須符合例外狀況的完整名稱。

## <a name="project-debugging-options"></a>專案偵錯選項

根據預設，偵錯工具會使用標準 Python 啟動器啟動您的程式，不使用任何命令列引數或其他特殊路徑或條件。 在 [方案總管] 中以滑鼠右鍵按一下您的專案，選取 [屬性]，然後選取 [偵錯] 索引標籤來存取專案的偵錯屬性，可以變更啟動選項。

![專案偵錯屬性](media/debugging-project-properties.png)

### <a name="launch-mode-options"></a>啟動模式選項

| 選項 | 描述 |
| --- | --- |
| **標準 Python 啟動器** | 使用相容於 CPython、IronPython 及 Stackless Python 等變體的可攜式 Python 撰寫的偵錯程式碼。 它能為純 Python 程式碼的偵錯提供最佳體驗。 當您附加至執行中的 *python.exe* 處理序時，會使用這個啟動器。 這個啟動器也為 CPython 提供[混合模式偵錯](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)，讓您可以順暢地在 C/C++ 和 Python 程式碼之間逐步執行。 |
| **Web 啟動器** | 在啟動時開啟預設瀏覽器並對範本啟用偵錯。 如需詳細資訊，請參閱 [Web 範本偵錯](python-web-application-project-templates.md#debugging)一節。 |
| **Django Web 啟動器** | 與 Web 啟動器相同，在有回溯相容性需求時才會顯示。 |
| **IronPython (.NET) 啟動器** | 使用 .NET 偵錯工具，它僅適用於 IronPython，但允許在任一 .NET 語言專案 (包括 C# 和 VB) 之間逐步執行。 如果您附加至裝載 IronPython 的執行中 .NET 處理序，會使用這個啟動器。 |

### <a name="run-options-search-paths-startup-arguments-and-environment-variables"></a>執行選項 (搜尋路徑、啟動引數和環境變數)

| 選項 | 描述 |
| --- | --- |
| **搜尋路徑** | 這些值符合在**方案總管**中，專案 [搜尋路徑] 節點所顯示的內容。 您可以在此處修改此值，但使用 [方案總管] 會比較容易，因為可讓您瀏覽資料夾並自動將路徑轉換成相對格式。 |
| **指令碼引數** | 這些引數會新增至用來啟動指令碼的命令，顯示在您的指令碼檔案名稱之後。 此處的第一個項目以 `sys.argv[1]` 的格式提供給您的指令碼，第二個項目則是 `sys.argv[2]`，依此類推。 |
| **解譯器引數** | 這些引數會新增至指令碼名稱之前的啟動器命令列。 此處常見的引數包括控制警告的 `-W ...`，稍微最佳化程式的 `-O` 和使用未緩衝處理之 IO 的 `-u`。 IronPython 使用者可能會使用此欄位傳遞 `-X` 選項，例如 `-X:Frames` 或 `-X:MTA`。 |
| **解譯器路徑** | 覆寫與目前環境相關聯的路徑。 使用非標準解譯器啟動您的指令碼時，此值會很有用。 |
| **環境變數** | 在這個多行文字方塊中，新增 \<NAME>=\<VALUE> 格式的項目。 因為這個設定是最後套用的，在任何現有的全域環境變數之上，而且在依據 [搜尋路徑] 設定 `PYTHONPATH` 之後，所以可以用來手動覆寫那些其他變數中的任一項。 |

## <a name="immediate-and-interactive-windows"></a>即時運算視窗和互動式視窗

偵錯工作階段期間有兩個可用的互動式視窗︰標準的 Visual Studio [即時運算] 視窗，以及 [Python 互動式偵錯] 視窗。

[即時運算] 視窗 ([偵錯] > [視窗] > [即時運算]) 用於快速評估 Python 運算式和檢查或指派執行中程式內的變數。 如需詳細資料，請參閱一般[即時運算視窗](../ide/reference/immediate-window.md)一文。

[Python 互動式偵錯] 視窗 ([偵錯] > [視窗] > [Python 互動式偵錯]) 更豐富，因為它可在偵錯時提供完整的[互動式 REPL](python-interactive-repl-in-visual-studio.md) 體驗，包括撰寫和執行程式碼。 它會使用標準 Python 啟動器自動連線到在偵錯工具中啟動的任一處理序 (包括透過 [偵錯] > [附加至處理序] 附加的處理序)。 不過，它在使用混合模式 C/C++ 偵錯時無法使用。

![[Python 偵錯互動式 (Python Debug Interactive)] 視窗](media/debugging-interactive.png)

[互動式偵錯] 視窗支援[標準 REPL 命令](python-interactive-repl-in-visual-studio.md#meta-commands)以外的特殊中繼命令：

| 命令 | 引數 | 描述 |
| --- | --- | --- |
| `$continue`, `$cont`, `$c` | 從目前的陳述式開始執行程式。 |
| `$down`, `$d` | 在堆疊追蹤中將目前的框架下移一層。 |
| `$frame` | | 顯示目前的框架 ID。
| `$frame` | 框架 ID | 將目前的框架切換到指定的框架 ID。
| `$load` | 從檔案載入命令並執行，直到完成為止 |
| `$proc` |  | 顯示目前的處理序 ID。 |
| `$proc` | 處理序 ID | 將目前的處理序切換到指定的處理序 ID。 |
| `$procs` | | 列出目前正在進行偵錯的處理序。 |
| `$stepin`, `$step`, `$s` | 逐步執行下一個函式呼叫 (如有可能)。 |
| `$stepout`, `$return`, `$r` | 跳離目前的函式。 |
| `$stepover`, `$until`, `$unt` | 不進入下一個函式呼叫。 |
| `$thread` | | 顯示目前的執行緒 ID。 |
| `$thread` | 執行緒 ID | 將目前的執行緒切換到指定的執行緒 ID。 |
| `$threads` | | 列出目前正在進行偵錯的執行緒。 |
| `$up`, `$u` | | 在堆疊追蹤中將目前的框架上移一層。 |
| `$where`, `$w`, `$bt` | 列出目前執行緒的框架。 |

請注意，標準偵錯工具視窗 (例如 [處理序]、[執行緒] 和 [呼叫堆疊]) 不會與 [互動式偵錯] 視窗同步。 在 [互動式偵錯] 視窗中變更使用中的處理序、執行緒或框架，不會影響其他偵錯工具視窗。 同樣地，在其他偵錯工具視窗變更使用中的處理序、執行緒或框架，也不會影響 [互動式偵錯] 視窗。

[互動式偵錯] 視窗有自己的一組選項，您可以透過 [工具] > [選項] > [Python 工具] > [互動式偵錯視窗] 來存取。 不同於一般 [Python 互動式] 視窗針對各個 Python 環境有不同的執行個體，[互動式偵錯] 視窗只有一個，而且一律使用 Python 解譯器進行處理序偵錯。 請參閱[選項 - 偵錯選項](python-support-options-and-settings-in-visual-studio.md#debugging-options)。

![[偵錯互動式視窗 (Debug Interactive Window)] 選項](media/debugging-interactive-options.png)

<a name="use-the-experimental-debugger"></a>

## <a name="use-the-legacy-debugger"></a>使用舊版偵錯工具

Visual Studio 2017 15.8 版及更新版本使用以 ptvsd 4.1+ 版為基礎的偵錯工具。 這個版本的 ptvsd 與 Python 2.7 及 Python 3.5+ 相容。 如果您使用的是 Python 2.6、3.1 到 3.4 或 IronPython，Visual Studio 會顯示**偵錯工具不支援此 Python 環境**的錯誤：

![使用偵錯工具時，偵錯工具不支援此 Python 環境的錯誤](media/debugging-experimental-incompatible-error.png)

在這些情況下，您必須使用舊版偵錯工具 (即為Visual Studio 2017 15.7 及更舊版本中的預設)。 選取 [工具] > [選項] 功能表命令，瀏覽到 [Python] > [偵錯]，然後選取 [使用舊版偵錯工具] 選項。

若您已在目前環境中安裝舊版 ptvsd (例如較舊的 4.0.x 版，或遠端偵錯所需的 3.x 版)，Visual Studio 可能會顯示錯誤或警告。

當您已安裝 ptvsd 3.x 版時，會顯示**無法載入偵錯工具套件**的錯誤：

![使用偵錯工具時，無法載入偵錯工具套件的錯誤](media/debugging-experimental-version-error.png)

在這種情況下，選取 [使用舊版偵錯工具] 以設定 [使用舊版偵錯工具] 選項，然後重新啟動偵錯工具。

當您已安裝較早的 ptvsd 4.x 版時，會顯示**偵錯工具套件已過時**的警告：

![使用偵錯工具時，偵錯工具套件已過時的警告](media/debugging-experimental-version-warning.png)

> [!Important]
> 雖然您可以選擇忽略某些 ptvsd 版本的警告，但 Visual Studio 可能無法正常運作。

管理您的 ptvsd 安裝：

1. 瀏覽到 [Python 環境] 視窗中的 [套件] 索引標籤。

1. 在搜尋方塊中輸入 "ptvsd"，然後檢查已安裝的 ptvsd 版本：

    ![在 [Python 環境] 視窗中檢查 ptvsd 版本](media/debugging-experimental-check-ptvsd.png)

1. 如果版本低於 4.1.1a9 (隨附於 Visual Studio 的版本)，請選取套件右側的 **X** 以將舊版解除安裝。 Visual Studio 就會使用其隨附的版本。 (您也可以使用 `pip uninstall ptvsd` 從 PowerShell 解除安裝。)

1. 或者，您可以將 ptvsd 套件更新為其最新版本。 在搜尋方塊中輸入 `ptvsd --upgrade -pre`，然後選取 [執行命令: pip install ptvsd --upgrade -pre]。 (您也可以從 PowerShell 使用相同的命令。)

    ![在 [Python 環境] 視窗中提供升級命令](media/debugging-experimental-upgrade-ptvsd.png)

## <a name="see-also"></a>另請參閱

如需 Visual Studio 偵錯工具的詳細資訊，請參閱 [Visual Studio 偵錯](../debugger/debugger-feature-tour.md)。
