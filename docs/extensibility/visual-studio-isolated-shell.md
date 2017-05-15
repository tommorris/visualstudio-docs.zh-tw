---
title: "Visual Studio 隔離 Shell |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], shell-based applications, isolated mode
- Visual Studio shell, isolated mode
- isolated shell-based applications [Visual Studio]
- Visual Studio shell, shell-based applications, isolated mode
- Shell [Visual Studio], isolated mode
ms.assetid: d2620e71-be9e-44c9-b5b7-03a4c8d9cf0b
caps.latest.revision: 35
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
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: d6925bbb3fa432c098f62d223b1c1a7478ecca23
ms.lasthandoff: 02/22/2017

---
# <a name="visual-studio-isolated-shell"></a>Visual Studio 隔離 Shell
Visual Studio 隔離 shell 可讓您建立可執行的並行的獨立應用程式與其他版本的 Visual Studio。 它是主要是用於裝載專門的工具，可以使用 Visual Studio 服務，但也有自訂的外觀和商標。 Visual Studio 功能和功能表命令群組可以輕鬆地開啟和關閉。 應用程式標題、 應用程式圖示和啟動顯示畫面都開放完全自訂。 如需可自訂的功能，請參閱[自訂獨立 Shell](../extensibility/customizing-the-isolated-shell.md)。  
  
 若要使用獨立的 shell 專案，您必須安裝 Visual Studio SDK。 啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
 若要建立獨立的 shell 應用程式，Visual Studio Shell 外掛式主控專案開始。 此專案包含您要開發和測試獨立的 shell 應用程式的所有項目。 撰寫部署您的應用程式安裝程式準備好時，您必須取得獨立的 shell 可轉散發套件，從[Microsoft Visual Studio Shell （獨立模式） 可轉散發套件](http://go.microsoft.com/fwlink/?LinkId=616022)。  
  
> [!NOTE]
>  您可以存取獨立的 shell 可轉散發套件之前，系統會要求您填寫簡短的客戶問卷調查。  之後填寫問卷調查，您將被導向至 Visual Studio Connect 含可轉散發套件的下載連結。  您可以在後續造訪 Visual Studio 連線站台底下找到下載連結**程式 |VISUAL STUDIO 2015 整合和隔離 SHELL**  索引標籤。  
  
> [!NOTE]
>  如需如何部署隔離的 shell 架構應用程式的詳細資訊，請參閱[逐步解說︰ 建立基本的隔離 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
## <a name="working-with-the-isolated-shell"></a>使用獨立 shell  
 Visual Studio 隔離 shell 應用程式具有完整存取權 Visual Studio 服務，並支援特殊的自訂和品牌形象。 有數種方式，您可以自訂獨立的 shell 應用程式︰  
  
-   您可以使用 VSPackages 和 Managed Extensibility Framework (MEF) 組件的元件來擴充獨立的 shell 應用程式，就像您想要在其他 Visual Studio 擴充功能中使用。 如需詳細資訊，請參閱[擴充獨立 Shell](../extensibility/extending-the-isolated-shell.md)。  
  
-   若要讓 Visual Studio 功能與功能表命令群組可用或無法使用，請更新.vsct 檔的應用程式使用者介面 (UI) 專案中。  
  
-   若要移除**選項**頁面或應用程式，從其他 Visual Studio shell 元件更新.pkgundef 檔案的應用程式。  
  
-   若要修改其他方面的外觀或行為的殼層，更新應用程式的.pkgdef 檔。  
  
-   當應用程式啟動時，也可以指定殼層的某些層面。 若要這樣做，請更新 appenvstub.dll 開始進入點呼叫中的參數。  
  
 如需您可以自訂的不同元素的詳細資訊，請參閱[獨立 Shell 的項目](../extensibility/elements-of-the-isolated-shell.md)。  
  
## <a name="standard-features-of-the-isolated-shell"></a>獨立 Shell 的標準功能  
 下列功能是所有版本的 Visual Studio 的標準。  
  
|功能分類|功能|  
|----------------------|-------------|  
|IDE 功能|匯入/匯出設定<br /><br /> 工具箱控制項的安裝程式<br /><br /> 工作清單 i 錯誤清單<br /><br /> 輸出視窗<br /><br /> 起始頁<br /><br /> 屬性視窗<br /><br /> 工具箱<br /><br /> 底下提供說明，包括方案總管<br /><br /> 書籤視窗<br /><br /> 類別檢視<br /><br /> 物件瀏覽器<br /><br /> 命令視窗<br /><br /> 文件大綱<br /><br /> 資源檢視<br /><br /> 外部工具<br /><br /> Windows Communication Foundation (WCF) 加入服務參考<br /><br /> 語言整合查詢 (LINQ) 支援|  
|編輯器/設計工具|瀏覽工具統一的尋找、 來源定義 （繼承） 的程式碼<br /><br /> IntelliSense<br /><br /> 智慧標籤<br /><br /> 程式碼片段管理員<br /><br /> 程式碼片段<br /><br /> 重構<br /><br /> 美化<br /><br /> IntelliSense 篩選<br /><br /> 程式碼定義視窗<br /><br /> 應用程式設計工具<br /><br /> Windows Form 設計工具<br /><br /> Windows Presentation Foundation (WPF) 設計工具|  
|偵錯|C# 運算式評估工具<br /><br /> 本機偵錯<br /><br /> Managed 偵錯<br /><br /> 編輯後繼續<br /><br /> 跨執行緒偵錯<br /><br /> 視覺效果<br /><br /> 資料提示方塊<br /><br /> 原生偵錯<br /><br /> 指令碼偵錯<br /><br /> Interop 偵錯<br /><br /> 在 just-in-time (JIT) 偵錯<br /><br /> 多處理序偵錯<br /><br /> XSLT 偵錯<br /><br /> 附加至本機的處理序<br /><br /> 追蹤點<br /><br /> 中斷點條件約束|  
|資料|伺服器總管 （簡體-僅限資料）<br /><br /> 資料繫結至本機資料 (。MDF 或。MDB)<br /><br /> 資料繫結至物件<br /><br /> 資料繫結至 Web 服務<br /><br /> 完整的資料控制項<br /><br /> XML 編輯器<br /><br /> 資料繫結至本機資料庫伺服器<br /><br /> 資料來源視窗|  
|Web|HTML 編輯器<br /><br /> 網頁瀏覽器<br /><br /> Web Form 設計工具<br /><br /> 網站專案<br /><br /> Web 應用程式專案|  
|擴充性|使用 VSPackages 和 MEF 元件|  
  
## <a name="see-also"></a>另請參閱  
 [Shell （獨立或整合）](../extensibility/shell-isolated-or-integrated.md)