---
title: "x:ClassModifier 指示詞"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xClassModifier
- x:ClassModifier
- ClassModifier
helpviewer_keywords:
- XAML [XAML Services], x:ClassModifier attribute
- x:ClassModifier attribute [XAML Services]
- ClassModifier attribute in XAML [XAML Services]
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
caps.latest.revision: "22"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1a4918e23a915ee07eace388ea2cea512c2e479d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="xclassmodifier-directive"></a>x:ClassModifier 指示詞
修改 XAML 編譯行為時`x:Class`也會提供。 具體來說，而不是建立在部分`class`具有`Public`存取層級 （預設值），提供`x:Class`會透過`NotPublic`存取層級。 這個行為會影響產生的組件中的類別的存取層級。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|*NotPublic*|要傳遞至指定的完整字串<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>與<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>會有所差異，視您使用的程式碼後置程式語言而定。 請參閱＜備註＞。|  
  
## <a name="dependencies"></a>相依性  
 [X:class](../../../docs/framework/xaml-services/x-class-directive.md)也必須提供在相同的項目，該項目必須是在網頁中的根項目。 如需詳細資訊，請參閱[ \[MS-XAML\]區段 4.3.1.8](http://go.microsoft.com/fwlink/?LinkId=114525)。  
  
## <a name="remarks"></a>備註  
 值`x:ClassModifier`在.NET Framework XAML 服務使用方式會因程式語言。 要使用的字串取決於各種語言的實作方式其<xref:System.CodeDom.Compiler.CodeDomProvider>和類型轉換器，它會傳回定義意義<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>和<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>，以及該語言是否區分大小寫。  
  
-   如[!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)]，要傳遞至指定的字串<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>是`internal`。  
  
-   如[!INCLUDE[TLA2#tla_visualbnet](../../../includes/tla2sharptla-visualbnet-md.md)]，要傳遞至指定的字串<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>是`Friend`。  
  
-   如[!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)]，任何目標存在編譯 XAML 支援，因此，要傳遞的值未指定。  
  
 您也可以指定<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>(`public`中[!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)]，`Public`中[!INCLUDE[TLA2#tla_visualb](../../../includes/tla2sharptla-visualb-md.md)]); 不過，指定<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>不常是因為<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>已經是預設行為。  
  
 其他值，與對等的使用者程式碼存取層級的限制，例如`private`中[!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)]，不相關的`x:ClassModifier`因為在 XAML 中，不支援巢狀的類別的參考，因此，<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>修飾詞具有相同的效果。  
  
## <a name="security-notes"></a>安全性注意事項  
 中所宣告的存取層級`x:ClassModifier`仍受限於特定架構和其功能所解譯。 WPF 包含的功能，以載入和執行個體化類型其中`x:ClassModifier`是`internal`，如果該類別從 WPF 資源透過 URI 參考的組件參考。 由於此情況下，可能會類似其他架構所實作的其他人，不能以獨佔方式在`x:ClassModifier`封鎖所有可能的具現化嘗試。  
  
## <a name="see-also"></a>請參閱  
 [x:Class 指示詞](../../../docs/framework/xaml-services/x-class-directive.md)  
 [WPF 中的程式碼後置和 XAML](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [x:FieldModifier 指示詞](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md)  
 [安全性 (WPF)](../../../docs/framework/wpf/security-wpf.md)  
 [從 WPF 移轉至 System.Xaml 的類型](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
