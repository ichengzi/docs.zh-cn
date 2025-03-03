---
title: 演练：在 WPF 应用程序中缓存应用程序数据
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthroughs [WPF], caching
- caching [.NET Framework]
- caching [WPF]
ms.assetid: dac2c9ce-042b-4d23-91eb-28f584415cef
ms.openlocfilehash: f0082bd99b154f87ab90bee7a89afdb8405f6623
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920320"
---
# <a name="walkthrough-caching-application-data-in-a-wpf-application"></a>演练：在 WPF 应用程序中缓存应用程序数据
缓存可以将数据存储在内存中以便快速访问。 再次访问数据时，应用程序可以从缓存获取数据，而不是从原始源检索数据。 这可改善性能和可伸缩性。 此外，数据源暂时不可用时，缓存可提供数据。

 .NET Framework 提供使你能够在 .NET Framework 应用程序中使用缓存的类。 这些类位于 <xref:System.Runtime.Caching> 命名空间中。

> [!NOTE]
> <xref:System.Runtime.Caching> 命名空间是 .NET Framework 4 中的新命名空间。 此命名空间使缓存可供所有 .NET Framework 应用程序使用。 在以前版本的 .NET Framework 中，只能在 <xref:System.Web> 命名空间中使用缓存，因此需要依赖 ASP.NET 类。

 本演练演示如何使用 .NET Framework 中提供的缓存功能作为 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 应用程序的一部分。 在本演练中，您将缓存文本文件的内容。

 本演练演示以下任务：

- 创建 WPF 应用程序项目。

- 添加对 .NET Framework 4 的引用。

- 初始化缓存。

- 添加包含文本文件内容的缓存项。

- 为缓存条目提供逐出策略。

- 监视缓存文件的路径，并通知缓存实例对被监视项的更改。

## <a name="prerequisites"></a>Prerequisites
 若要完成本演练，你将需要：

- Visual Studio 2010。

- 包含少量文本的文本文件。 （将在消息框中显示文本文件的内容。）本演练中所示的代码假设您正在使用以下文件：

     `c:\cache\cacheText.txt`

     但是，您可以使用任何文本文件并对此演练中的代码进行较小的更改。

## <a name="creating-a-wpf-application-project"></a>创建 WPF 应用程序项目
 首先创建一个 WPF 应用程序项目。

#### <a name="to-create-a-wpf-application"></a>创建 WPF 应用程序

1. 启动 Visual Studio。

2. 在 "**文件**" 菜单中，单击 "**新建**"，然后单击 "**新建项目**"。

     随即显示“新建项目”对话框。

3. 在 "**已安装的模板**" 下，选择要使用的编程语言（**Visual Basic**或**视觉对象C#** ）。

4. 在 "**新建项目**" 对话框中，选择 " **WPF 应用程序**"。

    > [!NOTE]
    > 如果看不到 " **Wpf 应用程序**" 模板，请确保以支持 WPF 的 .NET Framework 的版本为目标。 在 "**新建项目**" 对话框中，从列表中选择 ".NET Framework 4"。

5. 在 "**名称**" 文本框中，输入项目的名称。 例如，可以输入**WPFCaching**。

6. 选择“为解决方案创建目录”复选框。

7. 单击“确定”。

     WPF 设计器将在 "**设计**" 视图中打开并显示 mainwindow.xaml 文件。 Visual Studio 将创建 "**我的项目**" 文件夹、应用程序 .xaml 文件和 mainwindow.xaml 文件。

## <a name="targeting-the-net-framework-and-adding-a-reference-to-the-caching-assemblies"></a>针对 .NET Framework 并添加对缓存程序集的引用
 默认情况下，WPF 应用程序以 [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]为目标。 若要在 WPF 应用程序中使用 <xref:System.Runtime.Caching> 命名空间，应用程序必须以 .NET Framework 4 （而不是 [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]）为目标，并且必须包括对命名空间的引用。

 因此，下一步是更改 .NET Framework 目标并添加对 <xref:System.Runtime.Caching> 命名空间的引用。

> [!NOTE]
> Visual Basic 项目和可视化C#项目中更改 .NET Framework 目标的过程有所不同。

#### <a name="to-change-the-target-net-framework-in-visual-basic"></a>更改目标 .NET Framework Visual Basic

1. 在 "**解决方案资源管理器**" 中，右键单击项目名称，然后单击 "**属性**"。

     将显示应用程序的 "属性" 窗口。

2. 单击“编译”选项卡。

3. 在窗口底部，单击 "**高级编译选项 ...** "。

     将显示 "**高级编译器设置**" 对话框。

4. 在 "**目标框架（所有配置）** " 列表中，选择 ".NET Framework 4"。 （请勿选择 [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]。）

5. 单击“确定”。

     随即显示“目标框架更改”对话框。

6. 在 "**目标框架更改**" 对话框中，单击 **"是"** 。

     项目已关闭，然后重新打开。

7. 按照以下步骤添加对缓存程序集的引用：

    1. 在**解决方案资源管理器**中，右键单击项目名称，然后单击 "**添加引用**"。

    2. 选择 " **.net** " 选项卡，选择 "`System.Runtime.Caching`"，然后单击 **"确定"** 。

#### <a name="to-change-the-target-net-framework-in-a-visual-c-project"></a>更改可视化C#项目中的目标 .NET Framework

1. 在**解决方案资源管理器**中，右键单击项目名称，然后单击 "**属性**"。

     将显示应用程序的 "属性" 窗口。

2. 单击“应用程序” 选项卡。

3. 在 "**目标框架**" 列表中，选择 ".NET Framework 4"。 （请勿选择 **.NET Framework 4 客户端配置文件**。）

4. 按照以下步骤添加对缓存程序集的引用：

    1. 右键单击 "**引用**" 文件夹，然后单击 "**添加引用**"。

    2. 选择 " **.net** " 选项卡，选择 "`System.Runtime.Caching`"，然后单击 **"确定"** 。

## <a name="adding-a-button-to-the-wpf-window"></a>将按钮添加到 WPF 窗口
 接下来，您将添加一个按钮控件，并为按钮的 `Click` 事件创建事件处理程序。 稍后你将向添加代码，以便在单击按钮时，将缓存并显示文本文件的内容。

#### <a name="to-add-a-button-control"></a>添加按钮控件

1. 在**解决方案资源管理器**中，双击 mainwindow.xaml 文件以将其打开。

2. 从 "**工具箱**" 的 "**常用 WPF 控件**" 下，将 "`Button`" 控件拖动到 "`MainWindow`" 窗口。

3. 在 "**属性**" 窗口中，将 `Button` 控件的 `Content` 属性设置为 "**获取缓存**"。

## <a name="initializing-the-cache-and-caching-an-entry"></a>初始化缓存并缓存项
 接下来，你将添加代码来执行以下任务：

- 创建缓存类的实例，即，将实例化新的 <xref:System.Runtime.Caching.MemoryCache> 对象。

- 指定缓存使用 <xref:System.Runtime.Caching.HostFileChangeMonitor> 对象来监视文本文件中的更改。

- 读取文本文件并将其内容缓存为缓存条目。

- 显示缓存的文本文件的内容。

#### <a name="to-create-the-cache-object"></a>创建缓存对象

1. 双击刚才添加的按钮，以便在 MainWindow.xaml.cs 或 Mainwindow.xaml 文件中创建事件处理程序。

2. 在文件顶部（类声明之前），添加以下 `Imports` （Visual Basic）或 `using` （C#）语句：

    ```csharp
    using System.Runtime.Caching;
    using System.IO;
    ```

    ```vb
    Imports System.Runtime.Caching
    Imports System.IO
    ```

3. 在事件处理程序中，添加以下代码以实例化缓存对象：

    ```csharp
    ObjectCache cache = MemoryCache.Default;
    ```

    ```vb
    Dim cache As ObjectCache = MemoryCache.Default
    ```

     <xref:System.Runtime.Caching.ObjectCache> 类是提供内存中对象缓存的内置类。

4. 添加以下代码以读取名为 `filecontents`的缓存条目的内容：

    ```vb
    Dim fileContents As String = TryCast(cache("filecontents"), String)
    ```

    ```csharp
    string fileContents = cache["filecontents"] as string;
    ```

5. 添加以下代码以检查是否存在名为 `filecontents` 的缓存条目：

    ```vb
    If fileContents Is Nothing Then

    End If
    ```

    ```csharp
    if (fileContents == null)
    {

    }
    ```

     如果指定的缓存项不存在，则必须读取文本文件并将其作为缓存项添加到缓存中。

6. 在 `if/then` 块中，添加以下代码以创建新的 <xref:System.Runtime.Caching.CacheItemPolicy> 对象，该对象指定该缓存条目在10秒后过期。

    ```vb
    Dim policy As New CacheItemPolicy()
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)
    ```

    ```csharp
    CacheItemPolicy policy = new CacheItemPolicy();
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);
    ```

     如果未提供任何逐出或过期信息，则默认值为 <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>，这意味着缓存条目永远不会仅基于绝对时间过期。 相反，缓存项仅在存在内存压力时过期。 最佳做法是，应始终显式提供绝对或可调过期。

7. 在 `if/then` 块中，在上一步中添加的代码后面，添加以下代码以创建要监视的文件路径的集合，并将文本文件的路径添加到集合中：

    ```vb
    Dim filePaths As New List(Of String)()
    filePaths.Add("c:\cache\cacheText.txt")
    ```

    ```csharp
    List<string> filePaths = new List<string>();
    filePaths.Add("c:\\cache\\cacheText.txt");
    ```

    > [!NOTE]
    > 如果不 `c:\cache\cacheText.txt`要使用的文本文件，请指定要使用的文本文件的路径。

8. 在上一步中添加的代码后面，添加以下代码，以将新的 <xref:System.Runtime.Caching.HostFileChangeMonitor> 对象添加到缓存项的更改监视器集合中：

    ```vb
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))
    ```

    ```csharp
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));
    ```

     <xref:System.Runtime.Caching.HostFileChangeMonitor> 对象监视文本文件的路径，并在发生更改时通知缓存。 在此示例中，如果文件的内容发生更改，缓存项将过期。

9. 在上一步中添加的代码后面，添加以下代码以读取文本文件的内容：

    ```vb
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()
    ```

    ```csharp
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + "\n" + DateTime.Now;
    ```

     添加了日期和时间戳，以便您能够查看缓存条目的过期时间。

10. 在上一步中添加的代码后面，添加以下代码，以将文件内容作为 <xref:System.Runtime.Caching.CacheItem> 实例插入到缓存对象中：

    ```vb
    cache.Set("filecontents", fileContents, policy)
    ```

    ```csharp
    cache.Set("filecontents", fileContents, policy);
    ```

     通过将之前创建的 <xref:System.Runtime.Caching.CacheItemPolicy> 对象作为参数传递，来指定有关如何逐出缓存项的信息。

11. 在 `if/then` 块后，添加以下代码以在消息框中显示缓存的文件内容：

    ```vb
    MessageBox.Show(fileContents)
    ```

    ```csharp
    MessageBox.Show(fileContents);
    ```

12. 在 "**生成**" 菜单中，单击 "**生成 WPFCaching** " 以生成项目。

## <a name="testing-caching-in-the-wpf-application"></a>在 WPF 应用程序中测试缓存
 现在可以对应用程序进行测试。

#### <a name="to-test-caching-in-the-wpf-application"></a>在 WPF 应用程序中测试缓存

1. 按 Ctrl+F5 运行应用程序。

     将显示 "`MainWindow`" 窗口。

2. 单击 "**获取缓存**"。

     文本文件中的缓存内容显示在一个消息框中。 请注意该文件上的时间戳。

3. 关闭消息框，然后再次单击 "**获取缓存**"。

     时间戳未更改。 这表示显示缓存内容。

4. 等待10秒钟或更多，然后再次单击 "**获取缓存**"。

     此时将显示新的时间戳。 这表示策略使缓存条目过期，并显示新的缓存内容。

5. 在文本编辑器中，打开您创建的文本文件。 不要进行任何更改。

6. 关闭消息框，然后再次单击 "**获取缓存**"。

     再次注意时间戳。

7. 对文本文件进行更改，然后保存该文件。

8. 关闭消息框，然后再次单击 "**获取缓存**"。

     此消息框包含文本文件中的更新内容和新的时间戳。 这表明在更改文件时，主机文件更改监视器会立即逐出缓存项，即使绝对超时期限尚未过期。

    > [!NOTE]
    > 你可以将逐出时间增加到20秒或更多，以允许更多的时间来对文件进行更改。

## <a name="code-example"></a>代码示例
 完成本演练后，你创建的项目的代码将与以下示例类似。

 [!code-csharp[CachingWPFApplications#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]

## <a name="see-also"></a>请参阅

- <xref:System.Runtime.Caching.MemoryCache>
- <xref:System.Runtime.Caching.ObjectCache>
- <xref:System.Runtime.Caching>
- [在 .NET Framework 应用程序中缓存](../../performance/caching-in-net-framework-applications.md)
