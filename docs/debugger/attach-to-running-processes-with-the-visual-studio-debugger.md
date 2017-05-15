---
title: "使用 Visual Studio Debugger 附加至執行中處理序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.processes.attach"
  - "vs.debug.process"
  - "vs.debug.programs"
  - "vs.debug.detaching"
  - "vs.debug.processes"
  - "vs.debug.error.attach"
  - "vs.debug.remotemachine"
dev_langs: 
  - "C++"
  - "CSharp"
  - "FSharp"
  - "VB"
  - "c++"
helpviewer_keywords: 
  - "遠端偵錯, 附加至程式"
  - "處理序, 附加至執行中的處理序"
  - "[附加至處理序] 對話方塊"
  - "偵錯 [Visual Studio], 附加至處理序"
  - "偵錯工具, 處理序"
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
caps.latest.revision: 57
caps.handback.revision: 53
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 使用 Visual Studio Debugger 附加至執行中處理序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio 偵錯工具附加至處理序時，通常您還沒開始應用程式從 Visual Studio 中，但您想要進行偵錯。 例如，您可以附加至 IIS 處理序或裝載.NET 應用程式的 Windows 服務。 附加至處理序可以是本機或遠端。 另一個範例是如果您正在執行的應用程式，而不偵錯工具，並叫用例外狀況，您接著可能會附加至執行應用程式以開始偵錯的處理序。

對於某些應用程式類型 （例如 Windows 市集應用程式） 中，您不直接附加到處理序名稱，但使用 **偵錯已安裝的應用程式套件** 功能表選項 （請參閱資料表）。

為了協助您找出您要附加至處理序，您的案例，一些最常見的偵錯案例如下所示。 其中的詳細指示，我們提供的連結。

|情節|偵錯方法|處理序名稱|請注意連結|
|-|-|-|-|
|藉由從 Visual Studio 偵錯在本機電腦上任何支援的應用程式類型|標準的 F5 偵錯|N/A|請參閱 [偵錯工具使用者入門](../debugger/getting-started-with-the-debugger.md)|
|遠端偵錯 ASP.NET 4 或 4.5 的 IIS 伺服器上|使用遠端工具，並附加至處理序|w3wp.exe|請參閱 [遠端 IIS 電腦上的遠端偵錯 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|遠端偵錯 ASP.NET 核心 IIS 伺服器上|使用遠端工具，並附加至處理序|dnx.exe|應用程式部署，請參閱 [發行至 IIS](https://docs.asp.net/en/latest/publishing/iis.html)。 進行偵錯，請參閱 [遠端 IIS 電腦上的遠端偵錯 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|伺服器處理序上的其他支援之應用程式類型進行偵錯|使用遠端工具 （如果伺服器位於遠端），並附加至處理序|iexplore.exe 或其他處理程序|如果有必要，請使用工作管理員，協助找出程序。 請參閱 [遠端偵錯](../debugger/remote-debugging.md) 和本主題稍後的章節|
|遠端偵錯 Windows 桌面應用程式|遠端工具和 F5|N/A| 請參閱 [遠端偵錯](../debugger/remote-debugging.md)|
|遠端偵錯的 Windows 通用 (UWP)、 OneCore、 HoloLens 或 IoT 應用程式|偵錯已安裝應用程式封裝|N/A|使用 **偵錯 / 其他偵錯目標 / 偵錯已安裝應用程式套件** 而不是 **附加至處理序**|
|您未從 Visual Studio 啟動的 Windows 通用 (UWP)、 OneCore、 HoloLens 或 IoT 應用程式進行偵錯|偵錯已安裝應用程式封裝|N/A|使用 **偵錯 / 其他偵錯目標 / 偵錯已安裝應用程式套件** 而不是 **附加至處理序**|
  
> [!WARNING]
>  若要附加至以 JavaScript 撰寫的 Windows 通用應用程式，您必須先啟用應用程式的偵錯功能。 請參閱 Windows 開發人員中心的 [Attach the debugger](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Attach_the_debugger) 。  
  
> [!NOTE]
>  偵錯工具若要附加至以 C++ 撰寫的程式碼，該程式碼必須發出 `DebuggableAttribute`。 您可以使用 [/ASSEMBLYDEBUG](/visual-cpp/build/reference/assemblydebug-add-debuggableattribute) 連結器選項連結，將其自動加入程式碼。

## <a name="what-debugger-features-can-i-use"></a>可以使用哪些偵錯工具功能？

若要使用 Visual Studio 偵錯工具 （例如叫用中斷點） 的完整功能，可執行檔必須完全符合您的本機來源和符號 (也就是偵錯工具必須能夠載入正確 [符號檔 (.pbd)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md))。 根據預設，這需要偵錯組建。

遠端偵錯的情況下，您必須使用任一個原始碼的原始程式碼的複本已經在 Visual Studio 中開啟。 在本機電腦上，在遠端電腦上的已編譯的應用程式二進位檔必須來自相同的組建。

本機偵錯案例，您可以使用偵錯在 Visual Studio 中沒有來源的存取權如果與該應用程式有正確的符號檔 （根據預設，這需要偵錯組建）。 如需詳細資訊，請參閱 [指定符號和來源檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。

針對 Windows 桌面應用程式，您可以也偵錯使用 JIT 偵錯工具 （Visual Studio 會開啟與您應用程式程式碼發生錯誤後中斷） 執行的應用程式。

##  <a name="a-namebkmkattachtoaprocessonaremotecomputera-attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> 附加至遠端電腦上的處理序  
 若要附加至處理程序，您必須知道處理序名稱。 針對已部署至 IIS 的 ASP.NET 應用程式，請參閱 [遠端 IIS 電腦上的遠端偵錯 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) 或 [發行至 IIS](https://docs.asp.net/en/latest/publishing/iis.html) ASP.NET 核心應用程式。 若為其他應用程式，您或許可在 [工作管理員] 中找到處理序名稱。
  
 使用 [附加至處理序]  對話方塊時，您可以選取已針對遠端偵錯設定的其他電腦。 如需詳細資訊，請參閱 [遠端偵錯](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)。 當您選取了遠端電腦時，您可以檢視該電腦上正在執行的可使用處理序清單，並附加至其中一個或多個處理序進行偵錯。
  
 **若要選取遠端電腦︰**  

1. 在 Visual Studio 選取 [偵錯] / [附加至處理序] 。

2.  在 [附加至處理序]  對話方塊中，從 [傳輸]  清單選取適當的連接類型。 [預設值] 是適合大部分情況的正確設定

    [傳輸]  設定在偵錯工作階段之間持續維持。 
  
3.  利用下列其中一種方法，使用 [限定詞]  清單方塊選擇遠端電腦名稱：  
  
    1.  在 [限定詞]  清單方塊中輸入名稱。
    
        >**請注意** 在稍後步驟中，您無法使用連接遠端電腦名稱，如果使用的 IP 位址。 （連接埠號碼可能會自動出現在選取程序之後。 您也可以輸入它以手動方式。 下圖中 4020 是遠端偵錯工具的預設連接埠）。  
  
    2.  按一下附加至 [限定詞]  清單方塊的下拉箭號，然後從下拉式清單中選取電腦名稱。  
  
    3.  按一下 [限定詞]  清單旁的 [尋找] 按鈕，開啟 [遠端偵錯工具連接]  對話方塊。 [選取遠端偵錯工具連接]  對話方塊會列出位於您本機子網路上的所有裝置，以及透過乙太網路纜線直接附加至電腦的裝置。 按一下您想要的電腦或裝置，然後按一下 [選取] 。 
    
    ![DBG_Basics_Attach_To_Process](../debugger/media/dbg_basics_attach_to_process.png "DBG_Basics_Attach_To_Process") 
  
     [限定詞]  設定只有在使用該限定詞成功產生偵錯連接時，才會在偵錯工作階段之間持續維持。
     
4.  按一下 [確定] ****。

      [可使用的處理序]  清單會在您開啟 [處理序]  對話方塊時自動顯示。 當對話方塊開啟時，處理序可以在背景中啟動和停止。 但內容不一定是最新的。 您可以隨時按一下 [重新整理] 以重新整理該清單，查看目前的處理序清單。 
     
4.  請在 [附加至處理序]  對話方塊的 [可使用的處理序]  清單中，尋找您要附加的程式。  
  
     如果該處理序正在不同的使用者帳戶下執行，請選取 [顯示所有使用者的處理序]  核取方塊。
     
5.  按一下 [附加] 。  
  
##  <a name="a-namebkmkattachtoarunningprocessa-attach-to-a-running-process-on-the-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a> 附加至本機電腦上執行的處理序  
 若要附加至處理程序，您必須知道處理序名稱。  您或許可在 [工作管理員] 中找到處理序名稱。  
  
1.  在 Visual Studio 選取 [偵錯] / [附加至處理序] 。
  
2.  請在 [附加至處理序]  對話方塊的 [可使用的處理序]  清單中，尋找您要附加的程式。  
  
     如果該處理序正在不同的使用者帳戶下執行，請選取 [顯示所有使用者的處理序]  核取方塊。
  
3.  在 [附加至]  方塊中，確定其中已列出您要偵錯的程式碼類型。 預設的 [自動]  設定會自動判斷您要偵錯的程式碼類型。 若要手動設定程式碼類型，請執行下列程序  
  
    1.  按一下 [附加至]  方塊中的 [選取] 。  
  
    2.  在 [選取程式碼類型]  對話方塊中，按一下 [偵錯這些程式碼類型]  ，然後選取要偵錯的類型。  
  
    3.  按一下 [確定] 。  
  
4.  按一下 [附加] 。

## <a name="additional-info"></a>其他資訊

偵錯時，您可以附加至多個程式，但是無論在任何時間，偵錯工具一次只能有一個使用中程式。 您可以在 [偵錯位置]  工具列或 [處理序]  視窗中設定使用中的程式。 如需詳細資訊，請參閱 [如何：設定目前的處理序](http://msdn.microsoft.com/zh-tw/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e)。  
  
如果您嘗試附加至未受信任的使用者帳戶所擁有的處理序，會出現安全性警告對話方塊確認訊息。 如需詳細資訊，請參閱 [安全性警告︰ 附加至不受信任的使用者所擁有的處理序可能會有危險。如果下列資訊看起來有問題，或您不確定，不會附加至這個處理序](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)。  
  
在某些情況下，在遠端桌面 (終端機服務) 工作階段中進行偵錯時，[可使用的處理序]  清單並不會顯示所有可使用的處理序。 如果您是以受限制的使用者身分執行 Visual Studio，則 [可使用的處理序]  清單不會顯示在工作階段 0 中執行的處理序，因為工作階段 0 是用於服務以及其他包括 w3wp.exe 的伺服器處理序。 您可藉由使用系統管理員帳戶來執行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，或是從伺服器主控台 (而非終端機服務工作階段) 執行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，來解決這個問題。 如果這些解決方法都沒有效，第三個方法就是從 Windows 命令列執行 `vsjitdebugger.exe -p` *ProcessId* 以連結至流程。 您可以使用 tlist.exe 來判斷處理序 ID。 若要取得 tlist.exe，您可以從  [WDK 和 WinDbg 下載](http://go.microsoft.com/fwlink/?LinkId=168279)來下載並安裝 Debugging Tools for Windows。
  
##  <a name="a-namebkmktroubleshootattacherrorsa-troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> 疑難排解附加錯誤  
 當偵錯工具附加至執行中的處理序時，該處理序可以包含一種或多種程式碼類型。 偵錯工具可附加的程式碼類型會在 [選取程式碼類型]  對話方塊中顯示並供您選取。  
  
 有時候，偵錯工具可以成功附加至一種程式碼類型，而無法附加至另一種程式碼類型。 如果您嘗試附加至遠端電腦上正在執行的處理序，可能會發生這種狀況。 遠端電腦可能為某些程式碼類型安裝了遠端偵錯元件，但沒有安裝其他程式碼類型的遠端偵錯元件。 如果您嘗試附加至兩個或多個處理序以進行直接的資料庫偵錯，也可能會發生這種狀況。 (SQL 偵錯僅支援附加至單一處理序)。  
  
 如果偵錯工具能附加至某些程式碼類型 (而非所有程式碼類型)，您可能會看到識別無法附加之類型的訊息。  
  
 如果偵錯工具成功附加到至少一種程式碼類型，您可以繼續偵錯該處理序。 您只能偵錯已附加成功的程式碼類型。 上述範例訊息顯示該指令碼類型附加失敗。 因此，您無法在處理序內偵錯指令碼。 處理序中的指令碼仍可執行，但是您將無法在指令碼內設定中斷點、檢視資料，或執行其他的偵錯作業。  
  
 如果您需要更多相關資訊以了解偵錯工具無法附加至程式碼類型的原因，可以嘗試重新附加至該程式碼。  
  
 **若要取得程式碼類型附加失敗的原因的相關資訊**  
  
1.  與處理序中斷連結。 在 [偵錯]  功能表上按一下 [中斷所有連結] 。  
  
2.  重新附加至處理序，並只選取單一程式碼類型。  
  
    1.  在 [附加至處理序]  對話方塊的 [可使用的處理序]  清單中，選取該處理序。  
  
    2.  按一下 [選取] 。  
  
    3.  在 [選取程式碼類型]  對話方塊中，選取 [偵錯這些程式碼類型]  以及之前附加失敗的程式碼類型。 清除任何其他程式碼。  
  
    4.  按一下 [確定] 。 [選取程式碼類型]  對話框會關閉。  
  
    5.  在 [附加至處理序]  對話方塊中按一下 [附加] 。  
  
     這時，該附加將完全失敗，您將取得特定的錯誤訊息。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯多個處理序](../debugger/debug-multiple-processes.md)   
 [在 [Just-in-time 偵錯](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [遠端偵錯](../debugger/remote-debugging.md)