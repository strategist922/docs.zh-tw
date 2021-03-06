---
title: "停用 WPF 應用程式的 RealTimeStylus"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 71fc4ec888419e385a57216f078387f731c0ab8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a>停用 WPF 應用程式的 RealTimeStylus
Windows Presentation Foundation (WPF) 有內建支援來處理 Windows 7 具備觸控輸入。支援是透過 tablet 平台的即時手寫筆輸入<xref:System.Windows.UIElement.OnStylusDown%2A>， <xref:System.Windows.UIElement.OnStylusUp%2A>，和<xref:System.Windows.UIElement.OnStylusMove%2A>事件。 Windows 7 也會提供多點觸控輸入做為 Win32 WM_TOUCH 視窗訊息。 這些兩個 Api 互斥上相同的 HWND。 啟用觸控輸入透過 tablet 平台 （WPF 應用程式的預設值） 會停用 WM_TOUCH 訊息。 如此一來，若要使用 WM_TOUCH 接收來自 WPF 視窗的觸控式訊息，您必須停用在 WPF 中的內建的手寫筆支援。 這也適用於裝載使用 WM_TOUCH 的元件，為 WPF 視窗等狀況中。  
  
 若要停用 WPF 接聽手寫筆輸入，移除任何新增的 WPF 視窗的平板電腦支援。  
  
## <a name="example"></a>範例  
 下列範例程式碼會示範如何使用反映來移除預設平板電腦平台支援。  
  
```  
public static void DisableWPFTabletSupport()  
{  
    // Get a collection of the tablet devices for this window.    
    TabletDeviceCollection devices = System.Windows.Input.Tablet.TabletDevices;  
  
    if (devices.Count > 0)  
    {     
        // Get the Type of InputManager.  
        Type inputManagerType = typeof(System.Windows.Input.InputManager);  
  
        // Call the StylusLogic method on the InputManager.Current instance.  
        object stylusLogic = inputManagerType.InvokeMember("StylusLogic",  
                    BindingFlags.GetProperty | BindingFlags.Instance | BindingFlags.NonPublic,  
                    null, InputManager.Current, null);  
  
        if (stylusLogic != null)  
        {  
            //  Get the type of the stylusLogic returned from the call to StylusLogic.  
            Type stylusLogicType = stylusLogic.GetType();  
  
            // Loop until there are no more devices to remove.  
            while (devices.Count > 0)  
            {  
                // Remove the first tablet device in the devices collection.  
                stylusLogicType.InvokeMember("OnTabletRemoved",  
                        BindingFlags.InvokeMethod | BindingFlags.Instance | BindingFlags.NonPublic,  
                        null, stylusLogic, new object[] { (uint)0 });  
            }                  
        }  
  
    }  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [攔截手寫筆的輸入](../../../../docs/framework/wpf/advanced/intercepting-input-from-the-stylus.md)
