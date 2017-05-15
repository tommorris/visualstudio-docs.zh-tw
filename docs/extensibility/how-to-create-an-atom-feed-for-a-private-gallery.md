---
title: "如何: 建立的 Atom 摘要的私用組件庫 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Atom 摘要時，VSIX 私用組件庫"
  - "VSIX 私用組件庫，Atom 摘要"
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# 如何: 建立的 Atom 摘要的私用組件庫
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以建立 Atom \(RSS\) 到內部網路位置，其中包含延伸模組，並加入至摘要 **擴充功能和更新** 為私用組件庫。 如需詳細資訊，請參閱[私用組件庫](../extensibility/private-galleries.md)。  
  
## 建立 Atom 摘要  
 若要建立的 Atom 摘要做為私用組件庫，您先收集您的擴充功能 \(.vsix 檔案\) 的資料夾。 您可以將它們組織到子資料夾如果您想。 您還需要下列資源:  
  
-   會讓延伸可做為私用組件庫 atom.xml 檔案。 如需有關如何連接至 atom.xml 檔案資訊 **擴充功能和更新**, ，請參閱 [私用組件庫](../extensibility/private-galleries.md)。  
  
-   包含任何擴充功能 \(例如，螢幕擷取畫面\) 中擷取的映像檔的資料夾。 Atom.xml 檔案會包含這些映像的相關連結，讓它們可在 **擴充功能和更新**。  
  
 例如，假設您已收集下列兩個延伸到到資料夾:  
  
-   Template\_Wizard\_239.vsix，也就是空的 VSIX 專案範本。  
  
-   SelectionHighlight.vsix，是一種工具來反白顯示選取的字的所有執行個體。  
  
 Atom.xml 檔案的內容會看起來像下列範例:  
  
```  
  <?xml version="1.0" encoding="utf-8" ?> - <feed xmlns="http://www.w3.org/2005/Atom"> <title type="text" /> <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id> <updated>2011-04-14T21:25:48Z</updated> - <entry> <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id> <title type="text">Highlight all occurrences of selected word</title> <summary type="text">This extends the editor to highlight ….</summary> <published>2011-04-14T14:24:51-07:00</published> <updated>2011-04-14T14:24:22-07:00</updated> - <author> <name>Microsoft</name> </author> <link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" /> <link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" /> <content type="application/octet-stream" src="SelectionHighlight.vsix" /> - <Vsix xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010"> <Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id> <Version>1.31</Version> <References /> <Rating xsi:nil="true" /> <RatingCount xsi:nil="true" /> <DownloadCount xsi:nil="true" /> </Vsix> </entry> - <entry> <id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id> … </entry> </feed>  
  
```  
  
 請注意這兩個連結標籤，請參閱產生資料夾中的映像的螢幕擷取畫面。  
  
## 請參閱  
 [私用組件庫](../extensibility/private-galleries.md)