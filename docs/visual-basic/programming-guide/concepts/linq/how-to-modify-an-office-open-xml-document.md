---
title: 如何：修改 Office Open XML 文档
ms.date: 07/20/2015
ms.assetid: 1cefd7f5-8e39-44c4-869c-f8021538a777
ms.openlocfilehash: 623376a68ee2f032fb53d51b61c4c5881b0b9e18
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336018"
---
# <a name="how-to-modify-an-office-open-xml-document-visual-basic"></a>How to: Modify an Office Open XML Document (Visual Basic)
本主题显演示一个打开、修改和保存 Office Open XML 文档的示例。  
  
 For more information on Office Open XML, see [Eric White's Blog](http://www.ericwhite.com).  
  
## <a name="example"></a>示例  
 本示例查找文档中的第一个段落元素。 示例从段落中检索文本，然后删除段落中的所有文本域。 它创建一个由第一个段落已转换为大写的文本构成的新文本域。 然后将已更改的 XML 序列化为 Open XML 包并关闭该包。  
  
 本示例使用 WindowsBase 程序集中的类。 它使用 <xref:System.IO.Packaging?displayProperty=nameWithType> 命名空间中的类型。  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(ByVal source As IEnumerable(Of String)) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each s As String In source  
            sb.Append(s)  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal func As Func(Of T, String)) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each item As T In source  
            sb.Append(func(item))  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal separator As String) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each s As T In source  
            sb.Append(s).Append(separator)  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal func As Func(Of T, String), ByVal separator As String) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each item As T In source  
            sb.Append(func(item)).Append(separator)  
        Next  
        Return sb.ToString()  
    End Function  
  
    Public Function ParagraphText(ByVal e As XElement) As String  
        Dim w As XNamespace = e.Name.Namespace  
        Return (e.<w:r>.<w:t>).StringConcatenate(Function(element) CStr(element))  
    End Function  
  
    ' Following function is required because VB does not support short circuit evaluation  
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, _  
                                         ByVal defaultStyle As String) As String  
        If (styleNode Is Nothing) Then  
            Return defaultStyle  
        Else  
            Return styleNode.@w:val  
        End If  
    End Function  
  
    Sub Main()  
        Dim fileName = "SampleDoc.docx"  
  
        Dim documentRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Dim stylesRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
        Dim wordmlNamespace = _  
          "http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.ReadWrite)  
            Dim docPackageRelationship As PackageRelationship = wdPackage _  
                    .GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", _  
                            UriKind.Relative), docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                '  Load the document XML in the part into an XDocument instance.  
                Dim xDoc As XDocument = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                '  Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = documentPart _  
                        .GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                Dim stylePart As PackagePart = Nothing  
                Dim styleDoc As XDocument = Nothing  
  
                If (styleRelation IsNot Nothing) Then  
                    Dim styleUri As Uri = PackUriHelper.ResolvePartUri( _  
                            documentUri, styleRelation.TargetUri)  
                    stylePart = wdPackage.GetPart(styleUri)  
  
                    ' Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
  
                Dim paraNode As XElement = xDoc.Root.<w:body>...<w:p>.FirstOrDefault()  
  
                Dim paraText As String = ParagraphText(paraNode)  
  
                ' Remove all text runs.  
                paraNode...<w:r>.Remove()  
  
                paraNode.Add(<w:r><w:t><%= paraText.ToUpper() %></w:t></w:r>)  
  
                ' Save the XML into the package.  
                Using xw As XmlWriter = _  
                  XmlWriter.Create(documentPart.GetStream(FileMode.Create, FileAccess.Write))  
                    xDoc.Save(xw)  
                End Using  
  
                Console.WriteLine("New first paragraph: >{0}<", paraText.ToUpper())  
            End If  
        End Using  
    End Sub  
End Module  
```  
  
 如果在运行此程序之后打开 `SampleDoc.docx`，则可以看到此程序已将文档中的第一个段落转换为大写。  
  
 When run with the sample Open XML document described in [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md), this example produces the following output:  
  
```console  
New first paragraph: >PARSING WORDPROCESSINGML WITH LINQ TO XML<  
```  
  
## <a name="see-also"></a>请参阅

- [Advanced Query Techniques (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
