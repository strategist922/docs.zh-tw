---
title: "事件和回呼"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 39dd4e31e84e455b72ce53bd8abffd650ce77dfc
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="events-and-callbacks"></a>事件和回呼
回呼是延伸點，可允許呼叫委派透過使用者程式碼的架構。 這些委派通常會透過方法的參數傳遞給架構。  
  
 事件是回呼的支援方便且一致的語法提供委派 （事件處理常式） 的特殊案例。 此外，Visual Studio 的陳述式完成和設計工具提供說明中使用以事件為基礎的 Api。 (請參閱[事件設計](../../../docs/standard/design-guidelines/event.md)。)  
  
 **✓ 考慮**使用回呼，以允許使用者提供架構所執行的自訂程式碼。  
  
 **✓ 考慮**使用事件可讓使用者自訂的架構，而不需要了解物件導向設計的行為。  
  
 **✓ 不要**而不用事件純文字的回呼，因為它們是更廣泛的開發人員熟悉，而且會與 Visual Studio 陳述式完成整合。  
  
 **請避免 x**重視效能的 Api 中使用回呼。  
  
 **✓ 不要**使用新`Func<...>`， `Action<...>`，或`Expression<...>`類型而不是自訂委派，定義應用程式開發介面，以回撥時。  
  
 `Func<...>`和`Action<...>`代表的泛型委派。 `Expression<...>`代表函式定義可編譯及後續叫用執行階段，但也會序列化，並傳遞給遠端處理程序。  
  
 **✓ 不要**衡量並且了解使用的效能含意`Expression<...>`，而不是使用`Func<...>`和`Action<...>`委派。  
  
 `Expression<...>`類型會在大部分的情況下，邏輯上相當於`Func<...>`和`Action<...>`委派。 主要差異是，為了將委派用於本機處理序的案例;運算式被供情況下，很有幫助和可能用於評估的運算式，在遠端處理序或電腦中。  
  
 **✓ 不要**了解呼叫委派時，您會執行任意程式碼，並可能會有安全性、 正確性，以及相容性的影響。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>請參閱  
 [擴充性設計](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
