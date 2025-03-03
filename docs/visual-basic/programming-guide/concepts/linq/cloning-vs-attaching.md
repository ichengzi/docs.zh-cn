---
title: 克隆与附加
ms.date: 07/20/2015
ms.assetid: 3c3bd105-c9d3-49bd-875b-27ab4e8bc7a3
ms.openlocfilehash: 22e86ee78d5c3fa0a7b80ae559c39f424fc9d61a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345692"
---
# <a name="cloning-vs-attaching-visual-basic"></a>Cloning vs. Attaching (Visual Basic)
在将 <xref:System.Xml.Linq.XNode>（包括 <xref:System.Xml.Linq.XElement>）或 <xref:System.Xml.Linq.XAttribute> 对象添加到新树中时，如果新内容没有父级，则直接将这些对象附加到 XML 树中。 如果新内容已经有父级，并且是另一 XML 树的一部分，则克隆新内容。 然后将新克隆的内容附加到 XML 树中。  
  
## <a name="example"></a>示例  
 下面的代码演示将有父级的元素添加到树中，以及将没有父级的元素添加到树中时的行为。  
  
```vb  
' Create a tree with a child element.  
Dim xmlTree1 As XElement = _  
    <Root>  
        <Child1>1</Child1>  
    </Root>  
  
' Create an element that is not parented.  
Dim child2 As XElement = <Child2>2</Child2>  
  
' Create a tree and add Child1 and Child2 to it.  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child1>(0) %>  
        <%= child2 %>  
    </Root>  
  
' Compare Child1 identity.  
Console.WriteLine("Child1 was {0}", _  
    IIf(xmlTree1.Element("Child1") Is xmlTree2.Element("Child1"), _  
    "attached", "cloned"))  
  
' Compare Child2 identity.  
Console.WriteLine("Child2 was {0}", _  
    IIf(child2 Is xmlTree2.Element("Child2"), _  
    "attached", "cloned"))  
```  
  
 该示例产生下面的输出：  
  
```console  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a>请参阅

- [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
