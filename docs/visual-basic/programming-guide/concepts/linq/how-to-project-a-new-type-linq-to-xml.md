---
title: 如何：投影新类型 (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 8cfb24f5-89b2-4cfb-b85d-e7963f8f1845
ms.openlocfilehash: a2486d88af537fb4aa8f34243a5a739d25ee5be1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353337"
---
# <a name="how-to-project-a-new-type-linq-to-xml-visual-basic"></a>How to: Project a New Type (LINQ to XML) (Visual Basic)
本节中的其他示例已演示了一些查询，这些查询以 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement>、<xref:System.Collections.Generic.IEnumerable%601> 的 `string` 和 <xref:System.Collections.Generic.IEnumerable%601> 的 `int` 的形式返回结果。 这些是常见结果类型，但它们不是对所有情况都适用。 在很多情况下，会希望查询返回其他类型的 <xref:System.Collections.Generic.IEnumerable%601>。  
  
## <a name="example"></a>示例  
 此示例演示如何在 `Select` 子句中实例化对象。 代码首先定义一个具有一个构造函数的新类，然后修改 `Select` 语句，使该表达式成为新类的新实例。  
  
 本示例使用以下 XML 文档：[示例 XML 文件：典型采购订单 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md)。  
  
```vb  
Public Class NameQty  
    Public name As String  
    Public qty As Integer  
    Public Sub New(ByVal n As String, ByVal q As Integer)  
        name = n  
        qty = q  
    End Sub  
End Class  
  
Public Class Program  
    Shared Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
  
        Dim nqList As IEnumerable(Of NameQty) = _  
            From n In po...<Item> _  
            Select New NameQty( _  
                n.<ProductName>.Value, CInt(n.<Quantity>.Value))  
  
        For Each n As NameQty In nqList  
            Console.WriteLine(n.name & ":" & n.qty)  
        Next  
    End Sub  
End Class  
```  
  
 This example uses the `M:System.Xml.Linq.XElement.Element` method that was introduced in the topic [How to: Retrieve a Single Child Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md). 还使用强制转换来检索 `M:System.Xml.Linq.XElement.Element` 方法返回的元素值。  
  
 该示例产生下面的输出：  
  
```console  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a>请参阅

- [Projections and Transformations (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
