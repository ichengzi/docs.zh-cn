---
title: 特性列表
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: f9332f52622551bb6b944242f71bd80f439982e9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354063"
---
# <a name="attribute-list-visual-basic"></a>特性列表 (Visual Basic)
Specifies the attributes to be applied to a declared programming element. 用逗号分隔多个属性。 Following is the syntax for one attribute.  
  
## <a name="syntax"></a>语法  
  
```vb  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a>部件  
|||
|---|---|
|`attributemodifier`|Required for attributes applied at the beginning of a source file. Can be [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) or [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md).|
|`attributename`| 必须的。 属性的名称。|
|`attributearguments`|可选。 List of positional arguments for this attribute. Multiple arguments are separated by commas.|
|`attributeinitializer`|可选。 List of variable or property initializers for this attribute. Multiple initializers are separated by commas.|
  
## <a name="remarks"></a>备注  
 You can apply one or more attributes to nearly any programming element (types, procedures, properties, and so forth). Attributes appear in your assembly's metadata, and they can help you annotate your code or specify how to use a particular programming element. You can apply attributes defined by Visual Basic and the .NET Framework, and you can define your own attributes.  

 For more information on when to use attributes, see [Attributes overview](../../../visual-basic/programming-guide/concepts/attributes/index.md). For information on attribute names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="rules"></a>规则  
  
- **Placement.** You can apply attributes to most declared programming elements. To apply one or more attributes, you place an *attribute block* at the beginning of the element declaration. Each entry in the attribute list specifies an attribute you wish to apply, and the modifier and arguments you are using for this invocation of the attribute.  
  
- **Angle Brackets.** If you supply an attribute list, you must enclose it in angle brackets ("`<`" and "`>`").  
  
- **Part of the Declaration.** The attribute must be part of the element declaration, not a separate statement. You can use the line-continuation sequence (" `_`") to extend the declaration statement onto multiple source-code lines.  
  
- **Modifiers.** An attribute modifier (`Assembly` or `Module`) is required on every attribute applied to a programming element at the beginning of a source file. Attribute modifiers are not allowed on attributes applied to elements that are not at the beginning of a source file.  
  
- **Arguments.** All positional arguments for an attribute must precede any variable or property initializers.  
  
## <a name="example"></a>示例  
 The following example applies the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute to a skeleton definition of a `Function` procedure.  
  
 [!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]  
  
 <xref:System.Runtime.InteropServices.DllImportAttribute> indicates that the attributed procedure represents an entry point in an unmanaged dynamic-link library (DLL). The attribute supplies the DLL name as a positional argument and the other information as variable initializers.  
  
## <a name="see-also"></a>请参阅

- [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md)
- [Module \<关键字>](../../../visual-basic/language-reference/modifiers/module-keyword.md)
- [属性概述](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [如何：在代码中拆分和合并语句](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
