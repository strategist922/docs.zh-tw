---
title: "AssemblyOptions 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyOptions
api_location: alink.dll
api_type: COM
f1_keywords: AssemblyOptions
helpviewer_keywords:
- Alink API, AssemblyOptions enumeration
- AssemblyOptions enumeration
ms.assetid: 84f83921-64cb-49e3-ac8b-22a0b77b18a8
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6ad4f9e02ed0d22009fcb8a5ac078231f2cb22e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="assemblyoptions-enumeration"></a>AssemblyOptions 列舉
列舉組件的選項。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum _AssemblyOptions {  
    optAssemTitle = 0,  
    optAssemDescription,  
    optAssemConfig,  
    optAssemOS,  
    optAssemProcessor,  
    optAssemLocale,  
    optAssemVersion,  
    optAssemCompany,  
    optAssemProduct,  
    optAssemProductVersion,  
    optAssemCopyright,  
    optAssemTrademark,  
    optAssemKeyFile,  
    optAssemKeyName,  
    optAssemAlgID,  
    optAssemFlags,  
    optAssemHalfSign,  
    optAssemFileVersion,  
    optAssemSatelliteVer,  
    optLastAssemOption  
}   AssemblyOptions;  
```  
  
## <a name="fields"></a>欄位  
  
|欄位|描述|  
|-----------|-----------------|  
|optAssemTitle|字串-代表組件標題。|  
|optAssemDescription|字串-包含組件描述。|  
|optAssemConfig|字串-包含組件組態。|  
|optAssemOS|字串的編碼為:"dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion"。|  
|optAssemProcessor|ULONG|  
|optAssemLocale|字串-包含組件的地區設定。|  
|optAssemVersion|字串的編碼為:"Major.Minor.Build.Revision"。|  
|optAssemCompany|字串-包含公司。|  
|optAssemProduct|字串-包含產品名稱。|  
|optAssemProductVersion|字串 (也稱為 InformationalVersion)。|  
|optAssemCopyright|字串-包含著作權資訊。|  
|optAssemTrademark|字串-包含商標資訊。|  
|optAssemKeyFile|字串 （檔案名稱）。|  
|optAssemKeyName|字串 （機碼名稱）。|  
|optAssemAlgID|ULONG|  
|optAssemFlags|ULONG|  
|optAssemHalfSign|Bool （也稱為 DelaySign）。|  
|optAssemFileVersion|字串的編碼為"Major.Minor.Build.Revision"-ProductVersion 相同。|  
|optAssemSatelliteVer|字串的編碼為"Major.Minor.Build.Revision"。|  
|optLastAssemOption|元素數目的計數器。|  
  
## <a name="requirements"></a>需求  
 **標頭：** alink.h  
  
 **程式庫**: alink.dll  
  
## <a name="see-also"></a>請參閱  
 [Al.exe (組件連結器)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
