---
title: "MSBuild 錯誤 MSB3156 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.ProductValidation"
helpviewer_keywords: 
  - "MSB3156"
ms.assetid: 98b1bd42-9efe-44a2-8a43-476edc03590d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3156
**MSB3156: 位於 '\<folder\>' 的項目 '\<package\>' 未通過 Xml 驗證。**  
  
 如果資訊清單 \(特別是 product.xml\) 沒有通過 XML 驗證，就會產生這個警告訊息。  後續的錯誤訊息中 \([MSBuild 錯誤 MSB3159](/visual-cpp/misc/msbuild-error-msb3159) 或 [MSBuild 錯誤 MSB3160](../misc/msbuild-error-msb3160.md)\) 會列出特定問題。  
  
### 若要更正這個錯誤  
  
-   解決後續的錯誤訊息中所列出的資訊清單驗證問題。  
  
## 請參閱  
 [產品和封裝結構描述參考](../deployment/product-and-package-schema-reference.md)   
 [\<PackageFiles\> 項目](../deployment/packagefiles-element-bootstrapper.md)