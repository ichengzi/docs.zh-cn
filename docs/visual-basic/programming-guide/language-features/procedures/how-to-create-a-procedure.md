---
title: 如何：创建过程
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: a831814c18f97991fca8067f1c9c8e491da1b665
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344914"
---
# <a name="how-to-create-a-procedure-visual-basic"></a>如何：创建过程 (Visual Basic)

You enclose a procedure between a starting declaration statement (`Sub` or `Function`) and an ending declaration statement (`End Sub` or `End Function`). All the procedure's code lies between these statements.

 A procedure cannot contain another procedure, so its starting and ending statements must be outside any other procedure.

 If you have code that performs the same task in different places, you can write the task once as a procedure and then call it from different places in your code.

### <a name="to-create-a-procedure-that-does-not-return-a-value"></a>To create a procedure that does not return a value

1. Outside any other procedure, use a `Sub` statement, followed by an `End Sub` statement.

2. In the `Sub` statement, follow the `Sub` keyword with the name of the procedure, then the parameter list in parentheses.

3. Place the procedure's code statements between the `Sub` and `End Sub` statements.

### <a name="to-create-a-procedure-that-returns-a-value"></a>To create a procedure that returns a value

1. Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.

2. In the `Function` statement, follow the `Function` keyword with the name of the procedure, then the parameter list in parentheses, and then an `As` clause specifying the data type of the return value.

3. Place the procedure's code statements between the `Function` and `End Function` statements.

4. Use a `Return` statement to return the value to the calling code.

### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a>To connect your new procedure with the old, repetitive blocks of code

1. Make sure you define the new procedure in a place where the old code has access to it.

2. In your old, repetitive code block, replace the statements that perform the repetitive task with a single statement that calls the `Sub` or `Function` procedure.

3. If your procedure is a `Function` that returns a value, ensure that your calling statement performs an action with the returned value, such as storing it in a variable, or else the value will be lost.

## <a name="example"></a>示例

 The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides:

 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

## <a name="see-also"></a>请参阅

- [过程](index.md)
- [Sub 过程](sub-procedures.md)
- [Function 过程](function-procedures.md)
- [属性过程](property-procedures.md)
- [运算符过程](operator-procedures.md)
- [过程参数和自变量](procedure-parameters-and-arguments.md)
- [递归过程](recursive-procedures.md)
- [过程重载](procedure-overloading.md)
- [对象和类](../objects-and-classes/index.md)
- [面向对象的编程 (Visual Basic)](../../concepts/object-oriented-programming.md)
