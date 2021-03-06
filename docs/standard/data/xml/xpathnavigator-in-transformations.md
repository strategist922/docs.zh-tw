---
title: "轉換中的 XPathNavigator"
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
ms.assetid: 118f97d1-7110-4d1b-b0bd-4143252c0bb0
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 09f89708607ada18181bc6605994c7908e1dd14b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="xpathnavigator-in-transformations"></a>轉換中的 XPathNavigator
<xref:System.Xml.XPath.XPathNavigator> 類別可提供資料的唯讀隨機存取，並可當作可延伸樣式表語言轉換 (XSLT) 的輸入。 它可實作於 <xref:System.Xml.XPath.XPathDocument>、<xref:System.Xml.XmlDataDocument> 及 <xref:System.Xml.XmlDocument>。 <xref:System.Xml.XPath.XPathNavigator> 以 XML 路徑語言 (XPath) 之建議事項第 5 節中所說明的全球資訊網協會 (W3C) 資料模型為基礎。  
  
 <xref:System.Xml.XPath.XPathNavigator> 可定義任何存放區上的資料指標模型，並可針對任何資料存放區提供快速、唯讀的 XPath 查詢。 <xref:System.Xml.XPath.XPathNavigator> 也是可用來重複 Result Tree Fragment 的類別。  
  
 此 API 讓您能夠從存放區目前的節點中取得資訊，並移至連接的節點上。 <xref:System.Xml.XPath.XPathNavigator>是一種資料指標樣式模型，透過使用一組存放區執行周遊**移動**方法。 <xref:System.Xml.XPath.XPathNavigator> 一律定位於節點上。 任何**移動**方法失敗<xref:System.Xml.XPath.XPathNavigator>不變。  
  
 <xref:System.Xml.XPath.XPathNavigator> 是可用來重複 Result Tree Fragment 的類別。 下列程式碼範例將藉由呼叫附有 `fragment` 參數的函式，在樣式表中建立 Result Tree Fragment。  
  
## <a name="testxsl"></a>test.xsl  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl ="urn:schemas-microsoft-com:xslt"  
                xmlns:user="http://www.adventure-works.com"  
                version="1.0">  
  
<xsl:variable name="fragment">  
    <authorlist>  
       <author>Joe</author>  
    </authorlist>  
</xsl:variable>  
  
<msxsl:script language="C#" implements-prefix="user">  
<![CDATA[  
   string NodeFragment(XPathNavigator nav)  
   {  
      if (nav.HasChildren)  
        return nav.Value;  
      else  
        return "";  
   }  
]]>  
</msxsl:script>  
  
<xsl:template match="/">  
     <xsl:value-of select="user:NodeFragment($fragment)"/>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="testxml"></a>test.xml  
  
```xml  
<root>Some text</root>  
```  
  
 下列程式碼會使用**test.xsl**樣式表和**test.xml**輸入資料。  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.Xsl  
Imports System.Xml.XPath  
Imports System.Text  
Public Class sample  
  
    Public Shared Sub Main()  
        Dim xslt As New XslTransform()  
        xslt.Load("test.xsl")  
  
        Dim xd As New XPathDocument("test.xml")  
  
        Dim strmTemp = New FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite)  
        xslt.Transform(xd, Nothing, strmTemp, Nothing)  
    End Sub 'Main  
End Class 'sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.Xsl;  
using System.Xml.XPath;  
using System.Text;  
  
public class sample  
{  
    public static void Main()  
    {  
        XslTransform xslt = new XslTransform();  
        xslt.Load("test.xsl");  
  
        XPathDocument xd = new XPathDocument("test.xml");  
  
        Stream strmTemp = new FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite);  
        xslt.Transform(xd, null, strmTemp, null);  
    }  
}  
```  
  
## <a name="output"></a>輸出  
 轉換的結果檔案中找到**out.xml**:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>Joe  
```  
  
## <a name="see-also"></a>另請參閱  
 [XslTransform 類別實作 XSLT 處理器](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
