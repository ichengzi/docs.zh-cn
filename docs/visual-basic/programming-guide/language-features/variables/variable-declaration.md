---
title: 变量声明
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], declaring
- member variables [Visual Basic], declarations
- Dim statement [Visual Basic], variable declaration
- declaring variables [Visual Basic]
- variables [Visual Basic], scope
- variables [Visual Basic], data types
- data types [Visual Basic], variable declarations
- lifetime [Visual Basic], variables
- variables [Visual Basic], lifetime
- access levels [Visual Basic], variables
- scope [Visual Basic], declaration statements
- variables [Visual Basic], access level
- local variables [Visual Basic], declarations
- scope [Visual Basic], variables
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
ms.openlocfilehash: b89773e9527af0d65cde53b61654f2511f5c8dde
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351766"
---
# <a name="variable-declaration-in-visual-basic"></a>Visual Basic 中的变量声明
You declare a variable to specify its name and characteristics. The declaration statement for variables is the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md). Its location and contents determine the variable's characteristics.  
  
 For variable naming rules and considerations, see [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="declaration-levels"></a>Declaration Levels  
  
### <a name="local-and-member-variables"></a>Local and Member Variables  
 A *local variable* is one that is declared within a procedure. A *member variable* is a member of a Visual Basic type; it is declared at module level, inside a class, structure, or module, but not within any procedure internal to that class, structure, or module.  
  
### <a name="shared-and-instance-variables"></a>Shared and Instance Variables  
 In a class or structure, the category of a member variable depends on whether or not it is shared. If it is declared with the [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) keyword, it is a *shared variable*, and it exists in a single copy shared among all instances of the class or structure.  
  
 Otherwise it is an *instance variable*, and a separate copy of it is created for each instance of the class or structure. A given copy of an instance variable is available only to the instance of the class or structure in which it was created. It is independent of a copy of the instance variable in any other instance of the class or structure.  
  
## <a name="declaring-data-type"></a>Declaring Data Type  
 The [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause in the declaration statement allows you to define the data type or object type of the variable you are declaring. You can specify any of the following types for a variable:  
  
- An elementary data type, such as `Boolean`, `Long`, or `Decimal`  
  
- A composite data type, such as an array or structure  
  
- An object type, or class, defined either in your application or in another application  
  
- A .NET Framework class, such as <xref:System.Windows.Forms.Label> or <xref:System.Windows.Forms.TextBox>  
  
- An interface type, such as <xref:System.IComparable> or <xref:System.IDisposable>  
  
 You can declare several variables in one statement without having to repeat the data type. In the following statements, the variables `i`, `j`, and `k` are declared as type `Integer`, `l` and `m` as `Long`, and `x` and `y` as `Single`:  
  
```vb  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 For more information on data types, see [Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md). For more information on objects, see [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) and [Programming with Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).  
  
## <a name="local-type-inference"></a>局部类型推理  
 *Type inference* is used to determine the data types of local variables declared without an `As` clause. The compiler infers the type of the variable from the type of the initialization expression. This enables you to declare variables without explicitly stating a type. In the following example, both `num1` and `num2` are strongly typed as integers.  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
  
 If you want to use local type inference, `Option Infer` must be set to `On`. 有关详细信息，请参阅[本地类型推断](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)和 [Option Infer 语句](../../../../visual-basic/language-reference/statements/option-infer-statement.md)。  
  
## <a name="characteristics-of-declared-variables"></a>Characteristics of Declared Variables  
 The *lifetime* of a variable is the period of time during which it is available for use. In general, a variable exists as long as the element that declares it (such as a procedure or class) continues to exist. If the variable does not need to continue existing beyond the lifetime of its containing element, you do not need to do anything special in the declaration. If the variable needs to continue to exist longer than its containing element, you can include the `Static` or `Shared` keyword in its `Dim` statement. For more information, see [Lifetime in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
 The *scope* of a variable is the set of all code that can refer to it without qualifying its name. A variable's scope is determined by where it is declared. Code located in a given region can use the variables defined in that region without having to qualify their names. 有关详细信息，请参阅 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)。  
  
 A variable's *access level* is the extent of code that has permission to access it. This is determined by the access modifier (such as [Public](../../../../visual-basic/language-reference/modifiers/public.md) or [Private](../../../../visual-basic/language-reference/modifiers/private.md)) that you use in the `Dim` statement. For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>请参阅

- [如何：创建新变量](../../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md)
- [如何：将数据移入和移出变量](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)
- [数据类型](../../../../visual-basic/language-reference/data-types/index.md)
- [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)
- [Static](../../../../visual-basic/language-reference/modifiers/static.md)
- [已声明元素的特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [局部类型推理](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Infer 语句](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
