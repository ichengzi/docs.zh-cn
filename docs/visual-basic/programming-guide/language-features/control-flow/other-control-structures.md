---
title: 其他控件结构
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: 758df361f421684655147ae288af3f350e53c4d7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348137"
---
# <a name="other-control-structures-visual-basic"></a>其他控件结构 (Visual Basic)
Visual Basic provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.  
  
## <a name="usingend-using-construction"></a>Using...End Using Construction  
 The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection. You can optionally acquire the resource with the `Using` statement. When you exit the `Using` block, Visual Basic automatically disposes of the resource so that it is available for other code to use. The resource must be local and disposable. 有关详细信息，请参阅 [Using 语句](../../../../visual-basic/language-reference/statements/using-statement.md)。  
  
## <a name="withend-with-construction"></a>With...End With Construction  
 The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members. This can simplify your code and improve performance because Visual Basic does not have to re-establish the reference for each statement that accesses it. For more information, see [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).  
  
## <a name="see-also"></a>请参阅

- [控制流](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [决策结构](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [循环结构](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [嵌套的控件结构](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Using 语句](../../../../visual-basic/language-reference/statements/using-statement.md)
- [With...End With 语句](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
