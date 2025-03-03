---
title: 如何：创建固定值变量
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: d5d8a6b066ae7e8795afd2f788b60823d8efdafa
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348636"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a>如何：创建固定值变量 (Visual Basic)

The notion of a variable that does not change its value might appear to be contradictory. But there are situations when a constant is not feasible and it is useful to have a variable with a fixed value. In such a case you can define a member variable with the [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) keyword.

You cannot use the [Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value in the following circumstances:

- The `Const` statement does not accept the data type you want to use

- You do not know the value at compile time

- You are unable to compute the constant value at compile time

### <a name="to-create-a-variable-that-does-not-change-in-value"></a>To create a variable that does not change in value

1. At module level, declare a member variable with the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md), and include the [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) keyword.

    ```vb
    Dim ReadOnly timeStarted
    ```

    You can specify `ReadOnly` only on a member variable. This means you must define the variable at module level, outside of any procedure.

2. If you can compute the value in a single statement at compile time, use an initialization clause in the `Dim` statement. Follow the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause with an equal sign (`=`), followed by an expression. Be sure the compiler can evaluate this expression to a constant value.

    ```vb
    Dim ReadOnly timeStarted As Date = Now
    ```

    You can assign a value to a `ReadOnly` variable only once. Once you do so, no code can ever change its value.

    If you do not know the value at compile time, or cannot compute it at compile time in a single statement, you can still assign it at run time in a constructor. To do this, you must declare the `ReadOnly` variable at class or structure level. In the constructor for that class or structure, compute the variable's fixed value, and assign it to the variable before returning from the constructor.

## <a name="see-also"></a>请参阅

- [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [Const 语句](../../../../visual-basic/language-reference/statements/const-statement.md)
