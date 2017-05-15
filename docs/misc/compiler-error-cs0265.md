---
title: "編譯器錯誤 CS0265 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0265"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0265"
ms.assetid: d43d19c2-8a66-4bb1-95a0-557b0a29bce1
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0265
'type' 的部分宣告對類型參數 'type parameter' 有不一致的條件約束  
  
 如果您定義泛型類別作為部分類別，而讓其部分定義出現在多個位置，而且兩個以上位置中的泛型類型條件約束不一致或不同，則會發生這個錯誤。 如果您在多個位置指定條件約束，則它們都必須要相同。 最簡單的解決方法是在一個位置指定條件約束，其他位置則予以省略。 如需詳細資訊，請參閱 [部分類別和方法](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods) 與 [類型參數的條件約束](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)。  
  
 下列程式碼會產生錯誤 CS0265。  
  
## 範例  
 在這個程式碼中，部分類別定義都在單一檔案中，但它們也可以分散到多個檔案中。  
  
```  
// CS0265.cs public class GenericsErrors { interface IFace1 { } interface IFace2 { } partial class PartialBadBounds<T> where T : IFace1 { } // CS0265 partial class PartialBadBounds<T> where T : IFace2 { } }  
```