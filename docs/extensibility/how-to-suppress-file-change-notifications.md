---
title: 如何： 隱藏檔案變更通知 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 28f4c2e2929fecb29da6ddeecdd6cede6b8fa4d7
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497959"
---
# <a name="how-to-suppress-file-change-notifications"></a>如何： 隱藏檔案變更通知
當已變更之實體的檔案，表示文字緩衝區時，對話方塊會顯示與訊息**您要儲存下列項目的變更嗎？** 這就是檔案變更通知。 如果檔案要許多變更，不過，不斷地顯示此對話方塊中可能很快就會造成困擾。  
  
 您以程式設計的方式可以抑制此對話方塊中，使用下列程序。 藉由隱藏對話方塊中，您可以重新載入檔案立即而不需要提示使用者每次儲存變更。  
  
## <a name="to-suppress-file-change-notification"></a>若要隱藏檔案變更通知  
  
1.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>方法來判斷哪一個文字緩衝區物件為您開啟的檔案與相關聯。  
  
2.  直接<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>要略過的記憶體中監視檔案變更所取得的物件<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>從介面<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>（文件資料） 物件，然後實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A>方法`fIgnore`參數若要設定`true`。  
  
3.  上呼叫方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>而<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>介面來更新記憶體中<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>（例如當欄位加入至您的元件） 的檔案變更的物件。  
  
4.  更新與變更的磁碟上的檔案，而不考慮任何暫止的編輯使用者可能會有進行中。  
  
     如此一來，當您直接<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>物件，以繼續監視檔案變更通知，在記憶體中的文字緩衝區會反映您所產生的變更。 文字緩衝區在記憶體中的也會反映所有暫止的編輯。 磁碟上的檔案會反映您所產生的最新的程式碼和任何先前在使用者編輯的程式碼中儲存使用者所做的變更。  
  
5.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A>方法來通知<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>物件，以繼續設定監視的檔案變更告知`fIgnore`參數來`false`。  
  
6.  如果您打算變更數個檔案，原始程式碼控制 (SCC)，為例，您必須告訴暫時暫止檔案變更告知的通用檔案變更服務。  
  
     例如，如果您重寫檔案，然後變更 時間戳記時，您必須先暫停檔案變更通知，因為重寫 」 和 「 時間戳記作業各計為個別的檔案變更事件。 若要啟用全域檔案變更通知，您應該改為呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A>方法。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何隱藏檔案變更通知。  
  
```cpp  
//Misc. helper classes  
  
CSuspendFileChanges::CSuspendFileChanges(  
    /* [in] */ const CString& strMkDocument,   
    /* [in] */ BOOL fSuspendNow /* = TRUE */)   
:  
    m_strMkDocument(strMkDocument),  
    m_fFileChangeSuspended(FALSE)  
{  
    if(fSuspendNow)  
        Suspend();  
}  
CSuspendFileChanges::~CSuspendFileChanges()  
{  
    Resume();  
}  
void CSuspendFileChanges::Suspend()  
{  
    USES_CONVERSION;  
  
    // Prevent suspend from suspending more than once.  
    if(m_fFileChangeSuspended)  
        return;  
  
    IVsRunningDocumentTable* pRDT =   
      _VxModule.GetIVsRunningDocumentTable();  
    ASSERT(pRDT);  
    if (!pRDT)  
        return;  
  
    CComPtr<IUnknown> srpDocData;  
    VSCOOKIE vscookie = VSCOOKIE_NIL;  
    pRDT->FindAndLockDocument(RDT_NoLock, T2COLE(m_strMkDocument),    
      NULL, NULL, &srpDocData, &vscookie);  
    if ( (vscookie == VSCOOKIE_NIL) || !srpDocData)  
        return;  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
    {  
        m_fFileChangeSuspended = TRUE;  
        srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, TRUE);   
        srpDocData->QueryInterface(IID_IVsDocDataFileChangeControl,   
          (void**)&m_srpIVsDocDataFileChangeControl);  
        if(m_srpIVsDocDataFileChangeControl)  
            m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(TRUE);  
    }  
}  
void CSuspendFileChanges::Resume()  
{  
    if(!m_fFileChangeSuspended)  
        return;  
  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
  
    srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, FALSE);   
    if(m_srpIVsDocDataFileChangeControl)  
        m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(FALSE);  
    m_fFileChangeSuspended = FALSE;  
    m_srpIVsDocDataFileChangeControl.Release();  
}  
// Misc. helper classes  
```  
  
## <a name="robust-programming"></a>穩固程式設計  
 如果您的案例牽涉到多個變更檔案，如同 SCC，情況則重要警示繼續監視檔案變更的文件資料之前繼續通用檔案變更通知。