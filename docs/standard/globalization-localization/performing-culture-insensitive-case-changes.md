---
title: "執行不區分文化特性的大小寫變更"
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
helpviewer_keywords:
- String.ToLower method
- culture, case sensitivity
- Char.ToLower method
- case, changing in culture-insensitive strings
- Char.ToUpper method
- culture-insensitive string operations, case changes
- String.ToUpper method
- culture parameter
ms.assetid: 822d551c-c69a-4191-82f4-183d82c9179c
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c500b882c335572b8b458ba515b282e9f5362b85
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="performing-culture-insensitive-case-changes"></a>執行不區分文化特性的大小寫變更
<xref:System.String.ToUpper%2A?displayProperty=nameWithType>， <xref:System.String.ToLower%2A?displayProperty=nameWithType>， <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>，和<xref:System.Char.ToLower%2A?displayProperty=nameWithType>方法提供不接受任何參數的多載。 根據預設，不含參數的這些多載會執行大小寫變更的值為基礎<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>。 這會產生區分大小寫可能會因文化特性的結果。 若要清除您是否想要區分文化特性或不區分文化特性的大小寫變更，您應該使用這些方法需要您明確指定的多載`culture`參數。 對於區分文化特性大小寫變更，指定`CultureInfo.CurrentCulture`如`culture`參數。 不區分文化特性的大小寫變更為指定`CultureInfo.InvariantCulture`如`culture`參數。  
  
 通常，字串會轉換至標準案例，以更新版本可讓您更輕鬆查閱。 當以這種方式使用字串時，您應該指定`CultureInfo.InvariantCulture`如`culture`參數，因為值<xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType>有可能變更大小寫變更的時間之間的查閱，就會發生的時間。  
  
 如果安全性決策根據大小寫變更作業，應該不區分文化特性以確保結果的值不會影響作業`CultureInfo.CurrentCulture`。 請參閱 「 字串比較，使用目前文化特性 」 一節[使用字串的最佳作法](../../../docs/standard/base-types/best-practices-strings.md)文件的範例示範如何區分文化特性字串作業可能會產生不一致的結果。  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a>使用 String.ToUpper 和 String.ToLower 方法  
 程式碼更清楚，所以，建議您一定要使用的多載`String.ToUpper`和`String.ToLower`方法可讓您指定`culture`參數明確。 例如，下列程式碼會執行識別項查詢。 `key.ToLower`作業是區分文化特性的預設值，但這種行為並不清楚，無法讀取程式碼。  
  
### <a name="example"></a>範例  
  
```vb  
Shared Function LookupKey(key As String) As Object  
   Return internalHashtable(key.ToLower())  
End Function  
```  
  
```csharp  
static object LookupKey(string key)   
{  
    return internalHashtable[key.ToLower()];  
}  
```  
  
 如果您想`key.ToLower`作業是不區分文化特性，您應該變更上述範例，如下所示，以明確地使用`CultureInfo.InvariantCulture`時變更大小寫。  
  
```vb  
Shared Function LookupKey(key As String) As Object  
    Return internalHashtable(key.ToLower(CultureInfo.InvariantCulture))  
End Function  
```  
  
```csharp  
static object LookupKey(string key)   
{  
    return internalHashtable[key.ToLower(CultureInfo.InvariantCulture)];  
}  
```  
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a>使用 Char.ToUpper 和 Char.ToLower 方法  
 雖然`Char.ToUpper`和`Char.ToLower`方法有相同的特性`String.ToUpper`和`String.ToLower`方法，只會受到影響的文化特性為土耳其文 （土耳其） 和亞塞拜然 （拉丁文，亞塞拜然）。 這些是只有兩個文化特性而有所不同，但單一字元大小寫的差異。 如需這個特殊案例對應的詳細資訊，請參閱 <xref:System.String> 類別主題中的＜大小寫＞一節。 程式碼更清楚，所以，並確保一致的結果，建議您一律使用這些方法可讓您明確指定的多載`culture`參數。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.String.ToUpper%2A?displayProperty=nameWithType>  
 <xref:System.String.ToLower%2A?displayProperty=nameWithType>  
 <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>  
 <xref:System.Char.ToLower%2A?displayProperty=nameWithType>  
 [執行不區分文化特性的字串作業](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
