---
title: "XAML 設計工具選項頁面 | Microsoft Docs"
ms.custom: 
ms.date: 03/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.XAMLDesigner
ms.assetid: ad3820b2-0d95-4807-a75c-c3467ed973a3
caps.latest.revision: 1
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: d23a47b708754248cd5c3fb8d86510a0c96491fa
ms.lasthandoff: 03/07/2017

---
# <a name="xaml-designer-options-page"></a>XAML 設計工具選項頁面
使用 [XAML 設計工具] 選項頁面來指定如何設定 XAML 文件中元素和屬性的格式。 若要開啟此頁面，請選擇 [工具] 功能表，然後選擇 [選項]。 若要存取 [XAML 設計工具] 屬性頁面，請選擇 [XAML 設計工具] 節點。 當您開啟文件時，會套用 XAML 設計工具的設定。 因此，若要變更設定，您需要關閉然後重新開啟 Visual Studio，才能看到變更。

> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  

## <a name="enable-xaml-designer"></a>啟用 XAML 設計工具
選取時，此設定會啟用 XAML 設計工具。 XAML 設計工具提供視覺化工作區，讓您編輯 XAML 文件。 Visual Studio 中的特定功能，例如資源與資料繫結的 IntelliSense，需要啟用 XAML 設計工具。

只有在啟用 XAML 設計工具時，下列設定才適用。 如果您變更這個選項，必須重新啟動 Visual Studio，設定才會生效。

## <a name="default-document-view"></a>預設文件檢視
使用此設定可控制載入 XAML 文件時是否出現設計檢視。

|||  
|-|-|  
|**原始碼檢視**|指定是否只有 XAML 原始碼會出現在 XAML 檢視。 載入大型文件時，這非常有用。|  
|**設計檢視**|指定是否只有視覺化 XAML 設計工具會出現在 XAML 檢視。|  
|**分割檢視**|指定是否視覺化 XAML 設計工具和 XAML 原始碼相鄰出現在 XAML 檢視中 (位置根據 [分割方向] 設定)。|  

## <a name="split-orientation"></a>分割方向
使用此設定可控制編輯 XAML 文件時，何時以及如何顯示 XAML 設計工具。 這些設定只適用於 [預設文件檢視] 設為 [分割檢視] 時。

|||  
|-|-|  
|**垂直**|XAML 原始碼出現在 XAML 檢視的左邊，另一邊則出現 XAML 設計工具。|  
|**水平**|XAML 設計工具會顯示在 XAML 檢視的頂端，XAML 原始碼出現在它下方。|  
|**Default**|XAML 文件會使用文件專案之目標平台的建議分割方向。 對於大部分的平台，這相當於 [水平]。|  

## <a name="zoom-by-using"></a>縮放方式
使用此設定可決定編輯 XAML 文件時，縮放的運作方式。

|||  
|-|-|  
|**滑鼠滾輪**|捲動滑鼠滾輪來放大 XAML 設計工具。|  
|**CTRL + 滑鼠滾輪**|按住 CTRL 鍵同時捲動滑鼠滾輪，來放大 XAML 設計工具。|  
|**Alt + 滑鼠滾輪**|按住 ALT 鍵同時捲動滑鼠滾輪，來放大 XAML 設計工具。|  

這些設定會決定編輯 XAML 文件時的設計工具行為。

|||  
|-|-|  
|**建立時自動命名互動元素**|指定當您將互動元素新增至設計工具時，是否要提供新互動元素的預設名稱。|  
|**自動在建立元素時插入配置屬性**|指定當您將新項目新增至設計工具時，是否要提供新項目的配置屬性。|  
|**使用四分色配置**|指定目前選取的控制項是否對齊父容器的最近邊緣。 如果清除此核取方塊，則控制項對齊方式不會在移動或建立作業期間變更。|  
|**自動填入工具箱項目**|指定目前方案中的使用者控制項和自訂控制項是否自動顯示在工具箱。|  

## <a name="settings-blend-only"></a>設定 (僅 Blend)
使用這些選項可決定使用 Blend 編輯 XAML 檔案時的設定。

|||  
|-|-|  
|**縮放方式**|捲動滑鼠滾輪，或按住 CTRL 或 ALT 鍵並同時捲動滑鼠滾輪，來放大 XAML 設計工具。|  
|**類型單位**|指定設計工具上的度量單位是根據點數還是像素。 因為通用 Windows 應用程式不支援點，所以如果選取 [點]，單位會自動轉換為像素。|  

## <a name="artboard-blend-only"></a>畫板 (僅 Blend)
使用這些設定可決定在 Blend 中編輯 XAML 文件時的 XAML 設計工具行為。

### <a name="snapping"></a>貼齊

|||  
|-|-|  
|**顯示貼齊格線**|選取此選項時，設計工具中會顯示格線，幫助您對齊控制項。 選取 [貼齊格線] 選項時，新增到設計工具的控制項會貼齊這些格線。|  
|**貼齊格線**|在設計工具新增或移動控制項時，它們會貼齊格線。|  
|**格線間距**|以像素或點為單位 (由 [類型單位] 設定所決定)，指定格線之間的間距。|  
|**貼齊對齊線**|指定控制項是否貼齊對齊線。|  
|**預設邊界**|啟用 [貼齊對齊線] 時，以像素或點為單位 (由 [類型單位] 設定所決定)，指定控制項和對齊線之間的間距。|  
|**預設邊框間距**|啟用 [貼齊對齊線] 時，以像素或點為單位 (由 [類型單位] 設定所決定)，指定控制項和對齊線之間的額外間距。|  

### <a name="animation"></a>動畫
使用此設定可決定在 Blend 中啟用相依 (未加速) 動畫時，是否會出現警告。

### <a name="effects"></a>效果
使用這些設定可決定使用 Blend 在 XAML 設計工具中編輯 XAML 檔案時，是否呈現效果。

|||  
|-|-|  
|**呈現效果**|指定使用 Blend 在 XAML 設計工具中編輯 XAML 檔案時，是否呈現效果。|  
|**縮放臨界值**|指定當選取 [呈現效果] 核取方塊時，效果呈現所使用的縮放百分比。 如果放大超過此設定，效果將不再呈現於 XAML 設計工具中。|  

## <a name="see-also"></a>另請參閱  
 [WPF 中的 XAML](http://msdn.microsoft.com/Library/5d858575-a83b-42df-ad3f-047ed2d6e3c8)   
 [如何︰變更 XAML 檢視設定](http://msdn.microsoft.com/en-us/aee87c79-ca01-4f84-8fb7-a9e47048ee47)   
 [XAML 和程式碼逐步解說](http://msdn.microsoft.com/en-us/b3ff41a0-a2a3-4f61-b698-ac88ec8f799c)
