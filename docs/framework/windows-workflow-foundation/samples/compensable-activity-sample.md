---
title: "可補償的活動範例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58f4898c-b2b8-44a4-9a73-3bef4da6d5ba
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b2fd8d38e95dbddbe85f11bf88ef500697b6c02a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="compensable-activity-sample"></a>可補償的活動範例
這個範例示範如何使用 `CompensableActivity` 活動，定義一般執行期間針對給定動作所執行的工作，以及稍後如有需要，為了補償該動作所必須執行的工作。  範例的第一個部分示範如何使用 [!INCLUDE[wf](../../../../includes/wf-md.md)] 活動，在 `CompensableActivity` 中定義可補償的工作單位，以及成功執行時這些工作單位如何執行。  範例的第二個部分示範當發生未預期的事件，工作流程執行個體取消時，相同的可補償工作單位如何自動處理補償。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  使用 Visual Studio 2010 開啟 CompensableActivity.sln。  
  
2.  按 CTRL+SHIFT+B 建置此方案。  
  
3.  按 F5 鍵執行應用程式。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\BasicCompensableActivity`