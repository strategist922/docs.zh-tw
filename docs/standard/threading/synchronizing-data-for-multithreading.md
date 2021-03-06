---
title: "同步處理多執行緒處理的資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- synchronization, threads
- threading [.NET Framework], synchronizing threads
- managed threading
ms.assetid: b980eb4c-71d5-4860-864a-6dfe3692430a
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a17eba2f930fda06d643d78c73c117e89ae86928
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="synchronizing-data-for-multithreading"></a>同步處理多執行緒處理的資料
當多個執行緒可以對單一物件的屬性和方法進行呼叫時，請務必同步處理這些呼叫。 否則某個執行緒可能會中斷另一個執行緒正在執行的作業，而且物件可能會處於無效狀態。 其成員受到保護免於這種中斷的類別，稱為安全執行緒。  
  
 通用語言基礎結構提供幾種策略來同步存取執行個體和靜態成員︰  
  
-   同步程式碼區域。 您可以使用<xref:System.Threading.Monitor>類別或是編譯器的這個類別，以同步處理程式碼區塊，僅支援需要可改善效能。  
  
-   手動同步處理。 您可以使用 .NET Framework 類別庫提供的同步處理物件。 請參閱[同步處理原始物件概觀](../../../docs/standard/threading/overview-of-synchronization-primitives.md)，其中包含的討論<xref:System.Threading.Monitor>類別。  
  
-   同步處理的內容。 您可以使用<xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>啟用簡單、 自動同步處理的<xref:System.ContextBoundObject>物件。  
  
-   中的集合類別<xref:System.Collections.Concurrent?displayProperty=nameWithType>命名空間。 這些類別會提供內建同步處理新增和移除作業。 如需詳細資訊，請參閱[安全執行緒集合](../../../docs/standard/collections/thread-safe/index.md)。  
  
 通用語言執行平台提供執行緒模型，其中類別分為一些分類，可以根據需求以各種不同的方式同步處理。 下表顯示為指定同步處理分類的欄位和方法提供哪些同步處理支援。  
  
|分類|全域欄位|靜態欄位|靜態方法|執行個體欄位|執行個體方法|特定程式碼區塊|  
|--------------|-------------------|-------------------|--------------------|---------------------|----------------------|--------------------------|  
|沒有同步處理|否|否|否|否|否|否|  
|同步處理的內容|否|否|否|是|是|否|  
|同步程式碼區域|否|否|只有當標記時|否|只有當標記時|只有當標記時|  
|手動同步處理|手動|手動|手動|手動|手動|手動|  
  
## <a name="no-synchronization"></a>沒有同步處理  
 這是物件的預設值。 任何執行緒可以隨時存取任何方法或欄位。 一次應該只有一個執行緒存取這些物件。  
  
## <a name="manual-synchronization"></a>手動同步處理  
 .NET Framework 類別庫提供一些類別來同步處理執行緒。 請參閱[同步處理原始物件概觀](../../../docs/standard/threading/overview-of-synchronization-primitives.md)。  
  
## <a name="synchronized-code-regions"></a>同步程式碼區域  
 您可以使用<xref:System.Threading.Monitor>類別或編譯器關鍵字來同步處理的程式碼中，執行個體方法和靜態方法的區塊。 不支援同步處理的靜態欄位。  
  
 Visual Basic 和 C# 都支援使用特定語言關鍵字來標示程式碼區塊，在 C# 中為 `lock`陳述式，在 Visual Basic 中為 `SyncLock` 陳述式。 由執行緒執行程式碼時，會嘗試取得鎖定。 如果已經由另一個執行緒取得鎖定，則執行緒會封鎖，直到鎖定可用為止。 當執行緒結束已同步處理的程式碼區塊時，鎖定會被釋放，不論執行緒如何結束區塊。  
  
> [!NOTE]
>  `lock`和`SyncLock`陳述式會使用實作<xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType>和<xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType>，讓其他方法<xref:System.Threading.Monitor>可用於額外搭配這些同步處理的區域內。  
  
 您也可以使用 **MethodImplAttribute** 和 **MethodImplOptions.Synchronized** 來裝飾方法，其效果與使用 [監視] 或其中一個編譯器關鍵字來鎖定方法的整個主體相同。  
  
 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>可以用於切割執行緒封鎖作業，例如，等待同步處理的程式碼區域的存取。 **Thread.Interrupt**也用來中斷執行緒作業，像是超出<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>。  
  
> [!IMPORTANT]
>  不要鎖定型別 — 也就是，C# 中的 `typeof(MyType)`、Visual Basic 中的 `GetType(MyType)`或 C++ 中的 `MyType::typeid` — 以便保護 `static` 方法 (Visual Basic 中的 `Shared`方法)。 請改為使用私用靜態物件。 同樣地，在 C# 中不要使用 `this`(在 Visual Basic 中不要使用 `Me`) 以鎖定執行個體方法。 請改為使用私用物件。 類別或執行個體會被您專屬的程式碼以外的程式碼鎖定，可能造成死結或效能問題。  
  
### <a name="compiler-support"></a>編譯器支援  
 Visual Basic 和 C# 支援的語言關鍵字，會使用<xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType>和<xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType>鎖定物件。 Visual Basic 支援 [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) 陳述式；C# 支援 [lock](~/docs/csharp/language-reference/keywords/lock-statement.md) 陳述式。  
  
 在這兩種情況下，如果在程式碼區塊中擲回例外狀況，**lock** 或 **SyncLock** 取得的鎖定會自動釋放。 C# 和 Visual Basic 編譯器會在嘗試開始時發出 **try**/**finally** 區塊與 **Monitor.Enter**，以及在 **finally** 區塊中發出 **Monitor.Exit**。 如果在 **lock** 或 **SyncLock** 區塊內擲回例外狀況，會執行 **finally** 處理常式以允許您進行任何清除工作。  
  
## <a name="synchronized-context"></a>同步處理的內容  
 您可以在任何 **ContextBoundObject** 上使用 **SynchronizationAttribute**，以同步所有執行個體方法和欄位。 相同內容網域中所有物件都共用相同的鎖定。 允許多個執行緒存取方法和欄位，但是一次只允許單一執行緒。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>  
 [執行緒和執行緒處理](../../../docs/standard/threading/threads-and-threading.md)  
 [同步處理原始物件概觀](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 [SyncLock 陳述式](~/docs/visual-basic/language-reference/statements/synclock-statement.md)  
 [lock 陳述式](~/docs/csharp/language-reference/keywords/lock-statement.md)
