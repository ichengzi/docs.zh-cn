---
title: '#if 预处理器指令 - C# 参考'
ms.custom: seodec18
ms.date: 10/27/2019
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: 561a628c60888a8d4f3c50c8413784e1ed210599
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/29/2019
ms.locfileid: "73035996"
---
# <a name="if-c-reference"></a>#if（C# 参考）

如果 C# 编译器遇到 `#if` 指令，最终是 [#endif](preprocessor-endif.md) 指令，则仅当定义指定的符号时，它才编译这些指令之间的代码。 与 C 和 C++ 不同，你不能为符号分配数字值。 C# 中的 #if 语句是布尔值，且仅测试是否已定义该符号。 例如:

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

仅可以使用运算符 [==](../operators/equality-operators.md#equality-operator-)（相等）和 [!=](../operators/equality-operators.md#inequality-operator-)（不相等）测试 [true](../keywords/true-literal.md) 或 [false](../keywords/false-literal.md)。 True 表示定义该符号。 语句 `#if DEBUG` 具有与 `#if (DEBUG == true)` 相同的含义。 可以使用运算符 [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) (and)、[&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) (or) 和 [!](../operators/boolean-logical-operators.md#logical-negation-operator-) (not) 评估是否已经定义了多个符号。 还可以用括号对符号和运算符进行分组。

## <a name="remarks"></a>备注

`#if` 以及 [#else](preprocessor-else.md)、[#elif](preprocessor-elif.md)、[#endif](preprocessor-endif.md)、[#define](preprocessor-define.md) 和 [#undef](preprocessor-undef.md) 指令，允许基于是否存在一个或多个符号包括或排除代码。 这在编译调试版本的代码或编译特定配置的代码时会很有用。

以 `#if` 指令开头的条件指令必须以 `#endif` 指令显式终止。

`#define` 允许你定义一个符号。 然后通过将该符号用作传递给 `#if` 指令的表达式，该表达式的计算结果为 `true`。

还可以通过 [-define](../compiler-options/define-compiler-option.md) 编译器选项来定义符号。 可以通过 [#undef](preprocessor-undef.md) 取消定义符号。

使用 `-define` 或 `#define` 定义的符号与具有相同名称的变量不冲突。 也就是说，变量名称不应传递给预处理器指令，且符号仅能由预处理器指令评估。

使用 `#define` 创建的符号的作用域是在其中定义它的文件。

此外，生成系统还会感知表示 SDK 样式项目中不同[目标框架](../../../standard/frameworks.md)的预定义预处理器符号。 在创建可以面向多个.NET 实现或版本的应用程序时，这些符号会很有用。

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

> [!NOTE]
> 对于传统的 .NET Framework 项目，必须通过项目的属性页面在 Visual Studio 中为不同目标框架手动配置条件编译符号。

其他预定义符号包括 DEBUG 和 TRACE 常量。 你可以使用 `#define` 替代项目的值集。 例如，会根据生成配置属性（“调试”或者“发布”模式）自动设置 DEBUG 符号。

## <a name="examples"></a>示例

下例显示如何在文件上定义 MYTEST 符号，然后测试 MYTEST 和 DEBUG 符号的值。 此示例的输出取决于是在“调试”还是“发布”配置模式下生成项目。

```csharp
#define MYTEST
using System;
public class MyClass
{
    static void Main()
    {
#if (DEBUG && !MYTEST)
        Console.WriteLine("DEBUG is defined");
#elif (!DEBUG && MYTEST)
        Console.WriteLine("MYTEST is defined");
#elif (DEBUG && MYTEST)
        Console.WriteLine("DEBUG and MYTEST are defined");  
#else
        Console.WriteLine("DEBUG and MYTEST are not defined");
#endif
    }
}
```

下例显示如何针对不同的目标框架进行测试，以便在可能时使用较新的 API：

```csharp
public class MyClass
{
    static void Main()
    {
#if NET40
        WebClient _client = new WebClient();
#else
        HttpClient _client = new HttpClient();
#endif
    }
    //...
}
```

## <a name="see-also"></a>请参阅

- [C# 参考](../index.md)
- [C# 编程指南](../../programming-guide/index.md)
- [C# 预处理器指令](index.md)
- [如何：使用跟踪和调试执行有条件编译](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
