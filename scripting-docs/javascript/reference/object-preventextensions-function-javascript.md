---
title: "Object.preventExtensions 函式 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Object.preventExtensions 函式 [JavaScript]"
  - "preventExtensions 函式 [JavaScript]"
  - "防止新增屬性 [JavaScript]"
  - "屬性 [JavaScript], 防止新增"
ms.assetid: e6b48197-2374-4437-a9fe-519dd45a2077
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Object.preventExtensions 函式 (JavaScript)
避免將新的屬性加入至物件。  
  
## 語法  
  
```javascript  
Object.preventExtensions(object)  
```  
  
#### 參數  
 `object`  
 必要項。  要設為無法擴充的物件。  
  
## 傳回值  
 傳遞給函式的物件。  
  
## 例外狀況  
 如果 `object` 不是物件，就會擲回 `TypeError` 例外狀況。  
  
## 備註  
 `Object.preventExtensions` 函式會讓物件無法擴充，這樣新的具名屬性便無法加入其中。  當物件設為無法擴充之後，就不能將它設為可擴充。  
  
 如需如何設定屬性 \(Property\) 的屬性 \(Attribute\) 的詳細資訊，請參閱 [Object.defineProperty 函式](../../javascript/reference/object-defineproperty-function-javascript.md)。  
  
## 相關函式  
 以下相關函式可防止修改物件屬性。  
  
|函式|物件設為無法擴充|`configurable` 針對每個屬性設定為 `false`|`writable` 針對每個屬性設定為 `false`|  
|--------|--------------|--------------------------------------|----------------------------------|  
|`Object.preventExtensions`|是|否|否|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|是|是|否|  
|[Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|是|是|是|  
  
 如果下表中所有標記的條件都成立，則下列函式會傳回 `true`。  
  
|函式|物件可擴充嗎？|所有屬性的 `configurable` 都是 `false` 嗎？|所有資料屬性的 `writable` 都是 `false` 嗎？|  
|--------|-------------|----------------------------------------|--------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|是|否|否|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|否|是|否|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|否|是|是|  
  
## 範例  
 以下範例說明 `Object.preventExtensions` 函式的用法。  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Make the object non-extensible.  
Object.preventExtensions(obj);  
document.write(Object.isExtensible(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.  
obj.newProp = 50;  
document.write(obj.newProp);  
  
// Output:  
// false  
// undefined  
  
```  
  
## 需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 請參閱  
 [Object.seal 函式](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.freeze 函式](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible 函式](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed 函式](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen 函式](../../javascript/reference/object-isfrozen-function-javascript.md)