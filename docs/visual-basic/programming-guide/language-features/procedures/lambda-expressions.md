---
title: Lambda 表达式
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: f3f963167e1b3633cc5fe6e1f435e374cd272cce
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345973"
---
# <a name="lambda-expressions-visual-basic"></a>Lambda 表达式 (Visual Basic)

A *lambda expression* is a function or subroutine without a name that can be used wherever a delegate is valid. Lambda expressions can be functions or subroutines and can be single-line or multi-line. You can pass values from the current scope to a lambda expression.

> [!NOTE]
> The `RemoveHandler` statement is an exception. You cannot pass a lambda expression in for the delegate parameter of `RemoveHandler`.

You create lambda expressions by using the `Function` or `Sub` keyword, just as you create a standard function or subroutine. However, lambda expressions are included in a statement.

The following example is a lambda expression that increments its argument and returns the value. The example shows both the single-line and multi-line lambda expression syntax for a function.

[!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]

The following example is a lambda expression that writes a value to the console. The example shows both the single-line and multi-line lambda expression syntax for a subroutine.

[!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]

Notice that in the previous examples the lambda expressions are assigned to a variable name. Whenever you refer to the variable, you invoke the lambda expression. You can also declare and invoke a lambda expression at the same time, as shown in the following example.

[!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]

A lambda expression can be returned as the value of a function call (as is shown in the example in the [Context](#context) section later in this topic), or passed in as an argument to a parameter that takes a delegate type, as shown in the following example.

[!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]

## <a name="lambda-expression-syntax"></a>Lambda 表达式语法

The syntax of a lambda expression resembles that of a standard function or subroutine. The differences are as follows:

- A lambda expression does not have a name.

- Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.

- Single-line lambda functions do not use an `As` clause to designate the return type. Instead, the type is inferred from the value that the body of the lambda expression evaluates to. For example, if the body of the lambda expression is `cust.City = "London"`, its return type is `Boolean`.

- In multi-line lambda functions, you can either specify a return type by using an `As` clause, or omit the `As` clause so that the return type is inferred. When the `As` clause is omitted for a multi-line lambda function, the return type is inferred to be the dominant type from all the `Return` statements in the multi-line lambda function. The *dominant type* is a unique type that all other types can widen to. If this unique type cannot be determined, the dominant type is the unique type that all other types in the array can narrow to. 如果无法确定为这两种唯一类型之一，则基准类型是 `Object`。 In this case, if `Option Strict` is set to `On`, a compiler error occurs.

     For example, if the expressions supplied to the `Return` statement contain values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`. Both `Integer` and `Long` widen to `Double` and only `Double`. 因此， `Double` 是基准类型。 有关详细信息，请参阅 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。

- The body of a single-line function must be an expression that returns a value, not a statement. There is no `Return` statement for single-line functions. The value returned by the single-line function is the value of the expression in the body of the function.

- The body of a single-line subroutine must be single-line statement.

- Single-line functions and subroutines do not include an `End Function` or `End Sub` statement.

- You can specify the data type of a lambda expression parameter by using the `As` keyword, or the data type of the parameter can be inferred. Either all parameters must have specified data types or all must be inferred.

- `Optional` and `Paramarray` parameters are not permitted.

- Generic parameters are not permitted.

## <a name="async-lambdas"></a>异步 lambda

You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [Async](../../../../visual-basic/language-reference/modifiers/async.md) and [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) keywords. 例如，下面的 Windows 窗体示例包含一个调用和等待异步方法 `ExampleMethodAsync`的事件处理程序。

```vb
Public Class Form1

    Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
        ' ExampleMethodAsync returns a Task.
        Await ExampleMethodAsync()
        TextBox1.Text = vbCrLf & "Control returned to button1_Click."
    End Sub

    Async Function ExampleMethodAsync() As Task
        ' The following line simulates a task-returning asynchronous process.
        Await Task.Delay(1000)
    End Function

End Class
```

You can add the same event handler by using an async lambda in an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md). 若要添加此处理程序，请在 lambda 参数列表前添加一个 `Async` 修饰符，如下例所示。

```vb
Public Class Form1

    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AddHandler Button1.Click,
            Async Sub(sender1, e1)
                ' ExampleMethodAsync returns a Task.
                Await ExampleMethodAsync()
                TextBox1.Text = vbCrLf & "Control returned to Button1_ Click."
            End Sub
    End Sub

    Async Function ExampleMethodAsync() As Task
        ' The following line simulates a task-returning asynchronous process.
        Await Task.Delay(1000)
    End Function

End Class
```

For more information about how to create and use async methods, see [Asynchronous Programming with Async and Await](../../../../visual-basic/programming-guide/concepts/async/index.md).

## <a name="context"></a>上下文

A lambda expression shares its context with the scope within which it is defined. It has the same access rights as any code written in the containing scope. This includes access to member variables, functions and subs, `Me`, and parameters and local variables in the containing scope.

Access to local variables and parameters in the containing scope can extend beyond the lifetime of that scope. As long as a delegate referring to a lambda expression is not available to garbage collection, access to the variables in the original environment is retained. In the following example, variable `target` is local to `makeTheGame`, the method in which the lambda expression `playTheGame` is defined. Note that the returned lambda expression, assigned to `takeAGuess` in `Main`, still has access to the local variable `target`.

[!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]

The following example demonstrates the wide range of access rights of the nested lambda expression. When the returned lambda expression is executed from `Main` as `aDel`, it accesses these elements:

- A field of the class in which it is defined: `aField`

- A property of the class in which it is defined: `aProp`

- A parameter of method `functionWithNestedLambda`, in which it is defined: `level1`

- A local variable of `functionWithNestedLambda`: `localVar`

- A parameter of the lambda expression in which it is nested: `level2`

 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]

## <a name="converting-to-a-delegate-type"></a>Converting to a Delegate Type

A lambda expression can be implicitly converted to a compatible delegate type. For information about the general requirements for compatibility, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md). For example, the following code example shows a lambda expression that implicitly converts to `Func(Of Integer, Boolean)` or a matching delegate signature.

[!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]

The following code example shows a lambda expression that implicitly converts to `Sub(Of Double, String, Double)` or a matching delegate signature.

[!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]

When you assign lambda expressions to delegates or pass them as arguments to procedures, you can specify the parameter names but omit their data types, letting the types be taken from the delegate.

## <a name="examples"></a>示例

- The following example defines a lambda expression that returns `True` if the nullable argument has an assigned value, and `False` if its value is `Nothing`.

     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]

- The following example defines a lambda expression that returns the index of the last element in an array.

     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]

## <a name="see-also"></a>请参阅

- [过程](./index.md)
- [Visual Basic 中的 LINQ 简介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [委托](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Function 语句](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub 语句](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [可以为 null 的值类型](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [如何：在 Visual Basic 中将过程传递给另一过程](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [如何：创建 lambda 表达式](./how-to-create-a-lambda-expression.md)
- [宽松委托转换](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
