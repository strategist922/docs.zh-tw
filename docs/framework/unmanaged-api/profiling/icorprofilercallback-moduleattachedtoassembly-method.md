---
title: "ICorProfilerCallback::ModuleAttachedToAssembly 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ModuleAttachedToAssembly
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ModuleAttachedToAssembly
helpviewer_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly method [.NET Framework profiling]
- ModuleAttachedToAssembly method [.NET Framework profiling]
ms.assetid: b595798a-5d40-4cac-ab4f-911c61d2c5d2
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6183014bf5487d0eebccf2fb70a13c363212046b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a>ICorProfilerCallback::ModuleAttachedToAssembly 方法
通知分析工具模組要附加到其父組件。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
#### <a name="parameters"></a>參數  
 `moduleId`  
 [in]要附加的模組識別碼。  
  
 `AssemblyId`  
 [in]要附加之模組的父組件識別碼。  
  
## <a name="remarks"></a>備註  
 可以透過匯入位址表 (IAT)，載入模組，透過呼叫`LoadLibrary`，或透過中繼資料參考。 如此一來，common language runtime (CLR) 載入器有多個程式碼路徑，以判斷模組存在所在的組件。 因此，可能會之後[icorprofilercallback:: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)呼叫時，此模組並不知道哪一個組件處於和取得父組件識別碼不可行。 `ModuleAttachedToAssembly`模組附加至其父組件和識別碼可透過其父組件時，呼叫方法。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
