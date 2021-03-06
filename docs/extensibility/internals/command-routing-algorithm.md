---
title: 命令路由演算法 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c11b7d08821be981254162f930251968773a7c54
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511583"
---
# <a name="command-routing-algorithm"></a>命令路由演算法
在 Visual Studio 中許多不同的元件會處理命令。 命令會從最內側的內容中，根據目前的選取範圍，路由傳送到最外層的 （也稱為全域） 內容。 如需詳細資訊，請參閱 <<c0> [ 命令可用性](../../extensibility/internals/command-availability.md)。  
  
## <a name="order-of-command-resolution"></a>命令解析順序  
 命令會傳遞下列命令內容層級：  
  
1.  增益集： 環境第一次會提供任何增益集出現的命令。  
  
2.  優先順序命令： 使用這些命令會註冊<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>。 它們會針對每個命令在 Visual Studio 中，呼叫和其註冊順序呼叫。  
  
3.  內容功能表命令： 提供至內容功能表，並在那之後才能設定路由的典型命令目標先提供 內容功能表上的命令。  
  
4.  工具列設定命令目標： 當您呼叫時，這些命令目標會註冊<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>。 `pCmdTarget`參數可以是`null`。 如果不是`null`，則此命令的目標用來更新您要設定在工具列上找到的任何命令。 如果介面設定您的工具列中，則它會傳遞做為視窗框架`pCmdTarget`，讓所有更新的命令，在視窗框架中，透過您工具列的流程甚至都是當它不是處於焦點。  
  
5.  工具視窗： 工具視窗，通常會實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>介面中，也應該實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面，讓 Visual Studio 工具視窗是作用中視窗時，可取得命令目標。 不過，如果工具視窗有焦點就**專案** 視窗中，則命令會路由傳送至<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>介面，是常見的父項的所選的項目。 如果此選取項目跨越多個專案，此命令會路由傳送至<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution>階層。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>介面會包含<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>並<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>相對應的命令，在類似的方法<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面。  
  
6.  文件視窗中： 如果命令已具有`RouteToDocs`旗標設定其 *.vsct*檔案，Visual Studio 會尋找命令目標，是在文件檢視物件上的執行個體<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>介面或執行個體文件物件 (通常<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>介面或<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>介面)。 如果文件檢視物件不支援的命令，Visual Studio 會將路由的命令<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>傳回的介面。 （這是文件資料物件的選用介面）。  
  
7.  目前的階層： 目前的階層可以是擁有使用中的文件視窗或階層中所選取的專案**方案總管 中**。 Visual Studio 尋找<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>實作最新狀態，或使用中的階層的介面。 階層應支援階層為作用中，即使專案項目的文件視窗具有焦點時是有效的命令。 不過，命令套用時，才**方案總管**具有焦點必須支援使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>介面及其<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>方法。  
  
     **剪下**，**複製**，**貼上**，**刪除**，**重新命名**，**輸入**，及**DoubleClick**命令都需要特殊處理。 如需有關如何處理資訊**刪除**並**移除**命令，在階層中，請參閱<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>介面。  
  
8.  Global： 如果先前所述的內容尚未處理命令，Visual Studio 會嘗試將它路由至擁有實作命令的 VSPackage<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面。 如果 VSPackage 尚未已經載入，它時不會載入 Visual Studio 會呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法。 只有當載入 VSPackage<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>呼叫方法。  
  
## <a name="see-also"></a>另請參閱  
 [命令設計](../../extensibility/internals/command-design.md)