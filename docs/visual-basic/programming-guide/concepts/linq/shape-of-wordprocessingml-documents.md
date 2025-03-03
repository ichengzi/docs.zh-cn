---
title: WordprocessingML 文档的形状
ms.date: 07/20/2015
ms.assetid: 2dfb446b-5a07-4c00-9ab3-a74ba734ff3a
ms.openlocfilehash: 64e9ca280c000ba488bfc72248bd83e37474f043
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350608"
---
# <a name="shape-of-wordprocessingml-documents-visual-basic"></a>Shape of WordprocessingML Documents (Visual Basic)
本主题介绍 WordprocessingML 文档的 XML 形状。  
  
## <a name="microsoft-office-formats"></a>Microsoft Office 格式  
 2007 Microsoft Office 系统的本机文件格式为 Office Open XML（通常称为 Open XML）。 Open XML 是一种基于 XML 的格式（Ecma 标准），当前即将通过 ISO-IEC 标准流程。 Open XML 中用于文字处理文件的标记语言称为 WordprocessingML。 本教程使用 WordprocessingML 源文件作为示例的输入。  
  
 如果使用 Microsoft Office 2003，则在已安装适用于 Word、Excel 和 PowerPoint 2007 文件格式的 Microsoft Office 兼容包的情况下，可以将文档保存为 Office Open XML 格式。  
  
## <a name="the-shape-of-wordprocessingml-documents"></a>WordprocessingML 文档的形状  
 首先要了解的是 WordprocessingML 文档的形状。 WordprocessingML 文档包含一个正文元素（称为 `w:body`），该元素包含文档的各个段落。 每个段落包含一个或多个文本域（称为 `w:r`）。 每个文本域包含一个或多个文本块（称为 `w:t`）。  
  
 下面是一个非常简单的 WordprocessingML 文档：  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<w:document  
xmlns:ve="http://schemas.openxmlformats.org/markup-compatibility/2006"  
xmlns:o="urn:schemas-microsoft-com:office:office"  
xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"  
xmlns:m="http://schemas.openxmlformats.org/officeDocument/2006/math"  
xmlns:v="urn:schemas-microsoft-com:vml"  
xmlns:wp="http://schemas.openxmlformats.org/drawingml/2006/wordprocessingDrawing"  
xmlns:w10="urn:schemas-microsoft-com:office:word"  
xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
xmlns:wne="http://schemas.microsoft.com/office/word/2006/wordml">  
  <w:body>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is a paragraph.</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is another paragraph.</w:t>  
      </w:r>  
    </w:p>  
  </w:body>  
</w:document>  
```  
  
 此文档包含两个段落。 这两个段落都包含单个文本域，每个文本域都包含单个文本块。  
  
 查看 XML 格式的 WordprocessingML 文档内容的最简单方式是使用 Microsoft Word 创建一个 XML 文档，保存该文档，然后运行下面的程序，将该 XML 打印到控制台。  
  
 本示例使用 WindowsBase 程序集中的类。 它使用 <xref:System.IO.Packaging?displayProperty=nameWithType> 命名空间中的类型。  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    Sub Main()  
        Dim documentRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
  
        Using wdPackage As Package = _  
          Package.Open("SampleDoc.docx", _  
                       FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = wdPackage _  
                .GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri( _  
                            New Uri("/", UriKind.Relative), _  
                            docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                ' Get the officeDocument part from the package.  
                ' Load the XML in the part into an XDocument instance.  
                Dim xDoc As XDocument = _  
                    XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
                Console.WriteLine(xDoc.Root)  
            End If  
        End Using  
    End Sub  
End Module  
```  
  
## <a name="external-resources"></a>外部资源  
 [介绍 Office (2007) Open XML 文件格式](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205(v=office.12))  
  
 [Overview of WordprocessingML](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812(v=office.11))（WordprocessingML 概述）  
  
 [Office 2003: XML Reference Schemas Download page](https://go.microsoft.com/fwlink/?LinkId=98095)（Office 2003：XML 参考架构下载页）  
  
## <a name="see-also"></a>请参阅

- [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
