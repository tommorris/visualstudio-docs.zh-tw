---
title: "IDebugBreakpointRequest2::GetRequestInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointRequest2::GetRequestInfo"
helpviewer_keywords: 
  - "IDebugBreakpointRequest2::GetRequestInfo"
ms.assetid: 5defd8d7-6daa-479b-8909-fcc4ae0b357a
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugBreakpointRequest2::GetRequestInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得描述這個中斷點要求中斷點要求資訊。  
  
## 語法  
  
```cpp#  
HRESULT GetRequestInfo(   
   BPREQI_FIELDS    dwFields,  
   BP_REQUEST_INFO* pBPRequestInfo  
);  
```  
  
```c#  
int GetRequestInfo(   
   eunm_BPREQI_FIELDS  dwFields,  
   BP_REQUEST_INFO[]   pBPRequestInfo  
);  
```  
  
#### 參數  
 `dwFields`  
 \[in\]從的旗標組合[BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)列舉型別，以判斷哪些欄位`pBPRequestInfo`參數都必須填寫。  
  
 `pBPRequestInfo`  
 \[\] out指定[BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)好填入這些中斷點要求的描述的結構。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 範例  
 下列範例會示範如何實作這個方法，如`CDebugBreakpointRequest`物件，公開 \(expose\) [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)介面。  
  
```  
HRESULT CDebugBreakpointRequest::GetRequestInfo(  
   BPREQI_FIELDS    dwFields,  
   BP_REQUEST_INFO* pBPRequestInfo)    
{    
   HRESULT hr;    
  
   if (pBPRequestInfo)    
   {    
      // Copy the specified fields of the request info from the class  
      // member variable to the local BP_REQUEST_INFO variable.    
      hr = CopyBP_REQUEST_INFO(m_bpRequestInfo,  
                               *pBPRequestInfo, dwFields);    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
  
HRESULT CDebugBreakpointRequest::CopyBP_REQUEST_INFO(  
   BP_REQUEST_INFO& bpReqSrc,  
   BP_REQUEST_INFO& bpReqDest,  
   DWORD dwFields)    
{    
   HRESULT hr = S_OK;    
  
   // Start with a raw copy.    
   memcpy(&bpReqDest, &bpReqSrc, sizeof (BP_REQUEST_INFO));    
  
   // The fields in the destination are the result of the AND of  
   // bpReqSrc.dwFields and dwFields.    
   bpReqDest.dwFields = dwFields & bpReqSrc.dwFields;    
  
   // Fill in the bp location information if the BPREQI_BPLOCATION flag is  
   // set in BPREQI_FIELDS.    
   if (IsFlagSet(bpReqDest.dwFields, BPREQI_BPLOCATION))    
   {    
      // Switch based on the BP_LOCATION_TYPE.      
      switch (bpReqSrc.bpLocation.bpLocationType)    
      {    
         case BPLT_CODE_FILE_LINE:    
         {    
            // Copy the bstrContext and AddRef the IDebugDocumentPosition2  
            // of the BP_LOCATION_CODE_FILE_LINE structure.    
            bpReqDest.bpLocation.bpLocation.bplocCodeFileLine.bstrContext =  
               SysAllocString(bpReqSrc.bpLocation.bpLocation.bplocCodeFileLine.bstrContext);    
            bpReqDest.bpLocation.bpLocation.bplocCodeFileLine.pDocPos->AddRef();    
            break;    
         }    
         case BPLT_CODE_FUNC_OFFSET:    
         {    
            // Copy the bstrContext and AddRef the IDebugFunctionPosition2  
            // of the BP_LOCATION_CODE_FUNC_OFFSET structure.    
            bpReqDest.bpLocation.bpLocation.bplocCodeFuncOffset.bstrContext =  
               SysAllocString(bpReqSrc.bpLocation.bpLocation.bplocCodeFuncOffset.bstrContext);    
            bpReqDest.bpLocation.bpLocation.bplocCodeFuncOffset.pFuncPos->AddRef();    
            break;    
         }    
         case BPLT_CODE_CONTEXT:    
         {    
            // AddRef the IDebugCodeContext2 of the BP_LOCATION_CODE_CONTEXT  
            // structure.    
            bpReqDest.bpLocation.bpLocation.bplocCodeContext.pCodeContext->AddRef();    
            break;    
         }    
         case BPLT_CODE_STRING:    
         {    
            // Copy the bstrContext and bstrCodeExpr of the BP_LOCATION_CODE_STRING  
            // structure.    
            bpReqDest.bpLocation.bpLocation.bplocCodeString.bstrContext =  
               SysAllocString(bpReqSrc.bpLocation.bpLocation.bplocCodeString.bstrContext);    
            bpReqDest.bpLocation.bpLocation.bplocCodeString.bstrCodeExpr =  
               SysAllocString(bpReqSrc.bpLocation.bpLocation.bplocCodeString.bstrCodeExpr);    
            break;    
         }    
         case BPLT_CODE_ADDRESS:    
         {    
            // Copy the bstrContext, bstrModuleUrl, bstrFunction, and bstrAddress  
            // of the BP_LOCATION_CODE_ADDRESS structure.    
            bpReqDest.bpLocation.bpLocation.bplocCodeAddress.bstrContext =  
               SysAllocString(bpReqSrc.bpLocation.bpLocation.bplocCodeAddress.bstrContext);    
            bpReqDest.bpLocation.bpLocation.bplocCodeAddress.bstrModuleUrl =  
               SysAllocString(bpReqSrc.bpLocation.bpLocation.bplocCodeAddress.bstrModuleUrl);    
            bpReqDest.bpLocation.bpLocation.bplocCodeAddress.bstrFunction =  
               SysAllocString(bpReqSrc.bpLocation.bpLocation.bplocCodeAddress.bstrFunction);    
            bpReqDest.bpLocation.bpLocation.bplocCodeAddress.bstrAddress =  
               SysAllocString(bpReqSrc.bpLocation.bpLocation.bplocCodeAddress.bstrAddress);    
            break;    
         }    
         case BPLT_DATA_STRING:    
         {    
            // Conditional AddRef of the IDebugThread2 of the BP_LOCATION_DATA_STRING  
            // structure.    
            if (bpReqDest.bpLocation.bpLocation.bplocDataString.pThread)    
            {    
               bpReqDest.bpLocation.bpLocation.bplocDataString.pThread->AddRef();    
            }    
            // Copy the bstrContext and bstrDataExpr of the BP_LOCATION_DATA_STRING  
            // structure.    
            bpReqDest.bpLocation.bpLocation.bplocDataString.bstrContext =  
                  SysAllocString(bpReqSrc.bpLocation.bpLocation.bplocDataString.bstrContext);    
            bpReqDest.bpLocation.bpLocation.bplocDataString.bstrDataExpr =  
                  SysAllocString(bpReqSrc.bpLocation.bpLocation.bplocDataString.bstrDataExpr);    
            break;    
         }    
         case BPLT_RESOLUTION:    
         {    
            // AddRef of the IDebugBreakpointResolution2 of the BP_LOCATION_RESOLUTION  
            // structure.    
            bpReqDest.bpLocation.bpLocation.bplocResolution.pResolution->AddRef();    
            break;    
         }    
         default:    
         {    
            assert(FALSE);    
            // Clear the BPREQI_BPLOCATION flag in the BPREQI_FIELDS of the  
            // destination BP_REQUEST_INFO.    
            ClearFlag(bpReqDest.dwFields, BPREQI_BPLOCATION);    
            break;    
         }    
      }    
   }    
   // AddRef the IDebugProgram2 if the BPREQI_PROGRAM flag is set in BPREQI_FIELDS.    
   if (IsFlagSet(bpReqDest.dwFields, BPREQI_PROGRAM))    
   {    
      bpReqDest.pProgram->AddRef();    
   }     
   // Copy the bstrProgramName if the BPREQI_PROGRAMNAME flag is set in BPREQI_FIELDS.    
   if (IsFlagSet(bpReqDest.dwFields, BPREQI_PROGRAMNAME))    
   {    
      bpReqDest.bstrProgramName = SysAllocString(bpReqSrc.bstrProgramName);    
   }    
   // AddRef the IDebugThread2 if the BPREQI_THREAD flag is set in BPREQI_FIELDS.    
   if (IsFlagSet(bpReqDest.dwFields, BPREQI_THREAD))    
   {    
      bpReqDest.pThread->AddRef();    
   }    
   // Copy the bstrThreadName if the BPREQI_THREADNAME flag is set in BPREQI_FIELDS.    
   if (IsFlagSet(bpReqDest.dwFields, BPREQI_THREADNAME))    
   {    
      bpReqDest.bstrThreadName = SysAllocString(bpReqSrc.bstrThreadName);    
   }    
   // Check to see if the BPREQI_CONDITION flag is set in BPREQI_FIELDS.    
   if (IsFlagSet(bpReqDest.dwFields, BPREQI_CONDITION))    
   {    
      // Conditional AddRef of the IDebugThread2 of the BP_CONDITION structure.    
      if (bpReqDest.bpCondition.pThread)    
      {    
         bpReqDest.bpCondition.pThread->AddRef();    
      }    
      // Copy the bstrContext and bstrCondition of the BP_CONDITION structure.    
      bpReqDest.bpCondition.bstrContext = SysAllocString(bpReqSrc.bpCondition.bstrContext);    
      bpReqDest.bpCondition.bstrCondition = SysAllocString(bpReqSrc.bpCondition.bstrCondition);    
   }    
  
   return hr;    
}    
```  
  
## 請參閱  
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)