---
title: 如何： 以程式設計方式建立新的 Visio 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], creating Visio documents
- documents [Office development in Visual Studio], creating Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9b5b66690d3856a2bf1fc6df417b60ab5e293127
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256740"
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>如何： 以程式設計方式建立新的 Visio 文件
  當您建立新的 Microsoft Office Visio 繪圖文件時，您會將它加入`Microsoft.Office.Interop.Visio.Documents`開啟 Visio 文件的集合。 因此，`Microsoft.Office.Interop.Visio.Documents.Add`方法會建立新的 Visio 繪圖文件。 如需詳細資訊，請參閱 Microsoft.Office.Interop.Visio.Documents.Add [myTemplate.vst](http://msdn.microsoft.com/library/office/ff766868.aspx) 方法的 VBA 參考文件。  
  
## <a name="create-new-blank-documents"></a>建立新的空白文件  
  
### <a name="to-create-a-new-document"></a>建立新文件  
  
-   使用`Microsoft.Office.Interop.Visio.Documents.Add`方法用來建立新的空白文件不是以範本為基礎。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#1)]  
  
## <a name="create-documents-copied-from-existing-documents"></a>建立複製現有文件的文件  
 `Microsoft.Office.Interop.Visio.Documents.Add`方法可以建立新的文件，這是現有的 Visio 文件的複本。 您必須提供圖表的檔案名稱和完整路徑。  
  
### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>建立從現有文件複製的新文件  
  
-   呼叫`Microsoft.Office.Interop.Visio.Documents.Add`方法並指定 Visio 圖表的路徑。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#2)]  
  
## <a name="create-stencils-copied-from-existing-stencils"></a>建立從現有樣板複製的樣板  
 Microsoft.Office.Interop.Visio.Documents.Add [myTemplate.vst](http://msdn.microsoft.com/library/office/ff766868.aspx) 方法可建立現有 Visio 樣板複本的新樣板。 您必須提供樣板的檔案名稱和完整路徑。  
  
### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>建立從現有樣板複製的新樣板  
  
-   呼叫`Microsoft.Office.Interop.Visio.Documents.Add`方法並指定樣板的路徑。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#3)]  
  
## <a name="create-documents-based-on-existing-templates"></a>建立現有範本為基礎的文件  
 `Microsoft.Office.Interop.Visio.Documents.Add`方法可建立新的文件 ( *.vsd*檔案)，根據現有的 Visio 範本 ( *.vst*檔案)。 這個方法會複製屬於範本工作區一部分的樣板、樣式和設定。 您必須提供範本的檔案名稱和完整路徑。  
  
### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>建立以現有範本為基礎的新文件  
  
-   呼叫`Microsoft.Office.Interop.Visio.Documents.Add`方法並指定範本的路徑。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#4)]  
  
## <a name="compile-the-code"></a>編譯程式碼  
 這個程式碼範例需要下列項目：  
  
-   名為 Visio 文件`myDrawing.vsd`必須位於名為`Test`中*我的文件*資料夾 （適用於 Windows XP 及更早版本） 或*文件*（適用於 Windows Vista) 的資料夾。  
  
-   名為 Visio 文件`myStencil.vss`必須位於名為`Test`中*我的文件*資料夾 （適用於 Windows XP 及更早版本） 或*文件*（適用於 Windows Vista) 的資料夾。  
  
-   名為 Visio 文件`myTemplate.vst`必須位於名為`Test`中*我的文件*資料夾 （適用於 Windows XP 及更早版本） 或*文件*（適用於 Windows Vista) 的資料夾。  
  
## <a name="see-also"></a>另請參閱  
 [Visio 方案](../vsto/visio-solutions.md)   
 [Visio 物件模型概觀](../vsto/visio-object-model-overview.md)   
 [如何： 以程式設計方式開啟 Visio 文件](../vsto/how-to-programmatically-open-visio-documents.md)   
 [如何： 以程式設計方式關閉 Visio 文件](../vsto/how-to-programmatically-close-visio-documents.md)   
 [如何： 以程式設計方式儲存 Visio 文件](../vsto/how-to-programmatically-save-visio-documents.md)   
 [如何： 以程式設計方式列印 Visio 文件](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  