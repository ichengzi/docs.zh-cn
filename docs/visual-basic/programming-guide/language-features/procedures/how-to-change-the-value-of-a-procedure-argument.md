---
title: 如何：更改过程自变量的值
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
ms.openlocfilehash: e562c0f5ec01380c792b4dc064554171cfb007e7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74339961"
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a>如何：更改过程参数的值 (Visual Basic)
When you call a procedure, each argument you supply corresponds to one of the parameters defined in the procedure. In some cases, the procedure code can change the value underlying an argument in the calling code. In other cases, the procedure can change only its local copy of an argument.  
  
 When you call the procedure, Visual Basic makes a local copy of every argument that is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). For each argument passed [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic gives the procedure code a direct reference to the programming element underlying the argument in the calling code.  
  
 If the underlying element in the calling code is a modifiable element and the argument is passed `ByRef`, the procedure code can use the direct reference to change the element's value in the calling code.  
  
## <a name="changing-the-underlying-value"></a>Changing the Underlying Value  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a>To change the underlying value of a procedure argument in the calling code  
  
1. In the procedure declaration, specify [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) for the parameter corresponding to the argument.  
  
2. In the calling code, pass a modifiable programming element as the argument.  
  
3. In the calling code, do not enclose the argument in parentheses in the argument list.  
  
4. In the procedure code, use the parameter name to assign a value to the underlying element in the calling code.  
  
 See the example further down for a demonstration.  
  
## <a name="changing-local-copies"></a>Changing Local Copies  
 If the underlying element in the calling code is a nonmodifiable element, or if the argument is passed `ByVal`, the procedure cannot change its value in the calling code. However, the procedure can change its local copy of such an argument.  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a>To change the copy of a procedure argument in the procedure code  
  
1. In the procedure declaration, specify [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) for the parameter corresponding to the argument.  
  
     或  
  
     In the calling code, enclose the argument in parentheses in the argument list. This forces Visual Basic to pass the argument by value, even if the corresponding parameter specifies `ByRef`.  
  
2. In the procedure code, use the parameter name to assign a value to the local copy of the argument. The underlying value in the calling code is not changed.  
  
## <a name="example"></a>示例  
 The following example shows two procedures that take an array variable and operate on its elements. The `increase` procedure simply adds one to each element. The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#36)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41". Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.  
  
 The second `MsgBox` call displays "After replace(n): 101, 201, 301". Because `n` is passed `ByRef`, `replace` can modify the variable `n` in the calling code and assign a new array to it. Because `n` is a reference type, `replace` can also change its members.  
  
 You can prevent the procedure from modifying the variable itself in the calling code. See [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md).  
  
## <a name="compiling-the-code"></a>编译代码  
 When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.  
  
 The default in Visual Basic is to pass arguments by value. However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter. This makes your code easier to read.  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code. Make sure you expect this value to be changed, and be prepared to check it for validity before using it.  
  
## <a name="see-also"></a>请参阅

- [过程](./index.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [如何：将自变量传递给过程](./how-to-pass-arguments-to-a-procedure.md)
- [按值和按引用传递自变量](./passing-arguments-by-value-and-by-reference.md)
- [可修改和不可修改自变量之间的差异](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [通过值传递自变量和通过引用传递自变量之间的差异](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [如何：防止过程自变量的值被更改](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [如何：强制通过值传递自变量](./how-to-force-an-argument-to-be-passed-by-value.md)
- [按位置和按名称传递自变量](./passing-arguments-by-position-and-by-name.md)
- [值类型和引用类型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
