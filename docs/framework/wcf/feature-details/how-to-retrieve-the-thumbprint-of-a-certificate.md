---
title: "HOW TO：擷取憑證的指紋"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: certificates [WCF], retrieving thumbprint
ms.assetid: da3101aa-78cd-4c34-9652-d1f24777eeab
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f6d00d31023aa8d6dbfec4a8306f1cb9da17c74
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-retrieve-the-thumbprint-of-a-certificate"></a>HOW TO：擷取憑證的指紋
撰寫使用 X.509 憑證進行驗證的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 應用程式時，通常需要指定在憑證中找到的宣告。 例如，當您在 <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> 方法中使用 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> 列舉時，就必須提供指紋宣告。 尋找宣告值時，需要兩個步驟。 首先，開啟憑證的 Microsoft Management Console (MMC) 嵌入式管理單元 (請參閱 [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md))。接著，如此處所描述，尋找適當的憑證並複製其指紋 (或其他宣告值)。  
  
 如果您在服務驗證中使用憑證，則記下 [ **核發給** ] 欄位 (主控台中的第一欄) 之值是相當重要的。 使用 Secure Sockets Layer (SSL) 做為傳輸安全性時，前幾項檢查其中完成的一項，就是比較服務之統一資源識別元 (URI) 的基底位址和 [ **核發給** ] 的值。 這些值必須相符，否則會中止驗證程序。  
  
 您也可以使用 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SDK 的 Makecert.exe 工具，以建立僅在開發期間使用的暫存憑證。 然而，這類憑證預設不是由憑證授權單位所發出，而且無法用於生產目的。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][How to： 在開發期間建立暫時憑證，供](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)。  
  
### <a name="to-retrieve-a-certificates-thumbprint"></a>若要擷取憑證的指紋  
  
1.  開啟憑證的 Microsoft Management Console (MMC) 嵌入式管理單元 (請參閱 [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md))。  
  
2.  在 [ **主控台根目錄** ] 視窗的左窗格中，按一下 [ **憑證 (本機電腦)**]。  
  
3.  按一下 [ **個人** ] 資料夾以展開。  
  
4.  按一下 [ **憑證** ] 資料夾以展開。  
  
5.  在憑證清單中，請記下 [ **使用目的** ] 的標題。 尋找會將 [ **用戶端驗證** ] 列為使用目的之憑證。  
  
6.  按兩下憑證。  
  
7.  在 [ **憑證** ] 對話方塊中，按一下 [ **詳細資料** ] 索引標籤。  
  
8.  捲動欄位清單，並按一下 [ **指紋**]。  
  
9. 複製方塊中的十六進位字元。 如果是針對 `X509FindType`在程式碼中使用此指紋，請移除十六進位數字之間的空格。 例如，在程式碼中應該將指紋 "a9 09 50 2d d8 2a e4 14 33 e6 f8 38 86 b0 0d 42 77 a3 2a 7b" 指定為 "a909502dd82ae41433e6f83886b00d4277a32a7b"。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>  
 [如何：使用 SSL 憑證設定連接埠](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [如何：使用 MMC 嵌入式管理單元來檢視憑證](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [如何：建立開發時要使用的暫時憑證](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
