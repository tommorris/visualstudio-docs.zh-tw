---
title: "SccGetUserOption 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGetUserOption"
helpviewer_keywords: 
  - "SccGetUserOption 函式"
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# SccGetUserOption 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函式會擷取各種不同的使用者特定的選項。  
  
## 語法  
  
```cpp  
SCCRTN SccGetUserOption(  
   LPVOID pContext,  
   LONG nOption,  
   LPLONG lpVal  
);  
```  
  
#### 參數  
 pContext  
 \[\] in原始檔控制外掛程式的內容指標。  
  
 nOption  
 \[\] in要擷取 \(如可能的選項，請參閱 \< 備註 \>\) 的選項。  
  
 lpVal  
 \[\] out與選項相關聯的值。  
  
## 傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|已成功擷取選項。|  
|SCC\_E\_OPNOTSUPPORTED|不支援選項。|  
|SCC\_E\_NONSPECIFICERROR|發生意外的錯誤。|  
  
## 備註  
 此命令支援下列選項:  
  
|使用者選項|描述|  
|-----------|--------|  
|`SCC_USEROPT_CHECKOUT_LOCALVER`|決定使用者是否想要簽出檔案的本機版本。`lpVal` 指派 `SCC_USEROPT_COLV_YES` \(使用者想要簽出本機檔案\) 或 `SCC_USEROPT_COLV_NO`。|  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [錯誤代碼](../extensibility/error-codes.md)