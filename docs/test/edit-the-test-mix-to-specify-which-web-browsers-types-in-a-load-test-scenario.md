---
title: Visual Studio 中用於負載測試的瀏覽器測試混合 | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, web browser types
- load tests, scenarios
- load tests, adding browsers
- load tests, removing browsers
ms.assetid: 47f981d9-3038-45cc-a486-82b9daf9a9a1
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: bae150fcd528166121f49a7018be0a71d7cbf37f
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2018
---
# <a name="edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario"></a>編輯測試混合以指定負載測試情節中的網頁瀏覽器類型

「瀏覽器混合」提供在負載測試情節中更真實的模擬負載方法。 負載是使用 Web 瀏覽器的異質混合，而非只是以單一的 Web 瀏覽器來產生。 您會建立與應用程式搭配使用之 Web 瀏覽器的極為近似混合。

 瀏覽器混合會指定在負載測試情節中，一位虛擬使用者執行特定 Web 瀏覽器類型的可能性。 當您建立負載測試時，可能想要模擬多個 Web 瀏覽器所產生的負載。 當您從提供的 Web 瀏覽器集合，將 Web 瀏覽器類型加入至混合時，所選 Web 瀏覽器的一組關聯標頭就會加入至由 Web 效能測試所送出的每個 HTTP 要求。

 瀏覽器混合的運作方式與其他混合選項相同。 Web 瀏覽器類型會根據瀏覽器混合，隨機地與虛擬使用者相關聯。 該使用者的測試則會根據您在混合中指定的可能性，而在特定的 Web 瀏覽器上執行。

 在指定瀏覽器混合之後，您依然可以在瀏覽器混合中加入或移除 Web 瀏覽器類型。 您也可以使用混合控制來變更瀏覽器混合的散發。 混合控制讓您能夠輕鬆調整情節中瀏覽器的分佈。

## <a name="adding-new-browsers-to-a-scenario"></a>將新瀏覽器加入至情節

### <a name="to-add-new-browsers-to-a-scenario"></a>將新瀏覽器加入至情節

1.  在指定情節的瀏覽器混合時，選擇 [新增]。

     新的瀏覽器項目就會加入至方格。

    > [!NOTE]
    > 若要顯示 [編輯瀏覽器混合] 對話方塊，請以滑鼠右鍵按一下現有情節，然後選擇 [編輯瀏覽器混合]。

2.  在 [瀏覽器類型] 欄中，選擇新項目的箭號並選擇需要的瀏覽器類型。

3.  (選擇性) 調整混合控制項以指定測試分佈。

4.  完成新增瀏覽器後，選擇 [確定]。

##  <a name="EditingTestMixSpecifyBrowserRemovingBrowserTypes"></a> 從情節移除瀏覽器

### <a name="to-remove-browsers-from-a-scenario"></a>從情節移除瀏覽器

1.  開啟負載測試。

2.  以滑鼠右鍵按一下您要移除瀏覽器的情節，然後選擇 [編輯瀏覽器混合]。

     [編輯瀏覽器混合] 對話方塊隨即顯示。

3.  在方格中選取瀏覽器，然後選擇 [移除]。

4.  (選擇性) 調整混合控制項以指定測試分佈。

5.  完成移除瀏覽器後，選擇 [確定]。

## <a name="about-the-mix-control"></a>關於混合控制項

 混合控制可讓您在負載測試情節中，調整分佈在測試、瀏覽器類型或網路類型中的負載百分比。 您可以藉由移動滑桿調整百分比值。 調整瀏覽器類型混合可指定在負載測試情節中，一位虛擬使用者執行特定瀏覽器類型的可能性。

 當您移動滑桿時，所有可用項目的百分比值就會變更。 如果您有兩個以上的項目，您所新增或移除的數量會在其他項目間平均分佈。 您無法覆寫這個行為。 如果您針對特定項目選取鎖定資料行中的核取方塊，就會鎖定該項目所指定的百分比值。 之後，當您移動滑桿時，您所新增或移除的數量僅會套用到其餘未鎖定的所有項目。

 [均分] 按鈕用於平均配置所有項目間的百分比值。 例如，如果您有三個項目，選擇 [均分] 會將百分比值設定為 34、33 與 33。

> [!WARNING]
> [均分] 按鈕會覆寫所有已鎖定的項目。

 您也可以不使用滑桿，直接將百分比值輸入 **%** 資料行。 如果您直接輸入百分比值，其他項目就不會自動調整。

> [!NOTE]
> 當總數相加沒有達到 100%，或輸入 **%** 資料行的百分比值有小數點時，滑桿便會停用。

 當您手動輸入百分比值時，應確認所有項目的總和為 100%。 當您儲存混合時，如果總和不是 100%，系統會提示您接受該百分比值，或返回予以調整。 如果您選擇接受此設定，則會按比例分配至 100%。  例如，如果您有兩個項目，而且手動設定為 80% 和 40%。第一個項目會被設定為 66.67% (80 除以 120)，而第二個項目則會被設定為 33.33% (40 除以 120)。

## <a name="see-also"></a>另請參閱

- [編輯負載測試情節](../test/edit-load-test-scenarios.md)