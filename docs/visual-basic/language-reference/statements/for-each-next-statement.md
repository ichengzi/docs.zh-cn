---
title: For Each...Next 语句
ms.date: 07/20/2015
f1_keywords:
- vb.ForEach
- vb.ForEachNext
- vb.Each
- ForEachNext
helpviewer_keywords:
- infinite loops
- Next statement [Visual Basic], For Each...Next
- endless loops
- loop structures [Visual Basic], For Each...Next
- loops, endless
- Each keyword [Visual Basic]
- instructions, repeating
- For Each statement [Visual Basic]
- collections, instruction repetition
- loops, infinite
- For Each...Next statements
- For keyword [Visual Basic], For Each...Next statements
- Exit statement [Visual Basic], For Each...Next statements
- iteration
ms.assetid: ebce3120-95c3-42b1-b70b-fa7da40c75e2
ms.openlocfilehash: 572f1efc0148bd8df4f13fa5651e74249caa45a7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351198"
---
# <a name="for-eachnext-statement-visual-basic"></a>For Each...Next 语句 (Visual Basic)

Repeats a group of statements for each element in a collection.

## <a name="syntax"></a>语法

```vb
For Each element [ As datatype ] In group
    [ statements ]
    [ Continue For ]
    [ statements ]
    [ Exit For ]
    [ statements ]
Next [ element ]
```

## <a name="parts"></a>部件

|术语|定义|
|---|---|
|`element`|Required in the `For Each` statement. Optional in the `Next` statement. Variable. Used to iterate through the elements of the collection.|
|`datatype`|Optional if [`Option Infer`](option-infer-statement.md) is on (the default) or `element` is already declared; required if `Option Infer` is off and `element` isn't already declared. `element`的数据类型。|
|`group`|必须的。 A variable with a type that's a collection type or Object. Refers to the collection over which the `statements` are to be repeated.|
|`statements`|可选。 One or more statements between `For Each` and `Next` that run on each item in `group`.|
|`Continue For`|可选。 Transfers control to the start of the `For Each` loop.|
|`Exit For`|可选。 Transfers control out of the `For Each` loop.|
|`Next`|必须的。 Terminates the definition of the `For Each` loop.|

## <a name="simple-example"></a>Simple Example

Use a `For Each`...`Next` loop when you want to repeat a set of statements for each element of a collection or array.

> [!TIP]
> A [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) works well when you can associate each iteration of a loop with a control variable and determine that variable's initial and final values. However, when you are dealing with a collection, the concept of initial and final values isn't meaningful, and you don't necessarily know how many elements the collection has. In this kind of case, a `For Each`...`Next` loop is often a better choice.

In the following example, the `For Each`…`Next` statement iterates through all the elements of a List collection.

[!code-vb[VbVbalrStatements#121](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#121)]

For more examples, see [Collections](../../../standard/collections/index.md) and [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).

## <a name="nested-loops"></a>Nested Loops

You can nest `For Each` loops by putting one loop within another.

The following example demonstrates nested `For Each`…`Next` structures.

[!code-vb[VbVbalrStatements#122](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#122)]

When you nest loops, each loop must have a unique `element` variable.

You can also nest different kinds of control structures within each other. For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).

## <a name="exit-for-and-continue-for"></a>Exit For and Continue For

The [Exit For](../../../visual-basic/language-reference/statements/exit-statement.md) statement causes execution to exit the `For`…`Next` loop and transfers control to the statement that follows the `Next` statement.

The `Continue For` statement transfers control immediately to the next iteration of the loop. For more information, see [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).

The following example shows how to use the `Continue For` and `Exit For` statements.

[!code-vb[VbVbalrStatements#123](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#123)]

You can put any number of `Exit For` statements in a `For Each` loop. When used within nested `For Each` loops, `Exit For` causes execution to exit the innermost loop and transfers control to the next higher level of nesting.

`Exit For` is often used after an evaluation of some condition, for example, in an `If`...`Then`...`Else` structure. You might want to use `Exit For` for the following conditions:

- Continuing to iterate is unnecessary or impossible. This might be caused by an erroneous value or a termination request.

- An exception is caught in a `Try`...`Catch`...`Finally`. You might use `Exit For` at the end of the `Finally` block.

- There an endless loop, which is a loop that could run a large or even infinite number of times. If you detect such a condition, you can use `Exit For` to escape the loop. For more information, see [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).

## <a name="iterators"></a>Iterators

You use an *iterator* to perform a custom iteration over a collection. An iterator can be a function or a `Get` accessor. It uses a `Yield` statement to return each element of the collection one at a time.

You call an iterator by using a `For Each...Next` statement. `For Each` 循环的每次迭代都会调用迭代器。 When a `Yield` statement is reached in the iterator, the expression in the `Yield` statement is returned, and the current location in code is retained. 下次调用迭代器时，将从该位置重新开始执行。

The following example uses an iterator function. The iterator function has a `Yield` statement that's inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop. In the `ListEvenNumbers` method, each iteration of the `For Each` statement body creates a call to the iterator function, which proceeds to the next `Yield` statement.

[!code-vb[VbVbalrStatements#127](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#127)]

For more information, see [Iterators](../../programming-guide/concepts/iterators.md), [Yield Statement](../../../visual-basic/language-reference/statements/yield-statement.md), and [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).

## <a name="technical-implementation"></a>技术实现

When a `For Each`…`Next` statement runs, Visual Basic evaluates the collection only one time, before the loop starts. If your statement block changes `element` or `group`, these changes don't affect the iteration of the loop.

When all the elements in the collection have been successively assigned to `element`, the `For Each` loop stops and control passes to the statement following the `Next` statement.

If [Option Infer](option-infer-statement.md) is on (its default setting), the Visual Basic compiler can infer the data type of `element`. If it is off and `element` hasn't been declared outside the loop, you must declare it in the `For Each` statement. To declare the data type of `element` explicitly, use an `As` clause. Unless the data type of element is defined outside the `For Each`...`Next` construct, its scope is the body of the loop. Note that you cannot declare `element` both outside and inside the loop.

You can optionally specify `element` in the `Next` statement. This improves the readability of your program, especially if you have nested `For Each` loops. You must specify the same variable as the one that appears in the corresponding `For Each` statement.

You might want to avoid changing the value of `element` inside a loop. Doing this can make it more difficult to read and debug your code. Changing the value of `group` doesn't affect the collection or its elements, which were determined when the loop was first entered.

When you're nesting loops, if a `Next` statement of an outer nesting level is encountered before the `Next` of an inner level, the compiler signals an error. However, the compiler can detect this overlapping error only if you specify `element` in every `Next` statement.

If your code depends on traversing a collection in a particular order, a `For Each`...`Next` loop isn't the best choice, unless you know the characteristics of the enumerator object the collection exposes. The order of traversal isn't determined by Visual Basic, but by the <xref:System.Collections.IEnumerator.MoveNext%2A> method of the enumerator object. Therefore, you might not be able to predict which element of the collection is the first to be returned in `element`, or which is the next to be returned after a given element. You might achieve more reliable results using a different loop structure, such as `For`...`Next` or `Do`...`Loop`.

The runtime must be able to convert the elements in `group` to `element`. The [`Option Strict`] statement controls whether both widening and narrowing conversions are allowed (`Option Strict` is off, its default value), or whether only widening conversions are allowed (`Option Strict` is on). For more information, see [Narrowing conversions](#narrowing-conversions).

The data type of `group` must be a reference type that refers to a collection or an array that's enumerable. Most commonly this means that `group` refers to an object that implements the <xref:System.Collections.IEnumerable> interface of the `System.Collections` namespace or the <xref:System.Collections.Generic.IEnumerable%601> interface of the `System.Collections.Generic` namespace. `System.Collections.IEnumerable` defines the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method, which returns an enumerator object for the collection. The enumerator object implements the `System.Collections.IEnumerator` interface of the `System.Collections` namespace and exposes the <xref:System.Collections.IEnumerator.Current%2A> property and the <xref:System.Collections.IEnumerator.Reset%2A> and <xref:System.Collections.IEnumerator.MoveNext%2A> methods. Visual Basic uses these to traverse the collection.

### <a name="narrowing-conversions"></a>收缩转换

When `Option Strict` is set to `On`, narrowing conversions ordinarily cause compiler errors. In a `For Each` statement, however, conversions from the elements in `group` to `element` are evaluated and performed at run time, and compiler errors caused by narrowing conversions are suppressed.

In the following example, the assignment of `m` as the initial value for `n` doesn't compile when `Option Strict` is on because the conversion of a `Long` to an `Integer` is a narrowing conversion. In the `For Each` statement, however, no compiler error is reported, even though the assignment to `number` requires the same conversion from `Long` to `Integer`. In the `For Each` statement that contains a large number, a run-time error occurs when <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> is applied to the large number.

[!code-vb[VbVbalrStatements#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class3.vb#89)]

### <a name="ienumerator-calls"></a>IEnumerator Calls

When execution of a `For Each`...`Next` loop starts, Visual Basic verifies that `group` refers to a valid collection object. If not, it throws an exception. Otherwise, it calls the <xref:System.Collections.IEnumerator.MoveNext%2A> method and the <xref:System.Collections.IEnumerator.Current%2A> property of the enumerator object to return the first element. If `MoveNext` indicates that there is no next element, that is, if the collection is empty, the `For Each` loop stops and control passes to the statement following the `Next` statement. Otherwise, Visual Basic sets `element` to the first element and runs the statement block.

Each time Visual Basic encounters the `Next` statement, it returns to the `For Each` statement. Again it calls `MoveNext` and `Current` to return the next element, and again it either runs the block or stops the loop depending on the result. This process continues until `MoveNext` indicates that there is no next element or an `Exit For` statement is encountered.

**Modifying the Collection.** The enumerator object returned by <xref:System.Collections.IEnumerable.GetEnumerator%2A> normally doesn't let you change the collection by adding, deleting, replacing, or reordering any elements. If you change the collection after you have initiated a `For Each`...`Next` loop, the enumerator object becomes invalid, and the next attempt to access an element causes an <xref:System.InvalidOperationException> exception.

However, this blocking of modification isn't determined by Visual Basic, but rather by the implementation of the <xref:System.Collections.IEnumerable> interface. It is possible to implement `IEnumerable` in a way that allows for modification during iteration. If you are considering doing such dynamic modification, make sure that you understand the characteristics of the `IEnumerable` implementation on the collection you are using.

**Modifying Collection Elements.** The <xref:System.Collections.IEnumerator.Current%2A> property of the enumerator object is [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md), and it returns a local copy of each collection element. This means that you cannot modify the elements themselves in a `For Each`...`Next` loop. Any modification you make affects only the local copy from `Current` and isn't reflected back into the underlying collection. However, if an element is a reference type, you can modify the members of the instance to which it points. The following example modifies the `BackColor` member of each `thisControl` element. You cannot, however, modify `thisControl` itself.

```vb
Sub LightBlueBackground(thisForm As System.Windows.Forms.Form)
    For Each thisControl In thisForm.Controls
        thisControl.BackColor = System.Drawing.Color.LightBlue
    Next thisControl
End Sub
```

The previous example can modify the `BackColor` member of each `thisControl` element, although it cannot modify `thisControl` itself.

**Traversing Arrays.** Because the <xref:System.Array> class implements the <xref:System.Collections.IEnumerable> interface, all arrays expose the <xref:System.Array.GetEnumerator%2A> method. This means that you can iterate through an array with a `For Each`...`Next` loop. However, you can only read the array elements. You cannot change them.

## <a name="example"></a>示例

The following example lists all the folders in the C:\ directory by using the <xref:System.IO.DirectoryInfo> class.

[!code-vb[VbVbalrStatements#124](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#124)]

## <a name="example"></a>示例

以下示例阐释了对集合排序的过程。 The example sorts instances of a `Car` class that are stored in a <xref:System.Collections.Generic.List%601>. `Car` 类实现 <xref:System.IComparable%601> 接口，此操作需要实现 <xref:System.IComparable%601.CompareTo%2A> 方法。

Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that's used for sorting. `CompareTo` 方法中用户编写的代码针对当前对象与另一个对象的每个比较返回一个值。 如果当前对象小于另一个对象，则返回的值小于零；如果当前对象大于另一个对象，则返回的值大于零；如果当前对象等于另一个对象，则返回的值等于零。 这使你可以在代码中定义大于、小于和等于条件。

在 `ListCars` 方法中，`cars.Sort()` 语句对列表进行排序。 对 <xref:System.Collections.Generic.List%601> 的 <xref:System.Collections.Generic.List%601.Sort%2A> 方法的此调用将导致为 `List` 中的 `Car` 对象自动调用 `CompareTo` 方法。

[!code-vb[VbVbalrStatements#125](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#125)]

## <a name="see-also"></a>请参阅

- [集合](../../../standard/collections/index.md)
- [For...Next 语句](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [循环结构](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While 语句](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Do...Loop 语句](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [扩大转换和收缩转换](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [对象初始值设定项：命名类型和匿名类型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [集合初始值设定项](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [数组](../../../visual-basic/programming-guide/language-features/arrays/index.md)
