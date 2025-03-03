---
title: Async
ms.date: 07/20/2015
f1_keywords:
- vb.Async
helpviewer_keywords:
- Async [Visual Basic]
- Async keyword [Visual Basic]
ms.assetid: 1be8b4b5-9689-41b5-bd33-b906bfd53bc5
ms.openlocfilehash: 73d433c66750ead3a97b1c283cc26b4c43f078df
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351631"
---
# <a name="async-visual-basic"></a>Async (Visual Basic)

The `Async` modifier indicates that the method or [lambda expression](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) that it modifies is asynchronous. Such methods are referred to as *async methods*.

异步方法提供了一种简便方式来完成可能需要长时间运行的工作，而不必阻止调用方的线程。 The caller of an async method can resume its work without waiting for the async method to finish.

> [!NOTE]
> `Async` 和 `Await` 关键字是在 Visual Studio 2012 中引入的。 For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md).

下面的示例显示一个异步方法的结构。 按照约定，异步方法名的结尾为“Async”。

```vb
Public Async Function ExampleMethodAsync() As Task(Of Integer)
    ' . . .

    ' At the Await expression, execution in this method is suspended and,
    ' if AwaitedProcessAsync has not already finished, control returns
    ' to the caller of ExampleMethodAsync. When the awaited task is
    ' completed, this method resumes execution.
    Dim exampleInt As Integer = Await AwaitedProcessAsync()

    ' . . .

    ' The return statement completes the task. Any method that is
    ' awaiting ExampleMethodAsync can now get the integer result.
    Return exampleInt
End Function
```

Typically, a method modified by the `Async` keyword contains at least one [Await](../../../visual-basic/language-reference/modifiers/async.md) expression or statement. 方法同步运行，直至到达第一个 `Await`，此时暂停，直到等待的任务完成。 同时，控制权返回给方法的调用方。 If the method doesn't contain an `Await` expression or statement, the method isn't suspended and executes as a synchronous method does. A compiler warning alerts you to any async methods that don't contain `Await` because that situation might indicate an error. For more information, see the [compiler error](../error-messages/bc42358.md).

`Async` 关键字是一个非保留的关键字。 在修饰方法或 lambda 表达式时，它是关键字。 在所有其他上下文中，都会将其解释为标识符。

## <a name="return-types"></a>返回类型

An async method is either a [Sub](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedure, or a [Function](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) procedure that has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>. The method cannot declare any [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parameters.

You specify `Task(Of TResult)` for the return type of an async method if the [Return](../../../visual-basic/language-reference/statements/return-statement.md) statement of the method has an operand of type TResult. 如果当方法完成时未返回有意义的值，则应使用 `Task`。 即对方法的调用返回 `Task`，但 `Task` 完成时，等待 `Await` 的任何 `Task` 语句不会产生结果值。

异步子例程主要用于定义需要 `Sub` 程序的事件处理程序。 异步子程序的调用方不能等待它，并且无法捕获该方法引发的异常。

有关详细信息和示例，请参阅[异步返回类型](../../../visual-basic/programming-guide/concepts/async/async-return-types.md)。

## <a name="example"></a>示例

下面的示例显示一个异步事件处理程序、一个异步 lambda 表达式和一个异步方法。 For a full example that uses these elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). 可从[开发人员代码示例](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)下载演练代码。

```vb
' An event handler must be a Sub procedure.
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click
    textBox1.Clear()
    ' SumPageSizesAsync is a method that returns a Task.
    Await SumPageSizesAsync()
    textBox1.Text = vbCrLf & "Control returned to button1_Click."
End Sub

' The following async lambda expression creates an equivalent anonymous
' event handler.
AddHandler button1.Click, Async Sub(sender, e)
                              textBox1.Clear()
                              ' SumPageSizesAsync is a method that returns a Task.
                              Await SumPageSizesAsync()
                              textBox1.Text = vbCrLf & "Control returned to button1_Click."
                          End Sub

' The following async method returns a Task(Of T).
' A typical call awaits the Byte array result:
'      Dim result As Byte() = Await GetURLContents("https://msdn.com")
Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())

    ' The downloaded resource ends up in the variable named content.
    Dim content = New MemoryStream()

    ' Initialize an HttpWebRequest for the current URL.
    Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

    ' Send the request to the Internet resource and wait for
    ' the response.
    Using response As WebResponse = Await webReq.GetResponseAsync()
        ' Get the data stream that is associated with the specified URL.
        Using responseStream As Stream = response.GetResponseStream()
            ' Read the bytes in responseStream and copy them to content.
            ' CopyToAsync returns a Task, not a Task<T>.
            Await responseStream.CopyToAsync(content)
        End Using
    End Using

    ' Return the result as a byte array.
    Return content.ToArray()
End Function
```

## <a name="see-also"></a>请参阅

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [Await 运算符](../../../visual-basic/language-reference/operators/await-operator.md)
- [使用 Async 和 Await 的异步编程](../../../visual-basic/programming-guide/concepts/async/index.md)
- [演练：使用 Async 和 Await 访问 Web](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
