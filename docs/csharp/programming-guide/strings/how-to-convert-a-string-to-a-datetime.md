---
title: "如何：將字串轉換為 DateTime (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: strings [C#], converting to DateTIme
ms.assetid: 88abef11-3a06-4b49-8dd2-61ed0e876fc3
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b459f245f0090fff16918bceb12a0082f6944331
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-convert-a-string-to-a-datetime-c-programming-guide"></a>如何：將字串轉換為 DateTime (C# 程式設計手冊)
程式常讓使用者將日期輸入為字串值。 若要將字串型的日期轉換成 <xref:System.DateTime?displayProperty=nameWithType> 物件，您可以使用 <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=nameWithType> 方法或 <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> 靜態方法，如下例所示。  
  
 **文化特性**。  世界各地的不同文化，有不同的日期字串撰寫方式。  例如，01/20/2008 在美國是 January 20th, 2008。  在法國，這會擲回 InvalidFormatException。 這是因為法國讀取的日期時間為日/月/年，而在美國是月/日/年。  
  
 因此，像 20/01/2008 這樣的字串在法國會剖析成 1 月 20 日 2008 年 ，但在美國會擲回 InvalidFormatException。  
  
 若要判斷目前的文化特性設定，您可以使用 System.Globalization.CultureInfo.CurrentCulture。  
  
 如需將字串轉換成 dateTime 的簡單範例，請參閱下例。  
  
 如需更多的日期字串範例，請參閱 <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=nameWithType>。  
  
```csharp  
string dateTime = "01/08/2008 14:50:50.42";  
            DateTime dt = Convert.ToDateTime(dateTime);  
            Console.WriteLine("Year: {0}, Month: {1}, Day: {2}, Hour: {3}, Minute: {4}, Second: {5}, Millisecond: {6}",  
                              dt.Year, dt.Month, dt.Day, dt.Hour, dt.Minute, dt.Second, dt.Millisecond);  
            // Specify exactly how to interpret the string.  
            IFormatProvider culture = new System.Globalization.CultureInfo("fr-FR", true);  
  
            // Alternate choice: If the string has been input by an end user, you might    
            // want to format it according to the current culture:   
            // IFormatProvider culture = System.Threading.Thread.CurrentThread.CurrentCulture;  
            DateTime dt2 = DateTime.Parse(dateTime, culture, System.Globalization.DateTimeStyles.AssumeLocal);  
            Console.WriteLine("Year: {0}, Month: {1}, Day: {2}, Hour: {3}, Minute: {4}, Second: {5}, Millisecond: {6}",  
                              dt2.Year, dt2.Month, dt2.Day, dt2.Hour, dt2.Minute, dt2.Second, dt2.Millisecond  
/* Output (assuming first culture is en-US and second is fr-FR):  
    Year: 2008, Month: 1, Day: 8, Hour: 14, Minute: 50, Second: 50, Millisecond: 420  
Year: 2008, Month: 8, Day: 1, Hour: 14, Minute: 50, Second: 50, Millisecond: 420  
Press any key to continue . . .  
 */  
```  
  
## <a name="example"></a>範例  
 [!code-csharp[csProgGuideStrings#13](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-a-string-to-a-datetime_1.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [字串](../../../csharp/programming-guide/strings/index.md)
