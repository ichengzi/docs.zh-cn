---
title: 分部方法
ms.date: 07/20/2015
f1_keywords:
- vb.PartialMethod
- PartialMethod
helpviewer_keywords:
- custom logic into code [Visual Basic]
- partial methods [Visual Basic]
- partial [Visual Basic], methods [Visual Basic]
- methods [Visual Basic], partial methods
- inserting custom logic into code
ms.assetid: 74b3368b-b348-44a0-a326-7d7dc646f4e9
ms.openlocfilehash: 7abf0565a985f1fb44fcf2bb91b9220d57a10f20
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352625"
---
# <a name="partial-methods-visual-basic"></a>分部方法 (Visual Basic)
Partial methods enable developers to insert custom logic into code. Typically, the code is part of a designer-generated class. Partial methods are defined in a partial class that is created by a code generator, and they are commonly used to provide notification that something has been changed. They enable the developer to specify custom behavior in response to the change.  
  
 The designer of the code generator defines only the method signature and one or more calls to the method. Developers can then provide implementations for the method if they want to customize the behavior of the generated code. When no implementation is provided, calls to the method are removed by the compiler, resulting in no additional performance overhead.  
  
## <a name="declaration"></a>声明  
 The generated code marks the definition of a partial method by placing the keyword `Partial` at the start of the signature line.  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 The definition must meet the following conditions:  
  
- The method must be a `Sub`, not a `Function`.  
  
- The body of the method must be left empty.  
  
- The access modifier must be `Private`.  
  
## <a name="implementation"></a>实现  
 The implementation consists primarily of filling in the body of the partial method. The implementation is typically in a separate partial class from the definition, and is written by a developer who wants to extend the generated code.  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 The previous example duplicates the signature in the declaration exactly, but variations are possible. In particular, other modifiers can be added, such as `Overloads` or `Overrides`. Only one `Overrides` modifier is permitted. For more information about method modifiers, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="use"></a>使用“管理”工作区中的“连接的管理组”  
 You call a partial method as you would call any other `Sub` procedure. If the method has been implemented, the arguments are evaluated and the body of the method is executed. However, remember that implementing a partial method is optional. If the method is not implemented, a call to it has no effect, and expressions passed as arguments to the method are not evaluated.  
  
## <a name="example"></a>示例  
 In a file named Product.Designer.vb, define a `Product` class that has a `Quantity` property.  
  
 [!code-vb[VbVbalrPartialMeths#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#4)]  
  
 In a file named Product.vb, provide an implementation for `QuantityChanged`.  
  
 [!code-vb[VbVbalrPartialMeths#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#5)]  
  
 Finally, in the Main method of a project, declare a `Product` instance and provide an initial value for its `Quantity` property.  
  
 [!code-vb[VbVbalrPartialMeths#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#6)]  
  
 A message box should appear that displays this message:  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a>请参阅

- [Sub 语句](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Sub 过程](./sub-procedures.md)
- [可选参数](./optional-parameters.md)
- [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)
- [LINQ to SQL 中的代码生成](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [通过使用分部方法添加业务逻辑](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
