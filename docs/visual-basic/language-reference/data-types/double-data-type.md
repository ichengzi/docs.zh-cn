---
title: Double 数据类型
ms.date: 07/20/2015
f1_keywords:
- vb.Double
helpviewer_keywords:
- 'identifier type characters [Visual Basic], #'
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- 0 characters [Visual Basic], trailing
- literal type characters [Visual Basic], R
- data types [Visual Basic], assigning
- Double data type [Visual Basic]
- '# identifier type character'
- double-precision numbers
- floating-point numbers [Visual Basic], Double data type
- R literal type character [Visual Basic]
- zeros, trailing
- Double data type
ms.assetid: 0c5670f7-fcb1-453a-bef1-374730cd38fd
ms.openlocfilehash: 347b5c7b7af4c4aafec0f91aca46a8cf640236b9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344015"
---
# <a name="double-data-type-visual-basic"></a>Double 数据类型 (Visual Basic)

Holds signed IEEE 64-bit (8-byte) double-precision floating-point numbers that range in value from -1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values and from 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values. Double-precision numbers store an approximation of a real number.

## <a name="remarks"></a>备注

The `Double` data type provides the largest and smallest possible magnitudes for a number.

`Double` 的默认值为 0。

## <a name="programming-tips"></a>编程提示

- **Precision.** When you work with floating-point numbers, remember that they do not always have a precise representation in memory. This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator. For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).

- **Trailing Zeros.** The floating-point data types do not have any internal representation of trailing zero characters. For example, they do not distinguish between 4.2000 and 4.2. Consequently, trailing zero characters do not appear when you display or print floating-point values.

- **Type Characters.** 将文本类型字符 `R` 追加到文本会将其强制转换为 `Double` 数据类型。 For example, if an integer value is followed by `R`, the value is changed to a `Double`.

  ```vb
  ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:
  Dim dub As Double = 4.0R
  ```

  将标识符类型字符 `#` 追加到任何标识符会将其强制转换为 `Double`。 In the following example, the variable `num` is typed as a `Double`:

  ```vb
  Dim num# = 3
  ```

- **Framework Type.** .NET Framework 中的对应类型是 <xref:System.Double?displayProperty=nameWithType> 结构。

## <a name="see-also"></a>请参阅

- <xref:System.Double?displayProperty=nameWithType>
- [数据类型](../../../visual-basic/language-reference/data-types/index.md)
- [Decimal 数据类型](../../../visual-basic/language-reference/data-types/decimal-data-type.md)
- [Single 数据类型](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [类型转换函数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [转换摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [有效使用数据类型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [数据类型疑难解答](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [类型字符](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
