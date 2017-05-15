---
title: "建立 Outlook 表單區域"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MICROSOFT.OFFICE.TOOLS.OUTLOOK.FORMREGION"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "表單區域 [Visual Studio 中的 Office 程式開發]"
  - "表單區域 [Visual Studio 中的 Office 程式開發], 建立"
  - "Outlook [Visual Studio 中的 Office 程式開發], 表單區域"
ms.assetid: a8005641-cc8b-4e07-8dca-294327cdc8d4
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# 建立 Outlook 表單區域
  您可以使用表單區域自訂 Microsoft Office Outlook 表單。  Visual Studio 提供進階的工具，可讓您更方便地設計、開發和偵錯表單區域。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 本主題提供下列資訊：  
  
-   [使用表單區域的優點](#Enhance)  
  
-   [將 Outlook 表單區域加入您的專案](#Adding)  
  
-   [使用表單區域設計工具](#UsingFormRegionDesigner)  
  
-   [使用 Outlook 中設計的表單區域](#UsingFormRegionDesignedOutlook)  
  
-   [將自訂程式碼加入表單區域](#AddingCustomCode)  
  
-   [建置專案](#Building)  
  
-   [偵錯表單區域](#Debugging)  
  
-   [部署表單區域](#Deploying)  
  
##  <a name="Enhance"></a> 使用表單區域的優點  
 表單區域提供許多超越傳統 Outlook 表單開發的增強功能：  
  
-   自訂任何標準表單的預設頁面。  
  
-   在任何標準表單中加入額外的頁面，最多 12 頁。  
  
-   置換或增強任何標準表單。  
  
-   在 \[讀取窗格\] 和 \[檢查\] 中顯示自訂 UI。  
  
 如需詳細資訊，請參閱[自訂表單頁面與表單區域](HV10038632)。  
  
##  <a name="Adding"></a> 將 Outlook 表單區域加入您的專案  
 您可以使用 \[新的 Outlook 表單區域精靈\] 設計新的表單區域，或是匯入已在 Outlook 中設計的表單區域。  此外，如果您在另一個 Outlook VSTO 增益集專案中使用表單區域，則可重複使用現有的表單區域。  
  
###  <a name="CreatingFormRegion"></a> 使用精靈建立新的表單區域  
 若要建立表單區域，請將 \[Outlook 表單區域\] 項目加入 Outlook VSTO 增益集專案中。  如此會啟動 \[新的 Outlook 表單區域精靈\]。  
  
 使用此精靈指出您要設計新的表單區域，或匯入已在 Outlook 中設計的表單區域。  如需設計新表單區域的詳細資訊，請參閱[使用表單區域設計工具](#UsingFormRegionDesigner)。  如需使用在 Outlook 中設計之表單區域的詳細資訊，請參閱[匯入在 Outlook 中設計的表單區域](#UsingFormRegionDesignedOutlook)。  
  
 使用此精靈指定要建立的表單區域類型。  下表將描述每一個表單區域類型。  
  
|區域類型|描述|  
|----------|--------|  
|獨立|加入表單區域，做為 Outlook 表單中的新頁面。|  
|相鄰|附加表單區域至 Outlook 表單預設頁面的下方。|  
|Replacement|加入表單區域，做為取代 Outlook 表單預設頁面的新頁面。|  
|全部取代|以表單區域取代整個 Outlook 表單。|  
  
 您也可以使用此精靈指定顯示條件以及選取要擴充的表單類型。  如需詳細資訊，請參閱[如何：在 Outlook 增益集專案中加入表單區域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)。  
  
 您在精靈中所做的選擇會影響其他精靈頁面中提供的選項。  例如，如果您在 \[建立新的 Outlook 表單區域\] 頁面中選取 \[相鄰\] 或 \[獨立\]，則 \[提供描述文字和選取顯示設定\] 頁面中不會提供 \[標題\] 和 \[描述\] 欄位。  這是因為 Outlook 顯示相鄰或獨立表單區域時不會使用這些欄位。  
  
#### 表單區域檔案  
 當您完成 \[新的 Outlook 表單區域精靈\] 時，Visual Studio 會自動將下列檔案加入您的專案：  
  
-   表單區域程式碼檔案。  這個檔案的名稱是您在 \[加入新項目\] 對話方塊中為 \[Outlook 表單區域\] 指定的名稱。  請將程式碼加入這個檔案以處理表單區域事件。  
  
-   表單區域設計工具程式碼檔案。  這個檔案包含表單區域設計工具所產生的程式碼，且不應直接編輯。  
  
-   Outlook 表單儲存區 \(.ofs\) 檔案。  
  
    > [!NOTE]  
    >  這個檔案只會在您匯入已在 Outlook 中設計的表單區域時加入專案。  
  
#### 表單區域 Factory 類別  
 表單區域程式碼檔案包含一個部分類別，用來實作 <xref:Microsoft.Office.Tools.Outlook.IFormRegionFactory> 介面。  也就是表單區域 Factory 類別。  表單區域 Factory 類別會負責建立表單區域的新執行個體。  
  
 您只要展開 \[表單區域 Factory\] 區域就可以找到這個類別。  
  
 \[新的 Outlook 表單區域精靈\] 會將屬性加入這個類別，用來指定表單區域的內部名稱，以及指定會顯示表單區域的訊息類別。  您可以在將檔案加入專案之後，手動修改這些屬性。  
  
 大部分表單區域 Factory 類別是在表單區域設計工具檔案中實作。  不過，`FormRegionInitializing` 事件處理常式會在表單區域程式碼檔案中公開。  您可以使用這個事件處理常式指定 Outlook 是否應顯示表單區域。  如需詳細資訊，請參閱[處理表單區域事件](#HandlingFormRegionEvents)。  
  
###  <a name="AddingExistingFormRegion"></a> 將現有的表單區域加入您的專案  
 如果在其他 Outlook 專案中有您使用的 Outlook 表單區域，則可使用 \[加入現有項目\] 對話方塊在目前的 Outlook VSTO 增益集專案中重複使用該表單區域。  
  
 現有的表單區域必須擁有程式碼檔案 \(.vb 或 .cs\)；您無法使用 \[加入現有項目\] 對話方塊加入 Outlook 表單儲存區 \(.ofs\) 檔案。  不過，您可以藉由匯入 Outlook 表單儲存區檔案建立新的表單區域。  如需詳細資訊，請參閱[如何：在 Outlook 增益集專案中加入表單區域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)。  
  
##  <a name="UsingFormRegionDesigner"></a> 使用 \[表單區域設計工具\]  
 \[表單區域設計工具\] 可協助您設計表單區域的配置和外觀。  您可以將 Managed 控制項拖曳至設計工具的介面，按兩下控制項開啟事件處理常式，然後設定 \[屬性\] 視窗中的屬性。  
  
> [!NOTE]  
>  您可以在 \[屬性\] 視窗中的 \[資訊清單\] 節點下，找到影響表單區域在 Outlook 中顯示方式的屬性。  
  
 \[表單區域設計工具\] 只有在您於 \[新的 Outlook 表單區域精靈\] 中，選取 \[選取您希望如何建立此表單區域\] 頁面中的 \[設計新的表單區域\] 時才會提供。  
  
 開啟 \[表單區域設計工具\] 的方式有三種：  
  
-   在 \[方案總管\] 中，按兩下表單區域程式碼檔案。  
  
-   在 \[方案總管\] 中，以滑鼠右鍵按一下表單區域程式碼檔案，然後按一下 \[設計工具檢視\]。  
  
-   在 \[方案總管\] 中選取表單區域程式碼檔案，然後按一下 \[檢視\] 功能表上的 \[設計工具\]。  
  
 \[表單區域設計工具\] 只支援 Managed 控制項。  因此您無法加入原生 Outlook 控制項。  
  
##  <a name="UsingFormRegionDesignedOutlook"></a> 匯入 Outlook 中設計的表單區域  
 當您在 Outlook 中設計時，可將原生 Outlook 控制項加入表單區域。  原生 Outlook 控制項可讓您在設計階段時繫結至 Outlook 資料。  不過，之後您就無法使用 \[表單區域設計工具\] 加入 Managed 控制項，或是變更表單區域的設計。  
  
 您可以使用 \[新的 Outlook 表單區域精靈\]，將表單區域匯入 Outlook VSTO 增益集專案中。  在 \[選取您希望如何建立此表單區域\] 頁面上選取 \[匯入 Outlook 表單儲存區 \(.ofs\) 檔案\]。  然後您就可以瀏覽至 Outlook 表單儲存區 \(.ofs\) 檔案的位置。  \(Outlook 會將表單區域儲存為 .ofs 檔案。\)  
  
 \[新的 Outlook 表單區域精靈\] 會將 .ofs 檔複製到專案目錄中，並且將控制項參考加入 \[表單區域設計工具\] 檔案。  然後您就可以在表單區域程式碼檔案中處理控制項事件。  
  
 若要在 Visual Basic 專案中處理事件，請從 \[程式碼編輯器\] 頂端的方法名稱清單選取事件。  
  
 若要在 C\# 專案中處理事件，請在 <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> 方法中訂閱控制項事件。  如需詳細資訊，請參閱[如何：訂閱及取消訂閱事件 &#40;C&#35; 程式設計手冊&#41;](http://msdn.microsoft.com/library/6319f39f-282c-4173-8a62-6c4657cf51cd)。  
  
 您可以在表單區域 Factory 類別的 `InitializeManifest` 方法中變更表單區域屬性。  
  
> [!NOTE]  
>  若要匯入表單區域，您必須在目標 Outlook 版本與開發電腦上所安裝版本相同的專案中進行。  例如，如果您已安裝 Outlook 2010，則只能在使用 \[Outlook 2010 增益集\] 專案範本建立的專案中匯入表單區域。  
  
### 更新匯入的表單區域設計  
 您可以加入、移除或變更表單區域上的控制項。  在執行這些動作前，請先備份您加入表單區域程式碼檔案的任何程式碼。  接著，開啟 Outlook 中的 .ofs 檔案，修改表單區域，然後儲存變更。  您可以使用 \[新的 Outlook 表單區域精靈\] 匯入已修改的 .ofs 檔案。  然後您可以將程式碼貼入新的表單區域程式碼檔案。  
  
##  <a name="AddingCustomCode"></a> 將自訂程式碼加入表單區域  
 <xref:Microsoft.Office.Tools.Outlook> 命名空間可讓您存取代表表單區域的類別、顯示表單區域的 Outlook 項目，以及其他實用的項目。  \[Outlook 表單區域\] 項目會自動將參考加入專案的這個組件，並且在表單區域程式碼檔案的頂端插入適當的 **using** 或 **Imports** 陳述式。  
  
 您可以使用 Microsoft.Office.Interop.Outlook 命名空間中的類別、方法和屬性來完成大部分 Outlook 程式設計工作。  如需 Outlook 物件模型的詳細資訊，請參閱 [Outlook 物件模型概觀](../vsto/outlook-object-model-overview.md)。  如需使用 Outlook 物件模型的一般工作範例，請參閱[Outlook 方案](../vsto/outlook-solutions.md)。  
  
###  <a name="HandlingFormRegionEvents"></a> 處理表單區域事件  
 \[Outlook 表單區域\] 項目會自動將下列三個事件處理常式加入表單區域程式碼檔案。  
  
|事件|描述|  
|--------|--------|  
|FormRegionInitializing|在表單區域初始化之前發生。  您可以檢查這個事件處理常式中的條件，以決定 Outlook 是否應顯示表單區域。  如需詳細資訊，請參閱[如何：防止 Outlook 顯示表單區域](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)。|  
|FormRegionShowing|發生於建立表單區域的執行個體之後，但在表單區域顯示之前。|  
|FormRegionClosed|發生於關閉表單區域之前。|  
  
##  <a name="Building"></a> 建置專案  
 當您建置包含表單區域的 Outlook VSTO 增益集專案時，Visual Studio 會在登錄中加入以下資訊：  
  
-   與一個或多個表單區域關聯之每個訊息類別的索引鍵。  
  
-   每個表單區域的項目，以及代表 Outlook VSTO 增益集名稱的關聯值。  
  
 Outlook 會使用這項資訊來載入表單區域。  
  
##  <a name="Debugging"></a> 偵錯表單區域  
 您可以對包含表單區域的 Outlook VSTO 增益集進行偵錯，就如同您對其他 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 專案進行偵錯一般。  當您啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 偵錯工具時，Visual Studio 會自動啟動 Outlook。  
  
 若要檢視表單區域，您必須開啟適當的 Outlook 項目。  例如，如果郵件項目底部附加了相鄰表單區域，則開啟郵件項目。  
  
##  <a name="Deploying"></a> 部署表單區域  
 表單區域會自動隨相關聯的 Outlook VSTO 增益集部署。  因此，您不需要執行任何特殊工作來部署表單區域。  如需部署 VSTO 增益集的詳細資訊，請參閱[部署 Office 方案](../vsto/deploying-an-office-solution.md)。  
  
## 相關主題  
  
|標題|描述|  
|--------|--------|  
|[建立 Outlook 表單區域的方針](../vsto/guidelines-for-creating-outlook-form-regions.md)|提供資訊來協助您最佳化表單區域及避免發生可能的問題。|  
|[如何：在 Outlook 增益集專案中加入表單區域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)|示範如何使用 \[新的 Outlook 表單區域精靈\] 建立表單區域，以擴充標準或自訂的 Microsoft Office Outlook 表單。|  
|[讓表單區域與 Outlook 訊息類別產生關聯](../vsto/associating-a-form-region-with-an-outlook-message-class.md)|說明如何藉由將表單區域和每個 Microsoft Office Outlook 項目的訊息類別產生關聯，指定要顯示表單區域的 Microsoft Office Outlook 項目。|  
|[逐步解說：設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)|示範如何設計自訂表單區域，該表單區域會在連絡人項目的 \[檢查\] 視窗中顯示為新頁面。|  
|[逐步解說：匯入在 Outlook 中設計的表單區域](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)|示範如何在 Microsoft Office Outlook 中設計表單區域，然後使用 \[新的 Outlook 表單區域精靈\] 將表單區域匯入至 Outlook VSTO 增益集專案。|  
|[在執行階段存取表單區域](../vsto/accessing-a-form-region-at-run-time.md)|描述如何撰寫程式碼以顯示、隱藏或修改表單區域上的控制項，以及如何使用 `Globals` 類別讓使用者從您專案的其他區域執行程式碼。|  
|[如何：防止 Outlook 顯示表單區域](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)|示範如何防止 Microsoft Office Outlook 針對特定項目顯示表單區域。|  
|示範如何存取顯示表單區域的 Outlook 項目。|  
|[Outlook 表單區域中的自訂動作](../vsto/custom-actions-in-outlook-form-regions.md)|描述如何讓使用者回應 Outlook 項目。|  
  
  