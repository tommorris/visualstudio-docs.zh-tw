---
title: 自訂文件屬性概觀
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], custom properties
- custom document properties
- document-level customizations [Office development in Visual Studio], custom properties
- Office documents [Office development in Visual Studio], custom properties
- _AssemblyLocation property
- _AssemblyName property
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 01a85b214c44f3b48a91d82a5abd59bcf4c9ac5c
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "35671503"
---
# <a name="custom-document-properties-overview"></a>自訂文件屬性概觀

當您建置文件層級專案時，Visual Studio 會將兩個自訂屬性加入至專案中的文件：\_組件位置和\_組件名稱。 當使用者開啟文件時，Microsoft Office 應用程式會檢查這些自訂文件屬性。 如果它們存在文件中，應用程式載入[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]，這會啟動自訂。 如需詳細資訊，請參閱 < [Visual Studio 中的 Office 架構方案](../vsto/architecture-of-office-solutions-in-visual-studio.md)。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="assemblyname"></a>\_組件名稱

此屬性包含的介面中的 Office 方案載入器元件的 CLSID [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。 4E3C66D5-58 D 4-491E-A7D4-64AF99AF6E8B 為 CLSID 值。 您不應該變更此值。

## <a name="assemblylocation"></a>\_組件位置

此屬性包含字串，提供自訂的部署資訊清單的詳細資料。 如需有關資訊清單的詳細資訊，請參閱[應用程式和部署資訊清單在 Office 方案中](../vsto/application-and-deployment-manifests-in-office-solutions.md)。

 The_AssemblyLocation 屬性值可以有不同的格式，根據部署解決方案的方式：

- 如果從網站、 UNC 路徑或在 CD 或 USB 磁碟機上安裝發行方案，則 _AssemblyLocation 屬性具有格式*DeploymentManifestPath*|*SolutionID*。 下列字串是範例：

     file://deployserver/MyShare/ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- 如果您要執行，或從 Visual Studio 方案進行偵錯，_AssemblyLocation 屬性具有格式*DeploymentManifestName*|*SolutionID*| vstolocal。 下列字串是範例：

     ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9|vstolocal

 *SolutionID*是 GUID，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]用來識別方案。 *SolutionID*建置專案時會自動產生。 **Vstolocal**詞彙來表示[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]從相同的資料夾和文件應該是載入的組件。

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中的 Office 方案的架構](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [文件層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)
- [在 Office 方案中的應用程式和部署資訊清單](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [如何： 使用 ClickOnce 發行 Office 方案](http://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [如何： 建立和修改自訂文件屬性](../vsto/how-to-create-and-modify-custom-document-properties.md)
