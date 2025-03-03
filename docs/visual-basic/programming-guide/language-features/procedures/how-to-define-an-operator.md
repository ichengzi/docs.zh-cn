---
title: 如何：定义运算符
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- operator procedures [Visual Basic], about operator procedures
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
ms.openlocfilehash: b99af8ff4d5428f1749bfc1a4c51a136f12405ee
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344866"
---
# <a name="how-to-define-an-operator-visual-basic"></a>如何：定义运算符 (Visual Basic)
If you have defined a class or structure, you can define the behavior of a standard operator (such as `*`, `<>`, or `And`) when one or both of the operands is of the type of your class or structure.  
  
 Define the standard operator as an operator procedure within the class or structure. All operator procedures must be `Public` `Shared`.  
  
 Defining an operator on a class or structure is also called *overloading* the operator.  
  
## <a name="example"></a>示例  
 The following example defines the `+` operator for a structure called `height`. The structure uses heights measured in feet and inches. One *inch* is 2.54 centimeters, and one *foot* is 12 inches. To ensure normalized values (inches < 12.0), the constructor performs *modulo* 12 arithmetic. The `+` operator uses the constructor to generate normalized values.  
  
 [!code-vb[VbVbcnProcedures#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#25)]  
  
 You can test the structure `height` with the following code.  
  
 [!code-vb[VbVbcnProcedures#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#26)]  

## <a name="see-also"></a>请参阅

- [运算符过程](./operator-procedures.md)
- [如何：定义转换运算符](./how-to-define-a-conversion-operator.md)
- [如何：调用运算符过程](./how-to-call-an-operator-procedure.md)
- [如何：使用定义运算符的类](./how-to-use-a-class-that-defines-operators.md)
- [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Structure 语句](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [如何：声明结构](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Mod 运算符](../../../../visual-basic/language-reference/operators/mod-operator.md)
