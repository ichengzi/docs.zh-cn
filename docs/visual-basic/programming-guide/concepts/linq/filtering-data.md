---
title: 筛选数据
ms.date: 07/20/2015
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
ms.openlocfilehash: 81e207e451055fb2952e4bf393db067f0851afb4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353491"
---
# <a name="filtering-data-visual-basic"></a>Filtering Data (Visual Basic)

筛选是指将结果集限制为仅包含满足指定条件的元素的操作。 它也称为选定内容。

下图演示了对字符序列进行筛选的结果。 筛选操作的谓词指定字符必须为“A”。

![显示 LINQ 筛选操作的图表](./media/filtering-data/linq-filter-operation.png)

下面一节列出了执行所选内容的标准查询运算符方法。

## <a name="methods"></a>方法

|方法名|描述|Visual Basic Query Expression Syntax|详细信息|
|-----------------|-----------------|------------------------------------------|----------------------|
|OfType|根据其转换为特定类型的能力选择值。|不适用。|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|Where|选择基于谓词函数的值。|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a>查询表达式语法示例

The following example uses the `Where` to filter from an array those strings that have a specific length.

```vb
Dim words() As String = {"the", "quick", "brown", "fox", "jumps"}

Dim query = From word In words
            Where word.Length = 3
            Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In query
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' the
' fox
```

## <a name="see-also"></a>请参阅

- <xref:System.Linq>
- [标准查询运算符概述 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Where 子句](../../../../visual-basic/language-reference/queries/where-clause.md)
- [如何：筛选查询结果](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md)
- [How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [How to: Query for Files with a Specified Attribute or Name (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
