---
title: Class 语句
ms.date: 05/12/2018
f1_keywords:
- vb.Class
helpviewer_keywords:
- class modules
- Class statement [Visual Basic]
- classes [Visual Basic], fields
- fields [Visual Basic], of classes
- class types [Visual Basic], class statements
- classes [Visual Basic], creating
- classes [Visual Basic], data members
- data members [Visual Basic], of classes
ms.assetid: f2664f38-eb5a-4d4b-a374-1d041521fb6c
ms.openlocfilehash: 3cb276f134e90ce3b3009234eb980d89477e0d09
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354151"
---
# <a name="class-statement-visual-basic"></a>Class 语句 (Visual Basic)
Declares the name of a class and introduces the definition of the variables, properties, events, and procedures that the class comprises.  
  
## <a name="syntax"></a>语法  
  
```vb  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] [ Partial ] _  
Class name [ ( Of typelist ) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ statements ]  
End Class  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`attributelist`|可选。 See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|可选。 可以是以下各项之一：<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md)<br />-   [Protected Friend](../../language-reference/modifiers/protected-friend.md)<br />- [Private Protected](../../language-reference/modifiers/private-protected.md)<br/><br/> 请参阅 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。|  
|`Shadows`|可选。 See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|可选。 See [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|可选。 See [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`Partial`|可选。 Indicates a partial definition of the class. See [Partial](../../../visual-basic/language-reference/modifiers/partial.md).|  
|`name`|必须的。 Name of this class. 请参阅 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|  
|`Of`|可选。 Specifies that this is a generic class.|  
|`typelist`|Required if you use the [Of](../../../visual-basic/language-reference/statements/of-clause.md) keyword. List of type parameters for this class. See [Type List](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|可选。 Indicates that this class inherits the members of another class. See [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|Required if you use the `Inherits` statement. The name of the class from which this class derives.|  
|`Implements`|可选。 Indicates that this class implements the members of one or more interfaces. See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Required if you use the `Implements` statement. The names of the interfaces this class implements.|  
|`statements`|可选。 Statements which define the members of this class.|  
|`End Class`|必须的。 Terminates the `Class` definition.|  
  
## <a name="remarks"></a>备注  
 A `Class` statement defines a new data type. A *class* is a fundamental building block of object-oriented programming (OOP). For more information, see [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
 You can use `Class` only at namespace or module level. This means the *declaration context* for a class must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure or block. 有关详细信息，请参阅[声明上下文和默认访问级别](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 Each instance of a class has a lifetime independent of all other instances. This lifetime begins when it is created by a [New Operator](../../../visual-basic/language-reference/operators/new-operator.md) clause or by a function such as <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>. It ends when all variables pointing to the instance have been set to [Nothing](../../../visual-basic/language-reference/nothing.md) or to instances of other classes.  
  
 Classes default to [Friend](../../../visual-basic/language-reference/modifiers/friend.md) access. You can adjust their access levels with the access modifiers. For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>规则  
  
- **Nesting.** You can define one class within another. The outer class is called the *containing class*, and the inner class is called a *nested class*.  
  
- **继承。** If the class uses the [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md), you can specify only one base class or interface. A class cannot inherit from more than one element.  
  
     A class cannot inherit from another class with a more restrictive access level. For example, a `Public` class cannot inherit from a `Friend` class.  
  
     A class cannot inherit from a class nested within it.  
  
- **Implementation.** If the class uses the [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md), you must implement every member defined by every interface you specify in `interfacenames`. An exception to this is reimplementation of a base class member. For more information, see "Reimplementation" in [Implements](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
- **Default Property.** A class can specify at most one property as its *default property*. For more information, see [Default](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>行为  
  
- **Access Level.** Within a class, you can declare each member with its own access level. Class members default to [Public](../../../visual-basic/language-reference/modifiers/public.md) access, except variables and constants, which default to [Private](../../../visual-basic/language-reference/modifiers/private.md) access. When a class has more restricted access than one of its members, the class access level takes precedence.  
  
- **Scope.** A class is in scope throughout its containing namespace, class, structure, or module.  
  
     The scope of every class member is the entire class.  
  
     **Lifetime.** Visual Basic does not support static classes. The functional equivalent of a static class is provided by a module. For more information, see [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Class members have lifetimes depending on how and where they are declared. For more information, see [Lifetime in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
- **Qualification.** Code outside a class must qualify a member's name with the name of that class.  
  
     If code inside a nested class makes an unqualified reference to a programming element, Visual Basic searches for the element first in the nested class, then in its containing class, and so on out to the outermost containing element.  
  
## <a name="classes-and-modules"></a>Classes and Modules  
 These elements have many similarities, but there are some important differences as well.  
  
- **Terminology.** Previous versions of Visual Basic recognize two types of modules: *class modules* (.cls files) and *standard modules* (.bas files). The current version calls these *classes* and *modules*, respectively.  
  
- **Shared Members.** You can control whether a member of a class is a shared or instance member.  
  
- **Object Orientation.** Classes are object-oriented, but modules are not. You can create one or more instances of a class. For more information, see [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="example"></a>示例  
 The following example uses a `Class` statement to define a class and several members.  
  
 [!code-vb[VbVbalrStatements#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#62)]  
  
## <a name="see-also"></a>请参阅

- [对象和类](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [结构和类](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Interface 语句](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Module 语句](../../../visual-basic/language-reference/statements/module-statement.md)
- [Property 语句](../../../visual-basic/language-reference/statements/property-statement.md)
- [对象生存期：如何创建和销毁对象](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [如何：使用泛型类](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
