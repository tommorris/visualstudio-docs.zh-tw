---
title: CA2149：透明方法不可以呼叫機器碼
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2149
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: a30e3581101b1065f26d01e70657981a5220e56c
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548736"
---
# <a name="ca2149-transparent-methods-must-not-call-into-native-code"></a>CA2149：透明方法不可以呼叫機器碼
|||
|-|-|
|TypeName|TransparentMethodsMustNotCallNativeCode|
|CheckId|CA2149|
|類別|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 方法會呼叫原生的函式，透過例如 P/Invoke 方法 stub。

## <a name="rule-description"></a>規則描述
 任何直接呼叫原生程式碼，例如透過 P/Invoke 的透明方法會引發此規則。 違反此規則會導致<xref:System.MethodAccessException>層級 2 透明度模型，而完整的要求，如<xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A>層級 1 透明度模型中。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，將方法呼叫原生程式碼標示<xref:System.Security.SecurityCriticalAttribute>或<xref:System.Security.SecuritySafeCriticalAttribute>屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 [!code-csharp[FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../code-quality/codesnippet/CSharp/ca2149-transparent-methods-must-not-call-into-native-code_1.cs)]