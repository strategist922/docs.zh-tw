---
title: "逐步解說：在 WPF 中裝載 Direct3D9 內容"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5ad6ac99a77e3477499a871e269cc7faa7a59f12
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a>逐步解說：在 WPF 中裝載 Direct3D9 內容
本逐步解說示範如何裝載 Direct3D9 Windows Presentation Foundation (WPF) 應用程式中的內容。  
  
 在這個逐步解說中，您將執行下列工作：  
  
-   建立 WPF 專案以裝載 Direct3D9 內容。  
  
-   匯入 Direct3D9 內容。  
  
-   使用顯示 Direct3D9 內容<xref:System.Windows.Interop.D3DImage>類別。  
  
 當您完成時，您將了解如何裝載 Direct3D9 內容，在 WPF 應用程式。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
-   DirectX 9 或更新版本的 SDK。  
  
-   DLL 包含 Direct3D9 WPF 相容格式的內容。 如需詳細資訊，請參閱[WPF 和 Direct3D9 互通](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)和[逐步解說： 建立 Direct3D9 內容為裝載於 WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)。  
  
## <a name="creating-the-wpf-project"></a>建立 WPF 專案  
 第一個步驟是建立 WPF 應用程式的專案。  
  
#### <a name="to-create-the-wpf-project"></a>若要建立 WPF 專案  
  
-   建立新的 WPF 應用程式專案在 Visual C# 中名為`D3DHost`。 如需詳細資訊，請參閱[如何：建立新的 WPF 應用程式專案](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82)。  
  
     在中開啟 MainWindow.xaml [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]。  
  
## <a name="importing-the-direct3d9-content"></a>匯入 Direct3D9 內容  
 您所匯入 Direct3D9 內容從 unmanaged DLL`DllImport`屬性。  
  
#### <a name="to-import-direct3d9-content"></a>若要匯入 Direct3D9 內容  
  
1.  開啟 MainWindow.xaml.cs 在程式碼編輯器。  
  
2.  下列程式碼取代自動產生的程式碼。  
  
     [!code-csharp[System.Windows.Interop.D3DImage#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]  
  
## <a name="hosting-the-direct3d9-content"></a>裝載 Direct3D9 內容  
 最後，使用<xref:System.Windows.Interop.D3DImage>Direct3D9 內容裝載的類別。  
  
#### <a name="to-host-the-direct3d9-content"></a>要裝載 Direct3D9 內容  
  
1.  在 MainWindow.xaml 中，請以下列 XAML 取代自動產生的 XAML。  
  
     [!code-xaml[System.Windows.Interop.D3DImage#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]  
  
2.  建置專案。  
  
3.  複製包含 Direct3D9 內容至 bin/Debug 資料夾的 DLL。  
  
4.  按 F5 執行專案。  
  
     Direct3D9 內容會出現在 WPF 應用程式中。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Interop.D3DImage>  
 [Direct3D9 和 WPF 互通性的效能考量](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)
