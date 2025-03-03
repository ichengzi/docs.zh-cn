---
title: 修改 XML 树 (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 4ae511a5-4fc9-4178-9c8e-761357deae3f
ms.openlocfilehash: c946052beb612c087d26e312875b7f7950ceadf5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353176"
---
# <a name="modifying-xml-trees-linq-to-xml-visual-basic"></a>Modifying XML Trees (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 是一个 XML 树在内存中的存储区。 在从源中加载或分析 XML 树之后，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 允许就地修改该树，然后序列化该树，可以将它保存到文件中或发送到远程服务器。  
  
 就地修改树时，可使用某些方法，例如 <xref:System.Xml.Linq.XContainer.Add%2A>。  
  
 但是有另外一种方法，就是使用函数构造来生成具有不同形状的新树。 根据需要对 XML 树所做的更改类型的不同，以及根据树大小的不同，该方法可能更加强大，更易于开发。 本节第一个主题将比较这两种方法。  
  
## <a name="in-this-section"></a>本节内容  
  
|主题|描述|  
|-----------|-----------------|  
|[In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md)|在内存中修改 XML 树与使用函数构造的比较。|  
|[Adding Elements, Attributes, and Nodes to an XML Tree (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/adding-elements-attributes-and-nodes-to-an-xml-tree.md)|提供有关向 XML 树中添加元素、属性或节点的信息。|  
|[修改 XML 树中的元素、特性和节点](../../../../visual-basic/programming-guide/concepts/linq/modifying-elements-attributes-and-nodes-in-an-xml-tree.md)|提供有关修改现有元素、属性或节点的信息。|  
|[Removing Elements, Attributes, and Nodes from an XML Tree (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/removing-elements-attributes-and-nodes-from-an-xml-tree.md)|提供有关从 XML 树中移除元素、属性或节点的信息。|  
|[Maintaining Name/Value Pairs (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/maintaining-name-value-pairs.md)|描述如何维护最好保存为名称/值对的应用程序信息，例如配置信息或全局设置。|  
|[How to: Change the Namespace for an Entire XML Tree (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-change-the-namespace-for-an-entire-xml-tree.md)|演示如何将 XML 树从一个命名空间移动到另一个命名空间。|  
  
## <a name="see-also"></a>请参阅

- [Programming Guide (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
