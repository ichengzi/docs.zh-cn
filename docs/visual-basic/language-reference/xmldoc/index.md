---
title: Recommended XML Tags for Documentation Comments
ms.date: 07/20/2015
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
ms.openlocfilehash: 093c967557b899c8661fdec348d421996e948b94
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352338"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>建议的用于文档注释的 XML 标记 (Visual Basic)
The Visual Basic compiler can process documentation comments in your code to an XML file. You can use additional tools to process the XML file into documentation.  
  
 XML comments are allowed on code constructs such as types and type members. For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.  
  
> [!NOTE]
> Documentation comments cannot be applied to namespaces. The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.  
  
 The compiler processes any tag that is valid XML. The following tags provide commonly used functionality in user documentation.  
  
||||  
|---|---|---|  
|[\<c>](../../../visual-basic/language-reference/xmldoc/c.md)|[\<code>](../../../visual-basic/language-reference/xmldoc/code.md)|[\<example>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup>|[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup>|[\<list>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<para>](../../../visual-basic/language-reference/xmldoc/para.md)|[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup>|[\<paramref>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup>|[\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup>|[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup>|[\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup>|[\<value>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 (<sup>1</sup> The compiler verifies syntax.)  
  
> [!NOTE]
> If you want angle brackets to appear in the text of a documentation comment, use `&lt;` and `&gt;`. For example, the string `"&lt;text in angle brackets&gt;"` will appear as `<text in angle brackets>`.  
  
## <a name="see-also"></a>请参阅

- [使用 XML 记录代码](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [-doc](../../../visual-basic/reference/command-line-compiler/doc.md)
- [如何：创建 XML 文档](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
