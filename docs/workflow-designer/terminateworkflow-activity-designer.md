---
title: "TerminateWorkflow 活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.TerminateWorkflow.UI"
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# TerminateWorkflow 活動設計工具
\[**TerminateWorkflow**\] 活動設計工具會用來建立及設定 <xref:System.Activities.Statements.TerminateWorkflow> 活動。  
  
## TerminateWorkflow 活動  
 <xref:System.Activities.Statements.TerminateWorkflow> 活動會終止工作流程的執行。  
  
### 使用 TerminateWorkflow 活動設計工具  
 \[**TerminateWorkflow**\] 活動設計工具位於 \[**工具箱**\] 的 \[**執行階段**\] 類別中，若要存取，請按一下 \[**工具箱**\] 索引標籤 \(也可以從 \[**檢視**\] 功能表選取 \[**工具箱**\]，或是按 CTRL\+ALT\+X\)。  
  
 \[**TerminateWorkflow**\] 活動設計工具可以從 \[**工具箱**\] 拖曳出來，放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上通常用來放置活動的任一處，例如 <xref:System.Activities.Statements.Sequence> 內部。這會建立一個 <xref:System.Activities.Statements.TerminateWorkflow> 活動，具有 TerminateWorkflow 的預設 \[**DisplayName**\]。<xref:System.Activities.Activity.DisplayName%2A> 值可以在 \[**TerminateWorkflow**\] 活動設計工具的標頭中編輯，或是在屬性方格的 \[**DisplayName**\] 方塊中編輯。  
  
### TerminateWorkflow 屬性  
 下表顯示 <xref:System.Activities.Statements.TerminateWorkflow> 屬性，並且描述屬性在設計工具中的使用方式。這些屬性可以在屬性方格中進行編輯，其中有一些可以在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上編輯。  
  
|屬性名稱|必要|使用方式|  
|----------|--------|----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.TerminateWorkflow> 活動的易記名稱。預設值為 TerminateWorkflow。雖然顯示名稱並非絕對必要，但建議您盡量使用顯示名稱。|  
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|當工作流程終止時所要擲回的例外狀況。請在屬性方格中設定這個屬性。|  
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|說明工作流程終止的原因。請在屬性方格中設定這個屬性。|  
  
## 請參閱  
 [執行階段](../workflow-designer/runtime-activity-designers.md)   
 [Persist](../workflow-designer/persist-activity-designer.md)