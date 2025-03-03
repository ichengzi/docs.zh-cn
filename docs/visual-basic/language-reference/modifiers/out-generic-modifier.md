---
title: Out（泛型修饰符）
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceOut
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
ms.openlocfilehash: 0460015b44971fa638dba47183690ffcc89ca55f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351423"
---
# <a name="out-generic-modifier-visual-basic"></a>Out（泛型修饰符）(Visual Basic)

For generic type parameters, the `Out` keyword specifies that the type is covariant.

## <a name="remarks"></a>备注

协变使你使用的类型可以比泛型参数指定的类型派生程度更大。 这样可以隐式转换实现变体接口的类以及隐式转换委托类型。

有关详细信息，请参阅[协变和逆变](../../programming-guide/concepts/covariance-contravariance/index.md)。

## <a name="rules"></a>规则

可以在泛型接口和委托中使用 `Out` 关键字。

在泛型接口中，如果类型参数满足以下条件，则可以声明为协变：

- 类型参数只用作接口方法的返回类型，而不用作方法参数的类型。

    > [!NOTE]
    > 此规则有一个例外。 如果在协变接口中将逆变泛型委托用作方法参数，则可以将协变类型用作此委托的泛型类型参数。 有关协变和逆变泛型委托的详细信息，请参阅[委托中的变体](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)和[对 Func 和 Action 泛型委托使用变体](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)。

- 类型参数不用作接口方法的泛型约束。

In a generic delegate, a type parameter can be declared covariant if it is used only as a method return type and not used for method arguments.

引用类型支持协变和逆变，但值类型不支持它们。

In Visual Basic, you cannot declare events in covariant interfaces without specifying the delegate type. Also, covariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.

## <a name="behavior"></a>行为

具有协变类型参数的接口使其方法返回的类型可以比类型参数指定的类型派生程度更大。 例如，因为在 .NET Framework 4 的 <xref:System.Collections.Generic.IEnumerable%601> 中，类型 T 是协变的，所以可以将 `IEnumerable(Of String)` 类型的对象分配给 `IEnumerable(Of Object)` 类型的对象，而无需使用任何特殊转换方法。

可以向协变委托分配相同类型的其他委托，不过要使用派生程度更大的泛型类型参数。

## <a name="example"></a>示例

下面的示例演示如何声明、扩展和实现协变泛型接口。 它还演示如何对实现协变接口的类使用隐式转换。

[!code-vb[vbVarianceKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#3)]

## <a name="example"></a>示例

以下示例演示如何声明、实例化和调用协变泛型委托。 It also shows how you can use implicit conversion for delegate types.

[!code-vb[vbVarianceKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#4)]

## <a name="see-also"></a>请参阅

- [泛型接口中的变体](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
