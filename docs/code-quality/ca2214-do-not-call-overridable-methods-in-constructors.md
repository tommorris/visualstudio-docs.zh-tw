---
title: CA2214：不要呼叫建構函式中的可覆寫方法
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ddc827e77b37de6490cb4bee081748f317865b57
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549556"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214：不要呼叫建構函式中的可覆寫方法

|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|類別|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因

非密封類型的建構函式會呼叫其類別中定義的虛擬方法。

## <a name="rule-description"></a>規則描述

呼叫虛擬方法時，執行階段之前將不會選取實際執行方法的型別。 當建構函式呼叫虛擬方法時，就可能會叫用方法的執行個體的建構函式尚未執行。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請勿呼叫類型的虛擬方法的型別之建構函式中。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。 建構函式應該重新設計，以消除呼叫虛擬方法。

## <a name="example"></a>範例

下列範例會示範違反此規則的效果。 測試應用程式建立的執行個體`DerivedType`，因而導致其基底類別 (`BadlyConstructedType`) 建構函式來執行。 `BadlyConstructedType`建構函式不正確地呼叫虛擬方法`DoSomething`。 如輸出所示`DerivedType.DoSomething()`執行，並因此之前`DerivedType`的建構函式執行。

[!code-csharp[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
[!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]

這個範例會產生下列輸出：

```txt
Calling base ctor.
Derived DoSomething is called - initialized ? No
Calling derived ctor.
```