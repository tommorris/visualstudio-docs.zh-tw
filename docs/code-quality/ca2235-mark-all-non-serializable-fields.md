---
title: CA2235：必須標記所有不可序列化的欄位
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2235
- MarkAllNonSerializableFields
helpviewer_keywords:
- CA2235
- MarkAllNonSerializableFields
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ad4328c13403b1bea6a4358661b3347404592c02
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549715"
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235：必須標記所有不可序列化的欄位

|||
|-|-|
|TypeName|MarkAllNonSerializableFields|
|CheckId|CA2235|
|類別|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 可序列化之類型中所宣告之類型的執行個體 (Instance) 欄位是不可序列化的。

## <a name="rule-description"></a>規則描述
 可序列化的型別是標示為<xref:System.SerializableAttribute?displayProperty=fullName>屬性。 當型別會序列化時，<xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName>如果某個類型包含不是可序列化型別的執行個體欄位，會擲回例外狀況。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，套用<xref:System.NonSerializedAttribute?displayProperty=fullName>屬性不是可序列化的欄位。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 只有隱藏此規則的警告，如果<xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName>類型宣告，可讓欄位進行序列化和還原序列化的執行個體。

## <a name="example"></a>範例
 下列範例顯示違反規則的類型，以及滿足規則的型別。

 [!code-csharp[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]

## <a name="related-rules"></a>相關的規則
 [CA2236：必須呼叫 ISerializable 類型上的基底類別方法](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240：必須正確實作 ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229：必須實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238：必須正確實作序列化方法](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2237：ISerializable 類型必須標記 SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239：必須為選擇性欄位提供還原序列化方法](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120：必須保護序列化建構函式](../code-quality/ca2120-secure-serialization-constructors.md)