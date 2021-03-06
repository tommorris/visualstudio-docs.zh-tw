---
title: 在 Visual Studio 中儲存測試失敗的負載測試記錄
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, logging
ms.assetid: 08a7fe98-a7f7-4b8d-94a3-ec82b65a2aaf
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: d6196a940ff1aba0c072c2b81a96371a5ad700d1
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2018
ms.locfileid: "39381449"
---
# <a name="how-to-specify-if-test-failures-are-saved-to-test-logs-using-the-load-test-editor"></a>如何：使用負載測試編輯器指定測試失敗是否會儲存至測試記錄

使用 [新增負載測試精靈] 建立負載測試之後，您就可以使用 [負載測試編輯器]，將負載測試屬性變更為符合您的測試需求和目標。 請參閱[逐步解說：建立和執行負載測試](../test/walkthrough-create-and-run-a-load-test.md)。 您可以變更 [測試失敗時儲存記錄] 屬性，指定當負載測試中的測試失敗時，是否要儲存測試記錄。

> [!NOTE]
> 如需回合設定屬性及其描述的完整清單，請參閱[負載測試回合設定屬性](../test/load-test-run-settings-properties.md)。


## <a name="to-specify-if-the-test-log-is-saved-when-a-test-fails-in-a-scenario"></a>若要指定當情節中的測試失敗時是否儲存測試記錄檔

1.  開啟負載測試。

     [負載測試編輯器] 隨即出現。 負載測試樹狀隨即顯示。

2.  在負載測試樹狀目錄的 [回合設定] 資料夾中，選擇您要指定其測試反覆項目數上限的回合設定節點。

3.  在 [檢視] 功能表上，選取 [屬性視窗]。

     回合設定分類和屬性會顯示在 [屬性] 視窗中。

4.  在 [測試失敗時儲存記錄檔] 屬性中，選取 [True] 或 [False] 以指定情節中的測試失敗時，是否要儲存測試記錄。

     屬性變更完成之後，選擇 [檔案] 功能表上的 [儲存]。

     您可以使用 [負載測試分析器] 的 [資料表] 檢視來檢視儲存在記錄檔中的資料。 如需詳細資訊，請參閱[在資料表檢視中分析負載測試結果和錯誤](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)。

## <a name="see-also"></a>另請參閱

- [編輯負載測試情節](../test/edit-load-test-scenarios.md)
- [逐步解說：建立和執行負載測試](../test/walkthrough-create-and-run-a-load-test.md)
- [如何：設定收集完整詳細資料以便啟用虛擬使用者活動圖](../test/how-to-configure-load-tests-to-collect-full-details.md)
- [如何：指定儲存測試記錄的頻率](../test/how-to-specify-how-frequently-test-logs-are-saved.md)