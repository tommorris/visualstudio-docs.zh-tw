---
title: "SccGetCommandOptions 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 86f8b896581d4238e1328bd0fe086987145c9fb5
ms.lasthandoff: 02/22/2017

---
# <a name="sccgetcommandoptions-function"></a>SccGetCommandOptions 函式
此函式會提示使用者指定之命令的進階選項。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
SCCRTN SccGetCommandOptions(  
   LPVOID pvContext,  
   HWND hWnd,  
   enum SCCCOMMAND iCommand,  
   LPCMDOPTS* ppvOptions  
);  
```  
  
#### <a name="parameters"></a>參數  
 pvContext  
 [in]原始檔控制外掛程式內容結構。  
  
 hWnd  
 [in]原始檔控制外掛程式可以使用為父代，它會提供任何對話方塊 IDE 視窗控制代碼。  
  
 iCommand  
 [in]要求其進階的選項的命令 (請參閱[的指令碼](../extensibility/command-code-enumerator.md)提供可能的值)。  
  
 ppvOptions  
 [in]選項結構 (也可以是`NULL`)。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一︰  
  
|值|說明|  
|-----------|-----------------|  
|SCC_OK|成功。|  
|SCC_I_ADV_SUPPORT|原始檔控制外掛程式支援命令的進階的選項。|  
|SCC_I_OPERATIONCANCELED|使用者已取消原始檔控制外掛程式單元的**選項**對話方塊。|  
|SCC_E_OPTNOTSUPPORTED|原始檔控制外掛程式不支援這項作業。|  
|SCC_E_ISCHECKEDOUT|無法執行這項作業目前已簽出檔案。|  
|SCC_E_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC_E_NONSPECIFICERROR|非特定的失敗。|  
  
## <a name="remarks"></a>備註  
 IDE 與第一次呼叫此函式`ppvOptions` = `NULL`決定原始檔控制外掛程式是否支援指定命令的進階的選項的功能。 如果外掛程式支援此功能的命令，IDE 會呼叫此函數一次使用者要求的進階的選項時 (通常是實作為**進階**在對話方塊中的按鈕)，並提供一個非 NULL 指標`ppvOptions`指向`NULL`指標。 外掛程式會儲存任何私用結構中的使用者所指定的進階的選項，並傳回在該結構的指標`ppvOptions`。 此結構會將傳遞至所有需要知道相關資訊，包括後續呼叫其他原始檔控制外掛程式 API 函式`SccGetCommandOptions`函式。  
  
 範例可能有助於釐清這種情況。  
  
 在使用者選擇**取得**命令，且 IDE 會顯示**取得**對話方塊。 IDE 呼叫`SccGetCommandOptions`函式與`iCommand`設`SCC_COMMAND_GET`和`ppvOptions`設為`NULL`。 這會解譯原始檔控制外掛程式的問題，「 您有任何此命令的進階的選項？ 」 如果外掛程式傳回`SCC_I_ADV_SUPPORT`，IDE 會顯示**進階**按鈕在其**取得**對話方塊。  
  
 第一次使用者按一下**進階** 按鈕，再次呼叫 IDE`SccGetCommandOptions`函式，此時間與非`NULL``ppvOptions`指向`NULL`指標。 外掛程式會顯示其本身**取得選項**對話方塊中，會提示使用者輸入資訊，放到它自己的結構，並傳回在該結構的指標`ppvOptions`。  
  
 如果使用者按一下**進階**一次在同一個對話方塊中，IDE 會呼叫`SccGetCommandOptions`函式一次而不變更`ppvOptions`，以便將結構傳遞至外掛程式。 這可讓外掛程式，以重新初始化其對話方塊，為使用者先前已設定的值。 外掛程式會修改位置中的結構，然後傳回。  
  
 最後，當使用者按一下**確定**在 IDE 中**取得** 對話方塊中，IDE 會呼叫[SccGet](../extensibility/sccget-function.md)，傳遞結構中傳回`ppvOptions`，其中包含進階的選項。  
  
> [!NOTE]
>  此命令`SCC_COMMAND_OPTIONS`IDE 會顯示時，會使用**選項**對話方塊，讓使用者設定控制整合的運作方式的喜好設定。 如果原始檔控制外掛程式想要提供自己的喜好設定對話方塊中，它可以顯示從**進階**IDE 的喜好設定 對話方塊中的按鈕。 外掛程式只負責取得及保存這項資訊。IDE 不會使用它，或修改它。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [指令碼](../extensibility/command-code-enumerator.md)