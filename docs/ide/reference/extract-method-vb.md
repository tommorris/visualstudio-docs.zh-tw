---
title: "使用 Visual Basic 來擷取方法 | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.extractmethod
dev_langs: VB
ms.workload: multiple
ms.openlocfilehash: f9e55a41f9a61626e8fce18cb11da6edc8a8bced
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2018
---
# <a name="extract-a-method-in-visual-basic"></a>使用 Visual Basic 來擷取方法

**功能：**讓您將程式碼片段轉換成它自己的方法。

**時機：**您在某個必須從另一個方法來呼叫的方法中有現有的程式碼片段。  

**原因：**您可以複製/貼上該程式碼，但那樣會造成重複。  較好的解決方案是將該片段重構成它自己的且可由任何其他方法自由呼叫的方法。

**做法：**

1. 醒目標示的擷取的程式碼：

   ![醒目標示的程式碼](media/extractmethod-highlight-vb.png)

1. 接著，執行下列其中一項操作：
   * **鍵盤**
     * 按 **CTRL+R**，再按 **CTRL+M**。  (請注意，根據您所選取的設定檔，鍵盤快速鍵可能會不同)。
     * 按 **Ctrl+.** 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [擷取方法]。
   * **滑鼠**
     * 選取 [編輯] > [重構] > [擷取方法]。
     * 在程式碼上按一下滑鼠右鍵，然後選取 [重構] > [擷取] > [擷取方法]。
     * 在程式碼上按一下滑鼠右鍵，選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [擷取方法]。

   系統將會立即建立方法。  從這裡，您現在即可輸入新名稱來為方法重新命名。

   > [!TIP]
   > 您也可以使用出現在 IDE 右上角 [重新命名] 方塊中的核取方塊，以更新註解和其他字串來使用這個新名稱，以及在儲存前先[預覽變更](../../ide/preview-changes.md)。

   ![重新命名方法](media/extractmethod-rename-vb.png)

1. 對變更感到滿意時，按一下 [套用] 按鈕或按 **Enter**，便會認可變更。

## <a name="see-also"></a>另請參閱

[重構](../refactoring-in-visual-studio.md)  
[預覽變更](../../ide/preview-changes.md)