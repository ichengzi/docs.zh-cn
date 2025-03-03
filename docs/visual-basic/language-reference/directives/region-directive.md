---
title: '#Region 指令'
ms.date: 07/20/2015
f1_keywords:
- vb.Region
- vb.#Region
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword [Visual Basic]'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
ms.openlocfilehash: 4cf9b103486378d001b588aa285f590980b51bb8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343791"
---
# <a name="region-directive"></a>#Region 指令

折叠并隐藏 Visual Basic 文件中的代码段。  
  
## <a name="syntax"></a>语法  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`identifier_string`|必须的。 当区域处于折叠状态时充当区域标题的字符串。 默认情况下，区域处于折叠状态。|  
|`#End Region`|终止 `#Region` 块。|  
  
## <a name="remarks"></a>备注  

 使用 `#Region` 指令指定使用 Visual Studio Code 编辑器的大纲显示功能时要展开或折叠的代码块。 You can place, or *nest*, regions within other regions to group similar regions together.  
  
## <a name="example"></a>示例  

 此示例使用 `#Region` 指令。  
  
 [!code-vb[VbVbalrConditionalComp#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#4)]  
  
## <a name="see-also"></a>请参阅

- [#If...Then...#Else 指令](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [大纲显示](/visualstudio/ide/outlining)
- [如何：折叠和隐藏代码节](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
