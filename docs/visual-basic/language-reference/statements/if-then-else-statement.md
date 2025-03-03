---
title: If...Then...Else 语句
ms.date: 04/16/2018
f1_keywords:
- vb.ElseIf
- vb.Then
- vb.If
- vb.EndIf
helpviewer_keywords:
- ElseIf statement [Visual Basic], If...Then...Else
- Then statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], branching
- execution [Visual Basic], conditional
- TypeOf...Is expression, and If...Then...Else statements
- If...Then...Else statements
- If statement [Visual Basic], If...Then...Else
- If statement [Visual Basic]
- Is operator [Visual Basic], in If...Then...Else statements
- If Operator [Visual Basic]
- branching [Visual Basic], conditional
- If function [Visual Basic], and If...Then...Else statements
- Else statement [Visual Basic]
ms.assetid: 790068a2-1307-4e28-8a72-be5ebda099e9
ms.openlocfilehash: f505755caeb9cc3cfeeb1ba83b6de15f48314103
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351160"
---
# <a name="ifthenelse-statement-visual-basic"></a>If...Then...Else 语句 (Visual Basic)

根据表达式的值有条件地执行一组语句。

## <a name="syntax"></a>语法

```vb
' Multiline syntax:
If condition [ Then ]
    [ statements ]
[ ElseIf elseifcondition [ Then ]
    [ elseifstatements ] ]
[ Else
    [ elsestatements ] ]
End If

' Single-line syntax:
If condition Then [ statements ] [ Else [ elsestatements ] ]
```

## <a name="quick-links-to-example-code"></a>Quick links to example code

This article includes several examples that illustrate uses of the `If`...`Then`...`Else` statement:

- [Multiline syntax example](#multi-line)
- [Nested syntax example](#nested)
- [Single-line syntax example](#single-line)

## <a name="parts"></a>部件

`condition` \
必须的。 Expression. Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.

If the expression is a [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variable that evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the condition is treated as if the expression is `False`, and the `ElseIf` blocks are evaluated if they exist, or the `Else` block is executed if it exists.

`Then` \
Required in the single-line syntax; optional in the multiline syntax.

`statements` \
可选。 后面`If`的一个或多个语句 ...如果计算结果为`True`，则执行。 `condition` `Then`

`elseifcondition` \
Required if `ElseIf` is present. Expression. Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.

`elseifstatements` \
可选。 后面`ElseIf`的一个或多个语句 ...如果计算结果为`True`，则执行。 `elseifcondition` `Then`

`elsestatements` \
可选。 One or more statements that are executed if no previous `condition` or `elseifcondition` expression evaluates to `True`.

`End If` \
Terminates the multiline version of `If`...`Then`...`Else` block.

## <a name="remarks"></a>备注

### <a name="multiline-syntax"></a>Multiline syntax

When an `If`...`Then`...`Else` statement is encountered, `condition` is tested. If `condition` is `True`, the statements following `Then` are executed. If `condition` is `False`, each `ElseIf` statement (if there are any) is evaluated in order. When a `True` `elseifcondition` is found, the statements immediately following the associated `ElseIf` are executed. If no `elseifcondition` evaluates to `True`, or if there are no `ElseIf` statements, the statements following `Else` are executed. After executing the statements following `Then`, `ElseIf`, or `Else`, execution continues with the statement following `End If`.

The `ElseIf` and `Else` clauses are both optional. You can have as many `ElseIf` clauses as you want in an `If`...`Then`...`Else` statement, but no `ElseIf` clause can appear after an `Else` clause. `If`...`Then`...`Else` statements can be nested within each other.

In the multiline syntax, the `If` statement must be the only statement on the first line. The `ElseIf`, `Else`, and `End If` statements can be preceded only by a line label. The `If`...`Then`...`Else` block must end with an `End If` statement.

> [!TIP]
> The [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) might be more useful when you evaluate a single expression that has several possible values.

### <a name="single-line-syntax"></a>Single-Line syntax

You can use the single-line syntax for a single condition with code to execute if it's true. However, the multiple-line syntax provides more structure and flexibility and is easier to read, maintain, and debug.

What follows the `Then` keyword is examined to determine whether a statement is a single-line `If`. If anything other than a comment appears after `Then` on the same line, the statement is treated as a single-line `If` statement. If `Then` is absent, it must be the start of a multiple-line `If`...`Then`...`Else`.

In the single-line syntax, you can have multiple statements executed as the result of an `If`...`Then` decision. All statements must be on the same line and be separated by colons.

## <a name="multiline-syntax-example"></a>Multiline syntax example

<a name="multi-line"></a>

The following example illustrates the use of the multiline syntax of the `If`...`Then`...`Else` statement.

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a>Nested syntax example

<a name="nested"></a>

The following example contains nested `If`...`Then`...`Else` statements.

[!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a>Single-Line syntax example

<a name="single-line"></a> The following example illustrates the use of the single-line syntax.

[!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]

## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [#If...Then...#Else 指令](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Select...Case 语句](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [嵌套的控件结构](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [决策结构](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Logical and Bitwise Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [If 运算符](../../../visual-basic/language-reference/operators/if-operator.md)
