---
title: "&lt;httpDigest&gt; 項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 95e6a7d31949bd7a6badb029e3f768a63fbaf924
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="lthttpdigestgt-element"></a>&lt;httpDigest&gt; 項目
指定對服務驗證用戶端時，所使用的摘要式類型認證。  
  
 \<系統。ServiceModel >  
\<行為 >  
\<endpointBehaviors >  
\<行為 >  
\<clientCredentials >  
\<httpDigest >  
  
## <a name="syntax"></a>語法  
  
```xml  
<digest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`impersonationLevel`|設定用戶端與伺服器通訊的模擬喜好設定。 用戶端選取的模擬模式不會在伺服器上強制使用。 有效值包括以下的值：<br /><br /> -Identification： 伺服器可取得的身分識別和權限的用戶端，但無法模擬用戶端。<br />模擬： 伺服器可以模擬用戶端的本機系統上的安全性內容。<br />-Delegation： 伺服器可以模擬用戶端的安全性內容，在遠端系統上。<br />匿名： 伺服器無法模擬或識別用戶端。<br />-無： 模擬層級未指派。<br /><br /> 預設為 Identification。 此屬性的型別為 <xref:System.Security.Principal.TokenImpersonationLevel>。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|指定用來對服務驗證用戶端的認證。|  
  
## <a name="remarks"></a>備註  
 摘要是指使用演算法和一組輸入所決定的雜湊。 驗證者和被驗證者一致同意某個演算法，並交換做為輸入的資料。 用戶端可計算雜湊，並將它傳送至服務。 服務也會計算雜湊並比較兩者的值。 比對會驗證用戶端。  
  
 此功能必須與 Windows 和 Internet Information Services (IIS) 上的 Active Directory 一起啟用。 [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][摘要式驗證在 IIS 6.0](http://go.microsoft.com/fwlink/?LinkId=88443)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>  
 <xref:System.ServiceModel.Configuration.HttpDigestClientElement>  
 <xref:System.ServiceModel.Security.HttpDigestClientCredential>  
 [安全性行為](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [保護用戶端安全](../../../../../docs/framework/wcf/securing-clients.md)  
 [使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [保護服務和用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
