---
title: 逐步解說： 自訂插入、 更新和刪除實體類別的行為
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: fb01ef51c0a44047e2caf2f23634ebe741cd2dcb
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174970"
---
# <a name="walkthrough-customize-the-insert-update-and-delete-behavior-of-entity-classes"></a>逐步解說： 自訂插入、 更新和刪除行為的實體類別

[在 Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)提供視覺化設計介面建立和編輯 LINQ to SQL 類別 （實體類別） 為基礎的資料庫中的物件。 藉由使用[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)，您可以使用 LINQ 技術來存取 SQL 資料庫。 如需詳細資訊，請參閱 < [LINQ (Language Integrated query)](/dotnet/csharp/linq/)。

根據預設，LINQ to SQL 執行階段會提供邏輯以執行更新。 執行階段會建立預設`Insert`， `Update`，和`Delete`資料表 （資料行定義和主索引鍵資訊） 的結構描述為基礎的陳述式。 當您不想要使用的預設行為時，您可以設定更新行為，並指定特定的預存程序來執行所需的插入、 更新和刪除資料庫中的資料搭配使用所需。 未產生預設行為時 (例如，實體類別是對應至檢視時)，同樣可以這樣做。 此外，在資料庫需要透過預存程序進行資料表存取時，也可以覆寫預設更新行為。 如需詳細資訊，請參閱 <<c0> [ 使用預存程序來自訂作業](/dotnet/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures)。

> [!NOTE]
> 本逐步解說需要的可用性**InsertCustomer**， **UpdateCustomer**，並**DeleteCustomer**預存程序，Northwind 資料庫。

這個逐步解說提供覆寫預設 LINQ to SQL 執行階段行為，以使用預存程序將資料儲存回資料庫的必要步驟。

在這個逐步解說中，您將了解如何執行下列工作：

-   建立新的 Windows Forms 應用程式，並加入 LINQ to SQL 檔案。

-   建立實體類別對應至 Northwind`Customers`資料表。

-   建立參考 LINQ to SQL 物件資料來源`Customer`類別。

-   建立 Windows 表單，其中包含<xref:System.Windows.Forms.DataGridView>繫結至`Customer`類別。

-   實作表單的儲存功能。

-   建立<xref:System.Data.Linq.DataContext>方法，藉由新增預存程序**O/R Designer**。

-   設定`Customer`類別，以使用預存程序來執行插入、 更新和刪除。

## <a name="prerequisites"></a>必要條件

本逐步解說會使用 SQL Server Express LocalDB 和 Northwind 範例資料庫。

1.  如果您沒有 SQL Server Express LocalDB，請將它安裝從[SQL Server Express 下載頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)，或透過**Visual Studio 安裝程式**。 在  **Visual Studio 安裝程式**，您可以安裝 SQL Server Express LocalDB 做為一部分**資料儲存和處理**工作負載，或作為個別的元件。

2.  安裝 Northwind 範例資料庫執行下列步驟：

    1. 在 Visual Studio 中開啟**SQL Server 物件總管**視窗。 (**SQL Server 物件總管**安裝的一部分**資料儲存和處理**中的工作負載**Visual Studio 安裝程式**。)依序展開**SQL Server**節點。 以滑鼠右鍵按一下您的 LocalDB 執行個體，然後選取**新的查詢**。

       查詢編輯器視窗隨即開啟。

    2. 複製[Northwind 的 TRANSACT-SQL 指令碼](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)到剪貼簿。 這個 T-SQL 指令碼會從頭建立 Northwind 資料庫，並填入資料。

    3. 將 T-SQL 指令碼貼到查詢編輯器，然後選擇**Execute**  按鈕。

       短時間之後，查詢完成執行，並建立 Northwind 資料庫。

## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>建立應用程式和加入 LINQ to SQL 類別

因為您是使用 LINQ to SQL 類別，並顯示 Windows Form 上的資料，建立新的 Windows Forms 應用程式，並加入 LINQ to SQL 類別檔案。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-new-windows-forms-application-project-that-contains-linq-to-sql-classes"></a>若要建立新的 Windows Forms 應用程式專案包含 LINQ to SQL 類別

1. 在 Visual Studio 中，在**檔案**功能表上，選取**新增** > **專案**。

2. 展開  **Visual C#** 或是**Visual Basic**的左側窗格中，然後選取**Windows Desktop**。

3. 在中間窗格中，選取**Windows Forms 應用程式**專案類型。

4. 將專案命名為**UpdatingWithSProcsWalkthrough**，然後選擇**確定**。

     **UpdatingWithSProcsWalkthrough**專案時建立，並加入至**方案總管 中**。

4.  在 [專案]  功能表中，按一下 [加入新項目] 。

5.  按一下 [ **LINQ to SQL 類別**範本，然後輸入**Northwind.dbml**中**名稱**] 方塊中。

6.  按一下 [加入] 。

     空的 LINQ to SQL 類別檔案 (**Northwind.dbml**) 會加入至專案，而**O/R Designer**隨即開啟。

## <a name="create-the-customer-entity-class-and-object-data-source"></a>建立 Customer 實體類別和物件資料來源

建立 LINQ to SQL 類別從資料表對應至資料庫資料表**伺服器總管**或是**資料庫總管**拖曳至**O/R 設計工具**。 結果會產生對應至資料庫中各資料表的 LINQ to SQL 實體類別。 建立實體類別之後，實體類別就和其他具有公用 (Public) 屬性的類別一樣，可以當成物件資料來源使用。

### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>若要建立 Customer 實體類別和將它設為資料來源

1.  在 **伺服器總管**或**資料庫總管**，找出**客戶**Northwind 範例資料庫的 SQL Server 版本中的資料表。

2.  拖曳**客戶**從節點**伺服器總管**或**資料庫總管**拖曳至 **O/R Designer*介面。

     實體類別**客戶**建立。 它的屬性會對應至 Customers 資料表中的各資料行。 實體類別名為**客戶**(不**客戶**) 因為它代表 Customers 資料表中的單一客戶。

    > [!NOTE]
    > 這個重新命名的行為稱為*複數表示*。 它可以開啟或關閉在中開啟[[選項] 對話方塊](../ide/reference/options-dialog-box-visual-studio.md)。 如需詳細資訊，請參閱 <<c0> [ 如何： 開啟和關閉 （O/R 設計工具） 的複數表示](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md)。

3.  在 **建置**功能表上，按一下**建置 UpdatingwithSProcsWalkthrough**來建置專案。

4.  按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。

5.  在 [ **資料來源** ] 視窗中，按一下 [ **加入新資料來源**]。

6.  按一下 [**物件**上**選擇資料來源類型**頁面，然後按一下**下一步]**。

7.  依序展開**UpdatingwithSProcsWalkthrough**節點並找出並選取**客戶**類別。

    > [!NOTE]
    > 如果**客戶**類別不提供，取消精靈、 建置專案時，並再次執行精靈。
8.  按一下 **完成**來建立資料來源並新增**客戶**實體類別，以**Zdroje dat**視窗。

## <a name="create-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>建立 DataGridView 以便在 Windows Form 上顯示的客戶資料

建立藉由拖曳 LINQ 到 SQL 資料來源項目，從繫結至實體類別的控制項**Zdroje dat**視窗拖曳至 Windows Form。

### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>若要加入繫結至實體類別的控制項

1.  開啟**Form1**設計 檢視中。

2.  從**資料來源** 視窗中，拖曳**客戶**節點拖曳至**Form1**。

    > [!NOTE]
    > 若要顯示**資料來源** 視窗中，按一下**顯示資料來源**上**資料**功能表。

3.  開啟**Form1**在程式碼編輯器。

4.  將下列程式碼加入至表單，通用的表單中，任何特定的方法之外，但內部`Form1`類別：

    ```vb
    Private NorthwindDataContext1 As New NorthwindDataContext
    ```

    ```csharp
    private NorthwindDataContext northwindDataContext1
        = new NorthwindDataContext();
    ```

5.  建立 `Form_Load` 事件的事件處理常式，並將下列程式碼加入至處理常式中：

    ```vb
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers
    ```

    ```csharp
    customerBindingSource.DataSource
        = northwindDataContext1.Customers;
    ```

## <a name="implement-save-functionality"></a>實作儲存功能

預設不會啟用儲存按鈕，也不會實作儲存功能。 同時，為物件資料來源建立資料繫結控制項時，並不會自動加入程式碼以將變更的資料儲存至資料庫。 本節說明如何啟用儲存按鈕並實作儲存功能的 LINQ 到 SQL 物件。

### <a name="to-implement-save-functionality"></a>若要實作儲存功能

1.  開啟**Form1**設計 檢視中。

2.  選取 [儲存] 按鈕**CustomerBindingNavigator** （磁碟片圖示的按鈕）。

3.  在 **屬性**視窗中，將**已啟用**屬性設 **，則為 True**。

4.  按兩下儲存按鈕以建立事件處理常式，並切換至 [色彩編輯器]。

5.  將下列程式碼加入至儲存按鈕事件處理常式：

    ```vb
    NorthwindDataContext1.SubmitChanges()
    ```

    ```csharp
    northwindDataContext1.SubmitChanges();
    ```

## <a name="override-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>覆寫預設行為，執行更新 （插入、 更新和刪除）

### <a name="to-override-the-default-update-behavior"></a>若要覆寫預設更新行為

1.  開啟 LINQ to SQL 中的檔案**O/R Designer**。 (按兩下**Northwind.dbml**中的檔案**方案總管 中**。)

2.  在 [**伺服器總管**或**資料庫總管**，展開 Northwind 資料庫**預存程序**] 節點並找出**InsertCustomers**， **UpdateCustomers**，並**DeleteCustomers**預存程序。

3.  將所有三個預存程序拖曳至**O/R Designer**。

     預存程序會加入至方法窗格中做為 <xref:System.Data.Linq.DataContext> 方法。 如需詳細資訊，請參閱 < [DataContext 方法 （O/R 設計工具）](../data-tools/datacontext-methods-o-r-designer.md)。

4.  選取 **客戶**中的實體類別**O/R Designer**。

5.  在 **屬性**視窗中，選取**插入**屬性。

6.  按一下省略符號 (**...**) 旁**使用執行階段**以開啟**設定行為** 對話方塊。

7.  選取 **來自訂**。

8.  選取  **InsertCustomers**方法中的**自訂**清單。

9. 按一下 **套用**儲存選取的類別和行為的組態。

    > [!NOTE]
    > 您可以繼續設定每個類別/行為組合的行為，只要您按**套用**每一項變更之後。 如果您變更了類別或行為再按一下 **套用**、 提供讓您套用任何變更會出現警告對話方塊。

10. 選取 **更新**中**行為**清單。

11. 選取 **來自訂**。

12. 選取  **UpdateCustomers**方法中的**自訂**清單。

     檢查清單**方法引數**並**類別屬性**，並注意有兩個**方法引數**並將兩個**類別屬性**資料表中的某些資料行。 這樣可以更容易追蹤變更，並建立陳述式來檢查並行違規。

13. 地圖**Original_CustomerID**方法引數**CustomerID (Original)** 類別屬性。

    > [!NOTE]
    > 根據預設，方法引數會對應至同名的類別屬性。 如果屬性名稱會變更，而且資料表與實體類別之間不再對應，您可能需要選取對等類別来對應的屬性，如果**O/R Designer**無法判斷正確的對應。 此外，如果方法引數沒有對應至有效的類別屬性，您可以設定**類別屬性**值 **（無）**。

14. 按一下 **套用**儲存選取的類別和行為的組態。

15. 選取 **刪除**中**行為**清單。

16. 選取 **來自訂**。

17. 選取  **DeleteCustomers**方法中的**自訂**清單。

18. 地圖**Original_CustomerID**方法引數**CustomerID (Original)** 類別屬性。

19. 按一下 [確定 **Deploying Office Solutions**]。

> [!NOTE]
> 雖然它不是本特定逐步解說的問題，值得注意的是，LINQ to SQL 會在插入期間處理資料庫產生的值，會自動針對識別 （自動遞增）、 rowguidcol (資料庫產生的 GUID) 和時間戳記資料行和更新。 其他資料行型別的資料庫產生值將非預期地產生 null 值。 若要傳回資料庫產生的值，您應該手動設定<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>來`true`並<xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>的下列其中一個： [AutoSync.Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>)， [AutoSync.OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>)，或[AutoSync.OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>)。

## <a name="test-the-application"></a>測試應用程式

執行應用程式一次，確認**UpdateCustomers**預存程序已正確更新資料庫中的客戶記錄。

1.  請按 **F5**。

2.  修改記錄，以在方格中，若要測試更新行為。

3.  加入新的記錄，以測試 「 插入 」 行為。

4.  按一下儲存按鈕，將變更儲存回資料庫。

5.  關閉表單 

6.  按下**F5**並確認更新的記錄和剛插入的記錄會保存。

7.  刪除的新記錄您在步驟 3，以測試 「 刪除 」 行為。

8.  按一下 [儲存] 按鈕，以將變更送出，並從資料庫移除已刪除的資料錄。

9. 關閉表單 

10. 按下**F5**並確認已從資料庫中移除已刪除的資料錄。

    > [!NOTE]
    > 如果您的應用程式會使用 SQL Server Express Edition 的值而定**複製到輸出目錄**資料庫檔案的屬性，變更可能不會出現當您按下**F5**在步驟 10。

## <a name="next-steps"></a>後續步驟

根據您的應用程式的需求，有數個步驟，您可能想要執行您建立 LINQ to SQL 實體類別之後。 您可以進行下列作業讓此應用程式發揮更強的功能：

- 在更新期間實作並行檢查。 如需資訊，請參閱[開放式並行存取： 概觀](/dotnet/framework/data/adonet/sql/linq/optimistic-concurrency-overview)。

- 加入 LINQ 查詢，以篩選資料。 如需資訊，請參閱[LINQ 查詢 (C#) 簡介](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)。

## <a name="see-also"></a>另請參閱

- [LINQ to SQL 工具，在 Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext 方法](../data-tools/datacontext-methods-o-r-designer.md)
- [如何： 指定用來執行更新、 插入和刪除的預存程序](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [LINQ to SQL 查詢](/dotnet/framework/data/adonet/sql/linq/linq-to-sql-queries)