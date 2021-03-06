---
title: 如何：為 Managed 程式碼的缺失建立工作項目
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- managed code, creating work items for code defects
- code analysis, creating work items
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: b251970bfd57b31842e1573e2e156e11a517c81a
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279469"
---
# <a name="how-to-create-a-work-item-for-a-managed-code-defect"></a>如何：為 Managed 程式碼的缺失建立工作項目

您可以使用記錄檔內工作項目從 Visual Studio 的工作項目追蹤功能。 若要使用這項功能，您的專案必須在 Azure DevOps 專案的一部分[!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)]。

## <a name="to-create-a-work-item-for-managed-code-defect"></a>若要建立受管理的程式碼缺失的工作項目

1. 在 [**程式碼分析**] 視窗中，選取警告。

2. 選擇**動作**，然後選擇**建立工作項目**，然後選擇 建立工作項目類型。

     為您指定的缺失資訊建立新的工作項目。

## <a name="to-create-a-work-item-for-multiple-managed-code-defects"></a>若要建立多個受管理的程式碼缺失的工作項目

1. 在 **錯誤清單**選取多個警告，然後以滑鼠右鍵按一下警告。

2. 指向**建立工作項目**，按一下 建立工作項目類型。

     單一工作項目會為所有選取的警告，讓您指定錯誤的資訊建立。