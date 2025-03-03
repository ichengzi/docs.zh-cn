---
title: 生存期
ms.date: 07/20/2015
helpviewer_keywords:
- static variables [Visual Basic], lifetime
- static variables [Visual Basic], Visual Basic
- declared elements [Visual Basic], lifetime
- Shared variable lifetime [Visual Basic]
- lifetime [Visual Basic], declared elements
- lifetime [Visual Basic], Visual Basic
- lifetime [Visual Basic]
ms.assetid: bd91e390-690a-469a-9946-8dca70bc14e7
ms.openlocfilehash: 05a39388e8aa9681af60cf86a3df8346d744b69e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345314"
---
# <a name="lifetime-in-visual-basic"></a>Visual Basic 中的生存期
The *lifetime* of a declared element is the period of time during which it is available for use. Variables are the only elements that have lifetime. For this purpose, the compiler treats procedure parameters and function returns as special cases of variables. The lifetime of a variable represents the period of time during which it can hold a value. Its value can change over its lifetime, but it always holds some value.  
  
## <a name="different-lifetimes"></a>Different Lifetimes  
 A *member variable* (declared at module level, outside any procedure) typically has the same lifetime as the element in which it is declared. A nonshared variable declared in a class or structure exists as a separate copy for each instance of the class or structure in which it is declared. Each such variable has the same lifetime as its instance. However, a `Shared` variable has only a single lifetime, which lasts for the entire time your application is running.  
  
 A *local variable* (declared inside a procedure) exists only while the procedure in which it is declared is running. This applies also to that procedure's parameters and to any function return. However, if that procedure calls other procedures, the local variables retain their values while the called procedures are running.  
  
## <a name="beginning-of-lifetime"></a>Beginning of Lifetime  
 A local variable's lifetime begins when control enters the procedure in which it is declared. Every local variable is initialized to the default value for its data type as soon as the procedure begins running. When the procedure encounters a `Dim` statement that specifies initial values, it sets those variables to those values, even if your code had already assigned other values to them.  
  
 Each member of a structure variable is initialized as if it were a separate variable. Similarly, each element of an array variable is initialized individually.  
  
 Variables declared within a block inside a procedure (such as a `For` loop) are initialized on entry to the procedure. These initializations take effect whether or not your code ever executes the block.  
  
## <a name="end-of-lifetime"></a>End of Lifetime  
 When a procedure terminates, the values of its local variables are not preserved, and Visual Basic reclaims their memory. The next time you call the procedure, all its local variables are created afresh and reinitialized.  
  
 When an instance of a class or structure terminates, its nonshared variables lose their memory and their values. Each new instance of the class or structure creates and reinitializes its nonshared variables. However, `Shared` variables are preserved until your application stops running.  
  
## <a name="extension-of-lifetime"></a>Extension of Lifetime  
 If you declare a local variable with the `Static` keyword, its lifetime is longer than the execution time of its procedure. The following table shows how the procedure declaration determines how long a `Static` variable exists.  
  
|Procedure location and sharing|Static variable lifetime begins|Static variable lifetime ends|  
|------------------------------------|-------------------------------------|-----------------------------------|  
|In a module (shared by default)|The first time the procedure is called|When your application stops running|  
|In a class, `Shared` (procedure is not an instance member)|The first time the procedure is called either on a specific instance or on the class or structure name itself|When your application stops running|  
|In an instance of a class, not `Shared` (procedure is an instance member)|The first time the procedure is called on the specific instance|When the instance is released for garbage collection (GC)|  
  
## <a name="static-variables-of-the-same-name"></a>Static Variables of the Same Name  
 You can declare static variables with the same name in more than one procedure. If you do this, the Visual Basic compiler considers each such variable to be a separate element. The initialization of one of these variables does not affect the values of the others. The same applies if you define a procedure with a set of overloads and declare a static variable with the same name in each overload.  
  
## <a name="containing-elements-for-static-variables"></a>Containing Elements for Static Variables  
 You can declare a static local variable within a class, that is, inside a procedure in that class. However, you cannot declare a static local variable within a structure, either as a structure member or as a local variable of a procedure within that structure.  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 The following example declares a variable with the [Static](../../../../visual-basic/language-reference/modifiers/static.md) keyword. (Note that you do not need the `Dim` keyword when the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) uses a modifier such as `Static`.)  
  
### <a name="code"></a>代码  
 [!code-vb[VbVbalrKeywords#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#13)]  
  
### <a name="comments"></a>注释  
 In the preceding example, the variable `applesSold` continues to exist after the procedure `runningTotal` returns to the calling code. The next time `runningTotal` is called, `applesSold` retains its previously calculated value.  
  
 If `applesSold` had been declared without using `Static`, the previous accumulated values would not be preserved across calls to `runningTotal`. The next time `runningTotal` was called, `applesSold` would have been recreated and initialized to 0, and `runningTotal` would have simply returned the same value with which it was called.  
  
### <a name="compiling-the-code"></a>编译代码  
 You can initialize the value of a static local variable as part of its declaration. If you declare an array to be `Static`, you can initialize its rank (number of dimensions), the length of each dimension, and the values of the individual elements.  
  
### <a name="security"></a>安全  
 In the preceding example, you can produce the same lifetime by declaring `applesSold` at module level. If you changed the scope of a variable this way, however, the procedure would no longer have exclusive access to it. Because other procedures could access `applesSold` and change its value, the running total could be unreliable and the code could be more difficult to maintain.  
  
## <a name="see-also"></a>请参阅

- [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
- [已声明的元素名称](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [对已声明元素的引用](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [变量](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [变量声明](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [数据类型疑难解答](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Static](../../../../visual-basic/language-reference/modifiers/static.md)
