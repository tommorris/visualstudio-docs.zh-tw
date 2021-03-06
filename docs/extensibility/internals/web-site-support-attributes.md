---
title: 網站支援屬性 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b312322c1d707f13c5121f1fd159f3fd7736886c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140832"
---
# <a name="web-site-support-attributes"></a>網站支援屬性
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 網站專案可以擴充來支援 Web 程式設計語言。 語言必須向[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，讓專案範本可以出現在**新網站**時選取語言 對話方塊。

IronPython Studio 範例包含網站的支援。 此範例包含下列屬性類別，以註冊 IronPython 做為新的 Web 專案的程式碼後置語言。

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 這個屬性會放在語言專案。 它會將語言加入 Web 程式設計語言中的清單**語言**清單中**新網站** 對話方塊。 例如，下列程式碼會將 IronPython 加入清單：

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 這個屬性也會設定為指向範本資料夾的範本路徑。 如需範本資料夾的位置的詳細資訊，請參閱[網站支援範本](../../extensibility/internals/web-site-support-templates.md)。

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 這個屬性會放在語言專案。 它允許其他檔案類型 （主要） 網站專案，建立巢狀 （相關） 的一種檔案類型中**方案總管 中**。

 例如，下列程式碼指定 IronPython 程式碼後置檔案與相關的.aspx 檔案。 IronPython Web site 方案中建立新的.aspx 網頁時，會產生新.py 原始程式檔，並會顯示為子節點的.aspx 網頁。

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 這個屬性會放在語言專案封裝。 它會選取語言的 IntelliSense 提供者。

 例如，下列程式碼指定 PythonIntellisenseProvider，實作的執行個體<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>，應該視提供語言服務建立。

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 IVsIntellisenseProject 實作處理的參考，並以程式碼的網頁要求，但不快取時所呼叫的語言編譯器。

## <a name="see-also"></a>另請參閱
 [網站支援](../../extensibility/internals/web-site-support.md)