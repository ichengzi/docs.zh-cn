---
title: <summary>
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 3bc4393d2fa14f804c6383780e238b1ac2610a94
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352202"
---
# <a name="summary-visual-basic"></a>\<summary> (Visual Basic)
Specifies the summary of the member.  
  
## <a name="syntax"></a>语法  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a>参数  
 `description`  
 对象的摘要。  
  
## <a name="remarks"></a>备注  
 Use the `<summary>` tag to describe a type or a type member. 使用 [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) 可针对某个类型说明添加补充信息。  
  
 The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser. For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).  
  
 使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 进行编译以便将文档注释处理到文件中。  
  
## <a name="example"></a>示例  
 This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>请参阅

- [XML 注释标记](../../../visual-basic/language-reference/xmldoc/index.md)
