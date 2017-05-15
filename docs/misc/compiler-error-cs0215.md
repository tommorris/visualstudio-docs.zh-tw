---
title: "編譯器錯誤 CS0215 | Microsoft Docs"
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
  - "CS0215"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0215"
ms.assetid: 2060440d-be22-4c10-8b26-43b08b615447
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0215
運算子 True 或 False 的傳回類型必須為 bool  
  
 使用者定義的 [true](/dotnet/csharp/language-reference/keywords/true) 和 [false](/dotnet/csharp/language-reference/keywords/false) 運算子必須具有傳回類型 [bool](/dotnet/csharp/language-reference/keywords/bool)。 如需詳細資訊，請參閱[多載運算子](/dotnet/csharp/programming-guide/statements-expressions-operators/overloadable-operators)。  
  
 下列範例會產生 CS0215：  
  
```  
// CS0215.cs class MyClass { public static int operator true (MyClass MyInt)   // CS0215 // try the following line instead // public static bool operator true (MyClass MyInt) { return true; } public static int operator false (MyClass MyInt)   // CS0215 // try the following line instead // public static bool operator false (MyClass MyInt) { return true; } public static void Main() { } }  
```