---
title: "&lt;assemblyBinding&gt;元素&lt;組態&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 8d670c56a885a5fdae059a87f63fba9ab32f020c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="assemblybinding-element-for-configuration"></a>\<assemblyBinding > 項目\<設定 >

指定位於組態層級的組件繫結原則。

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;**\<assemblyBinding >**

## <a name="syntax"></a>語法

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a>屬性

|           | 描述 |
| --------- | ----------- |
| **xmlns** | 必要屬性。<br><br>指定組件繫結所需的 XML 命名空間。 使用字串 "urn:schemas-microsoft-com:asm.v1" 做為值。 |

## <a name="parent-element"></a>父項目

|     | 描述 |
| --- | ----------- |
| [**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) | 通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。 |

## <a name="child-element"></a>子元素

|     | 描述 |
| --- | ----------- |
| [**\<linkedConfiguration >**](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) | 指定要包含的組態檔。 |

## <a name="remarks"></a>備註

[  **\<LinkedConfiguration >** ](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md)項目可簡化管理的元件組件，藉由使用應用程式組態檔，以包含組件中的組態檔已知的位置，而不是複製的組件組態設定。

> [!NOTE]
>  **\<LinkedConfiguration >**項目不支援有 Windows-並存資訊清單的應用程式。

## <a name="example"></a>範例

下列範例會示範如何包含在本機硬碟上的組態檔：

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>另請參閱

[適用於.NET Framework 組態檔結構描述](~/docs/framework/configure-apps/file-schema/index.md)
