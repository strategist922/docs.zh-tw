---
title: "泛型介面中的差異 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cc3fe009e89d5d8f6619b406c8c08f47620a881d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="variance-in-generic-interfaces-c"></a>泛型介面中的差異 (C#)
.NET Framework 4 針對數個現有泛型介面推出了差異支援。 差異支援可讓實作這些介面的類別以隱含方式轉換。 下列介面現在都是 Variant︰  
  
-   <xref:System.Collections.Generic.IEnumerable%601> (T 是 Covariant)  
  
-   <xref:System.Collections.Generic.IEnumerator%601> (T 是 Covariant)  
  
-   <xref:System.Linq.IQueryable%601> (T 是 Covariant)  
  
-   <xref:System.Linq.IGrouping%602> (`TKey` 和 `TElement` 都是 Covariant)  
  
-   <xref:System.Collections.Generic.IComparer%601> (T 是 Contravariant)  
  
-   <xref:System.Collections.Generic.IEqualityComparer%601> (T 是 Contravariant)  
  
-   <xref:System.IComparable%601> (T 是 Contravariant)  
  
 共變數允許方法具有比介面泛型型別參數所定義之衍生程度更大的傳回型別。 若要示範共變數功能，請考慮這些泛型介面︰`IEnumerable<Object>` 和 `IEnumerable<String>`。 `IEnumerable<String>` 介面不會繼承 `IEnumerable<Object>` 介面。 不過，`String` 型別確實會繼承`Object` 型別，而且在某些情況下，您可能希望將這些介面的物件指派給彼此。 這會顯示在以下程式碼範例中。  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 在舊版的 .NET Framework 中，此程式碼會造成 C# 使用 `Option Strict On` 的編譯錯誤。 但現在您可以使用 `strings`，而不使用 `objects`，如上例所示，因為 <xref:System.Collections.Generic.IEnumerable%601> 介面是 Covariant。  
  
 反變數允許方法具有比介面泛型參數所指定之衍生程度更小的引數型別。 為示範反變數，我們假設您已建立 `BaseComparer` 類別來比較 `BaseClass` 類別的執行個體。 `BaseComparer` 類別會實作 `IEqualityComparer<BaseClass>` 介面。 因為 <xref:System.Collections.Generic.IEqualityComparer%601> 介面現在是 Contravariant，所以您可以使用 `BaseComparer` 比較繼承了 `BaseClass` 類別的類別執行個體。 這會顯示在以下程式碼範例中。  
  
```csharp  
// Simple hierarchy of classes.  
class BaseClass { }  
class DerivedClass : BaseClass { }  
  
// Comparer class.  
class BaseComparer : IEqualityComparer<BaseClass>   
{  
    public int GetHashCode(BaseClass baseInstance)  
    {  
        return baseInstance.GetHashCode();  
    }  
    public bool Equals(BaseClass x, BaseClass y)  
    {  
        return x == y;  
    }  
}  
class Program  
{  
    static void Test()  
    {  
        IEqualityComparer<BaseClass> baseComparer = new BaseComparer();  
  
        // Implicit conversion of IEqualityComparer<BaseClass> to   
        // IEqualityComparer<DerivedClass>.  
        IEqualityComparer<DerivedClass> childComparer = baseComparer;  
    }  
}  
```  
  
 如需更多範例，請參閱[針對泛型集合使用介面中的差異 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)。  
  
 僅參考型別支援泛型介面的差異。 實值型別不支援差異。 例如，`IEnumerable<int>` 無法以隱含方式轉換成 `IEnumerable<object>`，因為整數是以實值型別表示。  
  
```csharp  
IEnumerable<int> integers = new List<int>();  
// The following statement generates a compiler errror,  
// because int is a value type.  
// IEnumerable<Object> objects = integers;  
```  
  
 請務必牢記，實作 Variant 介面的類別仍然是非變異的。 例如，雖然 <xref:System.Collections.Generic.List%601> 實作了 Covariant 介面 <xref:System.Collections.Generic.IEnumerable%601>，但您不能以隱含方式將 `List<Object>` 轉換成 `List<String>`。 下列程式碼範例說明此情形。  
  
```csharp  
// The following line generates a compiler error  
// because classes are invariant.  
// List<Object> list = new List<String>();  
  
// You can use the interface object instead.  
IEnumerable<Object> listObjects = new List<String>();  
```  
  
## <a name="see-also"></a>另請參閱  
 [針對泛型集合使用介面中的差異 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)  
 [建立 Variant 泛型介面 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)  
 [泛型介面](../../../../standard/generics/interfaces.md)  
 [委派中的差異 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
