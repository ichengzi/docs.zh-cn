---
title: Decimal 数据类型
ms.date: 07/20/2015
f1_keywords:
- vb.Decimal
helpviewer_keywords:
- literal type characters [Visual Basic], D
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- Decimal data type
- D literal type character [Visual Basic]
- decimals, Decimal data type
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- decimal keyword [Visual Basic]
- numbers [Visual Basic], real
- variable-precision numbers
- zeros, trailing
- '@ identifier type character'
- identifier type characters [Visual Basic], @
ms.assetid: 1d855b45-afe2-45b0-a623-96b6f63a43d5
ms.openlocfilehash: 6d62bcc1d043b45c0fc30154d9dc633b998f97b7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344032"
---
# <a name="decimal-data-type-visual-basic"></a>Decimal 数据类型 (Visual Basic)

Holds signed 128-bit (16-byte) values representing 96-bit (12-byte) integer numbers scaled by a variable power of 10. The scaling factor specifies the number of digits to the right of the decimal point; it ranges from 0 through 28. With a scale of 0 (no decimal places), the largest possible value is +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E+28). With 28 decimal places, the largest value is +/-7.9228162514264337593543950335, and the smallest nonzero value is +/-0.0000000000000000000000000001 (+/-1E-28).

## <a name="remarks"></a>备注

The `Decimal` data type provides the greatest number of significant digits for a number. It supports up to 29 significant digits and can represent values in excess of 7.9228 x 10^28. It is particularly suitable for calculations, such as financial, that require a large number of digits but cannot tolerate rounding errors.

`Decimal` 的默认值为 0。

## <a name="programming-tips"></a>编程提示

- **Precision.** `Decimal` is not a floating-point data type. The `Decimal` structure holds a binary integer value, together with a sign bit and an integer scaling factor that specifies what portion of the value is a decimal fraction. Because of this, `Decimal` numbers have a more precise representation in memory than floating-point types (`Single` and `Double`).

- **性能。** The `Decimal` data type is the slowest of all the numeric types. You should weigh the importance of precision against performance before choosing a data type.

- **Widening.** The `Decimal` data type widens to `Single` or `Double`. This means you can convert `Decimal` to either of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.

- **Trailing Zeros.** Visual Basic does not store trailing zeros in a `Decimal` literal. However, a `Decimal` variable preserves any trailing zeros acquired computationally. 下面的示例阐释了这一点。

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  The output of `MsgBox` in the preceding example is as follows:

  ```console
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- **Type Characters.** 将文本类型字符 `D` 追加到文本会将其强制转换为 `Decimal` 数据类型。 将标识符类型字符 `@` 追加到任何标识符会将其强制转换为 `Decimal`。

- **Framework Type.** .NET Framework 中的对应类型是 <xref:System.Decimal?displayProperty=nameWithType> 结构。

## <a name="range"></a>范围

 You might need to use the `D` type character to assign a large value to a `Decimal` variable or constant. This requirement is because the compiler interprets a literal as `Long` unless a literal type character follows the literal, as the following example shows.

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

The declaration for `bigDec1` doesn't produce an overflow because the value that's assigned to it falls within the range for `Long`. The `Long` value can be assigned to the `Decimal` variable.

The declaration for `bigDec2` generates an overflow error because the value that's assigned to it is too large for `Long`. Because the numeric literal can't first be interpreted as a `Long`, it can't be assigned to the `Decimal` variable.

For `bigDec3`, the literal type character `D` solves the problem by forcing the compiler to interpret the literal as a `Decimal` instead of as a `Long`.

## <a name="see-also"></a>请参阅

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [数据类型](../../../visual-basic/language-reference/data-types/index.md)
- [Single 数据类型](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [Double 数据类型](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [类型转换函数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [转换摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [有效使用数据类型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
