---
title: "自訂工作窗格"
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
  - "增益集 [Visual Studio 中的 Office 程式開發], 自訂工作窗格"
  - "應用程式層級增益集 [Visual Studio 中的 Office 程式開發], 自訂工作窗格"
  - "自訂工作窗格 [Visual Studio 中的 Office 程式開發]"
  - "自訂工作窗格 [Visual Studio 中的 Office 程式開發], 關於自訂工作窗格"
  - "自訂工作窗格 [Visual Studio 中的 Office 程式開發], 建立"
  - "自訂工作窗格 [Visual Studio 中的 Office 程式開發], 多個應用程式視窗"
  - "含有自訂工作窗格的多個應用程式視窗 [Visual Studio 中的 Office 程式開發]"
  - "Visual Studio 中的 Office 程式開發, 工作窗格"
  - "工作窗格 [Visual Studio 中的 Office 程式開發]"
  - "工作窗格 [Visual Studio 中的 Office 程式開發], 關於自訂工作窗格"
  - "工作窗格 [Visual Studio 中的 Office 程式開發], 建立"
  - "工作窗格 [Visual Studio 中的 Office 程式開發] 多個應用程式視窗"
  - "使用者介面面板 [Visual Studio 中的 Office 程式開發]"
  - "使用者介面 [Visual Studio 中的 Office 程式開發], 自訂工作窗格"
ms.assetid: 9a415109-5333-433e-95c6-3d59ce9c4d02
caps.latest.revision: 52
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 51
---
# 自訂工作窗格
  工作窗格是通常停駐在 Microsoft Office 應用程式視窗一側的使用者介面面板。  自訂工作窗格為您提供建立個人專屬工作窗格的方法，也為使用者提供了熟悉的介面，供他們用來存取您方案的功能。  例如，介面中可以包含控制項，而這些控制項則會執行程式碼來修改文件或顯示資料來源中的資料。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  自訂工作窗格與執行窗格不同。  而執行窗格則屬於 Microsoft Office Word 和 Microsoft Office Excel 之文件層級自訂的一部分。  如需詳細資訊，請參閱[執行窗格概觀](../vsto/actions-pane-overview.md)。  
  
## 自訂工作窗格的優點  
 自訂工作窗格可以讓您將功能整合成熟悉的使用者介面。  您可以利用 Visual Studio 工具快速建立自訂工作窗格。  
  
### 熟悉的使用者介面  
 Microsoft Office System 應用程式的使用者已經十分熟悉工作窗格的用法，例如 Word 中的 \[樣式與格式設定\] 工作窗格。  自訂工作窗格的行為與 Microsoft Office system 的其他工作窗格相同。  使用者可以將自訂工作窗格固定至應用程式視窗的不同側，或是他們可以將自訂工作窗格拖曳到視窗中的任何位置。  您可以建立同時顯示多個自訂工作窗格的 VSTO 增益集，而且使用者可以個別控制每個工作窗格。  
  
### Windows Form 支援  
 您以 Visual Studio 中的 Office 開發工具建立的自訂工作窗格使用者介面是以 Windows Forms 控制項為基礎。  您可以使用熟悉的 \[Windows Form 設計工具\] 設計自訂工作窗格的使用者介面。  也可以使用 Windows Form 中的資料繫結支援，將資料來源繫結至工作窗格上的控制項。  
  
## 建立自訂工作窗格  
 您可以利用下列兩個步驟建立基本的自訂工作窗格：  
  
1.  將 Windows Form 控制項加入 <xref:System.Windows.Forms.UserControl> 物件，以建立自訂工作窗格的使用者介面。  
  
2.  將使用者控制項傳遞給 VSTO 增益集中的 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> 物件，將自訂工作窗格具現化。  這個集合會傳回可以用來修改工作窗格外觀以及回應使用者事件的新 <xref:Microsoft.Office.Tools.CustomTaskPane> 物件。  
  
 如需詳細資訊，請參閱[如何：在應用程式中加入自訂工作窗格](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)。  
  
### 建立使用者介面  
 所有以 Visual Studio 中的 Office 開發工具建立的自訂工作窗格都會包含 <xref:System.Windows.Forms.UserControl> 物件。  這個使用者控制項提供了自訂工作窗格的使用者介面。  您可以在設計階段或執行階段建立此使用者控制項。  如果您在設計階段建立此使用者控制項，即可使用 \[Windows Form 設計工具\] 建構工作窗格的使用者介面。  
  
### 具現化自訂工作窗格  
 建立包含自訂工作窗格使用者介面的使用者控制項之後，您必須具現化 <xref:Microsoft.Office.Tools.CustomTaskPane>。  若要這樣做，請呼叫其中一個 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> 方法，以便將使用者控制項傳遞至 VSTO 增益集中的 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection>。  此集合會公開為 `ThisAddIn` 類別的 `CustomTaskPanes` 欄位。  下列程式碼範例預定由 `ThisAddIn` 類別執行。  
  
 [!code-csharp[Trin_TaskPaneBasic#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/CS/ThisAddIn.cs#2)]
 [!code-vb[Trin_TaskPaneBasic#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/VB/ThisAddIn.vb#2)]  
  
 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> 方法會傳回新的 <xref:Microsoft.Office.Tools.CustomTaskPane> 物件。  您可以使用這個物件修改工作窗格的外觀，並回應使用者事件。  
  
### 在多個視窗中控制工作窗格  
 自訂工作窗格會與文件框架視窗產生關聯，而該框架視窗會對使用者呈現文件或項目的檢視。  顯示相關聯的視窗時才能顯示工作窗格。  
  
 若要判斷顯示自訂工作窗格的視窗，則當您建立工作窗格時，請使用適當的 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> 方法多載：  
  
-   若要使工作窗格與現用視窗產生關聯，請使用 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> 方法。  
  
-   若要使工作窗格與指定之視窗所裝載的文件產生關聯，請使用 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> 方法。  
  
 當有多個視窗開啟時，有些 Office 應用程式對於何時建立或顯示工作窗格需要獲得明確的指示。  因此一定要考慮在何處具現化程式碼中的自訂工作窗格，以確保工作窗格會在應用程式中顯示適當的文件或項目。  如需詳細資訊，請參閱[管理應用程式視窗中的自訂工作窗格](#Managing)。  
  
## 從工作窗格存取應用程式  
 如果您要從使用者控制項自動化應用程式，可以使用程式碼中的 `Globals.ThisAddIn.Application` 直接存取物件模型。  靜態 `Globals` 類別會提供對 `ThisAddIn` 物件的存取。  這個物件的 `Application` 欄位為應用程式之物件模型的進入點。  
  
 如需 `ThisAddIn` 物件之 `Application` 欄位的詳細資訊，請參閱[VSTO 增益集程式設計](../vsto/programming-vsto-add-ins.md)。  如需示範如何從自訂工作窗格自動化應用程式的逐步解說，請參閱[逐步解說：運用自訂工作窗格自動化應用程式](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)。  如需 `Globals` 類別的詳細資訊，請參閱[全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)。  
  
## 管理工作窗格的使用者介面  
 在您建立工作窗格之後，可以使用 <xref:Microsoft.Office.Tools.CustomTaskPane> 物件的屬性和事件來控制工作窗格的使用者介面，以及在使用者變更工作窗格時予以回應。  
  
### 顯示自訂工作窗格  
 根據預設，工作窗格為隱藏狀態。  若要顯示工作窗格，您必須將 <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> 設定為 **true**。  
  
 使用者隨時可以按一下工作窗格角落的 \[關閉\] 按鈕 \(X\)，以關閉工作窗格。  但是，無法透過任何預設方法再次開啟自訂工作窗格。  如果使用者關閉了自訂工作窗格，除非您提供顯示工作窗格的方法，否則使用者將無法再次檢視該自訂工作窗格。  
  
 如果在 VSTO 增益集中建立自訂工作窗格，則應同時建立 UI 項目，例如使用者可以按一下來顯示或隱藏自訂工作窗格的按鈕。  如果您在支援自訂功能區的 Microsoft Office 應用程式中建立自訂工作窗格，可以將控制項群組加入功能區，且該功能區的按鈕可顯示或隱藏自訂工作窗格。  如需示範如何執行這項操作的逐步解說，請參閱[逐步解說：使用功能區按鈕同步處理自訂工作窗格](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)。  
  
 如果您在不支援自訂功能區的 Microsoft Office 應用程式中建立自訂工作窗格，則可加入用來顯示或隱藏自訂工作窗格的 <xref:Microsoft.Office.Core.CommandBarButton>。  
  
### 修改工作窗格的外觀  
 您可以使用 <xref:Microsoft.Office.Tools.CustomTaskPane> 物件的屬性，控制自訂工作窗格的大小和位置。  您還可以使用包含在自訂工作窗格內之 <xref:System.Windows.Forms.UserControl> 物件的屬性，對自訂工作窗格的外觀進行其他多項變更。  例如，您可以使用使用者控制項的 <xref:System.Windows.Forms.Control.BackgroundImage%2A> 屬性，指定自訂工作窗格的背景影像。  
  
 下表列出可以使用 <xref:Microsoft.Office.Tools.CustomTaskPane> 屬性進行的自訂工作窗格變更。  
  
|工作|屬性|  
|--------|--------|  
|變更工作窗格的大小|<xref:Microsoft.Office.Tools.CustomTaskPane.Height%2A><br /><br /> <xref:Microsoft.Office.Tools.CustomTaskPane.Width%2A>|  
|變更工作窗格的位置|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPosition%2A>|  
|隱藏或顯示工作窗格|<xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A>|  
|避免使用者變更工作窗格的位置|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionRestrict%2A>|  
  
### 自訂工作窗格事件的程式設計  
 您可能希望 VSTO 增益集能夠在使用者修改自訂工作窗格時做出回應。  例如，如果使用者將窗格從垂直方向改成水平方向，您可能會想要重新置放控制項。  
  
 下表列出您可以處理的事件，以回應使用者對自訂工作窗格所進行的變更。  
  
|工作|事件|  
|--------|--------|  
|在使用者變更工作窗格的位置時回應。|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionChanged>|  
|在使用者隱藏或顯示工作窗格時回應。|<xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged>|  
  
## 清除工作窗格所使用的資源  
 在您建立自訂工作窗格之後，只要 VSTO 增益集還在執行中，<xref:Microsoft.Office.Tools.CustomTaskPane> 物件就會留在記憶體中。  甚至在使用者按一下工作窗格角落的 \[關閉\] 按鈕 \(X\) 後，此物件仍會留在記憶體中。  
  
 若要在 VSTO 增益集仍執行時清除工作窗格使用的資源，請使用 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> 或 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> 方法。  這些方法會從 `CustomTaskPanes` 集合中移除指定的 <xref:Microsoft.Office.Tools.CustomTaskPane> 物件，並且呼叫該物件的 <xref:Microsoft.Office.Tools.CustomTaskPane.Dispose%2A> 方法。  
  
 當 VSTO 增益集卸載時，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會自動清除自訂工作窗格使用的資源。  請不要在專案的 `ThisAddIn_Shutdown` 事件處理常式中呼叫 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> 或 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> 方法。  因為 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會在呼叫 `ThisAddIn_Shutdown` 之前先清除 <xref:Microsoft.Office.Tools.CustomTaskPane> 物件使用的資源，所以這些方法會擲回 <xref:System.ObjectDisposedException>。  如需 `ThisAddIn_Shutdown` 的詳細資訊，請參閱 [Office 專案中的事件](../vsto/events-in-office-projects.md)。  
  
##  <a name="Managing"></a> 管理多個應用程式視窗中的自訂工作窗格  
 在使用多重視窗的應用程式中建立自訂工作窗格以顯示文件和其他項目時，需要採取額外步驟以確保工作窗格能夠在使用者需要時顯示。  
  
 所有應用程式中的自訂工作窗格會與文件框架視窗產生關聯，而該框架視窗會對使用者呈現文件或項目的檢視。  顯示相關聯的視窗時才能顯示工作窗格。  但是，並非所有應用程式都以相同方式來使用文件框架視窗。  
  
 下列應用程式群組具有不同的開發需求：  
  
-   [Outlook](#Outlook)  
  
-   [Word、InfoPath 和 PowerPoint](#WordAndInfoPath)  
  
 ![視訊的連結](../vsto/media/playvideo.png "視訊的連結") 如需相關的影片示範，請參閱[如何：管理 Word VSTO 增益集中的工作窗格？](http://go.microsoft.com/fwlink/?LinkId=136781)。  
  
##  <a name="Outlook"></a> Outlook  
 當您建立 Outlook 的自訂工作窗格時，自訂工作窗格將與特定 \[總管\] 或 \[檢查\] 視窗相關聯。  \[總管\] 視窗可顯示資料夾內容，而 \[檢查\] 視窗則會顯示電子郵件訊息或工作之類的項目。  
  
 如果要在多個 \[總管\] 或 \[檢查\] 視窗中顯示自訂工作窗格，您需要在 \[總管\] 或 \[檢查\] 視窗開啟時，建立自訂工作窗格的新執行個體。  若要這麼做，請在建立 \[總管\] 或 \[檢查\] 視窗時處理引發的事件，然後在事件處理常式中建立工作窗格。  您也可以處理 \[總管\] 與 \[檢查\] 事件，依據可見的視窗來隱藏或顯示工作窗格。  
  
 若要將工作窗格與特定 \[總管\] 或 \[檢查\] 產生關聯，請使用 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> 方法來建立工作窗格，並將 <xref:Microsoft.Office.Interop.Outlook.Explorer> 或 <xref:Microsoft.Office.Interop.Outlook.Inspector> 物件傳遞給 *window* 參數。  如需建立自訂工作窗格的詳細資訊，請參閱[自訂工作窗格概觀](../vsto/custom-task-panes.md)。  
  
 如需示範如何為每個開啟的電子郵件訊息建立工作窗格的逐步解說，請參閱[逐步解說：在 Outlook 中的電子郵件訊息顯示自訂工作窗格](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)。  
  
### Outlook 事件  
 若要監視 \[總管\] 視窗的狀態，可以處理下列與 \[總管\] 相關的事件：  
  
-   <xref:Microsoft.Office.Interop.Outlook.ExplorersEvents_Event.NewExplorer>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Activate>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Deactivate>  
  
 若要監視 \[檢查\] 視窗的狀態，可以處理下列與 \[檢查\] 相關的事件：  
  
-   <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>  
  
-   <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Activate>  
  
-   <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>  
  
-   <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Deactivate>  
  
### 避免在 Outlook 中顯示自訂工作窗格的多個執行個體  
 若要避免 Outlook 視窗顯示自訂工作窗格的多個執行個體，請在關閉每個視窗時，從 `ThisAddIn` 類別的 `CustomTaskPanes` 集合中明確移除自訂工作窗格。  請在視窗關閉時所引發的事件 \(例如 <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> 或 <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>\) 中呼叫 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> 方法。  
  
 如果您沒有明確移除自訂工作窗格，Outlook 視窗可能會顯示自訂工作窗格的多個執行個體。  Outlook 有時會回收視窗，而回收的視窗會保留對其附加之任何自訂工作窗格的參考。  
  
##  <a name="WordAndInfoPath"></a> Word、InfoPath 和 PowerPoint  
 Word、InfoPath 和 PowerPoint 會顯示不同文件框架視窗中的每份文件。  當您建立這些應用程式的自訂工作窗格時，自訂工作窗格只會與特定文件相關聯。  如果使用者開啟不同的文件，則自訂工作窗格會等到先前的文件重新顯示之後才會取消隱藏。  
  
 如果要在多份文件中顯示自訂工作窗格，可以在使用者建立新文件或開啟現有文件時，建立自訂工作窗格的新執行個體。  若要這麼做，請在建立或開啟文件時處理引發的事件，然後在事件處理常式中建立工作窗格。  您也可以處理文件事件，依據可見的文件來隱藏或顯示工作窗格。  
  
 若要使工作窗格與特定文件視窗產生關聯，請使用 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> 方法來建立工作窗格和傳遞 <xref:Microsoft.Office.Interop.Word.Window> \(適用於 Word\)，<xref:Microsoft.Office.Interop.InfoPath.WindowObject> \(適用於 InfoPath\)，或 <xref:Microsoft.Office.Interop.PowerPoint.DocumentWindow> \(適用於 PowerPoint\) 到 *window* 參數。  
  
### Word 事件  
 若要在 Word 中監視文件視窗的狀態，您可以處理下列事件：  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeClose>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.NewDocument>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowActivate>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowDeactivate>  
  
### InfoPath 事件  
 若要在 InfoPath 中監視文件視窗的狀態，您可以處理下列事件：  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.NewXDocument>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowActivate>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowDeactivate>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentBeforeClose>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentOpen>  
  
### PowerPoint 事件  
 若要在 PowerPoint 中監視文件視窗的狀態，您可以處理下列事件：  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterNewPresentation>  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterPresentationOpen>  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.NewPresentation>  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationOpen>  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.WindowActivate>  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.WindowDeactivate>  
  
## 請參閱  
 [如何：在應用程式中加入自訂工作窗格](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [逐步解說：運用自訂工作窗格自動化應用程式](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)   
 [逐步解說：使用功能區按鈕同步處理自訂工作窗格](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)   
 [逐步解說：在 Outlook 中的電子郵件訊息顯示自訂工作窗格](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)  
  
  