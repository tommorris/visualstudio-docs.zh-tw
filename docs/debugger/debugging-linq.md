---
title: "偵錯 LINQ | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "偵錯, LINQ"
  - "LINQ, 偵錯"
  - "LINQ, 編輯後繼續"
  - "LINQ, 逐步執行"
  - "LINQ, 在偵錯工具中檢視結果"
ms.assetid: dbae26cb-ac5f-4312-b474-b9f29714f4c6
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 偵錯 LINQ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 支援 Language Integrated Query \(LINQ\) 程式碼偵錯，但有一些限制。大部分偵錯功能都可以使用 LINQ 陳述式，包括逐步執行、設定中斷點，以及在偵錯工具視窗中檢視結果。  本主題將描述 LINQ 偵錯的主要限制。  
  
## 本主題內容  
 [檢視 LINQ 結果](../debugger/debugging-linq.md#BKMK_ViewingLINQResults)  
  
 [逐步執行和 LINQ](../debugger/debugging-linq.md#BKMK_SteppingAndLinq)  
  
 [LINQ 不支援編輯後繼續](../debugger/debugging-linq.md#BKMK_EditandContinueNotSupportedforLINQ)  
  
##  <a name="BKMK_ViewingLINQResults"></a> 檢視 LINQ 結果  
 藉由使用資料提示方塊、\[監看式\] 視窗和 \[快速監看式\] 對話方塊，您可以檢視 LINQ 陳述式的結果。  使用來源視窗時，您可以將指標暫停在來源視窗中的查詢上，則資料提示方塊會隨即出現。  您可以複製 LINQ 變數並張貼到 \[監看式\] 視窗或 \[快速監看式\] 對話方塊。  
  
 在 LINQ 中，建立或宣告查詢時並不會進行評估，只有在使用查詢時才會評估。  因此，直到評估前查詢都不會有值。  如需查詢建立和評估的完整說明，請參閱 [Introduction to LINQ Queries \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)或[撰寫第一個 LINQ 查詢](/dotnet/visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query)。  
  
 若要顯示查詢結果，偵錯工具必須進行評估。  在偵錯工具中檢視 LINQ 查詢結果時發生的這個隱含評估，會帶來一些您需要考慮的影響：  
  
-   每個查詢評估會耗費些許時間。  展開結果節點也會耗用時間。  對於有些查詢，重複的評估可能會導致可觀的效能傷害。  
  
-   評估查詢可能造成的副作用，會隨資料值或是程式的狀態而變更。  並不是所有的查詢都有副作用。  若要判斷查詢是否能夠安全通過評估而不會發生副作用，您必須了解實作查詢的程式碼。  
  
##  <a name="BKMK_SteppingAndLinq"></a> 逐步執行和 LINQ  
 進行 LINQ 程式碼偵錯時，您應該了解逐步執行的一些行為差異。  
  
### LINQ to SQL  
 在 LINQ to SQL 查詢中，偵錯工具無法控制述詞 \(Predicate\) 程式碼。  因此，您無法逐步執行述詞程式碼。  任何編譯成運算式樹狀架構的查詢所造成的程式碼，都無法由偵錯工具控制。  
  
### Visual Basic 中的逐步執行  
 在 Visual Basic 程式中逐步執行且偵錯工具遇到查詢宣告時，並不會逐步執行該宣告，而會將整個宣告反白顯示為單一陳述式。  這種行為的發生，是因為查詢是等到被呼叫時才會評估的  如需詳細資訊，請參閱[Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)。  
  
 如果逐步執行下列範例程式碼，偵錯工具會將查詢宣告或查詢建立反白顯示為單一陳述式。  
  
```  
Function MyFunction(ByVal x As Char)  
    Return True  
End Function  
  
Sub Main()  
    'Query creation  
    Dim x = From it In "faoaoeua" _  
            Where MyFunction(it) _  
            Select New With {.a = it}  
  
    ' Query execution  
    For Each cur In x  
        Console.WriteLine(cur.ToString())  
    Next  
End Sub  
```  
  
 再度逐步執行時，偵錯工具會反白顯示 `For Each cur In x`。  下一個逐步執行動作中，會進入函式 `MyFunction`。  逐步執行完 `MyFunction` 後，會跳回 `Console.WriteLine(cur.ToSting())`。  沒有任何一點會讓偵錯工具逐步執行查詢宣告中的述詞程式碼，雖然偵錯工具確實會評估該程式碼。  
  
### 使用函式取代述詞以啟用逐步執行 \(Visual Basic\)  
 如果基於偵錯目的而必須逐步執行述詞程式碼，您可以藉由呼叫包含原始述詞程式碼的函式來取代述詞。  例如，假設您有下段程式碼：  
  
```  
Dim items() as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}  
  
' Get the even numbers  
Dim query = From nextInt in items Where nextInt Mod 2 = 0 Select nextInt  
  
For each item in query  
      Console.WriteLine(item)  
Next  
```  
  
 您可以將述詞程式碼移到新的函式，名為 `IsEven`：  
  
```  
Dim items () as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}  
  
' Get the even numbers  
Dim query = From nextInt in items Where IsEven(nextInt) Select nextInt  
  
For each item in query  
      Console.WriteLine(item)  
Next  
...   
Function IsEven(item As =Integer) as Boolean  
      Return item Mod 2 = 0  
End Function  
```  
  
 修訂的查詢每回會透過 `items` 呼叫函式 `IsEven`。  您可以使用偵錯工具視窗查看每個項目是否符合指定狀況，而且可以逐步執行 `IsEven` 中的程式碼。  這個範例中的述詞相當簡單。  但是，當您必須偵錯更為複雜的述詞時，這個技巧就很好用。  
  
##  <a name="BKMK_EditandContinueNotSupportedforLINQ"></a> LINQ 不支援編輯後繼續  
 \[編輯後繼續\] 並不支援 LINQ 查詢的變更。  如果在偵錯工作階段期間加入、移除或變更 LINQ 陳述式，會出現對話方塊告訴您 \[編輯後繼續\] 並不支援該變更。  此時，您可以復原變更，或者是停止偵錯工作階段並使用編輯過的程式碼重新啟動新的工作階段。  
  
 除此之外，\[編輯後繼續\] 也不支援 LINQ 陳述式中所使用變數型別或值的變更。  同樣地，您可以復原變更，或者是停止並重新啟動偵錯工作階段。  
  
 在 C\# 中，您不能對包含 LINQ 查詢的方法中的任何程式碼使用 \[編輯後繼續\]。  
  
 在 Visual Basic 中，您可以對非 LINQ 程式碼使用 \[編輯後繼續\]，即使程式碼是在包含 LINQ 查詢的方法中。  您可以在 LINQ 陳述式前加入或移除程式碼，即使這些變更會影響到 LINQ 查詢的行號。  對非 LINQ 程式碼的 Visual Basic 偵錯體驗，與沒有採用 LINQ 前是相同的。  您無法變更、加入或移除 LINQ 查詢，除非您打算停止偵錯以套用變更。  
  
## 請參閱  
 [Debugging SQL](http://msdn.microsoft.com/zh-tw/f27c17e6-1d90-49f2-9fc0-d02e6a27f109)   
 [副作用和運算式](../Topic/Side%20Effects%20and%20Expressions.md)   
 [使用偵錯工具管理例外狀況](../debugger/managing-exceptions-with-the-debugger.md)   
 [Introduction to LINQ Queries \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)   
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)