---
title: CA1003：必須使用一般事件處理常式執行個體
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 29bd98677715a8772143ab448206f2a5ccddd763
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551614"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003：必須使用一般事件處理常式執行個體

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|類別|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 型別包含的委派，會傳回 void，其簽章包含兩個參數 （物件的第一個和第二個是指派給 EventArgs 的類型） 和包含的組件目標[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]。

## <a name="rule-description"></a>規則描述
 再[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]，以便將自訂資訊傳遞給事件處理常式中，新的委派必須宣告為所指定的類別，衍生自<xref:System.EventArgs?displayProperty=fullName>類別。 這不再是在中，則為 true [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]，它導入<xref:System.EventHandler%601?displayProperty=fullName>委派。 這個泛型委派可讓任何類別都衍生自<xref:System.EventArgs>要與事件處理常式一起使用。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，移除委派，並使用取代其使用<xref:System.EventHandler%601?displayProperty=fullName>委派。 如果委派是由自動產生[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]編譯器，變更要使用的事件宣告的語法<xref:System.EventHandler%601?displayProperty=fullName>委派。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的委派。 在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]範例中，註解將描述如何修改範例以符合規則。 C# 範例中，範例如下顯示修改過的程式碼。

 [!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
 [!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]

## <a name="example"></a>範例
 下列範例會移除和委派宣告從上一個範例中，符合規則，並會取代用於`ClassThatRaisesEvent`並`ClassThatHandlesEvent`方法使用<xref:System.EventHandler%601?displayProperty=fullName>委派。

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]

## <a name="related-rules"></a>相關的規則
 [CA1005：避免在泛型型別上包含過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010：集合應該實作泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000：不要在泛型型別上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002：不要公開泛型清單](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006：不要在成員簽章中巢狀化泛型類型](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004：泛型方法應該提供類型參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007：建議在適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>另請參閱

- [泛型](/dotnet/csharp/programming-guide/generics/index)