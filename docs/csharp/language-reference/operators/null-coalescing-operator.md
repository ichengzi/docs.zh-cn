---
title: ?? 和 ??= 运算符 - C# 参考
ms.custom: seodec18
ms.date: 09/10/2019
f1_keywords:
- ??_CSharpKeyword
- ??=_CSharpKeyword
helpviewer_keywords:
- null-coalescing operator [C#]
- ?? operator [C#]
- null-coalescing assignment [C#]
- ??= operator [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 2bd6fe3d2d283e64eebc2251416fa5234e30bdad
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739656"
---
# <a name="-and--operators-c-reference"></a>?? 和 ??= 运算符（C# 参考）

如果左操作数的值不为 `null`，则 null 合并运算符 `??` 返回该值；否则，它会计算右操作数并返回其结果。 如果左操作数的计算结果为非 null，则 `??` 运算符不会计算其右操作数。

适用于 C# 8.0 及更高版本，只有在左操作数计算为 `null` 时，null 合并赋值运算符 `??=` 才将其右操作数的值分配给左操作数。 如果左操作数的计算结果为非 null，则 `??=` 运算符不会计算其右操作数。

[!code-csharp[null-coalescing assignment](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#Assignment)]

`??=` 运算符的左操作数必须是变量、[属性](../../programming-guide/classes-and-structs/properties.md)或[索引器](../../programming-guide/indexers/index.md)元素。

在 C# 7.3 及更早版本中，`??` 运算符左操作数的类型必须是[引用类型](../keywords/reference-types.md)或[可以为 null 的值类型](../builtin-types/nullable-value-types.md)。 从 C# 8.0 版本开始，该要求替换为以下内容：`??` 和 `??=` 运算符的左操作数的类型一定是可以为 null 的值类型。 特别是从 C# 8.0 开始，可以使用具有无约束类型参数的 null 合并运算符：

[!code-csharp[unconstrained type parameter](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#UnconstrainedType)]

null 合并运算符是右结合运算符。 也就是说，窗体的表达式

```csharp
a ?? b ?? c
d ??= e ??= f
```

计算结果为

```csharp
a ?? (b ?? c)
d ??= (e ??= f)
```

## <a name="examples"></a>示例

`??` 和 `??=` 运算符在以下应用场景中很有用：

- 在包含 [null 条件运算符 ?. 和 ?[]](member-access-operators.md#null-conditional-operators--and-) 的表达式中，当包含 null 条件运算的表达式结果为 `null` 时，可以使用 `??` 运算符来提供替代表达式用于计算：

  [!code-csharp-interactive[with null-conditional](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- 当使用[可以为 null 值类型](../builtin-types/nullable-value-types.md)并且需要提供基础值类型的值时，可以使用 `??` 运算符指定当可以为 null 的类型的值为 `null` 时要提供的值：

  [!code-csharp-interactive[with nullable types](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  如果可以为 null 的类型的值为 `null` 时要使用的值应为基础值类型的默认值，请使用 <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> 方法。

- 从 C# 7.0 开始，可以使用 [`throw` 表达式](../keywords/throw.md#the-throw-expression)作为 `??` 运算符的右操作数，以使参数检查代码更简洁：

  [!code-csharp[with throw expression](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  前面的示例还演示了如何使用 [expression-bodied 成员](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)来定义属性。

- 从 C# 8.0 开始，可以使用 `??=` 运算符将窗体的代码

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  替换为以下代码：

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a>运算符可重载性

运算符 `??` 和 `??=` 无法进行重载。

## <a name="c-language-specification"></a>C# 语言规范

有关 `??` 运算符的详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)的 [null 合并运算符](~/_csharplang/spec/expressions.md#the-null-coalescing-operator)部分。

有关 `??=` 运算符的详细信息，请参阅[功能建议说明](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md)。

## <a name="see-also"></a>请参阅

- [C# 参考](../index.md)
- [C# 运算符](index.md)
- [?. 和 ?[] 运算符](member-access-operators.md#null-conditional-operators--and-)
- [?: 运算符](conditional-operator.md)
