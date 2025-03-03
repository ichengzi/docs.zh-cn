---
title: 异步返回类型
ms.date: 07/20/2015
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
ms.openlocfilehash: 96d3a945a49a12f7c2d5d60e8ee59ce047a0bae6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347981"
---
# <a name="async-return-types-visual-basic"></a>Async Return Types (Visual Basic)

异步方法具有三个可能的返回类型：<xref:System.Threading.Tasks.Task%601>、<xref:System.Threading.Tasks.Task>和 void。 在 Visual Basic 中，void 返回类型被写为 [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) 过程。 For more information about async methods, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).

在以下其中一节检查每个返回类型，且在本主题末尾可以找到使用全部三种类型的完整示例。

> [!NOTE]
> 若要运行该示例，计算机上必须安装 Visual Studio 2012 或更高版本和 .NET Framework 4.5 或更高版本。

## <a name="BKMK_TaskTReturnType"></a>Task(T) 返回类型

The <xref:System.Threading.Tasks.Task%601> return type is used for an async method that contains a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement in which the operand has type `TResult`.

在下面的示例中，`TaskOfT_MethodAsync` 异步方法包含返回整数的 return 语句。 因此，该方法声明必须指定 `Task(Of Integer)` 的返回类型。

```vb
' TASK(OF T) EXAMPLE
Async Function TaskOfT_MethodAsync() As Task(Of Integer)

    ' The body of an async method is expected to contain an awaited
    ' asynchronous call.
    ' Task.FromResult is a placeholder for actual work that returns a string.
    Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())

    ' The method then can process the result in some way.
    Dim leisureHours As Integer
    If today.First() = "S" Then
        leisureHours = 16
    Else
        leisureHours = 5
    End If

    ' Because the return statement specifies an operand of type Integer, the
    ' method must have a return type of Task(Of Integer).
    Return leisureHours
End Function
```

当 `TaskOfT_MethodAsync` 从 await 表达式中调用时，await 表达式将检索存储在由 `TaskOfT_MethodAsync` 返回的任务中的整数值（`leisureHours` 的值）。 For more information about await expressions, see [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md).

以下代码调用和等待方法 `TaskOfT_MethodAsync`。 此结果分配给 `result1` 变量。

```vb
' Call and await the Task(Of T)-returning async method in the same statement.
Dim result1 As Integer = Await TaskOfT_MethodAsync()
```

通过从应用程序 `Await` 中分离对 `TaskOfT_MethodAsync` 的调用，你可以更好地了解此操作，如下面的代码所示。 对非立即等待的方法 `TaskOfT_MethodAsync` 的调用返回 `Task(Of Integer)`，正如你从方法声明预料的一样。 该任务指派给示例中的 `integerTask` 变量。 因为 `integerTask` 是 <xref:System.Threading.Tasks.Task%601>，所以它包含类型 `TResult` 的 <xref:System.Threading.Tasks.Task%601.Result> 属性。 在这种情况下，TResult 表示整数类型。 `Await` 应用于 `integerTask`，await 表达式的计算结果为 `integerTask` 的 <xref:System.Threading.Tasks.Task%601.Result%2A> 属性内容。 此值分配给 `result2` 变量。

> [!WARNING]
> <xref:System.Threading.Tasks.Task%601.Result%2A> 属性为阻止属性。 如果你在其任务完成之前尝试访问它，当前处于活动状态的线程将被阻止，直到任务完成且值为可用。 在大多数情况下，应通过使用 `Await` 访问此值，而不是直接访问属性。

```vb
' Call and await in separate statements.
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()

' You can do other work that does not rely on resultTask before awaiting.
textBox1.Text &= "Application can continue working while the Task(Of T) runs. . . . " & vbCrLf

Dim result2 As Integer = Await integerTask
```

以下代码中的显示语句验证 `result1` 变量、`result2` 变量与 `Result` 属性的值是否相同。 请记住，`Result` 属性是锁定属性，在其任务完成之前不应访问。

```vb
' Display the values of the result1 variable, the result2 variable, and
' the resultTask.Result property.
textBox1.Text &= vbCrLf & $"Value of result1 variable:   {result1}" & vbCrLf
textBox1.Text &= $"Value of result2 variable:   {result2}" & vbCrLf
textBox1.Text &= $"Value of resultTask.Result:  {integerTask.Result}" & vbCrLf
```

## <a name="BKMK_TaskReturnType"></a>任务返回类型

不包含 return 语句或包含不返回操作数的 return 语句的异步方法通常具有返回类型 <xref:System.Threading.Tasks.Task>。 Such methods would be [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedures if they were written to run synchronously. 如果在异步方法中使用 `Task` 返回类型，调用方法可以使用 `Await` 运算符暂停调用方的完成，直至被调用的异步方法结束。

在下面的示例中，异步方法 `Task_MethodAsync` 不包含 return 语句。 因此，为此方法指定 `Task` 返回类型，这将启用 `Task_MethodAsync` 为等待。 `Task` 类型的定义不包括存储返回值的 `Result` 属性。

```vb
' TASK EXAMPLE
Async Function Task_MethodAsync() As Task

    ' The body of an async method is expected to contain an awaited
    ' asynchronous call.
    ' Task.Delay is a placeholder for actual work.
    Await Task.Delay(2000)
    textBox1.Text &= vbCrLf & "Sorry for the delay. . . ." & vbCrLf

    ' This method has no return statement, so its return type is Task.
End Function
```

通过使用 await 语句而不是 await 表达式来调用和等待 `Task_MethodAsync`，类似于异步 `Sub` 或返回返回 void 的方法的调用语句。 The application of an `Await` operator in this case doesn't produce a value.

以下代码调用和等待方法 `Task_MethodAsync`。

```vb
' Call and await the Task-returning async method in the same statement.
Await Task_MethodAsync()
```

As in the previous <xref:System.Threading.Tasks.Task%601> example, you can separate the call to `Task_MethodAsync` from the application of an `Await` operator, as the following code shows. 但是，请记住，`Task` 没有 `Result` 属性，并且当 await 运算符应用于 `Task` 时不产生值。

以下代码从等待 `Task_MethodAsync` 返回的任务中分离调用 `Task_MethodAsync`。

```vb
' Call and await in separate statements.
Dim simpleTask As Task = Task_MethodAsync()

' You can do other work that does not rely on simpleTask before awaiting.
textBox1.Text &= vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf

Await simpleTask
```

## <a name="BKMK_VoidReturnType"></a>返回类型为 void

The primary use of `Sub` procedures is in event handlers, where there is no return type (referred to as a void return type in other languages). Void 返回还可用于替代返回 void 的方法，或者用于执行可分类为"发后不理"活动的方法。 但是，你应尽可能地返回 `Task`，因为不能等待返回 void 的异步方法。 这种方法的任何调用方必须能够继续完成，而无需等待调用的异步方法完成，并且调用方必须独立于异步方法生成的任何值或异常。

返回 void 的异步方法的调用方无法捕获从该方法引发的异常，且此类未经处理的异常可能会导致应用程序故障。 如果返回 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 的异步方法中出现异常，此异常将存储于返回的任务中，并在等待该任务时再次引发。 因此，请确保可以产生异常的任何异步方法都具有返回类型 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601>，并确保会等待对方法的调用。

若要详细了解如何在异步方法中捕获异常，请参阅 [Try...Catch...Finally 语句](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。

下面的代码定义了异步事件处理程序。

```vb
' SUB EXAMPLE
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click

    textBox1.Clear()

    ' Start the process and await its completion. DriverAsync is a
    ' Task-returning async method.
    Await DriverAsync()

    ' Say goodbye.
    textBox1.Text &= vbCrLf & "All done, exiting button-click event handler."
End Sub
```

## <a name="BKMK_Example"></a>完整示例

以下 Windows Presentation Foundation (WPF) 项目包含本主题中的代码示例。

 若要运行项目，请执行下列步骤：

1. 启动 Visual Studio。

2. 在菜单栏上，依次选择 **“文件”** 、 **“新建”** 、 **“项目”** 。

     **“新建项目”** 对话框随即打开。

3. In the **Installed**, **Templates** category, choose **Visual Basic**, and then choose **Windows**. 从项目类型列表中，选择“WPF 应用程序”。

4. 输入 `AsyncReturnTypes` 作为项目名称，然后选择“确定”按钮。

     新项目将出现在“解决方案资源管理器”中。

5. 在 Visual Studio 代码编辑器中，选择 **“MainWindow.xaml”** 选项卡。

     如果此选项卡不可见，则在“解决方案资源管理器”中，打开 MainWindow.xaml 的快捷菜单，然后选择“打开”。

6. 在 MainWindow.xaml 的“XAML”窗口中，将代码替换为下面的代码。

    ```vb
    <Window x:Class="MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            Title="MainWindow" Height="350" Width="525">
        <Grid>
            <Button x:Name="button1" Content="Start" HorizontalAlignment="Left" Margin="214,28,0,0" VerticalAlignment="Top" Width="75" HorizontalContentAlignment="Center" FontWeight="Bold" FontFamily="Aharoni" Click="button1_Click"/>
            <TextBox x:Name="textBox1" Margin="0,80,0,0" TextWrapping="Wrap" FontFamily="Lucida Console"/>

        </Grid>
    </Window>
    ```

     MainWindow.xaml 的“设计”视图中将显示一个简单的窗口，其中包含一个文本框和一个按钮。

7. In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.

8. 将 MainWindow.xaml.vb 中的代码替换为以下代码。

    ```vb
    Class MainWindow

        ' SUB EXAMPLE
        Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click

            textBox1.Clear()

            ' Start the process and await its completion. DriverAsync is a
            ' Task-returning async method.
            Await DriverAsync()

            ' Say goodbye.
            textBox1.Text &= vbCrLf & "All done, exiting button-click event handler."
        End Sub

        Async Function DriverAsync() As Task

            ' Task(Of T)
            ' Call and await the Task(Of T)-returning async method in the same statement.
            Dim result1 As Integer = Await TaskOfT_MethodAsync()

            ' Call and await in separate statements.
            Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()

            ' You can do other work that does not rely on resultTask before awaiting.
            textBox1.Text &= "Application can continue working while the Task(Of T) runs. . . . " & vbCrLf

            Dim result2 As Integer = Await integerTask

            ' Display the values of the result1 variable, the result2 variable, and
            ' the resultTask.Result property.
            textBox1.Text &= vbCrLf & $"Value of result1 variable:   {result1}" & vbCrLf
            textBox1.Text &= $"Value of result2 variable:   {result2}" & vbCrLf
            textBox1.Text &= $"Value of resultTask.Result:  {integerTask.Result}" & vbCrLf

            ' Task
            ' Call and await the Task-returning async method in the same statement.
            Await Task_MethodAsync()

            ' Call and await in separate statements.
            Dim simpleTask As Task = Task_MethodAsync()

            ' You can do other work that does not rely on simpleTask before awaiting.
            textBox1.Text &= vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf

            Await simpleTask
        End Function

        ' TASK(OF T) EXAMPLE
        Async Function TaskOfT_MethodAsync() As Task(Of Integer)

            ' The body of an async method is expected to contain an awaited
            ' asynchronous call.
            ' Task.FromResult is a placeholder for actual work that returns a string.
            Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())

            ' The method then can process the result in some way.
            Dim leisureHours As Integer
            If today.First() = "S" Then
                leisureHours = 16
            Else
                leisureHours = 5
            End If

            ' Because the return statement specifies an operand of type Integer, the
            ' method must have a return type of Task(Of Integer).
            Return leisureHours
        End Function

        ' TASK EXAMPLE
        Async Function Task_MethodAsync() As Task

            ' The body of an async method is expected to contain an awaited
            ' asynchronous call.
            ' Task.Delay is a placeholder for actual work.
            Await Task.Delay(2000)
            textBox1.Text &= vbCrLf & "Sorry for the delay. . . ." & vbCrLf

            ' This method has no return statement, so its return type is Task.
        End Function

    End Class
    ```

9. 按 F5 键以运行程序，然后选择 **“启动”** 按钮。

     The following output should appear:

    ```console
    Application can continue working while the Task<T> runs. . . .

    Value of result1 variable:   5
    Value of result2 variable:   5
    Value of integerTask.Result: 5

    Sorry for the delay. . . .

    Application can continue working while the Task runs. . . .

    Sorry for the delay. . . .

    All done, exiting button-click event handler.
    ```

## <a name="see-also"></a>请参阅

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [演练：使用 Async 和 Await 访问 Web (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [异步程序中的控制流 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
- [Async](../../../../visual-basic/language-reference/modifiers/async.md)
- [Await 运算符](../../../../visual-basic/language-reference/operators/await-operator.md)
