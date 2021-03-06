---
title: "ISymUnmanagedWriter::Initialize 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.Initialize
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::Initialize
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: e0ebd793-3764-4df0-8f12-0e95f60b9eae
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 737e6b5218d51d8a1a051104ecdd11240a2ddac6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterinitialize-method"></a>ISymUnmanagedWriter::Initialize 方法
設定與這個寫入器將會在相關的中繼資料發出器介面，並將偵錯符號寫入的輸出檔名稱。  
  
 一次，呼叫這個方法，它必須進行任何其他寫入器方法之前呼叫。 有些寫入器可能需要的檔案名稱。 不過，您一律可以檔案名稱傳遞至這個方法沒有任何未使用的檔案名稱的寫入器上的負面影響。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
#### <a name="parameters"></a>參數  
 `emitter`  
 [in]中繼資料發出器介面指標。  
  
 `filename`  
 [in]偵錯符號寫入的檔案名稱。 如果檔案名稱是指定給不使用檔案名稱的寫入器，則這個參數會被忽略。  
  
 `pIStream`  
 [in]如果指定，符號寫入器會發出符號插入給定<xref:System.Runtime.InteropServices.ComTypes.IStream>，而不是檔案中指定`filename`參數。 `pIStream` 是選擇性參數。  
  
 `fFullBuild`  
 [in]`true`如果這是完整重建;`false`如果這是累加編譯。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭：**於 CorSym.idl、 CorSym.h  
  
## <a name="see-also"></a>請參閱  
 [ISymUnmanagedWriter 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [Initialize2 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)
