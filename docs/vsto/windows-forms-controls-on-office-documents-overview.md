---
title: "Office 文件上的 Windows Forms 控制項概觀"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "舊資料顯示錯誤 [Visual Studio 中的 Office 程式開發]"
  - "Windows Forms 控制項 [Visual Studio 中的 Office 程式開發]，Word"
  - "Windows Forms 控制項 [Visual Studio 中的 Office 程式開發]，加入"
  - "Windows Forms 控制項 [Visual Studio 中的 Office 程式開發]，排列"
  - "資料 [Visual Studio 中的 Office 程式開發]，舊資料顯示錯誤"
  - "使用者控制項 [Visual Studio 中的 Office 程式開發]，Windows Forms 控制項"
  - "Windows Forms 控制項 [Visual Studio 中的 Office 程式開發]"
  - "Windows Forms 控制項 [Visual Studio 中的 Office 程式開發]，移除"
  - "應用程式開發 [Visual Studio 中的 Office 程式開發]，Windows Forms 控制項"
  - "控制項 [Visual Studio 中的 Office 程式開發]，Windows Forms 控制項"
  - "Office [Visual Studio 中的 Office 程式開發]，Windows Forms 控制項"
  - "Office 文件 [Visual Studio 中的 Office 程式開發]，控制項"
  - "文件 [Visual Studio 中的 Office 程式開發]，Windows Forms 控制項"
  - "文件層級自訂 [Visual Studio 中的 Office 程式開發]，Windows Forms 控制項"
  - "Windows Forms 控制項 [Visual Studio 中的 Office 程式開發]，關於 Windows Forms 控制項"
  - "Office 應用程式 [Visual Studio 中的 Office 程式開發]，Windows Forms"
ms.assetid: a959506b-5038-49c2-831a-d63c6d6b797d
caps.latest.revision: 76
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 75
---
# Office 文件上的 Windows Forms 控制項概觀
  Windows Forms 控制項是使用者可以互動，輸入或操作資料的物件。 在 Microsoft Office Excel 和 Microsoft Office Word 的文件層級專案中，您可以在設計階段將 Windows Forms 控制項加入文件或活頁簿，或是用程式設計方式在執行階段中加入這些控制項。 您可以用程式設計方式，在執行階段於 Excel 或 Word 的 VSTO 增益集將這些控制項加入任何開啟的文件或活頁簿。  
  
 如需詳細資訊，請參閱[如何：將 Windows Form 控制項加入至 Office 文件](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)。  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## 使用 Windows Forms 控制項  
 您可以將 Windows Forms 控制項加入文件和可自訂的使用者介面 \(UI\) 項目，包括執行窗格、自訂工作窗格和 Windows Forms。 Windows Forms 控制項在文件上的行為通常與在這些其他 UI 項目上相同，但確實存在一些差異。 如需詳細資訊，請參閱 [Office 文件上的 Windows Form 控制項限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)。  
  
 決定是否要將 Windows Forms 控制項加入文件或某個其他 UI 項目，取決於許多因素。 在設計您的方案 UI 時，請考慮如下表所述來使用 Windows Forms 控制項。  
  
 在文件上。  
 -   當您想要一直顯示控制項時。  
  
-   當您想讓使用者直接在文件輸入資料時，例如在已鎖定編輯介面的表單式文件中。  
  
-   當您想控制項與文件中的資料對齊顯示時。 例如，如果您要將按鈕加入清單物件的每個資料列，您會想讓它們與每個清單項目對齊。  
  
 在執行窗格或自訂工作窗格上。  
 -   當您想要提供內容資訊給使用者時。  
  
-   當您只想要文件中出現結果，而不出現查詢控制項和資料時。  
  
-   當您想要確定控制項不會隨著文件列印出來時。  
  
-   當您想要確定控制項不會影響文件檢視時。  
  
 在 Windows Forms 上。  
 -   當您想要控制 UI 的大小時。  
  
-   當您想要防止使用者隱藏或刪除控制項時。  
  
-   當您想要從使用者取得輸入，並防止使用者在收到輸入之前在文件中做任何事時。  
  
## 以程式設計方式加入 Windows Forms 控制項  
 您可以在執行階段將 Windows Forms 控制項加入 Word 文件和 Excel 工作表。[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 提供 Helper 方法，來加入最常見的 Windows Forms 控制項。 這些 Helper 方法可讓您快速將控制項加入 Office 文件，並存取這些控制項結合後的 Windows Forms 控制項功能和 Office 相關功能。  
  
 如需詳細資訊，請參閱[在執行階段將控制項加入至 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
## 在文件層級專案中使用 Windows Forms 控制項  
 在文件上使用 Windows Forms 控制項，某些層面對於文件層級專案而言是唯一的，這可讓您使用 Visual Studio 設計工具來設計文件的 UI。  
  
### 建立自訂使用者控制項  
 您可以將使用者控制項加入您的專案，並再將它加入工具箱。 接著可以直接將使用者控制項拖曳到文件，就像您將 Windows Forms 控制項加入文件的方式一樣。 建立使用者控制項時，有一些事項要謹記在心：  
  
-   請勿建立 **sealed** 使用者控制項。 當您將控制項拖曳至文件時，Visual Studio 會產生衍生自使用者控制項的包裝函式類別，以便擴充它並支援其在文件上的使用。 如果使用者控制項為 **sealed**，則 Visual Studio 無法產生包裝函式類別。  
  
-   使用者控制項的 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 屬性必須設定為 **true**。 在 Office 專案中建立的使用者控制項，此屬性預設會設定為 **true**，但屬於外部專案一部分的使用者控制項，此屬性則可能不會設定為 **true**。  
  
-   將使用者控制項加入文件之後，請勿重新命名或從專案刪除 <xref:System.Windows.Forms.UserControl> 類別。 如果您需要變更使用者控制項的名稱，必須先將它從文件中刪除，然後在變更名稱之後將它重新加入。  
  
### 在設計階段排列控制項  
 如果您在設計階段將多個控制項加入 Word 和 Excel 文件，可以在 Visual Studio 中使用 **Microsoft Office Word** 和 **Microsoft Office Excel** 工具列，快速地設定所有選取控制項的對齊方式。 只有當文件或工作表在設計工具中開啟時，才能使用這些工具列。  
  
 當您在設計工具中選取多個控制項時，可以使用這些工具列中的下列按鈕來排列控制項：  
  
-   **對齊主控項的左緣**  
  
-   **對齊主控項的水平中央**  
  
-   **對齊主控項的右緣**  
  
-   **對齊主控項的上緣**  
  
-   **對齊主控項的垂直中間**  
  
-   **靠下對齊**  
  
-   **將水平間距設成相等**  
  
-   **將垂直間距設為相等**  
  
> [!NOTE]  
>  在 Word 專案中，只有選取的控制項與文字未對齊時才會啟用這些按鈕。 根據預設，在設計階段加入文件的控制項會與文字對齊。  
  
### 防止載入時舊資料出現在 Excel 活頁簿中  
 當您在設計階段將 Windows Forms 控制項加入文件或工作表時，如果使用者關閉文件，控制項仍然會留在文件中。 在設計階段加入的控制項也稱為*靜態控制項*。  
  
 開啟包含靜態控制項的 Excel 活頁簿時，活頁簿會在 ActiveX 控制項中顯示控制項的點陣圖，直到自訂程式碼執行並載入實際的控制項。 每次您儲存活頁簿，Excel 會建立此點陣圖並將它儲存在活頁簿中。 點陣圖顯示上次儲存活頁簿時，控制項的樣子，包括控制項當時顯示的任何資料。 如需有關包含 Windows Forms 控制項和點陣圖的 ActiveX 控制項詳細資訊，請參閱 [Office 文件上的 Windows Form 控制項限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)。  
  
 在某些情況下，程式碼不會載入，並且只會顯示點陣圖，例如當使用者在設計模式中開啟活頁簿。 此外，如果使用者在沒有安裝 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 的電腦上開啟活頁簿，自訂無法執行以載入控制項，因此只能看到控制項的點陣圖。 您在儲存活頁簿並將它傳送給另一位使用者之前，應該務必從活頁簿上的控制項移除個人資訊，以確保您的個人資訊不會意外洩漏。  
  
### 讓控制項大小符合 Excel 工作表上的儲存格大小  
 您可以設定在父儲存格的大小變更時自動調整控制項的大小。 如需詳細資訊，請參閱[如何：在工作表儲存格中調整控制項的大小](../vsto/how-to-resize-controls-within-worksheet-cells.md)。  
  
### 加入所有工作表共用的元件  
 您可以將想要在所有工作表之間共用的元件，例如 <xref:System.Data.DataSet>，加入活頁簿設計工具，而不是加入工作表。 元件會出現在元件匣中。  
  
### 在 Excel 工作表上內嵌控制項的公式  
 在 Excel 中選取控制項時，您會在 \[資料編輯列\] 看到 **\=EMBED\("WinForms.Control.Host",""\)** 。 這個文字是必要的，不應該刪除。  
  
### 在 Word 文件上的控制項配置樣式  
 當您使用 Visual Studio 設計工具將控制項加入文件層級專案中的 Word 文件時，控制項會加入與文字對齊。 若要變更控制項的配置樣式，請以滑鼠右鍵按一下控制項，再按一下 \[控制項格式\]。 在 \[物件格式\] 對話方塊的 \[配置\] 頁面選取文繞圖樣式。  
  
 當您在執行階段將控制項加入 Word 文件時，可以使用 <xref:Microsoft.Office.Tools.Word.ControlCollection> 類別的不同 `Add`\<*控制類別*\> 方法的多載，指定新控制項的配置樣式：  
  
-   若加入控制項並與文字對齊，請使用可接受指定控制項位置之 <xref:Microsoft.Office.Interop.Word.Range> 的多載。  
  
-   若要將控制項加入為浮動的圖形，請使用可接受控制項左邊和頂端座標的多載。  
  
 如需詳細資訊，請參閱[在執行階段將控制項加入至 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
 如果您在 Visual Studio 設計工具中開啟 Word 範本，可能看不到範本上的非內嵌控制項，因為 Visual Studio 會在 \[一般\] 檢視中開啟範本。 若要檢視控制項，請將檢視變更為 \[整頁模式\]。  
  
### 主要文件主體之外的控制項  
 在頁首或頁尾內，或在子文件內，不支援 Windows Forms 控制項。  
  
### 在設計階段加入元件  
 有些控制項或元件不會出現在文件，而會顯示在元件匣。 Visual Studio 針對每個文件視窗提供元件匣。 只有當元件存在於文件上時，畫面上才會出現元件匣。  
  
## 請參閱  
 [Office 文件上的控制項](../vsto/controls-on-office-documents.md)   
 [在執行階段將控制項加入至 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [執行窗格概觀](../vsto/actions-pane-overview.md)   
 [Windows Form 控制項](http://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a)   
 [Office 文件上的 Windows Form 控制項限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)   
 [如何：將 Windows Form 控制項加入至 Office 文件](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [如何：在工作表儲存格中調整控制項的大小](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [如何：列印時隱藏工作表的控制項](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [逐步解說：使用 CheckBox 控制項來變更工作表格式](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [逐步解說：使用 CheckBox 控制項來變更文件格式](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)   
 [逐步解說：使用按鈕在工作表的文字方塊中顯示文字](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [逐步解說：使用按鈕在文件的文字方塊中顯示文字](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)   
 [Office 文件上的 Windows Form 控制項限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)   
 [逐步解說：使用選項按鈕更新文件中的圖表](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)   
 [逐步解說：使用選項按鈕更新工作表中的圖表](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
  
  