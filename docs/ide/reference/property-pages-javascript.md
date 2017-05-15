---
title: "JavaScript、屬性頁 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "javascript.project.property.debugging.debuggertype"
  - "javascript.project.property.debugging.requireauthentication"
  - "javascript.project.property.outputpath"
  - "javascript.project.property.debugging.launchapplication"
  - "javascript.project.property.defaultlanguage"
  - "javascript.project.property.debugging.machinename"
  - "javascript.project.property.debugging.allowlocalnetworkloopback"
ms.assetid: a05ab01f-3d5d-4675-a845-eab51807d3a3
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# JavaScript、屬性頁
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

\[屬性頁\] 提供對專案設定的存取。  您可以使用 \[屬性頁\] 中所顯示的頁面，來變更專案屬性。  
  
 若要存取專案屬性，請選取 \[方案總管\] 中的專案節點。  在 \[專案\] 功能表上，按一下 \[屬性\]。  
  
 [!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
 下列頁面和選項會出現在 \[屬性頁\] 中。  
  
## 組態和平台頁面  
 您可以使用下列選項，來選取要顯示或修改的組態和平台。  
  
 **組態**  
 指定要顯示或修改的組態設定。  這些設定包括 \[偵錯\] \(預設值\)、\[發行\]、\[所有組態\] 或使用者定義的組態。  如需詳細資訊，請參閱[Debug and Release Project Configurations](http://msdn.microsoft.com/zh-tw/0440b300-0614-4511-901a-105b771b236e)。  
  
 **平台**  
 指定要顯示或修改的平台設定。  這些設定包括 \[任何 CPU\] \([!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] 應用程式的預設值\)、\[x64\]、\[ARM\]、\[x86\] 或使用者定義的平台。  如需詳細資訊，請參閱[Debug and Release Project Configurations](http://msdn.microsoft.com/zh-tw/0440b300-0614-4511-901a-105b771b236e)。  
  
## 一般頁面  
 您可以使用下列選項，來設定專案的一般屬性。  
  
> [!NOTE]
>  有些選項僅適用於 Windows 市集應用程式。  
  
 **輸出路徑**  
 指定專案組態的輸出檔位置。  路徑是相對的；如果您輸入絕對路徑，則會在專案中儲存絕對路徑。  預設路徑為 bin\\Debug。  
  
 當您使用簡化的組建組態時，專案系統會決定要建置偵錯或發行版本。  當您按一下 \[偵錯\]、\[開始偵錯\] \(或按 F5 鍵\) 時，組建會放在偵錯位置，而不論您指定的 \[輸出路徑\] 為何。  但是，\[建置\] 功能表上的 \[建置方案\] 命令卻會將其放在您指定的位置。  若要啟用進階組建組態，請在功能表列上選擇 \[工具\]、\[選項\]。  在 \[選項\] 對話方塊中，展開 \[專案和方案\]，選取 \[一般\]，然後清除 \[顯示進階組建組態\] 核取方塊。  這麼做可以讓您手動控制所有組態值，以及建置的是偵錯或發行版本。  如需詳細資訊，請參閱[NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/zh-tw/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)。  
  
 **預設語言**  
 指定專案的預設語言。  在控制台的 \[時鐘、語言和區域\] 中選取的語言選項，會指定使用者的慣用語言。  藉由指定專案預設語言，可確保當使用者的慣用語言不符合應用程式所提供的語言資源時，會使用指定的預設語言資源。  
  
## 偵錯頁面  
 您可以使用下列選項，來設定專案中偵錯行為的屬性。  
  
> [!NOTE]
>  有些選項僅適用於 Windows 市集應用程式。  
  
 **要啟動的偵錯工具**  
 指定偵錯工具的預設主機。  
  
-   選取 \[本機電腦\]，在 Visual Studio 主機電腦上啟動應用程式。  如需詳細資訊，請參閱[在本機電腦上執行應用程式](http://go.microsoft.com/fwlink/?LinkId=234912)。  
  
-   選取 \[模擬器\]，在模擬器中啟動應用程式。  如需詳細資訊，請參閱[在模擬器中執行應用程式](http://go.microsoft.com/fwlink/?LinkId=234913)。  
  
-   選取 \[遠端電腦\]，在遠端電腦上啟動應用程式。  如需遠端偵錯的詳細資訊，請參閱[在遠端電腦上執行應用程式](http://go.microsoft.com/fwlink/?LinkId=234914)。  
  
 **啟動應用程式**  
 指定當您按 F5 鍵，或按一下 \[偵錯\]、\[開始偵錯\] 時，是否要啟動應用程式。  選取 \[是\] 啟動應用程式，否則選取 \[否\]。  如果選取 \[否\]，即使使用不同的方法啟動應用程式，還是可以對它進行偵錯。  
  
 **偵錯工具類型**  
 指定要偵錯的程式碼類型。  選取 \[僅限指令碼\] 以偵錯 JavaScript 程式碼。  選取 \[僅限 Managed\] 以偵錯由 Common Language Runtime 所管理的程式碼。  選取 \[僅限原生\] 以偵錯 C\+\+ 程式碼。  選取 \[機器碼加指令碼\] 以偵錯 C\+\+ 和 JavaScript。  選取 \[混合 \(Managed 和原生\)\] 以偵錯 Managed 和 C\+\+ 程式碼。  
  
 **允許區域網路回送**  
 指定是否允許應用程式測試存取 IP 回送位址。  如果用戶端應用程式與執行中伺服器應用程式是在同一部電腦上，請選取 \[是\] 允許使用回送位址；否則選取 \[否\]。  只有在 \[要啟動的偵錯工具\] 屬性設定為 \[遠端電腦\] 時，才能使用這個屬性。  
  
 **電腦名稱**  
 指定要裝載偵錯工具之遠端電腦的名稱。  只有在 \[要啟動的偵錯工具\] 設定為 \[遠端電腦\] 時，才能使用這個屬性。  
  
 **需要驗證**  
 指定遠端電腦是否需要驗證。  只有在 \[要啟動的偵錯工具\] 設定為 \[遠端電腦\] 時，才能使用這個屬性。