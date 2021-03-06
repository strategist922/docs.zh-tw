---
title: "如何：使用 Catch 區塊中的特定例外狀況"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- try/catch blocks
- catch blocks
ms.assetid: 12af9ff3-8587-4f31-90cf-6c2244e0fdae
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 94e5840ca4bb5f871a0ae91f53404de6a60d749d
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2017
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a>如何在 catch 區塊中使用特定的例外狀況

一般情況下，它是良好的程式設計作法攔截特定類型的例外狀況，而不是使用基本`catch`陳述式。

發生例外狀況時，該例外狀況會在堆疊中向上傳遞，讓每個 catch 區塊都有機會處理。 Catch 陳述式的順序很重要。 請將針對特定例外狀況的 catch 區塊放在一般例外狀況的 catch 區塊之前，否則編譯器可能會發出錯誤。 藉由比對 catch 區塊中指定的例外狀況類型與例外狀況名稱，即可決定正確的 catch 區塊。 如果沒有特定 catch 區塊，則會由一般 catch 區塊 (如果有的話) 攔截例外狀況。

下列程式碼範例使用 `try`/`catch` 區塊來攔截 <xref:System.InvalidCastException>。 此範例會建立具有員工層級 (`Emlevel`) 之單一屬性的類別，稱為 `Employee`。 `PromoteEmployee` 方法會採用一個物件並遞增員工層級。 <xref:System.InvalidCastException> 會在 <xref:System.DateTime> 執行個體傳遞給 `PromoteEmployee` 方法時發生。

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)] 

## <a name="see-also"></a>另請參閱  
[例外狀況](index.md)
