---
title: Const 语句
ms.date: 05/12/2018
f1_keywords:
- vb.Const
helpviewer_keywords:
- Const statement [Visual Basic]
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
ms.openlocfilehash: 1411e019058e7aac8249b7a50ecd295885a74177
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354129"
---
# <a name="const-statement-visual-basic"></a>Const 语句 (Visual Basic)

Declares and defines one or more constants.

## <a name="syntax"></a>语法

```vb
[ <attributelist> ] [ accessmodifier ] [ Shadows ]
Const constantlist
```

## <a name="parts"></a>部件

`attributelist`  
可选。 List of attributes that apply to all the constants declared in this statement. See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").

`accessmodifier`  
可选。 Use this to specify what code can access these constants. Can be [Public](../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), [Protected Friend](../modifiers/protected-friend.md), [Private](../../../visual-basic/language-reference/modifiers/private.md), or [Private Protected](../../language-reference/modifiers/private-protected.md).

`Shadows`  
可选。 Use this to redeclare and hide a programming element in a base class. See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).

`constantlist`  
必须的。 List of constants being declared in this statement.

`constant` `[ ,` `constant` `... ]`

每个 `constant` 都具有以下语法和部件：

`constantname` `[ As` `datatype` `] =` `initializer`

|部件|描述|
|----------|-----------------|
|`constantname`|必须的。 Name of the constant. 请参阅 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|
|`datatype`|Required if `Option Strict` is `On`. Data type of the constant.|
|`initializer`|必须的。 Expression that is evaluated at compile time and assigned to the constant.|

## <a name="remarks"></a>备注

If you have a value that never changes in your application, you can define a named constant and use it in place of a literal value. A name is easier to remember than a value. You can define the constant just once and use it in many places in your code. If in a later version you need to redefine the value, the `Const` statement is the only place you need to make a change.

You can use `Const` only at module or procedure level. This means the *declaration context* for a variable must be a class, structure, module, procedure, or block, and cannot be a source file, namespace, or interface. 有关详细信息，请参阅[声明上下文和默认访问级别](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。

Local constants (inside a procedure) default to public access, and you cannot use any access modifiers on them. Class and module member constants (outside any procedure) default to private access, and structure member constants default to public access. You can adjust their access levels with the access modifiers.

## <a name="rules"></a>规则

- **Declaration Context.** A constant declared at module level, outside any procedure, is a *member constant*; it is a member of the class, structure, or module that declares it.

  A constant declared at procedure level is a *local constant*; it is local to the procedure or block that declares it.

- **Attributes.** You can apply attributes only to member constants, not to local constants. An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local constants.

- **Modifiers.** By default, all constants are `Shared`, `Static`, and `ReadOnly`. You cannot use any of these keywords when declaring a constant.

  At procedure level, you cannot use `Shadows` or any access modifiers to declare local constants.

- **Multiple Constants.** You can declare several constants in the same declaration statement, specifying the `constantname` part for each one. Multiple constants are separated by commas.

## <a name="data-type-rules"></a>Data Type Rules

- **Data Types.** The `Const` statement can declare the data type of a variable. You can specify any data type or the name of an enumeration.

- **Default Type.** If you do not specify `datatype`, the constant takes the data type of `initializer`. If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`. If neither `datatype` nor `initializer` is present, the data type defaults to `Object`.

- **Different Types.** You can specify different data types for different constants by using a separate `As` clause for each variable you declare. However, you cannot declare several constants to be of the same type by using a common `As` clause.

- **Initialization.** You must initialize the value of every constant in `constantlist`. You use `initializer` to supply an expression to be assigned to the constant. The expression can be any combination of literals, other constants that are already defined, and enumeration members that are already defined. You can use arithmetic and logical operators to combine such elements.

  You cannot use variables or functions in `initializer`. However, you can use conversion keywords such as `CByte` and `CShort`. You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.

## <a name="behavior"></a>行为

- **Scope.** Local constants are accessible only from within their procedure or block. Member constants are accessible from anywhere within their class, structure, or module.

- **Qualification.** Code outside a class, structure, or module must qualify a member constant's name with the name of that class, structure, or module. Code outside a procedure or block cannot refer to any local constants within that procedure or block.

## <a name="example"></a>示例

The following example uses the `Const` statement to declare constants for use in place of literal values.

[!code-vb[VbVbalrStatements#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#13)]

## <a name="example"></a>示例

If you define a constant with data type `Object`, the Visual Basic compiler gives it the type of `initializer`, instead of `Object`. In the following example, the constant `naturalLogBase` has the run-time type `Decimal`.

[!code-vb[VbVbalrStatements#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#87)]

The preceding example uses the <xref:System.Type.ToString%2A> method on the <xref:System.Type> object returned by the [GetType Operator](../../../visual-basic/language-reference/operators/gettype-operator.md), because <xref:System.Type> cannot be converted to `String` using `CStr`.

## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [Enum 语句](../../../visual-basic/language-reference/statements/enum-statement.md)
- [#Const 指令](../../../visual-basic/language-reference/directives/const-directive.md)
- [Dim 语句](../../../visual-basic/language-reference/statements/dim-statement.md)
- [ReDim 语句](../../../visual-basic/language-reference/statements/redim-statement.md)
- [隐式转换和显式转换](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [常量和枚举](../../../visual-basic/programming-guide/language-features/constants-enums/index.md)
- [常量和枚举](../../../visual-basic/language-reference/constants-and-enumerations.md)
- [类型转换函数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
