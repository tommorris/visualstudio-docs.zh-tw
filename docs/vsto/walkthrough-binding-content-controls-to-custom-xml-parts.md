---
title: "逐步解說：將內容控制項繫結至自訂 XML 組件"
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
  - "內容控制項 [Visual Studio 中的 Office 程式開發], 資料繫結"
  - "自訂 XML 組件, 繫結至內容控制項"
  - "資料繫結 [Visual Studio 中的 Office 程式開發], 內容控制項"
  - "DatePickerContentControl, 繫結至自訂 XML 組件"
  - "DropDownListContentControl, 將項目繫結至自訂 XML 組件"
  - "PlainTextContentControl, 繫結至自訂 XML 組件"
ms.assetid: 10d67769-6157-4703-a10c-d33e988f9095
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# 逐步解說：將內容控制項繫結至自訂 XML 組件
  本逐步解說示範如何將 Word 之文件層級自訂中的內容控制項繫結至文件中所儲存的 XML 資料。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Word 可讓您將 XML 資料 \(名為*「自訂 XML 組件」*\(custom XML part\) 儲存至文件。  將內容控制項繫結至自訂 XML 組件中的項目，即可控制這項資料的顯示。  本逐步解說中的範例文件會顯示自訂 XML 組件中所儲存的員工資訊。  開啟文件時，內容控制項會顯示 XML 項目的值。  您對內容控制項中文字進行的任何變更都會儲存在自訂 XML 組件中。  
  
 這個逐步解說將說明下列工作：  
  
-   在設計階段，將內容控制項新增至文件層級專案中的 Word 文件。  
  
-   建立 XML 資料檔，以及定義項目以繫結至內容控制項的 XML 結構描述。  
  
-   在設計階段，將 XML 結構描述附加至文件。  
  
-   在執行階段，將 XML 檔案的內容新增至文件中的自訂 XML 組件。  
  
-   將內容控制項繫結至自訂 XML 組件中的項目。  
  
-   將 <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> 繫結至 XML 結構描述中所定義的一組值。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word。  
  
## 建立新的 Word 文件專案  
 建立將在逐步解說中使用的 Word 文件。  
  
#### 建立新的 Word 文件專案  
  
1.  建立名稱為 EmployeeControls 的 Word 文件專案。  建立方案的新文件。  如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會在設計工具中開啟新的 Word 文件，並將 EmployeeControls 專案新增至 \[方案總管\]。  
  
## 將內容控制項新增至文件  
 建立包含三種不同類型之內容控制項的資料表，使用者可以使用這些內容控制項來檢視或編輯員工相關資訊。  
  
#### 將內容控制項新增至文件  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 設計工具所裝載的 Word 文件中，選擇功能區上的 \[插入\] 索引標籤。  
  
2.  在 \[資料表\] 群組中，選擇 \[資料表\]，然後插入具有 2 個資料行和 3 個資料列的資料表。  
  
3.  在第一個資料行中輸入文字，讓它類似下面資料行：  
  
    ||  
    |-|  
    |員工名稱|  
    |雇用日期|  
    |標題|  
  
4.  在資料表的第二個資料行中，選擇第一個資料列 \(\[員工名稱\] 旁邊\)。  
  
5.  在功能區上，選擇 \[開發人員\] 索引標籤。  
  
    > [!NOTE]  
    >  如果未顯示 \[開發人員\] 索引標籤，您必須先使其顯示。  如需詳細資訊，請參閱[如何：在功能區顯示開發人員索引標籤](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)。  
  
6.  在 \[控制項\] 群組中，選擇 \[文字\] 按鈕 ![PlainTextContentControl](../vsto/media/plaintextcontrol.png "PlainTextContentControl") 以將 <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> 新增至第一個儲存格。  
  
7.  在資料表的第二個資料行中，選擇第二個資料列 \(\[雇用日期\] 旁邊\)。  
  
8.  在 \[控制項\] 群組中，選擇 \[日期選擇器\] 按鈕 ![DatePickerContentControl](../vsto/media/datepicker.png "DatePickerContentControl") 以將 <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> 新增至第二個儲存格。  
  
9. 在資料表的第二個資料行中，選擇第三個資料列 \(\[職稱\] 旁邊\)。  
  
10. 在 \[控制項\] 群組中，選擇 \[下拉式清單\] 按鈕 ![DropDownListContentControl](../vsto/media/dropdownlist.png "DropDownListContentControl") 以將 <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> 新增至最後一個儲存格。  
  
 這是此專案的整個使用者介面。  如果您立即執行專案，則可以在第一個資料列中輸入文字，並在第二個資料列選取日期。  下一個步驟是將您想要顯示的資料附加至 XML 檔案中的文件。  
  
## 建立 XML 資料檔  
 通常，您會從外部來源 \(例如檔案或資料庫\) 取得要儲存在自訂 XML 組件中的 XML 資料。  在本逐步解說中，您會建立包含員工資料的 XML 檔案，而員工資料會標上將繫結至文件中內容控制項的項目。  若要將資料設為可在執行階段使用，請內嵌 XML 檔案做為自訂組件中的資源。  
  
#### 建立資料檔  
  
1.  在 \[**專案**\] 功能表中，選擇 \[**加入新項目**\]。  
  
     \[**加入新項目**\] 對話方塊隨即出現。  
  
2.  在 \[範本\] 窗格中，選取 \[XML 檔案\]。  
  
3.  將檔案命名為 **employees.xml**，然後選擇 \[新增\] 按鈕。  
  
     **employees.xml** 檔案隨即在 \[程式碼編輯器\] 中開啟。  
  
4.  將 **employees.xml** 檔案的內容取代為下列文字。  
  
    ```  
  
    <employees xmlns="http://schemas.microsoft.com/vsto/samples">  
      <employee>  
        <name>Karina Leal</name>  
        <hireDate>1999-04-01</hireDate>  
        <title>Manager</title>  
      </employee>  
    </employees>  
    ```  
  
5.  在 \[方案總管\] 中，選擇 **employees.xml** 檔案。  
  
6.  在 \[屬性\] 視窗中，選取 \[建置動作\] 屬性，然後將值變更為 \[內嵌資源\]。  
  
     此步驟會在您建置專案時，將 XML 檔案內嵌為組件中的資源。  這可讓您在執行階段存取 XML 檔案的內容。  
  
## 建立 XML 結構描述  
 如果您想要將內容控制項繫結至自訂 XML 組件中的單一項目，則不需要使用 XML 結構描述。  不過，若要將 <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> 繫結至一組值，您必須建立 XML 結構描述，以驗證您稍早建立的 XML 資料檔。  XML 結構描述定義 `title` 項目的可能值。  稍後，您將在本逐步解說中將 <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> 繫結至此項目。  
  
#### 建立 XML 結構描述  
  
1.  在 \[**專案**\] 功能表中，選擇 \[**加入新項目**\]。  
  
     \[**加入新項目**\] 對話方塊隨即出現。  
  
2.  在 \[範本\] 窗格中，選取 \[XML 結構描述\]。  
  
3.  將結構描述命名為 **employees.xsd**，然後選擇 \[新增\] 按鈕。  
  
     結構描述設計工具隨即開啟。  
  
4.  在 \[方案總管\] 中，開啟 **employees.xsd** 的捷徑功能表，然後選擇 \[檢視程式碼\]。  
  
5.  將 **employees.xsd** 檔案的內容取代為下列結構描述。  
  
    ```  
  
    <xs:schema xmlns="http://schemas.microsoft.com/vsto/samples"   
        targetNamespace="http://schemas.microsoft.com/vsto/samples"  
        xmlns:xs="http://www.w3.org/2001/XMLSchema"  
        elementFormDefault="qualified">  
      <xs:element name="employees" type="EmployeesType"></xs:element>  
      <xs:complexType name="EmployeesType">  
        <xs:all>  
          <xs:element name="employee" type="EmployeeType"/>  
        </xs:all>  
      </xs:complexType>  
      <xs:complexType name="EmployeeType">  
        <xs:sequence>  
          <xs:element name="name" type="xs:string" minOccurs="1" maxOccurs="1"/>  
          <xs:element name="hireDate" type="xs:date" minOccurs="1" maxOccurs="1"/>  
          <xs:element name="title" type="TitleType" minOccurs="1" maxOccurs="1"/>  
        </xs:sequence>  
      </xs:complexType>  
      <xs:simpleType name="TitleType">  
        <xs:restriction base="xs:string">  
          <xs:enumeration value ="Engineer"/>  
          <xs:enumeration value ="Designer"/>  
          <xs:enumeration value ="Manager"/>  
        </xs:restriction>  
      </xs:simpleType>  
    </xs:schema>  
    ```  
  
6.  在 \[檔案\] 功能表上，按一下 \[全部儲存\] 儲存 **employees.xml** 和 **employees.xsd** 檔案的變更。  
  
## 將 XML 結構描述附加至文件  
 您必須將 XML 結構描述附加至文件，以將 <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> 繫結至 `title` 項目的有效值。  
  
#### 將 XML 結構描述附加至文件 \([!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]\)  
  
1.  在設計工具中啟用 **EmployeeControls.docx**。  
  
2.  在功能區上，選擇 \[開發人員\] 索引標籤，然後選擇 \[增益集\] 按鈕。  
  
3.  在 \[範本與增益集\] 對話方塊中，選擇 \[XML 結構描述\] 索引標籤，然後選擇 \[新增結構描述\] 按鈕。  
  
4.  瀏覽至您稍早建立的 **employees.xsd** 結構描述 \(位於您的專案目錄中\)，然後選擇 \[開啟\] 按鈕。  
  
5.  在 \[結構描述設定\] 對話方塊中，選擇 \[確定\] 按鈕。  
  
6.  選擇 \[確定\] 按鈕關閉 \[範本與增益集\] 對話方塊。  
  
#### 將 XML 結構描述附加至文件 \(Word 2010\)  
  
1.  在設計工具中啟用 **EmployeeControls.docx**。  
  
2.  在功能區上，選擇 \[開發人員\] 索引標籤。  
  
3.  在 \[XML\] 群組中，選擇 \[結構描述\] 按鈕。  
  
4.  在 \[範本與增益集\] 對話方塊中，選擇 \[XML 結構描述\] 索引標籤，然後選擇 \[新增結構描述\] 按鈕。  
  
5.  瀏覽至您稍早建立的 **employees.xsd** 結構描述 \(位於您的專案目錄中\)，然後選擇 \[開啟\] 按鈕。  
  
6.  在 \[結構描述設定\] 對話方塊中，選擇 \[確定\] 按鈕。  
  
7.  選擇 \[確定\] 按鈕，關閉 \[範本與增益集\] 對話方塊。  
  
     \[XML 結構\] 工作窗格隨即開啟。  
  
8.  關閉 \[XML 結構\] 工作窗格。  
  
## 將自訂 XML 組件新增至文件  
 您必須先將 XML 檔案的內容新增至文件中的新自訂 XML 組件，才能將內容控制項繫結至 XML 檔案中的項目。  
  
#### 將自訂 XML 組件新增至文件  
  
1.  在 \[方案總管\] 中，開啟 **ThisDocument.cs** 或 **ThisDocument.vb** 的捷徑功能表，然後選擇 \[檢視程式碼\]。  
  
2.  將下列宣告新增至 `ThisDocument` 類別：  此程式碼會宣告數個物件，以用來將自訂 XML 組件新增至文件。  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/VB/ThisDocument.vb#1)]  
  
3.  將下列方法新增至 `ThisDocument` 類別。  這個方法會取得內嵌為組件中資源的 XML 資料檔內容，並以 XML 字串形式傳回內容。  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/VB/ThisDocument.vb#3)]  
  
4.  將下列方法新增至 `ThisDocument` 類別。  `AddCustomXmlPart` 方法會建立新的自訂 XML 組件，其中包含傳遞至此方法的 XML 字串。  
  
     若要確保自訂 XML 組件只建立一次，只有在文件中還沒有具有相符 GUID 的自訂 XML 組件時，此方法才會建立自訂 XML 組件。  第一次呼叫此方法時，它會將 <xref:Microsoft.Office.Core._CustomXMLPart.Id%2A> 屬性的值儲存至 `employeeXMLPartID` 字串。  `employeeXMLPartID` 字串的值會保存在文件中，因為它是使用 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 屬性所宣告。  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/CS/ThisDocument.cs#4)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/VB/ThisDocument.vb#4)]  
  
## 將內容控制項繫結至自訂 XML 組件中的項目  
 使用每個內容控制項的 **XMLMapping** 屬性，以將每個內容控制項繫結至自訂 XML 組件中的項目。  
  
#### 將內容控制項繫結至自訂 XML 組件中的項目  
  
1.  將下列方法新增至 `ThisDocument` 類別。  此方法會將每個內容控制項繫結至自訂 XML 組件中的項目，並設定 <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> 的日期顯示格式。  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/CS/ThisDocument.cs#5)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/VB/ThisDocument.vb#5)]  
  
## 在開啟文件時執行程式碼  
 建立自訂 XML 組件，並在開啟文件時，將自訂控制項繫結至資料。  
  
#### 在開啟文件時執行程式碼  
  
1.  將下面程式碼加新增至 `ThisDocument` 類別的 `ThisDocument_Startup` 方法。  此程式碼會從 **employees.xml** 檔案中取得 XML 字串，並將 XML 字串新增至文件中的新自訂 XML 組件，然後將內容控制項繫結至自訂 XML 組件中的項目。  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/VB/ThisDocument.vb#2)]  
  
## 測試專案  
 開啟文件時，內容控制項會顯示自訂 XML 組件中項目的資料。  您可以按一下 <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> 選取 `title` 項目的三個有效值的其中一個 \(定義於 **employees.xsd** 檔案中\)。  如果您編輯任何內容控制項中的資料，則新的值會儲存在文件的自訂 XML 組件中。  
  
#### 測試內容控制項  
  
1.  按 F5 執行專案。  
  
2.  請確認文件中的資料表類似於下表。  第二個資料行中的每個字串都會取自文件之自訂 XML 組件中的項目。  
  
    |||  
    |-|-|  
    |員工名稱|**Karina Leal**|  
    |雇用日期|**1999 年 4 月 1 日**|  
    |標題|**主管**|  
  
3.  選擇 \[員工名稱\] 儲存格右邊的儲存格，並輸入不同的名稱。  
  
4.  選擇 \[雇用日期\] 儲存格右邊的儲存格，並在日期選擇器中選取不同的日期。  
  
5.  選擇 \[職稱\] 儲存格右邊的儲存格，並從下拉式清單中選取新的項目。  
  
6.  儲存並關閉文件。  
  
7.  在 \[檔案總管\] 中，開啟專案位置下的 \\bin\\Debug 資料夾。  
  
8.  開啟 EmployeeControls.docx 的捷徑功能表，然後選擇 \[重新命名\]。  
  
9. 將檔案命名為 EmployeeControls.docx.zip。  
  
     EmployeeControls.docx 文件會儲存為 Open XML 格式。  將此文件重新命名為具有 .zip 副檔名，即可檢查文件的內容。  如需 Open XML 的詳細資訊，請參閱技術文件：[Office \(2007\) Open XML 檔案格式簡介](http://msdn.microsoft.com/zh-tw/96018532-f62c-4da7-bbff-16b96a483fbf)。  
  
10. 開啟 EmployeeControls.docx.zip 檔案。  
  
11. 開啟 **customXml** 資料夾。  
  
12. 開啟 **item2.xml** 的捷徑功能表，然後選擇 \[開啟\]。  
  
     此檔案包含您已新增至文件的自訂 XML 組件。  
  
13. 請確認 `name`、`hireDate` 和 `title` 項目包含您在文件中的內容控制項中輸入的新值。  
  
14. 關閉 **item2.xml** 檔案。  
  
## 後續步驟  
 您可以透過下列主題，進一步了解如何使用內容控制項：  
  
-   使用所有可用的內容控制項來建立範本。  如需詳細資訊，請參閱[逐步解說：使用內容控制項建立範本](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)。  
  
-   在關閉文件時，修改自訂 XML 組件中的資料。  下次使用者開啟文件時，繫結至 XML 項目的內容控制項會顯示新的資料。  
  
-   使用內容控制項保護文件的組件。  如需詳細資訊，請參閱[如何：使用內容控制項保護文件的部分](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)。  
  
## 請參閱  
 [使用擴充物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)   
 [內容控制項](../vsto/content-controls.md)   
 [如何：將內容控制項加入至 Word 文件](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [如何：使用內容控制項保護文件的部分](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [在執行階段將控制項加入至 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  