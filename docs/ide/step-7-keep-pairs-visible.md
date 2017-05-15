---
title: "步驟 7：讓配對保持可見 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42e1d08c-7b2e-4efd-9f47-85d6206afe35
caps.latest.revision: 21
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: eecbfe02fbb0850e7954be1baf7aa3d607601b80
ms.lasthandoff: 02/22/2017

---
# <a name="step-7-keep-pairs-visible"></a>步驟 7：讓配對保持可見
只要玩家僅選擇不相符的圖示配對，遊戲都可以運作良好。 但是，請考慮當玩家選擇相符的配對時會發生的情況。 遊戲不用藉由啟動計時器使圖示消失 (使用 `Start()` 方法)，而是應該本身進行重設，如此它就不會再使用 `firstClicked` 和 `secondClicked` 參考變數來追蹤任何標籤，但不需要重設已選擇之兩個標籤的色彩。  
  
### <a name="to-keep-pairs-visible"></a>若要讓配對保持可見  
  
1.  將下列 `if` 陳述式加入至 `label_Click()` 事件處理常式方法，位置靠近您啟動計時器之陳述式正上方的程式碼那一端。 將程式碼加入至程式時，請仔細觀察該程式碼。 請考慮程式碼的運作方式。  
  
     [!code-cs[VbExpressTutorial4Step7#9](../ide/codesnippet/CSharp/step-7-keep-pairs-visible_1.cs)]
     [!code-vb[VbExpressTutorial4Step7#9](../ide/codesnippet/VisualBasic/step-7-keep-pairs-visible_1.vb)]  
  
     您剛才加入的 `if` 陳述式的第一行會檢查玩家所選擇的第一個標籤中的圖示是否與第二個標籤中的圖示相同。 如果圖示相同，程式即執行在 C# 中大括號之間或 Visual Basic 中 `if` 陳述式內的三個陳述式。 前兩個陳述式會重設 `firstClicked` 和 `secondClicked` 參考變數，如此他們便不會再追蹤任何的標籤  (您可以辨識來自計時器的 Tick 事件處理常式中的那兩個陳述式)。第三個陳述式是 `return` 陳述式，該陳述式會告訴程式略過方法中其餘的陳述式，而不要執行它們。  
  
     如果在 Visual C# 中設計程式，您可能已注意到有些程式碼會使用單一等號 (`=`)，而其他陳述式則使用兩個等號 (`==`)。 請考慮為何某些地方使用 `=`，而其他地方使用 `==`。  
  
     這是一個顯示差異的好範例。 請仔細觀察 `if` 陳述式中括號之間的程式碼。  
  
    ```vb#  
    firstClicked.Text = secondClicked.Text  
    ```  
  
    ```c#  
    firstClicked.Text == secondClicked.Text  
    ```  
  
     然後，再仔細查看 `if` 陳述式之後程式碼區塊中的第一個陳述式。  
  
    ```vb#  
    firstClicked = Nothing  
    ```  
  
    ```c#  
    firstClicked = null;  
    ```  
  
     這兩個陳述式中的第一個會檢查兩個圖示是否相同。 因為有兩個值在進行比較，所以 Visual C# 程式會使用 `==` 相等運算子。 第二個陳述式會實際變更值 (稱為「指派」)，方法是將 `firstClicked` 參考變數設為等於 `null` 以進行重設。 這就是它為何改用 `=` 指派運算子的緣故。 Visual C# 會使用 `=` 來設定值，而使用 `==` 比較它們。 Visual Basic 則是使用 `=` 來進行變數指派和比較。  
  
2.  儲存並執行程式，然後開始在表單中選擇圖示。 如果您選擇不相符的配對，計時器的 Tick 事件觸發器和這兩個圖示都會消失。 如果選擇相符的配對，則會執行新的 `if` 陳述式，而 return 陳述式會導致方法略過用於啟動計時器的程式碼，如此圖示才能保持可見，如下列圖片所示。  
  
     ![您在本教學課程中建立的遊戲](../ide/media/express_finishedgame.png "Express_FinishedGame")  
含有可見圖示配對的配對遊戲  
  
### <a name="to-continue-or-review"></a>繼續或檢視  
  
-   若要移至下一個教學課程步驟，請參閱[步驟 8：新增方法以驗證玩家是否贏了](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)。  
  
-   若要返回上一個教學課程步驟，請參閱[步驟 6：新增計時器](../ide/step-6-add-a-timer.md)。