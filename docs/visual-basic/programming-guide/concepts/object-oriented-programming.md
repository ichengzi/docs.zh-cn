---
title: Object-oriented programming
ms.date: 07/20/2015
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
ms.openlocfilehash: 3739919273f4cdd285d519c414c542f1a82a16d2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348163"
---
# <a name="object-oriented-programming-visual-basic"></a>Object-oriented programming (Visual Basic)

Visual Basic provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.

 “封装”意味着将一组相关属性、方法和其他成员视为一个单元或对象。

 “继承”描述基于现有类创建新类的能力。

 多态性意味着可以有多个可互换使用的类，即使每个类以不同方式实现相同属性或方法。

 本节介绍下列概念：

- [类和对象](#classes-and-objects)
  - [类成员](#class-members)
    - [Properties and fields](#properties-and-fields)
    - [方法](#methods)
    - [构造函数](#constructors)
    - [析构函数](#destructors)
    - [事件](#events)
    - [Nested classes](#nested-classes)
  - [Access modifiers and access levels](#access-modifiers-and-access-levels)
    - [Instantiating classes](#instantiating-classes)
    - [Shared classes and members](#shared-classes-and-members)
    - [匿名类型](#anonymous-types)
- [继承](#inheritance)
  - [Overriding members](#overriding-members)
- [接口](#interfaces)
- [泛型](#generics)
- [委托](#delegates)

## <a name="classes-and-objects"></a>类和对象

“类”和“对象”这两个术语有时互换使用，但实际上，类描述对象的“类型”，而对象是类的可用“实例”。 因此，创建对象的操作称为“实例化”。 如果使用蓝图类比，类是蓝图，对象就是基于该蓝图的建筑。

定义类：

```vb
Class SampleClass
End Class
```

Visual Basic also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.

定义结构：

```vb
Structure SampleStructure
End Structure
```

有关详细信息，请参见:

- [Class 语句](../../../visual-basic/language-reference/statements/class-statement.md)
- [Structure 语句](../../../visual-basic/language-reference/statements/structure-statement.md)

### <a name="class-members"></a>Class members

每个类都可以具有不同的“类成员”。类成员包括属性（用于描述类数据）、方法（用于定义类行为）和事件（用于在不同的类和对象之间提供通信）。

#### <a name="properties-and-fields"></a>Properties and fields

字段和属性表示对象包含的信息。 字段类似于变量，因为可以直接读取或设置它们。

定义字段：

```vb
Class SampleClass
    Public SampleField As String
End Class
```

属性具有 get 和 set 过程，它们对如何设置或返回值提供更多的控制。

Visual Basic allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.

定义自动实现的属性：

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

如果你需要执行一些其他操作来读取和写入属性值，请定义一个用于存储属性值的字段，并提供用于存储和检索该字段的基本逻辑：

```vb
Class SampleClass
    Private m_Sample As String
    Public Property Sample() As String
        Get
            ' Return the value stored in the field.
            Return m_Sample
        End Get
        Set(ByVal Value As String)
            ' Store the value in the field.
            m_Sample = Value
        End Set
    End Property
End Class
```

大多数属性的方法或过程都是既可以设置也可以获取属性值。 但你可以创建只读或只写属性来限制对它们的修改或读取。 在 Visual Basic 中，可以使用 `ReadOnly` 和 `WriteOnly` 关键字。 但是，自动实现的属性不能为只读或只写。

有关详细信息，请参见:

- [Property 语句](../../../visual-basic/language-reference/statements/property-statement.md)
- [Get 语句](../../../visual-basic/language-reference/statements/get-statement.md)
- [Set 语句](../../../visual-basic/language-reference/statements/set-statement.md)
- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)

#### <a name="methods"></a>方法

 “方法”是对象可以执行的操作。

> [!NOTE]
> 在 Visual Basic 中，方法的创建途径有两种：如果方法不返回值，可使用 `Sub` 语句；如果方法返回值，可使用 `Function` 语句。

定义类的方法：

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

对于同一方法，一个类可以有多个实现，也叫“重载”，这些实现的区别在于参数个数或参数类型的不同。

重载方法：

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

大多数情况下，方法是在类定义中声明的。 However, Visual Basic also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.

有关详细信息，请参见:

- [Function 语句](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub 语句](../../../visual-basic/language-reference/statements/sub-statement.md)
- [重载](../../../visual-basic/language-reference/modifiers/overloads.md)
- [扩展方法](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)

#### <a name="constructors"></a>构造函数

构造函数一种类方法，它们在创建给定类型的对象时自动执行。 构造函数通常用于初始化新对象的数据成员。 构造函数只能在创建类时运行一次。 此外，构造函数中的代码始终在类中所有其他代码之前运行。 但是，你可以按照为任何其他方法创建重载的方式，创建多个构造函数重载。

定义类的构造函数：

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class
```

For more information, see: [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).

#### <a name="destructors"></a>析构函数

析构函数用于析构类的实例。 在 .NET Framework 中，垃圾回收器自动管理应用程序中托管对象的内存分配和释放。 但是，你可能仍会需要析构函数来清理应用程序创建的所有非托管资源。 一个类只能有一个析构函数。

有关析构函数和 .NET Framework 垃圾回收的详细信息，请参阅[垃圾回收](../../../standard/garbage-collection/index.md)。

#### <a name="events"></a>事件

类或对象可以通过事件向其他类或对象通知发生的相关事情。 发送（或引发）事件的类称为“发行者”，接收（或处理）事件的类称为“订户”。 有关事件以及如何引发和处理事件的详细信息，请参阅[事件](../../../standard/events/index.md)。

- To declare events, use the [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).

- To raise events, use the [RaiseEvent Statement](../../../visual-basic/language-reference/statements/raiseevent-statement.md).

- To specify event handlers using a declarative way, use the [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) statement and the [Handles](../../../visual-basic/language-reference/statements/handles-clause.md) clause.

- To be able to dynamically add, remove, and change the event handler associated with an event, use the [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md) and [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) together with the [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md).

#### <a name="nested-classes"></a>Nested classes

在另一个类中定义的类称为“嵌套”。 默认情况下，嵌套类是私有类。

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

若要创建嵌套类的实例，请使用容器类的名称，后接一个点，再接嵌套类的名称：

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a>Access modifiers and access levels

所有类和类方法都可以使用“访问修饰符”指定自己为其他类提供的访问级别。

可用的访问修饰符有以下这些：

|Visual Basic 修饰符|定义|
|---------------------------|----------------|
|[COMClassAttribute](../../../visual-basic/language-reference/modifiers/public.md)|同一程序集中的任何其他代码或引用该程序集的其他程序集都可以访问该类型或成员。|
|[Private](../../../visual-basic/language-reference/modifiers/private.md)|只有同一类中的代码可以访问该类型或成员。|
|[Protected](../../../visual-basic/language-reference/modifiers/protected.md)|只有同一类或派生类中的代码可以访问该类型或成员。|
|[Friend](../../../visual-basic/language-reference/modifiers/friend.md)|同一程序集中的任何代码都可以访问该类型或成员，但其他程序集中的代码不可以。|
|`Protected Friend`|同一程序集中的任何代码或其他程序集中的任何派生类都可以访问该类型或成员。|

For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

### <a name="instantiating-classes"></a>Instantiating classes

若要创建对象，你需要实例化类，即创建类实例。

```vb
Dim sampleObject as New SampleClass()
```

实例化类之后，可以为该实例的属性和字段赋值，还可以调用类方法。

```vb
' Set a property value.
sampleObject.SampleProperty = "Sample String"
' Call a method.
sampleObject.SampleMethod()
```

若要在类的实例化过程中为属性赋值，请使用对象初始值设定项：

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

有关详细信息，请参见:

- [New 运算符](../../../visual-basic/language-reference/operators/new-operator.md)
- [对象初始值设定项：命名类型和匿名类型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

### <a name="shared-classes-and-members"></a>Shared classes and members

 A shared member of the class is a property, procedure, or field that is shared by all instances of a class.

 To define a shared member:

```vb
Class SampleClass
    Public Shared SampleString As String = "Sample String"
End Class
```

 To access the shared member, use the name of the class without creating an object of this class:

```vb
MsgBox(SampleClass.SampleString)
```

 Shared modules in Visual Basic have shared members only and cannot be instantiated. Shared members also cannot access non-shared properties, fields or methods

 有关详细信息，请参见:

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Module 语句](../../../visual-basic/language-reference/statements/module-statement.md)

### <a name="anonymous-types"></a>匿名类型

匿名类型使你无需为数据类型编写类定义即可创建对象。 此时，编译器将为你生成类。 该类没有可使用的名称，且包含在声明对象时指定的属性。

创建匿名类型的实例：

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

有关详细信息，请参阅：[匿名类型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。

## <a name="inheritance"></a>继承

通过继承，可以创建一个新类，它重用、扩展和修改另一个类中定义的行为。 其成员被继承的类称为“基类”，继承这些成员的类称为“派生类”。 However, all classes in Visual Basic implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.

> [!NOTE]
> Visual Basic doesn't support multiple inheritance. 即，只能为一个派生类指定一个基类。

从基类继承：

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

默认情况下，可以继承所有类。 但你可以指定不得将某个类用作基类，也可以创建只能用作基类的类。

指定不得将某个类用作基类：

```vb
NotInheritable Class SampleClass
End Class
```

指定只能用作基类且无法实例化的类：

```vb
MustInherit Class BaseClass
End Class
```

有关详细信息，请参见:

- [Inherits 语句](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a>Overriding members

默认情况下，派生类继承其基类的所有成员。 若希望更改继承成员的行为，则需要重写该成员。 即，可以在派生类中定义方法、属性或事件的新实现。

下列修饰符用于控制如何重写属性和方法：

|Visual Basic 修饰符|定义|
|---------------------------|----------------|
|[Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)|允许在派生类中重写类成员。|
|[Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)|重写基类中定义的虚拟（可重写）成员。|
|[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)|禁止在继承类中重写成员。|
|[New](../../../visual-basic/language-reference/modifiers/mustoverride.md)|要求在派生类中重写类成员。|
|[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)|隐藏继承自基类的成员|

## <a name="interfaces"></a>接口

和类一样，接口也定义了一系列属性、方法和事件。 但与类不同的是，接口并不提供实现。 它们由类来实现，并从类中被定义为单独的实体。 接口表示一种约定，实现接口的类必须严格按其定义来实现接口的每个方面。

定义接口：

```vb
Public Interface ISampleInterface
    Sub DoSomething()
End Interface
```

在类中实现接口：

```vb
Class SampleClass
    Implements ISampleInterface
    Sub DoSomething
        ' Method implementation.
    End Sub
End Class
```

有关详细信息，请参见:

- [接口](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [Interface 语句](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Implements 语句](../../../visual-basic/language-reference/statements/implements-statement.md)

## <a name="generics"></a>泛型

Classes, structures, interfaces and methods in .NET can include *type parameters* that define types of objects that they can store or use. 最常见的泛型示例是集合，从中可以指定要存储在集合中的对象的类型。

定义泛型类：

```vb
Class SampleGeneric(Of T)
    Public Field As T
End Class
```

创建泛型类的实例：

```vb
Dim sampleObject As New SampleGeneric(Of String)
sampleObject.Field = "Sample string"
```

有关详细信息，请参见:

- [泛型](../../../standard/generics/index.md)
- [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)

## <a name="delegates"></a>委托

 “委托”是一种类型，它定义方法签名，可以提供对具有兼容签名的任何方法的引用。 你可以通过委托调用方法。 委托用于将方法作为参数传递给其他方法。

> [!NOTE]
> 事件处理程序就是通过委托调用的方法。 有关在事件处理中使用委托的详细信息，请参阅[事件](../../../standard/events/index.md)。

创建委托：

```vb
Delegate Sub SampleDelegate(ByVal str As String)
```

创建对与委托指定的签名相匹配的方法的引用：

```vb
Class SampleClass
    ' Method that matches the SampleDelegate signature.
    Sub SampleSub(ByVal str As String)
        ' Add code here.
    End Sub
    ' Method that instantiates the delegate.
    Sub SampleDelegateSub()
        Dim sd As SampleDelegate = AddressOf SampleSub
        sd("Sample string")
    End Sub
End Class
```

有关详细信息，请参见:

- [委托](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Delegate 语句](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [AddressOf 运算符](../../../visual-basic/language-reference/operators/addressof-operator.md)

## <a name="see-also"></a>请参阅

- [Visual Basic 编程指南](../../../visual-basic/programming-guide/index.md)
