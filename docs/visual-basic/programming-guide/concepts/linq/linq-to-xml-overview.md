---
title: LINQ to XML 概述
ms.date: 07/20/2015
ms.assetid: 502661e0-bc5d-438d-94c2-7efb63bb6fbd
ms.openlocfilehash: ef3fca844dc98440eb4816110a5a78482cfa4f4e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346795"
---
# <a name="linq-to-xml-overview-visual-basic"></a>LINQ to XML Overview (Visual Basic)
在很多环境中，XML 已广泛采用为格式化数据的方式。 例如，在 Web 上，在配置文件、Microsoft Office Word 文件以及数据库中，都可以看到 XML。  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 经过了重新设计，是最新的 XML 编程方法。 它提供文档对象模型 (DOM) 的内存文档修改功能，支持 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查询表达式。 尽管这些查询表达式在语法上与 XPath 不同，但它们提供类似的功能。  
  
## <a name="linq-to-xml-developers"></a>LINQ to XML 开发人员  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 是面向各种开发人员的。 对于只想完成某项工作的普通开发人员，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 通过提供与 SQL 相似的查询表达式，使 XML 变得更加简单。 只要稍加学习，程序员就能学会以自己选择的编程语言编写简洁、功能强大的查询。  
  
 专业开发人员可以使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 来大幅提高他们的工作效率。 通过使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]，他们可以编写出表达能力更强、更为紧凑、功能更强的代码。 他们可以同时对多个数据域使用查询表达式。  
  
## <a name="what-is-linq-to-xml"></a>什么是 LINQ to XML？  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 是一种启用了 LINQ 的内存 XML 编程接口，支持在 .NET Framework 编程语言中处理 XML。  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 将 XML 文档置于内存中，这一点很像文档对象模型 (DOM)。 您可以查询和修改 XML 文档，修改之后，可以将其另存为文件，也可以将其序列化然后通过 Internet 发送。 However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in Visual Basic.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 最重要的优势是它与 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] 的集成。 由于实现了这一集成，因此，可以对内存 XML 文档编写查询，以检索元素和属性的集合。 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 的查询功能在功能上（尽管不是在语法上）与 XPath 和 XQuery 具有可比性。 The integration of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] in Visual Basic provides stronger typing, compile-time checking, and improved debugger support.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 的另一个优势是通过将查询结果用作 <xref:System.Xml.Linq.XElement> 和 <xref:System.Xml.Linq.XAttribute> 对象构造函数的参数，实现了一种功能强大的创建 XML 树的方法。 此方法称为*功能构造*，可使开发人员轻松地将 XML 树从一个形状转换成另一个形状。  
  
 例如，你可能有一个[示例 XML 文件：典型采购订单 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md) 中所述的典型 XML 采购订单。 通过使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]，可以运行以下查询，以获取采购单每个项元素的部件号属性值：  
  
```vb  
Dim partNos = _  
    From item In purchaseOrder...<Item> _  
    Select item.@PartNumber  
```  
  
 另一个示例，您可能需要一个列表，列出值大于 100 美元的项，并根据部件号排序。 若要获取此信息，可以运行下面的查询：  
  
```vb  
Dim partNos = _  
From item In purchaseOrder...<Item> _  
Where (item.<Quantity>.Value * _  
       item.<USPrice>.Value) > 100 _  
Order By item.<PartNumber>.Value _  
Select item  
```  
  
 除了这些 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 功能以外，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 提供了改进的 XML 编程接口。 使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]，您可以：  
  
- 从文件或流加载 XML。  
  
- 将 XML 序列化为文件或流。  
  
- 使用函数构造从头开始创建 XML。  
  
- 使用类似 XPath 的轴查询 XML。  
  
- 使用 <xref:System.Xml.Linq.XContainer.Add%2A>、<xref:System.Xml.Linq.XNode.Remove%2A>、<xref:System.Xml.Linq.XNode.ReplaceWith%2A> 和 <xref:System.Xml.Linq.XElement.SetValue%2A> 等方法对内存 XML 树进行操作。  
  
- 使用 XSD 验证 XML 树。  
  
- 使用这些功能的组合，可将 XML 树从一种形状转换为另一种形状。  
  
## <a name="creating-xml-trees"></a>创建 XML 树  
 使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 编程的一个明显优势是易于创建 XML 树。 For example, to create a small XML tree, you can write  code as follows:  
  
```vb  
Dim contacts = _  
<Contacts>  
    <Contact>  
        <Name>Patrick Hines</Name>  
        <Phone Type="Home">206-555-0144</Phone>  
        <Phone Type="Work">425-555-0145</Phone>  
        <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
        </Address>  
    </Contact>  
</Contacts>  
```  
  
 The Visual Basic compiler translates XML literals into [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] method calls.  
  
 For more information, see [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).  
  
## <a name="see-also"></a>请参阅

- <xref:System.Xml.Linq>
- [入门 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
- [Visual Basic 中的 LINQ to XML 概述](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
