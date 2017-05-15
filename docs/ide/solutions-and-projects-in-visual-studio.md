---
title: "Visual Studio 中的方案和專案 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.savedeferredsaveprojectonclose"
  - "vs.untrustedtemplateopeningdocuments"
  - "Project Properties.FullPath"
  - "vs.addnewsolutionitem"
  - "vs.environment.projects"
  - "vs.openproject"
  - "vs.getopenfilename"
  - "vs.addnewitem"
  - "vs.encoding"
  - "vs.addexistingitem"
  - "Project Properties.URL"
  - "VS.SolutionExplorer"
  - "Project Properties.FileName"
  - "SolutionProperties.Name"
  - "VS.SaveChangesDlg"
  - "vs.newproject"
  - "VS.SolutionExplorer.Selection"
  - "SolutionProperties.Path"
  - "vs.getdirectoryname"
  - "vs.addexistingsolutionitem"
  - "SolutionProperties.Description"
  - "vs.environment.solutions"
  - "vs.saveordiscarddeferredsaveproject"
  - "VS.SolutionExplorer.Solutions"
helpviewer_keywords: 
  - "vs.solutionpropertypages"
  - "vs.solutionpropertypages.startupproject"
  - "vs.solutionpropertypages.configurationsettings"
  - "方案項目，在 [方案總管] 的資料夾"
  - "方案項目共用"
  - "方案 [Visual Studio]"
  - "專案項目 [Visual Studio]，關於專案項目"
  - "工作區"
  - "方案 [Visual Studio] 設計"
  - "專案 [Visual Studio]"
  - "方案 [Visual Studio]、 專案和"
  - "vs.solutionpropertypages.projectdependencies"
  - "應用程式 [Visual Studio]"
  - "專案 [Visual Studio] 設定"
  - "其他檔案"
ms.assetid: aeaf56cb-c2dd-47f6-b012-23b84b7a7254
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# <a name="solutions-and-projects-in-visual-studio"></a>Visual Studio 中的方案和專案
當您在 Visual Studio 中建立 App、應用程式、網站、Web 應用程式、指令碼、外掛程式等項目時，您必須開始一個「專案」 。 在邏輯方面而言，專案包含所有原始程式碼檔案、圖示、影像、資料檔案以及其他會編譯到可執行程式或網站的項目，或是執行編譯所需的項目。  專案也包含所有編譯器設定與其他組態檔，這些是您的程式將與其通訊的各種服務或元件所需的項目。

> [!NOTE]
>  如果您不想要，則不需要使用方案或專案。 您只需要在 Visual Studio 中開啟檔案，並開始編輯程式碼。 如需詳細資訊，請參閱 [Open Any Folder with Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2016/04/12/open-any-folder-with-visual-studio-15-preview/) (使用 Visual Studio 開啟任何資料夾)。


 就字面上的意義而言，專案是 XML 檔案 (*.vbproj、\*.csproj、\*.vcxproj)，它定義虛擬資料夾階層，以及其中包含之所有項目的路徑與所有建置設定。 在 Visual Studio 中，[方案總管] 會使用專案檔來顯示專案內容與設定。 當您編譯專案時，MSBuild 引擎會使用專案檔來建立可執行檔。 您也可以自訂專案來產生其他類型的輸出。  

 就邏輯與檔案系統方面而言，專案是包含在「方案」 內，這可能包含一或多個專案，以及建置資訊、Visual Studio 視窗設定與任何未與任何專案關聯的其他檔案。 就字面上的意義而言，方案是具有自己獨特格式的文字檔；它通常不適合手動編輯。  

 方案具有關聯的 *.suo 檔案，其中儲存有關每個專案使用者的設定、喜好設定與組態資訊。  

 下圖顯示專案與方案和其邏輯上包含之項目之間的關係。  

 ![Visual Studio 專案和方案](../ide/media/vs2015_project_diagram.png "vs2015_project_diagram")  

 您也可以建立自訂專案與項目範本。 如需詳細資訊，請參閱[建立專案和項目範本](../ide/creating-project-and-item-templates.md)。  

## <a name="creating-new-projects"></a>建立新專案  
 建立新專案最簡單的方式是從預先定義的專案範本開始，它們是由預先產生的程式碼檔案、組態檔、資產與設定的基本集合所組成，可讓您開始以特定的程式設計語言來建立特定類型的應用程式或網站。 當您從主功能表選擇 [檔案] &#124; [新增] &#124; [專案] 或 [檔案] &#124; [新增] &#124; [網站] 並巡覽時，可以在 [新增專案] 對話方塊中看到這些範本。 如需詳細資訊，請參閱[建立方案和專案](../ide/creating-solutions-and-projects.md)和 [NIB 根據範本建立專案](http://msdn.microsoft.com/en-us/7c36d86a-6b79-4480-8228-0f925f1204b2)。  

## <a name="managing-projects-in-solution-explorer"></a>管理 [方案總管] 中的專案  
 建立新專案之後，您可以使用 [方案總管]  來檢視及管理專案與方案，以及關聯的項目。 下圖顯示 [伺服器總管] 與包含兩個專案的 C# 方案。  

 ![方案總管](../ide/media/vs2015_solution_explorer.png "vs2015_solution_explorer")  

## <a name="in-this-section"></a>本章節內容  

-   [建立方案和專案](../ide/creating-solutions-and-projects.md)  

-   [新增和移除專案項目](../ide/adding-and-removing-project-items.md)  

-   [管理專案和方案屬性](../ide/managing-project-and-solution-properties.md)  

-   [管理專案中的參考](../ide/managing-references-in-a-project.md)  

-   [應用程式屬性](../ide/application-properties.md)  

-   [管理組件和資訊清單簽署](../ide/managing-assembly-and-manifest-signing.md)  

-   [如何：指定應用程式圖示 (Visual Basic、C#)](../ide/how-to-specify-an-application-icon-visual-basic-csharp.md)  

-   [以特定的 .NET Framework 版本為目標](../ide/targeting-a-specific-dotnet-framework-version.md)  

-   [建立專案和項目範本](../ide/creating-project-and-item-templates.md)  

## <a name="see-also"></a>另請參閱  
 [Visual Studio IDE](../ide/visual-studio-ide.md)



<!--HONumber=Feb17_HO4-->

