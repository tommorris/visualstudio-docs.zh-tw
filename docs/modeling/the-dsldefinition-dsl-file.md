---
title: "DslDefinition.dsl 檔 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "網域指定的語言, 定義檔"
ms.assetid: f3fc3ed7-2438-4e5a-b3d7-fe7e0e8a134c
caps.latest.revision: 22
caps.handback.revision: 22
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# DslDefinition.dsl 檔
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主題說明 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 方案之 Dsl 專案中的 DslDefinition.dsl 檔的結構，其定義*「網域指定的語言」*\(domain\-specific language\)。  DslDefinition.dsl 檔說明網域指定的語言之類別和關聯性，連同網域指定的語言之圖表、圖形、連接器、序列化格式和 \[工具箱\]，以及其編輯工具。  在網域指定的語言方案中，會根據 DslDefinition.dsl 檔中的資訊產生定義那些工具的程式碼。  
  
 一般而言，您會使用*「網域指定的語言設計工具」*\(Domain\-Specific Language Designer\) 編輯 DslDefinition.dsl 檔。  不過，其未經處理格式為 XML，因此可以在 XML 編輯器中開啟 DslDefinition.dsl 檔。  了解該檔案包含什麼資訊以及它如何編排以進行偵錯和擴充，可能會對您非常有用。  
  
 本主題中的範例取自「元件圖」方案範本。  若要查看範例，請根據「元件模型」方案範本建立網域指定的語言方案。  建立方案後，DslDefinition.dsl 檔會出現在網域指定的語言設計工具中。  關閉檔案，在 \[方案總管\] 中按一下滑鼠右鍵，指向 \[開啟方式\]，按一下 \[XML 編輯器\]，然後按一下 \[確定\]。  
  
## DslDefinition.dsl 檔的區段  
 根項目為 \<Dsl\>，其屬性識別網域指定的語言之名稱、命名空間，以及主要和次要版本號碼以進行版本控制。  `DslDefinitionModel` 結構描述定義有效 DslDefinition.dsl 檔的內容和結構。  
  
 \<Dsl\> 根項目的子項目如下：  
  
 類別  
 此區段定義的每一個網域類別都會在產生的程式碼中產生一個類別。  
  
 關聯性  
 此區段定義模型中的每一個關聯性。  來源和目標代表關聯性的兩端。  
  
 型別  
 此區段定義每一種類型以及其命名空間。  網域屬性有兩種類型。  `DomainEnumerations` 定義於模型，並產生類型到 DomainModel.cs。  `ExternalTypes` 是指在其他地方定義的類型 \(如 `String` 或 `Int32`\)，且不會產生任何內容。  
  
 圖形  
 此區段定義的圖形說明模型在設計工具中的顯示方式。  這些幾何圖形會對應至 \[圖表\] 區段之模型中的類別。  
  
 連接器  
 此區段定義出現在設計工具中的連接器外觀。  這些幾何樣式描述會對應至 \[圖表\] 區段之模型中的特定關聯性。  
  
 XmlSerializationBehavior  
 此區段定義序列化配置，並提供每一個類別如何儲存到檔案的其他資訊。  
  
 ExplorerBehavior  
 此區段定義使用者編輯模型時，\[DSL Explorer\] 視窗如何顯示。  
  
 ConnectionBuilders  
 此區段會為每一個連接器工具 \(在可以連接的任兩個類別之間建立連結的工具\) 定義連接產生器。  此區段決定您是否可以連接來源和目標類別。  
  
 圖表  
 此區段定義圖表，可以用來指定背景色彩和根類別之類的屬性。  \(根類別是以整體圖表所代表的網域類別。\)\[圖表\] 區段也包含 ShapeMap 和 ConnectorMap 項目，這些項目指定代表每一個網域類別或關聯性的圖形或連接器。  
  
 設計工具  
 此區段定義設計工具 \(編輯器\)，可將 \[工具箱\]、驗證設定、圖表和序列化配置聚集在一起。  \[設計工具\] 區段也定義模型的根類別，此類別通常也是圖表的根類別。  
  
 Explorer  
 此區段定義 \[DSL Explorer\] 行為 \(定義於 XmlSerializationBehavior 區段\)。  
  
## DslDefinition.dsl 檔中的 Moniker  
 在整個 DslDefinition.dsl 檔中，您都可以使用 Moniker 建立對特定項目的交互參考。  例如，每一個關聯性定義都包含 \[來源\] 子區段和 \[目標\] 子區段。  每一個子區段都包含可與該關聯性連結的物件類別 Moniker：  
  
```  
<DomainRelationship …        Name="LibraryHasMembers" Namespace="ExampleNamespace" >    <Source>      <DomainRole …>  
       <RolePlayer>  
         <DomainClassMoniker Name="Library" />  
       </RolePlayer>  
     </DomainRole>  
   </Source>  
```  
  
 通常，所參考項目 \(在本範例中為 `Library` 網域類別\) 的命名空間與參考方項目 \(在這個案例中是 LibraryHasMembers 網域關聯性\) 相同。  在那些案例中，Moniker 必須僅提供類別的名稱。  否則，您應使用完整格式 \/命名空間\/名稱：  
  
```  
  
<DomainClassMoniker Name="/ExampleNameSpace/Library" />  
  
```  
  
 Moniker 系統要求 XML 樹狀結構中的同層級具有不同名稱。  基於此原因，如果您嘗試儲存具有兩個同名類別 \(舉例而言\) 的網域指定語言定義，則會發生驗證錯誤。  您應該一律在儲存 DslDefinition.dsl 檔之前更正這類的重複名稱錯誤，以便在稍後正確地重新載入它。  
  
 每一種類型都有自己的 Moniker 類型：DomainClassMoniker、DomainRelationshipMoniker 等等。  
  
## 型別  
 \[類型\] 區段將 DslDefinition.dsl 檔包含的所有類型指定為屬性的類型。  這些類型分成兩種：外部類型 \(如 System.String\) 和列舉類型。  
  
### 外部類型  
 「元件圖」範例列出一組標準基本類型，不過只會使用其中的部分類型。  
  
 每一個外部類型定義都由名稱和命名空間所組成，如 String 與 System：  
  
```  
<ExternalType Name="String" Namespace="System" />  
```  
  
 使用類型的完整名稱，而不是對等的編譯器關鍵字，如 "string"。  
  
 外部類型不限於標準程式庫類型。  
  
### 列舉型別  
 一般的列舉規格類似以下範例：  
  
```  
<DomainEnumeration IsFlags="true" Name="PageSort"          Namespace="Fabrikam.Wizard">  
  <Literals>  
    <EnumerationLiteral Name="Start" Value="1"/>  
    <EnumerationLiteral Name="Decision" Value="2"/>  
  </Literals>  
</DomainEnumeration>  
```  
  
 `IsFlags` 屬性會控制產生的程式碼前面是否加上 `[Flags]` 通用語言執行平台 \(CLR\) 屬性，該屬性決定列舉值是否可以透過位元結合在一起。  如果此屬性設為 true，則應指定 2 的次方值為常值。  
  
## 類別  
 網域指定語言的任何定義中，大部分的項目都是 `DomainClass` 的直接或間接執行個體。  `DomainClass` 的子類別包括 `DomainRelationship`、`Shape`、`Connector` 和 `Diagram`。  DslDefinition.dsl 檔的 `Classes` 區段列出網域類別。  
  
 每一個類別都有一組屬性，並可能具有基底類別。  在「元件圖」範例中，`NamedElement` 是具有 `Name` 屬性的抽象類別，其類型為字串：  
  
```  
<DomainClass Id="ee3161ca-2818-42c8-b522-88f50fc72de8"  Name="NamedElement" Namespace="Fabrikam.CmptDsl5"      DisplayName="Named Element"  InheritanceModifier="Abstract">  
  <Properties>  
    <DomainProperty Id="ef553cf0-33b5-4e34-a30b-cfcfd86f2261"   Name="Name" DisplayName="Name"  DefaultValue="" Category="" IsElementName="true">  
      <Type>  
        <ExternalTypeMoniker Name="/System/String" />  
      </Type>  
    </DomainProperty>  
  </Properties>  
</DomainClass>  
```  
  
 `NamedElement` 是數個其他類別 \(例如 `Component`\) 的基底，此基底除了 `Name` 屬性 \(繼承自 `NamedElement`\) 外還有自己的屬性。  BaseClass 子節點包含 Moniker 參考。  由於參考的類別在相同的命名空間中，因此 Moniker 中只需要其名稱：  
  
```  
<DomainClass Name="Component" Namespace="Fabrikam.CmptDsl5"              DisplayName="Component">  
  <BaseClass>  
    <DomainClassMoniker Name="NamedElement" />  
  </BaseClass>  
  <Properties>  
    <DomainProperty Name="Kind" DisplayName="Kind" >  
      <Type>  
        <ExternalTypeMoniker Name="/System/String" />  
      </Type>  
    </DomainProperty>  
  </Properties>  
```  
  
 每個網域類別 \(包括關聯性、圖形、連接器和圖表\) 都可以有下列屬性和子節點：  
  
-   **Id。**這個屬性是 GUID。  如果您沒有在檔案中提供值，則「網域指定的語言設計工具」將建立一個值。  \(在此文件的圖中，通常會忽略此屬性以節省空間。\)  
  
-   **Name 與 Namespace。** 這些屬性指定所產生程式碼中的類別之名稱和命名空間。  它們在網域指定的語言內必須都是唯一的。  
  
-   **InheritanceModifier。**這個屬性為「抽象」、「密封」或無。  
  
-   **DisplayName。**這個屬性為 \[屬性\] 視窗中顯示的名稱。  DisplayName 屬性可以包含空格和其他標點符號。  
  
-   **GeneratesDoubleDerived。** 如果此屬性設為 true，則會產生兩個類別，其中一個是另一個的子類別。  所有產生的方法都在基底類別中，而建構函式在子類別中。  設定此屬性可讓您覆寫自訂程式碼中的所有產生的方法。  
  
-   **HasCustomConstructor**。  如果此屬性設為 true，則會從產生的程式碼中省略建構函式，讓您可以撰寫您自己的版本。  
  
-   **Attributes**。  此屬性包含所產生類別的 CLR 屬性。  
  
-   **BaseClass**。  如果您指定基底類別，其類型必須相同。  例如，網域類別必須有另一個網域類別做為其基底，而區間圖形必須有區間圖形。  如果您不指定基底類別，所產生程式碼中的類別會從標準架構類別中衍生。  例如，網域類別會從 `ModelElement` 中衍生。  
  
-   **Properties**。  此屬性 \(attribute\) 包含的屬性 \(properties\) 在異動控制之下維護，並在儲存模型時保存。  
  
-   **ElementMergeDirectives**。  每一個項目合併指示詞會控制另一個類別的不同執行個體加入父類別執行個體的方法。  您可以在本主題稍後找到項目合併指示詞的更多詳細資料。  
  
-   系統會針對 `Classes` 區段中所列出的每一個網域類別各產生一個 C\# 類別。  C\# 類別產生於 Dsl\\GeneratedCode\\DomainClasses.cs。  
  
### 屬性  
 每一個網域屬性都有名稱和類型。  該名稱在網域類別及其可轉移基底內必須是唯一的。  
  
 類型必須參考 `Types` 區段中列出的其中一個類型。  一般而言，Moniker 必須包括命名空間。  
  
```  
<DomainProperty Name="Name" DisplayName="Name"  DefaultValue="" Category="" IsElementName="true">  
  <Type>  
    <ExternalTypeMoniker Name="/System/String" />  
  </Type>  
</DomainProperty>  
```  
  
 每一個網域屬性 \(property\) 也可以具有下列屬性 \(attribute\)：  
  
-   **IsBrowsable**。  這個屬性 \(attribute\) 會在使用者按一下父類別的物件時，決定 \[屬性 \(property\)\] 視窗中是否出現屬性 \(property\)。  
  
-   **IsUIReadOnly**。  這個屬性 \(attribute\) 會決定使用者是否可以在 \[屬性 \(property\)\] 視窗中變更屬性 \(property\)，還是要透過其中存在該屬性 \(property\) 的裝飾項目來變更屬性 \(property\)。  
  
-   **Kind**。  您可以將此屬性設為 Normal、Calculated 或 CustomStorage。  如果將此屬性設為 Calculated，您必須提供可決定值的自訂程式碼，且該屬性將會是唯讀。  如果將此屬性設為 CustomStorage，您必須提供可取得並設定值的程式碼。  
  
-   **IsElementName**。  如果此屬性設為 true，在建立父類別的執行個體時，其值會自動設為唯一值。  此屬性 \(attribute\) 可以在每個類別中只針對一個屬性 \(property\) 設為 true，且此類別必須有字串類型。  在「元件圖」範例中，`NamedElement` 中的 `Name` 屬性將 `IsElementName` 設為 true。  每當使用者建立 `Component` 項目 \(繼承自 `NamedElement`\) 時，名稱會自動初始化為 "Component6" 之類的名稱。  
  
-   `DefaultValue`.  如果您已指定此屬性，則會針對此類別的新執行個體，將您指定的值指派給此屬性。  如果設定 `IsElementName`，DefaultValue 屬性會指定新字串的初始部分。  
  
-   在 \[屬性\] 視窗中，**分類**是其下將出現屬性的標頭。  
  
## 關聯性  
 `Relationships` 區段列出網域指定的語言中的所有關聯性。  每個 `Domain Relationship` 都是二進位且有向的，可連結來源類別的成員與目標類別的成員。  來源和目標類別通常是網域類別，但是也允許與其他關聯性產生關聯性。  
  
 例如，「連接」關聯性會將 OutPort 類別的成員連結到 InPort 類別的成員。  關聯性的每一個連結執行個體會將 OutPort 的執行個體連接到 InPort 的執行個體。  由於是多對多關聯性，因此每一個 OutPort 都可以有許多個來源在其中的 Connection 連結，且每一個 InPort 執行個體都可以有許多個以其為目標的 Connection 連結。  
  
### 來源和目標角色  
 每一個關聯性都包含具有下列屬性的來源和目標角色：  
  
-   `RolePlayer` 屬性參考連結之執行個體的網域類別：OutPort 適用於來源，InPort 適用於目標。  
  
-   `Multiplicity` 屬性有四個可能的值 \(ZeroMany、ZeroOne、One 和 OneMany\)。  此屬性參考可與一個角色扮演者相關聯的關聯性連結數。  
  
-   `PropertyName` 屬性指定角色扮演類別中用來存取位於另一端之物件的名稱。  此名稱在範本或自訂程式碼中用來周遊關聯性。  例如，來源角色的 `PropertyName` 屬性設為 `Targets`。  因此，下列程式碼將可運作：  
  
    ```  
    OutPort op = …; foreach (InPort ip in op.Targets) ...  
    ```  
  
     依照慣例，如果多重性為 ZeroMany 或 OneMany，則屬性名稱為複數。  
  
     角色的多重性是指可與此角色之每個執行個體相關聯的相反角色數。  例如，在關聯性 ComponentHasPorts 中，目標角色的 `RolePlayer` 屬性設為 Port，`PropertyName` 屬性設為 Component，`Multiplicity` 屬性設為 ZeroOne。  因此，使用此角色的適當程式碼為：  
  
    ```  
    ComponentPort p = …; Component c = p.Component; if (c != null) …  
    ```  
  
-   角色的 `Name` 是在 Relationship 類別內用來參考該連結端的名稱。  依照慣例，角色名稱一律為單數，因為每個連結在每一端都只有一個執行個體。  下列程式碼將可運作：  
  
    ```  
    Connection connectionLink = …; OutPort op = connectionLink.Source;  
    ```  
  
-   根據預設，`IsPropertyGenerator` 屬性設為 true。  如果它設為 false，則 Role Player 類別上不會建立任何屬性。  \(在該情況下，`op.Targets` \(舉例而言\) 將無法運作。\)  不過，如果自訂程式碼明確使用關聯性，仍然可以使用自訂程式碼周遊關聯性或取得連結本身的存取權：  
  
    ```  
    OutPort op = …; foreach (InPort ip in Connection.GetTargets(op)) …  
    foreach (Connection link in Connection.GetLinksToTargets(op)) …  
    ```  
  
### Relationship 屬性  
 除了可供所有類別使用的屬性和子節點之外，每個關聯性都具有以下屬性：  
  
-   **IsEmbedding**。  這個布林屬性指定關聯性是否為內嵌樹狀結構的一部分。  每個模型都必須以其內嵌關聯性形成樹狀結構。  因此，每個網域類別都必須是至少一個內嵌關聯性的目標，除非它是模型的根。  
  
-   **AllowsDuplicates**。  這個布林屬性預設為 false，僅適用於在來源和目標都具有 "many" 多重性的關聯性。  它決定語言使用者是否可以透過相同關聯性的多個連結來連接單一組來源和目標項目。  
  
## 設計工具和工具箱索引標籤  
 DslDefinition.dsl 檔之 \[設計工具\] 區段的主要部分為 **ToolboxTab** 項目。  一個設計工具可以具有數個項目，其中每個項目都代表產生的設計工具之 \[工具箱\] 中的開頭區段。  每個 **ToolboxTab** 項目可以包含一或多個 **ElementTool** 項目及\/或 **ConnectionTool** 項目。  
  
 項目工具可以建立特定網域類別的執行個體。  當使用者將項目工具拖曳到圖表上時，結果取決於本主題稍後關於項目合併指示詞的章節中所說明的項目合併指示詞。  
  
 每個連接工具都可以叫用特定的連接產生器。  一個連接產生器可以建立多種類型的關聯性，視使用者在何處按一下滑鼠而定，如連接產生器的相關章節所述。  
  
 沒有任何類型的工具會直接建構圖形或連接器。  每個工具都具現化網域類別或網域關聯性；然後 Shape 和 Connector 對應隨即決定該網域類別或網域關聯性如何顯示。  
  
## 路徑  
 網域路徑會出現在 DslDefinition.dsl 檔中的數個位置。  這些路徑會指定從模型中的一個項目到另一個項目的一連串連結 \(也就是網域指定語言的執行個體\)。  路徑語法簡單卻詳細。  
  
 路徑出現在 DslDefinition.dsl 檔的 `<DomainPath>…</DomainPath>` 標記中。  路徑可以巡覽多個連結，不過大部分的做法範例卻只周遊一個連結。  
  
 路徑由一連串的區段所組成。  每個區段都是從物件到連結或從連結到物件的一個躍點。  因此，躍點通常會在長路徑中交替。  第一個躍點是從物件到連結，第二個躍點是到位於連結另一端的物件，第三個躍點是到下一個連結，依此類推。  此順序偶然會出現例外，就是某關聯性本身就是另一個關聯性的來源或目標。  
  
 每一個區段都是以關聯性名稱做為開頭。  在物件到連結的躍點中，關聯性位於點和屬性名稱前面："`Relationship . Property`"。  在連結到物件的躍點中，關聯性位於驚嘆號和角色名稱前面："`Relationship ! Role`"。  
  
 「元件圖」範例包含 ShapeMap for InPort 的 ParentElementPath 中之路徑。  這個路徑的開頭如下所示：  
  
```  
    ComponentHasPorts.Component  
```  
  
 在本範例中，InPort 是 ComponentPort 的子類別，具有關聯性 ComponentHasPorts。  此屬性稱為 Component。  
  
 針對此模型撰寫 C\# 時，您可以在一個步驟中跳躍過一個連結，方法為使用關聯性在與它相關的每個類別上所產生的屬性：  
  
```  
     InPort port; ...  Component c = port.Component;  
```  
  
 不過，您必須在「路徑語法」中明確地執行兩個躍點。  由於此要求，您可以更輕鬆地存取中繼連結。  下列程式碼完成從連結到 Component 的躍點：  
  
```  
    ComponentHasPorts.Component / ! Component  
```  
  
 \(您可以省略關聯性名稱，它與前一個區段中的名稱相同。\)  
  
## 項目合併指示詞  
 當語言使用者將某個項目從 \[工具箱\] 拖曳到圖表上時，會建構該工具類別的執行個體。  此外，還會在該執行個體與現有的模型項目之間建立連結。  當語言使用者將某些項目 \(如元件或註解\) 從 \[工具箱\] 拖曳到圖表的空白部分時，就會建立這些項目。  當語言使用者將其他項目拖曳到其他主機項目時，就會建立其他項目。  例如，當語言使用者將 OutPort 或 InPort 拖曳到元件上時，就會建立它。  
  
 只有在可能的主機類別 \(如 Component\) 具有新項目之類別的項目合併指示詞時，該主機類別才會接受新項目。  例如，Name\="Component" 的 DomainClass 節點包含：  
  
```  
<DomainClass Name="Component" …> …  
    <ElementMergeDirective>  
      <Index>  
        <DomainClassMoniker Name="ComponentPort" />  
      </Index>  
      <LinkCreationPaths>  
        <DomainPath>ComponentHasPorts.Ports</DomainPath>  
      </LinkCreationPaths>  
    </ElementMergeDirective> …  
```  
  
 索引節點之下的類別 Moniker 參考可以接受的項目類別。  在這個案例中，ComponentPort 是 InPort 和 OutPort 的抽象基底類別。  因此，可以接受其中的任一項目。  
  
 ComponentModel 是語言的根類別，具有元件和註解的項目合併指示詞。  語言使用者可以直接將那些類別的項目拖曳到圖表上，因為圖表的空白部分代表根類別。  然而，ComponentModel 並沒有 ComponentPort 的項目合併指示詞。  因此，語言使用者無法直接將 InPorts 或 OutPorts 拖曳到圖表上。  
  
 項目合併指示詞會決定建立哪個或哪些連結，讓新項目可以整合或合併到現有模型中。  若是 ComponentPort，會建立 ComponentHasPorts 的執行個體。  DomainPath 會識別新項目將加入其中的父類別 Ports 的關聯性和屬性。  
  
 您可以併入多個連結建立路徑，即可在項目合併指示詞上建立多個連結。  必須內嵌其中一個路徑。  
  
 您可以在連結建立路徑中使用多個區段。  在此情況下，最後一個區段會定義必須建立的連結。  較早的區段會從父類別巡覽到應從其中建立新連結的物件。  
  
 例如，您可以將此項目合併指示詞加入 Component 類別：  
  
```  
<DomainClass Name="Component" …> …  
  <ElementMergeDirective>  
    <Index>  
       <DomainClassMoniker Name="Comment"/>  
    </Index>  
    <LinkCreationPaths>  
       <DomainPath>          ComponentModelHasComponents . ComponentModel / !ComponentModel         / ComponentModelHasComments.Comments       </DomainPath>  
       <DomainPath>CommentsReferenceComponents.Comments</DomainPath>  
    </LinkCreationPaths>  
  </ElementMergeDirective>  
```  
  
 然後語言使用者就可以將註解拖曳到元件上，並以元件的連結自動建立新註解。  
  
 第一個連結建立路徑從 `Component` 巡覽至 `ComponentModel`，然後建立內嵌關聯性 `ComponentModelHasComments` 的執行個體。  第二個連結建立路徑建立從主機 Component 到新 Comment 的參考關聯性 CommentsReferenceComponents 的連結。  所有連結建立路徑的開頭都必須是主機類別，且結尾都必須是一個連結，朝著新具現化的類別逐步邁進。  
  
## XmlClassData  
 每個網域類別 \(包括關聯性和其他子類型\) 都可以具有 `XmlClassData` 節點中提供的額外資訊，該節點出現在 DslDefinition.dsl 檔的 `XmlSerializationBehavior` 區段之下。  這項資訊特別著重在模型儲存至檔案時，類別的執行個體如何以序列化形式儲存。  
  
 `XmlSerializationBehavior` 所影響的大部分產生的程式碼位於 `Dsl\GeneratedCode\Serializer.cs` 中。  
  
 每個 `XmlClassData` 節點都包括以下子節點和屬性：  
  
-   Moniker 節點，此節點參考資料套用到的類別。  
  
-   類別上所定義之每個屬性的 **XmlPropertyData**。  
  
-   源自類別之每個關聯性的 **XmlRelationshipData**。  \(關聯性也有它們自己的 XmlClassData 節點。\)  
  
-   **TypeName** 字串屬性，決定所產生程式碼中的序列化協助程式類別之名稱。  
  
-   **ElementName** 字串，決定此類別之序列化執行個體的 XML 標記。  依照慣例，ElementName 通常與類別名稱相同，但是例外情形為第一個字母是小寫。  例如，模型檔案範例的開頭如下：  
  
    ```  
    <componentModel …  
    ```  
  
-   使用者的序列化模型檔案中的 **MonikerElementName**。  此屬性引進一個參考此類別的 Moniker。  
  
-   **MonikerAttributeName** 識別 Moniker 內的 XML 屬性名稱。  在使用者序列化檔案的這個片段中，網域指定語言的作者將 **MonikerElementName** 定義為 "inPortMoniker"，並將 **MonikerAttributeName** 定義為 "path"：  
  
    ```  
    <inPortMoniker path="//Component2/InPort1" />  
    ```  
  
### ConnectionBuilders  
 系統會為每個連接工具定義連接產生器。  每個連接產生器都由一或多個 LinkConnectDirective 項目所組成，其中每個項目都包含一或多個 SourceDirective 項目以及一或多個 TargetDirective 項目。  按一下連接工具之後，使用者可以從任何對應到模型項目 \(出現在 SourceDirective 項目清單中\) 的圖形啟動連接。  然後就可以在對應到項目 \(出現在 TargetDirective 項目清單中\) 的圖形上完成連接。  已具現化關聯性的類別取決於按照連接的啟動位置所指定的 LinkConnectDirective 項目。  
  
### XmlPropertyData  
 **DomainPropertyMoniker** 屬性會識別資料參考的屬性。  此屬性 \(attribute\) 必須是封入的 ClassData 類別之屬性 \(property\)。  
  
 **XmlName** 屬性提供 XML 中應顯示的對應屬性名稱。  依照慣例，此字串與屬性名稱相同，但是例外情形為第一個字母是小寫。  
  
 根據預設，**Representation** 屬性會設為 Attribute。  如果 **Representation** 設為 Element，則會在 XML 中建立子節點。  如果 **Representation** 設為 Ignore，則不會將屬性序列化。  
  
 **IsMonikerKey** 和 **IsMonikerQualifier** 屬性 \(attribute\) 授與屬性 \(property\) 識別父類別執行個體的角色。  您可以針對在類別中所定義的，或是由類別所繼承的一個屬性，將 **IsMonikerKey** 設為 true。  此屬性會識別父類別的個別執行個體。  您設為 `IsMonikerKey` 的屬性通常是名稱或其他索引鍵識別項。  例如，`Name` 字串屬性是 NamedElement 及其衍生類別的 Moniker 索引鍵。  當使用者將模型儲存到檔案時，此屬性必須包含每個執行個體的唯一值 \(在內嵌關聯性之樹狀結構中的同層級之間\)。  
  
 在序列化的模型檔案中，項目的完整 Moniker 是從模型根向下到內嵌關聯性之樹狀結構的路徑，引用每一個點上的 Moniker 索引鍵。  例如，InPorts 內嵌於元件內，而元件又內嵌於模型根。  因此，有效的 Moniker 為：  
  
```  
<inPortMoniker name="//Component2/InPort1" />  
```  
  
 您可以為字串屬性 \(property\) 設定 **IsMonikerQualifier** 屬性 \(attribute\)，並提供另一種建構項目完整名稱的方式。  例如，在 DslDefinition.dsl 檔中，**Namespace** 是 Moniker 限定詞。  
  
### XmlRelationshipData  
 在序列化的模型檔案內，連結 \(屬於內嵌和參考關聯性兩者\) 是由關聯性之來源端的子節點代表。  如果是內嵌關聯性，子節點包含子樹狀結構。  如果是參考關聯性，子節點包含參考樹狀結構之另一個部分的 Moniker。  
  
 **XmlClassData** 中的 **XmlRelationshipData** 屬性定義子節點在來源項目內的確切巢狀建構方式。  在網域類別上做為來源的每個關聯性都有一個 **XmlRelationshipData** 屬性。  
  
 **DomainRelationshipMoniker** 屬性會識別源自類別上的其中一個關聯性。  
  
 **RoleElementName** 屬性授與 XML 標記名稱，該名稱將子節點封入序列化資料。  
  
 例如，DslDefinition.dsl 檔包含：  
  
```  
<XmlClassData ElementName="component" …>  
  <DomainClassMoniker Name="Component" />  
  <ElementData>  
    <XmlRelationshipData RoleElementName="ports">  
      <DomainRelationshipMoniker Name="ComponentHasPorts" />  
    </XmlRelationshipData>  
```  
  
 因此，序列化的檔案包含：  
  
```  
<component name="Component1"> <!-- parent ->  
   <ports> <!-- role ->  
     <outPort name="OutPort1"> <!-- child element ->  
       …  
     </outPort>  
   </ports> …  
```  
  
 如果 **UseFullForm** 屬性設為 true，則會引進額外一層巢狀項目。  此圖層代表關聯性本身。  如果關聯性具有屬性 \(properties\)，則此屬性 \(attribute\) 必須設為 true。  
  
```  
<XmlClassData ElementName="outPort">  
   <DomainClassMoniker Name="OutPort" />  
   <ElementData>  
     <XmlRelationshipData UseFullForm="true" RoleElementName="targets">  
       <DomainRelationshipMoniker Name="Connection" />  
     </XmlRelationshipData>  
   </ElementData>  
 </XmlClassData>  
```  
  
 序列化的檔案包含：  
  
```  
<outPort name="OutPort1">  <!-- Parent ->  
   <targets>  <!-- role ->  
     <connection sourceRoleName="X">  <!-- relationship link ->  
         <inPortMoniker name="//Component2/InPort1" /> <!-- child ->  
     </connection>  
    </targets>  
  </outPort>  
```  
  
 \(連接關聯性具有自己的 XML 類別資料，該資料提供其項目和屬性名稱。\)  
  
 如果 **OmitElement** 屬性設為 true，則會省略將序列化的檔案予以縮寫的關聯性角色名稱，而在兩個類別有不超過一個關聯性時，該名稱是明確的。  例如：  
  
```  
<component name="Component3">  
  <!-- only one relationship could get here: ->  
  <outPort name="OutPort1">    
     <targets> …  
```  
  
### 序列化網域指定的語言定義  
 DslDefinition.dsl 檔本身是序列化的檔案，符合網域指定的語言定義。  下列是部分的 XML 序列化定義範例：  
  
-   **Dsl** 是 RootClass 節點以及圖表的類別。  DomainClass、DomainRelationship 和其他項目內嵌於 `Dsl` 之下。  
  
-   **類別**是網域指定的語言與 DomainClass 之間的關聯性之 **RoleElementName**。  
  
```  
<Dsl Name="CmptDsl5" …>  
  <Classes>  
    <DomainClass Name="NamedElement" InheritanceModifier="Abstract" …  
```  
  
-   **XmlSerializationBehavior** 屬性內嵌於 `Dsl` 屬性之下，但是 **OmitElement** 屬性已設定於內嵌關聯性上。  因此，沒有任何 `RoleElementName` 屬性介於其間。  相反地，**ClassData** 屬性是 **XmlSerializationBehavior** 屬性與 **XmlClassData** 屬性之間的內嵌關聯性之 `RoleElementName` 屬性。  
  
```  
<Dsl Name="CmptDsl5" …> …  
  <XmlSerializationBehavior Name="ComponentsSerializationBehavior" >  
    <ClassData>  
      <XmlClassData …>…</XmlClassData>  
      <XmlClassData …>…</XmlClassData>  
```  
  
-   ConnectorHasDecorators 是 `Connector` 與 `Decorator` 之間的內嵌關聯性。  `UseFullForm` 已設定，可讓關聯性名稱和連接器物件之每個連結的屬性清單一起顯示 。  不過，`OmitElement` 也已設定，這樣就沒有任何 `RoleElementName` 會封入內嵌於 `Connector` 內的多個連結：  
  
```  
<Connector Name="AssociationLink" …>  
  <ConnectorHasDecorators Position="TargetTop" …>  
    <TextDecorator Name="TargetRoleName"   />  
  </ConnectorHasDecorators>  
  <ConnectorHasDecorators Position="SourceTop" …>  
    <TextDecorator Name="SourceRoleName"   />  
  </ConnectorHasDecorators>  
</Connector>  
```  
  
## 圖形與連接器  
 圖形與連接器從網域類別繼承屬性和子節點，此外還有下列各項：  
  
-   `Color` 和 `Line` `Style` 屬性。  
  
-   **ExposesFillColorAsProperty** 以及數個類似屬性。  這些布林屬性會依使用者建立對應的屬性變數。  一般而言，當語言使用者按一下圖表上的圖形時，\[屬性\] 視窗上顯示的屬性就是該圖形對應到之網域類別執行個體的屬性。  如果 `ExposesFillColorAsProperty` 設為 true，則也會顯示圖形本身的屬性。  
  
-   **ShapeHasDecorators**。  每一個文字、圖示或展開\/摺疊裝飾項目都會發生此屬性的執行個體。  \(在 DslDefinition.dsl 檔中，`ShapeHasDecorators` 是 `UseFullForm` 設為 true 的關聯性。\)  
  
## 圖形對應  
 圖形對應會決定某個指定網域類別的執行個體如何顯示在畫面上，以圖形代表。  圖形和連接器對應都顯示在 DslDefinition.dsl 檔的 `Diagram` 區段之下。  
  
 在下列範例中，`ShapeMap` 項目最少具有網域類別的 Moniker、圖形的 Moniker，以及 `ParentElementPath` 項目：  
  
```  
<ShapeMap>  
  <DomainClassMoniker Name="InPort" />  
  <ParentElementPath>  
    <DomainPath>ComponentHasPorts.Component/!Component</DomainPath>  
  </ParentElementPath>  
  <PortMoniker Name="InPortShape" />  
</ShapeMap>  
```  
  
 `ParentElementPath` 項目的主要功能是讓物件的相同類別可以在不同的內容中顯示為不同的圖形。  例如，如果 `InPort` 也可以內嵌於註解，`InPort` 就可以針對該目的顯示為不同的圖形。  
  
 其次， 該路徑會決定圖形如何與其父系相關聯。  DslDefinition.dsl 檔中的圖形之間未定義任何內嵌結構。  您必須從圖形對應推斷該結構。  圖形的父系是對應到父項目路徑所識別之網域項目的圖形。  在這種情況下，該路徑會識別 `InPort` 所屬的元件。  在另一個圖形對應中，元件類別對應到 ComponentShape。  因此，新的 `InPort` 圖形成為其元件之 `ComponentShape` 的子圖形。  
  
 如果您改為將 InPort 圖形連結至圖表，父項目路徑必須為對應到圖表的元件模型採取另一個步驟：  
  
```  
ComponentHasPorts . Component / ! Component /    ComponentModelHasComponents . ComponentModel / ! ComponentModel  
```  
  
 該模型的根目錄沒有圖形對應。  改為直接從具有 `Class` 項目的圖表參考根目錄：  
  
```  
<Diagram Name="ComponentDiagram" >  
    <Class>  
      <DomainClassMoniker Name="ComponentModel" />  
    </Class>…  
```  
  
### 裝飾項目對應  
 裝飾項目對應會建立對應類別中的屬性與圖形上的裝飾項目之間的關聯。  如果屬性為列舉或布林類型，其值可以決定裝飾項目是否可見。  如果裝飾項目是文字裝飾項目，屬性的值可以出現，且使用者可以編輯它。  
  
### 區間圖形對應  
 區間圖形對應是圖形對應的子類型。  
  
## 連接器對應  
 最小連接器對應會參考連接器和關聯性：  
  
```  
<ConnectorMap>  
  <ConnectorMoniker Name="CommentLink" />  
  <DomainRelationshipMoniker Name="CommentsReferenceComponents" />  
</ConnectorMap>  
```  
  
 連接器對應也可以包含裝飾項目對應。  
  
## 請參閱  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/zh-tw/ca5e84cb-a315-465c-be24-76aa3df276aa)   
 [如何定義網域指定的語言](../modeling/how-to-define-a-domain-specific-language.md)   
 [了解模型、類別和關聯性](../modeling/understanding-models-classes-and-relationships.md)