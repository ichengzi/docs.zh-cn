---
title: boolean 数据类型
ms.date: 07/20/2015
f1_keywords:
- vb.FALSE
- vb.TRUE
- vb.Boolean
helpviewer_keywords:
- Boolean data type
- Boolean values [Visual Basic], False keyword
- False keyword [Visual Basic]
- True keyword [Visual Basic]
- Boolean values [Visual Basic], True keyword
ms.assetid: 4858e630-4813-4216-a55e-f4d0feb884e4
ms.openlocfilehash: 5d05514207c5d07e81aab897f40f728570f6bd87
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347845"
---
# <a name="boolean-data-type-visual-basic"></a>Boolean 数据类型 (Visual Basic)

Holds values that can be only `True` or `False`. The keywords `True` and `False` correspond to the two states of `Boolean` variables.  
  
## <a name="remarks"></a>备注  

 Use the [Boolean Data Type (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) to contain two-state values such as true/false, yes/no, or on/off.  
  
 `Boolean` 的默认值为 `False`。  
  
 `Boolean` values are not stored as numbers, and the stored values are not intended to be equivalent to numbers. You should never write code that relies on equivalent numeric values for `True` and `False`. Whenever possible, you should restrict usage of `Boolean` variables to the logical values for which they are designed.  
  
## <a name="type-conversions"></a>类型转换  

 When Visual Basic converts numeric data type values to `Boolean`, 0 becomes `False` and all other values become `True`. When Visual Basic converts `Boolean` values to numeric types, `False` becomes 0 and `True` becomes -1.  
  
 When you convert between `Boolean` values and numeric data types, keep in mind that the .NET Framework conversion methods do not always produce the same results as the Visual Basic conversion keywords. This is because the Visual Basic conversion retains behavior compatible with previous versions. For more information, see "Boolean Type Does Not Convert to Numeric Type Accurately" in [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="programming-tips"></a>编程提示  
  
- **Negative Numbers.** `Boolean` is not a numeric type and cannot represent a negative value. In any case, you should not use `Boolean` to hold numeric values.  
  
- **Type Characters.** `Boolean` has no literal type character or identifier type character.  
  
- **Framework Type.** .NET Framework 中的对应类型是 <xref:System.Boolean?displayProperty=nameWithType> 结构。  
  
## <a name="example"></a>示例  

 In the following example, `runningVB` is a `Boolean` variable, which stores a simple yes/no setting.  
  
```vb  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Boolean?displayProperty=nameWithType>
- [数据类型](../../../visual-basic/language-reference/data-types/index.md)
- [类型转换函数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [转换摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [有效使用数据类型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [数据类型疑难解答](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [CType 函数](../../../visual-basic/language-reference/functions/ctype-function.md)
