---
title: "&lt;篩選&gt;元素&lt;新增&gt;如&lt;接聽程式&gt;如&lt;來源&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: ff5acf8edcda68979c04f5e62237464ee6f040a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltlistenersgt-for-ltsourcegt"></a>&lt;篩選&gt;元素&lt;新增&gt;如&lt;接聽程式&gt;如&lt;來源&gt;
將篩選新增至追蹤來源之 `Listeners` 集合中的接聽項。  
  
 \<configuration>  
\<system.diagnostics >  
\<來源 >  
\<來源 >  
\<接聽項 >  
\<add>  
\<篩選條件 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`type`|必要屬性。<br /><br /> 指定類型的篩選器，應該繼承自<xref:System.Diagnostics.TraceFilter>類別。 您可以使用的類型，對應於該類型的命名空間限定名稱<xref:System.Type.FullName%2A>屬性，或者您可以使用的完整限定的類型名稱，包括組件資訊，其對應至<xref:System.Type.AssemblyQualifiedName%2A>屬性。 如需完整限定的類型名稱的資訊，請參閱[指定限定的型別名稱](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)。|  
|`initializeData`|選擇性屬性。<br /><br /> 指定的篩選條件類別傳遞至建構函式的字串。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
|`sources`|包含起始追蹤訊息的追蹤來源。|  
|`source`|指定起始追蹤訊息的追蹤來源。|  
|`listeners`|包含收集、 儲存和路由傳送訊息的接聽程式。 接聽程式將追蹤輸出導向至適當的目標。|  
|`add`|將接聽項新增至追蹤來源的 `Listeners` 集合。|  
  
## <a name="remarks"></a>備註  
 `<filter>`元素必須包含在`<add>`中的項目指定的接聽程式類型的追蹤來源接聽程式，不只接聽程式的名稱定義[ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)。 如果接聽程式已定義在[ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)，必須定義該接聽項的篩選條件，該元素中。  
  
 此項目可以用於電腦組態檔 (Machine.config) 和應用程式組態檔。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用`<filter>`將篩選加入至接聽程式的項目`console`中`Listeners`追蹤來源的集合`myTraceSource`，指定做為篩選事件層級`Error`。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" switchName="SourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="SourceSwitch" value="Warning" />  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.TraceFilter>  
 [追蹤和偵錯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
