---
title: "ICorDebugManagedCallback2::Exception 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.Exception
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::Exception
helpviewer_keywords:
- ICorDebugManagedCallback2::Exception method [.NET Framework debugging]
- Exception method, ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: 78b0f14f-2fae-4e63-8412-4df119ee8468
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79a8fa4709aeb04164bd1c2da07607435b76fff5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2exception-method"></a>ICorDebugManagedCallback2::Exception 方法
告知偵錯工具搜尋例外狀況處理常式已開始。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pAppDomain`  
 [in]表示包含擲回例外狀況所在的執行緒的應用程式網域的 ICorDebugAppDomain 物件指標。  
  
 `pThread`  
 [in]表示擲回例外狀況所在的執行緒 ICorDebugThread 物件的指標。  
  
 `pFrame`  
 [in]ICorDebugFrame 物件，表示在範圍內，由指標`dwEventType`參數。 如需詳細資訊，請參閱 < 備註 > 一節中的資料表。  
  
 `nOffset`  
 [in]整數，取決於指定位移，`dwEventType`參數。 如需詳細資訊，請參閱 < 備註 > 一節中的資料表。  
  
 `dwEventType`  
 [in]指定此例外狀況回呼類型 CorDebugExceptionCallbackType 列舉值。  
  
 `dwFlags`  
 [in]值為[CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)列舉，指定例外狀況的其他資訊  
  
## <a name="remarks"></a>備註  
 `Exception`回呼例外狀況處理程序的搜尋階段期間，會呼叫在不同時間點。 也就是說，它可以呼叫超過一次而回溯例外狀況。  
  
 正在處理的例外狀況可以從所參考的 ICorDebugThread 物件擷取`pThread`參數。  
  
 特定的畫面格和位移，由`dwEventType`參數，如下所示：  
  
|`dwEventType` 的值|`pFrame` 的值|`nOffset` 的值|  
|----------------------------|-----------------------|------------------------|  
|DEBUG_EXCEPTION_FIRST_CHANCE|擲回例外狀況框架。|指令指標框架中。|  
|DEBUG_EXCEPTION_USER_FIRST_CHANCE|最接近擲回的例外狀況位置之使用者程式碼框架。|指令指標框架中。|  
|DEBUG_EXCEPTION_CATCH_HANDLER_FOUND|包含 catch 處理常式的框架。|Catch 處理常式開頭的 Microsoft intermediate language (MSIL) 位移。|  
|DEBUG_EXCEPTION_UNHANDLED|NULL|未定義。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [ICorDebugManagedCallback2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [ICorDebugManagedCallback 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
