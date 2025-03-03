---
title: 'How to: Control Namespace Prefixes (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 2fcf28a5-31b6-409d-84ea-27c22f71fc9f
ms.openlocfilehash: 5ba415452a8671466c3a4c71a88731e5bd3cda60
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348378"
---
# <a name="how-to-control-namespace-prefixes-visual-basic-linq-to-xml"></a>如何：控制命名空间前缀 (Visual Basic) (LINQ to XML)
本主题说明如何控制命名空间前缀。  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 本示例声明两个命名空间。 It specifies that the `http://www.adventure-works.com` namespace has the prefix `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.  
  
### <a name="code"></a>代码  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <fc:Child>  
                    <aw:DifferentChild>other content</aw:DifferentChild>  
                </fc:Child>  
                <aw:Child2>c2 content</aw:Child2>  
                <fc:Child3>c3 content</fc:Child3>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
### <a name="comments"></a>注释  
 该示例产生下面的输出：  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a>请参阅

- [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)
