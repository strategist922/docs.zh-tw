---
title: "_EFN_GetManagedExcepStack 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _EFN_GetManagedExcepStack
api_location: mscordbi.dll
api_type: COM
f1_keywords: _EFN_GetManagedExcepStack
helpviewer_keywords: _EFN_GetManagedExcepStack function [.NET Framework debugging]
ms.assetid: 21ceed9e-62b2-4024-b027-6d095109955a
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: edcd93bec29c6f0fef3b0bed4b8293efead3932d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="efngetmanagedexcepstack-function"></a>_EFN_GetManagedExcepStack 函式
給予 Managed 例外狀況物件位址後，會傳回內部包含堆疊追蹤版本的字串。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
#### <a name="parameters"></a>參數  
 `Client`  
 [in]用戶端進行偵錯。  
  
 `StackObjAddr`  
 [in]Managed 的物件指標，衍生自<xref:System.Exception>。  
  
 szStackString  
 [out]傳回的字串。  
  
 `cbString`  
 [out]在字串緩衝區中的字元數。  
  
## <a name="remarks"></a>備註  
 如果沒有任何 managed 程式碼的執行緒上目前內容中，函數會傳回 HRESULT SOS_E_NOMANAGEDCODE 0xa0 設備值與 0x1000 錯誤碼。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** SOS_Stacktrace.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [偵錯全域靜態函式](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
