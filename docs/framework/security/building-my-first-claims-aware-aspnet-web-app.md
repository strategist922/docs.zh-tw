---
title: "建置第一個宣告感知 ASP.NET Web 應用程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ee8ee7f-caba-4267-9343-e313fae2876d
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 182f7c1646e112026852efcb5bb110607fe19360
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="building-my-first-claims-aware-aspnet-web-application"></a>建置第一個宣告感知 ASP.NET Web 應用程式
## <a name="applies-to"></a>適用於  
  
-   Windows Identity Foundation (WIF)  
  
-   ASP.NET  
  
 本主題概述使用 WIF 建置宣告感知 ASP.NET Web 應用程式的案例。 在一個宣告感知應用程式案例中，通常會有三個參與者：應用程式本身、使用者和 Security Token Service (STS)。 下列圖將說明這個案例：  
  
 ![WIF 基本 Web 應用程式](../../../docs/framework/security/media/wifbasicwebapp.gif "WIFBasicWebApp")  
  
1.  宣告感知應用程式使用 WIF 識別未驗證的要求，並將它們重新導向至 STS。  
  
2.  使用者提供認證給 STS，一旦驗證成功，STS 就會發行權杖給使用者。  
  
3.  使用者從 STS 重新導向至宣告感知應用程式，並且要求中已包含 STS 發行的權杖。  
  
4.  宣告感知應用程式設定為信任 STS 和它發行的權杖。 宣告感知應用程式會使用 WIF 驗證和剖析權杖。 開發人員可以使用適當的 WIF API 和類型 (例如 **ClaimsPrincpal**) 來滿足應用程式的需求 (例如為它實作授權)。  
  
 從 .NET 4.5 開始，WIF 是 .NET Framework 套件的一部分。 在架構中直接提供 WIF 類別可讓 .NET 中的宣告式身分識別的整合更加深入，讓您更容易使用宣告。 使用 WIF 4.5，您不必安裝任何超出範圍的元件就能開始開發宣告感知 Web 應用程式。 WIF 類別現在已廣泛存在於各種組件，主要的類別是 System.Security.Claims、System.IdentityModel 和 System.IdentityModel.Services。  
  
 STS 服務會在驗證成功後發行權杖。 Microsoft 提供兩項業界標準 STS：  
  
-   [Active Directory Federation Services (AD FS) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516) (http://go.microsoft.com/fwlink/?LinkID=247516)  
  
-   [Windows Azure 存取控制服務 (ACS)](http://go.microsoft.com/fwlink/?LinkID=247517) (http://go.microsoft.com/fwlink/?LinkID=247517)。  
  
 AD FS 2.0 是 Windows Server R2 的一部分，可以當做供內部部署案例使用的 STS； ACS 則是當做 Microsoft Azure 平台的一部分而提供的雲端服務。 此外，基於測試或教育目的，您也可以使用其他 STS 建立專屬宣告感知應用程式。 例如，您可以使用包含在 [Identity and Access Tool for Visual Studio](http://go.microsoft.com/fwlink/?LinkID=245849) (適用於 Visual Studio 的識別和存取工具) (http://go.microsoft.com/fwlink/?LinkID=245849) (可在線上免費取得) 中的本機開發 STS。  
  
 若要使用 WIF 建立您的第一個宣告感知 ASP.NET 應用程式，請遵循下列其中一項指示執行：  
  
-   [操作說明：使用 WIF 建置宣告感知 ASP.NET MVC Web 應用程式](../../../docs/framework/security/how-to-build-claims-aware-aspnet-mvc-web-app-using-wif.md)  
  
-   [操作說明：使用 WIF 建置宣告感知 ASP.NET Web Form 應用程式](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)  
  
-   [操作說明：使用表單型驗證建置宣告感知 ASP.NET 應用程式](../../../docs/framework/security/claims-aware-aspnet-app-forms-authentication.md)  
  
## <a name="see-also"></a>請參閱  
 [開始使用 WIF](../../../docs/framework/security/getting-started-with-wif.md)
