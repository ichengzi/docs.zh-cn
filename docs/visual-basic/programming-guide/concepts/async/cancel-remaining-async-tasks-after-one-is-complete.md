---
title: 在完成一个异步任务后取消剩余任务
ms.date: 07/20/2015
ms.assetid: c928b5a1-622f-4441-8baf-adca1dde197f
ms.openlocfilehash: e6747f35e665611ac7a48a87f955c8b893ee2b99
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347925"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-visual-basic"></a>Cancel Remaining Async Tasks after One Is Complete (Visual Basic)

通过结合使用 <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> 方法和 <xref:System.Threading.CancellationToken>，可在一个任务完成时取消所有剩余任务。 `WhenAny` 方法采用任务集合中的一个参数。 该方法启动所有任务，并返回单个任务。 当集合中任意任务完成时，完成单个任务。

此示例演示如何结合使用取消标记与 `WhenAny` 保留任务集合中第一个要完成的任务，并取消剩余任务。 每个任务都下载网站内容。 本示例显示第一个完成的下载的内容长度，并取消其他下载。

> [!NOTE]
> 若要运行该示例，计算机上必须安装有 Visual Studio 2012 或更高版本和 .NET Framework 4.5 或更高版本。

## <a name="downloading-the-example"></a>下载示例

若要下载完整的 Windows Presentation Foundation (WPF) 项目，请参阅 [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)（异步示例：微调应用程序），然后遵循以下步骤。

1. 解压缩下载的文件，然后启动 Visual Studio。

2. 在菜单栏上，依次选择 **“文件”** 、 **“打开”** 和 **“项目/解决方案”** 。

3. 在“打开项目”对话框中，打开保存已解压的示例代码的文件夹，然后打开 AsyncFineTuningVB 的解决方案 (.sln) 文件。

4. 在“解决方案资源管理器”中，打开“CancelAfterOneTask”项目的快捷菜单，然后选择“设为启动项目”。

5. 选择 F5 键运行该项目。

    选择 Ctrl+F5 键运行该项目，而不进行调试。

6. 运行程序若干次，以验证首先完成的下载是不同的。

如果不想下载项目，可在本主题末尾处查看 MainWindow.xaml.vb 文件。

## <a name="building-the-example"></a>生成示例

The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks. 该示例使用相同的 UI，但未显示使用“取消”按钮。

若要自行生成示例，请按“下载示例”部分的说明逐步操作，选择“CancelAListOfTasks”作为“启动项目”。 将此主题中的更改添加到该项目。

In the MainWindow.xaml.vb file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.

```vb
' ***Bundle the processing steps for a website into one async method.
Async Function ProcessURLAsync(url As String, client As HttpClient, ct As CancellationToken) As Task(Of Integer)

    ' GetAsync returns a Task(Of HttpResponseMessage).
    Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

    ' Retrieve the website contents from the HttpResponseMessage.
    Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

    Return urlContents.Length
End Function
```

在 `AccessTheWebAsync` 中，此示例使用查询、<xref:System.Linq.Enumerable.ToArray%2A> 方法和 `WhenAny` 方法创建并启动任务数组。 将 `WhenAny` 应用到数组将返回单个任务，该任务在等待时对任务数组中首先完成的任务进行评估。

在 `AccessTheWebAsync` 中，进行下列更改。 星号标记了代码文件中的更改。

1. 注释禁止或删除循环。

2. 创建一个查询，它在执行时将生成常规任务的集合。 每次调用 `ProcessURLAsync` 均在 `TResult` 为整数时返回 <xref:System.Threading.Tasks.Task%601>。

    ```vb
    ' ***Create a query that, when executed, returns a collection of tasks.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url, client, ct)
    ```

3. 通过调用 `ToArray` 来执行查询并启动任务。 下一步中应用 `WhenAny` 方法将在不使用 `ToArray` 的情况下执行查询并启动任务，但其他方法可能无法执行此操作。 最安全的做法是显式强制执行查询。

    ```vb
    ' ***Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. 在任务集合上调用 `WhenAny`。 `WhenAny` 返回 `Task(Of Task(Of Integer))` 或 `Task<Task<int>>`。  也就是说，在等待时 `WhenAny` 将返回一个任务，它将评估单个的 `Task(Of Integer)` 或 `Task<int>`。 该单个任务是集合中首先完成的任务。 首先完成的任务被分配给 `firstFinishedTask`。 `firstFinishedTask` 的类型为 <xref:System.Threading.Tasks.Task%601>，其中 `TResult` 是整数，这是因为它是 `ProcessURLAsync` 的返回类型。

    ```vb
    ' ***Call WhenAny and then await the result. The task that finishes
    ' first is assigned to firstFinishedTask.
    Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)
    ```

5. 在此示例中，你只对首先完成的任务感兴趣。 因此，使用 <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> 取消剩余任务。

    ```vb
    ' ***Cancel the rest of the downloads. You just want the first one.
    cts.Cancel()
    ```

6. 最后，等待 `firstFinishedTask` 检索下载内容的长度。

    ```vb
    Dim length = Await firstFinishedTask
    resultsTextBox.Text &= vbCrLf & $"Length of the downloaded website:  {length}" & vbCrLf
    ```

运行程序若干次，以验证首先完成的下载是不同的。

## <a name="complete-example"></a>完整的示例

The following code is the complete MainWindow.xaml.vb or MainWindow.xaml.cs file for the example. 对添加到此示例的元素进行了星号标记。

请注意，必须为 <xref:System.Net.Http> 添加引用。

可以从 [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)（异步示例：微调应用程序）下载这些项目。

```vb
' Add an Imports directive and a reference for System.Net.Http.
Imports System.Net.Http

' Add the following Imports directive for System.Threading.
Imports System.Threading

Class MainWindow

    ' Declare a System.Threading.CancellationTokenSource.
    Dim cts As CancellationTokenSource

    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)

        ' Instantiate the CancellationTokenSource.
        cts = New CancellationTokenSource()

        resultsTextBox.Clear()

        Try
            Await AccessTheWebAsync(cts.Token)
            resultsTextBox.Text &= vbCrLf & "Download complete."

        Catch ex As OperationCanceledException
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf

        Catch ex As Exception
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf
        End Try

        ' Set the CancellationTokenSource to Nothing when the download is complete.
        cts = Nothing
    End Sub

    ' You can still include a Cancel button if you want to.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub

    ' Provide a parameter for the CancellationToken.
    ' Change the return type to Task because the method has no return statement.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task

        Dim client As HttpClient = New HttpClient()

        ' Call SetUpURLList to make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        '' Comment out or delete the loop.
        ''For Each url In urlList
        ''    ' GetAsync returns a Task(Of HttpResponseMessage).
        ''    ' Argument ct carries the message if the Cancel button is chosen.
        ''    ' Note that the Cancel button can cancel all remaining downloads.
        ''    Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

        ''    ' Retrieve the website contents from the HttpResponseMessage.
        ''    Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        ''    resultsTextBox.Text &=
        ''        vbCrLf & $"Length of the downloaded string: {urlContents.Length}." & vbCrLf
        ''Next

        ' ***Create a query that, when executed, returns a collection of tasks.
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
            From url In urlList Select ProcessURLAsync(url, client, ct)

        ' ***Use ToArray to execute the query and start the download tasks.
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()

        ' ***Call WhenAny and then await the result. The task that finishes
        ' first is assigned to firstFinishedTask.
        Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)

        ' ***Cancel the rest of the downloads. You just want the first one.
        cts.Cancel()

        ' ***Await the first completed task and display the results
        ' Run the program several times to demonstrate that different
        ' websites can finish first.
        Dim length = Await firstFinishedTask
        resultsTextBox.Text &= vbCrLf & $"Length of the downloaded website:  {length}" & vbCrLf
    End Function

    ' ***Bundle the processing steps for a website into one async method.
    Async Function ProcessURLAsync(url As String, client As HttpClient, ct As CancellationToken) As Task(Of Integer)

        ' GetAsync returns a Task(Of HttpResponseMessage).
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

        ' Retrieve the website contents from the HttpResponseMessage.
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        Return urlContents.Length
    End Function

    ' Add a method that creates a list of web addresses.
    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

End Class

' Sample output:

' Length of the downloaded website:  158856

' Download complete.
```

## <a name="see-also"></a>请参阅

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [微调异步应用程序 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [使用 Async 和 Await 的异步编程 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [异步示例：微调应用程序](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
