---
title: CA2216：可處置類型應該宣告完成項
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DisposableTypesShouldDeclareFinalizer
- CA2216
helpviewer_keywords:
- CA2216
- DisposableTypesShouldDeclareFinalizer
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9362d7aea5f66be7a7faa237ab1f78853ac7fd6f
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549294"
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216：可處置類型應該宣告完成項

|||
|-|-|
|TypeName|DisposableTypesShouldDeclareFinalizer|
|CheckId|CA2216|
|類別|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因

型別可實作<xref:System.IDisposable?displayProperty=fullName>，且建議使用的 unmanaged 資源的欄位，不會實作完成項，如所述<xref:System.Object.Finalize%2A?displayProperty=fullName>。

## <a name="rule-description"></a>規則描述

如果可處置型別包含下列類型的欄位，就會報告這項規則的違規情形：

- <xref:System.IntPtr?displayProperty=fullName>

- <xref:System.UIntPtr?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，實作完成項，會呼叫您<xref:System.IDisposable.Dispose%2A>方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

它可安全地隱藏此規則的警告，如果類型未實作<xref:System.IDisposable>用於釋放 unmanaged 的資源。

## <a name="example"></a>範例

下列範例顯示違反此規則的型別。

[!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../code-quality/codesnippet/CSharp/ca2216-disposable-types-should-declare-finalizer_1.cs)]

## <a name="related-rules"></a>相關的規則

[CA2115：使用原生資源時必須呼叫 GC.KeepAlive](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

[CA1816：正確呼叫 GC.SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

[CA1049：具有原生資源的類型應該要可呼叫 Dispose 方法明確釋放資源](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)

## <a name="see-also"></a>另請參閱

- <xref:System.IDisposable?displayProperty=fullName>
- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>
- <xref:System.Object.Finalize%2A?displayProperty=fullName>
- [Dispose 模式](/dotnet/standard/design-guidelines/dispose-pattern)