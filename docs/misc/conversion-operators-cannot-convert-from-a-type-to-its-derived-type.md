---
title: "轉換運算子無法從類型轉換為其衍生類型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc33027"
  - "bc33027"
helpviewer_keywords: 
  - "BC33027"
ms.assetid: 861954f2-f563-4234-af84-bdd02f39979b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 轉換運算子無法從類型轉換為其衍生類型
轉換運算子是以衍生自參數類型的傳回類型進行宣告。  
  
 在編譯時期，[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 會考慮存在從任何參考類型到其繼承階層架構中任何類型的預先定義轉換 \(亦即，從中衍生的任何類型，或從它衍生的任何類型\)。 這類轉換可能會在執行階段失敗，但編譯器無法預測執行階段結果，因此它可以編譯任何這類轉換。  
  
 因為編譯器認為已定義這項轉換，所以不允許您重新定義它。  
  
 **錯誤 ID︰**BC33027  
  
### 更正這個錯誤  
  
-   請完整移除這個運算子定義。 它已預先定義。  
  
## 請參閱  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)