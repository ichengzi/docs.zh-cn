---
title: Me、My、MyBase 和 MyClass
ms.date: 07/20/2015
f1_keywords:
- MyClass
- vb.Me
- MyBase
- vb.MyBase
- Me
- vb.MyClass
- vb.This
- vb.My
helpviewer_keywords:
- My object
- self-reference [Visual Basic], Me keyword
- MyClass keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], referring to the current instance of an object
- Me keyword [Visual Basic]
- self-reference
- current instance [Visual Basic], Me keyword
- MyBase keyword [Visual Basic], relationship to similar programming elements
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
ms.openlocfilehash: a21dfeb12e8d99f5f8b8afede084846711c299ab
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347341"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Visual Basic 中的 Me、My、MyBase 和 MyClass
`Me`, `My`, `MyBase`, and `MyClass` in Visual Basic have similar names, but different purposes. This topic describes each of these entities in order to distinguish them.  
  
## <a name="me"></a>Me  
 The `Me` keyword provides a way to refer to the specific instance of a class or structure in which the code is currently executing. `Me` behaves like either an object variable or a structure variable referring to the current instance. Using `Me` is particularly useful for passing information about the currently executing instance of a class or structure to a procedure in another class, structure, or module.  
  
 For example, suppose you have the following procedure in a module.  
  
```vb  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 You can call this procedure and pass the current instance of the <xref:System.Windows.Forms.Form> class as an argument by using the following statement.  
  
```vb  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>My  
 The `My` feature provides easy and intuitive access to a number of .NET Framework classes, enabling the Visual Basic user to interact with the computer, application, settings, resources, and so on.  
  
## <a name="mybase"></a>MyBase  
 The `MyBase` keyword behaves like an object variable referring to the base class of the current instance of a class. `MyBase` is commonly used to access base class members that are overridden or shadowed in a derived class. `MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.  
  
## <a name="myclass"></a>MyClass  
 The `MyClass` keyword behaves like an object variable referring to the current instance of a class as originally implemented. `MyClass` is similar to `Me`, but all method calls on it are treated as if the method were `NotOverridable`.  
  
## <a name="see-also"></a>请参阅

- [继承的基础知识](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
