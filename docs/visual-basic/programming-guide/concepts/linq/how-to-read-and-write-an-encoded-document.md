---
title: 如何：读取和写入嵌入文档
ms.date: 07/20/2015
ms.assetid: 159d868f-5ac8-40f2-95ca-07dd925f35c6
ms.openlocfilehash: 913b08d91b8d4886bc74cbe538df8e27826a6cca
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347620"
---
# <a name="how-to-read-and-write-an-encoded-document-visual-basic"></a>How to: Read and Write an Encoded Document (Visual Basic)

若要创建编码的 XML 文档，请向 XML 树中添加一个 <xref:System.Xml.Linq.XDeclaration>，将编码设置为需要的代码页名称。

由 <xref:System.Text.Encoding.WebName%2A> 返回的任何值都是有效值。

如果您读取编码的文档，则要将 <xref:System.Xml.Linq.XDeclaration.Encoding%2A> 属性设置为该代码页名称。

如果将 <xref:System.Xml.Linq.XDeclaration.Encoding%2A> 设置为一个有效的代码页名称，则 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 将用指定的编码进行序列化。

## <a name="example"></a>示例

下面的示例创建两个文档，一个文档使用 utf-8 编码，另一个使用 utf-16 编码。 然后，该示例加载这两个文档并将编码输出到控制台。

```vb
Console.WriteLine("Creating a document with utf-8 encoding")
Dim encodedDoc8 As XDocument = _
        <?xml version='1.0' encoding='utf-8' standalone='yes'?>
        <Root>Content</Root>

encodedDoc8.Save("EncodedUtf8.xml")
Console.WriteLine("Encoding is:{0}", encodedDoc8.Declaration.Encoding)
Console.WriteLine()

Console.WriteLine("Creating a document with utf-16 encoding")
Dim encodedDoc16 As XDocument = _
        <?xml version='1.0' encoding='utf-16' standalone='yes'?>
        <Root>Content</Root>

encodedDoc16.Save("EncodedUtf16.xml")
Console.WriteLine("Encoding is:{0}", encodedDoc16.Declaration.Encoding)
Console.WriteLine()

Dim newDoc8 As XDocument = XDocument.Load("EncodedUtf8.xml")
Console.WriteLine("Encoded document:")
Console.WriteLine(File.ReadAllText("EncodedUtf8.xml"))
Console.WriteLine()
Console.WriteLine("Encoding of loaded document is:{0}", newDoc8.Declaration.Encoding)
Console.WriteLine()

Dim newDoc16 As XDocument = XDocument.Load("EncodedUtf16.xml")
Console.WriteLine("Encoded document:")
Console.WriteLine(File.ReadAllText("EncodedUtf16.xml"))
Console.WriteLine()
Console.WriteLine("Encoding of loaded document is:{0}", newDoc16.Declaration.Encoding)
```

该示例产生下面的输出：

```console
Creating a document with utf-8 encoding
Encoding is:utf-8

Creating a document with utf-16 encoding
Encoding is:utf-16

Encoded document:
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Root>Content</Root>

Encoding of loaded document is:utf-8

Encoded document:
<?xml version="1.0" encoding="utf-16" standalone="yes"?>
<Root>Content</Root>

Encoding of loaded document is:utf-16
```

## <a name="see-also"></a>请参阅

- <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=nameWithType>
- [Advanced LINQ to XML Programming (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
