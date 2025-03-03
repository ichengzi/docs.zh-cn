---
title: ReadOnly
ms.date: 07/20/2015
f1_keywords:
- vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
ms.openlocfilehash: 8c7e7e7c1571fd7c595ebfd54fb5767078ef41f8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351280"
---
# <a name="readonly-visual-basic"></a>ReadOnly (Visual Basic)
Specifies that a variable or property can be read but not written.

## <a name="remarks"></a>备注

## <a name="rules"></a>规则

- **Declaration Context.** 只能在模块级别使用 `ReadOnly`。 This means the declaration context for a `ReadOnly` element must be a class, structure, or module, and cannot be a source file, namespace, or procedure.

- **Combined Modifiers.** You cannot specify `ReadOnly` together with `Static` in the same declaration.

- **Assigning a Value.** Code consuming a `ReadOnly` property cannot set its value. But code that has access to the underlying storage can assign or change the value at any time.

     You can assign a value to a `ReadOnly` variable only in its declaration or in the constructor of a class or structure in which it is defined.

## <a name="when-to-use-a-readonly-variable"></a>When to Use a ReadOnly Variable

There are situations in which you cannot use a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value. For example, the `Const` statement might not accept the data type you want to assign, or you might not be able to compute the value at compile time with a constant expression. You might not even know the value at compile time. In these cases, you can use a `ReadOnly` variable to hold a constant value.

> [!IMPORTANT]
> If the data type of the variable is a reference type, such as an array or a class instance, its members can be changed even if the variable itself is `ReadOnly`. 下面的示例阐释了这一点。

```vb
ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}
Sub ChangeArrayElement()
    characterArray(1) = "M"c
End Sub
```

When initialized, the array pointed to by `characterArray()` holds "x", "y", and "z". Because the variable `characterArray` is `ReadOnly`, you cannot change its value once it is initialized; that is, you cannot assign a new array to it. However, you can change the values of one or more of the array members. Following a call to the procedure `ChangeArrayElement`, the array pointed to by `characterArray()` holds "x", "M", and "z".

Note that this is similar to declaring a procedure parameter to be [ByVal](byval.md), which prevents the procedure from changing the calling argument itself but allows it to change its members.

## <a name="example"></a>示例

The following example defines a `ReadOnly` property for the date on which an employee was hired. The class stores the property value internally as a `Private` variable, and only code inside the class can change that value. However, the property is `Public`, and any code that can access the class can read the property.

[!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]

`ReadOnly` 修饰符可用于下面的上下文中：

- [Dim 语句](../statements/dim-statement.md)
- [Property 语句](../statements/property-statement.md)

## <a name="see-also"></a>请参阅

- [WriteOnly](writeonly.md)
- [关键字](../keywords/index.md)
