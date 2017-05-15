---
title: "ProjectTemplateLink 項目 (Visual Studio 範本) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink"
helpviewer_keywords: 
  - "<ProjectTemplateLink> 項目 [Visual Studio 樣板]"
  - "ProjectTemplateLink 項目 [Visual Studio 樣板]"
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# ProjectTemplateLink 項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定多專案範本中某一個專案的 .vstemplate 檔路徑。  
  
## 語法  
  
```  
<ProjectTemplateLink ProjectName="Name">     PathToTemplateFile </ProjectTemplateLink>  
```  
  
## 屬性和項目  
 下列章節將說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`ProjectName`|選擇性屬性。<br /><br /> 指定多專案範本中每一個別專案的名稱。  \[**新增專案**\] 對話方塊無法指派名稱給個別專案。|  
|`CopyParameters`|可將主群組範本中的所有變數複製到每一個連結的範本。<br /><br /> 在連結之範本中的參數會有前置詞 `"$ext_*$"`。  例如，如果父群組範本中 `$projectname$` 參數的值為 ExampleProject1，則輪到連結的範本執行時，該範本會擷取 `$ext_projectname$` 參數，而該參數是父群組範本中 `$projectname$` 參數的複本。<br /><br /> 這樣可讓連結的範本共用某些只有在父群組範本中才方便建立的通用參數。<br /><br /> 這個屬性是選擇性的，如果未包含，則它會自動預設為 `false`。<br /><br /> 已在 Visual Studio 2013 Update 2 中引入。  若要參考正確的產品版本，請參閱[Referencing Assemblies Delivered in the Visual Studio 2013 SDK Update 2](http://msdn.microsoft.com/zh-tw/42b65c3e-e42b-4c39-98c8-bea285f25ffb)。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|指定多專案範本的組織和內容。|  
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|將多專案範本中的專案分組。|  
  
## 文字值  
 需要文字值。  
  
 此文字會指定範本的 .vstemplate 檔路徑。  
  
## 備註  
 多專案範本是做為兩個以上專案的容器使用。  `ProjectTemplateLink` 項目用於指定範本中某一個專案的 .vstemplate 檔位置。  在多專案範本的 .vstemplate 檔中，範本中的每個專案都有一個 `ProjectTemplateLink` 項目。  如需多專案範本的詳細資訊，請參閱 [如何：建立多專案的範本](../ide/how-to-create-multi-project-templates.md)。  
  
## 範例  
 這個範例將示範簡單的多專案根 .vstemplate 檔案。  在這個範例中，範本包含兩個專案 `My Windows Application` 和 `My Class Library`。  `ProjectTemplateLink` 項目的 `ProjectName` 屬性會設定 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的名稱，以指派此專案。  如果 `ProjectName` 屬性不存在，則 .vstemplate 檔案的名稱會做為專案名稱。  
  
```  
<VSTemplate Version="3.0.0" Type="ProjectGroup"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-Project Template Sample</Name>  
        <Description>An example of a multi-project template</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectCollection>  
            <ProjectTemplateLink ProjectName="My Windows Application">  
                WindowsApp\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
            <ProjectTemplateLink ProjectName="My Class Library" CopyParameters="true">  
                ClassLib\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## 請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)   
 [如何：建立多專案的範本](../ide/how-to-create-multi-project-templates.md)