---
title: 结构和其他编程元素
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], arrays
- procedures [Visual Basic], structures as arguments to
- objects [Visual Basic], structure elements
- arrays [Visual Basic], structure elements
- nested structures [Visual Basic]
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
ms.openlocfilehash: 309d0e5214897675e1758bd98b964392b379ca1b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346122"
---
# <a name="structures-and-other-programming-elements-visual-basic"></a>结构和其他编程元素 (Visual Basic)
You can use structures in conjunction with arrays, objects, and procedures, as well as with each other. The interactions use the same syntax as these elements use individually.  
  
> [!NOTE]
> You cannot initialize any of the structure elements in the structure declaration. You can assign values only to elements of a variable that has been declared to be of a structure type.  
  
## <a name="structures-and-arrays"></a>Structures and Arrays  
 A structure can contain an array as one or more of its elements. 下面的示例阐释了这一点。  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure   
```  
  
 You access the values of an array within a structure the same way you access a property on an object. 下面的示例阐释了这一点。  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 You can also declare an array of structures. 下面的示例阐释了这一点。  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 You follow the same rules to access the components of this data architecture. 下面的示例阐释了这一点。  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a>Structures and Objects  
 A structure can contain an object as one or more of its elements. 下面的示例阐释了这一点。  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 You should use a specific object class in such a declaration, rather than `Object`.  
  
## <a name="structures-and-procedures"></a>Structures and Procedures  
 You can pass a structure as a procedure argument. 下面的示例阐释了这一点。  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 The preceding example passes the structure *by reference*, which allows the procedure to modify its elements so that the changes take effect in the calling code. If you want to protect a structure against such modification, pass it by value.  
  
 You can also return a structure from a `Function` procedure. 下面的示例阐释了这一点。  
  
```vb  
Dim allSystems(100) As systemInfo  
Function findByDate(ByVal searchDate As Date) As systemInfo  
    Dim i As Integer  
    For i = 1 To 100  
        If allSystems(i).purchaseDate = searchDate Then Return allSystems(i)  
    Next i  
   ' Process error: system with desired purchase date not found.  
End Function  
```  
  
## <a name="structures-within-structures"></a>Structures Within Structures  
 Structures can contain other structures. 下面的示例阐释了这一点。  
  
```vb  
Public Structure driveInfo  
    Public type As String  
    Public size As Long  
End Structure  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As driveInfo  
    Public purchaseDate As Date  
End Structure  
```  
  
```vb  
Dim allSystems(100) As systemInfo  
ReDim allSystems(1).diskDrives(3)  
allSystems(1).diskDrives(0).type = "Floppy"  
```  
  
 You can also use this technique to encapsulate a structure defined in one module within a structure defined in a different module.  
  
 Structures can contain other structures to an arbitrary depth.  
  
## <a name="see-also"></a>请参阅

- [数据类型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [基本数据类型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [复合数据类型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [值类型和引用类型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [结构](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [数据类型疑难解答](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [如何：声明结构](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [结构变量](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [结构和类](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Structure 语句](../../../../visual-basic/language-reference/statements/structure-statement.md)
