---
title: "逐步解說：偵錯 XSLT 樣式表 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# 逐步解說：偵錯 XSLT 樣式表
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此逐步教學中的步驟示範如何使用 XSLT 偵錯工具。這些步驟包括檢視變數、設定中斷點及逐步執行程式碼。樣式表會尋找低於書籍價格平均值的所有書籍。  
  
### 準備此逐步教學  
  
1.  關閉任何開啟的解決方案。  
  
2.  將兩個範例檔案複製到本機電腦。  
  
## 開始偵錯  
  
#### 開始偵錯  
  
1.  從 \[檔案\] 功能表中指向 \[開啟\]，再按一下 \[檔案\]。  
  
2.  找出 belowAvg.xsl 檔案，再按一下 \[開啟\]。  
  
     樣式表會在 XML 編輯器中開啟。  
  
3.  按一下文件屬性視窗中 \[輸入\] 欄位上的瀏覽按鈕 \(**...**\)。  
  
4.  找出 books.xml 檔案，再按一下 \[開啟\]。  
  
     這會設定用於 XSLT 轉換的來源文件檔案。  
  
5.  在 `xsl:if` 開始標記上按一下滑鼠右鍵，並指向 \[中斷點\] 後，再按一下 \[插入中斷點\]。  
  
6.  在 \[XML 編輯器\] 工具列上，按一下 \[偵錯 XSL\] 按鈕。  
  
 這會啟動偵錯處理，並開啟偵錯工具所使用的幾個新視窗。  
  
 顯示輸入文件與樣式表的視窗有兩個。偵錯工具會使用這些視窗來顯示目前的執行狀態。偵錯工具定位於樣式表的 `xsl:if` 項目上，以及 books.xml 檔的第一個書籍節點上。  
  
 \[本機\] 視窗會顯示所有區域變數及其目前的值。其中包括在樣式表中定義的變數，及偵錯工具用來追蹤目前內容中之節點的變數。  
  
 \[XSL 輸出\] 視窗會顯示 XSL 轉換的輸出。此視窗與 \[Visual Studio 輸出\] 視窗是分開的。  
  
## 監看式視窗  
  
#### 使用 \[監看式\] 視窗  
  
1.  從 \[偵錯\] 功能表中，依序指向 \[視窗\] 及 \[監看式\] 後，再按一下 \[監看式 1\]。  
  
     這樣可讓 \[監看式 1\] 視窗可見。  
  
2.  在 \[名稱\] 欄位中輸入 `$bookAverage`，再按 ENTER 鍵。  
  
     `$bookAverage` 變數的值會顯示於視窗中。  
  
3.  在 \[名稱\] 欄位中輸入 `self::node()`，再按 ENTER 鍵。  
  
     `self::node()` 是一種 XPath 運算式，可評估目前的內容節點。`self::node()` XPath 運算式的值為第一個書籍節點。它會隨著轉換的進行而變更。  
  
4.  展開 `self::node()` 節點，然後展開 `price` 節點。  
  
     這樣可讓您查看書籍價格的值，而且可以輕鬆將其與 `$bookAverage` 值進行比較。因為書籍價格低於平均值，所以 `xsl:if` 條件應該會成功。  
  
## 逐步執行程式碼  
 偵錯工具可讓您逐行執行程式碼。  
  
#### 逐步執行程式碼  
  
1.  按 **F5** 以繼續。  
  
     因為第一個書籍節點滿足 `xsl:if` 條件，所以會將該書籍節點加入至 \[XSL 輸出視窗\]。偵錯工具繼續執行，直到其再次定位於樣式表的 `xsl:if` 項目上為止。偵錯工具現在定位於 books.xml 檔的第二個書籍節點上。  
  
     在 Watch1 視窗中，`self::node()` 值會變更為第二個書籍節點。藉由檢查價格項目的值，您可以確定價格高於平均值，因此 `xsl:if` 條件應該會失敗。  
  
2.  按 **F5** 以繼續。  
  
     因為第二個書籍節點與 `xsl:if` 條件不符，所以不會將該書籍節點加入至 \[XSL 輸出視窗\]。偵錯工具繼續執行，直到其再次定位於樣式表的 `xsl:if` 項目上為止。偵錯工具現在定位於 books.xml 檔的第三個 `book` 節點上。  
  
     在 Watch1 視窗中，`self::node()` 值會變更為第三個書籍節點。藉由檢查 `price` 項目的值，您可以確定價格低於平均值，因此 `xsl:if` 條件應該會成功。  
  
3.  按 **F5** 以繼續。  
  
     因為已滿足 `xsl:if` 條件，所以會將第三本書加入至 \[XSL 輸出\] 視窗。當處理過 XML 文件中的所有書籍後，偵錯工具會停止。  
  
## 範例檔案  
 逐步教學會使用下列兩個檔案。  
  
### belowAvg.xsl  
  
```  
<?xml version='1.0'?>  
<xsl:stylesheet version="1.0"  
      xmlns:xsl="http://www.w3.org/1999/XSL/Transform">  
  <xsl:output method="xml" encoding="utf-8"/>  
  <xsl:template match="/">  
    <xsl:variable name="bookCount" select="count(/bookstore/book)"/>  
    <xsl:variable name="bookTotal" select="sum(/bookstore/book/price)"/>  
    <xsl:variable name="bookAverage" select="$bookTotal div $bookCount"/>  
    <books>  
      <!--Books That Cost Below Average-->  
      <xsl:for-each select="/bookstore/book">  
        <xsl:if test="price < $bookAverage">  
          <xsl:copy-of select="."/>  
        </xsl:if>  
      </xsl:for-each>  
    </books>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### books.xml  
  
```  
<?xml version='1.0'?>  
<!-- This file represents a fragment of a book store inventory database -->  
<bookstore>  
  <book genre="autobiography" publicationdate="1981" ISBN="1-861003-11-0">  
    <title>The Autobiography of Benjamin Franklin</title>  
    <author>  
      <first-name>Benjamin</first-name>  
      <last-name>Franklin</last-name>  
    </author>  
    <price>8.99</price>  
  </book>  
  <book genre="novel" publicationdate="1967" ISBN="0-201-63361-2">  
    <title>The Confidence Man</title>  
    <author>  
      <first-name>Herman</first-name>  
      <last-name>Melville</last-name>  
    </author>  
    <price>11.99</price>  
  </book>  
  <book genre="philosophy" publicationdate="1991" ISBN="1-861001-57-6">  
    <title>The Gorgias</title>  
    <author>  
      <name>Plato</name>  
    </author>  
    <price>9.99</price>  
  </book>  
</bookstore>  
```  
  
## 請參閱  
 [偵錯 XSLT](../xml-tools/debugging-xslt.md)