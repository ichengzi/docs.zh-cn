---
title: ^ 运算符
ms.date: 07/20/2015
f1_keywords:
- vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponentiation
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
ms.openlocfilehash: b9860b7b6e076fc9c0288818aa9e4f2c0fc4c356
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331108"
---
# <a name="-operator-visual-basic"></a>^ 运算符 (Visual Basic)

Raises a number to the power of another number.

## <a name="syntax"></a>语法

```vb
number ^ exponent
```

## <a name="parts"></a>部件

`number`\
必须的。 任何数值表达式。

`exponent`\
必须的。 任何数值表达式。

## <a name="result"></a>结果

The result is `number` raised to the power of `exponent`, always as a `Double` value.

## <a name="supported-types"></a>支持的类型

`Double` Operands of any different type are converted to `Double`.

## <a name="remarks"></a>备注

Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).

The value of `exponent` can be fractional, negative, or both.

When more than one exponentiation is performed in a single expression, the `^` operator is evaluated as it is encountered from left to right.

> [!NOTE]
> The `^` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure. If your code uses this operator on such a class or structure, be sure you understand its redefined behavior. 有关更多信息，请参见 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。

## <a name="example"></a>示例

The following example uses the `^` operator to raise a number to the power of an exponent. The result is the first operand raised to the power of the second.

[!code-vb[VbVbalrOperators#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#20)]

The preceding example produces the following results:

`exp1` is set to 4 (2 squared).

`exp2` is set to 19683 (3 cubed, then that value cubed).

`exp3` is set to -125 (-5 cubed).

`exp4` is set to 625 (-5 to the fourth power).

`exp5` is set to 2 (cube root of 8).

`exp6` is set to 0.5 (1.0 divided by the cube root of 8).

Note the importance of the parentheses in the expressions in the preceding example. Because of *operator precedence*, Visual Basic normally performs the `^` operator before any others, even the unary `–` operator. If `exp4` and `exp6` had been calculated without parentheses, they would have produced the following results:

`exp4 = -5 ^ 4` would be calculated as –(5 to the fourth power), which would result in -625.

`exp6 = 8 ^ -1.0 / 3.0` would be calculated as (8 to the –1 power, or 0.125) divided by 3.0, which would result in 0.041666666666666666666666666666667.

## <a name="see-also"></a>请参阅

- [^= 运算符](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [算术运算符](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic 中的运算符优先级](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [按功能列出的运算符](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
