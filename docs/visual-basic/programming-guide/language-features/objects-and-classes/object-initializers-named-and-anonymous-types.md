---
title: 对象初始值设定项：命名类型和匿名类型
ms.date: 07/20/2015
f1_keywords:
- vb.ObjectInitializer
helpviewer_keywords:
- object initializers [Visual Basic]
- anonymous types [Visual Basic], object initializers
- initializing properties [Visual Basic]
- initializers [Visual Basic]
- named types [Visual Basic]
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
ms.openlocfilehash: 20e46d7ecc206abb28240075d9ec5f764ab78d01
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346135"
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a>对象初始值设定项：命名类型和匿名类型 (Visual Basic)
Object initializers enable you to specify properties for a complex object by using a single expression. They can be used to create instances of named types and of anonymous types.  
  
## <a name="declarations"></a>声明  
 Declarations of instances of named and anonymous types can look almost identical, but their effects are not the same. Each category has abilities and restrictions of its own. The following example shows a convenient way to declare and initialize an instance of a named class, `Customer`, by using an object initializer list. Notice that the name of the class is specified after the keyword `New`.  
  
 [!code-vb[VbVbalrObjectInit#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#1)]  
  
 An anonymous type has no usable name. Therefore an instantiation of an anonymous type cannot include a class name.  
  
 [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
 The requirements and results of the two declarations are not the same. For `namedCust`, a `Customer` class that has a `Name` property must already exist, and the declaration creates an instance of that class. For `anonymousCust`, the compiler defines a new class that has one property, a string called `Name`, and creates a new instance of that class.  
  
## <a name="named-types"></a>Named Types  
 Object initializers provide a simple way to call the constructor of a type and then set the values of some or all properties in a single statement. The compiler invokes the appropriate constructor for the statement: the parameterless constructor if no arguments are presented, or a parameterized constructor if one or more arguments are sent. After that, the specified properties are initialized in the order in which they are presented in the initializer list.  
  
 Each initialization in the initializer list consists of the assignment of an initial value to a member of the class. The names and data types of the members are determined when the class is defined. In the following examples, the `Customer` class must exist, and must have members named `Name` and `City` that can accept string values.  
  
 [!code-vb[VbVbalrObjectInit#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#3)]  
  
 Alternatively, you can obtain the same result by using the following code:  
  
 [!code-vb[VbVbalrObjectInit#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#4)]  
  
 Each of these declarations is equivalent to the following example, which creates a `Customer` object by using the parameterless constructor, and then specifies initial values for the `Name` and `City` properties by using a `With` statement.  
  
 [!code-vb[VbVbalrObjectInit#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#5)]  
  
 If the `Customer` class contains a parameterized constructor that enables you to send in a value for `Name`, for example, you can also declare and initialize a `Customer` object in the following ways:  
  
 [!code-vb[VbVbalrObjectInit#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#6)]  
  
 You do not have to initialize all properties, as the following code shows.  
  
 [!code-vb[VbVbalrObjectInit#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#7)]  
  
 However, the initialization list cannot be empty. Uninitialized properties retain their default values.  
  
### <a name="type-inference-with-named-types"></a>Type Inference with Named Types  
 You can shorten the code for the declaration of `cust1` by combining object initializers and local type inference. This enables you to omit the `As` clause in the variable declaration. The data type of the variable is inferred from the type of the object that is created by the assignment. In the following example, the type of `cust6` is `Customer`.  
  
 [!code-vb[VbVbalrObjectInit#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#8)]  
  
### <a name="remarks-about-named-types"></a>Remarks About Named Types  
  
- A class member cannot be initialized more than one time in the object initializer list. The declaration of `cust7` causes an error.  
  
     [!code-vb[VbVbalrObjectInit#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#9)]  
  
- A member can be used to initialize itself or another field. If a member is accessed before it has been initialized, as in the following declaration for `cust8`, the default value will be used. Remember that when a declaration that uses an object initializer is processed, the first thing that happens is that the appropriate constructor is invoked. After that, the individual fields in the initializer list are initialized. In the following examples, the default value for `Name` is assigned for `cust8`, and an initialized value is assigned in `cust9`.  
  
     [!code-vb[VbVbalrObjectInit#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#10)]  
  
     The following example uses the parameterized constructor from `cust3` and `cust4` to declare and initialize `cust10` and `cust11`.  
  
     [!code-vb[VbVbalrObjectInit#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#11)]  
  
- Object initializers can be nested. In the following example, `AddressClass` is a class that has two properties, `City` and `State`, and the `Customer` class has an `Address` property that is an instance of `AddressClass`.  
  
     [!code-vb[VbVbalrObjectInit#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#12)]  
  
- The initialization list cannot be empty.  
  
- The instance being initialized cannot be of type Object.  
  
- Class members being initialized cannot be shared members, read-only members, constants, or method calls.  
  
- Class members being initialized cannot be indexed or qualified. The following examples raise compiler errors:  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a>匿名类型  
 Anonymous types use object initializers to create instances of new types that you do not explicitly define and name. Instead, the compiler generates a type according to the properties you designate in the object initializer list. Because the name of the type is not specified, it is referred to as an *anonymous type*. For example, compare the following declaration to the earlier one for `cust6`.  
  
 [!code-vb[VbVbalrObjectInit#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#13)]  
  
 The only difference syntactically is that no name is specified after `New` for the data type. However, what happens is quite different. The compiler defines a new anonymous type that has two properties, `Name` and `City`, and creates an instance of it with the specified values. Type inference determines the types of `Name` and `City` in the example to be strings.  
  
> [!CAUTION]
> The name of the anonymous type is generated by the compiler, and may vary from compilation to compilation. Your code should not use or rely on the name of an anonymous type.  
  
 Because the name of the type is not available, you cannot use an `As` clause to declare `cust13`. Its type must be inferred. Without using late binding, this limits the use of anonymous types to local variables.  
  
 Anonymous types provide critical support for [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries. For more information about the use of anonymous types in queries, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) and [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
### <a name="remarks-about-anonymous-types"></a>Remarks About Anonymous Types  
  
- Typically, all or most of the properties in an anonymous type declaration will be key properties, which are indicated by typing the keyword `Key` in front of the property name.  
  
     [!code-vb[VbVbalrObjectInit#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#14)]  
  
     For more information about key properties, see [Key](../../../../visual-basic/language-reference/modifiers/key.md).  
  
- Like named types, initializer lists for anonymous type definitions must declare at least one property.  
  
     [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
- When an instance of an anonymous type is declared, the compiler generates a matching anonymous type definition. The names and data types of the properties are taken from the instance declaration, and are included by the compiler in the definition. The properties are not named and defined in advance, as they would be for a named type. Their types are inferred. You cannot specify the data types of the properties by using an `As` clause.  
  
- Anonymous types can also establish the names and values of their properties in several other ways. For example, an anonymous type property can take both the name and the value of a variable, or the name and value of a property of another object.  
  
     [!code-vb[VbVbalrObjectInit#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#15)]  
  
     For more information about the options for defining properties in anonymous types, see [How to: Infer Property Names and Types in Anonymous Type Declarations](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
## <a name="see-also"></a>请参阅

- [局部类型推理](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [匿名类型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Visual Basic 中的 LINQ 简介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [如何：推断匿名类型声明中的属性名和类型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [Key](../../../../visual-basic/language-reference/modifiers/key.md)
- [如何：使用对象初始值设定项声明对象](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
