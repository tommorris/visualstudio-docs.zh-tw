---
title: DA0010：GetHashCode 高度耗費資源 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a670eb3145f3fd2ab9478dc68e0490cdeda8ac56
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749956"
---
# <a name="da0010-expensive-gethashcode"></a>DA0010：GetHashCode 高度耗費資源
|||  
|-|-|  
|規則 ID|DA0010|  
|分類|.NET Framework 使用方式|  
|分析方法|取樣<br /><br /> .NET 記憶體|  
|訊息|GetHashCode 函式應該便宜，而且不會配置任何記憶體。 盡可能降低雜湊碼函式的複雜度。|  
|訊息類型|警告|  
  
## <a name="cause"></a>原因  
 類型的 GetHashCode 方法呼叫大部分是分析資料，或方法會配置記憶體。  
  
## <a name="rule-description"></a>規則描述  
 雜湊是一種技術，可快速尋找大型集合中的特定項目。 因為雜湊表可能很龐大，而且必須支援極高的存取率，所以雜湊表應該很有效率。 這項需求的含意在於 .NET Framework 中的 GetHashCode 方法不應該配置記憶體。 配置記憶體時會增加記憶體回收行程的負載，而且在因配置要求而需要執行記憶體回收時公開潛在延遲方法。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 降低方法的複雜性。