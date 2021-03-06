---
title: CommandPlacement 元素 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c5da750b3f33127fdcfdf2e2a76d4df1556561b2
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232425"
---
# <a name="commandplacement-element"></a>CommandPlacement 元素
CommandPlacement 元素可讓按鈕、 群組和包含在一個以上的群組或功能表的功能表。 藉由使用 CommandPlacement 元素，您不必完全重新定義這些項目，若要修改的使用者介面外觀。  
  
 如需詳細資訊，請參閱 <<c0> [ 建立可重複使用的按鈕群組](../extensibility/creating-reusable-groups-of-buttons.md)。  
  
## <a name="syntax"></a>語法  
  
```  
<CommandPlacement guid="guidMyCommandSet" id="MyCommand" priority="0x001" >  
  <Parent>... </Parent>  
</CommandPlacement>  
```  
  
## <a name="attributes-and-elements"></a>屬性和元素  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|guid|必要。 中所定義的命令集的 guid [Symbols 元素](../extensibility/symbols-element.md)。|  
|id|必要。 功能表、 群組或放置時，如中所定義的命令識別碼`Symbols Element`。|  
|priority|必要。 判斷項目在其父項目中的視覺位置。|  
|條件|選擇性。 請參閱[條件式 Aattributes](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|父代|必要。 功能表或裝載要放置的項目群組中。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[CommandPlacements 元素](../extensibility/commandplacements-element.md)|指定 CommandPlacements 和 CommandPlacement 元素的群組。|  
  
## <a name="example"></a>範例  
  
```  
<CommandPlacements>  
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"  
    priority="0x0300">  
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>  
  </CommandPlacement>  
</CommandPlacements>  
```  
  
## <a name="see-also"></a>另請參閱  
 [CommandPlacements 元素](../extensibility/commandplacements-element.md)   
 [Visual Studio 命令表檔案 (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
