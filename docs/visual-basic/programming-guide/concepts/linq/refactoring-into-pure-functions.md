---
title: 重构为纯函数
ms.date: 07/20/2015
ms.assetid: 99e7d27b-a3ff-4577-bdb2-5a8278d6d7af
ms.openlocfilehash: 22b371c6136836d6e0f1281f824b69378c0d3e4a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346524"
---
# <a name="refactoring-into-pure-functions-visual-basic"></a>Refactoring Into Pure Functions (Visual Basic)

纯函数转换的一个重要方面是学习如何使用纯函数重构代码。

如本节前面所述，纯函数具有两个有用的特性：

- 它没有任何副作用。 函数不会更改函数以外的任何变量或任何类型的数据。

- 它具有一致性。 在提供同一组输入数据的情况下，它将始终返回相同的输出值。

 转换为函数编程的一种方式是重构现有代码以消除不必要的副作用和外部依赖项。 这样，您可以创建现有代码的纯函数版本。

本主题讨论什么是纯函数，什么不是纯函数。 The [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.

## <a name="eliminating-side-effects-and-external-dependencies"></a>消除副作用和外部依赖项

下面的示例对比两个非纯函数和一个纯函数。

### <a name="non-pure-function-that-changes-a-class-member"></a>可更改类成员的非纯函数

在下面的代码中，`HyphenatedConcat` 函数不是纯函数，因为它修改了类中的 `aMember` 数据成员：

```vb
Module Module1
    Dim aMember As String = "StringOne"

    Public Sub HyphenatedConcat(ByVal appendStr As String)
        aMember = aMember & "-" & appendStr
    End Sub

    Sub Main()
        HyphenatedConcat("StringTwo")
        Console.WriteLine(aMember)
    End Sub
End Module
```

此代码生成以下输出：

```console
StringOne-StringTwo
```

Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a  `shared` member or an instance member. 纯函数不会更改函数以外的任何数据。

### <a name="non-pure-function-that-changes-an-argument"></a>可更改参数的非纯函数

此外，此同一个函数的下面版本不是纯函数，因为它修改了其参数 `sb` 的内容。

```vb
Module Module1
    Public Sub HyphenatedConcat(ByVal sb As StringBuilder, ByVal appendStr As String)
        sb.Append("-" & appendStr)
    End Sub

    Sub Main()
        Dim sb1 As StringBuilder = New StringBuilder("StringOne")
        HyphenatedConcat(sb1, "StringTwo")
        Console.WriteLine(sb1)
    End Sub
End Module
```

此版本的程序生成的输出与第一个版本相同，因为 `HyphenatedConcat` 函数已通过调用 <xref:System.Text.StringBuilder.Append%2A> 成员函数而更改了其第一个参数的值（状态）。 请注意，即使 `HyphenatedConcat` 实际上使用了按值调用参数传递，也会发生此更改。

> [!IMPORTANT]
> 对于引用类型，按值传递参数会得到对所传递对象的引用的副本。 此副本与原始引用一样，仍与同一个实例数据关联（除非为引用变量分配新对象）。 函数修改参数不一定需要按引用调用。

### <a name="pure-function"></a>纯函数

下面版本的程序演示如何将 `HyphenatedConcat` 函数作为纯函数实现。

```vb
Module Module1
    Public Function HyphenatedConcat(ByVal s As String, ByVal appendStr As String) As String
        Return (s & "-" & appendStr)
    End Function

    Sub Main()
        Dim s1 As String = "StringOne"
        Dim s2 As String = HyphenatedConcat(s1, "StringTwo")
        Console.WriteLine(s2)
    End Sub
End Module
```

此版本同样生成相同的输出行：`StringOne-StringTwo`。 请注意保留串联值，它存储在中间变量 `s2` 中。

一种非常实用的方法是编写本地不纯（即声明和修改本地变量）但在全局为纯的函数。 这些函数具有许多需要的可组合特性，但舍弃了一些较为繁复的函数编程语法，如在使用简单的循环即可完成同样操作时必须使用递归。

## <a name="standard-query-operators"></a>标准查询运算符

标准查询运算符的重要特性是它们以纯函数的形式实现。

For more information, see [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).

## <a name="see-also"></a>请参阅

- [Introduction to Pure Functional Transformations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [Functional Programming vs. Imperative Programming (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
