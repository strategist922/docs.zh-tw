---
title: 1015 - StartCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bc317157ed7658a52aa60c9b74942f9e84d47257
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="1015---startcompletionworkitem"></a>1015 - StartCompletionWorkItem
## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|ID|1015|  
|關鍵字|WFRuntime|  
|層級|詳細資訊|  
|通道|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>描述  
 表示 CompletionWorkItem 開始執行。  
  
## <a name="message"></a>訊息  
 開始執行活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 CompletionWorkItem。 已完成活動 '%4'、DisplayName：'%5'、InstanceId：'%6'。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|ParentActivity|xs:string|父活動的型別名稱。|  
|ParentDisplayName|xs:string|父活動的顯示名稱。|  
|ParentInstanceId|xs:string|父活動的執行個體 ID。|  
|CompletedActivity|xs:string|已完成之活動的型別名稱。|  
|CompletedActivityDisplayName|xs:string|已完成之活動的顯示名稱。|  
|CompletedActivityInstanceId|xs:string|已完成之活動的執行個體 ID。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
