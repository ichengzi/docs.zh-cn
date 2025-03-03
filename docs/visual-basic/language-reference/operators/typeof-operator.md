---
title: TypeOf 运算符
ms.date: 07/20/2015
f1_keywords:
- TypeOf
- vb.TypeOf
helpviewer_keywords:
- types [Visual Basic], compatible
- comparison operators [Visual Basic]
- TypeOf...Is expression
- data types [Visual Basic], compatible
- TypeOf operator [Visual Basic]
- compatible data types [Visual Basic]
ms.assetid: 33f65296-659a-4b9a-9a29-c2a91cff68b2
ms.openlocfilehash: 22af5b8f8488ca44e388596530decd52e33525dc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350895"
---
# <a name="typeof-operator-visual-basic"></a>TypeOf 运算符 (Visual Basic)
Checks whether the runtime type of an expression's result is type-compatible with the specified type.
  
## <a name="syntax"></a>语法  
  
```vb  
result = TypeOf objectexpression Is typename  
```  
  
```vb  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a>部件  
 `result`  
 返回。 一个 `Boolean` 值。  
  
 `objectexpression`  
 必须的。 计算结果为引用类型的任何表达式。  
  
 `typename`  
 必须的。 任何数据类型名。  
  
## <a name="remarks"></a>备注  
 `TypeOf` 运算符确定 `objectexpression` 的运行时类型是否与 `typename` 兼容。 兼容性取决于 `typename` 的类型类别。 下表显示如何确定兼容性。  
  
|`typename` 的类型类别|兼容性条件|  
|---------------------------------|-----------------------------|  
|实例|`objectexpression` 属于类型 `typename` 或继承自 `typename`|  
|结构|`objectexpression` 属于类型 `typename`|  
|接口|`objectexpression` 实现 `typename` 或继承自实现 `typename` 的类|  
  
 如果 `objectexpression` 的运行时类型满足兼容性条件，则 `result` 是 `True`。 否则 `result` 为 `False`。  如果 `objectexpression` 为 null，则 `TypeOf`...`Is` 返回 `False`，...`IsNot` 返回 `True`。  
  
 `TypeOf` 始终与 `Is` 关键字一起使用来构造 `TypeOf`...`Is` 表达式，或与 `IsNot` 关键字一起使用来构造 `TypeOf`...`IsNot` 表达式。  
  
## <a name="example"></a>示例  
 下面的示例使用 `TypeOf`...`Is` 表达式测试具有不同数据类型的两个对象引用变量的类型兼容性。  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 变量 `refInteger` 具有运行时类型 `Integer`。 它与 `Integer` 兼容，但不与 `Double` 兼容。 变量 `refForm` 具有运行时类型 <xref:System.Windows.Forms.Form>。 它与 <xref:System.Windows.Forms.Form> 兼容因为这是其类型，与 <xref:System.Windows.Forms.Control> 兼容因为 <xref:System.Windows.Forms.Form> 继承自 <xref:System.Windows.Forms.Control>，与 <xref:System.ComponentModel.IComponent> 兼容因为 <xref:System.Windows.Forms.Form> 继承自 <xref:System.ComponentModel.Component>（它实现 <xref:System.ComponentModel.IComponent>）。 但是，`refForm` 与 <xref:System.Windows.Forms.Label> 不兼容。  
  
## <a name="see-also"></a>请参阅

- [Is 运算符](../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot 运算符](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Comparison Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic 中的运算符优先级](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [按功能列出的运算符](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [运算符和表达式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
