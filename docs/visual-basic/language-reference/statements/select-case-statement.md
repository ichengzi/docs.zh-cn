---
title: Select...Case 语句
ms.date: 07/20/2015
f1_keywords:
- vb.Select
- vb.Case
helpviewer_keywords:
- Select statement [Visual Basic]
- Case statement [Visual Basic]
- Select...Case statements
- conditional statements [Visual Basic], Select Case
- control flow [Visual Basic], branching
- Else keyword [Visual Basic], in Select...Case statements
- execution [Visual Basic], conditional
- To keyword [Visual Basic], in Select...Case statements
- Select Case statement [Visual Basic], Select...Case
- Select statement [Visual Basic], Select...Case
- Is operator [Visual Basic], in Select...Case statements
- branching [Visual Basic], conditional
- Case Else statement [Visual Basic], Select...Case
- End keyword [Visual Basic], Select Case statements
- Case statement [Visual Basic], Select...Case
ms.assetid: 68877b65-5419-4bf0-a465-20cd0e4c7d44
ms.openlocfilehash: 4dddfe5fbf7092c911291ffc6841e76f8c2748e9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352831"
---
# <a name="selectcase-statement-visual-basic"></a>Select...Case 语句 (Visual Basic)
Runs one of several groups of statements, depending on the value of an expression.  
  
## <a name="syntax"></a>语法  
  
```vb  
Select [ Case ] testexpression  
    [ Case expressionlist  
        [ statements ] ]  
    [ Case Else  
        [ elsestatements ] ]  
End Select  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`testexpression`|必须的。 Expression. Must evaluate to one of the elementary data types (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, and `UShort`).|  
|`expressionlist`|Required in a `Case` statement. List of expression clauses representing match values for `testexpression`. Multiple expression clauses are separated by commas. Each clause can take one of the following forms:<br /><br /> -   *expression1* `To` *expression2*<br />-   [ `Is` ] *comparisonoperator* *expression*<br />-   *expression*<br /><br /> Use the `To` keyword to specify the boundaries of a range of match values for `testexpression`. The value of `expression1` must be less than or equal to the value of `expression2`.<br /><br /> Use the `Is` keyword with a comparison operator (`=`, `<>`, `<`, `<=`, `>`, or `>=`) to specify a restriction on the match values for `testexpression`. If the `Is` keyword is not supplied, it is automatically inserted before *comparisonoperator*.<br /><br /> The form specifying only `expression` is treated as a special case of the `Is` form where *comparisonoperator* is the equal sign (`=`). This form is evaluated as `testexpression` = `expression`.<br /><br /> The expressions in `expressionlist` can be of any data type, provided they are implicitly convertible to the type of `testexpression` and the appropriate `comparisonoperator` is valid for the two types it is being used with.|  
|`statements`|可选。 One or more statements following `Case` that run if `testexpression` matches any clause in `expressionlist`.|  
|`elsestatements`|可选。 One or more statements following `Case Else` that run if `testexpression` does not match any clause in the `expressionlist` of any of the `Case` statements.|  
|`End Select`|Terminates the definition of the `Select`...`Case` construction.|  
  
## <a name="remarks"></a>备注  
 If `testexpression` matches any `Case` `expressionlist` clause, the statements following that `Case` statement run up to the next `Case`, `Case Else`, or `End Select` statement. Control then passes to the statement following `End Select`. If `testexpression` matches an `expressionlist` clause in more than one `Case` clause, only the statements following the first match run.  
  
 The `Case Else` statement is used to introduce the `elsestatements` to run if no match is found between the `testexpression` and an `expressionlist` clause in any of the other `Case` statements. Although not required, it is a good idea to have a `Case Else` statement in your `Select Case` construction to handle unforeseen `testexpression` values. If no `Case` `expressionlist` clause matches `testexpression` and there is no `Case Else` statement, control passes to the statement following `End Select`.  
  
 You can use multiple expressions or ranges in each `Case` clause. For example, the following line is valid.  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
> The `Is` keyword used in the `Case` and `Case Else` statements is not the same as the [Is Operator](../../../visual-basic/language-reference/operators/is-operator.md), which is used for object reference comparison.  
  
 You can specify ranges and multiple expressions for character strings. In the following example, `Case` matches any string that is exactly equal to "apples", has a value between "nuts" and "soup" in alphabetical order, or contains the exact same value as the current value of `testItem`.  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 The setting of `Option Compare` can affect string comparisons. Under `Option Compare Text`, the strings "Apples" and "apples" compare as equal, but under `Option Compare Binary`, they do not.  
  
> [!NOTE]
> A `Case` statement with multiple clauses can exhibit behavior known as *short-circuiting*. Visual Basic evaluates the clauses from left to right, and if one produces a match with `testexpression`, the remaining clauses are not evaluated. Short-circuiting can improve performance, but it can produce unexpected results if you are expecting every expression in `expressionlist` to be evaluated. For more information on short-circuiting, see [Boolean Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).  
  
 If the code within a `Case` or `Case Else` statement block does not need to run any more of the statements in the block, it can exit the block by using the `Exit Select` statement. This transfers control immediately to the statement following `End Select`.  
  
 `Select Case` constructions can be nested. Each nested `Select Case` construction must have a matching `End Select` statement and must be completely contained within a single `Case` or `Case Else` statement block of the outer `Select Case` construction within which it is nested.  
  
## <a name="example"></a>示例  
 The following example uses a `Select Case` construction to write a line corresponding to the value of the variable `number`. The second `Case` statement contains the value that matches the current value of `number`, so the statement that writes "Between 6 and 8, inclusive" runs.  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [End 语句](../../../visual-basic/language-reference/statements/end-statement.md)
- [If...Then...Else 语句](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Option Compare 语句](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Exit 语句](../../../visual-basic/language-reference/statements/exit-statement.md)
