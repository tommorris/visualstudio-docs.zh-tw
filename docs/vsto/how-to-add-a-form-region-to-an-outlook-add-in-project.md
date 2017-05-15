---
title: "如何：在 Outlook 增益集專案中加入表單區域"
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
  - "VSTO.NewFormRegionWizard.Page1"
  - "VSTO.NewFormRegionWizard.Page3"
  - "VSTO.NewFormRegionWizard.Page2"
  - "VSTO.NewFormRegionWizard.Page0"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "表單區域 [Visual Studio 中的 Office 程式開發]，加入"
ms.assetid: 49fa3d1e-1b8a-48be-95fb-35c59c4711f6
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# 如何：在 Outlook 增益集專案中加入表單區域
  使用 \[新的 Outlook 表單區域精靈\] 建立表單區域，以擴充標準或自訂的 Microsoft Office Outlook 表單。 您可以建立新的表單區域並且在 Visual Studio 中設計使用者介面，或者匯入在 Outlook 中設計的表單區域並加入 Visual Basic 或 C\# 程式碼。  
  
 如果在其他 Outlook 專案中有您使用的 Outlook 表單區域，則可使用 \[加入現有項目\] 對話方塊在目前的 Outlook VSTO 增益集專案中重複使用該表單區域。 如需詳細資訊，請參閱[建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
### 將新的表單區域加入 Outlook 專案  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中開啟或建立 Outlook VSTO 增益集專案。 如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
2.  在方案總管中，選取 Outlook VSTO 增益集專案節點。  
  
3.  在 \[專案\] 功能表中，按一下 \[加入新項目\]。  
  
4.  選取 \[加入新項目\] 對話方塊中的 \[Outlook 表單區域\]。  
  
5.  在 \[名稱\] 方塊中輸入表單區域的名稱，然後按一下 \[加入\]。  
  
     \[新的 Outlook 表單區域精靈\] 隨即啟動。  
  
6.  在 \[選取您希望如何建立此表單區域\] 頁面中，選取要藉由拖曳 Managed 控制項至視覺化設計工具來設計表單區域，或匯入之前在 Outlook 中設計的表單區域。  
  
    > [!NOTE]  
    >  如果您選擇匯入之前在 Outlook 中設計的表單區域，則必須指定 Outlook 表單儲存區 \(.ofs\) 檔j案的位置。 您無法將 Managed 控制項加入在 Outlook 中設計的表單區域；只能在現有 UI 後面加入程式碼。 如需詳細資訊，請參閱[建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)。  
  
7.  在 \[選取要建立的表單區域類型\] 頁面上，檢視表單區域類型並選取其中一個，然後按 \[下一步\]。 如需表單區域類型的詳細資訊，請參閱[建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)。  
  
8.  在 \[提供描述文字和選取顯示設定\] 頁面的 \[名稱\] 方塊中，輸入表單區域的名稱。 針對取代型和全部取代型表單區域類型，另外還提供 \[標題\] 和 \[描述\] 方塊。  
  
     如需部署表單區域時，名稱、標題和描述在 Outlook 中所出現位置的詳細資訊，請參閱[建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)。  
  
9. 選取一個或多個要用來顯示表單區域的顯示模式。  
  
     所有表單區域類型都可以顯示在偵測器的撰寫模式 \(用於建立項目\) 和讀取模式 \(用於檢視項目\) 中。 相鄰型、取代型和全部取代型表單區域類型亦可出現在 \[讀取窗格\] 中。  
  
10. 按 \[**下一步**\]。  
  
11. 在 \[識別將顯示此表單區域的訊息類別\] 頁面上，選取標準的 Outlook 訊息類別，或輸入一個或多個自訂訊息類別的名稱，然後按一下 \[完成\]。 如需詳細資訊，請參閱[讓表單區域與 Outlook 訊息類別產生關聯](../vsto/associating-a-form-region-with-an-outlook-message-class.md)。  
  
## 請參閱  
 [在執行階段存取表單區域](../vsto/accessing-a-form-region-at-run-time.md)   
 [Outlook 方案](../vsto/outlook-solutions.md)   
 [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)   
 [建立 Outlook 表單區域的方針](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [逐步解說：設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [逐步解說：匯入在 Outlook 中設計的表單區域](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Outlook 表單區域中的自訂動作](../vsto/custom-actions-in-outlook-form-regions.md)  
  
  