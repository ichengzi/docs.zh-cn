---
title: '#Const 指令'
ms.date: 07/20/2015
f1_keywords:
- vb.#Const
- '#vb.Const'
- '#Const'
helpviewer_keywords:
- '#Const directive'
- conditional compilation [Visual Basic], directives
- Const directive (#Const)
- Visual Basic compiler, compiler directives
- constants [Visual Basic], Const directive
- constants [Visual Basic], declaring
- Const statement [Visual Basic], directive (#Const)
- 'declaring constants [Visual Basic], #const directive'
ms.assetid: 707669e5-23f9-4f17-8622-a0d534429386
ms.openlocfilehash: 278219edb1bb5d1c0bb015611d69cbe4ae70014b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343847"
---
# <a name="const-directive"></a>#Const 指令

Defines conditional compiler constants for Visual Basic.  
  
## <a name="syntax"></a>语法  
  
```vb  
#Const constname = expression  
```  
  
## <a name="parts"></a>部件  

 `constname`  
 必须的。 Name of the constant being defined.  
  
 `expression`  
 必须的。 Literal, other conditional compiler constant, or any combination that includes any or all arithmetic or logical operators except `Is`.  
  
## <a name="remarks"></a>备注  

 Conditional compiler constants are always private to the file in which they appear. You cannot create public compiler constants using the `#Const` directive; you can create them only in the user interface or with the `/define` compiler option.  
  
 You can use only conditional compiler constants and literals in `expression`. Using a standard constant defined with `Const` causes an error. Conversely, you can use constants defined with the `#Const` keyword only for conditional compilation. Constants can also be undefined, in which case they have a value of `Nothing`.  
  
## <a name="example"></a>示例  

 此示例使用 `#Const` 指令。  
  
 [!code-vb[VbVbalrConditionalComp#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>请参阅

- [-define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [#If...Then...#Else 指令](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Const 语句](../../../visual-basic/language-reference/statements/const-statement.md)
- [条件编译](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [If...Then...Else 语句](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
