---
title: 检索段落及其样式
ms.date: 07/20/2015
ms.assetid: d9ed2238-d38e-4ad4-b88b-db7859df9bde
ms.openlocfilehash: 862a07c26733a4989ae010854ceaca1fd7e3578e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347514"
---
# <a name="retrieving-the-paragraphs-and-their-styles-visual-basic"></a>Retrieving the Paragraphs and Their Styles (Visual Basic)
在本示例中，我们编写一个从 WordprocessingML 文档检索段落节点的查询。 它还标识每个段落的样式。  
  
 This query builds on the query in the previous example, [Finding the Default Paragraph Style (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), which retrieves the default style from the list of styles. 这些信息是必需的，以便查询能标识未显式设置样式的段落样式。 段落样式通过 `w:pPr` 元素来设置；如果段落未包含此元素，则它会使用默认样式的格式。  
  
 本主题解释某些查询的意义，然后作为一个完整工作示例的一部分来显示查询。  
  
## <a name="example"></a>示例  
 检索文档中所有段落及其样式的查询的源如下所示：  
  
```vb  
xDoc.Root.<w:body>...<w:p>  
```  
  
 This expression is similar to the source of the query in the previous example, [Finding the Default Paragraph Style (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md). 主要区别是它使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 轴，而不是 <xref:System.Xml.Linq.XContainer.Elements%2A> 轴。 该查询使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 轴，因为在包含节的文档中，段落将不是正文元素的直接子元素；而是在层次结构中的两个级别之下。 通过使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 轴，无论文档是否使用节，代码都能运行。  
  
## <a name="example"></a>示例  
 该查询使用 `Let` 子句来确定包含样式节点的元素。 如果没有任何元素，则将 `styleNode` 设置为 `Nothing`：  
  
```vb  
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()  
```  
  
 `Let` 子句首先使用 <xref:System.Xml.Linq.XContainer.Elements%2A> 轴，查找所有名为 `pPr` 的元素，然后使用 <xref:System.Xml.Linq.Extensions.Elements%2A> 扩展方法，查找所有名为 `pStyle` 的子元素，最后使用 <xref:System.Linq.Enumerable.FirstOrDefault%2A> 标准查询运算符，将集合转换为单一实例。 如果集合为空，则将 `styleNode` 设置为 `Nothing`。 这是一个用于查找 `pStyle` 子代节点的有用方法。 请注意，如果 `pPr` 子节点不存在，代码不会通过引发异常而运行失败；相反，它会将 `styleNode` 设置为 `Nothing`，这是此 `Let` 子句的期望行为。  
  
 该查询投影一个具有两个成员 `StyleName` 和 `ParagraphNode` 的匿名类型的集合。  
  
## <a name="example"></a>示例  
 本示例处理一个 WordprocessingML 文档，它从 WordprocessingML 文档中检索段落节点。 它还标识每个段落的样式。 本示例以本教程中前面的一些示例为基础构建。 下面代码中的注释标识出了这个新查询。  
  
 You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
 本示例使用 WindowsBase 程序集中的类。 它使用 <xref:System.IO.Packaging?displayProperty=nameWithType> 命名空间中的类型。  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, ByVal defaultStyle As String) As String  
        If (styleNode Is Nothing) Then  
            Return defaultStyle  
        Else  
            Return styleNode.@w:val  
        End If  
    End Function  
  
    Sub Main()  
        Dim fileName = "SampleDoc.docx"  
  
        Dim documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Dim stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
        Dim wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                '  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                '  Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If (styleRelation IsNot Nothing) Then  
                    Dim styleUri As Uri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)  
  
                    '  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
            End If  
        End Using  
  
        Dim defaultStyle As String = _  
            ( _  
                From style In styleDoc.Root.<w:style> _  
                Where style.@w:type = "paragraph" And _  
                      style.@w:default = "1" _  
                Select style _  
            ).First().@w:styleId  
  
        ' Following is the new query that finds all paragraphs in the  
        ' document and their styles.  
        Dim paragraphs = _  
            From para In xDoc.Root.<w:body>...<w:p> _  
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault() _  
        Select New With { _  
            .ParagraphNode = para, _  
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _  
        }  
  
        For Each p In paragraphs  
            Console.WriteLine("StyleName:{0}", p.StyleName)  
        Next  
  
    End Sub  
End Module  
```  
  
 This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
```console  
StyleName:Heading1  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
```  
  
## <a name="next-steps"></a>后续步骤  
 In the next topic, [Retrieving the Text of the Paragraphs (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), you'll create a query to retrieve the text of paragraphs.  
  
## <a name="see-also"></a>请参阅

- [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
