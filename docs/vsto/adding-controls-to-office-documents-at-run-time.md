---
title: "在執行階段將控制項加入至 Office 文件"
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
  - "Office 文件 [Visual Studio 中的 Office 程式開發，Windows Form 控制項"
  - "主控制項 [Visual Studio 中的 Office 程式開發]，加入"
  - "Windows Form 控制項 [Visual Studio 中的 Office 程式開發]，加入"
  - "Office 文件 [Visual Studio 中的 Office 程式開發]，主控制項"
  - "使用者控制項 [Visual Studio 中的 Office 程式開發]，在執行階段加入"
  - "文件 [Visual Studio 中的 Office 程式開發]，Windows Form 控制項"
  - "文件層級自訂 [Visual Studio 中的 Office 程式開發]，主控制項"
  - "文件 [Visual Studio 中的 Office 程式開發]，主控制項"
  - "文件層級自訂 [Visual Studio 中的 Office 程式開發]，Windows Form 控制項"
  - "控制項 [Visual Studio 中的 Office 程式開發]，在執行階段加入"
  - "Helper 方法 [Visual Studio 中的 Office 程式開發]"
ms.assetid: 4f43b3eb-f0ec-44e2-9885-6ede327c6913
caps.latest.revision: 102
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 101
---
# 在執行階段將控制項加入至 Office 文件
  您可以在執行階段將控制項加入 Microsoft Office Word 文件與 Microsoft Office Excel 活頁簿中。 您也可以在執行階段加以移除。 您在執行階段加入或移除的控制項稱為*動態控制項*。  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 本主題說明下列項目：  
  
-   [在執行階段使用控制項集合來管理控制項](#ControlsCollection)。  
  
-   [將主控制項加入文件中](#HostControls)。  
  
-   [將 Windows Form 控制項加入文件中](#WindowsForms)。  
  
 ![視訊的連結](../vsto/media/playvideo.png "視訊的連結")如需相關的影片示範，請參閱[如何：在執行階段將控制項加入文件介面？](http://go.microsoft.com/fwlink/?LinkId=132782)。  
  
##  <a name="ControlsCollection"></a> 在執行階段使用控制項集合來管理控制項。  
 若要在執行階段加入、取得或移除控制項，請使用 <xref:Microsoft.Office.Tools.Excel.ControlCollection> 與 <xref:Microsoft.Office.Tools.Word.ControlCollection> 物件的 Helper 方法。  
  
 您存取這些物件的方式，取決於您所開發的專案類型：  
  
-   在 Excel 的文件層級專案中，請使用 `Sheet1`、`Sheet2` 與 `Sheet3` 類別的 <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> 屬性。 如需這些類別的詳細資訊，請參閱[Worksheet 主項目](../vsto/worksheet-host-item.md)。  
  
-   在 Word 的文件層級專案中，請使用 `ThisDocument` 類別的 <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> 屬性。 如需這個類別的詳細資訊，請參閱[Document 主項目](../vsto/document-host-item.md)。  
  
-   在 Excel 或 Word 的 VSTO 增益集專案中，請使用您在執行階段所產生的 <xref:Microsoft.Office.Tools.Excel.Worksheet> 或 <xref:Microsoft.Office.Tools.Word.Document> 的 Controls 屬性。 如需在執行階段產生這些物件的詳細資訊，請參閱[在 VSTO 增益集的執行階段中擴充 Word 文件和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
### 加入控制項  
 <xref:Microsoft.Office.Tools.Excel.ControlCollection> 與 <xref:Microsoft.Office.Tools.Word.ControlCollection> 類型包括 Helper 方法，其可用來將主控制項和通用 Windows Form 控制項加入文件與工作表中。 每個方法名稱皆具有格式 `Add` *控制項類別*，其中*控制項類別*是您想要加入的控制項類別名稱。 例如，若要將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項加入文件中，請使用 <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddNamedRange%2A> 方法。  
  
 下列程式碼範例在 Excel 的文件層級專案中，將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 加入 `Sheet1` 中。  
  
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelWorkbookDynamicControls/CS/ThisWorkbook.cs#3)]
 [!code-vb[Trin_ExcelWorkbookDynamicControls#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelWorkbookDynamicControls/VB/ThisWorkbook.vb#3)]  
  
### 存取與刪除控制項  
 您可以使用 <xref:Microsoft.Office.Tools.Excel.Worksheet> 或 <xref:Microsoft.Office.Tools.Word.Document> 的 Controls 屬性來逐一查看文件中的所有控制項，包括在設計階段加入的控制項。 您在設計階段加入的控制項也稱為*靜態控制項*。  
  
 您可以透過呼叫控制項的 Delete 方法，或藉由呼叫每個 Controls 集合的 Remove 方法來移除動態控制項。 下列程式碼範例在 Excel 的文件層級專案中使用 <xref:Microsoft.Office.Tools.Excel.ControlCollection.Remove%2A> 方法，將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 從 `Sheet1` 移除。  
  
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelWorkbookDynamicControls/CS/ThisWorkbook.cs#4)]
 [!code-vb[Trin_ExcelWorkbookDynamicControls#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelWorkbookDynamicControls/VB/ThisWorkbook.vb#4)]  
  
 您無法在執行階段移除靜態控制項。 如果您嘗試使用 Delete 或 Remove 方法來移除靜態控制項，就會擲回 <xref:Microsoft.Office.Tools.CannotRemoveControlException>。  
  
> [!NOTE]  
>  在文件的 `Shutdown` 事件處理常式中，請勿以程式設計方式移除控制項。 當 `Shutdown` 事件受到引發時，文件的 UI 項目便無法再使用。 如果您想在文件關閉前移除控制項，請將程式碼加入另一個事件的事件處理常式中，例如 <xref:Microsoft.Office.Tools.Word.Document.BeforeClose> 或 <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> \(針對 Word\)，或是 <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeClose>或 <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeSave> \(針對 Excel\)。  
  
##  <a name="HostControls"></a> 將主控制項加入文件中  
 在您以程式設計方式將主控制項加入文件中時，您必須提供控制項的唯一識別名稱，且必須指定要將控制項加入文件的所在位置。 如需特定的相關指示，請參閱下列主題：  
  
-   [如何：將 ListObject 控制項加入至工作表](../vsto/how-to-add-listobject-controls-to-worksheets.md)  
  
-   [如何：將 NamedRange 控制項加入至工作表](../vsto/how-to-add-namedrange-controls-to-worksheets.md)  
  
-   [如何：將圖表控制項加入至工作表](../vsto/how-to-add-chart-controls-to-worksheets.md)  
  
-   [如何：將內容控制項加入至 Word 文件](../vsto/how-to-add-content-controls-to-word-documents.md)  
  
-   [如何：將書籤控制項加入至 Word 文件](../vsto/how-to-add-bookmark-controls-to-word-documents.md)  
  
 如需主控制項的詳細資訊，請參閱[主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)。  
  
 在文件儲存後關閉時，所有動態建立的主控制項皆會與其事件中斷連接，並失去其資料繫結功能。 您可以將程式碼加入方案中，以便在文件重新開啟時重新建立主控制項。 如需詳細資訊，請參閱[在 Office 文件中保存動態控制項](../vsto/persisting-dynamic-controls-in-office-documents.md)。  
  
> [!NOTE]  
>  未替下列主控制項提供 Helper 方法，原因是這些控制項不能以程式設計方式加入文件中：<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>、<xref:Microsoft.Office.Tools.Word.XMLNode>與 <xref:Microsoft.Office.Tools.Word.XMLNodes>。  
  
##  <a name="WindowsForms"></a> 將 Windows Form 控制項加入文件中  
 在您以程式設計方式將 Windows Form 控制項加入文件中時，您必須提供控制項位置，以及控制項的唯一識別名稱。[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 為每個控制項提供 Helper 方法。 這些方法受到多載，以便讓您為控制項的位置傳遞一定範圍或特定的座標。  
  
 在文件儲存後關閉時，所有動態建立的 Windows Form 控制項會從文件中移除。 您可以將程式碼加入方案中，以便在文件重新開啟時重新建立控制項。 如果您使用 VSTO 增益集來建立動態的 Windows Form 控制項，則控制項的 ActiveX 包裝函式會保留在文件中。 如需詳細資訊，請參閱[在 Office 文件中保存動態控制項](../vsto/persisting-dynamic-controls-in-office-documents.md)。  
  
> [!NOTE]  
>  Windows Form 控制項無法以程式設計方式加入受保護的文件中。 如果您以程式設計方式將 Word 文件或 Excel 工作表取消保護以加入控制項，則您必須撰寫額外的程式碼，以便在文件關閉時移除控制項的 ActiveX 包裝函式。 控制項的 ActiveX 包裝函式不會自動從受保護的文件刪除。  
  
### 加入自訂控制項  
 如果您想要加入 <xref:System.Windows.Forms.Control>，而其不受可用的 Helper 方法支援 \(例如自訂使用者控制項\)，請使用下列方法：  
  
-   針對 Excel，請使用 <xref:Microsoft.Office.Tools.Excel.ControlCollection> 物件的其中一種 <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> 方法 。  
  
-   針對 Word，請使用 <xref:Microsoft.Office.Tools.Word.ControlCollection> 物件的其中一種 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddControl%2A> 方法 。  
  
 若要加入控制項，請將 <xref:System.Windows.Forms.Control>、控制項的位置，以及控制項的唯一識別名稱傳遞至 AddControl 方法。AddControl 方法會傳回物件，其會定義控制項與工作表或文件互動的方式。AddControl 方法會傳回 <xref:Microsoft.Office.Tools.Excel.ControlSite> \(針對 Excel\) 或 <xref:Microsoft.Office.Tools.Word.ControlSite> 物件 \(針對 Word\)。  
  
 下列程式碼範例示範如何使用 <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> 方法，以動態方式將自訂使用者控制項加入文件層級 Excel 專案的工作表中。 在此範例中，使用者控制項名為 `UserControl1`，而 <xref:Microsoft.Office.Interop.Excel.Range> 名為 `range1`。 若要使用此範例，請從專案中的 `Sheet`*n* 類別加以執行。  
  
 [!code-csharp[Trin_VstcoreProgrammingControlsExcel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#2)]
 [!code-vb[Trin_VstcoreProgrammingControlsExcel#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#2)]  
  
### 使用自訂控制項的成員  
 在使用其中一個 AddControl 方法，將控制項加入工作表或文件中後，您現在便有兩個不同的控制項物件：  
  
-   <xref:System.Windows.Forms.Control> 代表自訂控制項。  
  
-   ControlSite、OLEObject 或 OLEControl 物件，代表加入工作表或文件中後的控制項。  
  
 這些控制項之間共用許多屬性和方法。 請務必透過適當的控制項存取這些成員：  
  
-   若要存取僅屬於自訂控制項的成員，請使用 <xref:System.Windows.Forms.Control>。  
  
-   若要存取控制項所共用的成員，請使用 ControlSite、OLEObject 或 OLEControl 物件。  
  
 如果您從 <xref:System.Windows.Forms.Control> 存取共用的成員，其可能會在沒有警告或通知的情況下失敗，或產生無效的結果。 除非所需的方法或屬性無法使用，否則一律使用 ControlSite、OLEObject 或 OLEControl 物件的方法或屬性；只有在方法或屬性無法使用時參考 <xref:System.Windows.Forms.Control>。  
  
 例如，<xref:Microsoft.Office.Tools.Excel.ControlSite> 類別與 <xref:System.Windows.Forms.Control> 類別皆具有 Top 屬性。 若要取得或設定控制項的頂端和文件頂端之間的距離，請使用 <xref:Microsoft.Office.Tools.Excel.ControlSite> 的 <xref:Microsoft.Office.Tools.Excel.ControlSite.Top%2A> 屬性，而非 <xref:System.Windows.Forms.Control> 的 <xref:System.Windows.Forms.Control.Top%2A> 屬性。  
  
 [!code-csharp[Trin_VstcoreProgrammingControlsExcel#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#3)]
 [!code-vb[Trin_VstcoreProgrammingControlsExcel#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#3)]  
  
## 請參閱  
 [Office 文件上的控制項](../vsto/controls-on-office-documents.md)   
 [在 Office 文件中保存動態控制項](../vsto/persisting-dynamic-controls-in-office-documents.md)   
 [如何：將 ListObject 控制項加入至工作表](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [如何：將 NamedRange 控制項加入至工作表](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [如何：將圖表控制項加入至工作表](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [如何：將內容控制項加入至 Word 文件](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [如何：將書籤控制項加入至 Word 文件](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Office 文件上的 Windows Forms 控制項概觀](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [如何：將 Windows Form 控制項加入至 Office 文件](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)  
  
  