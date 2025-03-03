---
title: Using 语句
ms.date: 07/20/2015
f1_keywords:
- vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
ms.openlocfilehash: 6ec0e228b3898f66f27e322b5db2dd7f3bf3d7d6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352762"
---
# <a name="using-statement-visual-basic"></a>Using 语句 (Visual Basic)

Declares the beginning of a `Using` block and optionally acquires the system resources that the block controls.

## <a name="syntax"></a>语法

```vb
Using { resourcelist | resourceexpression }
    [ statements ]
End Using
```

## <a name="parts"></a>部件

|术语|定义|  
|---|---|  
|`resourcelist`|Required if you do not supply `resourceexpression`. List of one or more system resources that this `Using` block controls, separated by commas.|  
|`resourceexpression`|Required if you do not supply `resourcelist`. Reference variable or expression referring to a system resource to be controlled by this `Using` block.|  
|`statements`|可选。 Block of statements that the `Using` block runs.|  
|`End Using`|必须的。 Terminates the definition of the `Using` block and disposes of all the resources that it controls.|  

 Each resource in the `resourcelist` part has the following syntax and parts:

 `resourcename As New resourcetype [ ( [ arglist ] ) ]`

 或

 `resourcename As resourcetype = resourceexpression`

## <a name="resourcelist-parts"></a>resourcelist Parts

|术语|定义|  
|---|---|  
|`resourcename`|必须的。 Reference variable that refers to a system resource that the `Using` block controls.|  
|`New`|Required if the `Using` statement acquires the resource. If you have already acquired the resource, use the second syntax alternative.|  
|`resourcetype`|必须的。 The class of the resource. The class must implement the <xref:System.IDisposable> interface.|  
|`arglist`|可选。 List of arguments you are passing to the constructor to create an instance of `resourcetype`. See [Parameter List](parameter-list.md).|  
|`resourceexpression`|必须的。 Variable or expression referring to a system resource satisfying the requirements of `resourcetype`. If you use the second syntax alternative, you must acquire the resource before passing control to the `Using` statement.|  
  
## <a name="remarks"></a>备注

 Sometimes your code requires an unmanaged resource, such as a file handle, a COM wrapper, or a SQL connection. A `Using` block guarantees the disposal of one or more such resources when your code is finished with them. This makes them available for other code to use.

 Managed resources are disposed of by the .NET Framework garbage collector (GC) without any extra coding on your part. You do not need a `Using` block for managed resources. However, you can still use a `Using` block to force the disposal of a managed resource instead of waiting for the garbage collector.

 A `Using` block has three parts: acquisition, usage, and disposal.

- *Acquisition* means creating a variable and initializing it to refer to the system resource. The `Using` statement can acquire one or more resources, or you can acquire exactly one resource before entering the block and supply it to the `Using` statement. If you supply `resourceexpression`, you must acquire the resource before passing control to the `Using` statement.

- *Usage* means accessing the resources and performing actions with them. The statements between `Using` and `End Using` represent the usage of the resources.

- *Disposal* means calling the <xref:System.IDisposable.Dispose%2A> method on the object in `resourcename`. This allows the object to cleanly terminate its resources. The `End Using` statement disposes of the resources under the `Using` block's control.

## <a name="behavior"></a>行为

 A `Using` block behaves like a `Try`...`Finally` construction in which the `Try` block uses the resources and the `Finally` block disposes of them. Because of this, the `Using` block guarantees disposal of the resources, no matter how you exit the block. This is true even in the case of an unhandled exception, except for a <xref:System.StackOverflowException>.

 The scope of every resource variable acquired by the `Using` statement is limited to the `Using` block.

 If you specify more than one system resource in the `Using` statement, the effect is the same as if you nested `Using` blocks one within another.

 If `resourcename` is `Nothing`, no call to <xref:System.IDisposable.Dispose%2A> is made, and no exception is thrown.

## <a name="structured-exception-handling-within-a-using-block"></a>Structured Exception Handling Within a Using Block

 If you need to handle an exception that might occur within the `Using` block, you can add a complete `Try`...`Finally` construction to it. If you need to handle the case where the `Using` statement is not successful in acquiring a resource, you can test to see if `resourcename` is `Nothing`.

## <a name="structured-exception-handling-instead-of-a-using-block"></a>Structured Exception Handling Instead of a Using Block

 If you need finer control over the acquisition of the resources, or you need additional code in the `Finally` block, you can rewrite the `Using` block as a `Try`...`Finally` construction. The following example shows skeleton `Try` and `Using` constructions that are equivalent in the acquisition and disposal of `resource`.

```vb
Using resource As New resourceType
    ' Insert code to work with resource.
End Using

' For the acquisition and disposal of resource, the following  
' Try construction is equivalent to the Using block.
Dim resource As New resourceType
Try
    ' Insert code to work with resource.
Finally
    If resource IsNot Nothing Then
        resource.Dispose()
    End If
End Try
```

> [!NOTE]
> The code inside the `Using` block should not assign the object in `resourcename` to another variable. When you exit the `Using` block, the resource is disposed, and the other variable cannot access the resource to which it points.

## <a name="example"></a>示例

 The following example creates a file that is named log.txt and writes two lines of text to the file. The example also reads that same file and displays the lines of text:

 Because the <xref:System.IO.TextWriter> and <xref:System.IO.TextReader> classes implement the <xref:System.IDisposable> interface, the code can use `Using` statements to ensure that the file is correctly closed after the write and read operations.

 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]

## <a name="see-also"></a>请参阅

- <xref:System.IDisposable>
- [Try...Catch...Finally 语句](try-catch-finally-statement.md)
- [如何：释放系统资源](../../programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
