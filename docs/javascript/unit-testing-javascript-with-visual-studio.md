---
title: Node.js 的單元測試
description: Visual Studio 支援使用適用於 Visual Studio 的 Node.js 工具進行單元測試
ms.custom: ''
ms.date: 06/06/2018
ms.technology: vs-nodejs
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: bc2a839583f62f3efab18fdb55274ec559d5e6cf
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924788"
---
# <a name="unit-testing-in-nodejs"></a>Node.js 的單元測試

適用於 Visual Studio 的 Node.js 工具可讓您使用一些較熱門的 JavaScript 架構撰寫和執行單元測試，而不需要切換到命令提示字元。

支援的架構包括：
* Mocha ([mochajs.org](http://mochajs.org/))
* Jasmine ([Jasmine.github.io](https://jasmine.github.io/))
* Tape ([github.com/substack/tape](https://github.com/substack/tape))
* 匯出執行器 (此架構是適用於 Visual Studio 的 Node.js 工具所特定)

> [!WARNING]
> Tape 的問題目前會導致 Tape 測試無法執行。 如果合併了 [PR #361](https://github.com/substack/tape/pull/361)，應該就能解決問題。

如果不支援您最愛的架構，請參閱[新增單元測試架構的支援](#addingFramework)，以取得新增支援的資訊。 

## <a name="write-unit-tests"></a>撰寫單元測試

將單元測試新增至您的專案之前，請確定您打算使用的架構已安裝在本機專案中。 使用 [npm 套件安裝視窗](npm-package-management.md#npmInstallWindow)可以輕鬆地完成此動作。

將單元測試新增至專案的慣用方法是在專案中建立 *tests* 資料夾，並在專案屬性中將其設定為測試根目錄。 您還必須選取要使用的測試架構。

![設定測試根目錄和測試架構](../javascript/media/unit-test-project-properties.png)

您可以使用 [新增項目] 對話方塊，將簡單的空白測試新增至您的專案。 相同專案中同時支援 JavaScript 和 TypeScript。

![新增單元測試](../javascript/media/unit-test-add-new-item.png)

如果是 Mocha 單元測試，請使用下列程式碼：

```javascript
var assert = require('assert');

describe('Test Suite 1', function() {
    it('Test 1', function() {
        assert.ok(true, "This shouldn't fail");
    })

    it('Test 2', function() {
        assert.ok(1 === 1, "This shouldn't fail");
        assert.ok(false, "This should fail");
    })
})
```

如果您尚未在專案屬性中設定單元測試選項，則必須確定 [屬性] 視窗中的 [測試架構] 屬性已針對您的單元測試檔案設定為正確的測試架構。 這是由單元測試檔案範本自動完成。

![測試架構](../javascript/media/UnitTestsFrameworkMocha.png)

> [!Note]
> 單元測試選項優先於個別檔案的設定。

開啟 [測試總管] (選擇 [測試] > [Windows] > [測試總管]) 之後，Visual Studio 會探索並顯示測試。 如果一開始未顯示測試，則重建專案以重新整理清單。

![測試總管](../javascript/media/UnitTestsDiscoveryMocha.png)

> [!NOTE]
> 請勿在 *tsconfig.json* 中使用 `outdir` 或 `outfile` 選項，因為 [測試總管] 無法在 TypeScript 檔案中尋找您的單元測試。

## <a name="run-tests"></a>執行測試

您可以在 Visual Studio 2017 中執行測試，或從命令列執行測試。

### <a name="run-tests-in-visual-studio-2017"></a>在 Visual Studio 2017 中執行測試

您可以按一下 [測試總管] 中的 [全部執行] 連結來執行測試。 或者，您可以選取一或多個測試或群組，按一下滑鼠右鍵，然後從捷徑功能表中選取 [執行選取的測試] 來執行測試。 測試會在背景中執行，而 [測試總管] 會自動更新並顯示結果。 此外，您也可以選取 [偵錯選取的測試]，對選取的測試進行偵錯。

> [!Warning]
> 使用 Node 8 以上版本對單元測試進行偵錯目前僅適用於 JavaScript 測試檔案，TypeScript 測試檔案將無法叫用中斷點。 因應措施是使用 `debugger` 關鍵字。

> [!NOTE]
> 我們目前不支援分析測試或程式碼涵蓋範圍。

### <a name="run-tests-from-the-command-line"></a>從命令列執行測試

您可以使用下列命令，從 Visual Studio 2017 的[開發人員命令提示字元](/dotnet/framework/tools/developer-command-prompt-for-vs)執行測試：

```
vstest.console.exe <path to project file>\NodejsConsoleApp23.njsproj /TestAdapterPath:<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter
```

這個命令會顯示與下列類似的輸出：

```
Microsoft (R) Test Execution Command Line Tool Version 15.5.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
Processing: NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js
  Creating TestCase:NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js::Test Suite 1 Test 1::mocha
  Creating TestCase:NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js::Test Suite 1 Test 2::mocha
Processing finished for framework of Mocha
Passed   Test Suite 1 Test 1
Standard Output Messages:
 Using default Mocha settings
 1..2
 ok 1 Test Suite 1 Test 1

Failed   Test Suite 1 Test 2
Standard Output Messages:
 not ok 1 Test Suite 1 Test 2
   AssertionError [ERR_ASSERTION]: This should fail
       at Context.<anonymous> (NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js:10:16)

Total tests: 2. Passed: 1. Failed: 1. Skipped: 0.
Test Run Failed.
Test execution time: 1.5731 Seconds
```

> [!NOTE]
> 如果您收到錯誤，指出找不到 *vstest.console.exe*，請確定您已開啟開發人員命令提示字元，而不是一般的命令提示字元。 

## <a name="addingFramework"></a>新增單元測試架構的支援

您可以使用 JavaScript 實作 探索和執行邏輯，以新增其他測試架構的支援。 您可以使用測試架構的名稱新增資料夾來完成此動作：

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks`

此資料夾必須包含具有相同名稱的 JavaScript 檔案，該檔案會匯出下列 2 個函式：

* `find_tests`
* `run_tests`

如需 `find_tests` 和 `run_tests` 實作的良好範例，請參閱 Mocha 單元測試架構在下列內容的實作：

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks\mocha\mocha.js`

探索可用的測試架構會在 Visual Studio 啟動時發生。 如果在 Visual Studio 執行時新增架構，請重新啟動 Visual Studio 來偵測此架構。 不過，當您對實作進行變更時，不需要重新啟動。