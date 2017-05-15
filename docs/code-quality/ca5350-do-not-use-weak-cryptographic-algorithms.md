---
title: "CA5350: 請勿使用弱式密碼編譯演算法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c51bb8a-fcfa-46aa-ab61-634be84c4a7a
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA5350: 請勿使用弱式密碼編譯演算法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseWeakCryptographicAlgorithms|  
|CheckId|CA5350|  
|分類|Microsoft.Cryptography|  
|中斷變更|非中斷|  
  
> [!NOTE]
>  上次於 2015 年 11 月更新此警告。  
  
## 原因  
 例如 <xref:System.Security.Cryptography.TripleDES> 的加密演算法，和例如 <xref:System.Security.Cryptography.SHA1> 及 <xref:System.Security.Cryptography.RIPEMD160> 的雜湊演算法，被視為弱式。  
  
 這些密碼編譯演算法提供的安全性保證不像更新的同類型演算法那麼多。 密碼編譯雜湊演算法 <xref:System.Security.Cryptography.SHA1> 和 <xref:System.Security.Cryptography.RIPEMD160> 提供的衝突防禦比更新的雜湊演算法少。 加密演算法 <xref:System.Security.Cryptography.TripleDES> 提供比更新的加密演算法較少的安全性位元。  
  
## 規則描述  
 現今，弱式加密演算法和雜湊函式用於多種原因，但它們不應該用來保證所保護資料的機密性。  
  
 此規則會在它在程式碼中發現 3DES、SHA1 或 RIPEMD160 演算法時觸發，並擲回警告給使用者。  
  
## 如何修正違規  
 使用密碼編譯較強的選項：  
  
-   若為 TripleDES 加密，請使用 <xref:System.Security.Cryptography.Aes> 加密。  
  
-   若為 SHA1 或 RIPEMD160 雜湊函式，請使用 [SHA\-2](https://msdn.microsoft.com/en-us/library/windows/desktop/aa382459.aspx) 系列 \(例如 <xref:System.Security.Cryptography.SHA512>、<xref:System.Security.Cryptography.SHA384>、<xref:System.Security.Cryptography.SHA256>\)。  
  
## 隱藏警告的時機  
 當資料所需的保護層級不需要安全性保證時，隱藏此規則的警告。  
  
## 虛擬程式碼範例  
 在本文撰寫之時，下列虛擬程式碼範例說明這個規則偵測到的模式。  
  
### SHA\-1 雜湊違規  
  
```  
using System.Security.Cryptography; ... var hashAlg = SHA1.Create();  
  
```  
  
### 方案  
  
```  
using System.Security.Cryptography; ... var hashAlg = SHA256.Create();  
  
```  
  
### RIPEMD160 雜湊違規  
  
```  
using System.Security.Cryptography; ... var hashAlg = RIPEMD160Managed.Create();  
  
```  
  
### 方案  
  
```  
using System.Security.Cryptography; ... var hashAlg = SHA256.Create();  
  
```  
  
### TripleDES 加密違規  
  
```  
using System.Security.Cryptography; ... using (TripleDES encAlg = TripleDES.Create()) { ... }  
```  
  
### 方案  
  
```  
using System.Security.Cryptography; ... using (AesManaged encAlg = new AesManaged()) { ... }  
```