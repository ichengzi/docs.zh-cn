---
title: 默认值表 - C# 引用
ms.custom: seodec18
description: 了解 C# 类型的默认值。
ms.date: 07/29/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 2f1ad5cc029b93261153e46d854cd8bf3e31ce92
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428535"
---
# <a name="default-values-table-c-reference"></a>默认值表（C# 引用）

下表显示 C# 类型的默认值：

|类型|默认值|
|---------|------------------|
|任何引用类型|`null`|
|任何[内置整数数值类型](../builtin-types/integral-numeric-types.md)|0（零）|
|任何[内置浮点型数值类型](../builtin-types/floating-point-numeric-types.md)|0（零）|
|[bool](bool.md)|`false`|
|[char](../builtin-types/char.md)|`'\0'` (U + 0000)|
|[enum](enum.md)|表达式 `(E)0` 生成的值，其中 `E` 是枚举标识符。|
|[struct](struct.md)|通过如下设置生成的值：将所有值类型的字段设置为其默认值，将所有引用类型的字段设置为 `null`。|
|任何[可以为 null 的值类型](../builtin-types/nullable-value-types.md)|<xref:System.Nullable%601.HasValue%2A> 属性为 `false` 且 <xref:System.Nullable%601.Value%2A> 属性未定义的实例。 该默认值也称为可以为 null 的值类型的“null”  值。|

使用[默认运算符](../operators/default.md)生成默认类型值，如下面的示例所示：

```csharp
int a = default(int);
```

从 C# 7.1 开始，可使用[`default`文本](../operators/default.md#default-literal)来初始化变量，使其具有其类型的默认值：

```csharp
int a = default;
```

对于值类型，隐式无参数构造函数还可生成类型的默认值，如以下示例所示：

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

## <a name="c-language-specification"></a>C# 语言规范

有关更多信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)的以下部分：

- [默认值](~/_csharplang/spec/variables.md#default-values)
- [默认构造函数](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a>请参阅

- [C# 参考](../index.md)
- [C# 关键字](index.md)
- [内置类型表](built-in-types-table.md)
- [构造函数](../../programming-guide/classes-and-structs/constructors.md)
