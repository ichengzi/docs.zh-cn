---
title: 如何：创建属性
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
ms.openlocfilehash: ee5a9f687765ce064eb3c3f84218ed36eb916d9d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349704"
---
# <a name="how-to-create-a-property-visual-basic"></a>如何：创建属性 (Visual Basic)
You enclose a property definition between a `Property` statement and an `End Property` statement. Within this definition you define a `Get` procedure, a `Set` procedure, or both. All the property's code lies within these procedures.  
  
 The `Get` procedure retrieves the property's value, and the `Set` procedure stores a value. If you want the property to have read/write access, you must define both procedures. For a read-only property, you define only `Get`, and for a write-only property, you define only `Set`.  
  
### <a name="to-create-a-property"></a>To create a property  
  
1. Outside any property or procedure, use a [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md), followed by an `End Property` statement.  
  
2. If the property takes parameters, follow the `Property` keyword with the name of the procedure, then the parameter list in parentheses.  
  
3. Follow the parentheses with an `As` clause to specify the data type of the property's value. You must specify the data type even for a write-only property.  
  
4. Add `Get` and `Set` procedures, as appropriate. See the following directions.  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a>To create a Get procedure that retrieves a property value  
  
1. Between the `Property` and `End Property` statements, write a [Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md), followed by an `End Get` statement. You do not need to define any parameters for the `Get` procedure.  
  
2. Place the code statements to retrieve the property's value between the `Get` and `End Get` statements. This code can include other calculations and data manipulations in addition to generating and returning the property's value.  
  
3. Use a `Return` statement to return the property's value to the calling code.  
  
 You must write a `Get` procedure for a read-write property and for a read-only property. You must not define a `Get` procedure for a write-only property.  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a>To create a Set procedure that writes a property's value  
  
1. Between the `Property` and `End Property` statements, write a [Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md), followed by an `End Set` statement.  
  
2. In the `Set` statement, follow the `Set` keyword with a parameter list in parentheses. This parameter list must include at least a value parameter for the value passed by the calling code. The default name for this value parameter is `Value`, but you can use a different name if appropriate. The value parameter must have the same data type as the property itself.  
  
3. Place the code statements to store a value in the property between the `Set` and `End Set` statements. This code can include other calculations and data manipulations in addition to validating and storing the property's value.  
  
4. Use the value parameter to accept the value supplied by the calling code. You can either store this value directly in an assignment statement, or use it in an expression to calculate the internal value to be stored.  
  
 You must write a `Set` procedure for a read-write property and for a write-only property. You must not define a `Set` procedure for a read-only property.  
  
## <a name="example"></a>示例  
 The following example creates a read/write property that stores a full name as two constituent names, the first name and the last name. When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name. When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names. If it does not find a space, it stores it all as the first name.  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 The following example shows typical calls to the property procedures of `fullName`. The first call sets the property value and the second call retrieves it.  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>请参阅

- [过程](./index.md)
- [属性过程](./property-procedures.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md)
- [如何：声明具有混合访问级别的属性](./how-to-declare-a-property-with-mixed-access-levels.md)
- [如何：调用 Property 过程](./how-to-call-a-property-procedure.md)
- [How to: Declare and Call a Default Property in Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [如何：在属性中放置值](./how-to-put-a-value-in-a-property.md)
- [如何：从属性获取值](./how-to-get-a-value-from-a-property.md)
