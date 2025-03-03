---
title: 早期绑定和后期绑定
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- objects [Visual Basic], late-bound
- objects [Visual Basic], early-bound
- objects [Visual Basic], late bound
- early binding [Visual Basic], Visual Basic compiler
- binding [Visual Basic], late and early
- objects [Visual Basic], early bound
- Visual Basic compiler, early and late binding
- late binding [Visual Basic]
- late binding [Visual Basic], Visual Basic compiler
ms.assetid: d6ff7f1e-b94f-4205-ab8d-5cfa91758724
ms.openlocfilehash: bd70d8642c18e9bc2baba8128ec908c88e0477ce
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345186"
---
# <a name="early-and-late-binding-visual-basic"></a>早期绑定和后期绑定 (Visual Basic)
The Visual Basic compiler performs a process called `binding` when an object is assigned to an object variable. 如果对象被分配给声明为特定对象类型的变量，就是*早期绑定*对象。 借助早期绑定对象，编译器可以在应用程序执行前分配内存并执行其他优化。 例如，下面的代码片段将变量声明为类型 <xref:System.IO.FileStream>：  
  
 [!code-vb[VbVbalrOOP#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#90)]  
  
 由于 <xref:System.IO.FileStream> 是特定对象类型，因此分配给 `FS` 的实例就是早期绑定对象。  
  
 相反，如果对象被分配给声明为 `Object` 类型的变量，就是*晚期绑定*对象。 虽然这种类型的对象可保留对任何对象的引用，但却没有早期绑定对象的诸多优点。 例如，下面的代码片段将对象变量声明为保留 `CreateObject` 函数返回的对象：  
  
 [!code-vb[VbVbalrOOP#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/LateBinding.vb#91)]  
  
## <a name="advantages-of-early-binding"></a>早期绑定的优点  
 应尽量使用早期绑定对象，因为这样编译器可以执行重要优化，从而大大提升应用程序的工作效率。 早期绑定对象的速度远超晚期绑定对象，并明确指出在使用的对象类型，使得代码更易于阅读和维护。 Another advantage to early binding is that it enables useful features such as automatic code completion and Dynamic Help because the Visual Studio integrated development environment (IDE) can determine exactly what type of object you are working with as you edit the code. 早期绑定降低了运行时错误的数量和严重性，因为它允许编译器在编译程序时报告错误。  
  
> [!NOTE]
> 晚期绑定只能用于访问声明为 `Public` 的类型成员。 访问声明为 `Friend` 或 `Protected Friend` 的成员会导致生成运行时错误。  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>
- [对象生存期：如何创建和销毁对象](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Object 数据类型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
