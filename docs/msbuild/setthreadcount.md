---
title: SetThreadCount | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
apiname:
- SetThreadCount
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SetThreadCount
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9cc9a1ae5f7fb51981f3cebc4d6fa658f614de6d
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151836"
---
# <a name="setthreadcount"></a>SetThreadCount
設定全域執行緒計數，並將該計數指派給目前的執行緒。  
  
## <a name="syntax"></a>語法  
  
```cmd  
HRESULT WINAPI SetThreadCount(int threadCount);  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `threadCount`  
 要使用的執行緒數目。  
  
## <a name="return-value"></a>傳回值  
 如已更新執行緒計數，則為 **HRESULT** 和已設定的 **SUCCEEDED** 位元。  
  
## <a name="requirements"></a>需求  
 **標頭：** *FileTracker.h*