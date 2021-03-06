---
title: 如何： 以程式設計方式存取 Outlook 連絡人
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6ee09e0d0a51675bc00b19aedd0508276cb0cb09
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255937"
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>如何： 以程式設計方式存取 Outlook 連絡人
  此範例會尋找其最後一個的名稱包含指定之搜尋字串的所有連絡人。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>範例  
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]  
  
## <a name="compile-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   連絡人的姓氏包含字串"**Na 」** (例如 Tzipi Butnaru) 中**連絡人**資料夾。  
  
## <a name="see-also"></a>另請參閱  
 [使用連絡人項目](../vsto/working-with-contact-items.md)   
 [如何： 以程式設計方式將項目新增至 Outlook 連絡人](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)   
 [如何： 以程式設計方式搜尋特定的連絡人](../vsto/how-to-programmatically-search-for-a-specific-contact.md)   
 [如何： 以程式設計方式在連絡人電子郵件地址搜尋](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)   
 [如何： 以程式設計方式刪除 Outlook 連絡人](../vsto/how-to-programmatically-delete-outlook-contacts.md)  
  
  