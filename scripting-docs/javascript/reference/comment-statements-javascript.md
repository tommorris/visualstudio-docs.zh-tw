---
title: "註解陳述式 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Comment_JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "註解陳述式"
  - "註解, 忽略"
ms.assetid: b604824f-ac17-49d3-bcdb-2a893ab5fff8
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 註解陳述式 (JavaScript)
會導致 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 剖析器忽略註解。  
  
## 語法  
  
```  
Single-line Comment:  
// comment   
```  
  
```  
Multiline Comment:  
/*  
comment  
*/  
```  
  
```  
Comments with conditional compilation:  
//@CondStatement   
  
/*@  
condStatement  
@*/  
```  
  
## 備註  
 `comment` 引數是您想要在指令碼中包含的任何註解文字。  如果啟用條件式編譯，則會使用 `condStatement` 引數。  如果使用單行註解，則 "\/\/" 和 "@" 字元之間不能有空格。  
  
 使用註解來防止 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 剖析器讀取指令碼之某些部分。  您可以使用註解，在程式中包含說明備註。  
  
 如果使用單行註解，此剖析器會忽略註解標記與該行結尾之間的任何文字。  如果使用多行註解，此剖析器會忽略開頭和結尾標記之間的任何文字。  
  
 註解可用來支援條件式編譯，同時保留與不支援該功能的瀏覽器的相容性。  這些瀏覽器分別將這些形式的註解視為單行或多行註解。  
  
## 範例  
 下列範例說明最常見的註解用法。  
  
```javascript  
/* This is a multiline comment that  
    can span as many lines as necessary.  */  
function myfunction(arg1, arg2){  
    var r;  
    // This is a single line comment.  
    r = arg1 + arg2  
    return(r);  
}  
```  
  
## 範例  
 下列範例示範如何使用條件式編譯。  這個範例使用特殊的註解分隔符號，只有在條件式編譯是由 `@cc_on` 陳述式啟用時才會使用這些分隔符號。  不支援條件式編譯的指令碼引擎只會看到表示不支援條件式編譯的訊息。  
  
```javascript  
/*@cc_on @*/  
/*@if (@_jscript_version >= 4)  
    alert("JavaScript version 4 or better");  
    @else @*/  
    alert("Conditional compilation not supported by this scripting engine.");  
/*@end @*/  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]