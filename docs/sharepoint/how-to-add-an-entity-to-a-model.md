---
title: 如何： 將實體新增至模型 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- EntityTool
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], entity
- Business Data Connectivity service [SharePoint development in Visual Studio], adding an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], entity
- BDC [SharePoint development in Visual Studio], adding an entity
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 72dbebd8ff9b2e7bf7b001d540158656271c0556
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757703"
---
# <a name="how-to-add-an-entity-to-a-model"></a>如何： 將實體新增至模型
  若要建立實體，請從 Visual Studio 中新增實體控制項**工具箱**商務資料連接 (BDC) 設計工具上。  
  
### <a name="to-add-an-entity-to-the-model"></a>若要將實體新增至模型  
  
1.  建立 BDC 專案，或開啟現有的 BDC 專案。 如需詳細資訊，請參閱 <<c0> [ 建立 business data connectivity 模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
2.  在 **工具箱**，從**BusinessDataCatalog**群組中，新增**實體**控制項拖曳至設計工具。  
  
     新的實體會出現在設計工具。 Visual Studio 會加入`<Entity>`BDC 模型檔案，在您的專案中的 xml 項目。 實體項目之屬性的相關資訊，請參閱[實體](http://go.microsoft.com/fwlink/?LinkId=169296)。  
  
3.  在設計工具中，開啟實體的捷徑功能表，選擇 **新增**，然後選擇**識別項**。  
  
     新的識別碼會出現在實體中。  
  
    > [!NOTE]  
    >  您可以變更實體和中的識別項的名稱**屬性**視窗。  
  
4.  在類別中定義之實體的欄位。 您可以將新類別加入專案，或使用現有的類別使用物件關聯式設計工具 （O/R 設計工具） 等其他工具所建立。 下列範例顯示名為連絡人的實體類別。  
  
     [!code-csharp[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb#1)]  
  
## <a name="see-also"></a>另請參閱
 [如何： 新增建立者方法](../sharepoint/how-to-add-a-creator-method.md)   
 [如何： 加入刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)   
 [如何： 加入更新者方法](../sharepoint/how-to-add-an-updater-method.md)   
 [如何： 新增搜尋方法](../sharepoint/how-to-add-a-finder-method.md)   
 [如何： 加入特定搜尋方法](../sharepoint/how-to-add-a-specific-finder-method.md)  
  
 
