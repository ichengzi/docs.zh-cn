---
title: 如何：定义一个过程的多个版本
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: 83e96e271f6613aa325d59a0ca2fce9fc69fe059
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350492"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a>如何：定义一个过程的多个版本 (Visual Basic)
You can define a procedure in multiple versions by *overloading* it, using the same name but a different parameter list for each version. The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.  
  
 有关更多信息，请参见 [Procedure Overloading](./procedure-overloading.md)。  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a>To define multiple versions of a procedure  
  
1. Write a `Sub` or `Function` declaration statement for each version of the procedure you want to define. Use the same procedure name in every declaration.  
  
2. Precede the `Sub` or `Function` keyword in each declaration with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword. You can optionally omit `Overloads` in the declarations, but if you include it in any of the declarations, you must include it in every declaration.  
  
3. Following each declaration statement, write procedure code to handle the specific case where the calling code supplies arguments matching that version's parameter list. You do not have to test for which parameters the calling code has supplied. Visual Basic passes control to the matching version of your procedure.  
  
4. Terminate each version of the procedure with the `End Sub` or `End Function` statement as appropriate.  
  
## <a name="example"></a>示例  
 The following example defines a `Sub` procedure to post a transaction against a customer's balance. It uses the `Overloads` keyword to define two versions of the procedure, one that accepts the customer by name and the other by account number.  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
 The calling code can obtain the customer identification as either a `String` or an `Integer`, and then use the same calling statement in either case.  
  
 For information on how to call these versions of the `post` procedure, see [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md).  
  
## <a name="compiling-the-code"></a>编译代码  
 Make sure each of your overloaded versions has the same procedure name but a different parameter list.  
  
## <a name="see-also"></a>请参阅

- [过程](./index.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [过程疑难解答](./troubleshooting-procedures.md)
- [如何：重载带有可选参数的过程](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [如何：重载参数数量不确定的过程](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [重载过程注意事项](./considerations-in-overloading-procedures.md)
- [重载决策](./overload-resolution.md)
