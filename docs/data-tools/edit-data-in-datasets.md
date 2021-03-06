---
title: 編輯資料集中的資料
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c1ad74243c70b4ca7aaa8460759abbc898d30bb9
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757145"
---
# <a name="edit-data-in-datasets"></a>編輯資料集中的資料
如同您編輯任何資料庫中的資料表中的資料，您可以編輯資料的資料表中的資料。 此程序可以包含插入、 更新和刪除資料表中的記錄。 在資料繫結表單中，您可以指定哪些欄位是使用者可編輯。 在這些情況下，資料繫結基礎結構會處理所有變更追蹤，以便變更可以傳送回資料庫更新版本。 如果您以程式設計方式進行編輯的資料，而且您想要將這些變更傳送回資料庫，您必須使用的物件和方法，為您做的變更追蹤。

除了變更實際的資料，您也可以查詢<xref:System.Data.DataTable>傳回特定的資料列。 例如，您可能會查詢個別資料列、 特定版本的資料列 （原始及建議）、 已變更的資料列或資料列中有錯誤。

## <a name="to-edit-rows-in-a-dataset"></a>若要編輯資料集內的資料列
若要編輯現有的資料列中<xref:System.Data.DataTable>，您需要找出<xref:System.Data.DataRow>您想要編輯，然後將更新後的值指派給所需的資料行。

如果您不知道的資料列索引，您想要編輯，請使用`FindBy`方法來搜尋主索引鍵：

[!code-csharp[VbRaddataEditing#3](../data-tools/codesnippet/CSharp/edit-data-in-datasets_1.cs)]
[!code-vb[VbRaddataEditing#3](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_1.vb)]

如果您知道的資料列索引，您可以存取和編輯資料列，如下所示：

[!code-csharp[VbRaddataEditing#5](../data-tools/codesnippet/CSharp/edit-data-in-datasets_2.cs)]
[!code-vb[VbRaddataEditing#5](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_2.vb)]

## <a name="to-insert-new-rows-into-a-dataset"></a>將新的資料列插入資料集
通常使用資料繫結控制項的應用程式新增新的記錄，透過**加入新**按鈕[BindingNavigator 控制項](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms)。

若要以手動方式加入資料集的新記錄，建立新的資料列在 DataTable 上呼叫方法。 然後，新增要的資料列<xref:System.Data.DataRow>集合 (<xref:System.Data.DataTable.Rows%2A>) 的<xref:System.Data.DataTable>:

[!code-csharp[VbRaddataEditing#1](../data-tools/codesnippet/CSharp/edit-data-in-datasets_3.cs)]
[!code-vb[VbRaddataEditing#1](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_3.vb)]

若要保留的資料集必須將更新傳送至資料來源的資訊，請使用<xref:System.Data.DataRow.Delete%2A>方法來移除資料表中的資料列。 例如，如果您的應用程式使用 TableAdapter (或<xref:System.Data.Common.DataAdapter>)，TableAdapter`Update`方法會刪除資料庫中具有的資料列<xref:System.Data.DataRow.RowState%2A>的<xref:System.Data.DataRowState.Deleted>。

如果您的應用程式不需要將更新送回資料來源，就能夠直接存取資料列集合中移除的記錄 (<xref:System.Data.DataRowCollection.Remove%2A>)。

#### <a name="to-delete-records-from-a-data-table"></a>若要從資料表刪除記錄

-   呼叫<xref:System.Data.DataRow.Delete%2A>方法的<xref:System.Data.DataRow>。

     這個方法並不會實際移除記錄。 相反地，它會將記錄標示為刪除。

    > [!NOTE]
    >  如果您收到的 count 屬性<xref:System.Data.DataRowCollection>，產生的計數包括已標示為刪除的記錄。 若要取得精確的計數的不標示為要刪除的記錄，您可以逐一查看集合<xref:System.Data.DataRow.RowState%2A>每一筆記錄的屬性。 (標示為要刪除的記錄都有<xref:System.Data.DataRow.RowState%2A>的<xref:System.Data.DataRowState.Deleted>。)或者，您可以建立資料檢視的資料列狀態為基礎的篩選條件的資料集，並從該處取得計數屬性。

下列範例示範如何呼叫<xref:System.Data.DataRow.Delete%2A>方法，以將標記中的第一個資料列`Customers`資料表為已刪除：

[!code-csharp[VbRaddataEditing#8](../data-tools/codesnippet/CSharp/edit-data-in-datasets_4.cs)]
[!code-vb[VbRaddataEditing#8](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_4.vb)]

## <a name="determine-if-there-are-changed-rows"></a>判斷是否有變更的資料列
資料集內的記錄變更時，會儲存這些變更的相關資訊，直到認可它們。 當您呼叫時，認可的變更`AcceptChanges`方法的資料集或資料的資料表，或當您呼叫`Update`TableAdapter 或資料配接器的方法。

變更會追蹤每個資料列中的兩種方式：

-   每個資料列包含有關其<xref:System.Data.DataRow.RowState%2A>(例如<xref:System.Data.DataRowState.Added>， <xref:System.Data.DataRowState.Modified>， <xref:System.Data.DataRowState.Deleted>，或<xref:System.Data.DataRowState.Unchanged>)。

-   每個已變更的資料列包含該資料列的多個版本 (<xref:System.Data.DataRowVersion>)，原始的版本 （在之前的變更） 和目前的版本 （在之後變更）。 情況下，變更已暫止的時期間 (當您可以回應的時間<xref:System.Data.DataTable.RowChanging>事件)、 第三個版本 — 建議的版本 — 也有提供。

<xref:System.Data.DataSet.HasChanges%2A>資料集的方法會傳回`true`如果已變更資料集內。 決定之後變更的資料列存在，您可以呼叫`GetChanges`方法<xref:System.Data.DataSet>或<xref:System.Data.DataTable>傳回一組已變更的資料列。

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>若要判斷是否已變更的所有資料列

-   呼叫<xref:System.Data.DataSet.HasChanges%2A>方法的資料集，以檢查是否有變更的資料列。

下列範例示範如何檢查傳回的值，從<xref:System.Data.DataSet.HasChanges%2A>方法來偵測是否有任何變更的資料列集中名為`NorthwindDataset1`:

[!code-csharp[VbRaddataEditing#12](../data-tools/codesnippet/CSharp/edit-data-in-datasets_5.cs)]
[!code-vb[VbRaddataEditing#12](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_5.vb)]

## <a name="determine-the-type-of-changes"></a>判斷變更的類型
您也可以檢查以查看何種變更中所做的資料集傳遞的值<xref:System.Data.DataRowState>列舉型別<xref:System.Data.DataSet.HasChanges%2A>方法。

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>若要判斷何種變更已對資料列

-   傳遞<xref:System.Data.DataRowState>值<xref:System.Data.DataSet.HasChanges%2A>方法。

下列範例示範如何檢查名為資料集`NorthwindDataset1`來判斷是否任何新資料列已新增它：

[!code-csharp[VbRaddataEditing#13](../data-tools/codesnippet/CSharp/edit-data-in-datasets_6.cs)]
[!code-vb[VbRaddataEditing#13](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_6.vb)]

## <a name="to-locate-rows-that-have-errors"></a>若要找出有錯誤的資料列
使用個別資料行和資料列時，您可能會遇到錯誤。 您可以檢查`HasErrors`屬性來判斷是否錯誤存在於<xref:System.Data.DataSet>， <xref:System.Data.DataTable>，或<xref:System.Data.DataRow>。

1.  檢查`HasErrors`屬性，以查看資料集內是否有任何錯誤。

2.  如果`HasErrors`屬性是`true`，逐一查看的集合，這些資料表，然後透過資料列，以找出錯誤資料列。

[!code-csharp[VbRaddataEditing#23](../data-tools/codesnippet/CSharp/edit-data-in-datasets_7.cs)]
[!code-vb[VbRaddataEditing#23](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_7.vb)]

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)