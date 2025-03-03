---
title: 使用全局命名空间 (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: 80510e370e0a9c7ab27cb5177d9b547ead82715c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350998"
---
# <a name="working-with-global-namespaces-visual-basic-linq-to-xml"></a>使用全局命名空间 (Visual Basic) (LINQ to XML)
One of the key features of XML literals in Visual Basic is the capability to declare XML namespaces by using the `Imports` statement. 使用此功能时，您可以声明使用前缀的 XML 命名空间，也可以声明默认的 XML 命名空间。  
  
 此功能在两种情况下有用。 首先，使用 XML 文本声明的命名空间不会延续到嵌入的表达式。 声明全局命名空间可减少与命名空间一起使用嵌入表达式所必须执行的工作量。 其次，您必须声明全局命名空间才能与 XML 属性一起使用命名空间。  
  
 您可以在项目级别声明全局命名空间。 您也可以在模块级别声明全局命名空间，这会重写项目级全局命名空间。 最后，您可以使用 XML 文本重写全局命名空间。  
  
 在使用全局声明的命名空间中的 XML 文本或 XML 属性时，您可以在 Visual Studio 中通过将鼠标悬停在 XML 文本或属性上来查看扩展的 XML 文本或属性的名称。 您会在工具提示中看到扩展的名称。  
  
 使用 <xref:System.Xml.Linq.XNamespace> 方法可以获取对应于全局命名空间的 `GetXmlNamespace` 对象。  
  
## <a name="examples-of-global-namespaces"></a>全局命名空间的示例  
 下面的示例通过使用 `Imports` 语句声明一个默认的全局命名空间，然后使用 XML 文本在该命名空间中初始化一个 <xref:System.Xml.Linq.XElement> 对象：  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 该示例产生下面的输出：  
  
```xml  
<Root xmlns="http://www.adventure-works.com" />  
```  
  
 下面的示例声明一个具有前缀的全局命名空间，然后使用 XML 文本初始化一个元素：  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 该示例产生下面的输出：  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" />  
```  
  
## <a name="global-namespaces-and-embedded-expressions"></a>全局命名空间和嵌入式表达式  
 使用 XML 文本声明的命名空间不会延续到嵌入的表达式。 下面的示例声明一个默认命名空间。 然后对 `Child` 元素使用一个嵌入式表达式。  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 该示例产生下面的输出：  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="" />  
</Root>  
```  
  
 您可以看到，生成的 XML 包括一个默认命名空间声明，从而使 `Child` 元素不在任何命名空间中。  
  
 您可以在嵌入式表达式中重新声明该命名空间，如下所示：  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child xmlns="http://www.adventure-works.com"/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 该示例产生下面的输出：  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="http://www.adventure-works.com" />  
</Root>  
```  
  
 但是，这种方法更不便于使用，更好的方法是使用全局默认命名空间。 通过使用全局默认命名空间，您可以使用 XML 文本而无需声明命名空间。 生成的 XML 将处于全局声明的默认命名空间中。  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root>  
                                   <%= <Child/> %>  
                               </Root>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 该示例产生下面的输出：  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child />  
</Root>  
```  
  
## <a name="using-namespaces-with-xml-properties"></a>与 XML 属性一起使用命名空间  
 如果你使用位于某一命名空间中的 XML 树并使用 XML 属性，则必须使用全局命名空间，以使 XML 属性也位于正确的命名空间中。 下面的示例在一个命名空间中一个声明 XML 树。 然后打印 `Child` 元素的计数。  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <Child>content</Child>  
    </Root>  
Console.WriteLine(root.<Child>.Count())  
```  
  
 本示例指示没有 `Child` 元素。 它将生成以下输出：  
  
```console  
0  
```  
  
 但如果您声明一个默认的全局命名空间，则 XML 文本和 XML 属性都将位于该默认的全局命名空间中：  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child>content</Child>  
            </Root>  
        Console.WriteLine(root.<Child>.Count())  
    End Sub  
End Module  
```  
  
 本示例指示有一个 `Child` 元素。 它将生成以下输出：  
  
```console  
1  
```  
  
 如果您声明一个具有前缀的全局命名空间，则可以对 XML 文本和 XML 属性使用该前缀：  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child>content</aw:Child>  
            </aw:Root>  
        Console.WriteLine(root.<aw:Child>.Count())  
    End Sub  
End Module  
```  
  
## <a name="xnamespace-and-global-namespaces"></a>XNamespace 和全局命名空间  
 通过使用 <xref:System.Xml.Linq.XNamespace> 方法，可以获取一个 `GetXmlNamespace` 对象：  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Dim xn As XNamespace = GetXmlNamespace(aw)  
        Console.WriteLine(xn)  
    End Sub  
End Module  
```  
  
 该示例产生下面的输出：  
  
```console  
http://www.adventure-works.com  
```  
  
## <a name="see-also"></a>请参阅

- [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)
