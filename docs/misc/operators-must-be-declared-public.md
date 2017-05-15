---
title: "運算子必須宣告為 &#39;Public&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc33011"
  - "bc33011"
helpviewer_keywords: 
  - "BC33011"
ms.assetid: 67fc0dee-4ef5-4afc-a63a-f7d20bce7954
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 運算子必須宣告為 &#39;Public&#39;
[Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement) 不包含 [Public](/dotnet/visual-basic/language-reference/modifiers/public) 關鍵字。  
  
 `Operator` 程序需要 `Public` 和 [Shared](/dotnet/visual-basic/language-reference/modifiers/shared) 兩個關鍵字，且轉換運算子也需要 [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) 或 [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing) 關鍵字。  
  
 **錯誤 ID：**BC33011  
  
### 更正這個錯誤  
  
-   將 `Public` 關鍵字加入 `Operator` 陳述式。  
  
## 請參閱  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)