---
title: 工作流程設計工具-InitializeCorrelation 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8b210b5e0d3d0f3638e78331d9db093f7e86079e
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117169"
---
# <a name="initializecorrelation-activity-designer"></a>InitializeCorrelation 活動設計工具

**InitializeCorrelation**活動設計工具會用來建立及設定<xref:System.ServiceModel.Activities.InitializeCorrelation>活動。 <xref:System.ServiceModel.Activities.InitializeCorrelation>活動會建立訊息之前傳送或接收它們之間的相互關聯。

## <a name="the-initializecorrelation-activity"></a>InitializeCorrelation 活動

<xref:System.ServiceModel.Activities.InitializeCorrelation> 活動會用來在不傳送或接收訊息的情況下初始化相互關聯。 相互關聯通常會在傳送或接收訊息時初始化。 如果必須在傳送或接收訊息之前建立相互關聯，請使用 <xref:System.ServiceModel.Activities.InitializeCorrelation> 來初始化相互關聯。

### <a name="using-the-initializecorrelation-activity-designer"></a>使用 InitializeCorrelation 活動設計工具

存取權**InitializeCorrelation**中的活動設計工具**Messaging**類別**工具箱**。

**InitializeCorrelation**活動設計工具可以從拖曳**工具箱**並放到工作流程設計工具介面。 卸除活動設計工具會建立<xref:System.ServiceModel.Activities.InitializeCorrelation>預設值的活動<xref:System.Activities.Activity.DisplayName%2A>InitializeCorrelation。 <xref:System.Activities.Activity.DisplayName%2A>可以的標頭中編輯**InitializeCorrelation**活動設計工具或**DisplayName**方塊**屬性**視窗。

<xref:System.ServiceModel.Activities.CorrelationHandle>可以是指定**相互關聯**欄位中**屬性**視窗**InitializeCorrelation**活動設計工具介面。

若要顯示**初始化相互關聯**對話方塊中，您可以指定相互關聯控制代碼和索引鍵 / 值組用來初始化它，選取省略符號按鈕旁**CorrelationData**欄位**屬性**視窗。 或者，在選取 [檢視] 提示文字**InitializeCorrelation**活動設計工具介面。 如需使用此對話方塊的詳細資訊，請參閱 <<c0> [ 型別集合編輯器對話方塊](../workflow-designer/type-collection-editor-dialog-box.md)文章。

### <a name="the-initializecorrelation-properties"></a>InitializeCorrelation 屬性

下表顯示<xref:System.ServiceModel.Activities.InitializeCorrelation>屬性，並說明它們在設計工具的使用方式。 這些屬性可以在中編輯**屬性**視窗或在工作流程設計工具介面上。

|屬性名稱|必要項|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.InitializeCorrelation> 活動的易記名稱。 預設值為 InitializeCorrelation。<br /><br /> 雖然使用非預設值，做為易記<xref:System.Activities.Activity.DisplayName%2A>不是絕對必要，建議。|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|用於與相互關聯中工作流程活動相關聯的 <xref:System.ServiceModel.Activities.CorrelationHandle>。|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|相互關聯資料的字典，該字典會使訊息與工作流程執行個體產生關聯。<br /><br /> 使用**初始化相互關聯**對話方塊來設定<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>。 如需有關使用這個對話方塊中，請參閱[型別集合編輯器對話方塊](../workflow-designer/type-collection-editor-dialog-box.md)文章。|

## <a name="see-also"></a>另請參閱

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [接收](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [傳送](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)