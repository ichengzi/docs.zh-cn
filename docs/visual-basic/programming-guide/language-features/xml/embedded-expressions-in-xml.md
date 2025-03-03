---
title: XML 中的嵌入式表达式
ms.date: 07/20/2015
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
ms.openlocfilehash: 0cdb960160457108ddf18c554dae5f5993269833
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332356"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a>XML 中的嵌入式表达式 (Visual Basic)
Embedded expressions enable you to create XML literals that contain expressions that are evaluated at run time. The syntax for an embedded expression is `<%=` `expression` `%>`, which is the same as the syntax used in ASP.NET.  
  
 For example, you can create an XML element literal, combining embedded expressions with literal text content.  
  
 [!code-vb[VbXMLSamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#27)]  
  
 If `isbnNumber` contains the integer 12345 and `modifiedDate` contains the date 3/5/2006, when this code executes, the value of `book` is:  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a>Embedded Expression Location and Validation  
 Embedded expressions can appear only at certain locations within XML literal expressions. The expression location controls which types the expression can return and how `Nothing` is handled. The following table describes the allowed locations and types of embedded expressions.  
  
|Location in literal|Type of expression|Handling of `Nothing`|  
|---|---|---|  
|XML element name|<xref:System.Xml.Linq.XName>|Error|  
|XML element content|`Object` or array of `Object`|忽略|  
|XML element attribute name|<xref:System.Xml.Linq.XName>|Error, unless the attribute value is also `Nothing`|  
|XML element attribute value|`Object`|Attribute declaration ignored|  
|XML element attribute|<xref:System.Xml.Linq.XAttribute> or a collection of <xref:System.Xml.Linq.XAttribute>|忽略|  
|XML document root element|<xref:System.Xml.Linq.XElement> or a collection of one <xref:System.Xml.Linq.XElement> object and an arbitrary number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects|忽略|  
  
- Example of an embedded expression in an XML element name:  
  
     [!code-vb[VbXMLSamples#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#32)]  
  
- Example of an embedded expression in the content of an XML element:  
  
     [!code-vb[VbXMLSamples#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#33)]  
  
- Example of an embedded expression in an XML element attribute name:  
  
     [!code-vb[VbXMLSamples#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#34)]  
  
- Example of an embedded expression in an XML element attribute value:  
  
     [!code-vb[VbXMLSamples#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#35)]  
  
- Example of an embedded expression in an XML element attribute:  
  
     [!code-vb[VbXMLSamples#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#36)]  
  
- Example of an embedded expression in an XML document root element:  
  
     [!code-vb[VbXMLSamples#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#37)]  
  
 If you enable `Option Strict`, the compiler checks that the type of each embedded expression widens to the required type. The only exception is for the root element of an XML document, which is verified when the code runs. If you compile without `Option Strict`, you can embed expressions of type `Object` and their type is verified at run time.  
  
 In locations where content is optional, embedded expressions that contain `Nothing` are ignored. This means you do not have to check that element content, attribute values, and array elements are not `Nothing` before you use an XML literal. Required values, such as element and attribute names, cannot be `Nothing`.  
  
 For more information about using an embedded expression in a particular type of literal, see [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="scoping-rules"></a>作用域规则  
 The compiler converts each XML literal into a constructor call for the appropriate literal type. The literal content and embedded expressions in an XML literal are passed as arguments to the constructor. This means that all Visual Basic programming elements available to an XML literal are also available to its embedded expressions.  
  
 Within an XML literal, you can access the XML namespace prefixes declared with the `Imports` statement. You can declare a new XML namespace prefix, or shadow an existing XML namespace prefix, in an element by using the `xmlns` attribute. The new namespace is available to the child nodes of that element, but not to XML literals in embedded expressions.  
  
> [!NOTE]
> When you declare an XML namespace prefix by using the `xmlns` namespace attribute, the attribute value must be a constant string. In this regard, using the `xmlns` attribute is like using the `Imports` statement to declare an XML namespace. You cannot use an embedded expression to specify the XML namespace value.  
  
## <a name="see-also"></a>请参阅

- [在 Visual Basic 中创建 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML 文档文本](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [XML 元素文本](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Option Strict 语句](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Imports 语句（.NET 命名空间和类型）](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [XML 文本概述](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
