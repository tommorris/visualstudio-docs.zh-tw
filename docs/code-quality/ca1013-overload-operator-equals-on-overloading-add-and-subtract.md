---
title: CA1013：多載加號和減號運算子時必須一併多載等號比較運算子
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
helpviewer_keywords:
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
ms.assetid: 5bd28d68-c179-49ff-af47-5250b8b18a10
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e8f0f3d40ea24828430983efd2cf39f4fa399238
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547720"
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013：多載加號和減號運算子時必須一併多載等號比較運算子

|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|CheckId|CA1013|
|類別|Microsoft.Design|
|中斷變更|非重大|

## <a name="cause"></a>原因
 公用或保護的類型會實作加法或減法運算，但不會實作等號比較運算子。

## <a name="rule-description"></a>規則描述
 型別的執行個體可以結合使用加法和減法之類的作業，您幾乎都應該定義要傳回的等號比較`true`組成的值也相同，任何兩個執行個體。

 您無法使用預設等號比較運算子多載等號比較運算子的實作中。 這樣會導致堆疊溢位。 若要實作等號比較運算子，請在您的實作中使用 Object.Equals 方法。 請參閱下列範例。

```vb
If (Object.ReferenceEquals(left, Nothing)) Then
    Return Object.ReferenceEquals(right, Nothing)
Else
    Return left.Equals(right)
End If
```

```csharp
if (Object.ReferenceEquals(left, null))
    return Object.ReferenceEquals(right, null);
return left.Equals(right);
```

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，實作等號比較運算子，加法和減法運算子與以數學方式一致。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可安全地隱藏此規則的警告，等號比較運算子的預設實作會提供正確的行為類型時。

## <a name="example"></a>範例
 下列範例會定義類型 (`BadAddableType`)，違反這項規則。 這個型別應該實作等號比較運算子，讓任何兩個執行個體具有相同的欄位值測試`true`是否相等。 型別`GoodAddableType`顯示更正的實作。 請注意，此類型也會實作不等比較運算子，而且會覆寫<xref:System.Object.Equals%2A>來滿足其他規則。 完整的實作也會實作<xref:System.Object.GetHashCode%2A>。

 [!code-csharp[FxCop.Design.AddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_1.cs)]

## <a name="example"></a>範例
 下列範例會使用先前在本主題說明的預設和正確的行為的等號比較運算子定義類型的執行個體測試相等。

 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_2.cs)]

這個範例會產生下列輸出：

```txt
Bad type:  {2,2} {2,2} are equal? No
Good type: {3,3} {3,3} are equal? Yes
Good type: {3,3} {3,3} are == ?   Yes
Bad type:  {2,2} {9,9} are equal? No
Good type: {3,3} {9,9} are == ?   No
```

## <a name="see-also"></a>另請參閱

- [等號比較運算子](/dotnet/standard/design-guidelines/equality-operators)