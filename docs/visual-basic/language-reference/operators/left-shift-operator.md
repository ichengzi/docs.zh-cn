---
title: << 运算符
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: 327d0e5cbd1ebcc43bd47fb068f4513940c2165a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350984"
---
# <a name="-operator-visual-basic"></a>\<\< Operator (Visual Basic)
Performs an arithmetic left shift on a bit pattern.  
  
## <a name="syntax"></a>语法  
  
```vb  
result = pattern << amount  
```  
  
## <a name="parts"></a>部件  
 `result`  
 必须的。 Integral numeric value. The result of shifting the bit pattern. The data type is the same as that of `pattern`.  
  
 `pattern`  
 必须的。 Integral numeric expression. The bit pattern to be shifted. The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).  
  
 `amount`  
 必须的。 Numeric expression. The number of bits to shift the bit pattern. The data type must be `Integer` or widen to `Integer`.  
  
## <a name="remarks"></a>备注  
 Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end. In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.  
  
 To prevent a shift by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask that corresponds to the data type of `pattern`. The binary AND of these values is used for the shift amount. The size masks are as follows:  
  
|Data type of `pattern`|Size mask (decimal)|Size mask (hexadecimal)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`，`Byte`|7|&H00000007|  
|`Short`，`UShort`|15|&H0000000F|  
|`Integer`，`UInteger`|31|&H0000001F|  
|`Long`，`ULong`|63|&H0000003F|  
  
 If `amount` is zero, the value of `result` is identical to the value of `pattern`. If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.  
  
 Arithmetic shifts never generate overflow exceptions.  
  
> [!NOTE]
> The `<<` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure. If your code uses this operator on such a class or structure, be sure that you understand its redefined behavior. 有关更多信息，请参见 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>示例  
 The following example uses the `<<` operator to perform arithmetic left shifts on integral values. The result always has the same data type as that of the expression being shifted.  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 The results of the previous example are as follows:  
  
- `result1` is 192 (0000 0000 1100 0000).  
  
- `result2` is 3072 (0000 1100 0000 0000).  
  
- `result3` is -32768 (1000 0000 0000 0000).  
  
- `result4` is 384 (0000 0001 1000 0000).  
  
- `result5` is 0 (shifted 15 places to the left).  
  
 The shift amount for `result4` is calculated as 17 AND 15, which equals 1.  
  
## <a name="see-also"></a>请参阅

- [移位运算符](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [赋值运算符](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<<= 运算符](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [Visual Basic 中的运算符优先级](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [按功能列出的运算符](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
