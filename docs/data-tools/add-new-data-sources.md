---
title: 加入新的資料來源
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.datasource.datasourcefieldspicker
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 1bbe808f1c43e0f4083f5ed1d04db347560a2630
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "35666627"
---
# <a name="add-new-data-sources"></a>加入新的資料來源

.NET data tools 在 Visual Studio 中的內容中的字詞*資料來源*是指連接到資料存放區，並將資料公開給.NET 應用程式的.NET 物件。 Visual Studio 設計工具可以取用資料來源產生拖曳和卸除資料庫物件時，將資料繫結至表單的未定案程式碼的輸出**Zdroje dat**視窗。 這種資料來源可以是：

- 與某些類型的資料庫相關聯的 Entity Framework 模型中的類別。

- 與某些類型的資料庫相關聯的資料集。

- 表示 Windows Communication Foundation (WCF) 資料服務或 REST 服務作為網路服務的類別。

- 表示 SharePoint 服務的類別。

- 類別或您方案中的集合。

> [!NOTE]
> 如果您不使用資料繫結功能，資料集、 Entity Framework、 LINQ to SQL、 WCF、 或 SharePoint，「 資料來源 」 的概念不適用。 只要直接連接到資料庫所使用的 SQLCommand 物件，並直接與資料庫通訊。

您建立和編輯資料來源，使用**資料來源組態精靈**Windows Form 或 Windows Presentation Foundation 應用程式中。 Entity Framework 的第一次建立實體類別，並選取，以啟動精靈**專案** > **加入新的資料來源**（本文稍後詳細說明）。

![資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png)

建立資料來源之後，它會出現在**資料來源**工具視窗 (**Shift**+**Alt**+**D**或是**檢視** > **其他 Windows** > **資料來源**)。 您可以將從資料來源**Zdroje dat**視窗拖曳到表單的設計介面或控制項。 這會導致未定案程式碼產生，顯示從資料存放區的資料。 下圖顯示資料集拖曳至 Windows form 已卸除。 如果您選取**F5**應用程式，在基礎資料庫中的資料會出現在表單的控制項。

![資料來源拖放作業](../data-tools/media/raddata-data-source-drag-operation.png)

## <a name="data-source-for-a-database-or-a-database-file"></a>資料庫或資料庫檔案的資料來源

您可以建立資料集或 Entity Framework 模型做為資料來源使用的資料庫或資料庫檔案。

### <a name="dataset"></a>資料集

若要建立資料集做為資料來源，執行**資料來源組態精靈**藉由選取**專案** > **加入新的資料來源**。 選擇**資料庫**資料來源類型，並遵循提示來指定新的或現有的資料庫連接或資料庫檔案。

### <a name="entity-classes"></a>實體類別

若要建立 Entity Framework 模型做為資料來源：

1. 執行**Entity Data Model 精靈**建立實體類別。 選取 **專案** > **加入新項目** > **ADO.NET 實體資料模型**。

   ![新的 Entity Framework 模型專案項目](../data-tools/media/raddata-new-entity-framework-model-project-item.png)

1. 選擇您想要產生模型的方法。

   ![實體資料模型精靈](../data-tools/media/raddata-entity-data-model-wizard.png)

1. 將模型加入做為資料來源。 產生的類別會出現在**資料來源組態精靈**當您選擇**物件**類別目錄。

   ![使用實體類別的資料來源組態精靈](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png)

## <a name="data-source-for-a-service"></a>服務的資料來源

若要從服務中建立資料來源，執行**資料來源組態精靈**，然後選擇**服務**資料來源類型。 這是只捷徑**加入服務參考**對話方塊中，您也可以存取中的專案上按一下滑鼠右鍵**方案總管**，然後選取**加入服務參考**.

當您從服務建立資料來源時，Visual Studio 新增服務參考加入專案。 Visual Studio 也會建立對應至服務傳回之物件的 proxy 物件。 比方說，傳回的資料集的服務都會在您的專案做為資料集;傳回在您的專案做為類型中表示特定類型傳回服務。

您可以從下列服務類型來建立資料來源：

- [WCF Data Services](/dotnet/framework/data/wcf/wcf-data-services-overview)

- [WCF 服務](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- Web 服務

    > [!NOTE]
    > 在出現的項目**Zdroje dat**視窗均依存於服務所傳回的資料。 某些服務可能並未提供足夠的資訊，如**資料來源組態精靈**來建立可繫結的物件。 例如，如果服務傳回不具類型的資料集，顯示任何項目中**Zdroje dat**視窗中，當您完成精靈。 這是因為不具類型資料集不提供結構描述，因此精靈沒有足夠的資訊來建立資料來源。

## <a name="data-source-for-an-object"></a>物件的資料來源

您可以從任何公開 （expose） 執行的一或多個公用屬性的物件建立資料來源**資料來源組態精靈**，然後選取**物件**資料來源類型。 物件的所有公用屬性會顯示在**Zdroje dat**視窗。 如果您使用 Entity Framework，並產生一個模型，這是您在其中找到您的應用程式的資料來源的實體類別。

在 **選取資料物件**頁面上，展開樹狀檢視中找出您想要繫結至物件中的節點。 樹狀檢視中包含您的專案和組件和其他專案所參考的專案節點。

如果您想要繫結至組件或未出現在 [樹狀] 檢視的專案中的物件，請按一下**加入參考**並用**Add Reference Dialog Box**加入至組件或專案的參考。 加入參考之後，組件或專案會加入 [樹狀] 檢視中。

> [!NOTE]
> 若要建置的專案，然後物件才會出現在樹狀檢視中包含您的物件。

> [!NOTE]
> 若要支援拖放資料繫結物件實作<xref:System.ComponentModel.ITypedList>或<xref:System.ComponentModel.IListSource>介面都必須有預設建構函式。 否則，Visual Studio 無法具現化的資料來源物件，而且它會顯示錯誤，當您將項目拖曳至設計介面。

## <a name="data-source-for-a-sharepoint-list"></a>如需 SharePoint 清單的資料來源

您也可以執行從 SharePoint 清單建立資料來源**資料來源組態精靈**，然後選取**SharePoint**資料來源類型。 SharePoint 會公開透過 WCF Data Services，資料，因此建立 SharePoint 資料來源是從服務建立資料來源相同。 選取**SharePoint**中的項目**資料來源組態精靈**開啟**加入服務參考**對話方塊中，您連接至 SharePoint 資料服務藉由指向 SharePoint 伺服器。 這需要 SharePoint SDK。

## <a name="see-also"></a>另請參閱

- [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)