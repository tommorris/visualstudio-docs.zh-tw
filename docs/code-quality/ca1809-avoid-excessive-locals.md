---
title: CA1809：避免使用過多區域變數
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: be8dcc47e5df5970b2beea697173debcc4a1671f
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549792"
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809：避免使用過多區域變數
|||
|-|-|
|TypeName|AvoidExcessiveLocals|
|CheckId|CA1809|
|類別|Microsoft.Performance|
|中斷變更|非重大|

## <a name="cause"></a>原因
 成員包含超過 64 個區域變數，其中有些可能是編譯器所產生。

## <a name="rule-description"></a>規則描述
 常見的效能最佳化作法是將值儲存在處理器暫存器而不是在記憶體中，這指*註冊 (enregistering)* 值。 Common language runtime 會視為最多 64 個區域變數 enregistration。 不是機率的變數會放在堆疊上，並且必須移至操作之前暫存器。 若要允許機會所有區域變數都能註冊、 限制為 64 的本機變數數目。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，將實作重構為使用最多 64 個區域變數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 則隱藏這項規則的警告，或停用規則，如果效能不成問題。

## <a name="related-rules"></a>相關的規則
 [CA1804：必須移除未使用的區域變數](../code-quality/ca1804-remove-unused-locals.md)