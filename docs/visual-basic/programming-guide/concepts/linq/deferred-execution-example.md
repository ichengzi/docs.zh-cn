---
title: 延迟执行示例
ms.date: 07/20/2015
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
ms.openlocfilehash: 6ab8f6434bb24b7a66ca4afd1d082911481671f6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354231"
---
# <a name="deferred-execution-example-visual-basic"></a>Deferred Execution Example (Visual Basic)

本主题演示延迟执行和迟缓计算如何影响 LINQ to XML 查询的执行。

## <a name="example"></a>示例

下面的示例演示使用采用延迟执行的扩展方法时的执行顺序。 此示例声明一个由三个字符串组成的数组。 然后，循环访问 `ConvertCollectionToUpperCase` 所返回的集合。

```vb
Imports System.Runtime.CompilerServices

Module Module1

    <Extension()>
    Private Iterator Function ConvertCollectionToUpperCase(
    ByVal source As IEnumerable(Of String)) _
    As IEnumerable(Of String)
        For Each str As String In source
            Console.WriteLine("ToUpper: source {0}", str)
            Yield str.ToUpper()
        Next
    End Function

    Sub Main()
        Dim stringArray = New String() {"abc", "def", "ghi"}

        Dim q = From str In stringArray.ConvertCollectionToUpperCase()
                Select str

        For Each Str As String In q
            Console.WriteLine("Main: str {0}", Str)
        Next
    End Sub

End Module
```

该示例产生下面的输出：

```console
ToUpper: source abc
Main: str ABC
ToUpper: source def
Main: str DEF
ToUpper: source ghi
Main: str GHI
```

请注意，在循环访问 `ConvertCollectionToUpperCase` 所返回的集合时，每一项都从源字符串数组检索，并且在源字符串数组中检索下一项之前，被转换为大写形式。

可以看到，在 `foreach` 的 `Main` 循环中处理所返回集合的每一项之后，字符串数组才会完全转换为大写形式。

## <a name="see-also"></a>请参阅

- [Tutorial: Deferred Execution (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
