---
title: <example>
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 8f36ac1337dd0d1400180fbd3deae2bb24ad9c58
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348483"
---
# <a name="example-visual-basic"></a>\<example> (Visual Basic)
Specifies an example for the member.  
  
## <a name="syntax"></a>语法  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a>参数  
 `description`  
 代码示例的说明。  
  
## <a name="remarks"></a>备注  
 The `<example>` tag lets you specify an example of how to use a method or other library member. 这通常涉及到使用 [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) 标记。  
  
 使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 进行编译以便将文档注释处理到文件中。  
  
## <a name="example"></a>示例  
 This example uses the `<example>` tag to include an example for using the `ID` field.  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>请参阅

- [XML 注释标记](../../../visual-basic/language-reference/xmldoc/index.md)
