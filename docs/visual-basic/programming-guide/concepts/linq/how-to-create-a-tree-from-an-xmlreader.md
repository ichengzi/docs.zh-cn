---
title: 如何：从 XmlReader 创建树
ms.date: 07/20/2015
ms.assetid: 6de683d8-177d-402b-b0de-d0539f1ce5d8
ms.openlocfilehash: 7d8d7f5b6389bef520e11fd2b7cc3e1c7e862e73
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353090"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-visual-basic"></a>How to: Create a Tree from an XmlReader (Visual Basic)

本主题演示如何直接从 <xref:System.Xml.XmlReader> 创建 XML 树。 若要从 <xref:System.Xml.Linq.XElement> 创建 <xref:System.Xml.XmlReader>，必须将 <xref:System.Xml.XmlReader> 定位在元素节点上。 <xref:System.Xml.XmlReader> 将跳过注释和处理指令，但如果 <xref:System.Xml.XmlReader> 定位在文本节点上，则将引发错误。 若要避免这类错误，请在从 <xref:System.Xml.XmlReader> 创建 XML 树之前，始终将 <xref:System.Xml.XmlReader> 定位在元素上。

## <a name="example"></a>示例

本示例使用以下 XML 文档：[示例 XML 文件：图书 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md)。

下面的代码创建一个 `T:System.Xml.XmlReader` 对象，然后读取节点，直到找到第一个元素节点。 然后加载 <xref:System.Xml.Linq.XElement> 对象。

```vb
Dim r As XmlReader = XmlReader.Create("books.xml")
Do While r.NodeType <> XmlNodeType.Element
    r.Read()
Loop
Dim e As XElement = XElement.Load(r)
Console.WriteLine(e)
```

该示例产生下面的输出：

```xml
<Catalog>
   <Book id="bk101">
      <Author>Garghentini, Davide</Author>
      <Title>XML Developer's Guide</Title>
      <Genre>Computer</Genre>
      <Price>44.95</Price>
      <PublishDate>2000-10-01</PublishDate>
      <Description>An in-depth look at creating applications
      with XML.</Description>
   </Book>
   <Book id="bk102">
      <Author>Garcia, Debra</Author>
      <Title>Midnight Rain</Title>
      <Genre>Fantasy</Genre>
      <Price>5.95</Price>
      <PublishDate>2000-12-16</PublishDate>
      <Description>A former architect battles corporate zombies,
      an evil sorceress, and her own childhood to become queen
      of the world.</Description>
   </Book>
</Catalog>
```

## <a name="see-also"></a>请参阅

- [Parsing XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
