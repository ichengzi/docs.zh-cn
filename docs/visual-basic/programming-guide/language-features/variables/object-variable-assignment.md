---
title: 对象变量赋值
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], object variable assignment
- object variables [Visual Basic], initializing
- variables [Visual Basic], initializing
- objects [Visual Basic], current instance
- object variables [Visual Basic], assigning
- variables [Visual Basic], object variables
- current instance [Visual Basic], defined
- variables [Visual Basic], assigning
- assignment statements [Visual Basic], object variable assignment
- Me keyword [Visual Basic], as object variable
ms.assetid: 3706811d-fd40-44fe-8727-d692e8e55d6d
ms.openlocfilehash: 93de17490935d6d5cad01000e9ee3e2fe55bd16c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351819"
---
# <a name="object-variable-assignment-visual-basic"></a>对象变量赋值 (Visual Basic)

You use a normal assignment statement to assign an object to an object variable. You can assign an object expression or the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, as the following example illustrates.

```vb
Dim thisObject As Object
' The following statement assigns an object reference.
thisObject = Form1
' The following statement discontinues association with any object.
thisObject = Nothing
```

`Nothing` means there is no object currently assigned to the variable.

## <a name="initialization"></a>初始化

When your code begins running, your object variables are initialized to `Nothing`. Those whose declarations include initialization are reinitialized to the values you specify when the declaration statements are executed.

You can include initialization in your declaration by using the [New](../../../../visual-basic/language-reference/operators/new-operator.md) keyword. The following declaration statements declare object variables `testUri` and `ver` and assign specific objects to them. Each uses one of the overloaded constructors of the appropriate class to initialize the object.

```vb
Dim testUri As New System.Uri("https://www.microsoft.com")
Dim ver As New System.Version(6, 1, 0)
```

## <a name="disassociation"></a>Disassociation

Setting an object variable to `Nothing` discontinues the association of the variable with any specific object. This prevents you from accidentally changing the object by changing the variable. It also allows you to test whether the object variable points to a valid object, as the following example shows.

```vb
If otherObject IsNot Nothing Then
    ' otherObject refers to a valid object, so your code can use it.
End If
```

If the object your variable refers to is in another application, this test cannot determine whether that application has terminated or just invalidated the object.

An object variable with a value of `Nothing` is also called a *null reference*.

## <a name="current-instance"></a>Current Instance

The *current instance* of an object is the one in which the code is currently executing. Since all code executes inside a procedure, the current instance is the one in which the procedure was invoked.

The `Me` keyword acts as an object variable referring to the current instance. If a procedure is not [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), it can use the `Me` keyword to obtain a pointer to the current instance. Shared procedures cannot be associated with a specific instance of a class.

Using `Me` is particularly useful for passing the current instance to a procedure in another module. For example, suppose you have a number of XML documents and wish to add some standard text to all of them. The following example defines a procedure to do this.

```vb
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)
    XmlDoc.CreateTextNode("This text goes into every XML document.")
End Sub
```

Every XML document object could then call the procedure and pass its current instance as an argument. 下面的示例演示这一操作。

```vb
addStandardText(Me)
```

## <a name="see-also"></a>请参阅

- [对象变量](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [对象变量声明](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [对象变量值](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [How to: Declare an Object Variable and Assign an Object to It in Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [如何：使对象变量不引用任何实例](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)
- [Me、My、MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
