---
title: 演练：用 COM 对象实现继承
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
ms.openlocfilehash: 209e1005b9f944bf4883e8406031fb17d4d60df1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347988"
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a>演练：用 COM 对象实现继承 (Visual Basic)

You can derive Visual Basic classes from `Public` classes in COM objects, even those created in earlier versions of Visual Basic. The properties and methods of classes inherited from COM objects can be overridden or overloaded just as properties and methods of any other base class can be overridden or overloaded. Inheritance from COM objects is useful when you have an existing class library that you do not want to recompile.

The following procedure shows how to use Visual Basic 6.0 to create a COM object that contains a class, and then use it as a base class.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a>To build the COM object that is used in this walkthrough

1. In Visual Basic 6.0, open a new ActiveX DLL project. A project named `Project1` is created. It has a class named `Class1`.

2. In the **Project Explorer**, right-click **Project1**, and then click **Project1 Properties**. The **Project Properties** dialog box is displayed.

3. On the **General** tab of the **Project Properties** dialog box, change the project name by typing `ComObject1` in the **Project Name** field.

4. In the **Project Explorer**, right-click `Class1`, and then click **Properties**. The **Properties** window for the class is displayed.

5. Change the `Name` property to `MathFunctions`.

6. In the **Project Explorer**, right-click `MathFunctions`, and then click **View Code**. The **Code Editor** is displayed.

7. Add a local variable to hold the property value:

    ```vb
    ' Local variable to hold property value
    Private mvarProp1 As Integer
    ```

8. Add Property `Let` and Property `Get` property procedures:

    ```vb
    Public Property Let Prop1(ByVal vData As Integer)
       'Used when assigning a value to the property.
       mvarProp1 = vData
    End Property
    Public Property Get Prop1() As Integer
       'Used when retrieving a property's value.
       Prop1 = mvarProp1
    End Property
    ```

9. Add a function:

    ```vb
    Function AddNumbers(
       ByVal SomeNumber As Integer,
       ByVal AnotherNumber As Integer) As Integer

       AddNumbers = SomeNumber + AnotherNumber
    End Function
    ```

10. Create and register the COM object by clicking **Make ComObject1.dll** on the **File** menu.

    > [!NOTE]
    > Although you can also expose a class created with Visual Basic as a COM object, it is not a true COM object and cannot be used in this walkthrough. For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).

## <a name="interop-assemblies"></a>Interop Assemblies

In the following procedure, you will create an interop assembly, which acts as a bridge between unmanaged code (such as a COM object) and the managed code Visual Studio uses. The interop assembly that Visual Basic creates handles many of the details of working with COM objects, such as *interop marshaling*, the process of packaging parameters and return values into equivalent data types as they move to and from COM objects. The reference in the Visual Basic application points to the interop assembly, not the actual COM object.

### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a>To use a COM object with Visual Basic 2005 and later versions

1. 打开一个新的 Visual Basic Windows 应用程序项目。

2. 在“项目”菜单上，单击“添加引用”。

     “添加引用”对话框随即显示。

3. On the **COM** tab, double-click `ComObject1` in the **Component Name** list and click **OK**.

4. 在 **“项目”** 菜单上，单击 **“添加新项”** 。

     随即出现“添加新项”对话框。

5. In the **Templates** pane, click **Class**.

     The default file name, `Class1.vb`, appears in the **Name** field. Change this field to MathClass.vb and click **Add**. This creates a class named `MathClass`, and displays its code.

6. Add the following code to the top of `MathClass` to inherit from the COM class.

     [!code-vb[VbVbalrInterop#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#31)]

7. Overload the public method of the base class by adding the following code to `MathClass`:

     [!code-vb[VbVbalrInterop#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#32)]

8. Extend the inherited class by adding the following code to `MathClass`:

     [!code-vb[VbVbalrInterop#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#33)]

The new class inherits the properties of the base class in the COM object, overloads a method, and defines a new method to extend the class.

### <a name="to-test-the-inherited-class"></a>To test the inherited class

1. Add a button to your startup form, and then double-click it to view its code.

2. In the button's `Click` event handler procedure, add the following code to create an instance of `MathClass` and call the overloaded methods:

     [!code-vb[VbVbalrInterop#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#34)]

3. Run the project by pressing F5.

When you click the button on the form, the `AddNumbers` method is first called with `Short` data type numbers, and Visual Basic chooses the appropriate method from the base class. The second call to `AddNumbers` is directed to the overload method from `MathClass`. The third call calls the `SubtractNumbers` method, which extends the class. The property in the base class is set, and the value is displayed.

## <a name="next-steps"></a>后续步骤

You may have noticed that the overloaded `AddNumbers` function appears to have the same data type as the method inherited from the base class of the COM object. This is because the arguments and parameters of the base class method are defined as 16-bit integers in Visual Basic 6.0, but they are exposed as 16-bit integers of type `Short` in later versions of Visual Basic. The new function accepts 32-bit integers, and overloads the base class function.

When working with COM objects, make sure that you verify the size and data types of parameters. For example, when you are using a COM object that accepts a Visual Basic 6.0 collection object as an argument, you cannot provide a collection from a later version of Visual Basic.

Properties and methods inherited from COM classes can be overridden, meaning that you can declare a local property or method that replaces a property or method inherited from a base COM class. The rules for overriding inherited COM properties are similar to the rules for overriding other properties and methods with the following exceptions:

- If you override any property or method inherited from a COM class, you must override all the other inherited properties and methods.

- Properties that use `ByRef` parameters cannot be overridden.

## <a name="see-also"></a>请参阅

- [.NET Framework 应用程序中的 COM 互操作性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [Inherits 语句](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Short 数据类型](../../../visual-basic/language-reference/data-types/short-data-type.md)
