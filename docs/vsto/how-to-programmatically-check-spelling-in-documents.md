---
title: 如何： 以程式設計方式檢查文件中的拼字
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], checking spelling
- spelling checker, documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e916b16caaaa3944fcdf522ffd320198d9972b52
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256714"
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>如何： 以程式設計方式檢查文件中的拼字
  若要檢查文件中的拼字錯誤，請使用<xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A>方法。 這個方法會傳回布林值，指出所提供的參數的拼字是否正確。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-check-spelling-and-display-results-in-a-message-box"></a>若要檢查拼字，並在訊息方塊中顯示結果  
  
1.  呼叫<xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A>方法並將它傳遞來檢查是否有拼字錯誤的文字範圍。 若要使用這個程式碼範例，請從專案的 `ThisDocument` 或 `ThisAddIn` 類別中執行它。  
  
     [!code-vb[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#113)]
     [!code-csharp[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#113)]  
  
## <a name="see-also"></a>另請參閱  
 [如何： 以程式設計方式定義，並在文件中選取範圍](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  